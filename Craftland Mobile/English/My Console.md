# Myconsole

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_11-10-14.png" alt="image2025-8-13_11-10-14" style="zoom:80%;" /> 

# Map Overview

Myconsole (Re-Editable) is one of the official gameplay templates pre-installed in the Free Fire CraftLand editor. It provides developers with a reusable blueprint for foundational gameplay features, primarily encompassing map scenes, rule settings,UI interface, and block script.

Within this template, you can experience and learn the core gameplay editing methods—such as activating pre-designed HUD interfaces for interaction, adjusting player body proportions, or creating/destroying random terrain.

Additionally, you can quickly grasp and delve into other common game interaction mechanisms, including executing events for specific players, teleporting players to designated locations, displaying custom text, and other frequently used scripting logic. You can then expand upon and re-edit these features to further create your own unique works.

# Map Scene

First, the scene design: the entire arena uses the default 50x50 Champion Island. All players are on the same team and spawn on one side of the map (red box in Figure 1 below) upon entering the game. They can freely purchase consumables at the shop (red box in Figure 2 below) before experiencing the core gameplay.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_11-44-37.png" alt="image2025-8-13_11-44-37" style="zoom:67%;" />
      

> Figure 1

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_11-44-52.png" alt="image2025-8-13_11-44-52" style=“zoom:67%;” /> 

> Figure 2

In addition to making quick adjustments to objects directly within the Scene, you can also manage all Scene objects by clicking **More > Object Manager**.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_14-17-5.png" alt="image2025-8-13_14-17-5" style="zoom:67%;" /> 


# Feature-Related

## Rules

To configure gameplay rules, navigate to **Settings > Gameplay Settings > Gameplay Rules Editor**

*Note: The team count is preset to 1 here, meaning all players are on the same team. PVP will not occur during matches; the focus is on experiencing gameplay and mechanics.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_17-4-49.png" alt="image2025-8-13_17-4-49" style="zoom:67%;" /> 



You can edit detailed rules for this template here, including: Mode, Property Settings, Economy, and Camera

The current template's rule settings primarily differ from default settings in the following areas: Mode and Economy. Below are the specific rule entries that differ:

### Mode

- Round Settings: Configure parameters related to rounds
- Team Settings: Determine the number of players per game session, available team slots, and minimum players required to start the game

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_11-39-39.png" alt="image2025-8-13_11-39-39" style="zoom:67%;" /> 

### Economy

- Edit Shop: Determines the consumables players can purchase with tokens at specific locations and their prices

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_11-40-1.png" alt="image2025-8-13_11-40-1" style="zoom:67%;" /> 


<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_11-40-22.png" alt="image2025-8-13_11-40-22" style="zoom:67%;" /> 

## User Interface

To configure the user interface, click **More - Custom HUD**

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_17-10-38.png" alt="image2025-8-13_17-10-38" style="zoom:67%;" /> 


Here you can edit the custom HUD UI players can interact with in-game and jump to corresponding script designs.

The custom HUD UI widgets in the current template primarily include buttons that perform specific actions via “Myconsole” and panels that display relevant information after triggering actions.



To edit specific widgets, click **Edit Layout** - then select the desired widget from the left-hand list.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_17-11-27.png" alt=“image2025-8-13_17-11-27” style="zoom:67%;" /> 

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-9-3_10-58-57.png" alt="image2025-9-3_10-58-57" style="zoom:67%;" /> 

Here you can adjust various properties of specific widgets, such as: size, position, rotation angle, visibility, opacity, color, displayed content, etc.

