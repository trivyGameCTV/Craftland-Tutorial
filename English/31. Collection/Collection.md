# Collection

# Collections - User Manual

Collections is a module used to manage cosmetic assets such as weapon skins, character skins, and vehicle skins used by players in the game.

![image-20241028181225684](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/31-Collection/image-20241028181225684.png)

This is an optional module that can be enabled or disabled at your discretion.

By default, players joining a custom map you've created will bring their own collections with them, such as character skins and weapon skins.

You can configure and enable the Collections module to adjust the collections that players use in this game.

# Collections mechanism

Items are equivalent to the skins that players equip outside of a game, such as gun skins and vehicle skins. There is no necessary link between obtaining weapons, vehicles, backpacks and using skins. When a player obtains the corresponding weapon, vehicle or backpack, the appearance will automatically be replaced with the currently equipped skin.

![image-20241029174635102](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/31-Collection/image-20241029174635102.png)

When a weapon is discarded, the weapon skin will display the default state.

![image-20241029175218878](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/31-Collection/image-20241029175218878.png)

When you stop using a vehicle, it will retain the skin configuration of the last user.

![image-20241029175253517](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/31-Collection/image-20241029175253517.png)

Each player can only use one Skin for each weapon, vehicle, and dress-up part.

In particular, Emotes are also considered player collections, and their playback can be managed through the Collection Module.

![image-20241029181511199](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/31-Collection/image-20241029181511199.png)

# Collection properties, skill switch

In the Mechanics Parameters module, there are two configuration options related to collections.

Switching these two options can control whether the Gun Skin affects the Gun's values and whether the Gun Skin carries skills, respectively.

![image-20241029171827371](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/31-Collection/image-20241029171827371.png)

# Editing collections

After enabling the collections module, the relevant blocks can be used in the block script.

![image-20241029173325668](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/31-Collection/image-20241029173325668.png)

By default, players will enter the game with their skin configuration from the FreeFire game.

## Get Skin

By getting the Skin block, you can get the ID of the Skin currently being used by the player. Even if the player does not currently have the weapon, vehicle, or backpack corresponding to that Skin, the Skin ID will still be returned.

![image-20241029181213641](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/31-Collection/image-20241029181213641.png)

## Set Skin

![image-20241029175619832](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/31-Collection/image-20241029175619832.png)

Setting a skin will overwrite the player's real-owned collection configured outside the game with a temporary collection directly.

When setting clothing, you need to pay attention to using clothing that corresponds to the gender. Clothing that does not match the gender is equivalent to the player configuring in the appearance group of the other gender, and will not be displayed directly in the game.

![image-20241029180929998](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/31-Collection/image-20241029180929998.png)

## Remove Skin

Removing a Skin will remove any configured Skin settings, whether they are owned Collections configured outside of the game, or temporary Collections added inside the game.

![image-20241029181649505](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/31-Collection/image-20241029181649505.png)

## Restore Skin

Restore Skin will reset the skin settings to the player's actual owned collections outside of the game, only clearing the collections temporarily added inside the game.

![image-20241029181824040](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/31-Collection/image-20241029181824040.png)

## Out-of-game Skin Settings

Weapons, vehicles, and backpacks all have two collection-related properties: Skin and Player Configuration Priority.

![image-20241029182228316](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/31-Collection/image-20241029182228316.png)

You can modify it in the inspector panel when configuring the corresponding object in the Scene or dynamically through a script.

### Skin Settings

This setting will change the default skin of the object itself. For example, the weapon will restore the default skin when it is discarded. After modifying the configuration here, the discarded weapon will restore the appearance of the configured skin.

![image-20241029182653049](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/31-Collection/image-20241029182653049.png)

### Use player's off-server settings

Enable this setting so that the player's real-world collections and temporary collections added via the collection module blocks will be displayed on the item.

Disable this setting so that the item will always maintain the configured Skin.
