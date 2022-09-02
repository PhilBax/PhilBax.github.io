---
date: 2020-08-27 12:00:00 -0600
classes: wide
toc: false
title: "How to Rip with Handbrake"
categories: plex ripping handbrake
excerpt: "How to set up and use Handbrake to rip discs."
---

## Intro

This guide covers ripping discs with Handbrake.

## Note

It's important to note right off the bat that ripping copyrighted content, even for backup purposes, is *illegal* in the US (unlike ripping backups of CDs). Please be aware of this, and rip responsibly.

## Requirements

* This guide will only cover Windows, as that's what I run at home.

* You'll need at least one DVD drive to rip DVD discs. A Blu-ray drive can rip Blu-rays and DVDs. Some Blu-ray drives can be configured to rip 3D Blu-ray discs. However 4K/UHD discs are a different format, and require another type of drive. I have no experience ripping UHD, so it will be ignored in this guide.

* You'll want a fairly beefy CPU (or a lot of patience!), particularly if you're ripping Blu-ray discs. The processor is going to be your main bottleneck.

* You'll need a lot of disc space, depending on how much you're ripping and what your settings are. With my settings, an average movie on DVD takes up around 800 MB - 1.2 GB, and a Blu-ray movie can easily be 3-5 GB.


## Setup

To start, [download](https://handbrake.fr/) and install Handbrake. This will be doing most of the heavy lifting.

#### DVDs

To rip copy-protected DVDs, you'll need to download the latest [libdvdcss-2.dll](https://github.com/allienx/libdvdcss-dll) for your platform (likely x64). 

Place the dll file in the directory where Handbrake is installed (e.g. `C:\Program Files\Handbrake`), and restart Handbrake to load it. It should be able to read your copyrighted DVD discs.

#### Blu-Rays

To rip Blu-rays, you'll need a bit more. I've tried out [AnyDVD](https://www.redfox.bz/en/anydvdhd.html) and liked it pretty well. But for the moment, I'm using [MakeMKV](https://www.makemkv.com/) as it's cheaper, a little more straightforward, and is actually free while in beta (which it's been in beta since 2010!). Download and install it, and use the [latest beta key](https://www.makemkv.com/forum/viewtopic.php?t=1053) to license it for a month or two at a time. If you appreciate their work, and make heavy use of it, please buy the software to support the developers!

You can use MakeMKV to load and rip the discs losslessly to .mkv files, and then load those into Handbrake.

Alternatively, you can use MakeMKV work as the decrypter for Handbrake directly. This can be done in the software under `Preferences > Integration`, or you can manually copy `libmmbd.dll` into the Handbrake directory and rename it to `libaacs.dll`, duplicate it, and rename the copy to `libbdplus.dll`.

## Settings

## Workflow

## Problems

## Conclusion