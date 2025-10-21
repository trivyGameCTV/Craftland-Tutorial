# Behavior Tree

A Behavior Tree is a behavior decision model that can be used to set the behavior of any object that can mount a Behavior Tree entity component, such as a monster or a custom NPC.
The tree structure used by the Behavior Tree conforms to the way humans think, making behavior design more intuitive. Modularity also helps developers make modifications and adjustments.
In this tutorial, you will learn how behavior trees work and how to create one. In the example, you will learn how to create a behavior tree for a zombie that can patrol and chase the player.

## Structure and logic of behavior trees

A behavior tree consists of logical and leaf nodes and a special root node.

The behavior tree will traverse all executable nodes in the behavior tree in the defined order at each Tick (one or more frames, which can be modified in the properties of the behavior tree) and finally stop at a node.

The behavior tree will start from the root node and execute in order from left to right and top to bottom until it stops at a node or traverses all connected behavior tree nodes.

The behavior tree always starts execution from the root node, so only nodes directly or indirectly connected to the root node will be executed.
The execution order of the nodes is indicated by a numerical sequence in the editor, and nodes that will not be executed have no sequence number.
Every Tick, when the behavior tree stops at a node, the nodes whose execution order is after this node will not be executed.

## Behavior tree nodes

Root node: the initial node of each tree. All logic starts running from the root node. The root node is automatically created and cannot be deleted.

Logic node: nodes classified as Composite or Decorator. Logic nodes determine the logic of the child nodes. Logic nodes cannot be used as the last node of a branch.

Leaf node: nodes classified as Condition or Action. Leaf nodes determine the actual behavior of entities. Leaf nodes must be used as the last node of a branch.

## Creating a Behavior Tree

You can create a Behavior Tree file by right-clicking in the Assets window. You can also manage Behavior Tree files in the Assets window. Behavior Tree files have the extension .xbt.

![image-20240620150729511](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/25-BehaviorTree/create.png)

## Mounting a Behavior Tree

Before you can mount a behavior tree for any entity, you must first add the “Mountable Behavior Tree Entity” component to the inspector panel.
After you have added the “Mountable Behavior Tree” component, you can quickly mount the behavior tree file.

![image-20240620152117511](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/25-BehaviorTree/image-20240620152117511.png)

![image-20240620152208478](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/25-BehaviorTree/image-20240620152208478.png)

Only one behavior tree can be attached to each entity.

## Editing a behavior tree

Opening a behavior tree file opens the edit behavior tree panel.

![image-20241024151910366](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/25-BehaviorTree/image-20241024151910366.png)

The behavior tree editing panel is divided into three parts:

1. Node list

2. Canvas

3. Inspector

![image-20240620155309426](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/25-BehaviorTree/image-20240620155309426.png)

### Node list

All officially provided, custom and imported nodes are displayed here.
Drag and drop nodes into the canvas to create a new corresponding node.
Node search is supported.
The buttons in the upper right corner can be used to create custom nodes or import nodes.

#### Custom nodes

![image-20241024151959771](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/25-BehaviorTree/image-20241024151959771.png)

Click the “+” in the upper right corner to open the Create Node panel. In the Create Node panel, you can customize the following properties of the node:

1. Node name.
2. Node type. Currently, only custom Action and Condition nodes are supported.
3. Node script. Currently, in the Create Node panel, only existing scripts can be added to custom nodes, and editing is supported after creation.
4. Node variable type. You can create custom properties for the node to facilitate script invocation.
5. Node description.

Among the above, except for 2. Node type, all support modification after creation.

#### Import node

Click the Import button in the upper right corner to open the import file selection UI.
You can import nodes from other projects, with a .xbttemp extension.
When importing, be aware that the imported nodes may have scripts that do not exist in this project.



> Important! Modifying nodes in the node list will not affect nodes that have already been dragged into the canvas.

### Canvas

The canvas is the main area for editing the behavior tree. After dragging nodes from the node list into the canvas, you can arrange the behavior tree nodes in any order and edit their execution order by connecting any two nodes with a connection line from “out” to “in”. The canvas always contains a fixed root node.