The functionality and implementation methods for each specific widget will be detailed in the *[HUD Scripts](#HUD脚本)*.



Jump to corresponding block script design:

Click **Edit Script** - Jump to HUD script editing UI

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_15-37-31.png" alt="image2025-8-13_15-37-31" style=“zoom: 51.5%;” /> 



In-Game HUD UI Overview:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_18-0-31.png" alt="image2025-8-13_18-0-31" style="zoom:67%;" /> 

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_18-0-59.png" alt="image2025-8-13_18-0-59" style="zoom:67%;" /> 


The primary widgets include:

**MyConsole**: (Always active) Used to enable/disable this custom HUD UI

**1**: Switch to the UI for adjusting in-game player body proportions

​      **prev player**: Select the previous player, applying subsequent **big-/mini-/reset** operations to that player

​      **next player**: Selects the next player, applying subsequent **big-/mini-/reset** actions to them

​      **big head**: Increases the selected player's head size

​      **mini head**: Decreases the selected player's head size

​      **big foot**: Increases the selected player's foot size

​      **mini foot**: Reduces the foot size of the selected player

​      **big hand**: Increases the hand size of the selected player

​      **mini hand**: Reduces the hand size of the selected player

​      **reset**: Resets all body part sizes of the selected player to default

**2**: Switch to the UI for creating/destroying random terrain

​      **create terrain1**: Generate random terrain

​      **teleport**: Teleport player to a set location

​      **clear terrain**: Destroys the created terrain

**Information Display Panel**: Shows relevant feedback and prompt text after the player presses the above buttons

## Primitives

Additional gameplay rules require the Primitive Editor. To open it:

Click **More - Primitive Scripts**, then select the specific script you want to edit in the top-right corner of the UI

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_11-49-22.png" alt="image2025-8-13_11-49-22" style="zoom:67%;" /> 

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_16-52-9.png" alt="image2025-8-13_16-52-9" style="zoom:67%;" /> 


This section primarily introduces the core gameplay feature “Myconsole” and other specific rules implemented via scripts.

You can edit specific scripts and adjust related values here.

For script functions requiring further understanding, you can click on the specific script to view details.

### HUD Script

Overview:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_14-32-19.png" alt="image2025-8-13_14-32-19" style="zoom:67%;" /> 

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_14-42-35.png" alt="image2025-8-13_14-42-35" style="zoom:67%;" /> 

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_14-42-41.png" alt="image2025-8-13_14-42-41" style="zoom:67%;" /> 

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_14-44-46.png" alt="image2025-8-13_14-44-46" style="zoom:67%;" /> 


#### Core Gameplay

- First are the UI toggle buttons **MyConsole, 1&2**. Since core gameplay encompasses multiple functions, these are categorized across two pages for interaction, providing users with a clearer, more organized experience. Below is the specific script implementation:

**Zone 1-2**

**MyConsole**: Toggles the display/hide of the entire custom HUD UI (excluding this button)

**1**: Switches to the custom HUD UI for adjusting player body proportions. Hides the UI opened by button **2**, highlights button “1” color, restores button “2” color to normal, and calls the ‘loginfo’ function to display “player body modification menu” text

**2**: Toggles the custom HUD UI for creating/destroying random terrain and teleporting players. Hides the UI opened by button **1**, highlights button “2”, restores button “1” to normal color, and calls the ‘loginfo’ function to display “terrain creation menu” text.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_14-54-21.png" alt="image2025-8-13_14-54-21" style="zoom:67%;" /> 


<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_15-40-33.png" alt="image2025-8-13_15-40-33" style="zoom:67%;" /> <img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_18-59-38.png" alt="image2025-8-13_18-59-38" style="zoom: 36%;" /> 



- Below is UI 1, where the **next player/prev player** buttons select players within the match, and **big-/mini-/reset** adjust their body proportions. Here's the specific script implementation:

**Areas 1-3, 1-4**

This area's script demonstrates how subsequent events target the next/previous player in the team after the player clicks the **next player/prev player** button, and how the custom UI displays relevant information.

1. Set the index to move backward/forward by 1 player. If the index exceeds the total number of players, cycle to the first/last player.
2. Set a temporary variable (recorded as msg) equal to the concatenation of the left value “selected=” and the right value “index number”.
3. Append the following to the right side of this temporary variable's string: “player=”; “name of the player at the current index”; “UID=”; “UID of the player at the current index”.
4. Call the “loginfo” function to display the text contained in this temporary variable.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_14-54-49.png" alt="image2025-8-13_14-54-49" style="zoom: 45%;" /> <img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_15-41-42.png" alt="image2025-8-13_15-41-42" style="zoom: 62%;" />


<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_14-55-27.png" alt="image2025-8-13_14-55-27" style="zoom:45%;" /> <img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_15-41-30.png" alt="image2025-8-13_15-41-30" style="zoom:62%;" />


**Zone 1-5, 1-6**

This script demonstrates how to trigger the enlargement/reduction of the currently selected player character's head size after clicking **big head/mini head**, and display related information on the custom HUD UI.

1. Set temporary variable (recorded as selected_player) equal to the player at the current index
2. Set temporary variable (recorded as head) equal to the head of the player character at the current index
3. Set temporary variable (recorded as ori_scale) equal to the rig scale based on temporary variable “head”
4. Set temporary variable “head” to a new value equal to scaling the rig by 0.1x along each XYZ axis based on temporary variable ‘ori_scale’
5. Set temporary variable (recorded as msg) equal to concatenating the left value “player=” and the right value “name of the player at the current index”
6. Concatenate the following to the right side of this temporary variable's string: “UID=”; “UID of the player at the current index”; “head scale="; "Skeletal scale value of temporary variable ‘head’”
7. Call the “loginfo” function to display the text contained in this temporary variable

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_14-56-19.png" alt="image2025-8-13_14-56-19" style="zoom: 45%;" /> <img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_15-42-6.png" alt="image2025-8-13_15-42-6" style="zoom:62%;" /> 

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_14-56-4.png" alt="image2025-8-13_14-56-4" style="zoom:45%;" /> <img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_15-42-19.png" alt="image2025-8-13_15-42-19" style="zoom:62%;" />

**Zone 1-7, 1-8**

The scripts in this area demonstrate how to trigger the selected player character's foot size to shrink/enlarge after clicking **mini foot/big foot**, and display related information on the custom HUD UI.

---For detailed script content, refer to **Areas 1-5 and 1-6**. The modification involves: Replacing the temporary variable “head” with ‘left_foot’ and “right_foot”; Replace “head scale” in temporary variable ‘msg’ with “foot scale”

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_14-56-13.png" alt="image2025-8-13_14-56-13" style="zoom:45%;" /> <img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_15-42-38.png" alt="image2025-8-13_15-42-38" style="zoom:62%;" />

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_14-56-38.png" alt="image2025-8-13_14-56-38" style="zoom:45%;" /> <img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_15-42-50.png" alt="image2025-8-13_15-42-50" style="zoom:62%;" />

**Zone 1-9, 1-10**

This zone's script demonstrates how to trigger the selected player character's hand size to enlarge/shrink after clicking **big hand/mini hand**, and display related information on the custom HUD UI.

---For detailed script content, refer to **Sections 1-5 and 1-6**. Modifications include: - Rename temporary variable “head” to “left_hand” and “right_hand” - Change “head scale” in temporary variable ‘msg’ to “hand scale”

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_14-56-42.png" alt="image2025-8-13_14-56-42" style="zoom:45%;" /> <img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_15-43-9.png" alt="image2025-8-13_15-43-9" style="zoom:62%;" /> 

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_14-56-54.png" alt="image2025-8-13_14-56-54" style="zoom:45%;" /> <img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_15-43-20.png" alt="image2025-8-13_15-43-20" style="zoom:62%;" />


**Zone 1-11**

This script demonstrates how to reset all body part dimensions of the currently selected player character to default values when the player clicks **reset**, and how to display related information on the custom HUD UI.

1. Set temporary variable (recorded as `selected_player`) equal to the currently indexed player
2. Sequentially set temporary variables (recorded as `lf`, `rf`, `lh`, `rh`, `head`) equal to the left foot, right foot, left hand, right hand, and head rigs of the currently indexed player character, and set the scale of these rigs along the XYZ axes to 1
3. Set a temporary variable (recorded as msg) equal to the string concatenation of the left value “reset scale player=" and the right value "name of the player at the current index”
4. Call the ‘loginfo’ function to display the text contained in this temporary variable

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_14-57-9.png" alt="image2025-8-13_14-57-9" style="zoom:45%;" /> <img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_15-43-30.png" alt="image2025-8-13_15-43-30" style="zoom:62%;" /> 



- Next, we move to UI 2. The **teleport** button transports the player to a specified location, while **create terrain1/clear terrain** creates/destroys random terrain. Below is the specific script implementation:

**Area 1-12**

This area's script demonstrates how to teleport the player character to a set location when the **teleport** button is clicked.

1. Teleport player to coordinates XYZ = (0, 30, 0) with rotation Euler angles XYZ = (0, 0, 0)
2. Call the “loginfo” function to display the text “teleport player”

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_14-57-21.png" alt="image2025-8-13_14-57-21" style="zoom:45%;" /> <img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_15-48-44.png" alt="image2025-8-13_15-48-44" style="zoom:67%;" /> 

**Zone 1-13**

This script demonstrates clearing terrain created via “My Console” when the player clicks **clear terrain**, and displaying related information on the custom HUD UI.

1. If `is_spawning` is false, call the `loginfo` function to display “Running task, please stand by...” text. Set `is_spawning` to true, find the element in the `terrain_blocks` data container, destroy it, wait 1 millisecond, then clear the `terrain_blocks` data. Call `loginfo` to display "Terrain clearing task is completed“ text, set ”is_spawning“ to false
2. Otherwise, call the ”loginfo“ function to display ”System is busy now, please wait for current task“ text, wait 2 seconds, then if ”is_spawning“ is true, call the ‘loginfo’ function to display ”Running task, please stand by..." text

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_14-57-47.png" alt="image2025-8-13_14-57-47" style="zoom:45%;" /> <img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_15-48-58.png" alt="image2025-8-13_15-48-58" style="zoom:67%;" />


**Area 1-14**

This area's script demonstrates how to trigger random terrain generation when the player clicks **create terrain1**, and how to display related information on the custom HUD UI.

1. If “is_spawning” is false, call the ‘loginfo’ function to display the text “Running task, please stand by...”", sets `is_spawning` to true, iterates through all elements in the `terrain_blocks` data container, destroys each element, waits 1 millisecond, then clears the `terrain_blocks` data
   1. Sets a temporary variable (recorded as `offset`) equal to the 3D vector XYZ = (0~999999,30, 0~999999)
   2. Set temporary variable (recorded as pos0) equal to 3D vector XYZ = (x, 0, z)
   3. Set temporary variable (recorded as h) equal to floating-point number, value determined by calling “terrain1” function
   4. Set the Y component value “h” of vector “pos0”
   5. Call the “create_block” function to create terrain
   6. Call the ‘loginfo’ function to display the text “Terrain creating task is completed”, and set “is_spawning” to false
2. Otherwise, call the “loginfo” function to display the text “System is busy now, please wait for current task”, wait for 2 seconds, then if “is_spawning” is true, call the ‘loginfo’ function to display the text “Running task, please stand by...”

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_14-57-30.png" alt="image2025-8-13_14-57-30" style="zoom:45%;" /> <img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_15-48-16.png" alt="image2025-8-13_15-48-16" style="zoom:67%;" />


#### Supplementary Rules

- This section primarily includes the following components:
  - Multiple encapsulated functions:loginfo displays text on the HUD widget; “create_block” creates terrain entities; ‘terrain1’ and other functions collaborate with simulation algorithms to generate terrain randomness
  - 3 events: Variables define event execution logic, adding/removing players from the “All Players” list for the **next player/prev player** buttons
  **Area 2-1**

“loginfo” function

​    Sets the content of the UI label widget for the “Myconsole” entity to “msg”

“terrain1” function

​    Calculates the random state for terrain generation by setting temporary variables ‘vec2’ and “r” and using a simulated Perlin noise algorithm

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_14-58-41.png" alt="image2025-8-13_14-58-41" style="zoom:67%;" /> 


**Region 2-2**

The “perlin_noise” function in this region simulates the Perlin noise algorithm

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_14-59-7.png" alt="image2025-8-13_14-59-7" style="zoom:67%;" /> 

**Area 2-3**

”create_block“ function

1. Creates destructible wooden crates at positions based on the previously calculated vector ‘pos’
2. Sets a temporary variable (recorded as ”scale")
3. Set the local scale property value of the “obj” level object equal to the temporary variable “scale”
4. Append “obj” to the ‘terrain_blocks’ list

“hash” function

Used to simulate a hash function

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_14-58-49.png" alt="image2025-8-13_14-58-49" style="zoom:67%;" /> 


**Zone 2-4**

Functions in this zone assist **Zone 2-2 and Zone 2-3** in simulating corresponding algorithms/functions

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_14-58-9.png“ alt="image2025-8-13_14-58-9" style="zoom:67%;" /> 

**Zone 1-1**

1. Set the four custom variables ”is_spawning“, ”select_index“, ‘terrain_blocks’, and ”all_players" to their corresponding values
2. When a player joins/leaves the game, add/remove that player from the “All Players” list

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_14-54-6.png" alt="image2025-8-13_14-54-6" style="zoom:67%;" /> 

Appendix: Custom variables and functions required by this script. You can view and manage them by clicking **Variables** and **Functions**:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-9-3_15-13-34.png" alt="image2025-9-3_15-13-34 (1)"  /> <img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-9-3_15-13-14.png" alt="image2025-9-3_15-13-14" />

### Player Script

- To ensure players can smoothly experience core gameplay, the following settings are required: display the edited custom HUD on the player UI, allow players greater freedom in jumping and movement, enable instant death upon player kill with quick respawn at a designated location. Below is the specific script implementation:

1. Create a custom HUD for the player with the index “MyConsole”
2. Set the player's “Jump Height Scale” property value to: 5
3. Set the player's “Knockdown Settings” property value to: Skip Knockdown
4. When the player is killed, wait 1 second, teleport the player to the designated location, and respawn them on the next frame

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_14-24-14.png" alt="image2025-8-13_14-24-14" style="zoom:67%;" /> 


### Respawn Point Script

- Once players enter the match and begin experiencing core gameplay, the respawn point becomes a non-functional component that may interfere with player activity. Therefore, it must be destroyed.

​    Destroy this entity when the round begins.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MyConsole/image2025-8-13_14-24-40.png" alt="image2025-8-13_14-24-40" style="zoom:67%;" /> 




That concludes the full introduction to this template's functionality. You can click “Try It” to play and test it. You can also try expanding more gameplay features into this base template to create your own fun map!

# Secondary Editing Suggestions

- Adjust values within specific scripts to create more exaggerated player character body proportion changes or introduce unexpected shapes during random terrain generation, enhancing the game's dramatic impact
- Pair the player character body proportion mechanic with PVP combat gameplay
- Expand or deepen console functionality to explore and implement further customization options for player character models and terrain
