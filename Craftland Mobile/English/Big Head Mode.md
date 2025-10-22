# Big Head Mode

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/BigHead/image2025-8-12_15-18-14.png" alt="image2025-8-12_15-18-14" style="zoom:80%;" /> 


# Map Overview

Bigheadmode(Re-Editable) is one of the official gameplay templates pre-installed in the Free Fire CraftLand editor. It provides developers with a reusable blueprint for foundational gameplay features, primarily comprising three components: map scenes, rule settings, and block script.

Within this template, you can experience and learn the core gameplay mechanics—editing methods that encourage headshots by enlarging character models at strategic moments, delivering fast-paced, entertainment-driven gunfights.

Simultaneously, you can quickly grasp and deepen your understanding of other common in-game interaction systems. These include frequently used scripting logic for batch consumable acquisition and equipment swapping. Building upon this foundation, you can expand and customize these systems to create your own unique works.

# Map Scene

First, the scene design: the overall layout resembles a “田” character grid. Players from opposing teams spawn at opposite ends of the map (red box in Figure 1 below) upon entering the game. They can freely purchase weapon at the shop (red box in Figure 2 below) before advancing along multiple routes. Along the way, they utilize cover for evasion and counterattacks, fully experiencing the core gameplay.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/BigHead/image2025-8-13_11-15-46.png" alt="image2025-8-13_11-15-46" style="zoom:67%;" /> 


> Figure 1

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/BigHead/image2025-8-13_11-16-8.png" alt="image2025-8-13_11-16-8" style="zoom:67%;" /> 

> Figure 2

In addition to making quick adjustments to objects directly within the Scene, you can also manage all objects in the Scene by clicking **More - Object Manager**.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/BigHead/image2025-8-13_11-18-16.png" alt="image2025-8-13_11-18-16" style="zoom:67%;" /> 


# Feature-Related

## Rules

To configure gameplay rules, navigate to **Settings > Gameplay Settings > Gameplay Rules Editor**

*Note: Unlimited bullet is enabled here. If disabled, provide players with bullet acquisition methods via **Economy > Edit Shop** or other locations

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/BigHead/image2025-8-13_11-18-54.png" alt="image2025-8-13_11-18-54" style="zoom:67%;" /> 




You can edit detailed rules for this template here, including: Mode, Mechanics, General Settings, Property Settings, and Economy

The current template's rule settings primarily differ from default settings in the following areas: Mode, Mechanics, and Economy. Specific rule entries with differences are listed below

### Mode

- Points Setting: Determines the specific victory point requirement and scoring efficiency for players
- Round Setting: Determines the maximum duration of a single game session on this map
- Team Setting: Determines the number of players per game, the number of teams available, and the minimum number of players required to start the game

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/BigHead/image2025-8-13_11-19-2.png" alt="image2025-8-13_11-19-2" style="zoom:67%;" /> 


### Mechanics

- Danger Zone Settings: This template gameplay is not compatible with Danger Zones, so it is recommended to keep them disabled
- Respawn Settings: Determines the duration between a player's death and their respawn, as well as their respawn location
- Spectator Settings: Determines whether players can be spectated during a match and the types of players who can spectate

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/BigHead/image2025-8-13_11-19-21.png" alt="image2025-8-13_11-19-21" style="zoom:67%;" /> 


### Economy

- Game Economy: Determines the number of tokens players receive and can spend at the start of their turn, upon defeating an enemy, and upon winning a round
- Edit Shop: Determines the consumables players can purchase with tokens at specific locations and their prices

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/BigHead/image2025-8-13_11-19-43.png" alt="image2025-8-13_11-19-43" style="zoom:67%;" /> 

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/BigHead/image2025-8-13_11-19-59.png" alt="image2025-8-13_11-19-59" style="zoom:67%;" /> 


## Metadata

Additional gameplay rules require the block editor. Access it by:

Clicking **More > Metadata Scripts > Player > Metadata Scripts**

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/BigHead/image2025-8-13_11-20-38.png" alt="image2025-8-13_11-20-38" style="zoom:67%;" /> 

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/BigHead/image2025-8-13_11-21-13.png" alt="image2025-8-13_11-21-13" style="zoom:67%;" /> 


This section primarily introduces the core gameplay of ‘Big Head’ mode and other specific rules based on script implementation.

You can edit specific block scripts and adjust related values here.

For script functions requiring further understanding, you can click on the specific script to view details.



Overview:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/BigHead/image2025-8-13_11-24-21.png" alt="image2025-8-13_11-24-21" style="zoom:67%;" /> 


### Core Gameplay

- How do we enlarge or restore the character's head model?
- In game data terms, this involves scaling the character's head rig independently. To ensure consistent visual appearance before and after scaling, the head must be scaled simultaneously along all three XYZ axes at the same ratio. Scaling cannot be unlimited; upper limits must be set.
- Since resizing the head is a reusable function, we encapsulate it into a function triggered whenever the player kills or is killed. Below is the specific script implementation:

**Section 2-1**

“HeadBecomeBigger” Function

Ⅰ Set temporary variable “Headsize” to current value +0.2 (calculates new head size: 0.2 times larger than current)

Ⅱ If updated ‘Headsize’ ≥ 2, set “Headsize” = 2(Character head size cannot exceed twice the original size)

