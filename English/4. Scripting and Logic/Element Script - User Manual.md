# Block Script

This article introduces how to edit Block Scripts.

# Interface Description

![image-20240719154714450](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719154714450.png)

1. Canvas, the main editing area
2. The file currently being edited
3. Element classification, click any element to expand the element selection interface
4. Properties panel

# Element classification description

3. The graphic element categories corresponding to the regions are:

1. Search: Enter keywords to search for graphics.
2. Commonly used: The graphics set as commonly used graphics will be here.
3. Event: It will be triggered when the conditions are met, which is the beginning of logic.
4. Conditions: used for script flow control.
5. Behavior: actual operation on entities\data.
6. Modules: Some module-specific behaviors.
7. Data: Processing of data.
8. Variables: Use existing variables or add variables.
9. Function: Use or create a custom function.
10. External call: call custom functions of other scripts.

# **Use of graphics**

## Block Description

The bulge under the primitive indicates that other primitives can be linked to it.

![image-20240719162414368](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719162414368.png)

The depression above the primitive means that other primitives can be linked before this primitive, and it will only run after the preceding primitives run.

![image-20240719162458868](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719162458868.png)

If there is no depression on the top but a bulge on the bottom, it means that the primitive is the starting point of a logic segment, usually an event primitive.

![image-20240719162532230](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719162532230.png)

If there is no convexity or concaveness above or below, it means that the primitive is a piece of data and can be applied to other primitives.

![image-20240719162637872](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719162637872.png)

The primitives will have input and output parameters:

**Input parameters**:

The input parameter is blank by default, and the type marked inside it is the type of the required parameter.

![image-20240719163219101](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719163219101.png)

> The script name in this element is also a required parameter, but using the resource selector, you can directly select the corresponding resource in the project without considering type matching.

**Output parameters**:

The output parameters are colored squares by default, which can be dragged to fill in the required input parameter boxes:

![image-20240719163455421](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719163455421.png)

## Use of primitives

After selecting the element you want to use in the category, click or drag it to the canvas to use the corresponding element.

![image-20240719161426471](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719161426471.png)

![image-20240719161444643](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719161444643.png)

Using the primitive with the groove on top, you can join the two primitives together:

![image-20240719161910607](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719161910607.png)

![image-20240719161930593](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719161930593.png)

The logic of a group of primitives is always from top to bottom:

![image-20241105153444063](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20241105153444063.png)

![image-20241105153522814](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20241105153522814.png)


For a group of graphics elements connected in series, the necessary input parameters need to be filled with appropriate data to ensure the normal operation of the script. Inappropriate variables will result in an error. Click the error to see the error message:

![image-20240719163823327](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719163823327.png)

![image-20240719163854644](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719163854644.png)

When you drag an element, the elements below it will be dragged away as well:

![image-20240906110832061](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240906110832061.png)

![image-20240906110844840](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240906110844840.png)

Hold down the Ctrl key and drag to only drag the current element, and the elements below will automatically connect to the ones above:

![image-20240906110855565](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240906110855565.png)

## Element Properties Panel

Click on the element and it will be selected.

![image-20241122190755370](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20241122190755370.png)

In the Inspector panel on the right, you can view detailed information of the selected element, including its name, description, parameter name, parameter type, return value type, return value description, etc.

![image-20241122190944942](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20241122190944942.png)

# Flow Control

The default execution order of Block Scripts is from top to bottom. You may often need code flow control to implement complex logic.

Please refer to the following link for detailed instructions:

[Script Additional Notes](/zh-cn/tutorial/fe/1-10/)

# Variables

Three types of variables can be defined or modified at the variable location:

1. Global entity attributes: global component attributes, support customization. You can obtain or modify customized global entity attributes in any script.
2. Script variables: variables used only in the current script, other scripts can obtain and modify them externally.
3. Local variables: variables that are only used in the current code block and are invalid outside the code block.

## Global entity properties

Global entity properties can be added via the entity component properties in the component settings.

![image-20240719170731723](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719170731723.png)

![image-20240719170751222](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719170751222.png)

![image-20240719170812335](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719170812335.png)

After creating the global entity attribute, you can use Get Global Entity to obtain the attribute:

![image-20240719170915428](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719170915428.png)

Use the Set Global Entity to set this property:

![image-20240719170953632](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719170953632.png)

## Script variables

In the Variables category, there is a Create Variable button:

![image-20240719171622005](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719171622005.png)

![image-20240719171647910](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719171647910.png)

The variables created in this way are script variables and are used for data processing in the current script.

In other scripts, you can get and set this variable through external references:

![image-20240719171819031](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719171819031.png)

> Please note when referencing other scripts externally: when getting and setting, you need to specify the corresponding entity mounted by the referenced script.

## Local variables

The local variable primitive allows you to create variables that are only available in the current code block:

![image-20240719171508081](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719171508081.png)

You can rename a variable by double-clicking the variable name:

