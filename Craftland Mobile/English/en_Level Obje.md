# Level Objects

Introduce objects that are often used in the level, and explain some tips that may be used in the construction of some scenes.

## Infrastructure Components

Infrastructure components refer to decorative objects that do not have any functions but only use as structures. We can use these structures to build more complex combinations or use these simple structures as obstacles or bunkers in the scene.

![image-20241114113031240](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241114113031240.png)

**Example usage method:**

| Serial number | Description | Illustration |
| ---- | ------ | ------------------------------------------------------------ |
| 1 | Decoration | ![image-20241122181141757](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241122181141757.png) |
| 2 | Bunker | ![image-20241122181229931](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241122181229931.png) |
| 3 | Obstacles | ![image-20241122181214170](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241122181214170.png) |

### Item Manager

When a large number of objects are created in our scene, it may be difficult to find the location of an object. In this case, we can click **More**, find **Object Manager** and click Open, and we can open the item management interface.

![image-20241114152153431](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241114152153431.png)

In the item management interface, when we click on any object, the object's position will be highlighted and selected in the scene. After closing the item manager, you can directly edit the selected object.

![image-20241114154721963](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241114154721963.png)

When we merge a complex composition created into a structure, we will find that an empty parent empty object will be automatically created in the item manager, and all the objects selected by the merge will be stored in this empty parent object.

![image-20241114162715589](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241114162715589.png)

## Birth Point

The birth point is where the player generates at the beginning of the game. The birth point must exist in the map; otherwise, the game will not be able to proceed.

The arrows of the birth point indicate the direction the player faces when the birth point position is generated at the beginning of the game.

![image-20241114163601186](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241114163601186.png)

When we delete all birth points and run debug mode, we will be prompted that we cannot play the game.

![image-20241114163907596](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241114163907596.png)

The birth point has two unique configurations, capacity and team:

![image-20241114165449845](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241114165449845.png)

**Capacity:** Determines the number of births that the birth point can accommodate at the same time.  
**Team:** Determines the team to which the player who can be born at that point of birth belongs. If not configured as all teams, only one team can be selected.

After the team to which it belongs is configured as a specific team, the birth point will display the configured team in the scene.

![image-20241114165910983](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241114165910983.png)

## Weapon Loot Point

There are two ways to generate props at a specified location: generator and unit.

Use the generator to generate weapons or props, which can be set to refresh each turn, but only types can be specified. If the last generated prop was not taken away during refresh, it will be replaced with the newly generated prop.

Use the unit to place weapons or props, and you can accurately set the generated weapons or props. By default, only one corresponding prop will be generated.

In CraftLand, there are 6 types of weapon Loot Points, namely:

| Serial number | Name | Illustration | Type |
| ---- | ---------------- | ----------------------------------------------------------- | ------------------------------------------------------------ |
| 1 | Ammunition Loot Point | ![image-20241114175155884](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241114175155884.png) | 1.Random<br />2.AR Ammo<br />3.SMG Ammo<br />4.SN Ammo<br />5.HG Ammo<br />6.SN Ammo<br />7.Bow Ammo |
| 2 | Weapon Loot Point | ![image-20241114175147410](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241114175147410.png) | 1.Random<br />2.Rifle<br />3.SMG<br />4.Sniper Rifle<br />5.Pistol<br />6.ShotGun<br />7.Melee<br />8.CrossBow<br />9.Football Shooter |
| 3 | Consumables Loot Point | ![image-20241114175205876](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241114175205876.png) | 1.Random<br />2.Med Kit<br />3.Repair Kit<br />4.Horizaline<br />5.Inhaler<br />6.Gloo Wall |
| 4 | Grenade Loot Point | ![image-20241114175216900](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241114175216900.png) | 1.Random<br />2.Grenade<br />3.FlashBang<br />4.Smoke Grenade<br />5.Flash Freeze |
| 5 | Armor Loot Point | ![image-20241114175228498](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241114175228498.png) | 1.Random<br />2.Armor Lv1<br />3.Armor Lv2<br />4.Armor Lv3 |
| 6 | Scope Loot Point | ![image-20241114175239315](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241114175239315.png) | 1.Random<br />2.2X Scope<br />3.4X Scope<br />4.Thermal Scope |

