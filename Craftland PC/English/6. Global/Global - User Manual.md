# Global

A global entity is a unique abstract entity that represents the entire game. As an abstract entity, it can only be edited in the module menu in the game editor. You can also use scripts to get the value of its properties or modify those that support modification.

In this article, we will introduce the global entity properties that you can modify in the module menu, and how to use global modules in block scripts.

# Modules

You need to edit global entities under the Module - Global menu.

![image-20240704143528399](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/06-Global/image-20240704143528399.png)

## Static ECA and script

![image-20240704143555568](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/06-Global/image-20240704143555568.png)

Both static ECAs and scripts attached to global entities can be considered global scripts. That is, as soon as the game starts, the attached script will run.

The difference is that once a static ECA is created, it will definitely be attached to a global entity.

![image-20240704145113663](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/06-Global/image-20240704145113663.png)

![image-20240704145152046](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/06-Global/image-20240704145152046.png)

The script can freely choose which one to use or unmount the mounted script.

Mount:

![image-20240704145405919](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/06-Global/image-20240704145405919.png)

![image-20240704145455936](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/06-Global/image-20240704145455936.png)

> Static ECA will not be displayed in the Select Script interface

![image-20240704145508122](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/06-Global/image-20240704145508122.png)

Uninstall:

![image-20240704145543549](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/06-Global/image-20240704145543549.png)

![image-20240704145555812](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/06-Global/image-20240704145555812.png)

Unloaded scripts are still in your project and can be attached to any supported entity or component.

In global scripts, we recommend that you perform initialization work, such as setting global variables and setting public functions.

## Custom room parameters

![image-20240704151437651](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/06-Global/image-20240704151437651.png)

Custom room parameters are a special type of custom property. They can be used as custom properties for global entities, and they can be modified after the room has been created but before the game starts. For example, this map can set the enemy's health to 50%-100%. You can customize a health parameter and set its value before entering the game.

Because custom room parameters are a type of custom property, creating a new room parameter is the same as creating a custom property for a global entity. They are both located in the game entity in the component:

![image-20240704151633519](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/06-Global/image-20240704151633519.png)

![image-20240704151709435](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/06-Global/image-20240704151709435.png)

![image-20240704151808250](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/06-Global/image-20240704151808250.png)

After you create a new custom property for a game entity component, it will first appear in the game entities below:

![image-20240704152004938](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/06-Global/image-20240704152004938.png)

Click the plus sign to the right of the Custom Room Parameters to set the property as a custom room parameter:

![image-20240704152052468](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/06-Global/image-20240704152052468.png)

Select the property and the property settings screen will appear:

![image-20240704152243864](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/06-Global/image-20240704152243864.png)

1. The property name, which cannot be edited in this screen.
2. The room parameter name, the name you want it to display in the room and the KEY for multilingual translation.
3. The parameter display method, the way you want this parameter to be displayed in the room. In this case, we want it to be an integer selected from 50 to 100.

![image-20240704152701834](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/06-Global/image-20240704152701834.png)

![image-20240704152715077](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/06-Global/image-20240704152715077.png)

You can right-click on the custom room parameter to reopen the editing screen or remove the parameter:

![image-20240704152746233](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/06-Global/image-20240704152746233.png)

Adding a custom property as a custom room parameter will prevent it from appearing in the game entity bar, while deleting a custom room parameter will cause the property to reappear in the game entity bar.

## Frame rate

![image-20240704153934174](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/06-Global/image-20240704153934174.png)

The frame rate bar only has one option: whether to enable low logic frame mode.

Our game's default logic frame is 30, which means that a logic check is performed 30 times per second, mainly affecting the “when updating” event in the script.

When low logic frame mode is enabled, the “when updating” event will only be executed 15 times per second.

> The “On Fixed Updates” node is not affected by this configuration and will always run 30 times per second

## Dynamic Navmesh

Navmesh is an automatic pathfinding system. It only takes effect on units that need to find a path, such as monsters, NPCs, or some skills that rely on pathfinding.

