# Avatar

# Appearance groups

Appearance groups are a concept for categorizing and managing the appearance meshes in a model.

![image-20241011143752628](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/26-Avatar/image-20241011143752628.png)

Add models with rigs as prefabs to access appearance editing:

![image-20241011144305585](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/26-Avatar/image-20241011144305585.png)

In the appearance group settings, you can set the appearance group to be one of a set of mutually exclusive appearances:

![image-20241011153210375](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/26-Avatar/image-20241011153210375.png)

All appearance groups that are set to the same mutually exclusive group are mutually exclusive and will not be displayed at the same time. This is handy for things like switching skins.

Within an appearance group are parts in meshes, how many meshes a model has is determined when the model is created.

![image-20241011153357270](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/26-Avatar/image-20241011153357270.png)

In the mesh settings, you can modify its binding point to the rig, the binding method; modify the rendering method and other operations:

![image-20241011153506396](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/26-Avatar/image-20241011153506396.png)

You can add a new mesh to a model by creating a new appearance:

![image-20241011163120786](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/26-Avatar/image-20241011163120786.png)

You can select an existing mesh resource within the project:

![image-20241011163249400](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/26-Avatar/image-20241011163249400.png)

If the added mesh is not a match to the original rig, select the binding method to connect:

![image-20241011163331947](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/26-Avatar/image-20241011163331947.png)

![image-20241011163417536](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/26-Avatar/image-20241011163417536.png)

# Using Appearance Groups

Scripts can be used to control the appearance of a given appearance group or to toggle the appearance group.

![image-20241011144706308](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/26-Avatar/image-20241011144706308.png)

> Switching appearance groups hides the original appearance group and shows the new one.

There are two meshes in the alien pet, the alien body and the flying saucer:

![image-20241011153600498](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/26-Avatar/image-20241011153600498.png)

We create a new appearance group that can separate the two:

![image-20241011153629170](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/26-Avatar/image-20241011153629170.png)

By default, we make the flying saucer hidden and show the saucer after the start of the game round:

![image-20241011153714874](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/26-Avatar/image-20241011153714874.png)

![image-20241011153746239](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/26-Avatar/image-20241011153746239.png)

> Global Scripts

In the game preparation phase, you can see that there are only aliens:

![image-20241011153918797](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/26-Avatar/image-20241011153918797.png)

After the round starts, the flying saucer is shown:

![image-20241011153933339](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/26-Avatar/image-20241011153933339.png)

Flexible use of scripts to control the appearance group can be accomplished while switching the display of parts, changing Skins, transforming, etc. under specific conditions.