Ⅲ Set temporary variable “VarVector” to XYZ = (“Headsize”, “Headsize”, ‘Headsize’)

Ⅳ Set the character's Rig-Skeleton-Head bone scaling property to temporary variable “VarVector”

“ResetHeadSize” function

Set the rig-scale property of the character's Skeleton > Head to its default value of 1

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/BigHead/image2025-8-13_11-25-11.png" alt="image2025-8-13_11-25-11" style="zoom:67%;" /> 


- Secondly, timing the application of head scaling is crucial for maintaining player balance during matches.
- In this template, to ensure balance, players will increase the head volume of their controlled character upon killing enemies, making them easier to target.Conversely, when a player is killed, the head scaling resets, maintaining a dynamic equilibrium in kill efficiency across all players. Below is the specific script implementation:

**Zone 1-3**

Ⅰ When a player kills an enemy, call the “HeadBecomeBigger” function

Ⅱ When a player is killed, call the “ResetHeadSize” function

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/BigHead/image2025-8-13_11-24-51.png" alt="image2025-8-13_11-24-51" style="zoom:67%;" /> 


### Supplementary Rules

- To accelerate gameplay pace and emphasize entertainment over traditional CS modes, this template sets rules where players die instantly upon being killed but respawn quickly without losing consumables. Players are also provided with basic consumables and fresh armor (helmet and vest) from the start, allowing them to focus purely on combat. Below is the specific script implementation:

**Zone 1-2**

1. Set the player's “Knockdown Settings” property value to: Skip Knockdown

2. Set the player's “Prevent Item Loss” property value to: True

3. Set the player's “Prevent Item Discard” property value to: True

4. Set the player's “Lose All Equipment on Death” property to: False

5. Sequentially call the “AddItemGrenade”, “AddItemSmoke”, “AddItemMed”, ‘AddItemGlooWall’, and “ReplaceArmor” functions
<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/BigHead/image2025-8-13_11-24-58.png" alt="image2025-8-13_11-24-58" style="zoom:67%;" /> 


**Zones 2-2, 2-3, 2-4, 2-5**

“AddItemGrenade”, “AddItemSmoke”, ‘AddItemMed’, “AddItemGlooWall” functions

1. Set temporary variable “Max-ItemName-Num” equal to 3

2. If the player already possesses any of the above consumables in quantities less than the temporary variable “Max-ItemName-Num”, add the corresponding consumable to the player. The quantity (recorded in temporary variable ‘AddNum’) equals the difference between “Max-ItemName-Num” and the existing quantity value

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/BigHead/image2025-8-13_11-25-20.png" alt="image2025-8-13_11-25-20" style="zoom:67%;" /> 

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/BigHead/image2025-8-13_11-25-51.png" alt="image2025-8-13_11-25-51" style="zoom:67%;" /> 

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/BigHead/image2025-8-13_11-25-30.png" alt="image2025-8-13_11-25-30" style="zoom:67%;" /> 

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/BigHead/image2025-8-13_11-25-36.png" alt="image2025-8-13_11-25-36" style="zoom:67%;" /> 


**Zone 2-6**

“ReplaceArmor” function

1. Remove the character's current helmet and body armor (both Level 2)

2. Equip the character with new helmet and body armor (both Level 2)

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/BigHead/image2025-8-13_11-25-43.png" alt="image2025-8-13_11-25-43" style="zoom:67%;" /> 


Finally, to maintain the player's core gameplay experience, ensure respawn protection is enabled upon revival. Simultaneously replenish essential consumables and replace armor (helmet and vest) with new sets. Reset character head scaling at round start to ensure fresh match conditions. Below is the script implementation:

**Zones 1-4**

1. When a player respawns, sequentially call the “AddItemGrenade”, “AddItemSmoke”, “AddItemMed”, “AddItemGlooWall”, and ‘ReplaceArmor’ functions

2. Set the player's “invincible” property value to true

3. Wait 3 seconds (i.e., spawn protection duration is 3 seconds)

4. Set the player's “invincible” property to false

5. When the round begins, call the “ResetHeadSize” function

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/BigHead/image2025-8-13_11-24-46.png" alt="image2025-8-13_11-24-46" style="zoom:67%;" /> 




The following demonstrates how to guide players who start testing immediately after creating a template by displaying text in the console. If you've already reviewed the above content in full, you can skip this entry~

**Area 1-1**

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/BigHead/image2025-8-13_11-24-33.png" alt="image2025-8-13_11-24-33" style="zoom:67%;" /> 



Appendix: Custom variables and functions required for this script. You can view and manage them by clicking **Variables** and **Functions**

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/BigHead/image2025-9-1_15-58-36.png" alt="image2025-9-1_15-58-36" style="zoom:50%;" /> <img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/BigHead/image2025-9-1_15-57-41.png" alt="image2025-9-1_15-57-41" style="zoom:50%;" />


That concludes the full introduction to this template's features. You can click “Try It Out” to play and test it. You can also try expanding more gameplay mechanics into this base template to create your own fun map!
# Secondary Editing Suggestions

- Adjust values within specific scripts to set more exaggerated head size changes, enhancing the game's drama
- Configure gameplay so damage only occurs when hitting an enemy's head, or only when hitting an enemy's body
- Edit the shop to restrict weapon types available to players, e.g., only allow melee weapons during matches
- Reverse the gameplay to create a “Small Head Mode”
