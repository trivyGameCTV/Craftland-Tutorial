# Code Scripts

Introduces how to edit code scripts 

# Introduction to the concepts 

## Server Scripting and Client Scripting 

Scripts for different runtime platforms can use different events and interfaces. The scope of application of the element can be confirmed by querying the library.

Server scripts and client scripts cannot call each other directly, they can only notify the other end of the call by means of events.

Scripts have a .fcg extension. 

## Libraries 

Libraries have a .fcc extension 

Standard libraries are automatically added when a code script is created: 

![image-20240719185712867](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719185712867.png)

Standard library file: 

![image-20240719190200738](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719190200738.png)

![image-20240719190137198](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719190137198.png)

 The [platform_server] tag indicates that the platform to which this element applies is a server, and only server scripts may use this element.

The [platform_Client] tag indicates that the element applies to a client platform. Only client scripts may use this element.

Unlabeled elements can be used by both servers and clients.

[deprecated] means that the element has been deprecated, please do not use these elements.

There are official libraries in the editor path: \Craftland Studio\resources\LocalData\Utilities\UGCLanguage\release, you can refer to them as needed.

![image-20240719190423285](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719190423285.png)

Open any code script that references a library, hold down the Ctrl key and click on the library to jump directly to it.

![image-20240723163029073](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240723163029073.png)

![image-20240723163048981](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240723163048981.png)

> release is the path where the official library files are stored 

To use a library, you need to reference it in the header of the file, with the syntax: 

import "library file" as alias 

For official library files and new custom library files created within the editor, you don't need to add the path.

![image-20240719190631821](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719190631821.png)
> EditorGenlib.fcc is the library that holds the registered assets, mainly used for referencing block scripts 
> Support for player customized libraries, please see the section related to custom libraries below.

# Environment Preparation 

## VS Code Plugins 

### Installing Plugins 

Plugins have been released to VS Code's Plugin Marketplace, search for Free Fire Craftland Code or some of the keywords at VS Code Plugins: 

![image-20240723155136776](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240723155136776.png)

Just click Install.

After the installation is complete, you can find the plugin named `Free Fire Craftland Code` in the list of installed plugins. Open the code script file with VS Code and see the corresponding syntax highlighting in effect, which means that the plugin has been successfully installed.

![image-20240722105923448](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722105923448.png)

![image-20240722105939568](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722105939568.png)

### Important Features 

Plugin details can be found in the plugin's description in VS Code. Here are some important plugin features.

1. **Code Snippet Completion**: When inputting fixed format code snippets such as Bezier curves, vectors, etc., but more complex code snippets, you only need to input keywords to trigger the code snippet completion.

![image-20240722113232402](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722113232402.png)
![image-20240722113251580](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722113251580.png)

![image-20240722113318631](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722113318631.png)
![image-20240722113337989](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722113337989.png)

![image-20240722113419454](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722113419454.png)
![image-20240722113435218](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722113435218.png)

Auto-completion with this tag is code snippet completion in the plugin.

![image-20240722113517257](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722113517257.png)
![image-20240722113537919](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722113537919.png)

> The first if in the picture is the keyword complement that comes with VS, and the second to the fourth are the three different code snippets defined in the plugin. 

2. **Intelligent Hints and Completions**: auto-completion of variables that have appeared in the context, auto-completion of events and API names, and hints on formal parameters and return value information when calling functions. function's formal parameter and return value information, and automatically reference the library when using events or APIs that do not reference the library.

![image-20240722114721601](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722114721601.png)

![image-20240722114805025](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722114805025.png)

![image-20240722114830464](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722114830464.png)

3. **Diagnostics**: code with syntactic and semantic errors is marked red 

![image-20240722114858814](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722114858814.png)

Hover over the error to display an error message: 

![image-20240722115123382](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722115123382.png)

should read: 

![image-20240722114952927](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722114952927.png)

4. **Hover Tip**: mouse over the code of interest to see details 

![image-20240722115156280](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722115156280.png)

5. **Jump to Definition**: You can jump to the definition location by F12 or right clicking the corresponding code 

![image-20240722115231984](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722115231984.png)

![image-20240722115302977](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722115302977.png)

# Script Structure 

