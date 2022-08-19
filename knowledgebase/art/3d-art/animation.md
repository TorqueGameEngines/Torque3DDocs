# Animation

#### Threads

Animation threads allow multiple sequences to play at the same time on a single shape. For example, a 'headside' animation could rotate the player's head to look at something at the same time as a running animation is playing. Each animation sequence is played using a _thread_. Threads for non-blend sequences are applied first (in order of increasing priority), then blend sequence threads are applied on top (in order of increasing priority). The following rules determine what happens when more than one thread controls the same node in the shape:

* If two non-blend sequences control the same node, the sequence with higher priority will animate it.
* If two non-blend sequences with the same priority control the same node, the thread that was created last will animate it.
* [Blend](https://web.archive.org/web/20200207192111fw\_/http://docs.garagegames.com/torque-3d/official/content/documentation/Artist%20Guide/Primer/torque\_art\_primer.html#ANIM\_BLENDS) sequences are applied on top of any previous thread, so if two blend sequences control the same node, _both_ will animate it (applied in order of increasing priority, or thread creation order if priority is the same).

Threads can be initiated from script as follows:

```
%obj.playThread( 0, "run" );	// play the "run" animation in thread slot 0
```

**See also**

* [ShapeBase TorqueScript reference](https://web.archive.org/web/20200207192111/http://docs.garagegames.com/torque-3d/official/content/documentation/Scripting/Advanced/ShapeBase.html)
* [Setting up threads in T3D Shape Editor](https://web.archive.org/web/20200207192111/http://docs.garagegames.com/torque-3d/official/content/documentation/World%20Editor/Editors/ShapeEditor.html)

\
\


#### Ground Transforms

Animation sequences that move the character should include a ground transform. This tells the engine how fast the character would move along the ground when the animation is played back at normal speed. In the case of a Player object, this allows Torque to scale the animation playback speed to match the in-game speed that the Player is moving. For example, if the model was animated such that it would normally move at 3 units per second, but in-game was moving at 6 units per second, then the animation can be played back at double speed so the feet do not look like they are skating along the ground. Another use for ground transforms is to automatically switch between walking and running animations based on the in-game velocity of the Player.

The exact details of how to export ground transforms will depend on the modeling package. In general, the animation should be created so the character moves through space, rather than running or walking in-place. Animate the bounds node to move with the character so there is no translation relative to the bounds node. On export, the ground transform is determined by subtracting the movement of the bounds node from the walking or running animation so that it will play in-place in Torque 3D.

**See also**

* [Setting up ground transforms in Milkshape3D](https://web.archive.org/web/20200207192111/http://docs.garagegames.com/torque-3d/official/content/documentation/Artist%20Guide/Exporters/ms2dtsplus.html)

\
\


#### Triggers

Triggers are arbitrary markers that can be used to call events on specific frames in a sequence. For example, a trigger can be responsible for generating footstep sounds and footprints when the feet hit the ground during walk and run animations. There can be up to 30 independent trigger states each with their respective on (1 to 30) and off (-1 to -30) states. You decide what each of those trigger states means. You should work with your programmer to define what the trigger states mean and how you should use them.

For example, you could have one trigger for each foot of a character that creates a footprint when the foot is down on the ground. Let's say that a triggerState of 1 is the left foot down and a triggerState of 2 is the right foot down. When the sequence plays the frame during which the left foot touches the ground, you could have a trigger on that frame that has a triggerState of 1 to create a footprint. You would then create another trigger with a triggerState of 2 for the right foot. You don't necessarily need to turn off the footprints (let's assume that the programmer will turn them off when it is necessary), but you could by creating two more triggers with triggerStates -1 and -2.

**See also**

* [Setting up sequence triggers in Milkshape3D](https://web.archive.org/web/20200207192111/http://docs.garagegames.com/torque-3d/official/content/documentation/Artist%20Guide/Exporters/ms2dtsplus.html)
* [Setting up sequence triggers in T3D Shape Editor](https://web.archive.org/web/20200207192111/http://docs.garagegames.com/torque-3d/official/content/documentation/World%20Editor/Editors/ShapeEditor.html)

\
\


#### Blends

Blend animations allow additive animation on the node structure of the shape. These will not conflict with other threads, and can be played on top of the node animation contained in other threads; such animations are relative. Blends only store the **changes** that occur over the course of the animation and not the absolute position of the nodes. This means that if a node is transformed by a blend animation, it includes only the transform information for that node, and it will add that transformation on top of the existing position in the base shape. Common uses for blend animations are facial expressions, head turning or nodding, and arm aiming.

\


Bear in mind that a blend can be played as a normal sequence, or it can be played on top of other sequences. When another sequence is playing, it will alter the root position, and the blend will be applied on top of that.

\


If you try to do a blend sequence where the root position is different than the 'normal' root (in the default root animation), you might expect that the blend will blend it to the new root (the position the character is positioned in during the blend animation). However, it does not work this way. Since nothing would actually be animating, it doesn't move the bones to the new position. What is contained in the blend sequence is only transform offsets from the blend sequence root position.

\


It is not a good idea to have a different root position in your 'normal' animations and your blends, as they can easily get out of sync.

\


The values added from the blend animation are based on the root position in the DAE/DTS/DSQ file. This root position does not have to be the beginning of the animation. You can pick any position for the blend animation to reference.

\


This is useful, because you can have a blend animation that can have a reference position that is the 'root' position. For animation like hip twists and arm movements (as in the 'look' animation), the character can be in a natural default state. In this way, you can have one animation control the character through the base pose to an extreme in either direction while referencing the default 'base' state, which will exist somewhere in the middle of the blend animation.

\


**See also**

* [Setting up blends in Milkshape3D](https://web.archive.org/web/20200207192111/http://docs.garagegames.com/torque-3d/official/content/documentation/Artist%20Guide/Exporters/ms2dtsplus.html)
* [Setting up blends in T3D Shape Editor](https://web.archive.org/web/20200207192111/http://docs.garagegames.com/torque-3d/official/content/documentation/World%20Editor/Editors/ShapeEditor.html)

\
