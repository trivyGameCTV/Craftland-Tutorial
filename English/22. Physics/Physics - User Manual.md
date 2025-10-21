# Physics

The physics system helps you simulate real-world physical behaviors such as collisions and forces.

# Physics Module

Physics is a mod that is loaded by default.

![image-20240923155343336](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240923155343336.png)

You can modify global physics settings here:

1. **The direction and magnitude of gravity**.
2. **Default physical material**. Please refer to the Collision - Physical Material section below.
3. **Global energy threshold**. Calculate the kinetic energy of an object using the formula:

$$
Ek=1/2*m*v^2
$$

	m represents the mass of an object in kg.

	v represents the physical velocity in m/s.

	When the kinetic energy of an object is less than this threshold, it will stop moving. For example, if the threshold is set to 0.5, a 1kg object will stop moving when the speed is less than 1m/s.

4. **Character Controller Collision Threshold**. Only applicable to player mods that have [Use Player Controller with Physics] turned on or completely custom character controllers.

The momentum formula is:
$$
p=mv
$$
m is mass, unit is kg.

v is the velocity in m/s.

When a collision occurs, the momentum of the player and the hit rigid body is subtracted, and the modulus of the momentum difference on the collision normal is taken and compared with the character controller collision threshold. If it is less than this threshold, the rigid body will be pushed steadily, otherwise a violent collision will occur.

Roughly speaking, the parameters that affect whether a collision is violent are:

1. The greater the mass of the player or character, the more likely it is to have a violent collision.

2. The faster the relative speed between the player or character and the hit rigid body, the more likely it is to have a violent collision.

3. The larger the collision threshold of the character controller is set, the less likely it is to collide violently.

For example, when the character controller collision threshold is set to 50, a 50kg player traveling at 1m/s can collide violently with any stationary rigid body of similar mass to the player or character in a head-on collision.

5. **Physical level**. Whether collisions occur at different levels depends on the physical configuration.

To configure a non-default physics layer for a player:

![image-20240717181446557](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240717181446557.png)

Disable the collision of Custom and Default levels in the Physics Configuration:

![image-20240717181534541](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240717181534541.png)


	You will find that the player can pass through any object of the default physics level without feeling:

![image-20240923163608324](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240923163608324.png)

	Objects that rely on collision triggering will not trigger either:

![image-20240923163636790](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240923163636790.png)

Collision Shapes and Collisions

There are two basic components required to apply custom objects to the physics system:

**Collision Shape Component** and **Collision Component**.

![image-20240923150401236](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240923150401236.png)

> For most objects you will only find one collision component on them.
>

Because they are generally not custom objects:

![image-20240923150521786](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240923150521786.png)

For custom collision shapes and physical materials, we recommend that you create a new empty node and operate on it:

![image-20240923150725335](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240923150725335.png)

![image-20240923150807166](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240923150807166.png)

## Collision Shape

The collision shape component determines the boundaries within which objects collide.

Collision Type:

![image-20240923153336796](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240923153336796.png)

The collision type determines the basic shape of the collision. We provide three basic shapes: cube, sphere, capsule, and mesh collision.

Mesh colliders are collision shapes that are simulated based on the boundaries of a model and are close to the visual appearance of the model.

For the created empty node, you need to add a custom rendering component to specify its grid shape and size.

![image-20240923153752769](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240923153752769.png)

For basic collision shapes, you can modify their position, size or adjust their shape manually:

![image-20240923153907205](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240923153907205.png)

> Drag the yellow dot on the collision box to adjust the collision shape

Mesh collision shape has an option to be convex or not

![image-20240923154035083](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240923154035083.png)

Convex Polygons: Whether to collide with other Mesh Colliders. Mesh Colliders without Convex Polygons enabled are only supported on GameObjects without a Rigidbody component. To use a Mesh Collider with a Rigidbody component, check the Convex Polygons option.

## Collision

### Physical Materials

The physical material determines some physical properties of the collision body.

For custom objects, the physical material of the collision can be customized. However, for most officially provided non-custom objects, the physical material does not support modification.

![image-20240923154559903](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240923154559903.png)

Physical material files can be created.

![image-20240923154405512](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240923154405512.png)