![image-20240719171540482](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719171540482.png)

A code block is a continuous sequence of primitives. It is worth noting that the "if-else" primitive in the conditional classification is two code blocks by default. Each "if", "else", and "else-if" is an independent code block.

![image-20240722192115698](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722192115698.png)

![image-20240722192055277](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722192055277.png)

# Custom functions

Both functions with and without return values are supported in Block Scripts.

A function with a return value cannot be linked to other entities when called. The calling entity is the return value.

![image-20240719180031043](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719180031043.png)

![image-20240719180117743](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719180117743.png)

Functions without return values can be linked to other primitives when called.

![image-20240719180039563](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719180039563.png)

![image-20240719180134147](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719180134147.png)

Wait: When the primitive is an asynchronous function, it will be blocked and the next primitive will be executed after the asynchronous function is executed.

Execution: If the primitive is an asynchronous function, it will not be blocked and the following primitive will continue to be executed.

An asynchronous function is a function that uses primitives that perform asynchronous processing, such as "wait".

![image-20240722105341566](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722105341566.png)

**Note**: Using asynchronous primitives in functions with return values is not supported.

![image-20240806115625031](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240806115625031.png)

If you need an asynchronous function to return a value, use a void function and use an output variable.

![image-20240806115658582](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240806115658582.png)

Regardless of whether a custom function has a return value or not, you can use the function's output variable below the calling primitive to obtain the output.

![image-20240806113746376](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240806113746376.png)

![image-20240806121329099](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240806121329099.png)

# Custom Events

In addition to the various events officially provided, you can also trigger logic through custom events.

![image-20250630114130051](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20250630114130051.png)

Click the button to perform custom event management:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20250630114142109.png" alt="image-20250630114142109" style="zoom: 67%;" />

Right-click in the custom events list to manage custom events:

![image-20250630114340277](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20250630114340277.png)

Click the + button to create a new custom event:

![image-20250630114208389](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20250630114208389.png)

Here you need to set the name of the custom event, the object type to which the custom event signal is sent, and the parameters. Only the specified object type can receive the signal that triggers the event.

![image-20250121181204861](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20250121181204861.png)

> Send a custom event to all players at the start of their turn

![image-20250121181429023](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20250121181429023.png)

> The player triggers the logic after receiving the custom event signal

# Search and common use of graphics elements

Enter keywords to search for corresponding elements

![image-20240719181845696](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719181845696.png)

In the element selection interface, right-click an element to set it as a frequently used element, and then you can quickly use the element in the frequently used element category.

![image-20240719182033312](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719182033312.png)

![image-20240719182130450](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719182130450.png)

# Example

Let's use a simple example to demonstrate the use of the script:

The design is as follows:

1. Each player will be given an M4A1 when joining the game.
2. When a player fires, 1 health point will be deducted from his own health each time he fires.

**Create Script**:

1. The requirement is global, 2. is for each player. So you need to mount a script globally and for each player. The server needs to know about the distribution of props and the deduction of life, so both are created as server scripts.

![image-20240719183317332](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719183317332.png)

![image-20240719183333435](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719183333435.png)

**Edit Script:**

For 1, each player who joins the game needs to issue props once:

![image-20240719183627320](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719183627320.png)

For adding props primitives, three parameters are required: the target for adding props, the props to be added, and the number of props to be added.

The target of adding props is the player who triggered the event when the player joins the game. The prop is selected as M4A1 through the resource manager, and the quantity is 1.

![image-20240719183756275](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719183756275.png)

For 2, a health deduction needs to be performed every time a shot is fired:

We find that the primitives do not actually have their health deducted:

![image-20240719183925677](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719183925677.png)

> Filling in negative numbers in the health recovery primitive's parameters will not deduct health

However, as a player attribute, health can be adjusted by setting properties:

![image-20240719184034769](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719184034769.png)

To set the attribute primitive, you need the entity to be set, the attribute and value to be set, and several parameters to be calculated.

The entity whose attributes are set is the current player, so you can use this entity and double-click the parameter position to quickly fill in this entity.

![image-20240719184236329](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719184236329.png)

The attribute value that needs to be changed is the current health value, select the current health value.

The set value is the current health value minus 1, so the current health needs to be obtained.

![image-20240719184443713](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719184443713.png)

Use the subtraction method in data classification to reduce it by one and add parameters:

![image-20240719184604249](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719184604249.png)

![image-20240719184622223](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719184622223.png)

You can also use the operation of setting attribute primitives directly to implement this logic:

![image-20240719184700828](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719184700828.png)

Run the debugger to view the results:

![image-20240719184826220](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719184826220.png)

> Everyone was issued an M4A1.

![image-20240719184935284](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719184935284.png)

> Fired 8 times and lost 8 health points.
>
> When firing, it is triggered every time a firing command is executed. The shooting of a burst weapon before the weapon is lowered is considered as one firing, and this event can only be triggered once.
