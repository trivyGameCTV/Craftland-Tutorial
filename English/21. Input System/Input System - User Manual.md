# Input System

The Input System is a default module that can be used to remap game operations by modifying the Input System configuration.

![image-21-1](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/21-InputSystem/image-21-1.png) 

# In-game generic buttons 

The game comes with a set of generic in-game buttons. This default UI is automatically created and can be used to manipulate the player.

![image-21-2](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/21-InputSystem/image-21-2.png)

You can control the appearance of these buttons via scripts:

![image-21-3](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/21-InputSystem/image-21-3.png)

# Customize Input System

An input can be added or removed from the input system:

![image-21-4](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/21-InputSystem/image-21-4.png)

For an input, you can select the input type as keyboard, mouse or UI file.

## Keyboard and Mouse

Keyboard and mouse inputs are currently only available for PC Debug.

## Custom UI

For custom maps, in-game actions are mainly remapped through the custom UI.

![image-21-5](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/21-InputSystem/image-21-5.png)

In the input system, you can bind an input to a control on the custom UI so that you can use the custom UI's widgets to implement the action. This will help you make unique game modes or other Scenes where you want to change player inputs.

## How to configure custom inputs

Using the Custom UI as an example, you will need to prepare the Custom UI for custom inputs first.

![image-21-6](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/21-InputSystem/image-21-6.png)

Let's make a UI with just one button under this custom UI, with the plan that this button will have the effect of making the player advance.

![image-21-7](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/21-InputSystem/image-21-7.png)

Add a new input to the input system module.

![image-21-8](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/21-InputSystem/image-21-8.png)

Select the mapping action as Forward, the type as UI File, select the custom UI and buttons created earlier, and the input gesture as Press and Hold.

![image-21-9](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/21-InputSystem/image-21-9.png)

Create a custom UI for the player, this block script is created on the global module.

![image-21-10](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/21-InputSystem/image-21-10.png)

Run the game and find that this button's functionality is in effect.

![image-21-11](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/21-InputSystem/image-21-11.png)
