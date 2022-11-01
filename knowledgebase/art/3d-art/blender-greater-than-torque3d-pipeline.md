---
description: >-
  This page will describe how to create a simple 3d asset in Blender3D and bake
  all textures to an ORM map for use in Torque 3D
coverY: -291.80616740088107
---

# Blender -> Torque3D Pipeline

### Blender Setup

Before we get started we need to setup a few things in Blender.

First go to Edit Preferences -> Add-ons and Enable the Node Wrangler addon

<figure><img src="../../../.gitbook/assets/image (30).png" alt=""><figcaption></figcaption></figure>

Then go to System and make sure you are setup properly for rendering in cycles

<figure><img src="../../../.gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>

Next save your preferences and close the preferences window.&#x20;

After this head to the render tab and setup the render settings as follows&#x20;

<figure><img src="../../../.gitbook/assets/image (9).png" alt=""><figcaption><p>Note for baking textures we do not need a high sample count. It rarely effects the quality of the texture.</p></figcaption></figure>

Clear your scene and save this file in your Modules Shapes folder (if a shapes folder does not exist yet create one )

### Modelling

For this tutorial we are going to create a simple coin shape.

Add a cylinder

<figure><img src="../../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

Scale it along the Z axis with S + Z and then apply the scale with Ctrl + A and select Scale.

<figure><img src="../../../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

Rotate the cylinder by 90 degrees on the X Axis so one of the faces at the top are now facing along the positive Y Axis by pressing R + X + 90

Next press TAB to enter edit mode, switch to face edit by pressing 3 or selecting the face symbol at the top <img src="../../../.gitbook/assets/image (15).png" alt="" data-size="line">. Select and delete the 2 faces.

<figure><img src="../../../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>

Next switch to edge edit mode ![](../../../.gitbook/assets/image.png) and press Alt and select anywhere in the edge left by deleting those face. Press Ctrl + F and select Grid Fill.

<figure><img src="../../../.gitbook/assets/image (24).png" alt=""><figcaption><p>Doing this gives us nice Quad geometry for these faces.</p></figcaption></figure>

Repeat for the other side.

To finish off our modelling phase, right click the object and choose Auto Smooth.

### UV Mapping

Next navigate to the top corner and drag over a new window and open up the UV Editor. Be sure to turn on UV Sync Selection

&#x20;![](<../../../.gitbook/assets/image (19).png>)

You should see a similar layout to this.

<figure><img src="../../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

Press the Y axis on the view gizmo so we are looking straight down the Y Axis ![](<../../../.gitbook/assets/image (31).png>)

Next select all the faces created by the Grid Fill and Press U to unwrap. Select Project from view.

<figure><img src="../../../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>

A new selection should appear in the UV Editor window. Move this selection and scale it so it fits in the bottom left corner of our uv space like so.

<figure><img src="../../../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>

Repeat this procedure for the other side so you end up with something similar to this&#x20;

<figure><img src="../../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

Next Select the Faces in the UV editor for the side of our cylinder and select the top menu UV and choose Average Island Scale

<figure><img src="../../../.gitbook/assets/image (4) (3).png" alt=""><figcaption><p>If this does not change anything straight away, change the settings of Average Islands Scale to Non-Uniform</p></figcaption></figure>

Scale these UVs now to fit inside our UV Space.

<figure><img src="../../../.gitbook/assets/image (22).png" alt=""><figcaption><p>I like to keep my UV's quite close together and now with this latest change they match the 3d space proportions for this object. The side doesn't have a lot of resolution in this image but our main focus is the front and back of our coin.</p></figcaption></figure>

### Baking Procedural Material

Now we can TAB out of edit mode and go to the materials tab.&#x20;

Add a new material and name it coin\_Mat

<figure><img src="../../../.gitbook/assets/image (18).png" alt=""><figcaption><p>Names of these material slots are referenced in Torque3D so it is always good practice to rename them to something relevant.</p></figcaption></figure>

Next set our 3D Viewport to viewport shading ![](<../../../.gitbook/assets/image (25).png>) and change our UV Editor window to the Shader Editor

<figure><img src="../../../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

