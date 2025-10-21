# Economy

# Use the economy module

The economy module allows players to purchase items with currency. A built-in HUD template is often used to quickly set up an in-game shop.

![image-20240828152243244](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20240828152243244.png)

The economy module is an optional module. To use currency, shops, and other content, you need to load the economy module.

![image-20240827165606183](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20240827165606183.png)

After the economy module has been loaded, you can use economy-related blocks in the Script module category.

![image-20240827185355659](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20240827185355659.png)

![image-20240903142435204](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20240903142435204.png)

You can also add currencies and custom shops using the Economy module.

![image-20241114170544374](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20241114170544374.png)

When uninstalling the economy module, please note that all previously used economy module blocks will become invalid, and all custom shops and currencies will be cleared, which may affect your project.

![image-20240827185437279](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20240827185437279.png)

# Currencies and wallets

By default, there is only one default currency in the game. Without additional settings, all Scenes that use currencies are using this default currency.

![image-20240827185019720](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20240827185019720.png)

> 100 default currencies

## New currency

You can create custom currencies in the Economy module.

![image-20240827185850772](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20240827185850772.png)

You can name the new currency, select an icon for it and change its color.

The currency icon can be selected from the pictures included with the project or imported externally.

![image-20240827191301715](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20240827191301715.png)

> Custom image

To use the new currency, you need to set the property of the shop item and the currency given to the player to the currency type. See the relevant content below.

## Add or delete currencies

Currencies must be stored in the wallet, so you need to create a wallet for the player first.

![image-20241114173612703](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20241114173612703.png)

> There is no point in creating multiple wallets, only the wallet created initially will take effect.
>
> Players initially do not have a wallet, but any operation related to the wallet, such as purchasing, opening the built-in shop UI, and displaying the amount of currency, will create a wallet for that player.

Default or custom currencies can be added or removed from the player's wallet.

![image-20241114175126212](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20241114175126212.png)

# Shop

## Shop composition

![image-20241114175200910](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20241114175200910.png)

The shop UI shows a shop entity, which is made up of shelves, which are made up of shop items, which are created.

![image-20241114175659172](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20241114175659172.png)

### Shop items

To use an item as a shop item, add it to the shop items.

![image-20241114175734265](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20241114175734265.png)

For shop items, you can adjust the properties by setting blocks

![image-20241114175807957](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20241114175807957.png)

You can adjust the selling price, currency type, purchase restrictions, product name, icon, and other properties of the shop item.

You can choose between the default currency and a custom currency. If you choose a custom currency, the buyer must have that currency in their wallet before they can purchase the item.

### Shelf

A shelf is a collection of shop items.

![image-20241114175837005](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20241114175837005.png)

After creating a number of shop items, they need to be placed on the shelves:

![image-20241114180008073](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20241114180008073.png)

Shelves can be created and then have their properties modified using blocks.

![image-20241114180029440](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20241114180029440.png)

### Shop

A shop is a collection of shelves.

After creating a number of shelves, they are placed in the created shop, and the shop entity can then execute the selling logic normally.

![image-20241114180200725](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20241114180200725.png)

Properties of the shop:

![image-20241114180215997](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20241114180215997.png)

Below the shop, the amount of the currency type bound to the shop that the player has in their wallet is displayed

![image-20240828155631068](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20240828155631068.png)

> By default, only the quantity of the default currency owned by default is displayed

## Quickly create a shop

You can quickly create a shop in the Economy module, which is more intuitive and faster.

![image-20241114170846319](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20241114170846319.png)

![image-20241114171344238](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20241114171344238.png)

A shelf has already been created for you in the custom shop, and below it you can select the objects that will be your shop items.
Drag an object into the product grid to create a shop item on that shelf.

![image-20241114180704290](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20241114180704290.png)

On the right, you can edit the properties of the selected shop item, including the item's cover image, name, and selling price.

![image-20241114180719177](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20241114180719177.png)

Under Settings, you can add multiple items to individual shop items so that players get all the items in a group when they buy. For example, when buying a weapon, you can also get the ammunition.

![image-20241114181054784](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20241114181054784.png)



## Using shops

There are several ways to display shops in the game.

### Vending machines

There is a function object in the level object: Vending machine. Using the vending machine will open the specified shop entity.

![image-20240828153921490](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20240828153921490.png)

