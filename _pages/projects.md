---
permalink: /projects/
---

## Aegis Descent
*Traega Entertainment – 2021-2022*\
![RD](/assets/projects/aegisdescent.jpg){:class="img-responsive"}\
[Steam](https://store.steampowered.com/app/1251040/Aegis_Descent/) [Epic](https://store.epicgames.com/en-US/p/aegis-descent-a1f5a0)
Roguelite vehicle-based shooter set in WW2 era.
- Created subsystem for capturing player stats.
- Created awards system for granting achievements based on stats, and giving unlocks based on accumulated award score.
- Fleshed out support for 'perks' that modify the player's base stats.
- Built a new objective system with support for multiple objective types and capturing and displaying progress on the HUD.
- Developed a basic "New User Experience" popup system to introduce players to the game.
- Tracked down some performance issues to reach target framerate on our minspec machine.
- Integrated with EOS for Epic Games Store achievements.

## R&D Project
*Torch Technologies – 2019-2021*
![RD](/assets/projects/rd.jpg){:class="img-responsive"}\
Research towards government product
- Created a tool to generate an accurate Earth ellipsoid in UE4. Ellipsoid utilized Blue Earth/Black Earth textures from NASA and Epic's Sky Atmosphere. Earth could be ellipsoidal or flat, and the origin could be at the center of the globe or at a specified LLA location.
- Imported real-world terrain data, textured it, and oriented it on the Earth ellipsoid/plane.
- Worked on plugin that interfaced with KDIS and to receive DIS packets and create/position/orient/animate entities appropriately in-game.

## Synthetic Environment Generator (SEG)
*Torch Technologies – 2018-2019*
Scene generator in UE4 that generated accurate IR scenery for training missile sensors
- Wrote importers for IR terrain and models (static and skeletal).
- Delved into the renderer to ensure we got nearly 1-1 pixel parity with two existing IR scene generators. 
- Created the ability to have different missile sensors see only the visual data that pertains to them.
- Wrote an interface that let an external lab controller load/control/restart a scenario.
- Wrote a custom library that the interface could talk to to support another external lab controller.
- Worked exclusively in CentOS Linux.

## America's Army Proving Grounds
*SAIC/America's Army – 2010-2018*\
![AA4](/assets/projects/aa4.jpg){:class="img-responsive"}\
[Steam](https://store.steampowered.com/app/203290/Americas_Army_Proving_Grounds/)

- Responsible for weapon and combat code. Created inventory system. Created client and server hit detection systems. Created mirroring of pawn and weapon classes (so you always see your team as good guys and the other team as bad guys).
- Co-designed and implemented the spectate system.
- Responsible for the game flow code. Handled how the player joins the game, and how the mission progresses from start to finish. Created the various mission objective types.
- Created server admin tools, including syncing features (like a banned player list) between multiple admins.
- Implemented a voting system for players to change maps, kick cheaters off the server, etc.
- Worked closely with designers to quickly prototype and iterate on new features.
- Integrated Sony matchmaking features.
- Profiled and optimized Game and Rendering code.
- Worked on the unfinished Mac port.
- Finished porting the game server to Linux. Wrote scripts to deploy and run multiple servers on AWS boxes.

## America's Army 3
*SAIC/America's Army – 2009-2010*\
![AA3](/assets/projects/aa3.jpg){:class="img-responsive"}

- Co-designed and implemented sweeping changes to the injury and medic systems.
- Worked with Senior Designer and artists to redesign the HUD.
- Profiled and optimized code and net traffic
- Set up pipeline for handling crash reports, and resolved several crashes that had been difficult to reproduce.
- Fixed several multiplayer replication issues that had gone unnoticed.
- Interfaced closely with the Level Design team to provide tools, including visual scripting nodes and interactive actors for training levels.

## Government Applications
*SAIC/America's Army Gov Apps – 2005-2010*

Worked extensively on 10 Unreal Engine projects in UE2 and UE3. Provided support for several others. Some of the projects I worked on included:

### CROWS (UE2)
Taught soldiers how to use CROWS hardware.
- Recreated hardware UI and features in-engine based on manuals and documents.
- Built multiplayer physics-based vehicles.
- Used accurate ballistics for projectiles.
- Created some simple NPCs for standing at checkpoints and directing the driver player.
- Wrote a simple driving AI for when the trainer needed to be operated in singleplayer.


### CROWS (UE3)
New iteration of UE2 trainer 5 years later.
- Recreated hardware UI and features in-engine based on actual hardware we had in the lab, including recreating bugs from the real on-board software.
- UI was created in Scaleform GFx.
- Connected to existing vehicle from another project.
- Used accurate ballistics.

### Instructor Workstation (IWS) (UE2)
Special role used on multiple projects that allowed a player to act as the 'instructor' in a multiplayer environment. The instructor had the ability to free-fly around the map, pause any simulations, add/move/remove actors or effects in the environment, modify properties of actors or the world, possess placed characters or vehicles to challenge the players, save placed items as a scenario, load previously-saved scenarios, and use a filterable and zoomable minimap to see everything in the scenario and teleport anywhere in the game world.
- Helped build custom UI framework that was also used on other projects.
- Made an interactive minimap to track people, vehicles, missiles, etc. and provided hooks to easily add tracking of custom objects for use on other projects.
- Worked on and debugged various other aspects (e.g. actor placement, scenario system) as needed.

### CBRN/NBCRV (UE2)
Taught soldiers how to use special equipment for detecting biological and chemical weapons
- Built multiplayer physics-based vehicles with multiple interior 'seats' and physics-based attachments.
- Added animations to the vehicle mesh when the operators performed various actions. Animations also affected physics attachments.
- Created physically-simulated 'flags' (buoy-like with rounded bottoms) that the operator could drop from the vehicle to indicate that an contaminant was detected in the area.

### Gladiator (UE2)
A Basic Skills Trainer (BST) for the Gladiator unmanned ground vehicle.
- Built a small physics-based vehicle with attachments for weapons and cameras.
- Worked on split-screen implementation so we could see a 'game' view side-by-side with the view the operator would actually see.

### MULE
A small project that simulated the workload of operating the MULE unmanned ground vehicle to see if it would be acceptable for a single soldier to operate all of its functions successfully.
- Created physics-based vehicle with wheels attached to moving arms. Had to dig into the Karma physics code to figure out the best way to support this feature.
- Integrated DirectX device with Unreal. Allowed creation of route for vehicle to follow via a touchscreen and stylus.
- Created custom driving AI for the vehicle.

### RRM/SMAW-D Missile
Small project that integrated with a physical shoulder-mounted launcher, and let you fire it at targets on a projected screen (think Duck Hunt).
- Created handheld weapon with ballistically-accurate physics.
- Created UI and flow to get you into the scenario.

### TALON
Trainer for EOD in the use of a TALON robot.
- Created a tracked vehicle simulation. Could navigate several sandbox environments that a real TALON with tracks would be able to navigate. Engine and tire grip were modelled to fit provided 'truth' data.
- Built physics-based arms and a few end-point attachments (gripper claw, wire probe, etc.).
- Integrated with a gamepad for easier control.

### Medal of Honor Battle Recreation
A movie created in the game world that reinacted the battle in which Medal of Honor recipient Sergeant First Class Paul Ray Smith lost his life.

[Video](https://www.youtube.com/watch?v=qb9iWbPRDlU) (Note the stretched ratio is due to the fact that the presentation was done on an ultra-wide display (two or three projector screens, if I recall correctly))
- Created physics-based vehicles, some with attached weapons that could be operated by the player-actors.

### RRM
Project to simulate an incoming attack and allow operator to command missile-based response.
- Created custom UI with many custom widgets.
- Built the backend to allow the selection of different missile launchers and views from various sensors.
- Built multi-stage missile flight model that used simple physics and tracking methods.
- Integrated and expanded on the minimap initially created for the IWS.

### TRICT Rollover Trainer: 
![MRAP](/assets/projects/mrap-rollover.jpg){:class="img-responsive"}\
[Article 1](https://www.army.mil/article/56674/soldiers_flip_over_realistic_training_vehicle) [Article 2](https://www.waff.com/story/21890549/redstone-report-rollover-training-with-simulation-software/)

Trainer that put soldiers into surprise "roll-over events" so they could train exiting the MRAP while it is upside down.
- Helped build a multiplayer physics-based MRAP vehicle based on 'truth' data we went out and gathered at Ft McClellan. 
- Integrated the newly-created UE3 CROWS on top of the MRAP.
- Worked on the level loading and streaming process, and the loading of scenarios created by the new Instructor Workstation.
- Worked on post process effect setup for water.
- Created multiple 'seats' and help set up the cameras to integrate with the screens we put in the hollowed-out MRAP.
