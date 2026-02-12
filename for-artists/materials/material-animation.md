# Material Animation



IFL (image file list) and UV keyframed animations are deprecated in Torque 3D, but in most cases you can achieve an equivalent effect using Torque 3D animated materials.

**UV animation**

Simple UV animations can be achieved using the Rotate, Scroll and Wave animation features of Torque 3D Materials. The best place to experiment with these settings is in the [Material Editor](../../for-designers/editors/world-editor/material-editor.md).

|                           UV Rotate                           |                              UV Scroll                              |                         UV Wave (Scroll)                        |                                UV Wave (Scale)                               |
| :-----------------------------------------------------------: | :-----------------------------------------------------------------: | :-------------------------------------------------------------: | :--------------------------------------------------------------------------: |
| ![mat\_anim\_rot.gif](../../.gitbook/assets/mat_anim_rot.gif) | ![mat\_anim\_scroll.gif](../../.gitbook/assets/mat_anim_scroll.gif) | ![mat\_anim\_wave.gif](../../.gitbook/assets/mat_anim_wave.gif) | ![mat\_anim\_wave\_scale.gif](../../.gitbook/assets/mat_anim_wave_scale.gif) |

**Image Sequence animation**

Earlier Torque engines used IFL text files to specify a set of images with an optional number of frames to display each image. In Torque 3D, a similar effect can be achieved by putting all of the frames into a single texture, then setting the _sequenceFramePerSec_ and _sequenceSegmentSize_ fields of the Material (either manually, or via the [Material Editor](../../for-designers/editors/world-editor/material-editor.md)). For example, a 6-frame sequence, each frame sized 128x128 would be packed into a single texture of size 768x128.

![](../../.gitbook/assets/image_sequence.png)

The Material definition to display each frame for 1 second is shown below:

```
singleton Material(
{
   diffuseMap[0] = "art/shapes/examples/image_sequence";
   sequenceSegmentSize = 1 / 6;     // 1 / numFrames
   sequenceFramePerSec = 1;
};
```

![](../../.gitbook/assets/mat_anim_image_seq.gif)

There are two options available when UV mapping the model prior to export; neither work with tiled UVs.

1. UV map a single frame within the packed texture, and do not set the Scale bit in the Material animFlags. In the packed texture above, the U coordinate would be from 0.0 - 0.167. With this approach, the same packed texture can be used for UV mapping, however, the model will need to be remapped to change the number of frames in the sequence.
2. UV map the texture of a single frame only (or the entire packed texture), and set the Scale bit in the Material animFlags. In this case, the U coordinate would be from 0.0 - 1.0, and will be automatically scaled by Torque 3D to match the size of each frame in the packed texture. The advantage of this approach is that the number and size of the frames can be changed (by editing the texture, and modifying the Material parameters accordingly) without having to remap the model UVs.\
   Note: If you map the full 0.0-1.0 UV range but forget to set the Scale animFlag bit, the material will appear to scroll instead of flip between the image frames.
