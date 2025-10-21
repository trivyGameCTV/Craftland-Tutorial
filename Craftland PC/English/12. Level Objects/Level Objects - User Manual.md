# Level Object

Level objects are important components of a level. In order to make it easier for you to build levels faster, we have provided some templates for level objects. They are divided into the following categories: 

1. Functional level objects, such as tires and portals that bounce the player. 2.
2. structural objects.
3. decorative objects.

An object can have more than one of the above functions, for example, a tire can be used as a springboard to reach the second floor as well as a decoration. It depends on your design.

In the object selector, we have categorized the level objects for you so that you can find them faster: 

![image-20241017184403051](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20241017184403051.png)

1. Basic structures.
2. Objects with functionality, which come with default logic and can be further configured to adjust the functional performance.
3. Modular components that can be used to build stylized buildings.
4. Prefabricated buildings.
5. Scene props such as furniture and facilities.
6. Plants, stones and other natural Scene props.

Next, we will introduce some ways to build objects and how to use them in important levels.

# General - Object Building Methods 

This section describes how to build and manage objects. You can also use your own familiar methods for level editing and management.

## Height Alignment 

When building with infrastructure components, it is recommended to use Scene drag+transform to adjust the position and height of each object.

For example, in the image below, we use a staircase and a platform, but the platform is placed on the ground by default, so we need to raise the platform to the height of the end of the staircase.

![image-20240730112913152](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240730112913152.png)

First, make the platform a child of the staircase, so that the platform's transform position is relative to the staircase: 

![image-20240730113341339](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240730113341339.png)

![image-20240730113432881](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240730113432881.png)

Adjust platform height to try to align: 

![image-20240730113620766](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240730113620766.png)

Found that the height of the platform relative to the stairs is very close to 1. Guessing that the height of the end of the stairs is 1, set the platform height to 1. Then align the horizontals.

![image-20240730113845655](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240730113845655.png)

## Horizontal Plane Editing 

When there are multiple heights of planes to edit in the vertical direction, you can use the editor's auto-grounding feature by placing an auxiliary geometry to simplify adjusting the heights.

For example, in the stair landing scene just described, if you want to continue editing a plane with height 1, you can add a plane geometry: 

![image-20240730114536164](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240730114536164.png)

> It is also possible to use any object with a flat surface as a reference, although you will need to fine-tune the height of the reference when using objects with thickness. The planes in the geometry are planar colliders with no thickness, which are ideal for use as references.

Assuming you want to edit an area of 10*10, set the plane's scale to (10,1,10)and its height to 1, then drag the plane horizontally into the area you want to edit: 

![image-20240730114856205](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240730114856205.png)

At this point, a ground of height 1 has been created within the plane, and dragging an object onto this ground or using the Q shortcut key to quickly move an object onto this ground will automatically set the object height to the ground height: 

![image-20240730115012293](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240730115012293.png)

Delete this reference or set it to inactive at the end of editing.

![image-20240730115103394](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240730115103394.png)

## Hierarchy Management 

Typically, there will be a considerable number of objects on a Scene, and it is recommended to use Hierarchy Management to group objects and improve maintainability.

Objects can be organized in a way that is appropriate to their function, region, etc.

![image-20240730120020232](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240730120020232.png)

> Rename objects to more accurately find their counterparts 

# Base Structures 

Base Structures are purely structural objects with little to no functionality. They allow you to put together custom level structures to act as blocks, platforms, bunkers, etc. on the map.

![image-20241017184854172](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20241017184854172.png)

![image-20240730112025437](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240730112025437.png)

> A simple stair platform.

For an assembled custom structure group, it is recommended that you stow the corresponding objects under a parent object in the depth for easy management and fine-tuning: 

![image-20240730112557694](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240730112557694.png)

> Here is the staircase as the parent object. You can also create a new empty object as the parent, choose any suitable object as the parent, or further manage the child objects in the hierarchy as appropriate.

If this struct group will be heavily reused, you can set it to Prefab. by dragging it from the depth to the asset directory: 