When we select Loot Point, we can see that there are two unique configurations in Loot Point for us to choose:

**Weapon type:** In the configuration, we can choose the type of weapon we want to generate in Loot Point.  
**Whether to refresh each turn:** In the reset component of each turn, you can set whether the generated point will be refreshed at the beginning of each turn.

![image-20241115102255399](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241115102255399.png)

After the game starts, Loot Point's weapons will be refreshed at the center of the area, and the original blue light effect of Loot Point will disappear.

![image-20241115104134477](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241115104134477.png)

> It is worth noting that when a weapon Loot Point generates a weapon's full-level accessories and a certain number of bullets, so when we place a weapon Loot Point, we do not need to place the corresponding accessories for the weapon.

![SeaTalk_IMG_20241115_103433](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/SeaTalk_IMG_20241115_103433.jpg)

## Weapon Entity & Props Entity

Using weapon entities and prop entities, you can generate configured weapons or props at a specified location.

![image-20241115110655472](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241115110655472.png)

**The difference between entity generation points and Loot Point is the following:**

1. Weapon entities and prop entities can choose a specific prop under a certain type, such as M4A1 under the Rifle gun type or maintenance tools under the equipment type, but Loot Point can only choose a certain type.
   - Weapon entities can only select weapons, while prop entities can not only select weapons but also various props.

![image-20241115112549821](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241115112549821.png)

2. Weapon entities and prop entities can freely adjust various parameters of the generated props, such as adjusting the damage per bullet of M4A1 or adjusting the durability value of the bulletproof vest.

![image-20241115112831565](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241115112831565.png)

## Safety Area Items

We can find a custom security zone object from the Interactives category of **Functional Objects**. When we drag it into the scene, we will find that the custom security zone is a combination of two different objects, namely: the security zone start point and the security zone end point.

![image-20241115144930279](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241115144930279.png)

| Name | Illustration |
| ---------- | ----------------------------------------------------------- |
| Starting Point of the Safety Zone | ![image-20241115152704171](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241115152704171.png) |
| Safety Zone End | ![image-20241115152712300](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241115152712300.png) |

The safety zone will change from the range and position of the starting point to the range and position of the end point according to the configuration.

There is no limit on the range or location of the starting and ending points, and you can shrink, expand, or translate the safety zone according to your needs.

The starting objects in the safety area and the end objects in the safety area can be configured with the safety area related configuration:

![image-20241115153058111](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241115153058111.png)

**Initial radius of the safety area:** The initial radius of the safety area, unit is meters. Changing this setting allows you to observe the range changes of the starting object in the scene.

**Final radius of the safety zone:** The final radius of the safety zone, unit is meters. Changing this setting allows you to observe the range changes of the end object in the scene.

**Safety area effective time:** After the start of the round, how long it takes for the continuous bleeding outside the safety area and the effect of continuous bleeding from the safety area to take effect, in milliseconds.

**Time to shrink the ring:** How long it takes to change the safety zone from the starting point position and range to the end point position and range, in milliseconds.

**Start loop shrink time:** How long after the turn begins the safety zone begins to change, in milliseconds.

**Damage interval:** The interval between every two damages outside the safe zone, in milliseconds.

**Damage per time:** The amount of damage caused each time outside the safe zone.

**Safe Zone disappears time:** How long after the turn begins the safe zone disappears. If this time is less than the effective time of the safety zone, the safety zone will not appear at all, unit is milliseconds.

**Reset on each turn:** Whether to reset the safety zone settings to the initial state after a new turn is made.

## Trigger

Triggers are a type of level objects that detect entities entering their own range. They are often used to trigger certain condition events.

We provide some different shapes and basic triggers, and some already featured triggers.

![image-20241115174720049](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241115174720049.png)

**We can divide triggers into three categories:**

