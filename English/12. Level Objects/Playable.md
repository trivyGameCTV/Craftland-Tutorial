# Playable

A Playable system is a collection of concepts that can be played, including playback sound effects, playback special effects, and playback motion.

With the help of playback systems, a number of customized representations can be accomplished.

# Sound Effects and Special Effects 

Sound Effects and Special Effects entities can be created by unit entities.

![image-20240808164558855](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/18-Playable/image-20240808164558855.png)

and configurations can be modified via the Properties panel.

![image-20240808164850048](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/18-Playable/image-20240808164850048.png)

> Sound Entity Configuration 

![image-20240808164918183](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/18-Playable/image-20240808164918183.png)

> Visual Effects Entity Configuration 

Entities created in this way are static.

Scripts can be used when dynamic modification of sound/effects is required. Sound and FX entities are usually created and controlled via block scripts.

![image-20240808165048985](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/18-Playable/image-20240808165048985.png)

When creating via server script, you need to specify the player, and the created effects/sound effects can only be seen/heard by that player.

When created via client script, it is only created on the client running the logic.

The position of the created entity is (0, 0, 0)by default, you can adjust the position and other modifiable properties by setting properties.

![image-20240808171126793](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/18-Playable/image-20240808171126793.png)

> Some properties of the sound effect 

When you wish to end the effect/sound effect, you can choose to delete the corresponding entity.

![image-20240808171719976](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/18-Playable/image-20240808171719976.png)

Related to sound and special effects will be explained in the final example section along with motion.

# Motion 

Motion is the process of an entity's certain motion property constantly changing. Besides the common position, rotation, scaling, etc. are also properties that can be controlled by the motion playback system.

![image-20240808173854867](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/18-Playable/image-20240808173854867.png)

![image-20240808173909821](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/18-Playable/image-20240808173909821.png)

> Properties that can perform motion 

The motion entity must be created by a block script and mounted on some entity. This entity will move with prescribed rules to realize motion modes such as acceleration and rotation.

There are six playback modes for motion: 

![image-20241021152809580](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/18-Playable/image-20241021152809580.png)

1. **Tween** 
​	The rate of solid motion varies in a prescribed curve that requires a prescribed start and end point.

2. **Trajectory** 
​	Straight-line accelerated motion.

3. **Self-relative** 
​	Similar to interpolated motion, but always using the last change in self as the starting point.

4. **Frame Self-relative** 
​	Similar to motion relative to self, but the change frequency is per frame.

5. **Follow** 
​	Follows the target entity in position.

6. **Look At** 
​	Always faces the target entity in orientation.

## Motion Block Script

### Creating motion entities 

Each motion playback mode has a corresponding creation block with a different configuration.

The following parameters are presented in left-to-right top-to-bottom order 

#### **Tween** 

![image-20241021150932344](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/18-Playable/image-20241021150932344.png)

1. **Tween**: the Tween motion entity created.

2. **Target**: target entity.

3. **Property**: which property of the mounted entity to make it move, need to fill in the entity first before you can read the property it can move. Generally, it is position, rotation, scaling, etc. 

4. **Source value**: the value of the property of the mounted entity as the starting point of the motion.

5. **Target value**:  the value of the property of the mounted entity as the ending point of the motion.

6. **Style**: the mode of playback, you can choose Single, Loop and Reciprocal. Loop means that after each motion, the entity will perform another motion from the start value. Reciprocating means that after the movement from the start point to the end point is completed, the entity will move from the end point to the start point once more, and then repeat the process.

7. **Curve**: the rate curve of property change. The rate curve is a linear Bézier curve that consists of a fixed start point, end point, and two control points.

![image-20240808180830309](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/18-Playable/image-20240808180830309.png)

​	Several templates are provided, or you can customize the coordinates of the control points.

​	You can think of the horizontal coordinates of the curve in the graph as the time, the vertical coordinates as the property values, the starting point as the 	starting value when the time is 0, the end point as the target value when the time is the end of the movement, and the rate of change as the tangent to the 	curve.

​	The rate is constant if the curve is a straight line, i.e., if the coordinates of the control points are all (0, 0).

​	In the case shown in the figure the property change will slow down, then speed up, then slow down again.

8. **Duration**: the duration of a change in milliseconds.

9. **Auto play**: whether the playback starts automatically after creation.

#### **Trajectory** 

![image-20241021152054643](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/18-Playable/image-20241021152054643.png)

