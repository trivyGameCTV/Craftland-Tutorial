# Game Mechanics

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/1.png" alt="1" style="zoom:80%;" /> 

# Map Overview

Game Mechanics (Re-Editable) is one of the official gameplay templates pre-installed in the Free Fire CraftLand Editor. It provides developers with a reusable blueprint for foundational gameplay features, primarily comprising three major components: map scenes, rule settings, and block script.

Within this template, you can experience and learn the core gameplay editing methods—interacting with various pre-designed mechanisms and experiencing their feedback.

Simultaneously, you can rapidly grasp and deepen your understanding of other common game interaction mechanisms. These include activating custom triggers, increasing/decreasing player health, spawning monsters (zombies), moving objects, teleporting players to specific locations, displaying custom text, changing character skins, and interacting with custom HUD UI. You can then expand upon and re-edit these core scripts to create your own unique works.

# Map Scene

First, introducing scene design: the overall area is based on the default blank scene, with a simple square enclosed space constructed and interactive mechanisms scattered throughout (highlighted in the red box at the top of the image below). Players can be divided into three teams and will spawn on one side of the map upon entering the game (red box at bottom of image below) to freely experience the core gameplay.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/2.png" alt="2" style="zoom:67%;" /> 


Beyond quick adjustments to objects within the scene, you can also manage all scene objects by clicking **More > Object Manager**

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/3.png" alt="3" style="zoom:67%;" /> 

# Feature-Related

## Rules

To configure gameplay rules, click **Settings > Gameplay Settings > Gameplay Rule Editor**

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/4.png" alt="4" style="zoom:67%;" /> 



Here you can edit detailed rules for this template, including: Mode, Property Settings, Economy, and Camera.

The current template's rule settings primarily differ from default settings in the following areas: Mode and Economy. Below are the specific rule entries that differ:

### Mode

Round Settings: Used to configure round-related parameters.

Team Configuration: Determines the number of players per session, available team slots, and minimum players required to start the game

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/5.png" alt="5" style="zoom:67%;" /> 

### Economy

Shop Editor: Determines consumables that players can obtain with tokens at specific locations and their prices

*Note: As the core gameplay of this template focuses on mechanism experiences, **vending machines** are not included. If needed, drag one from the object library into the scene and create it.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/6.png" alt="6" style="zoom:67%;" /> 

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/7.png" alt="7" style="zoom:67%;" /> 

## User UI

To build a custom UI, click **More - Custom HUD**

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/8.png" alt="8" style="zoom:67%;" /> 

Here you can edit the custom HUD UI players can interact with during matches and jump to corresponding script designs.

The current template's custom HUD UI only serves **button door** mechanisms.



To edit specific widgets, click **Edit Layout** and select the desired widget from the left-hand list.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/9.png" alt="9" style="zoom:67%;" /> 

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/10.png" alt="10" style="zoom:67%;" /> 


Here you can adjust various property of specific widgets, such as: size, position, rotation angle, visibility, opacity, color, displayed content, etc.



Jump to corresponding block script design:

Click **Edit Script** - Jump to the HUD script editing UI. Specific script creation methods will be detailed below.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/11.png" alt="11" style="zoom:67%;" /> 



In-game UI Overview: (Automatically displayed when the player character enters the custom trigger range of the **Button Door**)

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/12.png" alt="12" style="zoom:67%;" /> 

This button controls the opening/closing of the door in the **Button Door** mechanism.

## Blocks

Additional gameplay rules require the Blocks Editor. Access it by:

Click **More - block script**, then select the specific script you wish to edit in the top-right corner of the UI

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/13.png" alt="13" style="zoom:67%;" /> 

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/14.png" alt="14" style="zoom:67%;" /> 

This section primarily introduces the core gameplay of “Game Mechanics” and how other specific rules are implemented via scripts.

You can edit specific scripts and adjust related values here.

For script functions requiring further understanding, click the specific script to view details.

### Custom Trigger Scripts

This section details the effects and script content for each mechanism.

| **No.** | **Mechanism Name** |
| -------- | ---------------- |
| ① | Healing Zone |
| ② | Damage Zone |
| ③ | Monster Spawn Zone |
| ④ | Trap Zone |
| ⑤ | Teleport Zone |
| ⑥ | Text Display Zone |
| ⑦ | Costume Change Zone |
| ⑧ | Elevator |
| ⑨ | Automatic Door |
| ⑩ | Button Door |