When connecting from the “out” tab of one node to the “in” tab of another node, we call the “out” connected node the parent node (output node), and the “in” connected node the child node (input node).
Depending on the node type, nodes can have one or more “outs”, but only one “in” (except for the root node, which has no corresponding input node).

The behavior tree will only execute nodes that are directly or indirectly connected to the root node, which are called activated nodes. The canvas will automatically identify the activated nodes and sort them in the order from left to right and top to bottom. The gray number in the upper right corner of the node is the order in which it is called. Nodes that are not activated will not display a number.
![image-20240624142617006](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/25-BehaviorTree/image-20240624142617006.png)

> You can drag the panel by pressing and holding down the left or middle mouse button.
> Zoom in and out of the panel by pressing Ctrl and scrolling the mouse wheel.

### Node view panel

Each node in the canvas contains the following information or part of it: basic node information, script, and node variable list.

Node basic information: includes the node ID, node name, node type, and node description.
Script: the script attached to this behavior tree node. A behavior tree node can only be attached to one script. The script controls the behavior that the behavior tree needs to execute when it runs to this node.
Node variable list: some variables required for the node to run, some provided by the official, and some added by the creator when creating the node.

The ID is automatically assigned in the basic information of the node, and the other information can be fully modified in the node list on the left. However, only the node name can be modified for nodes dragged into the canvas.
Scripts can be added when creating a node or edited in the canvas, but only one script can be attached to a node.
The node variable list can be set when creating or in the canvas.
>Always remember that the node in the variable list is not the same as the node in the canvas. The specific behavior tree uses the data of the node in the canvas as the standard.

## Behavior tree node types

There are four types of behavior tree nodes: Action, Condition, Composite, and Decorator.

The nodes in the Composite and Decorator categories are logic nodes and cannot be used as the last node on a branch.
The Action and Condition nodes are leaf nodes and can only be used as the last node on a branch.

### Action

Action nodes represent the “actions” that need to be performed by the behavior tree. Except for the official node “Wait @ms”, all other actions are created and defined by the creator. Actions are often used to make behavior tree entities or their parent entities perform specific actions. Action nodes can be used to create modular custom actions, such as going to a specific location, releasing a specific skill, and activating a specific effect.
There are only two possible results of executing an Action node: Complete and Running.

- Wait @ms: This node contains a variable “WaitTime” that is used to wait for a specific period of time (in milliseconds, the specific waiting time is the value of the “WaitTime” variable) during the execution of the behavior tree. While the waiting time has not expired, this node will always return “Running”, and after the waiting time node, this node will return “Complete”.

> Note: Since the behavior tree is executed once per Tick, using the “wait” block in the behavior tree node may cause the behavior tree to freeze due to repeated waiting at each Tick. Therefore, it is recommended to use the Wait @ms node instead of the “wait” behavior in the behavior tree script.

### Condition

Nodes of the Condition type represent conditional judgments that need to be performed by the behavior tree. All Condition nodes are created and defined by the creator. Condition nodes are often used to determine whether a specific condition is true.
The execution result of the Condition node has only two possibilities: true and false.

### Composite

There are only four nodes of the Composite type, and they are all official nodes. This type of node is mainly used to control the execution order of child nodes.

- Priority: implements child nodes or relationships, traverses child nodes in the defined order until one of the child nodes returns true, and then stops and returns true. If all child nodes return false, false is returned. Does not support storing the result of a single execution to the next execution.
- Sequence: implements child nodes and relationships, traverses child nodes in the defined order until one node returns false, stops, and returns false. If all child nodes return true, it returns true. Does not support storing the result of a single execution to the next execution.
- MemPriority: same as Priority, but supports storing the result of a single execution to the next execution.
- MemSequence: same as Sequence, but supports storing the result of a single execution to the next execution.

> Note: The Composite control subnode execution order function is only valid for all “subnodes” connected to the Composite node.
> Customization of the Composite node is not supported.

### Decorator

Decorator nodes are mainly used to control the execution logic of the behavior tree. There are currently only five official Decorator nodes.