1. **Trajectory**: the trajectory motion entity created.
2. **Target**: target entity.
3. **Initial Velocity**: the initial velocity, a 3D vector indicating the direction and magnitude of the velocity.
4. **Acceleration**: acceleration, a 3D vector indicating the direction and magnitude of the acceleration.
5. **Maximum Displacement**: the distance of the ballistic motion, the motion is completed after reaching the distance.
6. **Auto play**: whether the playback starts automatically after creation.

#### Self-relative

![image-20241021153418092](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/18-Playable/image-20241021153418092.png)

1. **Self-Relative**: the Self-Relative motion entity created.
2. **Target**: target entity.
3. **Property**: which property of the mounted entity to make it move.
4. **Delta**: the amount of change per movement, required to be the same data type as the property selected in **3. property**. For example, when selecting position, Delta should be filled with a 3D vector, indicating the change value of the position compared to itself.
5. **Curve**: Refer to the curve description of the interpolation motion, indicating the rate of change throughout the change process.
6. **Style**: the mode of playback, you can choose Single, Loop and Reciprocal. Loop means that after each motion.
7. **Duration**: the duration of a change in milliseconds.
8. **Auto play**: whether the playback starts automatically after creation.

#### **Frame Self-relative** 

![image-20241021154711290](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/18-Playable/image-20241021154711290.png)

1. **Frame Self Relative**: the Frame Self Relative motion entity created.
2. **Target**: target entity.
3. **Property**: which property of this entity to make this entity move.
4. **Delta**: the amount of change per frame of the motion, it is required to be the same data type as the property selected by **3. property**. For example, when selecting a position, the Delta should be filled with a three-dimensional vector that represents the change value of the position from itself.
5. **Type**: the configuration of combining with other motion modes, when it is true, it can be used in combination with relative motion, when it is false, it can be used in combination with absolute motion. Please refer to the following section for the combination rules.
6. **Auto Play**: if or not the playback will start automatically after creation.

#### **Follow** 

![image-20241021155156432](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/18-Playable/image-20241021155156432.png)

1. **Follow**: the Follow motion entity created.
2. **Target**: target entity.
3. **Follow Target**: the target to follow.
4. **Offset**: fill in the offset coordinate, the position of the motion entity will keep the direction and size of the offset coordinate with the follow target.
5. **Coordinate system**: you can choose world coordinates or relative coordinates. This determines which coordinate system the **4. offset coordinates** are offset in.
6. **Auto Play**: if or not the playback will start automatically after creation.

#### **Look  At ** 

![image-20241021155525570](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/18-Playable/image-20241021155525570.png)

1. **LookAt**: the Look At motion entity created.
2. **Target**: target entity.
3. **Look At Target**: the target of the LookAt.
4. **Offset**: fill in the offset coordinates, the center of focus will be offset from the center of the target by the corresponding direction and size.
5. **Coordinate system**: you can choose world coordinates or relative coordinates. This determines which coordinate system the **4. offset coordinates** are offset in.
6. **Auto Play**: whether the playback will start automatically after creation.

## Controls motion entity playback 

![image-20240808184649578](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/18-Playable/image-20240808184649578.png)

can be play or pause motion entities using the API.

Whether or not to replay in playback means whether or not to make the motion of the entity restart from the starting value.

Pausing motion does not delete the motion entity.

Deleting a motion entity requires the use of the Delete Entity interface, though it is important to note whether the parameter filled in is a motion entity or a mounted entity; the former deletes the created motion, and the latter deletes the mounted entity itself.

![image-20240808184808547](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/18-Playable/image-20240808184808547.png)

## Campaign entity events 

![image-20240808185009195](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/18-Playable/image-20240808185009195.png)

Motion Start, Motion End, Motion Pause, Motion Resume will trigger the corresponding events respectively. However, these events depend on the motion entity, so you should create the motion entity and then mount the corresponding script on the motion entity.

![image-20241021165059666](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/18-Playable/image-20241021165059666.png)

## Motion Entity Combinations 

Motion Entities can be used in combinations, and in general there is no limit to these combinations, entities that are mounted with multiple Motion Entities will perform multiple motions at the same time, but when using **Frame Self-relative**, you need to pay attention to the type of motion that is used in combination with it.

There is an IsSwitch option when creating a **Frame Self-relative**, which can be used in combination with relative motions when true, or with absolute motions when false.

The **Self-relative, Frame Self-relative, Follow,** and **Loot At** are relative motions, and the **Tween**, and **Trajectory** modes are absolute motions.

Using the wrong combination of modes can result in motion that is not as expected.