You can modify the following properties in the inspector panel of the physical material file so that all objects mounted with the physical material will obtain the corresponding physical properties.

![image-20240923154620475](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240923154620475.png)

### Is it a trigger?

When the Is It a Trigger checkbox is checked, the collider ignores physical collisions but can trigger events.

This means that the object will not participate in the default physics collision logic:

![image-20240923154941118](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240923154941118.png)

But a collision event can be triggered:

![image-20240923155036397](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240923155036397.png)

![image-20240923155220723](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240923155220723.png)

### Physical Level

Determines the level of physics. Whether collisions at different levels occur depends on the configuration in the physics module.

# Rigidbody

The Rigidbody component makes the object physically controlled, allowing it to be affected by forces.

To add a Rigidbody component, you must first have a Collision component.

Rigid bodies are divided into static, dynamic and kinematic.

![image-20240924112556743](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240924112556743.png)

**Static rigid bodies** are mostly used for objects that have no speed and are not subject to force, such as the ground, walls and other objects that do not move. Modifying the position and scale of these objects will increase performance overhead.

**Dynamic rigid body** is mostly used for objects with mechanical properties such as mass and velocity, which can be affected by force.

![image-20250630165950663](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20250630165950663.png)

You can modify the physics-related parameters such as center of gravity and mass under the Dynamic Rigid Body option. You can also choose to lock a specific axis so that the rigid body will not undergo a specific displacement or rotation.

**Kinematic rigid bodies** can be manually controlled to move and rotate, but are not affected by collisions or forces from other rigid bodies. They are often used in animation and special effects production.

# Character Controller

##FF Player Controller

By default, the player's actions on the player character are inherited from the FreeFire player controller.

## Player controller with physics

In the player module, after checking [Whether to use player controller with physics effects], you can modify the physical parameters of some player controllers. In this case, the player begins to participate in the physical simulation in the game to a certain extent, such as the [Character Controller Collision Threshold] configuration in the physics module will begin to take effect.

![image-20240924115708102](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240924115708102.png)

	**Whether to use player controller with physical effects: **Check to use a controller with custom physical effects and expand related configurations.
	
	**Total height, including upper and lower hemispheres:** The height of the character's capsule collision body.
	
	**The radius of the upper and lower hemispheres: **The radius of the capsule cannot exceed 1/2 of the height.
	
	**Quality:** Player quality.
	
	**Maximum uphill angle:** Slopes exceeding this angle cannot be climbed and the player will start to slide down.
	
	**Step Vertical Offset:** The distance the player can deviate from the configuration without leaving the ground or becoming blocked, commonly used when moving up and down stairs.
	
	**Minimum moving distance:** If the distance the character controller has to move is less than this value, the player will remain motionless.
	
	Skin Thickness: The depth other objects are allowed to embed into the character's collider, used to avoid jitter or sticking.
	
	**Gravity acceleration you receive:** The gravitational acceleration you receive in three dimensions. For player characters, this setting overrides the global physics settings.
	
	**Enable custom push:** When turned on, the force applied by the character when pushing the rigid body can be customized. Expand the relevant configuration after turning it on.
	
	**Custom Push Strength:** The amount of force applied when the character pushes the rigid body.
	
	**Multi-jump height:**The height of the jump when performing a multi-jump.
	
	**Maximum number of multi-hops: **The maximum number of jumps supported by each multi-hop.
	
	**Air Movement:** When enabled, players can change their movement speed and direction in the air.

## Fully customizable character controller

In the fully custom character controller, you can completely customize the character controller without any restrictions, but this controller does not have any default functions.

To use a completely custom character controller, you need to use the character controller component, and the object used as the controlled character cannot have collision, collision shape, rigid body and other components.

![image-20240924120030311](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240924120030311.png)

Please refer to the example below for specific usage.

# Example

We will explain how to use a custom character controller by making a simple horizontal mode character controller.

## Set up the scene

Simply build a scene.

![image-20240926150721110](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240926150721110.png)

## Creating a player character

Here we just make a simple player character.

Create an empty object:

![image-20240926150911348](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240926150911348.png)

Add a Character Controller component to this object.

![image-20240926151012964](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240926151012964.png)

Add a custom attribute to the character controller: state. We will use the state to control the left and right movement of the player character later.

