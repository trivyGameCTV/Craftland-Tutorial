# Scripts

Scripts are used to control the game's progress by manipulating specific objects under the right conditions, and thus realizing logic that is not possible or difficult to achieve by relying on self-contained objects.

## Distinction between script types 

## Block and code scripts 

We provide two ways to edit scripts: block scripts and code.

![image-20240718182931412](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240718182931412.png) 

Block scripts are more intuitive and easy to use with visual blocks for script editing. But the complexity rises faster and the script is more difficult to maintain when writing complex logic.

![image-20240718183124409](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240718183124409.png) 

Code Scripting Script editing using code is more free and maintainable when dealing with complex logic.

## Server and Client Scripts 

Regardless of block or code, scripts need to differentiate between running platforms: server or client.
Server scripts can only use events and interfaces supported by the server, and the same applies to clients.

![image-20240718183255210](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240718183255210.png) 

> Events that can only be run under the server platform 

## **Static Scripts**

A static script refers to a script that is automatically attached to the **global** entity by default.

It is a property of a script file and can be enabled or disabled on a client/server script.

For **Primitive (graph-based)** scripts, when selected in the **FE Project**, you will find a "Static" checkbox in the **Inspector** panel.

For **code-based** scripts, simply add the `static` keyword before the `graph` declaration, like this:

```go
static graph Test {
}
```

After editing the code, remember to go back to **FE** and save.

In the **Global** module of **FE**, you can browse all static scripts.

Using static scripts makes visual scripting easier. You can focus on editing them in the script editor without manually opening the global module and attaching them.

There is also an extra benefit for **code scripts**—a convenient syntax sugar available for static scripts:

```go
// GlobalManager.fcg
static graph GlobalManager {
    func MyFunc1() {
    }
    func MyFunc2() {
    }
}

// In another file
import "./GlobalManager.fcg" as GlobalManager
graph Test {
    event OnAwake() {
        GlobalManager.MyFunc1() // Call static script functions directly via dot notation
        GlobalManager.MyFunc2() // Equivalent to globalEntity<GlobalManager>.MyFunc2(), saves some typing
    }
}
```

Because static scripts are automatically attached to the global entity, their functions can be directly called by using the script name, without needing to reference `globalEntity`.

**Note:** A script attached to the global entity is **not** automatically considered a static script.
If you want to access `GlobalManager.MyFunc2` directly without specifying the entity, you **must** manually set the script as static.

![image-20240719152909186](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719152909186.png)

# Create a script 

Right click in the editable assets area to create a new script 

![image-20240719143643018](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719143643018.png) 

![image-20240719143706370](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719143706370.png) 

Select New when mounting the script: 

![image-20240719144041369](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719144041369.png) 

![image-20240719144112007](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719144112007.png) 

![image-20240719144219525](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719144219525.png) 

![image-20240719144236787](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719144236787.png) 

![image-20240719144248170](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719144248170.png) 

New scripts created in this way will be automatically mounted on the corresponding entity and will be automatically named with the name of the current entity.

When creating a script, you need to select/configure the category of the script: 

1. server script or client script, which affects the events and interfaces that can be used by this script.
2. block script or code script, this affects how the script is edited.

# Editing Scripts 

Double click on the script file to open it for editing, for block and code scripts please refer to the following documentation: 

[Block Scripts-User Manual](/en/tutorial/fe/1-8/)

[Code Scripts-User Manual](/en/tutorial/fe/1-9/)

# Mounting Scripts 

**Mounting to a Module**: 

![image-20240719145730470](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719145730470.png) 

![image-20240719145743950](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719145743950.png) 

**Mount to object**: 

Select the object you want to add script to, and choose Add Script in its inspector panel: 

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240929154213472.png" alt="image-20240929154213472" style="zoom:67%;" />

![image-20240719151758399](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719151758399.png) 

Again, you can select an existing script or create a new one.

**Adding scripts using scripts**: 

We provide an interface that can mount scripts for entities: 

Adding scripts: 

![image-20240719151930002](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719151930002.png) 

It is recommended that you use the Existing Scripts interface to confirm that the entity already has the same script before adding it.

![image-20240719152647755](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719152647755.png) 

# Uninstalling Scripts 

To statically uninstall a script before starting the game, simply find the mount and click the minus sign: 

![image-20240719152520504](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719152520504.png) 

To uninstall the script dynamically after the game has started, use the Delete Script interface: 

![image-20240719152550242](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719152550242.png) 

Again, we recommend confirming that the entity does indeed mount the script to be deleted before deleting: 

![image-20240719152717738](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719152717738.png) 

# Managing Script Files 

If you create a new script when adding a script, it will automatically create a new ECA folder under the Assets folder to hold the new script: 

![image-20240719153237929](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719153237929.png) 

> We also recommend that you use folders to categorize the scripts you create 

## Delete 

Scripts can be deleted by using the shortcut Delete, or by right-clicking on the script in the asset: 

![image-20240719153352815](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719153352815.png) 

For entities that already have this script mounted, an error with a yellow exclamation point will appear: 

![image-20240719153705926](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719153705926.png) 

## Copy 

Using the shortcut keys Ctrl+C, Ctrl+V, or using the right-click menu, you can copy the script. The copied script name is the name of the original script plus (X), and X is the number of copies - 1. 

![image-20240719153524358](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719153524358.png) 

## Rename 

Using the shortcut F2, or using the context menu, you can rename the script.

![image-20240719153932338](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719153932338.png) 

Scripts cannot be renamed, naming a script with the same name as an existing script will result in an error and cancel the renaming: 

![image-20240719154032997](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719154032997.png)
