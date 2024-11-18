# Terrain Editor - User Manual

This article provides instructional references related to the Terrain Editor.

## Terrain Objects

Terrain is a special scene object that allows you to create a custom surface. It is a plane with collision properties but no thickness.

If placed in mid-air, the terrain will be invisible from below, but its shadow will be visible.

![image-20240725181644841](./img/image-20240725181644841.png)

![image-20240725181631290](./img/image-20240725181631290.png)

As a scene object, terrain can be edited in the scene interface, but only its position can be changed.

![image-20240725181608654](./img/image-20240725181608654.png)

## Creating and Deleting Terrain

Select "New" in the terrain edit menu to enter pre-creation mode:

<img src="./img/image-20240725183119794.png" alt="image-20240725183119794" style="zoom:67%;" />

A blue terrain preview will appear in the scene:

![image-20240725183211959](./img/image-20240725183211959.png)

You can adjust parameters in the pre-creation interface or drag the blue sphere to adjust the size and position of the terrain:

![image-20240725183258302](./img/image-20240725183258302.png)

The position of the terrain can be changed later, but its size and aspect ratio cannot be altered once set.

Select the terrain area and use the Delete shortcut key or the hierarchy menu to delete the selected terrain area.

![image-20240725183456268](./img/image-20240725183456268.png)

## Sculpting

![image-20240725183543134](./img/image-20240725183543134.png)

Sculpting modifies the undulations of the terrain with four options: Raise, Lower, Smooth, and Flatten.

### **Raise**

![image-20240725185050088](./img/image-20240725185050088.png)

The brush raises the terrain it passes over. Continuously clicking a spot will keep raising it. Brush size affects the area raised per click or drag. Brush strength determines how quickly the terrain rises. Each piece of terrain has a maximum height limit; brush strength only affects how fast it reaches this limit.

![image-20240725183957835](./img/image-20240725183957835.png)

### **Lower**

![image-20240725185105397](./img/image-20240725185105397.png)

Opposite to Raise, the brush lowers the terrain it passes over. Similarly, there is a lower limit for how much the terrain can descend. Brush size affects the area impacted per click or drag, while brush strength influences how quickly it reaches the lowest depth.

![image-20240725184202194](./img/image-20240725184202194.png)

### **Smooth**

![image-20240725185121445](./img/image-20240725185121445.png)

This option adjusts the height of the affected area to match the average height of its surroundings for a smoothing effect. Brush size affects the area impacted per click or drag, while brush strength influences how quickly it reaches target height.

![image-20240725184503733](./img/image-20240725184503733.png)

![image-20240725184556242](./img/image-20240725184556242.png)

> As moving the brush affects terrain height, previously smoothed areas may generate new target heights. Repeated smoothing results in overall height changes, equal to all raised and lowered parts combined.

### **Flatten**

![image-20240725185135051](./img/image-20240725185135051.png)

Flattening sets affected terrain to a target height. The flatten target is this height. Brush size affects impact range per click or drag. Additionally, Flatten offers three modes:

![image-20240725185316005](./img/image-20240725185316005.png)

The first mode processes all terrain, the second only those above target height, and the third only those below target height.

![image-20240725185503304](./img/image-20240725185503304.png)

![image-20240725185516968](./img/image-20240725185516968.png)

## Painting

Painting offers two editing options: Vegetation Brush and Texture.

### Vegetation Brush

![image-20240725190347859](./img/image-20240725190347859.png)

Place decorative plants or rocks on the terrain.

Brush size affects grass and erasure, determining impact range per click or drag.

Brush density affects grass generation rate per click and during dragging.

![image-20240725190450551](./img/image-20240725190450551.png)

For trees and rocks, each click generates one object; dragging continuously generates objects.

![image-20240725190429926](./img/image-20240725190429926.png)

Hold Ctrl while using brush to erase selected plants from terrain; hold Shift to erase all vegetation or rocks touched by brush.

![image-20240725190509888](./img/image-20240725190509888.png)

Each type of decoration has a quantity limit with Vegetation Brush.

![image-20240725190534771](./img/image-20240725190534771.png)

### Texture

![image-20240725190548955](./img/image-20240725190548955.png)

Texture determines the appearance of the terrain itself.

![image-20240725190626742](./img/image-20240725190626742.png)

Edit alternative terrain textures through import, replace, or delete options.

![image-20240725190711520](./img/image-20240725190711520.png)

Brush size affects impact range per click or drag. Checking "Fill Entire Terrain" fills entire area with texture.

![image-20240725190736248](./img/image-20240725190736248.png)

Using new textures will overwrite old ones.

![image-20240725190918758](./img/image-20240725190918758.png)

## Terrain Property Settings

![image-20240725191508655](./img/image-20240725191508655.png)

Terrain has several properties:

**Position**: Overall position of the terrain.

**Decimation Ratio**: Reduces face count to improve performance, range 0.1–1; 1 means no decimation, 0.1 means faces reduced to 1/10th of default.

**Terrain File**: Each edited piece generates a file; modify files to apply settings from other blocks directly.

**Texture Pixels**: Pixels for each texture; changing one axis value alters another. Larger values mean denser terrain. For example:

In (1,1) case:

![image-20240725192200222](./img/image-20240725192200222.png)

In (3,3) case:

![image-20240725192303777](./img/image-20240725192303777.png)
