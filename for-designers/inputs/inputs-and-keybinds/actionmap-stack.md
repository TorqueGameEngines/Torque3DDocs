# ActionMap Stack

### Introduction

The ActionMap stack is a powerful mechanism in the Torque3D game engine that allows for the management of multiple ActionMaps. It provides a way to handle input events and callback functions based on the active ActionMap on the stack. This documentation article will guide you through the process of pushing and popping ActionMaps onto the stack and explain how the stack manages the engine's handling of input events and callback functions.

### ActionMap Stack Overview

The ActionMap stack is a Last-In-First-Out (LIFO) stack that holds multiple ActionMaps. The active ActionMap on the top of the stack determines how input events are processed and which callback functions are invoked. When an input event occurs, the stack is traversed from top to bottom, allowing the topmost ActionMap to handle the event first. If the event is not handled by the topmost ActionMap, it is passed down to the next ActionMap on the stack.

#### Stack Functions

To manage the ActionMap stack, the Torque3D engine provides the following functions:

* `push()`: Pushes the current ActionMap onto the stack, making it the active ActionMap.
* `pop()`: Removes the topmost ActionMap from the stack, reverting to the previous active ActionMap.

### Pushing and Popping ActionMaps

To manage multiple ActionMaps and switch between them, you can use the `push()` and `pop()` functions. These functions allow you to push a new ActionMap onto the stack or remove the topmost ActionMap from the stack, respectively.

#### Example Usage

Let's consider an example that demonstrates how to push and pop ActionMaps onto the stack:

```cpp
// Create two ActionMaps
new ActionMap(map1);
new ActionMap(map2);

// Set up keybinds for map1
map1.bind(keyboard, "w", "moveForward");
map1.bind(keyboard, "s", "moveBackward");

// Set up keybinds for map2
map2.bind(keyboard, "w", "strafeLeft");
map2.bind(keyboard, "d", "strafeRight");

// Push map1 onto the stack
map1.push();

// Handle input events and callbacks for map1
// ...

// Push map2 onto the stack
map2.push();

// Handle input events and callbacks for map2
// ...

// Pop map2 from the stack
map2.pop();

// Handle input events and callbacks for map1 again
// ...

// Pop map1 from the stack
map1.pop();
```

In this example, we first create two ActionMap instances: `map1` and `map2`. We set up keybinds for each ActionMap accordingly.

We then push `map1` onto the stack using the `push()` function, making it the active ActionMap. The engine will handle input events and invoke the appropriate callback functions defined in `map1`.

Next, we push `map2` onto the stack using `push()`, replacing `map1` as the active ActionMap. Now, the engine will handle input events and invoke the callbacks defined in `map2`.

In the example, map1 and map2 both define binds on "w". Because inputs are processed top-down, this means that when map2 is on the stack, it's bind is processed first, and strafeLeft() will be called.&#x20;

However, because map2 doesn't have a keybind for "s", map1's bind will continue to be in effect when the "s" key is pressed.

Later, we pop `map2` from the stack using the `pop()` function. This restores `map1` as the active ActionMap, and the engine will handle input events and callbacks defined in `map1` again.

Because map2 is no longer on the top of the stack, map1's "w" bind is in effect once more.

Finally, we pop `map1` from the stack, removing it from the stack entirely. At this point, there are no ActionMaps on the stack, and the engine will not process any further input events or invoke corresponding callbacks.

For a more practical example, below shows how you would have an ActionMap be pushed and popped from the stack based on a certain specific event. In the example, when a client connects or disconnects from the server, respectively:

```cpp
// Add the following code to your client-side Gamemode script

//This is called when a client connects to a server
function MyGameMode::onCreateClientConnection(%this)
{
   // Push the client's ActionMap onto the stack
   MyGameMoveMap.push();
}

//This is called when a client disconnects from a server
function MyGameMode::onDestroyClientConnection(%this)
{
   // Pop the client's ActionMap from the stack
   MyGameMoveMap.pop();
}
```

In this example, we have two event handlers for our GameMode object: onCreateClientConnection and onDestroyClientConnection.

When a client connects (onCreateClientConnection ), we  push the MyGameMoveMap ActionMap, which is defined in a different script file, onto the stack using the `push()` function, making it the active ActionMap for the client.

When a client disconnects (onDestroyClientConnection), we pop the client's ActionMap from the stack using the `pop()` function, reverting to the previous active ActionMap, if any. While we could also delete the ActionMap, it is normal to leave it in memory as we then don't need to recreate or or re-execute scripts in the event a player immediately joins another game.&#x20;

By using these event handlers, you can ensure that each client has its ActionMap with appropriate keybinds, and the ActionMaps are properly managed when clients connect or disconnect from the server.
