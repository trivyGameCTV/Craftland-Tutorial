# Headshot Only template

# Configuration

## Adding new maps
In order to add a new map into the map, you must first construct the map. The map must consist of **2 spawn points**, one for each team, and **a ground** for the player to stand on. 

![adding-new-maps-1](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/HeadshotOnly/adding-new-maps-1.png)
![adding-new-maps-2](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/HeadshotOnly/adding-new-maps-2.png)

It is important to note that each spawn point must be renamed for easier identification and the **Team** value must be set to 4. 

![adding-new-maps-5](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/HeadshotOnly/adding-new-maps-5.png)

Next, navigate to the **Global Script** as so:
![navigate-to-global-script](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/HeadshotOnly/adding-new-maps-3.png)

In here, you can find the location to add new map. Through the **Init** function in the **Global Script**, you can find where you can use the **AddMap** function. 
![add-new-map-function](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/HeadshotOnly/adding-new-maps-4.png)

To briefly explain the paramaters of the AddMap function:  
1. **MapName**: define the name of the new map (Must be unique)
2. **SpawnPointT1**: define the spawn point entity of team 1
3. **SpawnPointT2**: define the spawn point entity of team 2

The name of the map can be any text you want. The spawn point must be chosen and input correctly. An example of which can be seen from the set of images below. 

![name-map-as-desired](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/HeadshotOnly/adding-new-maps-6.png) 

Click on the eyedropper to choose the corresponding map's spawn points. 
![choose-map](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/HeadshotOnly/adding-new-maps-7.png)

The final result should be similar to this. 
![final-result](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/HeadshotOnly/adding-new-maps-8.png)

That concluded the logic section of adding in new maps to the pool. You can decorate the map as much as you want to construct the map of your dream. 

## Configuring Unlimited Gloo Walls
Configuring whether the map has Unlimited Gloo Wall is very simple. 

First, navigate to **Setting**, then **Gameplay Settings**, then simply toggle the Unlimited Gloo Walls option to turn on or off the feature. 

![unlimited-gloo-wall](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/HeadshotOnly/unlimited-gloo-config-1.png)

## Configuring Headshot Only and Dropping Item on Elimination. 
In order to toggle Headsho Only and Dropping Item on Elimination, navigate to **Setting**, then **Gameplay Settings**, then **Edit Gameplay Rules**.

![navigate-to-config](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/HeadshotOnly/headshot-only-config-1.png)

Fron there, navigate to the **Property Settings** to find the **Headshot Only** and **Is Drop item** option. 

![navigate-to-property-settings](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/HeadshotOnly/headshot-only-config-2.png)

Adjust these features as you wish to turn on or off these features. 

# Script Explanation

All logic of the project can be found in the Global and Player entity. 

## Global script
The logic of the entire map revolves around the 2 main events: `On Game Start` and `On Round Start`. The main function of this script is to correctly distribute players between each spawn point, randomizing maps and configure new map to add to the game. 

### On Game Start
When game start, the map must be initialized. This is done through the `Init` function. 

![global-on-game-start-init](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/HeadshotOnly/global-on-game-start-init.png) 

> This function is also where users can add map through the `AddMap` functions. 

![global-add-map](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/HeadshotOnly/global-add-map.png) 

This function works by adding a tag to each map's spawn points. This map is inputed through the `MapName` parameter. All spawn points would then be added to the spawn point lists to be used later. 

As such, each map name must be unique in order for the system to work as intended. 

### On Round Start
![global-on-round-start](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/HeadshotOnly/global-on-round-start.png)  

Every round a new map must be chosen. The game entity must first choose a map name (MapTag) from a pool of maps in the `ChooseRandomMap` function.  
![global-choose-random-map](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/HeadshotOnly/global-choose-random-map.png)

The tag would then be registered as a used map. If the the number of items in the list of used tag exceed the number of items in the total tag list, the used tag list would be reset. 
![global-set-current-map-tag](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/HeadshotOnly/global-set-current-map-tag.png)

The player's spawn points would then be determined using the same tag. Specifically, the spawn point of team 1 and team 2 would be registered for later usage. 
![global-set-current-spawn](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/HeadshotOnly/global-set-current-spawn.png)

## Player script
The player script is mainly responsible for the **Headshot Only** logic, **Unlimited GlooWall** logic, **Equipment**, and **User Interface** 

### On Awake
Starting with when player is first created, some functions are executed immediately.  
![player-on-awake](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/HeadshotOnly/player-on-awake.png) 

First on the list is the `Init` function. This function turn on invincibility for player in the Lobby and register the player's team ID for futher usage.  
![player-init](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/HeadshotOnly/player-init.png)

`SetPlayerSetting` is a function that is used for configuring the players, preventing them from dropping items when eliminated and the **Headshot Only** logic for player. The headshot only is achieved through setting the player's **Damage Taken Percentage** value to an extremely small value, practically nullifying any damage to the player. Since we want to damage the player through headshot, we must adjust the player's **Headshot Damage Reduction** by the same amount to counteract the effect of the **Damage Taken Percentage**. 
![player-set-player-setting](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/HeadshotOnly/player-set-player-setting.png)

Next, `InitEquipment` will add GlooWall into the player's inventory. If Unlimited Gloo Wall option is not turned on in the setting, this Gloo Would still be available in player's inventory. Remove this if needed. 
![player-init-equipment](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/HeadshotOnly/player-init-equipment.png)

To reduce confusion for when player is being in the lobby, a notification is created through the `CreateStartNoti` function. 
![player-create-start-noti](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/HeadshotOnly/player-create-start-noti.png)


### On Round Start
When a new round start, the player would be teleported to the corresponding map and their UI will be adjusted.    
![player-on-round-start](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/HeadshotOnly/player-on-round-start.png)

As the name suggested, `TPToSpawn` will teleport the player to the correct spawn point that was obtained through the Global script. 
![player-tp-to-spawn](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/HeadshotOnly/player-tp-to-spawn.png)

The `CreateHSOnlyNoti` will then notify player if the currently mode is Headshot Only or not. If the map is configed to be normal, then this notification will not appear. 
![player-create-hs-only-noti](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/HeadshotOnly/player-create-hs-only-noti.png)

At the same time, the notification created from the Lobby must be deleted.

### On Equip Weapon
From this event, an important logic for the Headshot Only mode is applied for weapon. 
![player-on-equip-weapon](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/HeadshotOnly/player-on-equip-weapon.png)

Normally, if only the player's **Headshot Damage Reduction** and **Damage Taken Percentage** are adjusted, the Headshot damage will only amount to 1 to 5 damage per shot. As such the weapon's **Head Damage Factor** needs to **55000** specifically to closely match the weapon's original headshot damage. This value can be adjusted if a different damage value is desired. 
![player-adjust-weapon-stat](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/HeadshotOnly/player-adjust-weapon-stat.png)


### On Phase End
The sole purpose of this event is to delete the player's Headshot Only Notification at the end of the combat phase.  
![player-on-phase-end](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/HeadshotOnly/player-on-phase-end.png)

### On User Quit or User Match End
![player-on-user-quit-or-user-match-end](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/HeadshotOnly/player-on-user-quit-or-user-match-end.png) 

This event is for ensuring that the HUD are deleted correctly when the match ends.
