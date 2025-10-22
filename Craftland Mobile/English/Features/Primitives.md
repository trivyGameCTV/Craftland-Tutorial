# Primitives and Logic

This article mainly introduces concepts related to the primitive editor and primitives in CraftLand.

## Overview of Metablocks

When editing graphics, we need to observe the shape of each graphics block. What we need to do is to piece these blocks together according to fixed rules.

### Basic Operations

Before we enter the primitive editor, we must first open a script. Open CraftLand, click [More] in the upper left corner, and then click [Block Script]. When we enter the primitive editor, we will open the 'global script' by default.
![image-20241031110011453](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/image-20241031110011453.png)

#### **Interface Introduction**

After entering the element editor, there are 4 areas in the editor interface that deserve our attention, as shown in the figure below. ![SeaTalk_IMG_20241031_113903](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/SeaTalk_IMG_20241031_113903.jpg)

| Serial Number| Image| Description|
| ---- | --------------------------------------------------------------- | ------------------------------------------------------------ |
| 1 | ![image-20241031114641450](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/image-20241031114641450.png) | In the upper left corner of the interface is a search box. Because there are a large number of primitive blocks, we can retrieve the primitive blocks we want by entering keywords in the search box. |
| 2 | ![image-20241031114811375](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/image-20241031114811375.png) | In the upper right corner of the interface is the script selection list. Click the icon on the right to display a drop-down option, showing the currently available scripts. Global scripts are created by default. |
| 3 | ![image-20241031173408111](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/image-20241031173408111.png) | We divide the primitives into 6 categories. We can click the category icon to expand the primitive block list.|
| 4 | ![image-20241031114830172](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/image-20241031114830172.png) | The icon on the left is the undo button, which can undo the last operation. The icon on the right is the redo button, which can redo the last undone operation.|

#### **Place primitives**

**1. Drag out the block: **After understanding the interface, we first open the first category in the lower left corner, select a primitive block from it and drag it to the blank space as the starting point of our logic![image-20241031171419878](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/image-20241031171419878.png)

**2. Connecting blocks**: We select a block with a depression on the top from the block list. We will find that when we drag the block to the bottom of the starting block, there will be a yellow UI prompt on the raised part below the starting block. When we release our fingers, we will find that the two blocks will automatically be adsorbed together. Then we have completed a simple logic. ![image-20241031171627914](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/image-20241031171627914.png)

**3. Fill in data: **First, we drag out the data in the primitive block or drag out the appropriate data type in the primitive list.

![image-20241031174335831](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/image-20241031174335831.png)

Then drag the data block to the corresponding data space. A yellow UI prompt box will appear in the data space, indicating that the current block type can be placed. When you release your finger, the data block will automatically be absorbed into the space. ![image-20241031175503431](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/image-20241031175503431.png)

> Note: When the filled data type is inconsistent with the data type in the space, the editor will have an obvious prompt and automatically pop up the data block that does not match the type.

![image-20241031183111256](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/image-20241031183111256.png)



**4. Disassembling blocks** When we move one of the multiple graphic blocks that are connected together, all the blocks connected below it will be taken away together.

![image-20241031182555866](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/image-20241031182555866.png)

**5. Delete blocks: **When you press and hold any graphic block, a 'trash can' will appear on the right side of the interface. We can delete the graphic block by moving it to the trash can.

![image-20241031182311721](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/image-20241031182311721.png)

Of course, we can also drag multiple blocks to the 'trash can' to delete multiple blocks at the same time.

![image-20241031183322347](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/image-20241031183322347.png)

Shape

| Block Description| Icon|
| ------------------------------------------------------------ | ----------------------------------------------------------- |
| Only the raised block below is the starting point of a logic. | ![image-20241030185836296](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/image-20241030185836296.png) |
| The block with only the sunken top is usually the end point of a logic. | ![image-20241030185844004](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/image-20241030185844004.png) |
| If there is no depression on the top and no protrusion on the bottom, it means that this block is a piece of data, which can be applied to other blocks as a parameter in some logical operations. | ![image-20241030185856813](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/image-20241030185856813.png) |
| If a block has both a raised top and a sunken bottom, it means that the block can be linked to other blocks with raised bottoms and can also be linked to more blocks below it. It can be a node of a logic. | ![image-20241031101239718](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/image-20241031101239718.png) |
| In the block classification, we will find a block with a special shape. This special block is a conditional expression, which is divided into external convexities and concave areas and internal convexities and concave areas. We can connect other blocks normally on the external convexities and concave areas of the conditional expression block like connecting other blocks, or we can link blocks inside the conditional expression, and the logic written inside it needs to meet a certain conditional logic before it can be calculated. | ![image-20241031101800841](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/image-20241031101800841.png) |

### Classification

In order to find the required blocks more efficiently in the primitive editor, we divide the blocks into 7 types.

As shown in the following figure:

