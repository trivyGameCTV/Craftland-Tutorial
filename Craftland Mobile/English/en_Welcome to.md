# Welcome to Craftland Studio

From simple changes like adjusting the number of players in a match to making players' heads bigger, or even introducing entirely new gameplay mechanics, Craftland has been enriched with a significant number of custom game maps created by its creative players.

![image-20250424161148051](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/013_Overview/image-20250424161148051.png)

In this series of tutorials, you will learn how to create an interesting Craftland map.

Before you start, you should know that you don't need to understand all the features and principles of Craftland to make the map you want.

If you just want to build your own scene level or modify some gameplay settings, you can customize existing templates to meet your needs. We recommend that you read the following:

## Basic Tutorial Navigation

1. [Create and publish a map](./3-40/)
2. [Basic scene editing](./3-41/)
3. [Set game parameters](./3-42/) 

If you have further needs, such as using various functional objects to build more complex levels, customizing game logic, or adjusting the UI, then you are welcome to start learning more from the following content:

## Advanced Tutorial Navigation

1. [Commonly Used Functional Objects](./3-44/)
2. [Block Scripts](./3-48/) 
3. [Customize UI](./3-49/)

In addition, you may have heard some terms used in game development, such as level, scene, and entity. In Craftland, their meanings are similar to those in other game development software. However, Craftland also has some relatively unique terms. Understanding the meanings of these terms in advance will help you get started with Craftland map editing.

## Common Terms

| Term | Explanation | Image |
| -------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Map | In Craftland, games are hosted on maps, and each map is equivalent to a brand-new game. | ![MAP](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/013_Overview/05.jpg) |
| Scene | A scene contains all the elements under it, including game objects, skyboxes, cameras, UI, and all other game elements. In Craftland, you cannot switch scenes. You can only edit the game in the main scene, which means that the concept of the current scene is almost the same as the map. | ![Scene](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/013_Overview/07.jpg) |
| Level Objects | Level objects are all visible and interactive objects in a scene. A basic cube, a zombie, a vending machine, and a building are all level objects, and they have different roles in the level depending on their functions. | ![Objects](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/013_Overview/06.jpg) |
| Skybox | The game's 3D space is a relatively limited area, and the skybox serves as the background at the boundaries of this space. In Craftland, skyboxes also integrate lighting and fog effects, but you can only modify them through block scripts. | ![skybox](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/013_Overview/09.jpg) |
| Templates | Templates are a series of preset game settings, level objects, and so on. Templates are determined when you create a map, and they provide you with a better starting point than a blank scene. You can perform advanced editing based on the content provided by the template. | ![Templete](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/013_Overview/10.jpg) |
| Gameplay Settings | Gameplay settings allow you to adjust how the map is played, enabling you to define the core gameplay logic of the map. | ![gameplay setting](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/013_Overview/04.jpg) |
| Block Scripts | Block scripts are a type of visual programming script that can help you customize game logic and realize all kinds of creative ideas. | ![block scripts](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/013_Overview/01.jpg) |
| Blocks | Blocks are the basic building blocks of block scripts. A block represents a function, an event, or a piece of data. By combining blocks, you can achieve the logic you want. | ![blocks](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/013_Overview/02.jpg) |
| Script variables | Script variables are custom variables used to specify scripts. You can use custom variables to store personalized data for block script editing. | ![scripts para](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/013_Overview/08.jpg) |
| Entity | An entity is a broad concept that refers to any concrete or abstract concept in a game that can be instantiated. Examples include abstract concepts such as the game as a whole, rounds, and phases, as well as concrete concepts such as NPCs, vehicles, weapons, and other objects that can be seen. | ![image-20250425145239636](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/013_Overview/image-20250425145239636.png) |
| Properties | Entities have data called properties, which represent certain functions of the entity, such as switches and numerical values. For vehicles, horsepower and braking ability are properties of the vehicle entity. | ![Entity property](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/013_Overview/03.jpeg) |
| UI | UI is the medium through which players interact with the game. It is typically 2D and always displayed at the front of the game screen. Players can issue commands to the character they control by clicking buttons on the screen, or obtain useful information from match information and images displayed on the screen. | ![UI](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/013_Overview/11.jpg) |
| Widgets | Widgets are functional elements in the UI. In Craftland, we provide four widgets for customizing the UI: text, images, buttons, and empty widgets. | ![widget](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLtutorial/013_Overview/12.jpg) |