The following is an overview of the structure of a coded script. A coded script file contains three sections: 

- Script Members 
- Variable Definitions 
- Function Definitions 
- Event Definitions 

This means that a first class member of a script can only be one of these three categories.

```golang 
graph script name { 
script variable name type = initial value 

	func function name (list of formal parameters - optional) { 
		//do sth...
	} 

	event listener event name() { 
		//do sth...
	} 
} 
```

We introduce the notion of a `block of code`, which is the content of code wrapped in a set of curly braces `{...} ` wrapped in a set of curly braces.

As an example, it would be wrong to write an expression like calling log printing directly in a first-class member of a script, but it could be written in a block of code for a function or an event: 

```golang 
graph Demo { 
	//LogInfo("Hello") // This is the wrong place to write it 

	func Hello() { 
		LogInfo("Hello" ) // Can be written in a function or event block 
	} 

	event OnAwake() { 
		LogInfo("Hello") // Can be written in a function or event block 
	} 
} 
```

# Edit Related 

## Basic Syntax 

The basic syntax of the code script can be found in detail in the corresponding section of the link below: 

[Script Additional Instructions](/en/tutorial/fe/1-10/)

## Data Types 

The data types of the code scripts can be found in detail in the corresponding section of the link below: 

[Script Additional Instructions](/en/tutorial/fe/1-10/)

## Operators 

Operators are used to perform mathematical or logical operations while the program is running.

The built-in operators are: 

- Arithmetic operators 
- Relational operators 
- Logical operators 
- Assignment operators 
- Other operators 

The operators of the code scripts can be found in detail in the corresponding section of the link below: 

[Script Additional Instructions](/en/tutorial/fe/1-10/)

## Flow control 

The default execution order of code lines is top-down, but in order to realize more complex flow control, we need to introduce flow control statements.

For the flow control of code scripts, you can check the corresponding section of the following link for details: 

[Script Additional Instructions](/en/tutorial/fe/1-10/)

## Variables 

Variables need to be declared in the code before they can be used, i.e. created. There are several types of variables: 

### Local Variables 

The general form of declaring a local variable is to use the `var` keyword, whose type can be automatically inferred by the compiler in the case of a right-side assignment statement, otherwise it should be declared actively.

The scope of a local variable is from the location of its declaration to the end of the statement block in which it is placed.

```go 
func Demo() int { 
    //complete statement 
    //var value int = 10 
    // omit type declaration 
    //var value = 10 
    // omit right hand side assignment statement 
    var value int 
    value = 10 //ok 
    if value == 10 { 
        var localVar = 20 
        value = localVar //ok 
    } 
    value = localVar //not ok 
    return value 
} 
```

### Script variables 

Script variables are scoped to the current script, and can be accessed by entity instances in other scripts.

``` go 
graph HelloWorldGraph { 
	SayTipWords string = "Hello, " // script variable 

	func SayHello(name string) { 
		std.PrintString(SayTipWords + name) 
	} 

	event OnAwake( ) { 
		start SayHello("FF_UGC") 
	} 
} 
```

### Component Properties 

Component properties are scoped to the current component, and component properties are all publicly available data that can be accessed through entity instances in any script.

``` go 
graph EntityDataStore { 
    func EntityPropModify(input int) int { 
        thisEntity.EcoKillMoney = input 
        return thisEntity.EcoKillMoney 
    } 

    func EntityPropModifyV2(input int) int { 
        thisEntity<std.Global>.EcoKillMoney = input 
        return thisEntity<std.Global>.EcoKillMoney 
    } 
} 
```

### Value and Reference Types 

bool, int, float, string and Vector2, Vector3, Quaternion are all basic types that are value types; a value type cannot be nil and must have a value. Value types make a value copy when they are assigned a value.

List\<T>, Map\<T>, and entity\<T> are all reference types and can have a value of nil. a reference type only changes the address it points to when it is assigned a value, and a change in the contents of the address changes the values of all the variables that point to it.

## Functions 

A function is a block of statements that organizes a number of related statements together to perform a task. To use a function, you need: 

- define the function 
- call the function 

### Define a function 

When defining a function, you are actually declaring the relevant elements of the function, which has the following basic structure: 

