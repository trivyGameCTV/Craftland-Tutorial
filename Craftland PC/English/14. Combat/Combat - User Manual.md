# Combat

The combat system is a crucial system in the game.

By default, players, AI zombies, and defensive towers are combat entities that naturally have combat properties such as health and damage capabilities.

Custom combat objectives rely on entities that can be targeted and are closely related to concepts such as assisted targeting and whether they can be attacked.

By using the combat system flexibly, you can create a custom combat system that even goes beyond the limitations of shooting games. However, shooting combat using FF's native firearms is more comprehensively supported, and if you want to create a combat system that does not use firearms (such as a sword and magic combat), it may require more effort and resources. So this article mainly introduces the combat system under the premise of using the officially provided firearms combat, but you may get more inspiration.

In this article, the following content will be introduced in turn:

1. Combat entities
2. Custom combat entities
3. How to create combat entities.
4. How to create a combat example.
5. Extension: self-made targets and guns that fire AOE ammunition.

# Combat entities

Combat entities are entities that will participate in combat by default. Currently, only players, AI zombies, and defensive towers are combat entities.

Combat-related events and interfaces can be used, but the combat entity component does not support custom additions.

Combat entities all have the ability to cause damage and have a health property. If their health is zero, they will die/be destroyed.

## Scripts

Combat entities can use some events and interfaces that depend on themselves.

By using these scripting contents flexibly, you can customize and extend the FF combat content to a certain extent.

![image-20240813164330675](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240813164330675.png)

![image-20240813164343647](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240813164343647.png)

Players, AI zombies, and defensive towers can also each use events and interfaces that rely on other entity components that they have.

![image-20240813163037984](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240813163037984.png)

> Adds a temporary shield before each damage, and the amount of damage is the value before damage amplification and reduction, so it cannot completely prevent headshot damage.

![image-20240814151439653](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240814151439653.png)

> After being hit, the player's health is restored by 10 points

## Guns and props

Weapons and props are indispensable in combat, and the vast majority of the damage dealt by players relies on them.

Only players can directly use weapons and props in combat.

### Weapons and props distribution

Weapons and props can be distributed to players through the scripted add-item interface. Each player can carry two primary weapons, one secondary weapon, one melee weapon, and several items by default.

Items exceeding the carrying limit will fall to the player's location by default when distributed.

![image-20240813164451166](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240813164451166.png)

![image-20240813164801221](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240813164801221.png)

> If the player already has a weapon in their hand, adding a weapon to the corresponding location will replace the currently used weapon.
> If the player's discard item property is turned off, the extra weapons or props will disappear.

![image-20240816113624270](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240816113624270.png)

> It should be noted that the interface for adding props returns a list of added props.

In addition, you can use level objects to place weapons and props or their generators directly on the field. You can also sell weapons or props to players through the store. Which method is used to issue props to players depends on the needs of the game design.

### Property configuration

For firearms and props placed in the scene through generators and level objects, you can configure the properties directly in the panel.

![image-20240813164821996](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240813164821996.png)

> Gun units and their configuration

The need to adjust the properties of guns and props after the game has started can be achieved by setting properties in the script.

![image-20240813154120654](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240813154120654.png)

> Modifying the properties of the player's main weapon

When attempting to modify the properties of a firearm via script, care must be taken to obtain the correct target for the firearm.

For example, after adding a firearm to the player using the add item interface, care must be taken that a list of entities is returned, and certain processing is required to obtain the specific firearm entity.

![image-20240816113802474](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240816113802474.png)

> Adjust the base damage of the M4A1 to 10 for the one with the number 0 among the three added at once.

The weapon itself also supports some script events:

![image-20240813163401140](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240813163401140.png)

To use these events, the script needs to be attached to the weapon entity. A practical example is given in the following example of an explosive bomb.

## Player

For the player in combat, the player module provides the following configuration:

![image-20240813154955756](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240813154955756.png)

This determines the ratio of damage dealt and received by the player.

In addition to the combat configuration, the player's basic property configuration also has an impact on combat, such as health, energy, movement speed, and whether or not they can be resurrected.

![image-20240813155108014](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240813155108014.png)

Similarly, the properties of the player can also be modified by setting properties while the game is running.

![image-20240813155205326](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240813155205326.png)

You can also use combat-specific events to receive trigger signals from players participating in combat or to perform damage operations on players.