#### Healing Area

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/15.png" alt="15" style="zoom:67%;" /> 

1. Upon entering, player characters continuously regain health at a rate of 15 HP per second while displaying healing effects



Overview:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/16.png" alt="16" style="zoom:67%;" /> 



- The core function of this device—healing players (increasing their health)—is encapsulated in the following function, which executes for every eligible player entering the device. Below is the specific script implementation:

**Area 2-3**

“Updatetreat” Function

1. If “ListOfTreat” > 0 and the result of GameTime - custom variable “LastUpDateTime” is greater than 1000, set custom variable “LastUpDateTime” equal to GameTime
2. Index the ‘Player’ element in data container “ListOfTreat”. If the player's current HP < their maximum HP, increase that player's HP by 15

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/17.png" alt="17" style="zoom:67%;" /> 




- When a player receives healing, we also want to provide visual feedback through special effects to indicate the function is active. This functionality is encapsulated in the following function; below is the specific script implementation:

**Area 2-2**

“CreateEffects” Function

1. Append the player to the “ListOfTreat” list
2. Create an ascending air current effect on the player. Set loop type to “Loop”, set “Play Immediately” to true, and return “SpecialEffect” 
3. Insert “SpecialEffect” into the “SpecialEffect” list at the index corresponding to its first appearance on the player
4. Create a “Tween” for ‘SpecialEffect’ to follow the player's target. Set XYZ axis offsets to none, set reference coordinate system to none, and set “Play Immediately”. Return “Tween”
5. Set the “SpecialEffect” color to green
6. Set the “SpecialEffect” scale to 0.5x along all XYZ axes
7. Insert the ‘Tween’ into the “Tween” list at the index corresponding to its first occurrence on the player

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/18.png" alt="18" style="zoom:67%;" /> 




- This section primarily defines variables to determine event execution timing, handles players entering/exiting mechanisms, and calls functions at appropriate moments. Below is the specific script implementation:

**Area 2-1**

1. At the start of the phase, set the custom variable “LastUpdateTime” equal to the game time. 
2. When the player character enters this custom trigger, call the ‘CreateEffects’ function.
3. When the player character leaves this custom trigger, batch destroy & delete the target values (some targets require indexing via a list).
4. When updating, call the “UpdateTreat” function.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/19.png" alt="19" style="zoom:67%;" /> 


Appendix: Custom variables and functions required for this script. You can view and manage them by clicking **Variables** and **Functions**.

