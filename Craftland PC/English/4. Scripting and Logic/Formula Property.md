# Formula Property

In Craftland Studio PC, some of the player's properties and the properties of weapons support formula calculations. This helps to implement more complex numerical operations.

For properties that support formula calculations, it has the following formula parameters:

```go
type Formula struct{
	minValue float32
	maxValue float32
	baseMul float32
	beforeAccumulator float32
	multiplier float32
	afterAccumulator float32
	SumMultiplier float32
}
```

The calculation logic is as follows:
$$
FinalValue=Min(maxValue,Max(minValue,(BaseValue×baseMul+beforeAccumulator)×multiplier×(1+SumMultiplier)+afterAccumulator))
$$


where BaseValue is the base value of this property.

Assuming that the player's maximum health is 200, and no parameters are set, the player's health will be 200.

With the following settings:

```
baseMul = 1.1
beforeAccumulator = -100.0
```

The player's maximum health is equal to:
$$
PlayerMaxHp = (200×1.1-100.0)×1×(1+0)+0=120
$$

# Setting calculable parameters

In the script, you can set calculable parameters for specific properties or clear all calculable parameters:

![image-20241011190938191](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/27-FormulaProperty/image-20241011190938191.png)

In the example above:

![image-20241011191814593](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/27-FormulaProperty/image-20241011191814593.png)

![image-20241011191829255](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/27-FormulaProperty/image-20241011191829255.png)

**Attention:** Setting a calculable parameter sets a formula for the property calculation, not the property value directly.

The property interface sets the BaseValue of the property, and if a formula has already been added to the property, the final result will be the result after the formula is calculated.

![image-20241011192558886](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/27-FormulaProperty/image-20241011192558886.png)

![image-20241011192613986](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/27-FormulaProperty/image-20241011192613986.png)

# Weapon damage calculation

There are also formulas for calculating weapon damage, and the formula parameters have been opened up as weapon properties, such as Min Damage and Min Damage Distance.

## Weapon base damage

The parameters related to the damage of a single bullet from a weapon are:

1. Damage
2. Min Damage
3. Min Damage Distance
4. Full Damage Distance
5. Range

![image-20241014150200654](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/27-FormulaProperty/image-20241014150200654.png)

When within Full Damage Distance, the weapon deals Full Damage. Between Full Damage Distance and Min Damage Distance, the weapon deals decreasing Damage, and at Min Damage Distance deals Min Damage. The weapon cannot deal Damage when outside Range.

All parameters may be affected by Attachments or Skins, which generally increase the weapon's Damage parameters directly.

## Hit Part Damage Multiplier Adjustment

When the weapon hits different parts of the character, the damage will be adjusted by different multiples.

1. When hitting the head, the part damage multiplier is 5.5 + Headshots DMG ratio, and the damage ratio will decay with distance.
2. When hitting the body, the part damage multiplier is 1 + Body shots DMG ratio.
3. When hitting the limbs, the part damage multiplier is 0.75 + Limb shots DMG ratio.

When calculating the part damage multiplier, each part is calculated separately. Assuming a single bullet hits the torso and causes 30 points of damage, if the Body shots DMG ratio is set to 1, the single bullet will now cause 30*(1+1)=60 points of damage within the maximum damage distance. However, when calculating headshot damage, the base damage of 30 is multiplied by the Headshots DMG ratio, not the 60 after the Body shots DMG ratio.

## Calculating modified damage

In some situations, the damage dealt by the weapon is further modified.

1. Attachment characteristics: Damage increases with each shot until it reaches its maximum value.
2. Additional damage to knocked-down units.
3. The percentage of additional damage dealt to special objects such as cars, oil drums, and ice walls.

## Calculate armor reduction

If the unit being hit is wearing armor, an additional armor reduction is calculated.
$$
RealDamage *= (1 - DmgReduction)
$$

$$
DmgReduction = DmgRedfactor* CurrentDurability/DurabilityMax* (1 - AromrPenetration)
$$

- DmgRedfactor: equipment property, damage reduction rate.
- CurrentDurability: equipment property, current durability. When damage is dealt to the player, the durability of the equipment is also reduced by the value of the equipment.
- DurabilityMax: equipment property, total durability.
- AromrPenetration: armor penetration of weapon + armor penetration of skill + armor penetration of FS mode. Armor penetration range is [0,1].

## Other properties

The following properties also affect the damage dealt by the player's weapon in actual combat.

- Fire rate 
- Weapon spread
- Crosshair recovery speed
- Bullet capacity
- Assisted aiming
- Effect of weapon on movement speed
