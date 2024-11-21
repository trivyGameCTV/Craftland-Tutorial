# Player User Manual

## Introduction

The player is a crucial concept in the game. The default player comes with basic functions such as health, movement, and inventory. You can customize the player's functions, attributes, appearance, and actions through editing. This section introduces the player concept from the perspectives of player modules and player scripts. Player modules allow you to configure the player before the game starts, while player scripts enable adjustments during gameplay.

> Players exist in the game as instances of player entities, meaning edits in the module will reflect on every created player entity instance. For scripts, be mindful of whether they target a "specific player" or "all players."

## Player Modules

With player modules, you can set various attributes for players to start the game in your desired state. Player modules correspond to player entities, and modifications here will affect every created player in the game.

Access the player menu in Editor - Modules:

![image-20240717161934051](./img/image-20240717161934051.png)

![image-20240717161954648](./img/image-20240717161954648.png)

### Preset Player Types

Here, you can use custom player resources instead of the default appearance. This means you can change how players look and partially or fully use custom actions.

#### How to Create Player Data:

Create a new player data file in Project - Assets:

![image-20240717162245294](./img/image-20240717162245294.png)

The player data file contains models and action resources used by the player.

#### How to Edit Player Data:

First, prepare the required model and action resources. It is recommended to use character models that match the skeleton of the default model located at your local editor path \resources\LocalData\Utilities\UGC_Cos_Artist_Rig.

Add resources:

![image-20240717164312839](./img/image-20240717164312839.png)

Character model (example):

![image-20240717164533494](./img/image-20240717164533494.png)

Character action (example):

![image-20240717164606501](./img/image-20240717164606501.png)

Double-click the newly created player data file to open the editing page:

![image-20240717163241459](./img/image-20240717163241459.png)

1. Skeleton Data
2. Preview Window
3. Edit Window

First, in 3. Edit Window, select your desired character model and choose gender.

![image-20240717164733316](./img/image-20240717164733316.png)

![image-20240717164758088](./img/image-20240717164758088.png)

> You can also quickly modify the model by dragging it from the asset interface to 2. Preview Window.

![image-20240717164811925](./img/image-20240717164811925.png)

Here we use a female model as an example, so select female.

After adding the model, you can see its appearance in 2. Preview Window. For demonstration purposes, it's just a white model.

![image-20240717164935257](./img/image-20240717164935257.png)

You can zoom in/out with the scroll wheel and rotate the camera by holding the right mouse button to observe model details.

In the bottom left corner, add actions you want to preview with this model to see how they perform on it:

![image-20240717170419275](./img/image-20240717170419275.png)

![image-20240717170438547](./img/image-20240717170438547.png)

![image-20240717170500447](./img/image-20240717170500447.png)

The action preview window below now shows information about this action; click play to preview:

![image-20240717170539261](./img/image-20240717170539261.png)

In 1. Skeleton Data, you can view the skeleton structure of this model:

![image-20240717165024021](./img/image-20240717165024021.png)

Once your model is ready, add action types you need to modify in 3. Edit Window's Character Actions window, such as modifying run or idle actions. Unmodified actions will play default animations.

As a demonstration, we add an idle action:

![image-20240717170727102](./img/image-20240717170727102.png)

![image-20240717170749343](./img/image-20240717170749343.png)

<img src="./img/image-20240717171127990.png" alt="image-20240717171127990" style="zoom:50%;" />

Modify this action so when the game requires a standing idle animation for players, it plays your custom action.

For demonstration purposes only, we configure a run action on idle standing. Note that this will cause odd behavior; please add appropriate actions to suitable trigger scenarios according to your design during actual operations.

<img src="./img/image-20240717171339001.png" alt="image-20240717171339001" style="zoom:50%;" />

![image-20240717171400484](./img/image-20240717171400484.png)

This player data will modify players as follows:

1. Replace player model with a white female model.
2. Replace player's standing idle with a running action.

#### How to Add Player Data to Players:

Configure in modules to apply this player data to all players:

![image-20240717171630297](./img/image-20240717171630297.png)

![image-20240717171650842](./img/image-20240717171650842.png)

![image-20240717171559118](./img/image-20240717171559118.png)

In-game performance:

![image-20240717171913535](./img/image-20240717171913535.png)

> Everyone performs running actions when supposed to be standing idle without actual displacement occurring.

Other actions still play default animations for respective genders:

![image-20240717172007098](./img/image-20240717172007098.png)

> This is why using models with default skeletons is recommended; if not fully modifying actions, using non-standard skeletons for default animations results in very odd behavior.

If you only want specific players' data modified, achieve this through script-specific nodes:

![image-20240717172439514](./img/image-20240717172439514.png)

This node allows adding specified player data for specific players based on your needs or triggering under suitable conditions.

### Scripts

Scripts can be attached to player entities and will be mounted on each configured script during runtime.

![image-20240717183132809](./img/image-20240717183132809.png)

