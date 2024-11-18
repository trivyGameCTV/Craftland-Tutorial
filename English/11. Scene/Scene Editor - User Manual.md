# Scene Editor - User Manual

This article will provide instructional references related to the scene editor.

## Overview

![image-20240725155010417](./img/image-20240725155010417.png)

1. Object Selector: Choose objects from the object selector to place in the scene.
2. Hierarchy Menu: Displays all editable objects in the scene in layers.
3. Overview: Displays the current editing file type in the project. In this context, it shows all scene files.
4. Scene Editor: Canvas for scene editing, adjust object placement, preview scene performance.
5. Attribute Menu: Edit specific object attributes.

## Object Placement

### Placing a Single Object

Drag an object from the object selector to the scene to create a corresponding object at the specified location:

![image-20240725164124627](./img/image-20240725164124627.png)

Right-click on an object to create an object in the scene. Objects created this way will be placed at world coordinates (0,0,0).

### Placing Objects Continuously

Click on an object in the object selector and then move the mouse to the scene editor.

According to the instructions below:

![image-20240725164648315](./img/image-20240725164648315.png)

1. Clicking once will place the object at the current position.
2. Dragging while holding down the left mouse button will continuously create the object. It can only be created along the X and Z axes.

   ![image-20240725164807468](./img/image-20240725164807468.png)

3. Use the ZXC shortcut keys to quickly rotate the object along three axes. It rotates 90 degrees each time.

   ![image-20240725164859270](./img/image-20240725164859270.png)

4. Right-click to exit the current object placement mode.

Pressing Ctrl+D allows you to duplicate a selected object with identical transform information.

![image-20240725173803096](./img/image-20240725173803096.png)

### Deleting Objects

Select the object to delete in the scene or hierarchy menu, then use the Delete shortcut key:

![image-20240725165024202](./img/image-20240725165024202.png)

![image-20240725165036256](./img/image-20240725165036256.png)

Alternatively, you can right-click on a specified object in the hierarchy menu to delete it:

![image-20240725165150327](./img/image-20240725165150327.png)

![image-20240725165123917](./img/image-20240725165123917.png)

## Camera Operations

Camera operations allow you to view the placement of objects in the scene.

1. Holding down the middle mouse button allows you to move the camera on the current plane.
2. Using the mouse scroll wheel enables you to zoom in and out with the camera.
3. Holding down the right mouse button lets you move the camera.
   1. Dragging with the right mouse button pressed allows you to rotate the camera view.
   2. Holding down the right mouse button and using WASD keys allows you to move the camera.
   3. Holding down the right mouse button and using QE keys lets you raise or lower the camera.
   4. Holding down Shift while moving with the right mouse button accelerates camera movement.

![image-20240725165703729](./img/image-20240725165703729.png)

> Permanent instructions for adjusting the camera while holding down the right mouse button.

In the top-right menu, you can adjust the default movement speed of the camera:

![image-20240725165748269](./img/image-20240725165748269.png)

## Adjusting Objects

### Adjustment Modes

![image-20240725172213806](./img/image-20240725172213806.png)

Use shortcut keys QWER or select from the menu to enter four adjustment modes for objects.

Q: Select - clicking on an object selects it, dragging it will automatically place it on a plane directly below.

![image-20240725170104849](./img/image-20240725170104849.png)

![image-20240725170140116](./img/image-20240725170140116.png)

W: Move - dragging along a coordinate axis moves objects only along that axis. Dragging on a plane moves objects only within that plane.

![image-20240725170246647](./img/image-20240725170246647.png)

E: Rotate - dragging along an axis rotates objects only in that direction.

![image-20240725170541650](./img/image-20240725170541650.png)

![image-20240725170553003](./img/image-20240725170553003.png)

R: Scale - dragging along a coordinate axis scales objects only on that axis.

![image-20240725170647373](./img/image-20240725170647373.png)

![image-20240725170659136](./img/image-20240725170659136.png)

When adjusting objects, if a parent or multiple objects are selected, they will all be affected. If a child object is selected, its parent will not be affected.

![image-20240725171547275](./img/image-20240725171547275.png)

![image-20240725171316745](./img/image-20240725171316745.png)

### Auxiliary Icon Control

![image-20240725172150602](./img/image-20240725172150602.png)

Placing two cubes in the scene for illustration purposes:

![image-20240725170806866](./img/image-20240725170806866.png)

In the hierarchy, merge two cubes into one object, with one on the left as a parent and one on the right as a child.

![image-20240725170845962](./img/image-20240725170845962.png)

#### Pivot/Center

In pivot mode, auxiliary icons appear on selected objects.

![image-20240725171103534](./img/image-20240725171103534.png)

![image-20240725171639319](./img/image-20240725171639319.png)

When selecting multiple objects, auxiliary icons appear on the first selected object.

![image-20240725171141407](./img/image-20240725171141407.png)

In center mode, auxiliary icons appear at the center of objects, automatically calculated by the program for multiple objects:

![image-20240725171623072](./img/image-20240725171623072.png)

> When selecting a parent object

![image-20240725171709327](./img/image-20240725171709327.png)

> When selecting a child object

## Game Object/World Space

When in game object mode, the coordinate axis of the auxiliary icon is in local coordinates and will change orientation with the game object.

![image-20240725171908914](./img/image-20240725171908914.png)

![image-20240725171926946](./img/image-20240725171926946.png)

When in world space mode, the coordinate axis of the auxiliary icon is always in world coordinates and will not change orientation with the object.

![image-20240725172056567](./img/image-20240725172056567.png)

### Grid

![image-20240725172130102](./img/image-20240725172130102.png)

The grid only affects official provided objects and has no effect on pure models or imported resources.

After enabling the grid, moving objects will snap to the green grid center on the current horizontal plane.

![image-20240725172411452](./img/image-20240725172411452.png)

### Alignment

![image-20240725172507155](./img/image-20240725172507155.png)

With alignment enabled, you can configure the granularity of movement, rotation, and scaling. Objects will only change according to the configured scale.

![image-20240725172611754](./img/image-20240725172611754.png)

**Move:** Use the buttons on the right to enable or disable axis alignment. When enabled, you can specify the distance moved on each axis, in meters. This setting only affects movement mode, quick movement in selection mode is not affected.

**Rotate:** The angle of rotation for each change.

**Scale:** The multiplier for each scaling adjustment.

### Attribute Adjustment

In addition to the above functions, the transform component in the attribute menu records specific data for the current object's position, rotation, and scale. You can directly adjust these component parameters to precisely adjust the object.

![image-20240725173052651](./img/image-20240725173052651.png)

## Scene File Management

In the overview, you can view all scene files.

![image-20240725173111010](./img/image-20240725173111010.png)

The name of a scene file is used as its reference name when included in a scene, without the .scene extension.

Right-clicking on a non-default scene allows you to set it as the default scene. The default scene is loaded when entering the game and there must always be a default scene.

![image-20240725173540067](./img/image-20240725173540067.png)
