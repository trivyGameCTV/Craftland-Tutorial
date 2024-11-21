# AVATAR-User Manual

# Appearance Group

The Appearance Group is a concept for categorizing and managing the appearance meshes in a model.

![image-20241011143752628](./img/image-20241011143752628.png)

Add a model with a skeleton as a prefab to enter appearance editing:

![image-20241011144305585](./img/image-20241011144305585.png)

In the Appearance Group settings, you can set this group as part of a mutually exclusive set:

![image-20241011153210375](./img/image-20241011153210375.png)

Appearance groups set in the same exclusive group will not display simultaneously, facilitating operations like skin switching.

Within an appearance group, parts are based on meshes. The number of meshes a model has is determined during its creation.

![image-20241011153357270](./img/image-20241011153357270.png)

In the mesh settings, you can modify its binding points and methods with the skeleton, as well as adjust rendering methods:

![image-20241011153506396](./img/image-20241011153506396.png)

You can add new meshes to the model by creating a new appearance:

![image-20241011163120786](./img/image-20241011163120786.png)

You can select existing mesh resources within the project:

![image-20241011163249400](./img/image-20241011163249400.png)

If the new mesh does not match the original skeleton, choose "Connect" as the binding method:

![image-20241011163331947](./img/image-20241011163331947.png)

![image-20241011163417536](./img/image-20241011163417536.png)

# Using Appearance Groups

Scripts can control the visibility or switch of specified appearance groups.

![image-20241011144706308](./img/image-20241011144706308.png)

> Switching appearance groups will hide the original group and display the new one.

The alien pet has two meshes: the alien body and the UFO:

![image-20241011153600498](./img/image-20241011153600498.png)

We can create a new appearance group to separate them:

![image-20241011153629170](./img/image-20241011153629170.png)

By default, we hide the UFO and display it after the game round starts:

![image-20241011153714874](./img/image-20241011153714874.png)

![image-20241011153746239](./img/image-20241011153746239.png)

> Global Script

During the game preparation phase, only the alien is visible:

![image-20241011153918797](./img/image-20241011153918797.png)

After the round starts, the UFO appears:

![image-20241011153933339](./img/image-20241011153933339.png)

By flexibly using scripts to control appearance groups, you can switch part displays, change skins, transform, and more under specific conditions.