```golang 
func function name(formal parameter argument name formal parameter type, ...) return value type { 

} 
```

Here is a simple example: 

```golang 
func TryAddExp(player entity<Player>, exp int) bool { 
    //...
    return false 
} 
```

### Calling a function 

You can call it using the function name, here is a simple example: 

```golang 
event OnAwake() { 
    //...
    // Call the user function of the current script 
    var isSuc = TryAddExp(curPlayer, 15) 
    // Standard library call 
    LogInfo(Format("AddExp %v:%v", List<object>{curPlayer, isSuc})) 
} 
```

### Synchronous and asynchronous functions.

A synchronous function is one that executes and returns immediately, with no asynchronous processes in between; 

An asynchronous function is one that uses an API within the function's implementation that does asynchronous waiting, such as `WaitForSeconds`.

Syntactically, asynchronous functions must be declared with the `async` keyword: 

```golang 
async func ShowGameTime(){ 
    while(thisEntity<Global>.GameTimeMs < 10000){ 
        LogInfo("GameTime:" + thisEntity<Global>.GameTimeMs) 
        WaitForSeconds(1000) 
    } 
} 
```

#### Calling Asynchronous Functions 

When calling an asynchronous function, we can choose the way it is executed: 

- start 
- call the asynchronous function, don't block, continue to the next line 
- wait 
- call the asynchronous function, block until the the asynchronous function finishes before executing the next line 

By default, the default is wait, which waits for the asynchronous function to execute.

```golang 
event OnAwake() { 
    LogInfo("1") 
    start TryAddExp(curPlayer, 15) 
    LogInfo("2") 
    wait TryAddExp(curPlayer, 15) 
    LogInfo("3") 
} 
```

#### Asynchronous function's Contagious 

If an asynchronous function is called in a custom function that chooses to be called as `wait`, the custom function must also be declared as `async`: 

```golang 
async func ShowGameTime(){ 
    while(thisEntity<Global>.GameTimeMs < 10000){ 
        LogInfo("GameTime:" + thisEntity<Global>.GameTimeMs) 
        //async's API 
        WaitForSeconds(1000) 
    } 
} 

async func Start() { 
    //wait a function of async 
    wait ShowGameTime() 
    LogInfo("Show End!") 
} 
```

#### Output parameters 

The return statement can be used to return only one value from a function. However, you can use out to return multiple values from a function, and the output parameter assigns the data output by the function to itself.

The basic form is as follows: 

``` 
out var form_parameter_name 
```

Here is an example: 

``` golang 
import "StdLibrary.fcc" as std
import "List.fcc" as list
import "EconomyModule.fcc" as economy

graph APIOutParam {
    func CreateWallet() int {
        NewWalletForEntity(nil, thisEntity, out var walletEntity)
        IncreaseMoneyForWallet(walletEntity, MoneyType.Basic, 1)
        return Length(walletEntity<Wallet>.Content)
    }
}
```

The output parameter must be explicitly declared to be an output parameter of out both at the time of definition and at the time of call; it is essentially the definition of a local variable at the function call, and the assignment of values to this local variable defined outside the domain inside the function. Assigning a value to this local variable defined outside the domain.

## Custom libraries 

Support user to create custom library file, create library file by creating new library file when you create new script at asset.

![image-20240719190920241](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719190920241.png)

![image-20240719191028356](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719191028356.png)

Custom events, components, types, enums are supported within the custom library.

### Custom events 

Register the needed events in the library: 

![image-20240719191343645](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719191343645.png)

The event logic needs to be written in a code script, and the code script with the event logic written in it needs to be guaranteed to run when used.

![image-20240723154821356](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240723154821356.png)

> DispatchEvent is an interface for customizing events. When an event is activated, you can send a custom event signal to the library, and the event in the library will receive the signal to trigger the event logic.

### Custom components 

Refer to the standard library definition of components: 

![image-20240723145305081](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240723145305081.png)

Abstract component: 

![image-20240723145331257](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240723145331257.png)

When defining a component, you can also define the properties in it.

### Extending official component properties 

You can extend official component properties using the partial keyword: 

![image-20240723164549184](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240723164549184.png)

### Custom enumeration 