![image-20240717183155736](./img/image-20240717183155736.png)

You can add existing scripts or create new ones:

![image-20240717183212209](./img/image-20240717183212209.png)

![image-20240717183306034](./img/image-20240717183306034.png)

Refer below for script content related details under Player Scripts section.

### Basic Settings

Set basic attributes for players:

**Max Health:** Maximum health value for players ranging from 20–1000.

**Max EP:** Maximum EP value for players ranging from 0–200.

**Initial EP Ratio:** Initial EP possessed by players = Initial EP Ratio * Max EP ranging from 0%–100%.

**Movement Speed:** Scaling ratio of movement speed; less than 100% is slower than default speed while greater than 100% is faster than default speed ranging from 50%–500%.

**Jump Height:** Scaling ratio of jump height; less than 100% is lower than default height while greater than 100% is higher than default height ranging from 10%–500%.

**Respawn:** Checkmark enables automatic respawn after death along with additional respawn wait time configuration.

**Respawn Wait Time:** Only appears when respawn is checked; how long after death until respawning occurs ranging from 0–9999 seconds.

> Modifying movement speed and jump height changes initial move speed and jump height; player's default movement speed scaling/jump height scaling attributes remain at 1. Script modifications on these two attributes are based on module configurations for scaling adjustments.

### Combat

Set player combat attributes:

Damage Multiplier: The amount of damage dealt. Less than 100% means lower than default damage, more than 100% means higher than default damage. Range: 0%-500%.

Damage Taken Multiplier: The amount of damage received. Less than 100% means lower than default damage, more than 100% means higher than default damage. Range: 0%-500%.

> Similar to movement speed and jump height, modifying the damage multiplier and damage taken multiplier will change the player's initial damage and damage resistance. The player's default damage multiplier and damage taken percentage remain at 1. Modifying these two attributes in the script is based on scaling adjustments within the mod's configuration.

### Player Controller with Physics Effects

**Physics Layer:** Determines the physical layer the player is on. Whether collisions occur between different layers depends on the physics configuration.

Configure a non-default physics layer for the player:

![image-20240717181446557](./img/image-20240717181446557.png)

Disable collisions between the Custom layer and the default layer in the physics configuration:

![image-20240717181534541](./img/image-20240717181534541.png)

You'll find that players can pass through any object in the default physics layer without feeling it:

![image-20240717181631892](./img/image-20240717181631892.png)

Items that rely on collision triggers will not activate either:

![image-20240717181838784](./img/image-20240717181838784.png)

**Use Player Controller with Physics Effects:** Check to use a controller with custom physics effects and expand related configurations.

**Total Height, Including Upper and Lower Hemispheres:** The height of the character's capsule collider.

**Radius of Upper and Lower Hemispheres:** Capsule radius, cannot exceed half of the height.

**Mass:** Player mass.

**Maximum Slope Angle:** Slopes steeper than this angle cannot be climbed; the player will start to slide down.

**Step Vertical Offset:** Allows players to deviate from this configuration without leaving the ground or being blocked, commonly used when moving on stairs.

**Minimum Movement Distance:** If the distance the character controller needs to move is less than this value, the player will remain stationary.

**Skin Thickness:** The depth other objects can embed into the character collider, used to prevent jittering or getting stuck.

**Gravity Acceleration on Self:** Gravity acceleration experienced in three-dimensional directions. For players, this setting overrides global physics settings.

**Enable Custom Thrust:** When enabled, the force applied when pushing rigid bodies can be customized. Expand related configurations when enabled.

**Custom Thrust Force:** The magnitude of force applied when pushing rigid bodies.

**Multi-Jump Height:** The height of jumps during multi-jumping.

**Maximum Number of Multi-Jumps:** The maximum number of jumps supported per multi-jump.

**Airborne Movement:** When enabled, players can change movement speed and direction while in mid-air.

## Player Scripts

Scripts mounted in Module-Player are attached to each player. Be aware that global events may trigger multiple times contrary to design intentions.

Typically, we perform operations on players and their components in player scripts. By triggering private events, you can limit the range of triggered objects:

![image-20240717183020345](./img/image-20240717183020345.png)

For example, grant a respawned player an M4A1 upon revival.

![image-20240717173710229](./img/image-20240717173710229.png)

The private event "When Player Revives" triggers only when the current player entity revives.

Adding an item grants an M4A1 to this entity, which is the revived player itself, fulfilling the requirement.

> In actual editing, consider issues like whether weapon slots are full when adding an M4A1.

Using a public event "When Player Revives" will trigger corresponding logic for all players each time one player revives. Such logic is recommended to be placed in global scripts.

![image-20240717174549389](./img/image-20240717174549389.png)

> Configuring such a script on a player module will cause every player to receive an M4A1 each time any player revives.

![image-20240717174653796](./img/image-20240717174653796.png)

> Configuring such a script on a player module will cause the revived player to receive as many M4A1s as there are total players each time they revive.
