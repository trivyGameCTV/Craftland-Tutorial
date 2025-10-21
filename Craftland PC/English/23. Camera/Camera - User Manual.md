# Camera

Players use cameras to observe game matches. Using different camera modes and camera parameters can provide different game visual performances.

# Camera Module

The camera module is a default module and does not need to be loaded additionally.

![image-20240911182555100](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/23-Camera/image-20240911182555100.png)

You can configure the main camera in the camera module.

# **Camera Mode**

In the camera module, after selecting a camera mode, you can further set the parameters of the mode.

Among the parameters, there are some common parameters for some camera modes:

![image-20240911182613203](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/23-Camera/image-20240911182613203.png)

## General Configuration

**Camera rotation angle limit type**: If you choose to keep the original logic, the camera will limit the angle of rotation that the player can operate. If you choose WideRange, this limit will be relaxed.

**Field of view**: The angle that the camera can see.

![image-20240910155604898](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/23-Camera/image-20240910155604898.png)

**Occlusion Mode**: Except for the first-person camera, the way to deal with the situation when there is an occlusion between the camera and the player character. There are three modes: fixed, zoomed in, and perspective.

![image-20240910164055112](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/23-Camera/image-20240910164055112.png)

> At this point, if the camera continues to rotate, it will be blocked by the wall.

In fixed mode, even if there are occluders between the camera and the player character, they will not be processed.

![image-20240910164104396](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/23-Camera/image-20240910164104396.png)

In zoom mode, the camera will change its position and get closer to the player character as if it is squeezed by an obstruction.

![image-20240910164258233](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/23-Camera/image-20240910164258233.png)

In perspective mode, the player character will be marked with a red outline.

![image-20240910164454220](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/23-Camera/image-20240910164454220.png)

**Projection mode**: In perspective mode, the camera uses the same rule as in reality that objects are larger when they are near and smaller when they are far away. In orthographic mode, the camera does not use the rule that objects are larger when they are near and smaller when they are far away.

![image-20240910173104387](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/23-Camera/image-20240910173104387.png)

> Perspective Mode

![image-20240910173353307](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/23-Camera/image-20240910173353307.png)

> Orthogonal mode. Generally speaking, the orthogonal mode is suitable for situations such as horizontal scrolling games that have special requirements for the scene.

**Offset**: In cameras that support setting offset, the offset is (0, 0, 0) which is the initial default position of the camera. By setting this parameter, you can adjust the default position of the camera.

## Third Person Camera

The third-person camera is a certain distance away from the player, and the player character is rendered. In the default third-person camera mode, the player can rotate the camera freely, and the player's forward movement command will make the player character move in the direction the camera is looking.

![image-20240910170247388](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/23-Camera/image-20240910170247388.png)

![image-20240910170300191](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/23-Camera/image-20240910170300191.png)

> The player will turn in the direction of movement before moving forward.

###FF Classic

FF Classic is like the third-person camera in the FreeFire game. The parameters of FF Classic mode cannot be changed.

### Chasing Back

The back-chasing camera will always look at the back of the player. In this mode, the horizontal direction of the player character is always equal to the horizontal direction of the camera, and turning the camera will also turn the player character.

## First Person Camera

The position of the first-person camera overlaps with the player character, as if observing the game world from the player character's perspective. The default first-person camera does not support adjusting the field of view.

### New first-person resources

At the bottom of the mod, you can use the new version of the resources for the first person.

![image-20240911182655142](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/23-Camera/image-20240911182655142.png)

When the new first-person asset is checked, the camera will always show both hands, instead of only showing both hands when performing actions.

###FF Classic

The FF Classic first-person camera is consistent with the first-person perspective in FreeFire. The FF Classic first-person camera has a dynamic effect that changes the field of view when moving.

## Top-down camera

The top-down camera is always facing the horizontal plane by default, and will move with the player when the player moves.

![image-20240910175642062](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/23-Camera/image-20240910175642062.png)

## Horizontal camera

By default, the horizontal perspective camera will always face the positive Z axis of the world coordinate system and move with the player.

![image-20240910180227779](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/23-Camera/image-20240910180227779.png)

The horizontal camera has a unique configuration:

![image-20240911182724156](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/23-Camera/image-20240911182724156.png)

**Pitch angle and horizontal angle**: You can adjust the initial angle of the camera, and the camera will maintain this angle after configuration.

**Whether to allow player X-axis movement**: When turned on, the player's movement instructions to the inside and outside of the screen will be blocked, and the player can only move to the left and right sides of the screen.

## Free view camera

In free-view camera mode, the player's movement commands will operate the camera instead of the player character. By default, the vertical view control of the free-view camera is flipped.

![image-20240910180722654](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/23-Camera/image-20240910180722654.png)

## Custom Camera

Custom cameras will only follow the player and have no other functionality. Your configuration determines how the player behaves when using the camera.

![image-20240910181200118](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/23-Camera/image-20240910181200118.png)

# script

In addition to configuring the main camera, scripts can be used to dynamically adjust camera parameters, create or switch cameras.

![image-20240910190054154](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/23-Camera/image-20240910190054154.png)

## Create & switch camera

![image-20240910190216300](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/23-Camera/image-20240910190216300.png)

By creating a camera, you can create an additional camera, but it is not put into use and the player's camera will not change.

After creating a camera, you can adjust the camera's performance by setting its properties.

Use Switch Camera to switch to the specified camera, and the player will start using the new camera.

## Mask

The camera can selectively render objects or players on the map by modifying the mask level. All visible units have a visibility component.

![image-20240910190543378](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/23-Camera/image-20240910190543378.png)

Set the levels in the component, then modify the level in the camera's mask that the camera will render.

![image-20240910190647512](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/23-Camera/image-20240910190647512.png)

> By default, the camera will render all levels (0-15), and the picture shows that objects at level 1 are not rendered.

By modifying the mask level, you can achieve the purpose of hiding the visibility of specified category units, saving performance, etc.

However, even if the unit is invisible, other functions such as collision still exist, and the player will still be blocked by non-rendering level objects or trigger certain collision events.

# New custom camera

Different from the existing cameras, we provide a custom camera that is completely controlled by the player:

![image-20250630171808382](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/23-Camera/image-20250630171808382.png)

You can double-click the lower left preview to adjust the camera perspective.

![image-20250630172138151](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/23-Camera/image-20250630172138151.png)

In the script, the camera is controlled using a new API. Different from the old cameras, the new cameras are collectively called custom cameras:

![image-20250630172253596](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/23-Camera/image-20250630172253596.png)
