# Customizing the UI

<iframe width="560" height="315" src="https://www.youtube.com/embed/xUrEDDpLn-8?si=RNtOhv-YoC6knwSL" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

# What is the UI

UI stands for User Interface. In games, such as the fire button, minimap, and crosshair — all part of the game's UI.

In short, the UI is the way you communicate with the game.

# Making a button that makes a sound

Let's make a button that makes a sound when clicked.

## Entering the UI editor

First, you need to go to the UI editor from "More" - "Customize UI", where you will create a UI.

![image-20250410105044685](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410105044685.png)

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410111319600.png" alt="image-20250410111319600" style="zoom:40%;" />

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410111716960.png" alt="image-20250410111716960" style="zoom:40%;" />

In the UI management interface, you can rename, copy and delete the entire UI at 1., edit the logic of the blockscript at 2., or edit the various elements on the UI at 3.

We don't have any elements yet, so let's go directly to the layout editor from 3.

## Add a button widget

In layout editing, the center is our UI canvas, and the bottom left corner is where we can place elements on the canvas. There are four types of elements: text, images, buttons, and empty nodes. We call these UI elements with certain functions widgets.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410111939776.png" alt="image-20250410111939776" style="zoom:40%;"  />

Select the button in the lower left corner, and a basic button will appear in the center of the canvas.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410113617807.png" alt="image-20250410113617807" style="zoom: 40%;" />

The right panel shows various settings for the button. In this case, we don't need to adjust the settings for the button. On the left side is a panel for viewing all UI widget levels, which currently only contains the button we just added.

## Adding button text

Next, we will add a text widget. When you add the text widget, you might notice that it appears either below or at the same level as the button.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410115458438.png" alt="image-20250410115458438" style="zoom:50%;"/>

The text widget we added may be below the button's level or at the same level as the button. This is because when you click in the lower-left area to add a widget, if you have selected a button, the new widget will be added below the button's level; if no widget is selected, the new widget will be created at the top level.

Changes made to a parent widget will also affect its child widgets, such as moving, scaling, deleting, or closing the display. However, adjustments to child widgets are not synchronized to the parent.

We need the text to be a child of the button, so we need to select the button before creating it.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410120434466.png" alt="image-20250410120434466" style="zoom:50%;" />

Next, select the text and modify the text on the right, for example, "Press me":

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410120839364.png" alt="image-20250410120839364" style="zoom:50%;"/>

> What if the widgets are stacked on top of each other and I can't select them? Click a few times to select the widgets in the current position in sequence.
> You can also select the widget you want directly via the left-hand hierarchical menu.

## Accessibility

The UI editor has a very useful accessibility feature in the bottom right corner:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410121054381.png" alt="image-20250410121054381" style="zoom:50%;"/>

On the right are the "Undo" and "Redo" options. If you make a mistake, these two functions can quickly get you back on track.

Clicking the left button displays the default UI on the canvas for reference, which can be used to help you adjust the custom UI widgets.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410121256871.png" alt="image-20250410121256871" style="zoom:50%;"/>

Let's use this function to place the newly created button below the weapon bar:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410121336163.png" alt="image-20250410121336163" style="zoom:50%;"/>

## Script editor

The button has been created, but the "press to make a sound" behavior needs custom logic. At this time, we need to go back to the previous page and select New Script to help us implement this logic.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410121610013.png" alt="image-20250410121610013" style="zoom:40%;"/>

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410121839989.png" alt="image-20250410121839989" style="zoom:40%;"/>

Drag "When pressing button" into the canvas:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410122101008.png" alt="image-20250410122101008" style="zoom:50%;" />

Remember what we need to do? We need the player to hear an audio effect when they press the button. Look for "Create Sound Effect" in the left-hand menu:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410122404756.png" alt="image-20250410122404756" style="zoom:50%;" />

![image-20250410122419492](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410122419492.png)

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410122430819.png" alt="image-20250410122430819" style="zoom:67%;"/>