![image-20240730120334320](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240730120334320.png)

![image-20240730120342913](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240730120342913.png)

A group of this structure can be quickly created by dragging the prefab into the Scene.

![image-20240730120413788](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240730120413788.png)

> Direct editing of a Prefab affects all objects that use the Prefab, while editing object instances does not affect the Prefab. 

# Birth Points 

A birth point is the location where the player is born when they enter the game. If there is no birth point on the Scene or no suitable birth point, the player will be born near (0,0,0).

![image-20240730164820463](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240730164820463.png)

The scrolling arrow on the birth point points to the front of the birth point. It is also the orientation of the player born on this birth point.

The birth point has two unique configurations that hold the number of people, and the teams they belong to: 

![image-20240730165045467](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240730165045467.png)

**Holding Number:** determines the number of births that the birth point can hold at the same time.

**Owned Teams:** determines the teams that the players who can be born at that birth point belong to. If not configured as all teams, only one team can be selected.

After the affiliation team is configured to a specific team, the birth point will display the configured team in the Scene.

![image-20240730165638821](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240730165638821.png)

The birth point supports configuring plural to the Scene.

# Combat Props 

Level Objects There are two ways to generate props at a given location: generators and units.

Using generators to generate weapons or props can be set to refresh every round, but only the type can be specified. If the last generated item has not been removed during the refresh, it will be replaced with the newly generated item.

Use units to place weapons or props, you can set the exact weapon or prop to be generated, by default only one copy of the corresponding prop will be generated.

## Generator 

![image-20240730180747977](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240730180747977.png)

![image-20240730180753598](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240730180753598.png)

Select the corresponding generator according to the type, take weapons as an example: 

![image-20240730181011764](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240730181011764.png)

In the configuration you can choose the type of weapon to generate: 

![image-20240730181034487](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240730181034487.png)

In the reset per round component you can set whether this generation point will be refreshed at the start of each round.

![image-20240730181104786](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240730181104786.png)

In particular, when choosing to generate a weapon, a matching set of ammo and accessories will be generated.

## Units 

![image-20240730175100849](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240730175100849.png)

Use the weapons and props in the unit to generate a configured weapon or prop at the specified location.

![image-20240730175225713](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240730175225713.png)

Props placed in this manner can have their properties modified: 

![image-20240730184405465](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240730184405465.png)

![image-20240730184527556](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240730184527556.png)

# Safe Zone objects 

![image-20240730184633593](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240730184633593.png)

Using a Safe Zone object creates both a Safe Zone start object and a Safe Zone end object.

![image-20240731102628767](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240731102628767.png)

> Safe Zone start point object 

![image-20240731102651732](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240731102651732.png)

> Safe Zone endpoint object 

The Safe Zone changes from the range and position of the start point to the range and position of the end point at an even rate, as configured. There is no limit to the range or position of the start and end points, and you can make the Safe Zone shrink, expand, or pan as required.

Both Safe Zone start and Safe Zone end objects can be configured with Safe Zone related configurations: 

![image-20240731111710404](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240731111710404.png)

> Their configurations are shared, and modifying one takes effect immediately for the other.

**Safe Zone Start Time**: After how long after the start of the round does the effect of the Safe Zone and the constant blood loss outside the Safe Zone take effect, in milliseconds.

**Shrink Duration**: how long after the turn the Safe Zone changes from its starting position and range to its ending position and range, in milliseconds.

**Damage Interval**: the interval between every two damages outside the Safe Zone, in milliseconds.

**Damage Value**: the amount of damage inflicted each time outside the Safe Zone.

**Safe Zone Close Time**: how long after the start of the round the Safe Zone disappears. If this time is less than the Safe Zone effective time, the Safe Zone will not appear at all, in milliseconds.

**Out-of-Zone Initial Radius**: the initial radius size of the Safe Zone in meters. Changing this setting allows you to observe changes in the range of the starting object in the Scene.

**Out-of-Zone End Radius**: The final radius size of the Safe Zone in meters. Changing this setting allows you to observe changes in the range of end point objects in the Scene.

