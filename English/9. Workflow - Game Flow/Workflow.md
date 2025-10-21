# Workflow

In this module, you can freely set the flow and duration of the game in phases and rounds. You can also attach scripts to the phases and rounds.

# Concept description

Our game flow is made up of phases. The game starts from a fixed start phase and ends after a set number of phases in a fixed end phase.
Each phase can be set to a duration, but it must be at least 5 seconds. After the phase ends, the flow will move on to the next phase.
The game start and game end phases must exist and serve as the starting and ending points of the game, so they cannot be deleted or their names changed.
A round is a special kind of phase that is a collection of several phases, and the number of times it can be repeated can be specified. Whenever the flow enters a round, the phases it contains will be executed repeatedly and in sequence within the round, and the round will end and continue downward after the number of times it can be repeated has been reached. A round cannot contain a round.

All phase or round entities are created at the beginning and destroyed at the end. Scripts and related entities attached to them may be affected.

> Unless otherwise stated, the term “phase” below includes the concept of a round.

# Viewing and configuring processes

The Processes module menu allows you to view and configure the current game process

![image-20240625172021283](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/09-Workflow/image-20240625172021283.png)

We have created some phases for you by default. You can customize all the phases and their order. The properties are described below:

1. ID: Each phase is assigned a unique ID, which cannot be modified. This is the ID used in the script for the phase index or round index.
2. Name: Customization is supported except for the start and end of the game. It is helpful for the script to customize the phase name in an organized manner, as detailed below.
3. Duration: The duration of the phase in seconds. The phase ends when the duration is reached. The minimum duration is 5 seconds and the maximum is 16777216 seconds. However, each game can only last up to one hour, so it is pointless to set a phase duration that is too long.
4. Script: Scripts attached to a specific phase will only take effect in that phase.
5. Phase entity: You can add scripts and properties to phases by customizing the phase entity component. The scripts and properties added to the component will be inherited when each phase entity is created.
6. Number of loops: This is only used for rounds and determines how many times the phases within the round will be repeated before exiting. The minimum value is 1 and the maximum value is 10.

# Order of phases

By default, the game starts with the creation of the game, and the order of the game end phase cannot be modified.
Game start: always at the top.
Game end: always at the bottom.

> The game preparation phase is just an ordinary phase. You can modify the name of the game preparation phase, and you can even delete it.

For other phases, you can drag and drop them to place them above the specified phase.

![image-20240625172301158](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/09-Workflow/image-20240625172301158.png) 

When your mouse turns into a prohibition symbol while dragging, it means you have not selected any nodes. At this time, releasing the mouse will not cause any changes to the sequence. Attempting to modify the sequence of the game start, game end, and game preparation nodes will also not cause any changes to the phase sequence!

![image-20240625172322732](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/09-Workflow/image-20240625172322732.png)

# Adding and deleting phases

When you select a phase other than the start or end of the game, two plus signs will appear at the top and bottom. Clicking on the plus signs will create a new phase in the corresponding location** based on the phase type above the plus sign**, regardless of the type of the selected phase.
If you use the plus sign to create a new phase within a round, the new phase will be a subphase of the round.

Example 1: If the plus sign is located below the round, a round will be created:

![image-20240625172530666](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/09-Workflow/image-20240625172530666.png)

Example 2: If the plus sign is below the phase, a phase is created

![image-20240625172707121](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/09-Workflow/image-20240625172707121.png)

You can also right-click on the phase:

![image-20240625173142623](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/09-Workflow/image-20240625173142623.png)

You can rename the phase, add a new phase, add a new round, and delete this phase.

# Script-related instructions

## Add a script

Select a node in the Modules - Workflow menu and add a script. The corresponding script will be attached to the node entity

![image-20240625192919120](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/09-Workflow/image-20240625192919120.png)

## Properties

The global variables can be used to retrieve the current phase index and current round index:

![image-20240625183026149](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/09-Workflow/image-20240625183026149.png)