# Example 

An example is shown below to illustrate how motion entities, effects and sound effects are used.

We will create four orbs that always rotate around the player and add effects, play sound effects, and shoot out towards the player when the player fires, and refresh the shot out orbs after 3 seconds.

![image-20240808185916124](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/18-Playable/image-20240808185916124.png)

![image-20240808190019007](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/18-Playable/image-20240808190019007.png)

## Preparation 

First create a Prefab which is composed of a parent object and four orbs, which facilitates the rotation configuration.

The orbs use the white orb of the base object, the scaling is set to 0.3, the positions are relative to the parent object (±0.6, 1, ±0.6), and collision is turned off.

![image-20240808190203386](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/18-Playable/image-20240808190203386.png)

again Create a bullet entity, configured to match the ball of the rotating entity, for special handling of the logic that fires it out.

![image-20240808192338970](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/18-Playable/image-20240808192338970.png)

The sound effects and special effects are chosen to use the default configurations of the officially provided resources and are not prepared in advance.

Create a global script that will create the parent object and store it using script variables.

![image-20240808190601288](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/18-Playable/image-20240808190601288.png)

Create the Player script that takes the parent object created out of the global script and fetches it using an external link, and registers the four child objects in a list for subsequent handling of the bullet firing logic.

![image-20241021181341680](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/18-Playable/image-20241021181341680.png)

## Create rotational motion 

The parent object needs to follow the player at all times and rotate itself, which is a combination of two motions.

We choose **Frame Self-relative** and **Follow** in the global script 

> The first motion can also be satisfied using interpolated motion or motion relative to itself.

![image-20241021181409659](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/18-Playable/image-20241021181409659.png)

The motion property of the **Frame self-relative motion** is set to RotationAngle, and Delta is set to (0, 10, 0), which means that the object will rotate 10 degrees per frame and 330 degrees per second, slightly less than a full rotation.

Type is set to true because it is combined with another relative motion.

Follow Target is set to the player who triggered the event, which means that every player who joins the game gets these four magic balls. Because the parent object is used and the child object already has an offset, the offset is not set.

## Creating a Shooting Campaign 

Shots need to be triggered by player shooting events, and we return to the player script.

Here the balls that have been fired are detected by an integer variable, and if they are greater than four then they can't be fired any further.

![image-20241021181432894](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/18-Playable/image-20241021181432894.png)

This variable adds 1 each time it fires, ranging from -1 to 2. In practice, the values obtained in the FireBall method are 0 to 3, corresponding to the 4 balls stored in the list.

And the value is decremented by 1 each time the FireBall method ends, so that the smallest numbered of the balls around you will always be fired to prevent crossing the line.

In the FireBall method, we use a little trick to handle complex multimovement combinatorial logic: each time it should fire, hide only the entity that is going to be fired out, and create a bullet entity at the location of that entity, mount a ballistic motion to it, and fire the created bullet out. And after some time in motion, destroy that bullet and show the hidden entity back again.

![image-20241021181513472](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/18-Playable/image-20241021181513472.png)

And then give the The bullet is fired, we use a sphere effect and set the effect to be a sub-object of the bullet, modify the position and size of the effect.

![image-20241021181616342](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/18-Playable/image-20241021181616342.png)

Because the the FX entity is a child of the bullet, it will be destroyed with the destruction of the bullet, so there is no need to specially handle the logic of destroying the FX.

But the sound effect we choose to create separately and give a destruction logic.

> Just for educational purposes, sound effects can be handled in the same way as effects.

![image-20240808193149552](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/18-Playable/image-20240808193149552.png)

In the The sound effect method is called once when the player fires.

![image-20241021181648007](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/18-Playable/image-20241021181648007.png)

here There's a function ordering issue to be aware of; both methods use an asynchronous block: wait. Then both functions are asynchronous, but the requirement is that the sound playback is parallel to the firing of the bullets, and the bullets must be fired immediately after the firing of the next moment, and the logic for each bullet is independent. So the sound method selects the execution method to execute and precedes the bullet method, which is set to wait, i.e., the bullet is destroyed before the counter is incremented by 1 so that it can be fired again.

## Run detection 

![image-20240808193558646](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/18-Playable/image-20240808193558646.png)

![image-20240808193615905](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/18-Playable/image-20240808193615905.png)

![image-20240808193624924](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/18-Playable/image-20240808193624924.png)

conforms to the Expected.

> This example is only used to show the content of the playback system, there are other ways to realize similar needs in practice.