| Serial number | Type name | Illustration |
| ---- | ------------ | ------------------------------------------------------------ |
| 1 | Basic class trigger | ![image-20241115175331638](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241115175331638.png)![image-20241115175325269](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241115175325269.png)![image-20241115175317306](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241115175317306.png) |
| 2 | Functional Trigger | ![image-20241115175426181](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241115175426181.png)![image-20241115175415101](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241115175415101.png)![image-20241115175354452](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241115175354452.png)![image-20241115175338868](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241115175338868.png)![image-20241115175346950](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241115175346950.png)![image-20241115175404064](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241115175404064.png) |
| 3 | Musical Instrument Trigger | ![image-20241115175513622](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241115175513622.png) |

### Basic Class Trigger

The difference between basic class triggers is just different in shape and does not have any logic. To use a trigger to trigger a specific event, you need to create a script for the trigger and use the relevant event to detect the trigger's trigger to detect the trigger's trigger.

First, we select the trigger, open **Properties**, and click **Edit Script** on the Setting interface to enter the Element Editor.

![image-20241115180246813](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241115180246813.png)

The trigger can detect whether the entity is from outside to the trigger area or exiting the area. When the player enters/leaves the trigger event only triggers when the player entity enters/leaves the trigger event, any entity can trigger.

![image-20241115180349931](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241115180349931.png)

### Functional Class Trigger

Functional class triggers have their own logic and come with them to detect events in which entities enter or leave from the area. Unless otherwise required, we do not need to add additional logic to the functional class triggers.

**1. Gravity Change Area**

![image-20241118105500276](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241118105500276.png)

In the gravity change zone, the gravity acceleration and jump height will be changed to the set value. At the same time, it can be set whether the area is visible.

When the player jumps in the gravity-changing area, the jump height will be reset to the value set in the gravity-changing area.

![image-20241118142910351](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241118142910351.png)

**2. Death/Invincible Area**

![image-20241118110841353](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241118110841353.png)

Can be set as a Death Zone or Invincible Zone.

Players or AI entities entering the death zone will die immediately. Like other instant death logic, players or AI entities currently in an invincible state will not be affected.

Players or AI entities entering the Invincible Zone will gain an Invincible state until they leave the Invincible Zone. Leaving the Invincible Zone will clear the Invincible state. Even if you have obtained other Invincible effects before, leaving the Invincible Zone will lose the Invincible effect.

You can set whether the area is visible.

![SeaTalk_IMG_20241118_111615](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/SeaTalk_IMG_20241118_111615.jpg)

**3. Climb Detection Area**

![image-20241118114735885](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241118114735885.png)

Players can vault when they enter in reverse of the vault trigger. This is mainly used to vault over obstacles such as windows.

The vault trigger can preview the direction of the vault in the scene. The player must be in the same direction as the vault to trigger the vault key. If you want to achieve bidirectional vaulting, you need to set two of these triggers.

When the player enters the vault trigger, the jump button will be replaced by the vault action button.

![image-20241118115607720](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241118115607720.png)

### Instrument Trigger

When a player touches the instrument trigger, the trigger will make a sound. There are 5 different types of instrument triggers, each with a different color.

Like other triggers, players cannot stand above the instrument trigger and continue to make sounds. They must leave the trigger determination range and enter the trigger again before triggering the decision again.

![image-20241119105335367](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241119105335367.png)

The triggers of instrument types according to different colors will also emit different tones. The scale players of the instrument can set them in the properties of the trigger, open **Properties**, and change the scale of the instrument type trigger in **Music Type** in the Setting interface.

![image-20241119105353417](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241119105353417.png)

## Zombie Monster

Zombies are monsters with AI. In CraftLand, we have two ways to generate zombies, namely, to use zombie generators to generate zombies or to directly place zombie entities to generate zombies.

| Name | Illustration |
| ---------- | ----------------------------------------------------------- |
| Zombie Generator | ![image-20241118150314000](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241118150314000.png) |
| Zombie Entity | ![image-20241118150326449](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241118150326449.png) |

The types and attributes of zombies can be changed regardless of the method.

For an introduction to AI zombies, you can refer to the AI ​​zombies user manual:

[This should be the document link for AI zombies]

Click **Properties** to open the entity's settings interface. Find **Edit** and you can open the zombie attribute settings interface.

