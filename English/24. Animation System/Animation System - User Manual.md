# Animation System - User Manual

# Overview of the Animation System

The basic concept of the animation system is the animation clip. An animation clip contains information about a specific object's changes in position, rotation, or other attributes over time. This linear record allows for animation effects like opening doors, walking, or jumping. Typically, an animation clip only includes short-duration animation information.

With an animation controller, clips can be organized for more logical and complex animation scenarios.

The animation system supports importing custom clips to create unique animations or replace default character animations.

# Supported Formats

Craftland Studio PC only supports FBX format for animation imports.

# Importing Animations

Like importing any other resource, you can drag the animation resource directly into the Assets folder or use the import function.

![image-20241009145333134](./img/image-20241009145333134.png)

![image-20241009145353148](./img/image-20241009145353148.png)

# Previewing Animations

Open the imported FBX file, where you should find the animation clip files.

![image-20241009150124874](./img/image-20241009150124874.png)

Double-click the animation, and you'll be prompted to use a model to play it.

![image-20241009150202966](./img/image-20241009150202966.png)

Drag in the prepared corresponding model to preview the animation.

![image-20241009150228158](./img/image-20241009150228158.png)

# Using Animations

Imported animations become assets in your game project. Here are two main ways to use them:

## Replacing Player Actions

In player data, you can replace default player action animations with imported ones.

![image-20241009152001198](./img/image-20241009152001198.png)

When replacing action animations, ensure they match the skeleton used in player data. In this example, using a cat's idle action requires replacing the player model with a cat model.

![image-20241009152652723](./img/image-20241009152652723.png)

In this setup, the player is replaced by a cat and only plays actions in idle state; no actions are played during other activities.

Further details on player data are available in the [Player] user manual.

## Animation State Machine

An animation state machine allows you to define a sequence of actions and play them as needed.

### Creating an Animation State Machine

![image-20241009152839716](./img/image-20241009152839716.png)

### Editing an Animation State Machine

![image-20241009154859239](./img/image-20241009154859239.png)

1. Status Bar: Set multiple states for easy switching under appropriate conditions. An animation state machine must have at least one Idle state.
2. Current State Clips: Edit clips and their playback order within a state.
3. Properties Panel: Modify state or clip configurations here.

In state properties, you can change names and set whether the entire state group loops.

![image-20241009155234382](./img/image-20241009155234382.png)

> The default Idle state's properties cannot be edited.

The loop property means that once all animations in a state finish playing, they will restart from the first one. Note that if a clip is set to loop within a state, it typically won't complete automatically and won't enter another loop.

![image-20241009155540119](./img/image-20241009155540119.png)

> Looping clips won't automatically proceed to the next clip or cause the current state to loop.

### Animation State Machine Application Example

We place a cat model in the scene and want it to run to a specified location at round start, then loop through an Idle + Eat animation combo.

![image-20241010174717222](./img/image-20241010174717222.png)

1. Add Component

   The animation state machine relies on adding an animation state machine component:

   ![image-20241009161031943](./img/image-20241009161031943.png)

2. Edit Animation State Machine

   Edit the added component's animation state machine.

   Add two states: Idle and Run.

   ![image-20241009161127033](./img/image-20241009161127033.png)

   In Idle state, add two actions: Idle and Eat.

   ![image-20241009161145386](./img/image-20241009161145386.png)

   Since Idle state's mode is set to loop, both clips are set not to loop to continuously play Idle + Eat.

   In Run state, add a running clip and set it or Run state to loop. These settings affect a script node parameter later; here we only set the clip's mode to loop.

   ![image-20241009161438144](./img/image-20241009161438144.png)

3. Edit Script

   Add a script to the cat model and write logic. Since added animations don't include actual displacement, use playable to add orientation and displacement:

   ![image-20241009161503010](./img/image-20241009161503010.png)

   > An invisible Box001 is added at displacement's endpoint on the map for consistent orientation towards it.

4. Test

   During preparation phase, Idle state auto-starts due to added animation state machine.

   ![image-20241010174749270](./img/image-20241010174749270.png)

​	Movement phase.

![image-20241010174759279](./img/image-20241010174759279.png)

​	After reaching destination.

![image-20241010174815354](./img/image-20241010174815354.png)
