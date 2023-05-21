# ActionMap

### Introduction

The ActionMap class in Torque3D is a powerful tool that allows developers to manage and handle user input in their games. It provides a simple and flexible way to define keybinds and associate them with specific actions or functions within the game.

This documentation article will guide you through the various aspects of the ActionMap class, including its definition, setup, and usage for creating keybinds in your Torque3D game.

### ActionMap Class Overview

The ActionMap class is responsible for handling input events and mapping them to specific actions in the game. It acts as a repository for all the keybinds defined in the game and provides a straightforward interface to manage and process user input.

#### Key Terms

Before diving into the usage of the ActionMap class, let's familiarize ourselves with a few key terms:

1. **Command**: A command is a specific game function triggered by user input. It can be associated with one or more keybinds.
2. **Keybind**: A keybind maps a specific input event, such as a keyboard key or mouse button, to an action.
3. **Device**: A device refers to the input source, such as a keyboard or mouse, from which the input events originate.

### Setting up Keybinds with ActionMap

To create keybinds using the ActionMap class, you'll typically follow these steps:

1. **Create an ActionMap instance**: Instantiate an ActionMap object to define a new keybind mapping.
2. **Define commands**: Define the commands you want to associate with specific keybinds.
3. **Add keybinds**: Associate keybinds with commands by specifying the input events (e.g., keyboard keys, mouse buttons) and the associated commands.
4. **Enable the ActionMap**: Push the ActionMap onto the stack to start processing input events and triggering the associated commands.

#### Example Usage

Let's walk through an example of how to use the ActionMap class to create keybinds for movement in a game:

```cpp
// Step 1: Create an ActionMap instance
if(!isObject(moveMap))
{
   new ActionMap(moveMap);
}

// Step 2: Define key commands
moveMap.bindCmd(keyboard, "w", "moveForward();", "moveStop();");
moveMap.bindCmd(keyboard, "a", "moveLeft();", "moveStop();");
moveMap.bindCmd(keyboard, "s", "moveBackward();", "moveStop();");
moveMap.bindCmd(keyboard, "d", "moveRight();", "moveStop();");

// Step 3: Add keybinds

// Binding the arrow keys for movement
moveMap.bind(keyboard, "up", "moveForward();");
moveMap.bind(keyboard, "down", "moveBackward();");
moveMap.bind(keyboard, "left", "moveLeft();");
moveMap.bind(keyboard, "right", "moveRight();");

// Step 4: Enable the ActionMap
moveMap.push();

// Game functions called as commands by the keybinds
function moveForward(%val) {
   // Logic to move the player forward
}

function moveBackward(%val) {
   // Logic to move the player backward
}

function moveLeft(%val) {
   // Logic to move the player left
}

function moveRight(%val) {
   // Logic to move the player right
}

function moveStop(%val) {
   // Logic to stop the player's movement
}
```

In the example above, we first create an instance of the ActionMap class called `moveMap`. Then, we define commands using the `bindCmd` function, which associates the commands with specific input events. The `bindCmd` function takes the following parameters: the device (e.g., keyboard), the input event (e.g., "w" for pressing the 'W' key), and the command associated with the key press, and key release.

{% hint style="info" %}
Important terminology: When a key is pressed down, it is "made", and when i t is released, it is "broken". Handling the make and break states give more full control over your game inputs.
{% endhint %}

Next, we add additional keybinds using the `bind` function. In this case, we bind the arrow keys to the corresponding movement actions.

Once all the keybinds are set up, we enable the `moveMap` by calling the `push` method. This activates the ActionMap and allows it to start processing input events and triggering the associated commands.

The example also includes placeholder functions (`moveForward`, `moveBackward`, `moveLeft`, `moveRight`, and `moveStop`) that represent the game functions or behaviors called when the inputs are made or broken. These functions can be implemented with the specific logic needed for player movement in your game.

It's also important to note that modifier keys ( shift, alt, ctrl, etc) can be used in conjunction with a normal input event, and is treated as a separate input.

```cpp
moveMap.bind(keyboard, "shift w", "sprintForward();");

// This function is only called if shift + w is pressed. 
// If only w is pressed, then the above moveForward function is 
// still called as normal
function sprintForward(%val) {
    // Logic to move the player at a sprint
}
```

Next, we'll go into more detail about the different bind functions and how to utilize them.
