# Player

Player is an important concept in the game. In Craftland, we have given the player entity basic functions such as health, movement, and backpack by default. If you want to further expand the function, attribute, appearance, or action performance of the player entity, you can also use the primitive editor to expand the logic. This article will introduce the important concept of player from two aspects: player primitive and player script.

> Players exist in the game as instances of player entities, which means that edits in the module will be mapped to each player entity instance created, and for scripts, it is important to pay attention to whether the scope of action is "a specific player" or "all players".

## Player Entity Settings

The default player created in CraftLand is basically the same as the player in FF, with some basic functions such as moving, jumping, picking up, and shooting. So the operations performed by the player in our FF game can be reproduced in CraftLand.

In CraftLand we cannot directly modify the player's entity properties, nor can we directly view the components mounted on the player entity. However, we can find some configurations corresponding to the player entity in the settings.

The player's setting options are divided into 3 categories: basic, skill settings, and pet settings.

### Base

Some basic attribute settings of the player entity.

![image-20241121171440547](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/8_Player/image-20241121171440547.png)

**Life Limit:** The player's maximum health value, ranging from 20-1000.

**EP Cap:** The player's maximum EP, ranging from 0-200.

**Initial EP Ratio:** The initial EP owned by the player = Initial EP Ratio * EP Cap, ranging from 0%-100%.

**EP Fast Conversion:** Whether to enable fast conversion of EP to HP.

**Unlimited Ammo:** Whether to enable unlimited ammo.

**Infinite Ice Wall:** Whether to enable infinite ice wall.

**Unlimited Throws:** Whether to enable unlimited throws.

**Damage Rate:** The damage caused by the player ranges from 0% to 500%, with 0% causing no damage.

**Injury Rate:** The percentage of damage the player will take when injured, ranging from 0% to 500%, with 0% causing no damage.

**Movement Speed:** The scaling ratio of movement speed. Less than 100% is slower than the default speed, and greater than 100% is faster than the default speed. The range is 50%-500%.

**Jump Height:** The scaling ratio of the jump height. Less than 100% is lower than the default height, and greater than 100% is higher than the default height. The range is 10%-500%.

### Skill Settings

In the skill settings, we can control the switch status of passive skills and active skills. If our game prohibits the use of skills, we can directly turn off the skill system, then all players in the world will not be able to use skills even if they are equipped with skills.

![image-20241122104409773](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/8_Player/image-20241122104409773.png)

**Passive Skills:** Whether to enable passive skills.

**Active Skills:** Whether to enable active skills. If disabled, the cooldown rate of all skills cannot be adjusted.

**Cooling Time:** The lower limit of cooling time is 0%, and the upper limit is 100%. 0% means no cooling time, and 100% is calculated according to the cooling time of the skill itself.

### Pet Settings

In the pet settings, we can change the activation status of the pet system.

![image-20241122111147660](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/8_Player/image-20241122111147660.png)

**Pet:** Whether to enable the pet system.

**Pet Skills:** Whether to enable pet skills.

## Player Script

The player script we created is actually a component mounted on the player entity, but in CraftLand we cannot directly view all the components mounted on a certain entity.

The game will not create a player script by default, so first we need to open a player script.

First, we click **Setting** in the upper left corner of the interface to open the settings border, select **GamePlay Settings**, and click **Edit Gameplay Rules** to enter the settings interface.

![image-20241121142412976](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/8_Player/image-20241121142412976.png)

After entering the settings interface, select the **Player Rules** category in **Property Setting** and click **Player Script** to open the player script.

![image-20241121143424135](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/8_Player/image-20241121143424135.png)

![SeaTalk_IMG_20241121_154847](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/8_Player/SeaTalk_IMG_20241121_154847.jpg)

When we write the primitive block in the player script, the player script will be automatically mounted on the player entity. All player entity instances created at the beginning of the game will have the new logic and functions we created.

## Related Primitives

Because the player script is attached to every instance of the player entity, be aware that global events may fire multiple times unintended.

Usually, we will expand and rewrite the player entity in the player script. Through private event triggering, we can limit the scope of the triggered object:

![image-20241121164231670](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/8_Player/image-20241121164231670.png)

### Example

Example logic: After killing a player, the killer will be given an M60.

First, we need to know that there are two "when the player causes a kill" events, they are player script private events and global public events.

![image-20241122155234399](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/8_Player/image-20241122155234399.png)

![image-20241122155242226](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/8_Player/image-20241122155242226.png)

When we add the same logic to these two events,

**Private 'When Player Causes Kill' Event:**

![image-20241122155703305](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/8_Player/image-20241122155703305.png)

The private event "When a player causes a kill" will only be triggered when the current player entity instance causes a kill.

Adding an item adds an M60 when this entity instance causes a kill. This entity is the one that causes the kill, so the requirement can be met.

> In actual editing, you also need to consider whether the M60 weapon is full when adding it.

**Public 'When Player Causes Kill' Event:**

![image-20241122155734121](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/8_Player/image-20241122155734121.png)

For example, if you use the public event "When a player kills", all players will be given an M60 when any player kills. It is recommended to put similar logic in the global script.

Therefore, it is not recommended to use public events to create logic in some cases.
