# Script - User Manual

Scripts are used to control the game process, operating on specific objects under appropriate conditions to achieve logic that cannot be easily accomplished with built-in objects.

## Distinction of Script Types

### Visual and Code Scripts

We offer two ways to edit scripts: Visual and Code.

![image-20240718182931412](./img/image-20240718182931412.png)

Visual scripts use visual elements for script editing, making it more intuitive and easier to operate. However, complexity increases rapidly when writing complex logic, making maintenance difficult.

![image-20240718183124409](./img/image-20240718183124409.png)

Code scripts use code for script editing, offering high flexibility and strong maintainability when handling complex logic.

### Server and Client Scripts

Regardless of visual or code, scripts need to distinguish the running platform: server and client.
Server scripts can only use server-supported events and interfaces, and the same applies to the client.

![image-20240718183255210](./img/image-20240718183255210.png)

> Events that can only run on the server platform

### **Static Scripts**

Scripts can be configured as static scripts:

![image-20240719152909186](./img/image-20240719152909186.png)

Static scripts always run under the global module.

![image-20240719153023952](./img/image-20240719153023952.png)

Static scripts can also be mounted on other entities, but be cautious of conflicts with the logic on global entities.

![image-20240722180436604](./img/image-20240722180436604.png)

> Mounting a static script New ECA.eca on a global entity will trigger internal events twice. (Not recommended)

![image-20240722180506048](./img/image-20240722180506048.png)

![image-20240722180749960](./img/image-20240722180749960.png)

> Configuring New ECA.eca on both Global and Player will trigger internal events once on each entity if supported.

## Creating Scripts

Right-click in the editable assets area to create a new script.

![image-20240719143643018](./img/image-20240719143643018.png)

![image-20240719143706370](./img/image-20240719143706370.png)

Select "Create New" when mounting a script:

![image-20240719144041369](./img/image-20240719144041369.png)

![image-20240719144112007](./img/image-20240719144112007.png)

![image-20240719144219525](./img/image-20240719144219525.png)

![image-20240719144236787](./img/image-20240719144236787.png)

![image-20240719144248170](./img/image-20240719144248170.png)

Scripts created this way will automatically mount on the corresponding entity and be named after the current entity.

When creating a script, you need to choose/configure the script type:

1. Server or client script, which affects the events and interfaces available for use.
2. Visual or code script, which affects the editing method.

## Editing Scripts

Double-click the script file to open it for editing. For editing visual and code scripts, please refer to the following documents:

[Visual Script - User Manual.md](Visual Script - User Manual.md) 

[Code Script - User Manual.md](Code Script - User Manual.md) 

## Mounting Scripts

**Mounting on Modules**:

![image-20240719145730470](./img/image-20240719145730470.png)

![image-20240719145743950](./img/image-20240719145743950.png)

**Mounting on Objects**:

Select the object you want to add a script to, then choose "Add Script" in its inspector panel:

<img src="./img/image-20240719151733528.png" alt="image-20240719151733528" style="zoom:67%;" />

![image-20240719151758399](./img/image-20240719151758399.png)

You can choose an existing script or create a new one.

**Adding Scripts via Scripts**:

We provide an interface for mounting scripts on entities:

Add a script:

![image-20240719151930002](./img/image-20240719151930002.png)

We recommend using the "Check if Script Exists" interface before adding a script to confirm whether the entity already has the same script.

![image-20240719152647755](./img/image-20240719152647755.png)

## Unmounting Scripts

To statically unmount scripts before game launch, simply find the mounting location and click the minus sign:

![image-20240719152520504](./img/image-20240719152520504.png)

To dynamically unmount scripts after game launch, use the "Delete Script" interface:

![image-20240719152550242](./img/image-20240719152550242.png)

Similarly, we recommend confirming that the entity indeed has the script you want to delete before proceeding:

![image-20240719152717738](./img/image-20240719152717738.png)

## Managing Script Files

When creating a new script while adding one, an ECA folder will automatically be created under Assets to store new scripts:

![image-20240719153237929](./img/image-20240719153237929.png)

> We also recommend using folders for categorizing created scripts

### Deleting

Use the Delete shortcut key or right-click on assets to delete scripts:

![image-20240719153352815](./img/image-20240719153352815.png)

Entities that have this script mounted will show a yellow exclamation error:

![image-20240719153705926](./img/image-20240719153705926.png)

### Copying

Use Ctrl+C, Ctrl+V shortcuts or right-click menu to copy scripts. The copied script name will be the original name plus (X), where X is copy number -1.

![image-20240719153524358](./img/image-20240719153524358.png)

### Renaming

Use F2 shortcut key or right-click menu to rename scripts.

![image-20240719153932338](./img/image-20240719153932338.png)

Scripts cannot have duplicate names; if you attempt to rename with an existing name, an error will occur and cancel the renaming:

![image-20240719154032997](./img/image-20240719154032997.png)