The vending machine comes with three default configurations:

![image-20241114181117915](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20241114181117915.png)

1. Bound shop: The shop used by this vending machine. The shop can be viewed in the economy module, or created or changed at a specified time after entering the game using blocks.
2. Trigger range: The shop button will be activated within a certain distance from the vending machine.
3. Show vending machine: Whether the model of the vending machine is displayed on the map.

To use the shop in the block, you need to add a script to the vending machine.

We encapsulate the logic of creating the shop as a function that returns the created shop, and set the shop created by the function as the shop of the vending machine in the vending machine script.

![image-20241114181336724](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20241114181336724.png)

When you approach a vending machine, a shop icon will be activated first, and tapping on it will open the shop UI.

![image-20240828154712119](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20240828154712119.png)

![image-20240828155110498](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20240828155110498.png)

If you need to use a button to open the shop, it is recommended to use the vending machine object directly. You can achieve this by hiding the object's display and triggering the button shop within a fixed range.

### Built-in shop UI

If you need to directly open the shop UI, for example, opening the shop UI directly at the beginning of a game round, or opening the shop immediately after entering a certain area, you need to use the built-in shop UI.

The built-in shop UI can be created by creating a built-in game UI block:

![image-20240828160536207](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20240828160536207.png)

![image-20240828160620814](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20240828160620814.png)

After creating the built-in shop UI, you can set the property of the UI to bind the shop to the created shop entity.

## Public and private shops

By default, a public shop is created. No additional processing is required, and all players can purchase from this shop. Once all the shop items have been purchased, other players will no longer be able to purchase items from this shop.

If each player needs to use the same shop individually, you can create a shop for each player.

It is highly recommended to encapsulate the creation of a shop as a method or to store the created shop entity in a public variable.

For example, in the global script, open a shop UI for each player who joins the game:

![image-20240828162519430](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20240828162519430.png)

This way, each player's UI uses a different instance created from the same shop entity, which achieves the goal of each person having their own shop.

# Example

Sell an invincible buff in the shop.

First, we create a script under the player module that manages the player's buff:

![image-20240903155517212](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20240903155517212.png)

In this script, write a script for an invincible buff that will give the current player invincibility for 5 seconds:

![image-20240903155534993](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20240903155534993.png)

Place a vending machine in the Scene and add a script to it:

![image-20240903155748790](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20240903155748790.png)

Add a method to the script of the vending machine that creates a shop:

![image-20240903155847418](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20240903155847418.png)

In this shop, there is only one shelf with one item, which does not correspond to any actual item.

Use an exclamation mark for the shop item icon, or any icon you like:

![image-20240903155958935](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20240903155958935.png)

The price of the shop item is set to 100 and the created item is stored in a script variable for later use.

![image-20240903160038460](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20240903160038460.png)

This method is called when the vending machine is created to create the shop entity and bind it to the vending machine:

![image-20240903160257525](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20240903160257525.png)

At this time, the shop already has this shop item, but the invincible buff cannot be triggered.

Create an additional shop script to monitor player purchase events:

![image-20240903160356906](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20240903160356906.png)

> The variable that stores the shop item is a script variable, and here an external link is used to obtain this variable. You can also obtain the shop item entity by setting a global variable.

Because the event of purchasing an item requires the script to be attached to the shop entity, and the shop is created after the game starts, it needs to be dynamically attached.

Back to the vending machine script, attach the shop script to the created shop entity:

![image-20240903160615415](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20240903160615415.png)

This way the shop is already built, but the player doesn't have the money to buy the shop items. Create a global script that adds 500 default currency to each player.

![image-20240903160713451](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20240903160713451.png)

![image-20240903160702615](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20240903160702615.png)

Running the game:

Initially, neither of the first two players is invincible:

![image-20240903160804430](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20240903160804430.png)

The shop is open, the shop items are there, and the amount of currency in the player's wallet is as expected:

![image-20240903160813727](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20240903160813727.png)

The purchase was successful, and the player who made the purchase gained invincibility:

![image-20240903160822669](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20240903160822669.png)

After 5 seconds, the invincibility effect ends:

![image-20240903160829176](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20240903160829176.png)

When you open the shop again, you notice that the money has been reduced by 100 as normal:

![image-20240903161018595](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/16-Economy/image-20240903161018595.png)
