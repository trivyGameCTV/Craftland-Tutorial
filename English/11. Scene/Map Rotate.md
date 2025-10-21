# Map Rotate

# Customize Map Rotation

Open *Bermuda.scene*

Under **Maps** entity, create a new empty object.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/1-FFA/maps.png">

Rename that new object to your desire map name. In this case, we will name it **New Map**

Under the **New Map**, create 1 basic block to be the map center, move that to the center of the map you want to created. Turn off the object activity status.

Under the **New Map**, create a new empty object, we will name it **Spawnpoints** to hold all the spawnpoints we want to create. Now add basic block to represent the spawn point position, move it to where you want players to spawn. Turn off the object activity status.

After that, the hierechy should look like this:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/1-FFA/hierechy.png">

Repeat the same step to create as much map as you want.

# Customize Map Border
Open *GlobalMap.eca*

In the **SetBorder** function, creator can customize *radius, damage, and duration* of the safezone.

In this case, duration is set to 999999, which mean the border will not move.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/1-FFA/border.png">

# Developing Tutorial
## Set Random Map
Create *GlobalMap.eca*

First, we need to take the map list from Bermuda.scene and store it in a variable. 

When match start, we get a random map to set it our Map for this session.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/1-FFA/set-random-map.png">