![image-20240723164601600](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240723164601600.png)

## Game Data in EditorGenlib.fcc 

Some game data will be stored in EditorGenlib.fcc automatically, no need to be edited by user. They are: 

1. game stage index.
2. custom currency.
3. tags.

If these game data are used, they will be automatically stored in EditorGenlib.fcc as enumerations, and thus can be used in the code.

Game stage index: 

![image-20240929180058516](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240929180058516.png)

Custom Currency: 

![image-20240929180123767](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240929180123767.png)

Custom Label: 

![image-20240929175956081](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240929175956081.png)

After editing this data in the editor, the corresponding enumeration can be found in EditorGenlib.fcc: 

![image-20240929180301214](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240929180301214.png)

## Import scripts 

can import library files and code scripts.

Library files contain type definitions, component definitions, event definitions, API definitions, script declarations, and so on.

Script files contain script property definitions, event handler functions, customized functions, and so on.

The import method is as follows: 

```golang 
import "file path" as alias 
```

The following is an example of importing standard library and custom library files: 

```golang 
import "StdLibrary.fcc" as std 
import "./MyEditorGenLib.fcc" as gen 
```

- When the file path is a filename, it will be looked up from the standard libraries included in the compiler 
- When the file path is a file path, it will be looked up according to the file path 

## Importing Block Scripts 

Block scripts will be stored in the EditorGenlib library in the form of one graph per file. To reference a graph script, you need to note: 

1. When the block script is a non-static script, you need to specify the entity on which the script is mounted at the time of use.

![image-20240723165142341](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240723165142341.png)

> ECA2 is a block script that is mounted on the player entity and has member MyFunction9982. 

2. The name of the block script cannot be a reserved keyword.

When the block script name is a keyword, the script must be changed by the following method before it can be successfully referenced: 

Right-click on the block script, select Modify Script Name, and make the change. This operation does not affect the displayed file name, but simply modifies the name of the script used for the code.

![image-20240722154723034](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722154723034.png)

![image-20240722154740629](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722154740629.png)

> The keyword cannot be used as a user-defined marker, not limited to custom block script names.

For block scripts that fulfill the conditions, the following statement can be used: 

```golang 
import script name from "EditorGenLib.fcc" 

//or 

import script name as script alias from "EditorGenLib.fcc" 
```

can be used to view the script names and aliases by accessing the EditorGenLib.fcc library file. View the script name and path information of the script 

![image-20240722154942791](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722154942791.png)

Here is an example of the import: 

```golang 
import Global1 as GLB from "EditorGenLib.fcc" 
```

## Accessing Assets 

While scripts can use some constants and literals to specify the asset id, the This approach is less maintainable and prone to problems. Therefore, to access assets in scripts, you need to use asset registration.

### Asset Registration 

Open the Asset Registration menu by clicking Tools - Script Tools - Script Asset Registration in the FE Editor: 

![image-20240723161452674](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240723161452674.png)

![image-20240723161507741](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240723161507741.png)

On the left hand side, select the asset class you want to register, and then select the plus sign to add a registered asset: 

![image-20240723161550621](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240723161550621.png)

![image-20240723161601536](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240723161601536.png)

Enter a legal key name and select the corresponding asset.

![image-20240723161645145](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240723161645145.png)

Click the Save button below to complete the asset registration.

![image-20240723161707124](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240723161707124.png)

> Special attention to Scene and UI. 
> There are objects in the Scene and widgets in the UI. You can register both the Scene and the UI, as well as the objects and widgets in them. 
> But there is a sequence of registration: make sure that the Scene and the UI files have been registered before you can register the objects and widgets in them. 

### Static Calls 

Call the corresponding assets in the script using the static call syntax in the FE Editor menu: 

![image-20240723162337457](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240723162337457.png)

![image-20240723162359710](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240723162359710.png)

Statically called assets can be viewed at Enumeration in the EditorGenLib.fcc library

![image-20240723182251643](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240723182251643.png)

### Dynamically called 

Assets accessed based on enumerations are convenient but lose flexibility: consider a scenario where the mapping of an item in the game is determined by configuring the csv table. This is when assets need to be accessed dynamically.

In EditorGenLib.fcc, a special Res graph is generated. its member variables are the maps that collect each asset. 