Using the round or phase index, you can get the index of any round or phase configured in the current game:

![image-20240625183157505](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/09-Workflow/image-20240625183157505.png)

This block will pull all the phases and rounds in the order they are executed. It is recommended that you give each phase and round a reasonable name at the beginning.

## Events

We provide the following four events that can be used to monitor the start and end of a phase or round. Using them, you can easily write the logic you want.

On Round Start
On Round End
On Phase Start
On Phase End

Here, rounds are distinguished from phases. The events **When a phase starts** and **When a phase ends** are only triggered when a phase starts or ends, but not when a round starts or ends. The same applies to phases.
**Example 1:** When a specified round starts

![image-20240625174421473](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/09-Workflow/image-20240625174421473.png)

**Example 2**: When the specified phase starts

![image-20240625181729598](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/09-Workflow/image-20240625181729598.png)

**Example 3**: Determine whether the current phase is the specified phase

![image-20240625180216231](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/09-Workflow/image-20240625180216231.png)

> Note that the parameter brought out at the beginning and end of the round is the index of the round; the parameter brought out at the beginning and end of the phase is the entity of the phase.
> The index of the phase and round is the ID field in the Module-Workflow panel.

## API

We provide two APIs for use:

Switch game phase
End game current phase

Switching the game phase forces the game to switch to the specified phase. It is worth noting that this API also supports entering the round index to switch directly to the specified round.
Caution is required when switching directly to a phase within a round. The phases will be executed in order within the round, until the last phase in the round, and then restart the first phase of the round. Regardless of which phase within the round is switched to, the first execution will not be counted in the number of rounds. The first execution of the round will be counted as the first execution of the round when restarting the round.

Suppose we have a round that needs to be executed twice in a loop

![image-20240625185003949](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/09-Workflow/image-20240625185003949.png)

Somewhere outside the round, the script used to switch game phases switches to the round phase 2. The game will then execute in the following order:

![image-20240625185440323](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/09-Workflow/image-20240625185440323.png)

This is because the logic of the round is to add 1 to the loop counter after it starts, and check whether the loop counter is greater than or equal to the configured number of loops after the last subphase ends. Forcing a jump to a phase in the round or jumping between phases in the round may produce unexpected results.

### Switching to a phase or round:

![image-20240625192029993](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/09-Workflow/image-20240625192029993.png)

### Ending the current phase of the game:

![image-20240625192121351](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/09-Workflow/image-20240625192121351.png)

# Example

A game with five innings and three outs, with a 5-second setup time and a 10-second setup time per round, and a game time of 180 seconds.

1. Set up and name the phases in the process:

![image-20240625195238497](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/09-Workflow/image-20240625195238497.png)

![image-20240625193443258](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/09-Workflow/image-20240625193443258.png)

2. Configure the desired duration:

![image-20240625193523846](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/09-Workflow/image-20240625193523846.png)

![image-20240625193547458](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/09-Workflow/image-20240625193547458.png)

![image-20240625195326740](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/09-Workflow/image-20240625195326740.png)

![image-20240625193809696](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/09-Workflow/image-20240625193809696.png)

3. Add a script:

The logic of the script is: At the end of each round, if either team scores 3 or more points, the game ends.
We usually create a global script to determine the flow of the entire game.

![image-20240625194244070](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/09-Workflow/image-20240625194244070.png)

![image-20240625194328624](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/09-Workflow/image-20240625194328624.png)

Edit this script:

We will use the event trigger logic operation **when the round ends**, and use the **switch to phase or round** API to end the game when the conditions are met.

When the specified round ends

![image-20241016112213687](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/09-Workflow/image-20241016112213687.png)

If the score of one team is 3 or higher, end the game (jump to the end of the game phase)

![image-20240625195024491](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/09-Workflow/image-20240625195024491.png)

![image-20241016113431814](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/09-Workflow/image-20241016113431814.png)

> This example is for reference only. You are free to write your own logic.