- Repeat @X: This node contains a variable “MaxLoop”. Its main function is to make the directly connected child node repeat the execution of “MaxLoop” times and return the result of the last execution.
- Repeat Until Failure: This node makes the directly connected child node execute repeatedly until the returned result is “Failure”, that is, “false”.
- Repeat Until Success: This node makes the directly connected child node execute repeatedly until the returned result is “Success”, that is, “true”.
- Max @Ms: This node contains a variable “MaxTime”. When executing the directly connected child node, the node will determine whether a timeout has occurred, and if so, return “false”.
- Inverter: This node will take the opposite value of the execution result of the child node directly connected to it. For example, it will invert “false” to “true”.

> Customization of the Decorator node is not supported.

## Basic rules for Behavior Tree node scripts

Each editable node in the behavior tree supports the addition of a maximum of one script.
Editable nodes are of the Action or Condition type, and depending on the type, the node script must return a specified return value.

The script of a Condition node must return a Bool value.
The script of an Action node must return a value of the type “Behavior tree node running state”, i.e. “completed” or “in progress”.

> If the script returns multiple return values to the behavior tree, the behavior tree will use the first return value as the result of the node.
> The return values of the basic nodes provided by the manufacturer are predefined.
> The logic nodes will make logical judgments based on the return values of the leaf nodes.

A node needs to have a special function, which must specify the types of input and output parameters, so that the behavior tree can call it.
The requirements for special functions are explained below.

![image-20240624151408391](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/25-BehaviorTree/image-20240624151408391.png)

It is recommended to use the “when the node enters” event to initialize the work and write the node logic into a special function.
This way, when the node returns the “in progress” result, the special function can be executed directly every tick without having to repeatedly initialize.

![image-20240624145846031](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/25-BehaviorTree/image-20240624145846031.png)

### How to return the result of running in a node

The behavior tree determines the return value by reading the value of a special function. There can be only one function of this type in the script of the same node.

The function is written differently in the Condition script and the Action script.

The writing under the Condition node is as follows:

![image-20240620163207149](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/25-BehaviorTree/image-20240620163207149.png)

Its input parameters are: mountable behavior tree entity (Owner, the entity to which we have mounted the corresponding behavior tree file).

The return value is: Bool (the result of running this node).

The Action node is written as follows:

![image-20240620163354803](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/25-BehaviorTree/image-20240620163354803.png)

Its input parameters are: the entity that can be mounted as a behavior tree (Owner, that is, the entity to which we have mounted the corresponding behavior tree file).

The return value is the running status of the behavior tree node (the result of running the node).

> The behavior tree will automatically read this type of function from the node script (make sure there is only one function of the same format), and call this function every Tick to get a return value. There is no need to call this special type of function separately.
> Each time a behavior tree node runs, the triggering order of each event is as follows: node entry, calling the special function, and node exit.
> There can only be one of these special functions in each script. Do not design a function with the same type of return value as its input value. You can program other block logic that you want to execute in this function, as long as you ensure that the function can eventually return a return value of the corresponding type.
> There can be an unlimited number of functions in the script that are not in a special format, and this will not affect the normal operation of the behavior tree or logical judgments.
> In this special function, calling an asynchronous function is not supported for the time being, and the result must be returned immediately when the tick occurs.

## Example

Create and apply a behavior tree using a simple requirement as an example.

> The actual writing of the script will not be included in this example

Let's assume a requirement:
In the Scene there is: a zombie and two coconut trees. Using a Behavior Tree, the zombie is to be made to patrol constantly between the coconut trees, to chase after the player if it is nearby, and to continue back to patrol if it loses the player as a target.
![image-20240621165320034](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/25-BehaviorTree/image-20240621165320034.png)

First, create a behavior tree file and edit it:

![image-20240621171320047](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/25-BehaviorTree/image-20240621171320047.png)

Analyze the requirements. The possible actions of the zombie are:

1. Patrol
2. Chase the player
3. Return to the patrol path

The conditions for the zombie to change its actions are:

1. It has found the player
2. It has lost the player
3. It has found that it is not on the patrol path
4. It has found that it is on the patrol path

where 1 and 2 and 3 and 4 are the positive and negative sides of the same condition. Therefore, only two Condition nodes need to be created.
Create all custom nodes:

Action nodes:

1. Patrol
2. Chase player
3. Return to patrol path

Condition nodes:

1. Did the player get spotted?
2. Am I on the patrol route?

![image-20240621165631677](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/25-BehaviorTree/image-20240621165631677-1718960193582-1.png)

Analysis of the conditions of the Action node:

| Action node           | Execution condition 1          | Execution condition 2 |
| --------------------- | ------------------------------ | --------------------- |
| Patrol                | Zombie has not detected player | On patrol path        |
| Chase player          | Zombie has detected player     |                       |
| Return to patrol path | Zombie has not detected player | Not on patrol path    |

The behavior that will require the fewest conditions: Chase player is taken out and used with its condition node to form a group with the Sequence node:

![image-20240621170020302](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/25-BehaviorTree/image-20240621170020302-1718960421910-3.png)

> Sequence node: the child nodes are executed sequentially until the child node returns false and stops, and returns false; if all child nodes return true, it returns true.

In this group, the pursuit behavior must be executed after the node that determines whether the player is found returns true.

If the zombie does not find the player, then the actual behavior of the zombie depends on the result of another condition: whether it is on the patrol path. Therefore, we need a logical node to connect the previous group with the new condition.
And because we are dealing with the logic of the zombie not finding the player at this time, the return value of the Sequence node in the previous group must be false, so our new logical node needs a node that can continue to run even if it receives false.

It is the Priority node:

![image-20240621170637325](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/25-BehaviorTree/image-20240621170637325.png)

> Priority node: child nodes are executed sequentially until they return true, at which point execution stops and true is returned. If all child nodes return false, false is returned.

This group determines whether the zombie is on the patrol route, assuming that the zombie has not found the player. According to the characteristics of the Priority node, we can directly connect the behavior of the zombie when the “on the patrol route” node returns false: return to the patrol route

![image-20240621170945343](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/25-BehaviorTree/image-20240621170945343.png)

So, when the “is on the patrol route” node returns true, the Priority node will terminate its operation because it receives true, and return a true value. We need a logic node that continues to execute the zombie's last behavior: patrolling, when its child node returns true.

![image-20240621171216518](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/25-BehaviorTree/image-20240621171216518.png)

This completes the creation of the behavior tree.

Next, we need to attach the behavior tree to the zombie entity:

Select the zombie and add the “Attachable Behavior Tree Entity” component

![image-20241024153049973](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/25-BehaviorTree/image-20241024153049973.png)

and add the behavior tree you just edited to it:

![image-20241024153150763](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/25-BehaviorTree/image-20241024153150763.png)

You're done

> The example is only a demonstration of one method of creation and is for reference only.
> There are different ways to draw the behavior tree canvas with the same logic, which can be handled according to your own preferences.
> You can continue editing the behavior tree after adding it to the entity, and it does not have to be edited in the same way as in the example.

## Additional

### prerequisites

When behavior X must be executed after condition A is met, we call condition A the prerequisite for behavior X. You can use the Sequence node to build logical units.
Prerequisites are used to meet logical requirements similar to if-then, for example, you must open the door to enter the house:

![image-20240624161142760](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/25-BehaviorTree/image-20240624161142760.png)

### Postcondition

Condition B must be true after the execution of behavior X. At this time, we call condition B the postcondition of behavior X. You can use the Priority node to construct logic units.
A postcondition is used to ensure that the condition is met when the logical block is executed successfully as a whole. For example, if the Animation of entering the house is successfully executed, the unit must be in the house:

![image-20240624162430364](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/25-BehaviorTree/image-20240624162430364.png)


### PPA mode (Postcondition-Precondition-Action)

Combining the two conditions above, we can use a widely used design method, PPA mode.

![image-20240624162916061](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/25-BehaviorTree/image-20240624162916061.png)

The advantage of this mode is that the entire behavior tree can be viewed as logic that is conditional on the postconditions, which better supports hierarchical designs, such as doors that may have a locked state:

![image-20240624164111760](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/25-BehaviorTree/image-20240624164111760.png)

The new logic mainly affects whether the door is open or not. You can edit the extended logic by making the opening of the door a postcondition.