![20](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/20.png) ![21](https:// dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/21.png) 

#### Damage Zones

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/22.png" alt=“22” style="zoom:67%;" /> 

1. Player characters continuously lose health at a rate of 15 per second upon entry



Overview:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/23.png" alt="23" style="zoom:67%;" /> 



- The core function of this mechanism—inflicting damage on players (reducing their health)—is encapsulated in the following function, which executes for every eligible player entering the mechanism. Below is the specific script implementation:

**Area 3-2**

“UpdateInjure” Function

1. If “ListOfInjure” length > 0
2. If game time - custom variable “LastUpdateTime” yields a result greater than 1000, set custom variable “LastUpdateTime” equal to game time, then index element ‘Player’ in data container “ListOfInjure”
3. If the player's current health ≠ 0, inflict 15 damage on that player

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/24.png" alt="24" style="zoom:67%; " /> 



- This section primarily defines variables to determine event execution timing, handles players entering/exiting the mechanism, and calls functions as needed. Below is the specific script implementation:

**Area 3-1**

1. At phase start, set custom variable “LastUpdateTime” to game time
2. When player character enters/exits this custom trigger, append/remove player from ‘ListOfInjure’
3. Upon update, call “UpdateInjure” function

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/26.png" alt="26" style="zoom:67%;" /> 

Note: Custom variables and functions required by this script can be viewed and managed by clicking **Variables** and **Functions**

![27](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/27.png) ![28](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/28.png)


#### Monster Spawn Zone

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/29.png" alt="29" style="zoom:67%;" /> 

1. Spawns one zombie near this zone when a player character enters



- The core function of this mechanism—spawning zombies—can be triggered by every player entering it, accompanied by corresponding sound effects. Below is the specific script implementation:

1. When a player character enters this custom trigger, create a zombie at coordinates: XYZ = (Player X coordinate - 2, Player Y coordinate, Player Z coordinate - 2). Set its type to Normal, auto-target to True, behavior type to Passive, and path to None.
2. Create a non-targeted alert sound effect with a loop type of “once” and “play immediately” set to true.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/30.png" alt=“30” style="zoom:67%;" /> 

#### Trap Area

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/31.png" alt="31" style="zoom:67%;" />  

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/32.png" alt="32" style="zoom:67%;" /> 


1. When a player character enters, the trap cage above their head will drop, trapping the player in that area.
2. After the trap cage drops, a 10-second countdown will appear. The trap will be restored once the countdown ends.



Overview:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/33.png" alt="33" style="zoom:67%;" /> 



- The core functionality—dropping the trap cage to trap players—is encapsulated in the following function, which executes for every eligible player entering the mechanism
- Additionally, the mechanism's initialization is encapsulated as a function, encompassing unified grouping of scene trap objects and pre-hiding the countdown text. Below is the specific script implementation:

**Area 4-2**

“TrapFalls” Function

1. If “TrapState” is true, move the level object “Trap” with index data container “Trap” to coordinates XYZ = (“Trap” X coordinate, ‘Trap’ Y coordinate - 2, “Trap” Z coordinate)
2. Set “TrapState” to false

“Initialization” function

1. Append “Iron Fence1-4” to ‘Trap’
2. Set custom variable “TrapTime” to true
3. Create a Text object at coordinates XYZ = (Scene Entity “Block” X coordinate, Scene Entity “Block” Y coordinate + 3, Scene Entity ‘Block’ Z coordinate), return “Text”
4. Set custom variable “Time” to “Text” 
5. Set “Text” position to coordinates: XYZ = (Scene Entity “Block” X coordinate, Scene Entity “Block” Y coordinate + 3, Scene Entity “Block” Z coordinate)
6. Set “Text” content to string ‘10’
7. Set “Text” scale factor to 0 in all XYZ directions

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/34.png" alt="34" style="zoom:67%;" /> 




- After the trap drops, display a 10-second countdown to the player. Once the countdown ends, raise the trap back up, restore it, and hide the countdown text. Part of this functionality is encapsulated in the following function. Below is the specific script implementation:

**Area 4-3**

“UpdateInjure” Function

1. If “TrapState” is false and the result of game time minus custom variable “LastUpDateTime” exceeds 1000, set custom variable “LastUpDateTime” equal to game time. Convert string ‘Time’ to integer and return " Result“, sets ”Time“ content to ”Result“-1
2. If ”Time“ content is 0, sets ”Text“ scaling factor to 0 on all XYZ axes, sets ”Text“ content to string ”10“, calls ‘TrapRecovery’ function, sets ”TrapState" to true

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/35.png" alt="35" style="zoom:67%;" /> 

**Area 4-4**

1. If “TrapState” is false, index the element “Each” in the data container “Trap”, moving the level object “Each” to coordinates XYZ = (“Each” X coordinate, “Each” Y coordinate + 2, ‘Each’ Z coordinate)
2. Set the “Time” scaling factor to 2 in all XYZ directions

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/36.png" alt="36" style="zoom:67%;" /> 




- This section primarily determines when each function is called; below is the specific script implementation:

**Area 4-1**

1. When the game starts, call the “Initialization” function
2. When the player character enters this custom trigger, wait 0.3 seconds, then call the “TrapFalls” and “CountDown” functions
3. During updates, call the ‘UpdateInjure’ function

<img src="https://dl.dir.freefiremobile.com/common/OB46/ CSH/OfficialWeb/CLWiki2/GameMechanics/37.png" alt="37" style="zoom:67%;" /> 

Note: Custom variables and functions required by this script. You can view and manage them by clicking **Variables** and **Functions**.

![38](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/38.png) ![39](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/39.png) 

# ### Transfer Area

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/40.png" alt="40" style="zoom:67%;" /> 

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/41.png" alt="41" style="zoom:67%;" /> 


1. Display a 3-second countdown when the player character enters, simultaneously playing a teleportation effect on the character
2. After the countdown ends, the character is teleported to the designated location



Overview:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/42.png" alt="42" style="zoom:67% ;" /> 



- The core functionality of this mechanism—teleporting entering players to a designated location after 3 seconds—is encapsulated in the following function, which can be executed for every eligible player entering the mechanism. Below is the specific script implementation:

**Area 5-2**

“MyUpdate” Function

1. Retrieve the “Player” element from the index data container “PlayerList”
2. Set the temporary variable “State” to the ‘index’ value from “PlayerStateList”
3. If “state” = 1, set temporary variable “enter_tick” to “index” in “EnterTickList”, set temporary variable “stay_tick” to game time - “enter_tick”, set temporary variable ‘countdown’ to (3000 - “stay_tick”) * 0.001 rounded up
4. If “countdown” > 0, set the content of “index” in “TextEntityList” to the string “countdown”. Otherwise, set temporary variable “target_pos” to the position of scene object “TeleportTar”, then teleport the player to coordinates XYZ = (“target_pos” X coordinate, ‘target_pos’ Y coordinate + 2, “target_pos” Z coordinate) , rotate with Euler angles XYZ = (0, 0, 0)

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/43.png" alt="43" style="zoom:67%;" /> 




- When the player is about to be teleported, we also want to provide visual feedback by generating special effects on the player to indicate the function is active, and display a corresponding 3-second teleportation countdown. This functionality is encapsulated into the following function; below is the specific script implementation:

**Area 5-3**

“InitPlayerData” Function

1. Append the player to “PlayerList”, append 0 to “PlayerStateList”, append 0 to “EnterTickList”
2. Create a text object at coordinates XYZ=(0,0,0), return ‘TextEntity’
3. Create “TextEntity” for player target tracking, offset based on player coordinate system XYZ= (0, 1.5, 0) and play immediately 
4. Append “TextEntity” to “TextEntityList”
5. Create a spark visual effect on the player, set loop type to loop, set play immediately to true, return “VisualEffectEnti”
6. Set ‘VisualEffectEnti’ effect color to blue
7. Create " VisualEffectEnti“ to follow the player's target, with no offset along any XYZ axis in its coordinate system, and play immediately. 
8. Append ‘VisualEffectEnti’ to ”VisualEffectList"

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/44.png" alt="44" style="zoom:67%;" /> 

**Area 5-4**

“ReadyToTeleport” Function

1. Set the “index” of “PlayerStateList” to 1
2. Set the “index” of “EnterTickList” to game time
3. Set the content of “index” in “TextEntityList” to empty
4. Set the scale factor of ‘index’ in “TextEntityList” to 1 in all XYZ directions
5. Set the scale factor of “index” in “VisualEffectList” to 1 in all XYZ directions

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/45.png" alt="45" style="zoom:67%;" /> 



- When canceling player teleportation, the following actions are executed: Hide the countdown text and teleportation effects. This functionality is encapsulated in the following function; below is the specific script implementation:

**Area 5-5**

“AbortTeleport” Function

1. Set the “index” of “PlayerStateList” to 0
2. Set the scaling factor of “index” in “TextEntityList” to 0 in all XYZ directions
3. Set the scaling factor of ‘index’ in “VisualEffectList” to 0 in all XYZ directions

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/46.png" alt="46" style="zoom:67%;" /> 




- This section primarily determines function call timing; below is the specific script implementation:

**Area 5-1**

1. Start loop execution: Wait 0.2 seconds, then call the “MyUpdate” function
2. When the player character enters this custom trigger, set the temporary variable “index” to the position where “Player” first appears in “PlayerList”. If index=-1, call the “InitPlayerData” function; call the ‘ReadyToTeleport’ function
3. When the player character leaves this custom trigger, call the “AbortTeleport” function

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/47.png" alt="47" style="zoom:67%;" /> 

Appendix: Custom variables and functions required by this script. You can view and manage them by clicking **Variables** and **Functions**

![48](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/48.png) ![49](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/49.png)


#### Text Display Area

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/50.png" alt="50" style="zoom:67%;" /> 

1. Display “HelloWorld” text when the player character enters
2. Hide ‘HelloWorld’ text when the player character leaves



- The core functionality of this trigger—displaying and hiding “HelloWorld” text at appropriate times—is encapsulated in the following function
- This content also determines when the above function is called; here's the specific script implementation:

1. When the player character enters/exits this custom trigger, append/remove “Player” from the “ListOfPlayer” list
2. At the position of the scene entity “CueArea” (recorded as Location), call the “CreateTips” function/call the ‘DeleteTips’ function

“CreateTips” function

1. Create a text object at position XYZ = (“Location” X coordinate, “Location” Y coordinate + 2, “Location” Z coordinate), returning “Tips”
2. Set custom variable ‘Tips’ = “Tips”
3. Set the content of “Tips” to “Hello World”

“DeleteTips” Function

If the length of ‘PlayerList’ ≤ 0, destroy “Tips”

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/51.png" alt="51" style="zoom:67%;" /> 

Appendix: Custom variables and functions required for this script. You can view and manage them by clicking **Variables** and **Functions* *

![52](https://dl.dir.freefiremobile.com/common/ OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/52.png) ![53](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/53.png) 

#### Outfit Change Area

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/54.png" alt="54" style="zoom:67%;" /> 

1. When a player character enters, the character's appearance changes according to their gender



- The core function of this mechanism—changing players into gender-appropriate attire—can be triggered by every player entering it. Below is the specific script implementation:

This area's script demonstrates how to randomly change a player character's outfit to the corresponding gender set upon entering this custom trigger

1. At game start, add the following sets to “Women's Wardrobe” and " Men'sWardrobe“
2. When a character enters this custom trigger, if their gender is 2, shuffle ”Men'sWardrobe“ and set their outfit to the set at index 0 of ”Men'sWardrobe“
3. Otherwise, shuffle ”Women'sWardrobe“ and set their outfit to the set at index 0 of ”Women'sWardrobe"

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/55.png" alt="55" style="zoom:67%;" /> 

Appendix: Custom variables required for this script. You can view and manage them by clicking **Variables**

![56](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/56.png) 

#### Elevator

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/57.png" alt="57" style="zoom:67%;" /> 

1. When the player character enters the elevator, it will slowly ascend until reaching the set maximum height
2. When the player character exits the elevator, it will slowly descend until returning to its initial position



Overview:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/58.png" alt="58" style="zoom:67%;" /> 



- The core functionality of this mechanism—raising the elevator object when a player enters and lowering it when they leave—is encapsulated in the following function, which executes for every eligible player entering the mechanism. Below is the specific script implementation:

**Area 6-2, 6-3**

“CreateAnElevator” Function

1. Set the custom variable ‘ElevatorsLocation’ to the position of “Elevator”
2. Execute loop if condition is met: `PlayerList` length > 0. Wait 0.5 seconds, set `ElevatorsLocation`'s Y coordinate to current value + 0.2, update custom variable `ElevatorsLocation`, set `Elevator`'s position to `ElevatorsLocation`, set this custom trigger's position to `ElevatorsLocation`
3. Continue looping until either the length of “PlayerList” ≤ 0 or the custom variable “Mark” ≥ 20. Otherwise, set ‘Mark’ value to current value + 1

“DescendElevator” function

1. Condition met: When “PlayerList” length = 0, start loop: Wait 0.5 seconds, set temp variable “Time” to “Elevator” position, set “Time” Y-coordinate to current value - 0.2, update custom variable “Time”, set “Elevator” position to “Time”, set this custom trigger's position to ‘Time’
 2. Until “PlayerList” length > 0 or “Time” Y-coordinate ≤ 2.8, otherwise continue looping and set “Mark” value to current value - 1

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/59.png" alt=“59” style="zoom:67%;" /> 

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/60.png" alt="60" style="zoom:67%; " /> 



- This section primarily determines when functions are called and defines variables for assigning values to Scene objects. Below is the specific script implementation:

**Area 6-1**

1. When the player character enters this custom trigger, add the player to “ListOfInjure” and call the “CreateAnElevator” function
2. When the player character leaves this custom trigger, remove the player from ‘ListOfInjure’. If the length of " PlayerList “length ≤ 0”, call the “DescendElevator” function
3. At game start, set the custom variable ‘Elevator’ to the scene object “High-Tech Platform A1”

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/61.png" alt="61" style="zoom:67%;" /> 


Appendix: Custom variables and functions required by this script. You can view and manage them by clicking **Variables** and **Functions**.

![62](https://dl.dir.freefiremobile.com/common/ OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/62.png) ![63](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/63.png) 

#### Automatic Door

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/64.png" alt="64" style="zoom:67%;" /> 

1. When the player character approaches the door (entering the custom trigger's range), the door automatically opens
2. When the character moves away from the door again (exiting the custom trigger's range), the door will automatically close



Overview:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/65.png" alt="65" style="zoom:67%;" /> 



- The core functionality of this mechanism—opening the door when the player approaches and closing it when they leave—is encapsulated in the following function, which executes for every eligible player entering the mechanism. Below is the specific script implementation:

**Area 7-3, 7-4**

“OpenTheDoor” Function

If `PlayerList` length ≥ 0, the condition is met: Execute the loop until `PlayerList` length = 0 or `Mark` > 5 when `Mark` ≤ 5; otherwise, continue the loop:

1. Wait 0.5 seconds
2. Set “Japanese-Style Platform A1” position coordinates XYZ = (“Japanese-Style Platform A1” X coordinate + 0.2, “Japanese-Style Platform A1” Y coordinate, “Japanese-Style Platform A1” Z coordinate)
3. Set “Japanese-Style Platform A1(1)” position coordinates XYZ = (“Japanese-Style Platform A1(1)” X coordinate - 0.2, “Japanese-Style Platform A1(1)” Y coordinate, “Japanese-Style Platform A1(1)” Z coordinate)
4. Increment “Mark” value by 1

“CloseTheDoor” function

If “PlayerList” length = 0, execute the loop when “Mark” ≥ 0 until “PlayerList” length > 0 or ‘Mark’ = 0; otherwise, continue looping:

1. Wait 0.5 seconds
2. Set “Mark” value to current value - 1
3. Set “Japanese-Style Platform A1” position coordinates XYZ = (“Japanese-Style Platform A1” X coordinate - 0.2, “Japanese-Style Platform A1” Y coordinate, “Japanese-Style Platform A1” Z coordinate)
4. Set the position coordinates XYZ of “Japanese-Style Platform A1(1)” to:    X = “Japanese-Style Platform A1(1)” X coordinate + 0.2,    Y = “Japanese-Style Platform A1(1)” Y coordinate,    Z = “Japanese-Style Platform A1(1)” Z coordinate “Japanese-Style Platform A1(1)”Z coordinate)

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/66.png" alt="66" style="zoom:67%;" /> 

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/67.png" alt="67" style="zoom:67%;" /> 




- This section primarily defines variables to determine event execution timing, handles players entering/exiting triggers, and calls functions at appropriate moments. Below is the specific script implementation:

**Zone 7-1, 7-2**

1. At game start, set custom variable “Mark” to 0
2. When the player character enters/exits this custom trigger, wait until the next frame, add/remove the player from “PlayerList”, wait until the next frame, and call the ‘OpenTheDoor’/“CloseTheDoor” function

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/68.png" alt="68" style="zoom:67%;" /> 

<img src="https://dl.dir.freefiremobile.com/common/ OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/69.png" alt="69" style="zoom:67%;" /> 

Appendix: Custom variables and functions required by this script. You can view and manage them by clicking **Variables** and **Functions**

![70](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/70.png) ![71](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/71.png)


Button Gate

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/72.png " alt="72" style="zoom:67%;" /> 

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/73.png" alt="73" style="zoom:67%;" /> 


When the player character approaches the door (enters the trigger's range), the UI will display a button <img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/ OfficialWeb/CLWiki2/GameMechanics/XX.png" alt="XX" style="zoom:50%;" />. Clicking it opens the door; clicking it again closes the door
. When the character moves away from the door (exiting the trigger's range), the UI button <img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/XX.png" alt="XX" style="zoom:50%;" /> disappears, while the door maintains its current open/closed state.



- The core functionality of this mechanism—opening the door when the player clicks the button and closing it upon another click—is encapsulated in the following function, which can be executed for every eligible player entering the mechanism:
- This also includes handling players entering/exiting the mechanism and calling functions at appropriate times. Below is the specific script implementation:

1. When a player enters this custom trigger, set the visibility property of the custom UI “HudList” to true

2. When a player joins the game, call the ‘CreateHUD’ function

3. The “CreateHUD” function

 Appends the player to “PlayerList”

 Creates a custom HUD ‘Button’ for the player <img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/XX.png" alt="XX" style="zoom:50%;" /> and returns the “Ui”

Insert the “Ui” into the “HudList” at the position corresponding to the first occurrence of “Player” in the ‘PlayerList’

Set the visibility property of the “HudList” (as the custom UI) to false

4. When the player leaves this custom trigger, set the visibility property of the “HudList” (as the custom UI) to false

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/74.png" alt="74" style="zoom:67%;" /> 

Appendix: Custom variables and functions required by this script. You can view and manage them by clicking **Variables** and **Functions**

![75](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/75-1757409940898-82.png) ![](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/76.png) 

### Global Script

- To streamline script content and facilitate monitoring multiple device statuses via a single variable (e.g., elevator runtime in Device ⑧**Elevator**, door status in Device ⑩**Button Door**), we need to define a global variable (named Mark)

 At game start, set custom variable “Mark” to 0

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/77.png" alt="77" style="zoom:67%;" /> 

Note: Custom variables required for this script can be viewed and managed by clicking **Variables**

![78](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/78.png) 

### Player Script

- To ensure players can smoothly experience core gameplay, allow respawning after death. Here's the script implementation:

1. When a player joins the game, set the custom variable “DamageDetermina” to false
2. When a player is killed, wait 3 seconds and respawn on the next frame

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/79.png" alt="79" style="zoom:67%;" /> 

Note: Custom variables required for this script can be viewed and managed by clicking **Variables**

![80](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/80.png) 

### HUD Script

Overview:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/81.png" alt="81" style="zoom:67%;" /> 



- Since clicking the button triggers different actions based on the door's current state, this script evaluates the entity's properties and the value of the custom variable Mark to invoke the corresponding function. Below is the specific script implementation:

**Area 1-1**

1. When button !<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/XX.png" alt="XX" style="zoom:50%;" /> is clicked, if the X-axis position of entity “Frozen Steel Panel A1” is ≥2 and custom variable “Mark” ≠ 1, then call the ‘CloseTheDoor’ function
2. Otherwise, call the “OpenTheDoor” function

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/82.png" alt="82" style="zoom:67%;" /> 




- Core functionality of Mechanism ⑩**Button Door**—opening/closing and holding the door—is encapsulated into the following functions, executable for every eligible player entering this mechanism. Below is the specific script implementation:

**Zones 1-2, 1-3**

“OpenTheDoor” Function

1. If custom variable “Mark” = 0, set “Mark” = 1
2. Start loop: Wait 0.5 seconds, move object 0.2 units along X-axis until object's X-position ≥ 2, set ‘Mark’ = 2 and break loop

“CloseTheDoor” Function

1. If custom variable “Mark” = 2, set ‘Mark’ = 1
2. Start loop: Wait 0.5 seconds, move the object -0.2 units along the X-axis. Once the object's X-position ≤ 1, set “Mark” = 0 and break the loop

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/83.png" alt="83" style="zoom:67%;" /> 


<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/84.png" alt="84" style="zoom:67%;" /> 

Note: Custom functions required by this script. You can view and manage them by clicking **Functions**

![85](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/85.png) 

### Respawn Point Script

- Once players enter the game and begin experiencing core gameplay, respawn points become non-functional components that may disrupt player activity. Therefore, they must be set to inactive status.

1. When the round begins, set this entity's active status to true
2. Wait 2 seconds
3. Set this entity's active status to false

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/GameMechanics/86.png" alt="86" style="zoom:67%;" /> 

# Secondary Editing Recommendations

- Adjust values within specific scripts to create more exaggerated, random trap behaviors, enhancing the game's drama
- Integrate with shop mechanics and add PvP combat gameplay, making traps part of the obstacle system
- Expand or deepen trap functionality, exploring and implementing further applications of different script mechanisms