**Start Shrink Time**: How long after the start of the round the Safe Zone starts to change, in milliseconds.

# Triggers 

Triggers are a class of level objects that will detect entities coming into their own range. They are often used to trigger events with specific conditions.

We provide some different shapes and basic triggers, and some triggers that are already functional.

![image-20240731145849536](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240731145849536.png)

Basic triggers differ only in shape and do not come with any logic. To use triggers to trigger specific events, you need to mount a script for the trigger and use the relevant event detection entity trigger on the trigger's script.

![image-20240731150111813](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240731150111813.png)

![image-20240731150310863](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240731150310863.png)

Triggers can detect both entities coming from outside into the trigger area and entities leaving the area. When player enters/leaves trigger events will only be triggered when a player entity enters/leaves the trigger, and when entity enters/leaves trigger events can be triggered by any entity, such as sensing mines.

These trigger events need to be used on the script that is mounted on the trigger.

The next section describes some triggers with functionality, you can also mount scripts on these triggers to handle additional logic, but they will always implement their own logic: 

## **Gravity change zone** 

![image-20240731154024959](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240731154024959.png)

Inside the gravity change zone, the gravity acceleration and jump height change to the set values. It is also possible to set whether the zone is visible or not.

## **Death/Invincibility Zone** 

![image-20240731154156220](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240731154156220.png)

can be set as a death zone or invincibility zone.

Players or AI entities that enter the death zone die immediately, and as with other instant-death logic, players or AI entities that are currently invincible are unaffected.

A player or AI entity that enters an invincibility zone gains invincibility until it leaves the invincibility zone. Leaving the invincibility zone clears the invincibility status, and even if other invincibility effects were previously gained, leaving the invincibility zone loses the invincibility effect.

You can set whether the zone is visible or not.

## **Rollover Trigger** 

![image-20240731154650753](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240731154650753.png)

Players can go over the flip trigger when it is entered in reverse. This is mainly used to go over obstacles such as windows.

The rollover trigger previews the direction of the rollover in Scene, and the player must be in the same direction as the rollover to trigger the rollover button. For i to achieve a two-way rollover, two of these triggers need to be set.

![image-20240731154924113](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240731154924113.png)

Allows you to set the height and distance for the rollover.

# Zombies 

Zombies are monsters with AI. You can use Zombie Spawn Points to continuously spawn zombies, or use Zombie Units to place specific zombies in the Scene.

![image-20240731160846972](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240731160846972.png)

![image-20240731160449497](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240731160449497.png)

Regardless of which way the zombies are generated, you can set the zombie type and properties.

![image-20240731161607670](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240731161607670.png)

For an introduction to AI Entities, you can refer to the AI Entities user manual: 

[This should be the link to the AI Entities documentation] 

Generators have some special settings compared to units: 

![image-20240731162000642](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20240731162000642.png)

**Zombies per wave**: number of zombies per generation.

**# of waves**: how many waves of zombies are generated per round when not continuously generated.

**Continuous**: continuous generation, ignore the number of generation waves setting and keep generating zombies.

**Start time**: how long after the round starts to start generating the first wave of zombies, in seconds.

**Wave Interval**: the length of time in seconds between every two waves of generated zombies.

Zombies generated by the generator will all be destroyed at the start of the next round and do not generate drops.

# Unit Generator

A unit generator is an object that can continuously generate units or prefabs in the scene according to the settings.

![image-20250122111711523](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20250122111711523.png)

A unit generator can choose to generate zombies, weapons or props on the scene, or it can choose prefabs to generate, but only one of them can be selected.

![image-20250122113035532](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20250122113035532.png)

The zombies, weapons, and props placed on the scene will be automatically added to the template selection panel

![image-20250122113626073](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20250122113626073.png)

![image-20250122113719384](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20250122113719384.png)

Prefabs require you to make or import them in advance. Prefabs for zombies, weapons, and props can all be used as generation templates.

![image-20250122114315229](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20250122114315229.png)

![image-20250122114337513](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/12-LevelObject/image-20250122114337513.png)
