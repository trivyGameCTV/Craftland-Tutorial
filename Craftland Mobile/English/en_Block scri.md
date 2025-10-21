# Block script

<iframe width="560" height="315" src="https://www.youtube.com/embed/xUrEDDpLn-8?si=RNtOhv-YoC6knwSL" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

# What is a block script?

![image-20250402145046440](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/009_BlockScript_New/image-20250402145046440.png)

Have you ever noticed that the characters' heads in Free Fire become very big?

This effect is achieved using a powerful block script.

![image-20250402192617114](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/009_BlockScript_New/image-20250402192617114.png)

Block script is a visual programming method that allows you to write highly customized game logic.

# Entry point

You can find the entry point to block script under the More menu.

![image-20250402145458469](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/009_BlockScript_New/image-20250402145458469.png)

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/009_BlockScript_New/image-20250402145643612.png" alt="image-20250402145643612" style="zoom:33%;"/>

There are also some other locations where you can enter the block script editing interface. You can find the entry for block scripts under Basic Settings and Property Settings in Edit Gameplay Rules . The editing interface they enter is the same. 

# Basic introduction to blocks

## Editor

First, we can see the important areas in the block editor.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/009_BlockScript_New/image-20250402181900017.png" alt="image-20250402181900017" style="zoom:50%;"/>

On the left there are all the available blocks in different categories. In the center is the editing scene we call the "canvas". Blocks need to be dragged and dropped into the canvas to take effect.

## Block categories

There are two core categories of blocks:

1. Events, which determine when logic is triggered, e.g. whenever a player joins the game, or when the start of a round. The currently available events for the script are in the red block category
2. Actions, which are instructions to the game. In our case, we need an action to make the character's head bigger! You can find the vast majority of actions in the green and blue block categories.

## Using blocks

From the left, hold down the block and drag it into the canvas to use it in the current script.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/009_BlockScript_New/image-20250402182437921.png" alt="image-20250402182437921" style="zoom:50%;"/>

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/009_BlockScript_New/image-20250402182455584.png" alt="image-20250402182455584" style="zoom:50%;"/>

Blocks can be connected to each other.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/009_BlockScript_New/image-20250402182616637.png" alt="image-20250402182616637" style="zoom:50%;"/>

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/009_BlockScript_New/image-20250402182630147.png" alt="image-20250402182630147" style="zoom:50%;"/>

## Manipulating blocks

### Selecting

Clicking on a block will select it, and a block operation panel will appear directly below the canvas, with the selected block highlighted.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/009_BlockScript_New/image-20250402184106420.png" alt="image-20250402184106420" style="zoom:67%;"/>

### Delete

Click to delete. This will delete the selected block from the group of blocks, and the blocks below will automatically fill upwards.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/009_BlockScript_New/image-20250402184414500.png" alt="image-20250402184414500" style="zoom:67%;" />

You can also drag connected blocks into the right side to delete it.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/009_BlockScript_New/image-20250402184634175.png" alt="image-20250402184634175" style="zoom:67%;" />

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/009_BlockScript_New/image-20250402184645257.png" alt="image-20250402184645257" style="zoom:67%;" />

### Undo and redo

Worried about making a mistake? The shortcut menu on the right allows you to undo or redo all changes to the block script:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/009_BlockScript_New/image-20250402184455422.png" alt="image-20250402184455422" style="zoom:67%;" />

### Block data

As you may have noticed, there are various colored blocks and plus signs on the blocks. This indicates the data that the block can provide for the block **below it** and the data it needs.

![image-20250402160101108](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/009_BlockScript_New/image-20250402160101108.png)

> Some of the required data has already been filled in with a default value for you, such as "Auto Play" in the image above

Each block has its own unique logic, and the data provided and the data required are of different data types. Sometimes, we have to use data blocks, variables, and even functions to provide and receive data. After all is said and done, a game is just a bunch of data calculations.

# Make Player's head bigger

Now that you know how to manipulate blocks, let's follow along and make the character's head bigger in your map!

All we need to do is complete the block script like this:

![image-20250402192617114](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/009_BlockScript_New/image-20250402192617114.png)

Don't let the length scare you, the core is just to set the zoom of the header to three times the default size.

![image-20250402192733907](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/009_BlockScript_New/image-20250402192733907.png)

First, let's prepare the blocks we need:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/009_BlockScript_New/image-20250402151812785.png" alt="image-20250402151812785" style="zoom:33%;" />

Adjusting the head zoom is a bit more complicated, because you cannot get the zoom of the player's head directly from the player properties. So we need Get property block to help us get properties that cannot be read directly from Set property block .

We use Get property to get the player's rig:

![image-20250402153444311](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/009_BlockScript_New/image-20250402153444311.png)

> The target entity of Get property is dragged down from On Player Join, which means: Whenever a player joins the game, get the properties of the player who has joined the game.

Use the obtained rig as the target entity and continue to get the "head"

![image-20250402153810754](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/009_BlockScript_New/image-20250402153810754.png)

Drag the "head" you obtained above into Set property, and select the property "Skeleton Scale":

![image-20250402154010766](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/009_BlockScript_New/image-20250402154010766.png)

Click the plus sign next to Value and select the Vector3 assignment block from the left.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/009_BlockScript_New/image-20250402154128112.png" alt="image-20250402154128112" style="zoom: 67%;" />

Fill in X, Y, and Z with 3.

![image-20250402154314494](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/009_BlockScript_New/image-20250402154314494.png)

> Vector3 is a data type consisting of three numbers. Here, the default scale of the rig is (1,1,1). Filling in (3,3,3) means that the head is enlarged three times in all three dimensions of 3D space. You can also try filling in different combinations of numbers to see the actual performance.

Finally, let's connect the Set Property block to the On Player Join block. Only connected blocks make the logic work.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/009_BlockScript_New/image-20250402154557829.png" alt="image-20250402154557829" style="zoom:67%;" />

Click on the debug button to enter the game and see how it performs:

![image-20250402154750511](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/009_BlockScript_New/image-20250402154750511.png)

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/009_BlockScript_New/image-20250402154804522.png" alt="image-20250402154804522" style="zoom:67%;" />

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/009_BlockScript_New/image-20250402154814476.png" alt="image-20250402154814476" style="zoom: 67%;" />

There are even more powerful functions in the block script waiting to be discovered by you.

# Different scripts

The same block may behave differently in different scripts!

This is because, in addition to the "global script" we just used, each player will have a "player script" and each team will have a "team script". If you wish, you can even add scripts to objects and consumables in the Scene.

Scripts take effect on the entity they are on. If an event such as "On Player Join" is placed on the "player script", then every player on the field (including the new player) will respond to this event whenever a player joins. If our block is to give the player an M4A1 when he joins, if it is placed in the global script, then each player will have one M4A1; if it is placed in the player script, each player will give the new player an M4A1, and the new player will have too many guns to handle!
