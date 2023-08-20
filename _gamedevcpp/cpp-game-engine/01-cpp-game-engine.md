---
title: "C++ Game Dev 1: Game Loop"
permalink: /gamedev/cpp-game-dev-1/
excerpt: "Project Setup"
layout: single
share: true
comments: true
previous: 
  url: /gamedev/cpp-game-dev-0/
sidebar:
  nav: "gamedev"
---



This is part of an ongoing series where we write a complete 2D game engine in C++ and SFML. A new tutorial is released every Monday. You can find the complete list of tutorials here and download the source code from the projects GitHub page.
In this first tutorial we will create our initial game loop (more on that in a bit) and create our first window.

## Initial Project Setup
You can follow the instructions at [www.sfml-dev.org/tutorials](http://www.sfml-dev.org/tutorials) for platform specific instructions on how to create the initial project. At the moment you can follow along on Windows, MacOS, or Linux; although mobile support has been promised. Once you have a working SFML project, make sure to delete any classes that are automatically generated for you, as we’ll write everything we need from scratch.

## The Game Loop
The first thing we’ll be writing is our game loop. You’ll often hear the game loop referred to as the “heart of a game”. It will be responsible for calling all of our game code and keeping the game running. A game loop can become quite complicated (and we will definitely be adding to it in future) but at its core, it is simply a loop that contains a number of methods that when called perform specific actions in our game. In fact we need to perform all input, physics, AI updates and drawing during each loop. Examples of some methods you will find in a typical game loop include:
- _Initialise/EarlyUpdate:_ this is usually called first. You would place any initialisation code that needs to be performed before updating and drawing here. 
- _Update_: This is where most of the game logic will go; including: movement, AI, and animation updates.
- _LateUpdate_: Any logic that relies on data calculated in the Update method will go here, for example: you could place collision logic here that checks for collisions once every entities position has been updated in the Update method.
- FixedUpdate: A special method that is only invoked n times a second, hence the name ‘Fixed’. This is normally used to update physics engines that require a fixed update schedule. This will be explained in detail when we come to implement our own.
- _Draw/Render_: Once all the entities have been updated, we draw them to the screen. This method will be responsible for drawing everything, including the games UI.

It’s not uncommon for game engines to have less/more methods than the ones stated above; you could add specific functions for processing user input, updating physics etc. To begin with we will implement: Update, LateUpdate, and Draw functions. As time goes on we may add a ProcessInput, FixedUpdate and a PhysicsStep method to our game loop; they will be explained in more detail when we need them.

Using this pattern we can also keep track of the progress of time and use this to ensure that our game runs the same no matter what hardware is used. We will discuss frame-rate/update independence, when we we look at moving our first sprite around the screen.

# Loop implementation
Let’s start with writing how we want the game loop to be setup. Create a class called **Main.cpp** (no need to create a corresponding header file). As you have probably guessed, this will be our entry point into the program. Let’s outline the initial loop that we would like our game to have.

**Main.cpp:**
```cpp
#include “Game.hpp”

int main()
{
    Game game;

    while (game.IsRunning())
    {
        game.Update();
        game.LateUpdate();
        game.Draw();
    }
}
```

While this won’t build (we have yet to create the game class), it does outline the minimum we want from our game engine loop. And it is just that, the minimum we require; there are a number of changes we will make to how the game loop functions in a future tutorial but for now this is all we need.

Create a **Game** class to meet our loops criteria.

**Game.hpp:**
```cpp
#ifndef Game_hpp
#define Game_hpp

class Game
{
public:
    void Update();
    void LateUpdate();
    void Draw();
    bool IsRunning() const;
};

#endif /* Game_hpp */
```

**Game.cpp:**
```cpp
#include “Game.hpp”

void Game::Update() { }

void Game::LateUpdate() { }

void Game::Draw() { }

bool Game::IsRunning() const
{
    // We’ll return true here for now but this will be 
    // changed shortly as we need a method of closing the window.
    return true;  
}
```

Our project should now build and we have our basic game engine loop setup. While it isn’t doing anything yet, that will change shortly.

## Creating a Window Class
Now we have our game loop, let’s lay the ground work for drawing and updating a sprite (which we’ll cover in the next tutorial). To help us with that SFML provides something called a [sf::RenderWindow](https://www.sfml-dev.org/documentation/2.4.2/classsf_1_1RenderWindow.php#details). SFML defines a RenderWindow as a “[Window](https://www.sfml-dev.org/documentation/2.4.2/classsf_1_1Window.php) that can serve as a target for 2D drawing”. So with that in mind we know that a RenderWindow can do everything the an SFML window can, plus it adds some 2D drawing features that will come in very handy shortly. Initialising a RenderWindow will create and display a window in your chosen OS that we can then place our sprites on; which is exactly what we need!

We’ll wrap this RenderWindow in our own class so we can extend its functionality in future. You’ll notice numbered comments in the code below, I will use these whenever I want to discuss a line in more detail. Create a **Window** class:

**Window.hpp:**
```cpp
#ifndef Window_hpp
#define Window_hpp

#include <SFML/Graphics.hpp>

class Window
{
public:
    Window(const std::string& windowName);

    void Update();
    
	void BeginDraw();
    void Draw(const sf::Drawable& drawable);
    void EndDraw();

    bool IsOpen() const;

private:
    sf::RenderWindow window;

};

#endif /* Window_hpp */
```

**Window.cpp:**
```cpp
#include “Window.hpp”

Window::Window(const std::string& windowName) 
	: window(sf::VideoMode(800, 600), windowName, sf::Style::Titlebar) // 1
{
    window.setVerticalSyncEnabled(true); // 2
}

void Window::Update()
{
    sf::Event event; // 3
    if (window.pollEvent(event))
    {
        if (event.type == sf::Event::Closed)
        {
            window.close();
        }
    }
}

void Window::BeginDraw() // 4
{
    window.clear(sf::Color::White);
}

void Window::Draw(const sf::Drawable& drawable)
{
    window.draw(drawable);
}

void Window::EndDraw()
{
    window.display();
}

bool Window::IsOpen() const
{
    return window.isOpen();
}
```

**1.** The RenderWindow constructor accepts a [sf::VideoMode](https://www.sfml-dev.org/documentation/2.4.2/classsf_1_1VideoMode.php) as a parameter. The VideoMode can be use to define the width, height, and depth of the window. We are currently creating a non-fullscreen window with a resolution of 800 x 600 pixels, although this will change later as we’ll eventually want to make the window full-screen and user adjustable. RenderWindow also accepts a[sf::Style](https://www.sfml-dev.org/documentation/2.4.2/) parameter; which is an enum and includes options for showing the title bar (an option we are currently using), resizing the window, and whether the window starts fullscreen.

**2.** Vertical Sync, often referred to as Vsync, allows a player to sync the frame rate of the game to the refresh rate of the monitor. It does this by reducing the frame rate, as unfortunately it cannot increase the frame rate. Consequently there will be a dip in the frame-rate with this setting turned on (unless your frame-rate happened to already sync with the monitor, unlikely but not impossible). Whilst it has its drawbacks, Vsync should help reduce visual artefacts caused by the graphics card rendering individual frames faster than a monitor can draw them, resulting in weird graphical glitches. So it’s a trade off between a games FPS (frames per second) and possible graphical errors. Eventually we will want this setting to be able to be changed by the player (you’ll often see a Vsync setting in many modern games) but for now we’ll leave it hard-coded.

**3.** In the Windows update method we listen for a close event and if received we close the window. This allows the player to quit the game with cmd-q on Mac and alt-f4 on Windows and Linux. You may be wondering why this is required; surely when the player attempts to close the window, we’d want the window to actually close? But that is not always the case, in fact in future we will want to do a number of things before closing the window; for example: we could show the player an ‘Are you sure you want to quit?’ option or we could save the players current progress. We will be writing our own event system in future so I will go into much more detail on the topic but for now it’ll be good to know a couple of SFML event specifics:
- [sf::Event](https://www.sfml-dev.org/documentation/2.4.2/classsf_1_1Event.php#details) class is a union so only one of its members is valid at one time. As all members share the same memory space,** **we need to test the event type to make sure we do not attempt to access invalid memory.
- pollEvent returns true if an event has occurred and fills the event with the relevant data (as the event object is passed by reference).
We will only rely on this event system for specific window events. All other game events will be handled by our own event system that we will write in a future tutorial.

**4.** Many graphics packages require the user to call a begin and end draw method before and after drawing; and SFML is no different. The BeginDraw method clears the screen to a uniform colour, without this call you’ll see all previously drawn frames; and the EndDraw method is responsible for  displaying the items we have requested to draw.

## Updating the Game Class
Lets update the game class to take advantage of our new window class:

**Game.hpp:**
```cpp
#include “Window.hpp”

class Game
{
…

private:
    Window window;
};
```

We need to initialise and update the window in Game.cpp:

**Game.cpp:**
```cpp
Game::Game() 
  : window(“that game engine”) // You can call the window anything you like. 
{
…
}

void Game::Update()
{
    window.Update();
}

void Game::Draw()
{
    window.BeginDraw();
    
    // We’ll add draw code here.

    window.EndDraw();
}
```

Also seeing as we should really allow any future players of our game to actually quit, we can also use the window to decide whether the game is running:

**Game.cpp:**
```cpp
bool Game::IsRunning() const
{
    return window.IsOpen();
}
```

Now, when the project is run you’ll be greeted with a window! It may currently only be a white-filled screen but it’s a start.

If you’ve got this far then congratulations! We have begun to lay a solid groundwork for a game engine, which we will extend in future tutorials. If you have any questions or suggestions then please let me know in the comments.

As always, thank you for reading 🙂