![image-20240704173040080](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/06-Global/image-20240704173040080.png)

When it is disabled, the path on the scene is automatically confirmed when the game starts, and the path will not be changed by the addition or removal of obstacles afterwards. If obstacles are dynamically created on the path, units may appear to pass through the obstacles directly.

When it is enabled, the game will identify the addition or removal of obstacles in the scene in real time, and dynamically modify the path of the automatic pathfinding.

Disabling this configuration means saving performance overhead.

## Match

![image-20240704173643976](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/06-Global/image-20240704173643976.png)

Initial player number: the game will start when the number of players matches the number of players in the match.

Prioritize Start with Full Team: If this box is ticked, the game will wait for the room to be full even if the number of players matches the number required for the game to start, for a certain period of time (around 10 seconds) after the match has started. After this time, the game will start as soon as the number of players matches the number required for the game to start.

Mid-game joining: Whether to allow players to join the game during play. If this is selected, further settings will be displayed:

![image-20240704182638421](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/06-Global/image-20240704182638421.png)

Time limit of mid-game joining: whether to limit the time for matchmaking. If enabled, the next configuration will be expanded to match the duration of matchmaking.
Duration of mid-game joining: how long is allowed for matchmaking after the game starts.
Mid-game joining player limit: whether to limit the number of matchmaking. If enabled, the next configuration will be expanded to accumulate the number of matchmaking.
Quota of joining mid-game: the maximum number of matchmaking supported.

Withdrawal
 allowed: Withdrawal is an action taken by the player. When enabled, the player will not be punished for withdrawing.

Disconnect reconnection disabled: When enabled, reconnection is disabled. When disabled, reconnection is enabled. When the game is closed and then opened again, the game will automatically reconnect by default.

## AFK & cheating

![image-20240704182345879](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/06-Global/image-20240704182345879.png)

Time of AFK: How long a player must remain inactive before being considered to have hung up. A player who is considered to have hung up will be kicked out of the game.

Turn on anti-hack feature: whether to enable anti-cheating.

# Script global module

In the block script, there is a global module that can perform certain operations on global mechanisms.

## Manipulate the poison circle

It is more like manipulating the safe zone than manipulating the poison circle.

![image-20240705150705190](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/06-Global/image-20240705150705190.png)

Enable Moving Safe Zone: The safe area smoothly moves to the focus from the starting point within the duration, and the radius gradually changes from the initial radius to the final radius. Players outside the safe area will take damage equal to the damage amount every second.
Turn on out-of-zone damage: The safe area is initially generated with a center point as the center and a set radius. After waiting for the configured duration, it smoothly moves towards the center point within the duration until it disappears. Players outside the safe area will take damage equal to the damage amount every second.
Turn off out-of-zone damage: Cancel the poison circle that continuously loses blood. This interface only closes the poison circle generated by the system and is invalid for the poison circle generated by the [custom safe area object] in the scene. However, the implementation of this interface is to create a huge safe area, so the player will be in the safe area and will not be harmed by other poison circles. Therefore, it is not recommended to use the system poison circle and custom safe area object at the same time.

Both the Move Poison Circle and Open Poison Circle interfaces set a new safety zone, replacing the previous one.
Both the Move Poison Circle and Open Poison Circle interfaces continue to execute downward once they start executing in the script. Please pay attention to the logic of the connection.

## Pause and resume the game

![image-20240705153104180](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/06-Global/image-20240705153104180.png)

These two nodes only affect the triggering of events when the fixed frame is updated.

![image-20240705153140762](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/06-Global/image-20240705153140762.png)

After suspending the game, the event is no longer thrown when the fixed frame is updated, and it continues to be thrown after the game resumes.

Pausing and resuming the game also trigger two separate events: one when the game is paused and one when the game is resumed:

![image-20240705153617815](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/06-Global/image-20240705153617815.png)

> The pause game command is invalid during a pause, and the same applies to resuming the game.