![image-20240723182513253](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240723182513253.png)

The value of the map is the corresponding asset ID, so an enumeration EResKeyXXX is generated based on the type of asset, and registered assets are populated into the enumeration by auto-completion: 

![image-20240723182603330](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240723182603330.png)

Based on map access, the need for dynamic access to assets can be realized. For example, an asset key read from csv can be used directly as an index to a map.

```go 
var CSVKey string 
// ...
// Get the key by reading the csv table 
var MySceneID = Res.Scene[CSVKey] 
```

## Compile 

Starting a DEBUG or saving the project will compile it automatically.

In VS Code, use the shortcut Alt+B to manually compile the current file.

> This is a feature of the Free Fire Craftland Code plugin 

In the FE editor, use the shortcut Alt+B to compile manually.

Compilation errors and messages can be viewed in the console of the corresponding software.

![image-20240723162639185](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240723162639185.png)

![image-20240723162659201](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240723162659201.png)

# Example 

Demonstrates how to make a code script work with a simple example: 

Customize a function in a block script that has the effect of printing the log "start". In the custom code script, make the custom function run every time the player fires, and after the "start" printout, the player's life is deducted by 25 if the player's life is greater than 25 or more, and by 1 if the player's life is less than or equal to 25.

> This is a pointless requirement setup, only used to show how to use the block script 

First implement the custom function in the block code. The function is called TestFunc. The script is called CustomFunc. 

![image-20240722170832760](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722170832760.png)

> Because the script file is named CustomFunc and is not a reserved keyword, there is no need to change the script name additionally.

Set this block script file as a static script for subsequent references. If not set as a static script, the script needs to be mounted on an entity that is active in the game and used when referencing it.

![image-20240722163322115](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722163322115.png)

A new code script is created and configured as a server script because decreasing lifesteal is a message that requires communication with the server. Also since each time the player fires is an event that needs to listen to the player's behavior, choose to mount this script on the player entity.

![image-20240722160613935](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722160613935.png)

![image-20240722160622197](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722160622197.png)

Open Player.fcg for editing: 

![image-20240722160649095](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722160649095.png)

First make sure the event trigger is when the player fires, try to select the corresponding event via VS Code autocompletion: 

![image-20240722161330315](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722161330315.png)

Auto-completion of the event will find that the Player library where the event is located is automatically referenced: 

![image-20240722161411103](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722161411103.png)

If you don't pick the event you want by auto-completion or you're not sure about the event, you can directly open the library of the corresponding module and search for it.

![image-20240722161542188](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722161542188.png)

After the player fires, you need to run the custom function first: TestFunc(), which requires a reference to CustomFunc.eca. 

![image-20240722161826722](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722161826722.png)

TestFunc() as a member of CustomFunc can be quickly filled in via "alias. " for quick filling: 

![image-20240722161915819](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722161915819.png)

-25 the current player's life value property. 

![image-20240722171044036](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722171044036.png)

Need to make a judgment on the player's current life value, and only set it to 1 if it is insufficient: 

![image-20240722171716691](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722171716691.png)

Because the script structure restricts that only one level of structure can exist under: function, event or variable definitions.

So you need to wrap a layer of functions around the conditional judgment.

![image-20240722171747144](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722171747144.png)

You can also use the following code to quickly handle the HP minus 25 logic: 

```golang 
thisEntity<Player>.HP -= 25 
```

Run the test: 

![image-20240722171851643](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722171851643.png)

![image-20240722171911458](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240722171911458.png)

behaves as expected.

Here is the code for the code script: 

```golang 
import "StdLibrary.fcc" as StdLib
import "EditorGenLib.fcc" as EditorLib
import "Player.fcc" as Player
import CustomFunc as Custom from "EditorGenLib.fcc"

graph Script {
    func DmgWhenFire(){
        if thisEntity<Player>.HP>25 {
            thisEntity<Player>.HP = thisEntity<Player>.HP-25
            //thisEntity<Player>.HP -= 25
        }else {
            thisEntity<Player>.HP = 1
        }
    }
    event OnStartFire() {
        Custom.TestFunc()
        DmgWhenFire()
    }
}
```
``