> Setting properties in this way modifies the player's health, and unlike dealing damage, cannot trigger damage-related events, and ignores invincibility, damage reduction and other statuses.

For other descriptions of players, please refer to the corresponding documentation.

[Player - User Manual](/en/tutorial/13)

## AI Zombie

The AI zombie is a monster that has a set of properties specific to AI entities.

![image-20240813160108842](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240813160108842.png)

AI zombies will actively attack players with different lineups, but will not attack other zombies or defensive towers.

## Defense towers

Defense towers are similar to AI zombies in that they also have their own unique property configuration.

![image-20240813161549497](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240813161549497.png)

The defensive tower will only attack players with different lineups, and will not attack another defensive tower or zombies.

# Custom combat entities

In addition to the default combat entities, you may need to add some shootable targets to the map, such as a target.

![image-20240812171755227](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812171755227.png)

> How to create a target with functions will be introduced later.

To create a custom combat entity, you must add the **Targetable Entity** component to it, and you can also add the **Assistible Target** component to it to add the function of being able to be assisted in targeting.

## Targetable Entity

Without considering the complete customization of a combat system from scratch, using officially provided firearms to fight, units that can be hit in battle need to be equipped with the **Targetable Entity** component.

![image-20240812162828766](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812162828766.png)

Units equipped with the **Targetable Entity** component can trigger related events to complete the combat logic.

![image-20240812162928108](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812162928108.png)

> Players, zombies, and defensive towers are combat entities that naturally come with this component.

The implementation of the event for targeting entities is actually dependent on collision. Please make sure that the collision component is added and enabled.

![image-20240812165344576](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812165344576.png)

## Aiming assist entities

For players, an aiming assist function is provided in the game. When firing, the crosshair will automatically be attracted to the targetable entity.

The aiming assist entity component depends on the **targetable entity** component.

![image-20240812170825084](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812170825084.png)

However, for the assistible targeting entity component to take effect, the target entity must be an entity that the player can attack. For AI zombies, other players, and defensive towers, as long as the **faction** is different, they are entities that the current player can attack. For other entities that can be targeted, the targeting relationship needs to be manually set in the script.

![image-20240812170416462](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812170416462.png)



## Example

Using a basic sphere as an example, after creating this object, you need to add the targetable entity component to it and ensure that collisions take effect.

![image-20240812171913379](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812171913379.png)

![image-20240812172006605](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812172006605.png)

If the object is needed to trigger the player's secondary targeting function, you need to add an additional entity that can assist in targeting, and handle its attack relationship with the player in the script.

![image-20240812172201279](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812172201279.png)

![image-20240812172304190](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812172304190.png)

![image-20240813111631911](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240813111631911.png)

# Example battle

The following is a simple example of how to create a battle.

1.**Create a project**

![image-20240812174733615](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812174733615.png)

2.**Set up the Scene objects**

We need a spawn point to specify the player's spawn location, some zombies, and some custom combat objects. Here, cones, cylinders, and cubes are used as custom combat objects.

![image-20240812175451608](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812175451608.png)

Add the AimableEntity component to the custom combat object.

![image-20240812175112073](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812175112073.png)

Use the weapon and prop units to place a gun and ammunition in front of the player's spawn point.

![image-20240812175247402](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812175247402.png)

Adjust the properties of the gun so that it can only deal 1 damage per shot.

![image-20240812175327766](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812175327766.png)

Adjust the properties of the zombie so that it is neutral in faction, has a long tracking range, and has a high health value of 200.

![image-20240812175556046](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812175556046.png)

> Neutral zombies will actively attack players in range

At this point, you should have noticed that players cannot eliminate zombies with firearms. We will now add some features to the custom combat entities:

Cone: When targeted by a player, it will destroy itself after adjusting the current main weapon damage of the player to 500.

Cube: When attacked by a bullet, it will make all players invincible and destroy itself.

Cylinder: When attacked, it will cause 500 barrel explosion damage to all **combatable entities** and destroy itself.

**Cone Script**:

![image-20240812181331111](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812181331111.png)

**Cube script**:

![image-20240812181458376](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812181458376.png)

**Cylinder script**:

![image-20240813104435940](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240813104435940.png)

**Add script to custom combat object**:

![image-20240814153824445](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240814153824445.png)

![image-20240814153840232](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240814153840232-1723621120933-1.png)

