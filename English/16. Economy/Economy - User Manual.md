# Economy - User Manual

## Using the Economy Module

The economy module allows players to purchase items with currency. It's commonly used in built-in HUD templates to quickly set up an in-game store.

![image-20240828152243244](./img/image-20240828152243244.png)

The economy module is optional. To use currency, stores, and related features, you need to load the economy module.

![image-20240827165606183](./img/image-20240827165606183.png)

Once the economy module is loaded, you can use economy-related elements in the script's module category.

![image-20240827185355659](./img/image-20240827185355659.png)

![image-20240903142435204](./img/image-20240903142435204.png)

When unloading the economy module, be aware that previously used economy elements will become invalid, which may affect your project.

![image-20240827185437279](./img/image-20240827185437279.png)

## Currency and Wallets

By default, there is only one default currency in the game. Without additional settings, all scenarios using currency will use this default currency.

![image-20240827185019720](./img/image-20240827185019720.png)

> 100 default currency

### Creating New Currency

You can create custom currencies within the economy module.

![image-20240827185850772](./img/image-20240827185850772.png)

You can name the new currency, choose its icon, and change its color.

Currency icons can be selected from built-in images or imported images. Imported images will appear at the bottom of the image selector.

![image-20240827191301715](./img/image-20240827191301715.png)

> Custom image

To use newly created currency, set the item properties and player-given currency to this type. See related content below.

### Adding and Removing Currency

Currency must be stored in a wallet, so you need to create a wallet for the player first.

![image-20240828151137222](./img/image-20240828151137222.png)

> Creating multiple wallets is pointless; only the initially created wallet will be effective.
>
> Players initially have no wallet, but any wallet-related operations, such as purchasing, opening the built-in store UI, or displaying currency amounts, will create a wallet for that player.

You can add or remove default or custom currencies from a player's wallet.

![image-20240828151500938](./img/image-20240828151500938.png)

## Store

### Store Composition

![image-20240828152243244](./img/image-20240828152243244.png)

A store interface displays a store entity composed of shelves, which are made up of items created as products.

![image-20240903144305251](./img/image-20240903144305251.png)

#### Products

To use items as products, add them to the product list to make them usable as products.

![image-20240828152412538](./img/image-20240828152412538.png)

For products, you can adjust properties by setting elements.

![image-20240828152513466](./img/image-20240828152513466.png)

You can adjust product price, currency type, purchase limits, product name, icon, and other attributes when used as a product.

The currency type can be set to default or custom. If custom currency is chosen, purchasing the product requires that currency in the buyer's wallet.

#### Shelves

Shelves are collections of several products.

![image-20240828152835055](./img/image-20240828152835055.png)

> Two shelves in this store

After creating several products, place them on shelves:

![image-20240828153035117](./img/image-20240828153035117.png)

Shelf properties can also be modified after creation.

![image-20240828153325349](./img/image-20240828153325349.png)

#### Store

A store is a collection of shelves.

After preparing several shelves, place them into the created store. The store entity can then execute sales logic normally.

![image-20240828153500270](./img/image-20240828153500270.png)

Store properties:

![image-20240828153543096](./img/image-20240828153543096.png)

Below the store, it will display the amount of store-bound currency type owned by the player's wallet.

![image-20240828155631068](./img/image-20240828155631068.png)

> By default, only the amount of default-owned default currency is displayed.

### Creating a Store

In sequence, first create the product, then the shelf, and finally the store. This gives us a store entity. However, it cannot yet be displayed in the game.

We can display the store in the game using the following methods.

#### Vending Machine

There is a functional object in the level objects: the vending machine. Using it can open a specified store entity.

![image-20240828153921490](./img/image-20240828153921490.png)

The vending machine has two default configurations:

![image-20240828154220013](./img/image-20240828154220013.png)

1. Trigger Range: Activates the store button within a certain distance from the vending machine.
2. Display Vending Machine: Determines whether the vending machine model is shown on the map.

To use a created store entity, you need to add a script to the vending machine.

We encapsulate the logic of creating a store into a function that returns the created store. In the vending machine script, set the store created by this function as the vending machine's store.

![image-20240828154815437](./img/image-20240828154815437.png)

When approaching the vending machine, a store icon will first be activated. Clicking this icon will open the store interface.

![image-20240828154712119](./img/image-20240828154712119.png)

![image-20240828155110498](./img/image-20240828155110498.png)

If you need to open the store with a button, it's recommended to use the vending machine object directly. You can achieve button-triggered stores within a fixed range by hiding this object.

#### Built-in Store UI

If you need to open the store UI directly, such as at the start of a game round or when entering a specific area, use the built-in store UI.

The built-in store UI can be created by making an in-game UI element:

![image-20240828160536207](./img/image-20240828160536207.png)

![image-20240828160620814](./img/image-20240828160620814.png)

After creating a built-in store UI, bind its properties to the created store entity.

### Public and Private Stores

By default, a public store is created, which requires no extra handling. All players can purchase from it, but once items are sold out, others can't buy them anymore.

If each player needs their own instance of the same store, create one for each player.

> It's strongly recommended to encapsulate store creation into a method or save created store entities into a public variable.

For example, in a global script, open a store UI for each player joining the game:

![image-20240828162519430](./img/image-20240828162519430.png)

This way, each player's UI uses different instances of the same store entity, allowing everyone to have their own exclusive store.

## Example

Selling an invincibility buff in a store.

First, create a script under the player module to manage player buffs:

![image-20240903155517212](./img/image-20240903155517212.png)

In this script, write an invincibility buff that grants 5 seconds of invincibility to the current player:

![image-20240903155534993](./img/image-20240903155534993.png)

Place a vending machine in the scene and add a script to it:

![image-20240903155748790](./img/image-20240903155748790.png)

In the vending machine's script, write a method to create a store:

![image-20240903155847418](./img/image-20240903155847418.png)

In this store, there is only one shelf with one product that doesn't correspond to any actual item.

Choose an exclamation mark or any icon you like for the product icon:

![image-20240903155958935](./img/image-20240903155958935.png)

Set the product price at 100 and save it into a script variable for later use.

![image-20240903160038460](./img/image-20240903160038460.png)

When creating the vending machine, call this method to create a store entity and bind it to the vending machine:

![image-20240903160257525](./img/image-20240903160257525.png)

At this point, there's already this product in the store but it can't trigger invincibility yet.

Create an additional store script to monitor player purchase events:

![image-20240903160356906](./img/image-20240903160356906.png)

> Since we're using script variables for storing products above, here we use external links to access these variables. Alternatively, you can save product entities into global variables via component properties.

Since this script handles purchase events and needs to be mounted on the store entity created during gameplay, it requires dynamic mounting.

Go back to the vending machine script and mount this store script onto the created store entity:

![image-20240903160615415](./img/image-20240903160615415.png)

Now that the store is complete but players don't have money for purchases yet, create a global script adding 500 default currency for each player.

![image-20240903160713451](./img/image-20240903160713451.png)

![image-20240903160702615](./img/image-20240903160702615.png)

Run the game:

Initially, neither player has invincibility:

![image-20240903160804430](./img/image-20240903160804430.png)

Open the store; products are available and players' wallets have expected amounts:

![image-20240903160813727](./img/image-20240903160813727.png)

Purchase successful; buying player gains invincibility effect:

![image-20240903160822669](./img/image-20240903160822669.png)

5 seconds later, invincibility ends:

![image-20240903160829176](./img/image-20240903160829176.png)

Reopen the store and notice 100 currency has been deducted correctly:

![image-20240903161018595](./img/image-20240903161018595.png)
