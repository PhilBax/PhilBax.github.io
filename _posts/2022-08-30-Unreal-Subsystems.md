---
layout: single
date: 2022-08-30 12:00:00 -0600
classes: wide
toc: true
title: "Writing Unreal Subsystems"
categories: ue4 ue5 unreal
excerpt: "Benefits of writing Subsystems in Unreal, and pitfalls to be aware of."
---

# Subsystems

Unreal now has support for creating a variety of "subsystems". These are specialized objects with automatically-managed lifetimes and easy accessibility from blueprints. They are often a great solution for what might otherwise be implemented as a Singleton or a vanilla subject. They're perfect are for separating out and modularizing functionality away from main system subclasses like GameMode or GameInstance, keeping those subclasses from becoming bloated.

This post will go over a brief introduction to using subsystems, and then dive into some caveats and potential workarounds. 

## Introduction

Epic already provides a [good introduction](https://docs.unrealengine.com/4.26/en-US/ProgrammingAndScripting/Subsystems/) to subsystems.

To summarize, you can create subsystems for:
- the Engine
- the GameInstance
- the LocalPlayer
- the Editor
- the [World](https://docs.unrealengine.com/4.27/en-US/API/Runtime/Engine/Subsystems/UWorldSubsystem/) (this one is not mentioned in the Programming Subsystems)

Each subsystem has automatic lifetime management -- the owning class automatically creates and destroys their subsystems, and calls virtual initialize/deinitialize functions on them. Each owning class also provides easy getters for their subsystems by type in both C++ and blueprint. 

They are very useful tools, and you can find many good examples of subsystems in the codebase.

## Caveats

There are some issues you may run into that the documentation fails to mention.

### 1. Engine subsystem have Editor lifetime in PIE

When you create an engine subsystem, you may not realize that these will be created and initialized only once when the editor starts. Playing in-editor will not reinitialize these subsystems, nor will exiting PIE deinitialize them. 

#### Workarounds

Depending on your situation, you may be able to workaround this by manually reinitializing your subsystem by calling a custom init function on it from some place in the game that _is_ called on PIE startup -- perhaps from your GameMode's `BeginPlay()`.

If you only need to utilize the subsystem in PIE for a few limited tests, another option may be to opt to temporarily switch PIE to launch a standalone process. 

### 2. Engine subsystems are created when running commandlets.

This could be useful or desired behavior. But if you don't know it happens, and your subsystem initialization process does stuff you don't want to do in a commandlet (like referencing certain assets), you might wind up breaking those commandlets.

#### Workarounds

If you run into this issue, the fix is straightforward: simply wrap any offending initialization in a check for [`IsRunningCommandlet()`](https://docs.unrealengine.com/4.27/en-US/API/Runtime/Core/IsRunningCommandlet/`)

### 3. Subsystems don't tick

Often subsystems don't need to tick. As such, just like UObjects, they don't have the ability to tick by default.

#### Workarounds

If you're creating a World subsystem, simply subclass [TickableWorldSubsystem](https://docs.unrealengine.com/4.27/en-US/API/Runtime/Engine/Subsystems/UTickableWorldSubsystem/).

If you're making another subsystem type, then just like with UObjects, the solution is to use multiple inheritance to make your subsystem also subclass `FTickableObject`, implement the required interface functions, and flag the object to tick. The tick may optionally be toggled or conditional.

Here is a bare-bones example to get this up and running:

```
UCLASS()
class UMyTickableGameInstanceSubsystem : public UGameInstanceSubsystem, public FTickableGameObject
{
	GENERATED_BODY()

public:
	virtual void Initialize(FSubsystemCollectionBase& Collection) override;
	virtual void Deinitialize() override;

	// FTickableGameObject implementation Begin
	virtual UWorld* GetTickableGameObjectWorld() const override { return GetWorld(); }
	virtual ETickableTickType GetTickableTickType() const override { return ETickableTickType::Always; }
	virtual bool IsAllowedToTick() const override { return true; }
	virtual void Tick(float DeltaTime) override;
	virtual TStatId GetStatId() const override { return TStatId(); }
	// FTickableGameObject implementation End
};
```

### 4. Subsystems don't replicate

Subsystems are all owned by non-replicating classes. You're either going to be on the server or on a client.

#### Workarounds

As with other server-only or server/owner-only classes, like GameMode and PlayerController, you could create a custom class to replicate the state you care about, like GameState and PlayerState.

In fact, if you only have a very small amount of data to replicate, perhaps the better route would be to add that data to one of those State classes. 

Alternatively, you might decide that this justifies moving your class away from being a subsystem, and just make it it's own replicated Actor. You'll have to manage things like its lifetime, its "singleton-ness", and its blueprint exposure manually. But it may be the better decision in your case.

## Conclusion

I hope this provides some insight into some aspects of Subsystems you might not have been aware of. They are very useful tools, and I've started using them for more and more standalone features.

Have you run into any issues I haven't mentioned here? Please get in touch!