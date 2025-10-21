# Terrain Editor

This post will provide instructional references related to the Terrain Editor.

# Terrain Objects 

A terrain is a special Scene object that creates a customized piece of ground. Terrain is a flat surface with collision, but no thickness.

If you choose to place it floating, you can't see the terrain from the bottom up, but you can see the shadow of the terrain.

![image-20240725181644841](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725181644841.png) 

![image-20240725181631290](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725181631290.png) 

As Scene object, terrain can also be edited in the Scene interface, but only the position can be changed.

![image-20240725181608654](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725181608654.png) 

# Create and Delete terrain 

Select new in terrain edit menu to enter pre-built mode: 

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725183119794.png" alt="image-20240725183119794" style="zoom:67%;" /> 

A blue preview of the terrain appears in Scene: 

![image-20240725183211959](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725183211959.png) 

The preview is available in the preview interface. You can adjust the parameters in the preview screen or by dragging the blue orb to adjust the size and position of the terrain: 

![image-20240725183258302](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725183258302.png) 

 Terrain Position The terrain position can be changed later, but the size and aspect ratio cannot be changed once they have been determined.

Selected terrain areas can be deleted using the shortcut Delete or in the hierarchy menu.

![image-20240725183456268](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725183456268.png) 

# Carve 

![image-20240725183543134](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725183543134.png) 

Engraving is a modification of the modification of terrain relief, there are four carving options: 

Raise, Lower, Smooth, Flat.

## **Raise** 

![image-20240725185050088](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725185050088.png) 

The terrain that the brush passes over will rise. terrain will be raised, and continually clicking on a spot will cause that spot to continue to be raised. Brush size affects how much the terrain is raised each time you click or drag it. Brush strength determines how fast the terrain is raised. There is a limit to how far each piece of terrain can be raised, and brush strength only affects the speed at which the maximum height is reached.

![image-20240725183957835](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725183957835.png) 

## ** Lower** 

![image-20240725185105397](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725185105397.png) 

As opposed to raise , the terrain that the brush passes through is lowered. Again, there is a lower limit for terrain descent. Brush size affects how far it affects when clicking or dragging, and brush strength affects how fast the minimum depth is reached.

![image-20240725184202194](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725184202194.png) 

## ** ** Smooth** 

![image-20240725185121445](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725185121445.png) 

Makes the brush affect the the height of the area is raised or lowered to the average of the surrounding heights to achieve a smooth effect. Brush size affects how far the area is affected when clicked or dragged, and brush strength affects how quickly the target height is reached.

![image-20240725184503733](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725184503733.png) 

![image-20240725184556242](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725184556242.png) 

> Because brush moves affects the height of the terrain, so terrain that has previously reached the smoothing target height generates a new target height, so the end result of repeated use of smoothing is a change in the overall height of the ground, with a value that is the sum of all the raised and landed parts.

## **Flat** 

![image-20240725185135051](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725185135051.png) 

Flat causes the the terrain affected by the brush becomes the target height, the leveling target is the target height, and the brush size affects the area affected when clicking or dragging. In addition, Flat provides three modes: 

![image-20240725185316005](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725185316005.png) 

The first will handle all terrain, the second will only handle those above the target height, and the third will only handle those below the target height.

![image-20240725185503304](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725185503304.png) 

![image-20240725185516968](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725185516968.png) 

# Drawing 

Drawing Two types of editing are available: vegetation brush and texture.

## Vegetation Brush 

![image-20240725190347859](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725190347859.png) 

On the terrain Place some decorative plants or rocks.

Brush size takes effect for turf and erasure, and determines how much each click or drag affects.

Brush density works on turf, and determines the amount of turf generated per click, and the rate of turf generation when dragging.

![image-20240725190450551](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725190450551.png) 

For trees and rocks, generate one corresponding object per click, and continuously generate the object when dragging.

![image-20240725190429926](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725190429926.png) 

When using brushes Ctrl will erase selected plants from the terrain, Shift will erase any vegetation or rocks the brush touches.

![image-20240725190509888](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725190509888.png) 

The vegetation brush has a limit on the amount of There is a limit to the number of each decoration.

![image-20240725190534771](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725190534771.png) 

## Materials 

![image-20240725190548955](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725190548955.png) 

The material determines how the appearance of the terrain itself.

![image-20240725190626742](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725190626742.png) 

With the Import, Replace, and Delete options to edit alternative terrain materials.

![image-20240725190711520](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725190711520.png) 

Brush Size Affects the area affected when clicking or dragging. Cover All Check this box to fill the entire terrain.

![image-20240725190736248](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725190736248.png) 

Using a new material will overwrite the old one.

![image-20240725190918758](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725190918758.png) 

# Terrain Properties Setting 

![image-20240725191508655](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725191508655.png)

Terrain has several properties: 

**Position**: where the terrain as a whole is located.

**Mesh Decimation**: you can improve the performance by reducing the number of surfaces of the terrain, the range is 0.1-1, 1 means no surface reduction, 0.1 means the number of surfaces is reduced to 1/10 of the default 

**Terrain File**: a terrain file will be generated for each terrain after editing, you can modify the terrain file to directly fetch the settings of the other terrains.

**Material pixels**: pixels of each material, change the value of any axis and the other axis will follow. The larger the value, the denser the terrain. Take the tablecloth material for example: 

(1,1) case: 

![image-20240725192200222](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725192200222.png) 

(3,3) case:

![image-20240725192303777](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/11-Scene/image-20240725192303777.png)
