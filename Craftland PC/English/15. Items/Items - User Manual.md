# Items

A firearm, a grenade, some bullets, these are all items, and the concept of items is inseparable from the gameplay when it comes to equipment or props.

Items depend on the player backpack to exist while they are on the player. The player backpack holds these items.

# Classification of Items 

Items possess the following classifications: 

## Equipment 

Equipment consists of weapons, defenses, backpacks, accessories, and functional equipment.

Where backpacks refer to the props of a specific backpack, rather than the concept of holding items as mentioned above.

![image-20240821150846221](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/15-Items/image-20240821150846221.png)

> Backpacks

## Consumables

Consumables contain grenades, healing props, special props, and various types of bullets.

# Player Backpacks 

Player backpacks here are distinguished from rucksacks by the abstract notion of space for items owned by the player, whereas rucksacks increase the space in the player's backpack and provide variations in appearance skins.

![image-20240821152243567](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/15-Items/image-20240821152243567.png)

> Player Backpacks 

## Backpack Contents Category 

### Equipment Bar 

The 1. part of the image above is the equipment bar in the player's backpack. Inside the equipment bar are the player's currently equipped weapons, defenses, backpacks, and functional equipment.

### Consumable Bar 

The 2. part of the image above is the consumable bar button in the player's backpack, with the area directly below it displaying the consumable.

![image-20240821152456167](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/15-Items/image-20240821152456167.png)

> When with consumables

all visible consumables are stored here.

### Device Bar 

The 3. part of the backpack image, is the device bar button. For the editor, there is currently only one device, the Ice Wall Generator.

![image-20240821154645057](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/15-Items/image-20240821154645057.png)

Devices can be turned on by the script to be turned on, and the equipment that is turned on is shown in the backpack under that category.

![image-20240821154756422](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/15-Items/image-20240821154756422.png)

### Black Hole Space 

Equipments and consumables that are not displayed in the backpack interface will exist in Black Hole Space, and players will not be able to view the consumable directly in the backpack.

### Using items in the backpack 

Generally speaking, most items can be used outside of the backpack or automatically. This includes weapons, accessories, grenades, etc.

But it is still possible to perform certain actions in the backpack.

To use a given item: 

![image-20240821160116244](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/15-Items/image-20240821160116244.png)

Remove/ Replace/Install attachments: 

![image-20240821160157425](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/15-Items/image-20240821160157425.png)

![image-20240821160207806](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/15-Items/image-20240821160207806.png)

> Remove attachments

Discard the items in your backpack: 

![image-20240821160306511](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/15-Items/image-20240821160306511.png)

# Arranging items in the scene 

There are two ways to generate items at a given location: generators and units.

Using generators to generate items can be set to refresh every turn, but only the type can be specified. If the last generated item is not taken when it is refreshed, it will be replaced with the newly generated item.

Using units to place items allows you to set the exact type of weapon or item to be generated, by default only one copy of the corresponding item will be generated.

## Generator 

![image-20240730180747977](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/15-Items/image-20240730180747977.png)

![image-20240730180753598](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/15-Items/image-20240730180753598.png)

Depending on the type Select the corresponding generator, take weapons for example: 

![image-20240730181011764](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/15-Items/image-20240730181011764.png)

In configuration In the configuration you can choose the type of weapon to generate: 

![image-20240730181034487](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/15-Items/image-20240730181034487.png)

This generator can be set per turn in the reset component. In the reset component you can set whether this generation point will refresh at the start of each turn.

![image-20240730181104786](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/15-Items/image-20240730181104786.png)

Special. When choosing to generate a weapon, a matching set of ammo and accessories will be generated.

## Unit 

![image-20240730175100849](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/15-Items/image-20240730175100849.png)

Using the units in the unit to generate a configured weapon or prop at the specified location.

![image-20240730175225713](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/15-Items/image-20240730175225713.png)

Items that are placed in this Items placed in this way can have their properties modified: 

![image-20240730184405465](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/15-Items/image-20240730184405465.png)

![image-20240730184527556](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/15-Items/image-20240730184527556.png)

