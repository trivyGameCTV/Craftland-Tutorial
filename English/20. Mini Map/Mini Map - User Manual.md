# Minimap

The minimap is a thumbnail of the entire game map, which can display the player's location and orientation in real time. It is used by players to locate themselves and other map information.

![image-20240906150001413](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/20-Minimap/image-20240906150001413.png)

A: The small, always-displayed minimap.

B: Detailed minimap that expands when you click on A.

1: The player himself, the direction of the arrow is the direction of facing, and the cone in front of the arrow is the player's field of view.

2: The player's teammate, the direction of the arrow is the direction of facing.

3: Objects on the map. The colored squares on the minimap that represent objects are called pixels.

4: Detected enemies, only displayed in thumbnail view.

The minimap always remains with the current player facing upwards, while the direction of the detailed minimap is fixed:

![image-20240906152758349](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/20-Minimap/image-20240906152758349.png)

After expanding the minimap, you can zoom in and out using the menu on the right:

![image-20240906151352112](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/20-Minimap/image-20240906151352112.png)

You can mark or unmark the minimap with the button at the bottom right:

![image-20240906151431011](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/20-Minimap/image-20240906151431011.png)

# Depth map

The default minimap supports the depth map function, which can mark objects with different colors based on their height.

In the Module - Mechanics parameters, you can find the Default Minimap category, which has a Depth Map switch function:

![image-20240906151823850](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/20-Minimap/image-20240906151823850.png)

If this option is deactivated, the objects on the map will be marked with the same color:

![image-20240906152838247](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/20-Minimap/image-20240906152838247.png)

With this option enabled, objects on the map are marked with different colors according to the surface with the highest collision body height:

![image-20240906153418258](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/20-Minimap/image-20240906153418258.png)

For a combination of multiple objects, the object with the highest collision surface is taken.

Combine the highest and lowest objects in the above figure, with the lowest object as the parent object, as shown:

![image-20240906153557081](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/20-Minimap/image-20240906153557081.png)

> You can see that objects in the lower position are considered to be in the upper position, and depth judgments are independent of parent-child relationships.

Keep the parent-child relationship above, but turn off the collision of the tallest block:

![image-20240906154136715](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/20-Minimap/image-20240906154136715.png)

> The larger the number behind the block, the higher the position of the block. The numbers only represent the ranking and do not indicate the absolute height.

![image-20240906154308434](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/20-Minimap/image-20240906154308434.png)

It is displayed as follows:

![image-20240906154330859](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/20-Minimap/image-20240906154330859.png)

You can see that the blocks that have been deactivated are no longer displayed on the minimap, and the lowest and highest groups are also handled as if they were the lowest blocks that still collide.

## Additional

1. The accuracy of the depth map is 1 meter.
2. Some objects will not be read by the minimap, such as basic white model objects:

![image-20240906154632909](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/20-Minimap/image-20240906154632909.png)

3. The depth map setting will also affect the depth representation of the objects marked on the custom minimap mentioned below.

# Custom minimap

You can customize the minimap background, other icons, and which objects to display.

To customize the minimap, you need to load the custom minimap module. The custom minimap module is an optional module. After uninstallation, the previously used content and blocks will become invalid.

![image-20240906154755924](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/20-Minimap/image-20240906154755924.png)

After enabling the custom minimap module function, the minimap will automatically display the custom minimap content. If the custom minimap has not been edited, it will appear as follows:

![image-20240906155033527](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/20-Minimap/image-20240906155033527.png)

## Custom mini-map properties

The custom mini-map has several properties

![image-20240912104416804](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/20-Minimap/image-20240912104416804.png)

**Center and map size**: The minimap is centered on a point in world coordinates and shows how much area is displayed on the map. The UI size of the minimap as seen by the player does not change, and the larger the map size, the larger the area represented by this fixed area of the minimap UI. If you are using a minimap background that depicts the terrain of the scene, the center and map size need to be adjusted to match the actual scene.

**Whether to enable depth map**: This property can be modified through the module configuration and can be modified dynamically within the script.

## Set mini-map icons

Blocks from the module can be used to add icons to the mini-map:

![image-20240906155247613](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/20-Minimap/image-20240906155247613.png)

The icon has the following properties:

![image-20240906160306780](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/20-Minimap/image-20240906160306780.png)

### Setting the background

By adjusting the depth and size of the icon, it can be used as a background.

We import a completely black image:

![image-20240906155316259](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/20-Minimap/image-20240906155316259.png)

Set the depth of this image to -1 and the scale to 10.

![image-20240906160602647](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/20-Minimap/image-20240906160602647.png)

### Setting high-interest units

You may want to highlight treasure chests and players of interest on the map. Use the follow target property of the icon to bind the icon to that object.

We add a vending machine to the map:

![image-20240906160856170](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/20-Minimap/image-20240906160856170.png)

and add a shop icon to it:

![image-20240906161046879](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/20-Minimap/image-20240906161046879.png)

Then add an icon for each other player that follows the player:

![image-20240906162117256](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/20-Minimap/image-20240906162117256.png)

This way, the shop on the map and the other players will be displayed:

![image-20240906162304786](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/20-Minimap/image-20240906162304786.png)

## Setting the pixels

As mentioned above, objects on the map are displayed as colored squares on the minimap. These squares are called pixels.

By default, no pixels are displayed in the custom minimap.

You can set which objects are displayed as pixels using blocks:

![image-20240906162503178](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/20-Minimap/image-20240906162503178.png)

Set all level objects to have pixels:

![image-20240906164411651](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/20-Minimap/image-20240906164411651.png)

![image-20240906164618061](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/20-Minimap/image-20240906164618061.png)

> The image shows the effect with the depth map setting enabled.