![image-20240814153858204](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240814153858204.png)

**Directly attack the zombies**:

![image-20240812182829477](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812182829477.png)

**Actual combat method 1**:

Gain damage boost through the aiming cone and kill all zombies.

![image-20240812182911259](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812182911259.png)

> The cone has been destroyed by aiming at it

![image-20240812182050467](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812182050467.png)

![image-20240812182106335](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812182106335.png)

> Easily kill zombies after increasing damage

**Actual combat method 2**:

Become invincible by attacking the cubes and destroy all the zombies by attacking the cylinders.

![image-20240812183012114](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812183012114.png)

> Destroy the cube to become invincible.

![image-20240812183034398](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812183034398.png)

> Destroy the cylinder to eliminate all zombies.

# Expansion example

## Basic target

Create a target in the scene.

![image-20240812171755227](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812171755227.png)

Create a parent object and drag five basic spheres below it to represent the 2, 4, 6, 8, and 10 rings.

![image-20240812183316438](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812183316438.png)

Scale the sphere to X=0.01, and Y and Z are successively 1, 0.8, 0.6, 0.4, and 0.2. This gives five circles, which are used to detect the number of rings hit by the bullet.

Adjust the X value of the position so that the rings with a large number are closer to the front.

![image-20240812183418348](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812183418348.png)

> Transform of 2-ring

![image-20240812183533443](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812183533443.png)

> Transform of 10-ring

Modify the sphere rendering so that the two adjacent rings are rendered differently.

![image-20240812183656728](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812183656728.png)

Modify the collision type of all child objects to Mesh, which makes the collision adhere closely to the object shape.

![image-20240812183826045](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812183826045.png)

Add the Aimable entity component to all child objects.

![image-20240812183903903](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812183903903.png)

This gives us a target object, and the larger the number of rings, the higher the collision detection will be. When the bullet hits, it will first detect the collision body with the largest number of rings at its current position.

![image-20240812183924000](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812183924000.png)

Place a huge background behind the target, turn off its visibility, and only keep the collision and targetable entities as the off-target detection.

![image-20240812184318718](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812184318718.png)

![image-20240812184352396](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812184352396.png)

Create a UI that displays the current player's score.

![image-20240812184551799](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812184551799.png)

Add three custom properties for players: current target score, total target score, and whether the player is active.

![image-20240812184844522](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812184844522.png)

> Whether it is used by the active player to determine which player is shooting at the target when there are multiple players, and the shooting actions of other non-active players will not be counted in the score.
>

Add scripts to all target objects and objects used to determine misses. Their script structures are similar, the only difference is that the value of the property that modifies the player's shooting points is different:

![image-20240812185042887](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812185042887.png)

> Script for the 2-ring object

![image-20240812185237825](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812185237825.png)

> Script for the off-target background

Add a script to the global module to set the player to active when they join a match and create a custom UI.

![image-20240812190821415](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812190821415.png)

> In practice, the player can be activated based on conditions.

When the target or background is hit by a bullet, an event is sent to the player.

![image-20240812185120193](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812185120193.png)

Add a script for the player that modifies the text on its own custom UI when it receives the event that the target has been hit.

![image-20240812185143837](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240812185143837.png)

Place the gun in the Scene and enter the game to test it.

![image-20240813111656143](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240813111656143.png)

> In this example, the miss caused by attacking the ground is not handled.

## Explosive bullet

Here's how to make a gun that fires bullets with AOE damage and has an explosion effect.

First, analyze the situation: the damage and hit effects should occur when the bullet actually hits the target, so use the bullet hit event.

![image-20240813105723682](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240813105723682.png)

This event depends on the weapon entity, so the script should be attached to the weapon.

Add an explosion effect when hit

![image-20240813110534368](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240813110534368.png)

> This effect is visible to each player

Adds AOE damage

![image-20240813110613308](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240813110613308.png)

> Calculate the hit point and the distance to the combatable entity, and deal damage to combatable entities within range.
>
> Here, only AI zombies and players will be damaged

This completes the weapon script, which is then attached to the corresponding weapon.

![image-20240813110733878](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240813110733878.png)

> Here is the player script. When any player equips the weapon, the weapon will gain AOE ability.

Add some AI zombies to the scene and test with multiple ends.

![image-20240813111117612](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/14-Combat/image-20240813111117612.png)
