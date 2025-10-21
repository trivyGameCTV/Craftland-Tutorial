# Scene Editor

This article will provide an instructional reference related to the Scene Editor.

# Overview 

![image-20240725155010417](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725155010417.png)

1. Objects Selector: Select the objects to be placed in the Scene from the Object Selector.
2. Hierarchy Menu: displays all editable objects in the Scene in a hierarchical manner. 3.
3. Overview: Displays the files of the current editable file type in the project. In the context of this article, all Scene files are displayed.
4. Scene Editor: the canvas for scene editing, adjusting object placement, and previewing scene performance.
5. Properties Menu: Edit the properties of specific objects.

# Object placement 

## Placing a single object 

Drag an object from the Object Selector to the Scene to create a corresponding object at the specified location: 

![image-20240725164124627](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725164124627.png)

Right-click on the object. You can also create an object to the Scene. Objects created this way are placed at world coordinates (0,0,0).

## Continuous Object Placement 

Click in the Object Selector and move the mouse to the Scene Editor.

Follow the instructions below: 

![image-20240725164648315](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725164648315.png)

1. each time. click will place one of the objects at the current location. 2.

2. Holding down the left mouse button and dragging will create the object continuously. Can only be created on the X and Z axes.

![image-20240725164807468](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725164807468.png)

3. Use the ZXC shortcut to quickly flip the object along all three axes. Flip 90 degrees along that axis at a time.

![image-20240725164859270](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725164859270.png)

4. Press the right button to to exit the current object placement mode.

With Ctrl+D, you can make a copy of the currently selected object with the same transform information as the current object.

The transform information is the same as the current object. 
[image-20240725173803096](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725173803096.png)

## Delete Objects 

Select the object you want to delete in the Scene or Hierarchy menu, use the shortcut Delete to delete it: 

![image-20240725165024202](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725165024202.png)

![image-20240725165036256](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725165036256.png)

You can also delete a specific object via the Hierarchical menu right-click to delete the specified object: 

![image-20240725165150327](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725165150327.png)

![image-20240725165123917](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725165123917.png)

# Lens Manipulation

You can view the placement of objects in the Scene through lens manipulation.

1. Hold down the middle mouse button to move the camera in the current plane. 2.

2. Use the mouse wheel to zoom the camera. 3.

3. Hold down the right mouse button, you can operate the camera to move.
1. Hold down the right mouse button and drag the mouse to rotate the camera view. 2.
2. Hold down the right mouse button and use the WASD shortcut to move the camera.
3. Hold down the right mouse button and use the QE shortcut key to raise or lower the camera.
4. Holding down the right mouse button and holding SHIFT will allow the camera to move faster.

![image-20240725165703729](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725165703729.png)

> Holding down the mouse Resident instructions when adjusting the camera with the right mouse button.

In the menu in the upper right corner, you can adjust the camera's default shift speed: 

![image-20240725165748269](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725165748269.png)

# Adjust objects

## Adjust mode 

![image-20240725172213806](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725172213806.png)

Using the shortcut keys QWER or select it in the menu to access the four modes of adjusting objects.

Q: Selected, clicking on an object selects it and dragging it automatically places it on the first plane directly below it.

![image-20240725170104849](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725170104849.png)

![image-20240725170140116](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725170140116.png)

W: Move. Select an axis to drag and the object will only move along that axis. Drag on a plane and the object will only move on that plane.

![image-20240725170246647](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725170246647.png)

E: Rotate. Select an axis and drag, the object will only rotate in that direction.

![image-20240725170541650](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725170541650.png)

![image-20240725170553003](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725170553003.png)

R: Scale. By selecting an axis and dragging, the object will only be scaled in that axis dimension.

![image-20240725170647373](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725170647373.png)

![image-20240725170659136](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725170659136.png)

When resizing an object , if the selection is a parent object or plural objects, then they are all affected. If a child object is selected, the parent object is not affected.

![image-20240725171547275](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725171547275.png)

![image-20240725171316745](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725171316745.png)

## Auxiliary Icon control 

![image-20240725172150602](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725172150602.png)

In Scene Place two cubes for easy illustration: 

![image-20240725170806866](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725170806866.png)

In the hierarchy combine the Merge the two cubes into one object, with the left side as the parent and the right side as the child.

![image-20240725170845962](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725170845962.png)

### pivot /Center 

In pivot mode, the secondary icon appears on the selected object.

![image-20240725171103534](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725171103534.png)

![image-20240725171639319](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725171639319.png)

When you select plural objects, the helper icon will appear on the first selected object.

![image-20240725171141407](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725171141407.png)

In center mode In center mode, the helper icon appears at the center of the object, which is automatically calculated by the program for multiple objects: 

![image-20240725171623072](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725171623072.png)

> when the parent object is selected

 ![image-20240725171709327](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725171709327.png)

> When the child object is selected 

### Game Object/World Space 

When in game object mode, the axis of the helper icon is local, and will change orientation with the game object.

![image-20240725171908914](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725171908914.png)

![image-20240725171926946](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725171926946.png) 

When in world space mode, the axis of the secondary icon will always be the world axis, and will not change orientation with the object.

![image-20240725172056567](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725172056567.png)

## Grid 

![image-20240725172130102](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725172130102.png)

Grids are only available for the It has no effect on pure models and imported resources.

When mesh is enabled, moving an object will cause the mesh to appear at the current level and the object will automatically attach to the center of the green mesh.

![image-20240725172411452](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725172411452.png)

## Align 

![image-20240725172507155](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725172507155.png)

Alignment Options When turned on, you can configure the granularity of movement, rotation, and scaling. Objects will only change the configured scale one at a time.

![image-20240725172611754](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725172611754.png)

**Movement: **The axial configuration can be turned on or off with the button on the right, on to specify the distance to move each time on each axis, off to move in any direction. The unit is meters. This configuration only takes effect for move mode, fast moves in selected mode are not affected.

**Rotation:** The angle of change per rotation.

**Scale:** The magnification of the zoom change per adjustment.

## Property Adjustment 

In addition to the above functions, the transform component at the property menu records the specific data of the current object's position, rotation, and scaling. You can adjust the parameters of this component directly to achieve the precise adjustment of the object.

![image-20240725173052651](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725173052651.png)

# Scene Files Manage 

In the Overview, you can view all Scene files.

![image-20240725173111010](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725173111010.png)

The name of the Scene file, i.e. the name of the Scene file that references it. name, i.e. the name of the scene when it is referenced, without the .scene suffix. 

Right-click on a non-default Scene to set a Scene as the default Scene, which is the one that is loaded by default when you enter the game, and the game always needs a default Scene.

![image-20240725173540067](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725173540067.png)