![image-20241118153028601](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241118153028601.png)

The same steps are also true in zombie generator.

![image-20241118154429086](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241118154429086.png)

**Zombie attribute settings:**

**Kind:** The kind of generated zombies determines the appearance and ability of zombies.

**Health:** The maximum health limit of the generated zombies.

**Damage:** The damage caused by each attack by zombies.

**Speed:** The movement speed of a zombie, the larger the value, the faster the zombie moves.

**Damage Rate:** All damages taken by zombies must be multiplied by this value.

**Enemy Search Range:** When an enemy appears within this range, the zombie will start chasing. The ranges are divided into near, medium, and far, corresponding to 2, 5, and 10 meters respectively.

**Auto Enemy Search:** Whether to enable the auto enemy search function, if enabled, it will determine whether to pursue the enemy based on the "Enemy Search Range".

**Attack Type:** Attack type is divided into active attacks. Zombies will actively attack after discovering the enemy, passive attacks. After the zombies are attacked, they will passively counterattack. No matter what happens, the zombies will not attack.

**Path:** Zombies can bind the "Path Setter" to control the movement of the zombies.

**Loot:** After we enable the loot drop, we can get random loot such as ammunition, guns, etc., by killing zombies.

**Zombie generator has some special settings compared to zombie entities:**

![image-20241118170444961](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241118170444961.png)

**Zombies per Wave:** The number of zombies generated each time.

**Wave Count:** How many waves of zombies are generated in each round when generated discontinuously.

**Continuous:** Continuous generation, ignoring the wave count setting, continuously generating zombies.

**Start Generation Time:** How long after the round begins, the first wave of zombies will be generated, in seconds.

**Wave Interval Time:** The time between each two waves of generated zombies, in seconds.

**Zombies generated by generators:** will be wiped out at the beginning of the next round and will not drop any loot.

## Shop and Gold Coins

We can find vending machines and coin generators in the Interactives category of **Functional Objects**.

![image-20241119111605290](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241119111605290.png)

![image-20241119111626866](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241119111626866.png)

We usually use this type of object together with the game's economic system, and players can use the gold coins they have obtained to purchase equipment or props in the vending machine.

There are usually several main ways to obtain gold coins in the game:

1. Kill the enemy
2. Obtain the round victory
3. Pick up gold coins

Among them, the third option is to use the gold coins generated by the gold coin generator we introduced here.

When we place a gold coin generator in the scene, a gold coin will be generated at the beginning of the game, and the player can obtain the set number of gold coins when picked up.

In the properties of gold coins, we can set the number of gold coins obtained when the gold coins are picked up, open **Properties**, and adjust the number of gold coins in the **Currency amount** of the Setting interface.

![image-20241119113745838](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241119113745838.png)

Once we have enough gold coins, we can buy equipment and props in the vending machine.

When the player approaches the vending machine, the store icon will appear. Click the store icon to open the store.

![image-20241119115346647](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241119115346647.png)

The vending machine has some unique configurations.

In the vending machine settings interface, we can switch the store opened by the vending machine. The game will create a ‘Default Store1’ as the initial default store, and use the drop-down option of Bind store entity to switch the store you want to open.

![image-20241119144936114](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241119144936114.png)

If you want to add more stores, we can click **More**, and enter **Store and Economy**.

![image-20241119145136584](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241119145136584.png)

Find the Edit Store class, click the plus key to add more stores.

![image-20241119145322339](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241119145322339.png)

For an introduction to the Economy store, you can refer to the Economy store’s user manual:

[This should be the document link of the Economy store]

We can also adjust the interaction range of the vending machine, draw a circle with a diameter of Trigger range with the vending machine as the center. Within this circle, the area where the player can interact with the vending machine.

We can adjust the diameter of the Trigger range circle in the Setting interface of the vending machine.

![image-20241119141423967](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241119141423967.png)

When the vending machine is selected, the red area displayed by the vending machine is the range in which the player can interact with the vending machine.

We can also use the switch to set whether the vending machine is displayed.

Hidden vending machines can still be interacted with.

![image-20241119150719789](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/6_LevelObjects/image-20241119150719789.png)