We found that the "Create sound effect" block needs some necessary parameters to run, which are in order:

1. For which player to play the sound effect
2. What sound effect to play
3. Whether to play the sound effect in a loop
4. Whether to start playing the sound effect immediately after it is created


You need:

1. Drag the triggering player from the red event block to the first parameter

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410142504114.png" alt="image-20250410142504114" style="zoom: 80%;" />

2. Click on the second parameter and select the sound effect type in the recommendation bar that pops up on the left. After entering the sound effect type, click on the sound effect type on the Create Sound Effect block, and the sound effect selection UI will appear.Select a sound effect you like — for example, “Reaction” from the UI widget sound effect category.


<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410142900404.png" alt="image-20250410142900404" style="zoom:50%;"/>

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410143243908.png" alt="image-20250410143243908" style="zoom:80%;" />

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410143357531.png" alt="image-20250410143357531" style="zoom:50%;"/>

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410143551695.png" alt="image-20250410143551695" style="zoom: 80%;" />

3. Click on the loop type parameter, select the loop type on the left, and then select Play once. Imagine if you played a looping sound effect every time you clicked a button.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410143825362.png" alt="image-20250410143825362" style="zoom: 50%;" />

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410143902325.png" alt="image-20250410143902325" style="zoom: 67%;" />

4. Select True for the Autoplay parameter

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410143934246.png" alt="image-20250410143934246" style="zoom: 67%;" />

So far, we have created a custom UI, and now we are just one step away from the final step: how to open this custom UI.

## Opening and closing the custom UI

Although the custom UI has been created, we need to open and close it at the right time.

First go to the global script editor:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410144339832.png" alt="image-20250410144339832" style="zoom:80%;" />

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410144354378.png" alt="image-20250410144354378" style="zoom:50%;" />

Select "When the player joins" in the event category

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410144512998.png" alt="image-20250410144512998" style="zoom:50%;" />

In the game category, select "Create custom UI"

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410144612637.png" alt="image-20250410144612637" style="zoom:50%;" />

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410144622733.png" alt="image-20250410144622733" style="zoom:67%;" />

Like the script for the UI itself, this block script for creating custom UIs also needs some parameters to run.

1. For which player to open the custom UI
2. Which custom UI you want to open


You need:

1. Drag the player from the event into the first parameter:


<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410144805756.png" alt="image-20250410144805756" style="zoom:67%;" />

2. If you have multiple custom UIs, select the one we just created:


<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410144818986.png" alt="image-20250410144818986" style="zoom:67%;" />

Next, select the game category's waiting block

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410145006578.png" alt="image-20250410145006578" style="zoom:50%;" />

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410145029538.png" alt="image-20250410145029538" style="zoom: 67%;" />

The waiting time is set to 30,000 milliseconds, which is 30 seconds

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410145120619.png" alt="image-20250410145120619" style="zoom:67%;" />



In the physical category, select destroy blocks

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410145311612.png" alt="image-20250410145311612" style="zoom:50%;" />

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410145327754.png" alt="image-20250410145327754" style="zoom:67%;" />

Drag the entity returned in the Create custom UI block into this destroy block

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410145419057.png" alt="image-20250410145419057" style="zoom:50%;" />

And that's it!

## Effect

We have now created a button that makes a sound when clicked, and the logic to control whether it is switched on or off.

It will be created when the player joins and destroyed 30 seconds after creation.

Let's click on the debug to see the effect.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410145535032.png" alt="image-20250410145535032" style="zoom:50%;" />

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410145547072.png" alt="image-20250410145547072" style="zoom:50%;" />

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/010_CustomUI_New/image-20250410145616858.png" alt="image-20250410145616858" style="zoom:50%;" />

> Note: If you select loop playback for the sound effect or the duration of each playback is very long, clicking this button repeatedly will cause the sound effects to be played one after the other, causing them to overlap or play in quick succession.