# items Events 

You can listen to some item-related events to implement the logic you want.

Here are some common events: 

| Name                   | Script Name  | Description                                                  | Parameter 1                                         | Parameter 2                                                  | Parameter 3 | Dependent Entity |
| ---------------------- | ------------ | ------------------------------------------------------------ | --------------------------------------------------- | ------------------------------------------------------------ | ----------- | ---------------- |
| When acquiring an item | OnObtainItem | Triggered when the player acquires an item from any source   | Item ID, the ID of the item acquired by the player  | Item Entity, the entity of the item acquired by the player, can be null |             | Player           |
| When using the item    | OnUseItem    | Triggered when the player uses the item                      | Item ID, the ID of the item used by the player      | Item Entity, the entity of the item used by the player, can be null | Player      |                  |
| When dropping props    | OnDropItem   | Triggered when the player drops an item                      | Item ID, the ID of the item that the player dropped | Item Entity, the entity of the item that the player dropped, can be null |             | Player           |
| When Picked Up         | OnPickup     | Triggered when the item is picked up, need to be mounted on the Item Entity |                                                     |                                                              |             |                  |
| When used              | OnUsed       | Triggered when the item is used, needs to be mounted on the item entity |                                                     |                                                              |             | InventoryBase    |
| When discarded         | OnDrop       | Triggered when the item is discarded, needs to be mounted on the item entity |                                                     |                                                              |             |                  |

# Item APIs 

Items can be manipulated using the item APIs.

Some common APIs are categorized below: 

**Add items**

| Name                 | ScriptName     | Description                            | Input Parameter 1 | Input Parameter 2 | Input Parameter 3 | Return Parameter 1                                           |
| -------------------- | -------------- | -------------------------------------- | ----------------- | ----------------- | ----------------- | ------------------------------------------------------------ |
| Add Item             | AddItem        | Send items to player's backpack        | Player            | Item              | Quantity of items | List of added items. Returned as a list, regardless of the quantity |
| Create Item In Scene | AddItemInScene | Create items in the specified location | Position of items | Item              | Quantity of items |                                                              |

**Delete Items** 

| Name              | ScriptName      | Description                                               | Input Parameter 1 | Input Parameter 2 | Input Parameter 3 | Return Parameter 1 |
| ----------------- | --------------- | --------------------------------------------------------- | ----------------- | ----------------- | ----------------- | ------------------ |
| Destroy Item      | DestroyItem     | Remove items from player                                  | Player            | Item              | Quantity of items |                    |
| Destroy Equipment | DeleteEquipment | Destroys a player's equipped item(s)according to its slot | Player            | Slot              | Quantity of items | Success or not     |
| Clear Backpack    | ClearBackpack   | Empty all items from the player, including equipped items | Player            |                   |                   |                    |

**Query Items**

| Name           | ScriptName    | Description                                          | Input Parameter 1 | Input Parameter 2 | Return Parameter 1   | Return Parameter 2                     |
| -------------- | ------------- | ---------------------------------------------------- | ----------------- | ----------------- | -------------------- | -------------------------------------- |
| Get Equipments | GetEquipments | Get the equipment according to the slot              | Player            | Slot              | Equipment entity     | List of attachments for this equipment |
| Get Item Count | GetItemCount  | Get the quantity of an item in the player's backpack | Player            | Item ID           | Quantity of the item |                                        |

**Modify Items**

| Name            | ScriptName     | Description                                                  | Input Parameter 1 | Input Parameter 2 | Input Parameter 3  | Return Parameter 1 | Return Parameter 2 |
| --------------- | -------------- | ------------------------------------------------------------ | ----------------- | ----------------- | ------------------ | ------------------ | ------------------ |
| Add Attachments | AddAttachments | Give the player an attachment for the weapon in certain slot | Player            | Slot              | Attachment item ID | Success or not     | Attachment entity  |
| Switch Weapon   | SwitchWeapon   | Switch weapon in slot to player's current weapon             | Player            | Slot              |                    | Success or not     |                    |
