# Important Concepts

Introduce some important concepts that exist in the UGC editor and provide a detailed explanation of these important concepts

## Entities and instances

Entities are one of the important concepts in UGC. Generally speaking, entities refer to specific entities, which are expressed as the abbreviation of logical entities, such as a certain player or a trigger.

An entity is a kind of concrete/abstract concept or collection of concepts.

An entity has properties, and modifications to properties will affect the instances created by the entity.

The concept of entity is very broad, and most of the concepts in this game exist in entity form.

Taking "player" as an example, the "player" entity refers to the concrete concept of the player, and the health value is the attribute of the player entity. The specific players A and B in a certain game are two instances of the player entity.

Players A and B both have the health value attributes of the player entity. The difference is that Player A has 150 health points, while Player B has 200 health points.

Health values ​​are attributes of entities, and health values ​​of 150 and 200 are attributes of instances.

In addition to entities that can be concreted such as players, vehicles, and weapons, there are also some abstract entities that cannot be directly concreted, such as global and game flow.

Abstract entities also have properties and instances are created.

For example, the game process is an abstract entity, and the duration of the preparation stage is an attribute. Assuming that two games are played, each game will create an instance of the game process.

The first game preparation phase lasts 5 seconds, and the second game preparation phase lasts 10 seconds.

The preparation phase duration of 5 seconds and 10 seconds is the instance attribute of the game flow entity.

In most cases, the entity mentioned in the game actually refers to an instance of an entity, such as deleting an entity, obtaining an entity's properties, and modifying an entity's properties.

In fact, the objects that are operated are instances of entities.

In the following and other articles, it is not necessary to no longer specifically emphasize the distinction between entity instances and entities.

### The life cycle of an entity

As mentioned above, the life cycle object is actually an instance of an entity.

Life cycle means that entities always go through specific processes from creation to destruction. You can achieve design goals by mastering the life cycle of entities that need to be edited and then operating entities at specific points in time.

All entities use Awake as the beginning of their life and use Destroy to mark the end of their life.

Most entities will be activated by Enable after Awake and will be activated using Disable before destruction.

> There may be entities that skip the enable or disable stage, but wake and destroy always exist.

**General Process**

![image-20241014171853741](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/03-ImportantConcepts/image-20241014171853741.png)

## Components and Properties Panels

In the editor item list, their properties are controlled by the components that make up the object, such as the position component of the object, the appearance component of the object, the material component of the object, and the name component of the object

From a functional point of view, it is like a "gate tool".

For example, in the appearance component of an object, the appearance of an object is changed through buttons and material options. By reusing these components, we can change the properties of a certain object very simply and conveniently to avoid repeated addition of code.

![image-20241113150847792](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/3_ImportantConcepts/image-20241113150847792.png)

In CraftLand, we cannot directly add or modify components, but we can change the parameters and options of some components of an object through the property panel to change the parameters and options of some components of an object through the property panel.

First, we can create an object and select it, and then we can see the property panel of the item

​ ![image-20241113160229762](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/3_ImportantConcepts/image-20241113160229762.png)

In the properties panel, we can move the position of the object, change the size of the object, and rotate the angle of the object. These are all changed through the object's 'Transform' component

There are 6 options in the properties panel, namely:

![image-20241106174706837](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/3_ImportantConcepts/image-20241106174706837-1731491487358-6.png)

| Name | Illustration | Description |
| ---- | ----------------------------------------------------------- | ------------------------------------------------------------ |
| Properties | ![image-20241106175250972](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/3_ImportantConcepts/image-20241106175250972.png) | Some attribute settings of objects can be changed<br /><img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/3_ImportantConcepts/image-20241106181010058.png" alt="image-20241106181010058" style="zoom:22%;" /> |
| Move | ![image-20241106175253495](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/3_ImportantConcepts/image-20241106175253495.png) | Can move object coordinates<br /><img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/3_ImportantConcepts/image-20241106180814579.png" alt="image-20241106180814579" style="zoom:25%;" /> |
| Zoom | ![image-20241106175256698](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/3_ImportantConcepts/image-20241106175256698.png) | You can modify object scaling to change the size of the object<br /><img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/3_ImportantConcepts/image-20241106180832478.png" alt="image-20241106180832478" style="zoom:28%;" /> |
| Rotate | ![image-20241106175300431](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/3_ImportantConcepts/image-20241106175300431.png) | You can rotate an object to change the orientation of an object<br /><img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/3_ImportantConcepts/image-20241106180846336.png" alt="image-20241106180846336" style="zoom:25%;" /> |
| Delete | ![image-20241106175303257](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/3_ImportantConcepts/image-20241106175303257.png) | You can click to delete objects<br /><img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/3_ImportantConcepts/image-20241106181055895.png" alt="image-20241106181055895" style="zoom:25%;" /> |
| Copy | ![image-20241106175306277](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/3_ImportantConcepts/image-20241106175306277.png) | Click to copy multiple identical current objects<br /><img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/3_ImportantConcepts/image-20241106180928598.png" alt="image-20241106180928598" style="zoom:25%;" /> |



Click [Properties] to view the changing component properties of different objects

Here we use a square object as a demonstration. First, we create a square and click [Properties] to view the square properties

![SeaTalk_IMG_20241113_171445](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/3_ImportantConcepts/SeaTalk_IMG_20241113_171445.jpg)

In Properties, we can find that according to the components held by the block, we can change the appearance and material of the block, and we can try to modify it.



Example:

By changing the material and size of the object, we can use different polygons to build a lot of compositions

For example, here we used multiple circles and cylinders to build a fountain

![SeaTalk_IMG_20241113_174525](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/3_ImportantConcepts/SeaTalk_IMG_20241113_174525.jpg)