![image-20240926151107697](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240926151107697.png)

Currently the character has no appearance, so add an empty child node to this empty node to display the appearance.

![image-20240926151307907](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240926151307907.png)

Add a custom render component for empty child nodes.

![image-20240926151344936](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240926151344936.png)

Select Mesh as Cylinder.

![image-20240926151443376](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240926151443376.png)

At this time, select the parent node and observe our character in the scene editor.

![image-20240926151546844](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240926151546844.png)

The capsule mesh is the character controller component of the parent object, and the cylinder is the custom render component of the child object. We found that the character controller seems to be a little taller than it looks, and has a smaller range than the model.

Adjust the relative height of the child objects and the character controller appearance so that they roughly match.

![image-20240926151803081](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240926151803081.png)

![image-20240926151903119](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240926151903119.png)

**Please pay special attention** that for the character controller, its height must be **greater** than twice the radius.

Set the created character as a prefab and rename it New_player (or any name you like). Delete the empty object used in the scene.

![image-20240926152126406](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240926152126406.png)

## Initialization

Create a global script to block the default player, create a new player, and set the movement method.

![image-20240926153801533](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240926153801533.png)

### 1. Clear the default UI

To use a custom character controller, you must first solve the built-in player controller. The player character cannot be deleted from the game, but we can use some methods to make the player character unable to be controlled or seen.

By closing the default UI interface, we can block all UIs that can directly manipulate the default player.

![image-20240926152534232](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240926152534232.png)

### 2. Use custom camera

The default camera follows the default player character, so we need to use a new custom camera to only observe the new player character we create.

![image-20240926152824590](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240926152824590.png)

### 3. Storing player data

Create a global variable to store each player's custom character controller.

![image-20240926153846600](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240926153846600.png)

![image-20240926153853898](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240926153853898.png)

![image-20240926153934182](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240926153934182.png)

### 4. Set the movement method

We control movement by judging the state of the character controller, setting 0 for no movement, 1 for left movement, and 2 for right movement.

Each time an update is made, all custom controllers execute a move method. The move method checks the state of the player controller. If it is in the moving state, it moves a small displacement in the corresponding direction.

![image-20240926154524350](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240926154524350.png)

> When the fixed frame is updated, the event is triggered at a frequency of 30 times per second, which is equivalent to the character controller moving at a speed of 30*0.1=3m/s.

## Create a custom action UI

Create a UI to control the movement of the custom character controller.

![image-20240926154930426](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240926154930426.png)

The three buttons are used to move the player left, right, and jump.

Add scripts to UI entities and use callback processing logic:

1. Jump

Jumping is achieved by applying force to the custom character controller.

![image-20240926155224218](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240926155224218.png)

> The force application interface can directly select the application speed, avoiding the calculation of force and mass.

2. Mobile

We control movement by changing state, handling the state of the player pressing and releasing the button separately.

![image-20240926155731649](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240926155731649.png)

![image-20240926155753513](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240926155753513.png)

Add callbacks on the buttons to call these methods respectively.

1. Jump

![image-20240926155857104](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240926155857104.png)

2. Mobile

![image-20240926155911048](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240926155911048.png)

![image-20240926155924485](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240926155924485.png)

## debug

![image-20240926160400721](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240926160400721.png)

The logic works normally.

# Added: Lens debugging

When using a custom lens, it is sometimes difficult to determine an appropriate lens parameter.

We can adjust the camera during the development phase by adding a UI to control the camera. Using the same idea can help you continuously optimize your character controller performance during the debugging phase.

## Create the UI

We use buttons to control the movement of the lens up, down, left, right, forward and backward, and print the current lens offset through a button.

![image-20240926160759275](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240926160759275.png)

## Writing the script

Add scripts for UI entities.

Move the lens, taking upward movement as an example:

![image-20240926160942701](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240926160942701.png)

Print lens parameters:

![image-20240926161034212](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240926161034212.png)

## Add callback

Add callbacks for each button:

Take moving up as an example:

![image-20240926161123354](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240926161123354.png)

Print lens parameters:

![image-20240926161149538](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240926161149538.png)

This way you can adjust the camera to achieve the effect you want when debugging the game:

![image-20240926161255378](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/22-Physics/image-20240926161255378.png)