| Type| Diagram| Overview|
| -------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Incident | ![SeaTalk_IMG_20241030_143100](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/SeaTalk_IMG_20241030_143100-1730270093809-7.jpg) | **Event type:** Generally, as the time point at which a logic starts, when we write the primitive logic, we first need to clarify at which time point we want this logic to be triggered. For example, when the player is resurrected, we want to give him a gun or when the round starts, we want to place an airdrop supply box in the center of the map, then 'When the player is resurrected' and 'When the round starts' are the time nodes required for this logic. |
| Entity | ![SeaTalk_IMG_20241030_143101](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/SeaTalk_IMG_20241030_143101-1730270723083-18.jpg) | **Entity type:** is an important concept in CraftLand (see 'Important concepts' for details). In the process of primitive editing, we often call or change the properties of an entity. |
| Game | ![SeaTalk_IMG_20241030_143105](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/SeaTalk_IMG_20241030_143105-1730270101855-11.jpg) | **Game Type:** In the Game type, we provide many commonly used functions for CL creators. These functions are usually settings that often need to be adjusted in some games. These functions are also very related to the gameplay, such as creating a monster, changing the skybox or joining a voice channel. |
| Data | ![SeaTalk_IMG_20241030_143106](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/SeaTalk_IMG_20241030_143106-1730270107552-13.jpg) | **Data type:** Data blocks can be parameters required for most logical operations. It can be a piece of data used in other blocks, or a piece of operation to calculate a value. |
| Logic | ![SeaTalk_IMG_20241030_143109](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/SeaTalk_IMG_20241030_143109.jpg) | **Logic type:** In the logic type, we provide multiple complex logic operations. This type of logic operation is often used when processing data. It can filter, judge or make decisions based on specific conditions. For example, determine whether a number is greater than another number, and then decide to take different actions. |
| Variable | ![SeaTalk_IMG_20241030_143111](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/SeaTalk_IMG_20241030_143111.jpg) | **Variable type:** In the variable type, we can create variables by ourselves. The variables created in this way are script variables, which are used for current script data processing. In other scripts, the variables can be obtained and set by external reference. |
| Function | ![SeaTalk_IMG_20241030_143113](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/SeaTalk_IMG_20241030_143113.jpg) | **Function type:** In the function type, you can create custom events. The custom events we create can encapsulate part of the logic, making the logic clearer, easier to understand and maintain. |

### Logical Element Block Description

| Block noun| Diagram| Description|
| -------------------------------------------- | ----------------------------------------------------------- | ------------------------------------------------------------ |
| Conditional statements (if statement) | ![image-20241104111959461](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/image-20241104111959461.png) | If the condition is met, the node under IF will be executed. |
| Conditional statements...else(if...else statement) | ![image-20241104112010284](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/image-20241104112010284.png) | If the condition is met, the node under IF will be executed. If the condition is not met, the node under ELSE will be executed. |
| Conditional loop (while statement) | ![image-20241104112023063](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/image-20241104112023063.png) | As long as the condition is met, the nodes below will be run in a loop. |
| Loop of integer rage (for index statement) | ![image-20241104112033968](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/image-20241104112033968.png) | Parameter i starts from the minimum value, and each time the lower node is run, i increases the step value until i is greater than or equal to the maximum value. |
| Loop every element (for each statement) | ![image-20241104112043683](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/image-20241104112043683.png) | For each KEY in the parameter list/dictionary, execute the node below once. |
| Check null | ![image-20241104112050652](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/image-20241104112050652.png) | Check whether it is a null value and handle the null value appropriately to avoid errors. |
| Continue to next | ![image-20241104112056253](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/image-20241104112056253.png) | Skip this loop and enter the next loop of the loop body. |
| Break loop | ![image-20241104112103316](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/image-20241104112103316.png) | Break the loop and continue executing the node after the loop body. |



## What is ECA?

In the context of code, ECA (Event-Condition-Action) usually refers to a rule representation method.

**I. Components**

1. Event

- A specific situation or occurrence that triggers the execution of a rule. For example, a player enters the game, a player causes a kill, or a player leaves the game.

**Example:** The player caused a kill, and after triggering this event, the player received 100 gold coins

![SeaTalk_IMG_20241101_114133](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/SeaTalk_IMG_20241101_114133.jpg)

2. Condition

- A logical expression that determines whether to perform subsequent actions after an event occurs. The corresponding action will only be performed if the condition is true. For example, if the number of zombies is less than 10, create a zombie, if the number of players is equal to 1, get a Gatling gun, or if the player's coordinates are equal to a certain value, teleport the player to another coordinate.

**Example:** When a player joins the game and has a microphone on, his name will become 'I have a microphone'![SeaTalk_IMG_20241101_143623](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/SeaTalk_IMG_20241101_143623.jpg)

3. Action

- If the event occurs and the conditions are met, the specific action will be performed. This can be to modify data, call a function, send a message, trigger another event, etc.
  

**Example:** Give the player an AK47 at the beginning of the round and set the player's health to 500

![SeaTalk_IMG_20241101_145943](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/SeaTalk_IMG_20241101_145943.jpg)

### Important concepts in ECA

