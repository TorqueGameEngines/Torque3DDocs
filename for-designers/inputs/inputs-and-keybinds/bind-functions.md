# Bind Functions

### Introduction

This article aims to provide a more detailed understanding of the key functions used with the ActionMap class: `bind`, `bindCmd`, and `bindContext`. These functions are essential for setting up keybinds and managing user input in your game.

### `bind` Function

The `bind` function is used to associate an input event with a specific action within the ActionMap. It allows you to define keybinds for various input devices such as keyboards, mice, or gamepads. The syntax for the `bind` function is as follows:

```cpp
bind(device, action, command);
```

* `device`: The input device for the keybind (e.g., `keyboard`, `mouse`, `gamepad`).
* `action`: The specific input event that triggers the action (e.g., a key name, mouse button name).
* `command`: The function or method that gets invoked when the input event occurs. In most cases, this is called twice: once when the key is pressed(make) and once when the key is released(break)

#### Example Usage of `bind` Function

Let's look at an example that demonstrates the usage of the `bind` function to set up a keybind for a specific action:

```cpp
// Binding the "F" key to the "interact" action
moveMap.bind(keyboard, "f", "interact");
```

In this example, the `bind` function is used to map the "F" key press event to the "interact" action. When the "F" key is pressed, the function `interact()` will be invoked.

Because the command is called when the input is made AND broken, the command is called with an argument to convey the key state, like in this example:

```cpp
function interact(%val)
{
    if(%val)
    {
        // Code for when the button is pressed down
    }
    else
    {
        // Code for when the button is releasedC
    }
}
```

### `bindCmd` Function

The `bindCmd` function provides a more flexible way to define keybinds by allowing you to specify different actions for key press, and key release. This function is particularly useful for actions that require different behaviors depending on the state of the key, but requires better control than the simple make/break state tracking of bind(). The syntax for the `bindCmd` function is as follows:

```cpp
bindCmd(device, action, pressCmd, releaseCmd);
```

* `device`: The input device for the keybind (e.g., `keyboard`, `mouse`, `gamepad`).
* `action`: The specific input event that triggers the action (e.g., a key name, mouse button name).
* `pressCmd`: The function or method invoked when the input event is initially triggered (key press / make).
* `releaseCmd`: The function or method invoked when the input event is released (key release / break).

#### Example Usage of `bindCmd` Function

Let's illustrate the usage of the `bindCmd` function with an example:

```cpp
// Binding the "Space" key to different actions based on the key state
moveMap.bindCmd(keyboard, "space", "jump();", "stopJump();");
```

In this example, the `bindCmd` function is used to map the "Space" key to different actions depending on the key state. When the "Space" key is initially pressed, the function `jump()` will be invoked. When the key is released, the function `stopJump()` will be invoked.

You may also note that the formatting of the commands is different compared to bind(). Whereas bind()'s command was simply the function name that is called back internally and the argument is passed for the make and break events, bindCmd explicitly defines to entire functional code statement called for the make/break states.

This allows you to pack in additional information as arguments, call multiple functions in one event, or more. This allows much more fine-tuned control over behavior when an input is made or broken.

### `bindContext` Function

The `bindContext` function allows you to define commands based on if the button is tapped, or held. The syntax for the `bindContext` function is as follows:

```cpp
indContext(device, action, holdFunction, tapFunction, holdTime);
```

* `device`: The input device for the keybind (e.g., `keyboard`, `mouse`, `gamepad`).
* `action`: The specific input event that triggers the action (e.g., a key name, mouse button name).
* `holdFunction`: The function or method invoked when the input event is held down for longer than the holdTime.
* `tapFunction`: The function or method invoked when the input event is held down for less than the hold time.
* `holdTime`: The amount of time in milliseconds to split between a tap and a hold.

#### Example Usage of `bindContext` Function

Let's consider an example to showcase the usage of the `bindContext` function:

```cpp
// Create a new context called "MainMenu"
moveMap.bindContext(keyboard, "c", "holdCrouch();", "toggleCrouch();", 500);

function holdCrouch() {
    // Logic for only crouched as long as the button is held down
}

function toggleCrouch() {
    // Logic for toggling crouched on and off perpetually
}
```

In this example, we define a keybind context for the "c" key. If the key is pressed and then releaed for less than the defined 500 millisecond hold time, then the toggleCrouch() function will be called. If it is held down for longer than 500 milliseconds, then the hold function is called.

It is important to note that the break status - releasing the key - is what dictates the context. If the key is released before the holdTime, it must be a tap. If it is held down for ANY period of time longer than the holdTime, including never being released at all, then the hold function is callled after the holdTime is passed.

Next, we'll go over how to manage multiple ActionMaps via the stack.
