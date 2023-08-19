---
title: "C++ GAME DEV 0: INTRODUCTION"
permalink: /gamedev/cpp-game-dev-0/
excerpt: "Project Setup"
sidebar:
  nav: "gamedev"
---

{% include base_path %}

This is part of an ongoing series where we write a complete 2D game engine in C++ and SFML. A new tutorial is released every Monday. You can find the complete list of tutorials here and download the source code from the projects [GitHub page](https://github.com/thatgamesguy/that_game_engine).

This is the first of a number of tutorials that will guide you through the development of a complete, full-featured game engine. Along the way, I’ll discuss a number of useful patterns and systems; and by the end of the series, you will have your own game engine. By following the tutorials, you will not only have a better understanding of how games are built, but you will have the foundational knowledge to create your own games, no matter the genre. As we will need to test the engine, we will also develop a 2D action/platform game (think Ghouls n’ Ghosts or Shovel Knight and you’ll be on the right track) to run on our engine.

Each week I will release a new tutorial focusing on one specific subject. I will explain, step-by-step, how to create every component our new game engine will require. Some of the features we’ll implement include, how to:
- Get input from the players: polling and real-time; and when to use each.
- Manage the various resources a typical game requires (textures, audio, and font files to name a few).
- Manage different scenes e.g. main menu, game, and pause states.
- Animate our characters.
- Create a simple physics engine.
- Create and import tile maps.
- Efficiently managing collisions with the map and with other objects in the level.
- Create an entity component system.
- Create an audio engine.
- Manage inter-system communication.
- Create and handle events.
- Serialise and de-serialise objects.

Creating games is a multi-faceted and at times complicated subject, and this is only a small selection of what we will cover. This tutorial series is aimed at existing programmers that want to become good game developers. This series will hopefully become the tutorial series that the younger me would have loved to have after graduating from university.

For this project we will use C++ and SFML. I assume you have some knowledge of C++ or a similar language and will not teach you how to use any language specific features; so if you are not comfortable with C++ I would recommend first following an intro course. I do not assume any knowledge of SFML and I’ll discuss relevant SFML topics as they arise.

## Why use SFML?
SFML is well documented online so I won’t go into details about what exactly it is; other than that it will help us with various functions such as drawing to the screen, and playing audio. I recommend starting at SFML’s website for more information: [https://www.sfml-dev.org.I](https://www.sfml-dev.org.i/) will however mention the reasons why 

I am using it for this tutorial series because:
- I have used it before so I can focus on the actual implementation without learning a new library.
- It has a number of bindings for different languages, including: java, python, and ruby. I’ll be using the C++ bindings but you are free to use any of the other available languages.
- It has a decent install base; which means finding support should not be too difficult.
- It is multi-platform, you can follow along on Windows, MacOS, or Linux. It is also being ported to Android and iOS, but that was not available when I started this series.

Of course SFML is not the only choice and you can find a number of decent alternatives online.

Having said all that, it is not really important what library you choose to use. If you are more comfortable with using a different library or even language then feel free to do so. It does not matter what language the game is programmed in, what is important is how we build and combine the various systems.

## Why not use Unity/Unreal Engine?
I’m a big fan of Unity, having used it for most of my professional career (I’m sure Unreal engine is great too, I just happened to use Unity). However I also think that as a games programmer, you should be able to roll your own games engine or at least have a good idea what is going on under the proverbial hood.

## How do you Setup SFML?
This is also well documented online and I will not go into detail here, rather I will link to the main source for each platform.
- Windows: [https://www.sfml-dev.org/tutorials/2.4/start-vc.php](https://www.sfml-dev.org/tutorials/2.4/start-vc.php)
- MacOS: [https://www.sfml-dev.org/tutorials/2.4/start-osx.php](https://www.sfml-dev.org/tutorials/2.4/start-osx.php)
- Linux: [https://www.sfml-dev.org/tutorials/2.4/start-linux.php](https://www.sfml-dev.org/tutorials/2.4/start-linux.php)

The links are for SFML version 2.4.2 and all tutorials will use that version unless otherwise stated. If a new version comes out with some cool new feature that we just have to try, I will talk you through upgrading SFML.

I create and test the projects in Visual c++ 14 (2015) 32bit for Windows and Clang 64bit for MacOS. You can download them from the SFML site but again you are free to use whichever implementation you would like. I will host the source files for each tutorial, once you have a project setup you can drag and drop these files into your project.

You can download the source code for each chapter from the Git repo as they become available (link will be at the top of each page). I will include the source files for each chapter in the separate folders and a current build for Xcode (which I am using for this series. The Xcode build can be considered the Dev build, it may not always run and will include code that has not yet been spoken about in a tutorial.

So this is the first and most likely last post of the series that does not include any code. From now on, we’ll be getting stuck in and creating new features for our engine. If you have any issues with setup or have suggestions on anything you would like to see included then please let me know in the comments.

Thank you for reading 🙂