| Concept Name| Description|
| ------ | ------------------------------------------------------------ |
| Function | A function (often called a method) is a reusable block of code that performs a specific task. A function encapsulates a specific operation or task in an independent method block, making operations and logic more modular and easier to maintain. External code can perform specific tasks by calling a function without having to understand the implementation details of the function. |
| Parameters | Parameters are values passed to functions or methods when they are called. They include formal parameters and actual parameters, which can be divided into parameter types to provide flexibility and data transfer, etc. |
| Enumeration| Enumeration is a concept of constant data collection, such as an attack method enumeration, which can contain options such as melee, shooting, explosion, etc. Different enumeration types cannot be assigned to each other, even if their values may be the same, they cannot be assigned due to different semantics. |



## Custom events & custom variables

### Custom Events

In the lower left corner of the element editor, we can find a total of seven types of element lists. In the function type, we can click [CREATE FUNCTION] to create a custom event![SeaTalk_IMG_20241101_150402](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/SeaTalk_IMG_20241101_150402.jpg)

![SeaTalk_IMG_20241101_150359](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/SeaTalk_IMG_20241101_150359.jpg)

#### Overview of the Custom Event Interface

| Serial Number| Image| Description|
| ---- | --------------------------------------------------------------- | ------------------------------------------------------------ |
| 1 | ![image-20241101151951739](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/image-20241101151951739.png) | Here we can fill in the name of the custom event|
| 2 | ![image-20241101151917848](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/image-20241101151917848.png) | Click the plus sign to add an internal parameter to the custom event. This parameter can only be used in the custom event to which it belongs. |
| 3 | ![image-20241101151927435](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/image-20241101151927435.png) | Click the plus sign in the lower right corner to add a return value to our custom event. When we call this event in other algorithm logic, we can get the data we want.|

#### Custom event description

When editing primitives, we will integrate multiple primitive blocks into a custom event. We can also say that we encapsulate multiple calculation logics in one method. There are several advantages to doing this:

**1. Clear naming: **Using encapsulated events, we don’t need to read complex primitive block logic, we can understand the entire event logic intent just by naming

**2. Simplify the primitive structure: ** Encapsulating complex calculations in custom events can make the logic of the main structure more concise and clear, reduce the complexity of the primitive structure, and improve readability.

**2. Reuse: **When multiple graphics logic blocks require the same operation, you can reuse the encapsulated custom event to avoid repeatedly writing the same graphics logic. Not only that, when we modify and maintain this custom event, we can also modify multiple graphics logic blocks that reuse the custom event at the same time to avoid repeatedly modifying the same code in multiple places.

### Custom variables

#### Overview of the Custom Variables Interface

In the element type list, select the [VARIABLE] type, and then click [CREATE VARIABLE] to create a custom variable

![image-20241101162644288](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/image-20241101162644288.png)

When creating a custom variable, we can set the variable name and the variable data type

![image-20241101162620704](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/image-20241101162620704.png)

#### Custom variable description

When we are writing graphic logic, we may sometimes need to define parameter variables of data types according to specific needs. The custom variable function solves this need.

The variables you create can also be used to pass data between different methods. By storing data in a variable, you can pass it as a parameter to another method or return it from a method to the caller.

### Custom event/variable example

> We will create a logic to demonstrate how to use custom events and custom variables in the primitive editor
>
> Example logic: When a player kills someone, the player's health limit will be reduced by 10 points, and the minimum will be reduced to 20.

1. First, we create a custom variable named 'CurrentMaxHp' and set the data type to 'int'. At the same time, we create a custom event named 'DecreaseMaxHp' as preliminary preparation

   ![SeaTalk_IMG_20241101_175037](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/SeaTalk_IMG_20241101_175037.jpg)

![SeaTalk_IMG_20241101_175059](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/SeaTalk_IMG_20241101_175059.jpg)

2. Find and drag out the 'When a player causes a kill' event, and connect it to the custom event 'DecreaseMaxHp' that we just created. After connecting, we have completed the logical basis for reducing the player's health limit when the player kills![SeaTalk_IMG_20241101_183151](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/SeaTalk_IMG_20241101_183151.jpg)

3. After completing the basic logic, we can start writing the primitive structure of the custom event. First, we assign the value of the variable we just created![SeaTalk_IMG_20241101_183704](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/SeaTalk_IMG_20241101_183704.jpg)

4. Next, connect an algorithm to set the variable to -10 each time an event is triggered![SeaTalk_IMG_20241101_183713](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/SeaTalk_IMG_20241101_183713.jpg)

5. Added the minimum health limit, added a check if the current health limit is less than or equal to 20, then the current health limit is equal to 20![SeaTalk_IMG_20241101_183808](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/SeaTalk_IMG_20241101_183808.jpg)

6Reassign the calculated variable to the player's life limit attribute. So far, we have completed all the required logic. ![SeaTalk_IMG_20241101_183902](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/SeaTalk_IMG_20241101_183902.jpg)

7. Verify![SeaTalk_IMG_20241101_184513](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/SeaTalk_IMG_20241101_184513.jpg)

The health limit is reduced correctly and verified correctly. ![image-20241101184737595](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/4_Block/image-20241101184737595.png)
