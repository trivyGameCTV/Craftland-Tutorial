# Animation Controller

Introducing Craftland Studio PC's brand new animation controller system.

# Features

Craftland Studio PC's animation controller now supports:

1. Preview animations
2. Manage animation clips playback and transitions in a track format
3. Manage groups of animation clips using states
4. Split rig parts to play only specific rig animations within an animation clip
5. Add keyframes and broadcast events at keyframes to implement script logic.

# Resource Preparation

To use the Animation Controller, you need to prepare:

1. A model
2. Animation resources matching the model

![image-20250821150239191](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/image-20250821150239191.png) 

The editor already includes built-in FreeFire characters and their corresponding Animation:

![image-20250821150636553](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/image-20250821150636553.png) 


![image-20250821150721434](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/image-20250821150721434.png) 

# Entry

To use the Animation controller, you need to create an Animation Controller file:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/image-20250821153246045.png" alt="image-20250821153246045" style="zoom: 80%;" /> 


Double-click to open the newly created animation controller file, and the Animation editing UI will open:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/image-20250821153401651.png" alt="image-20250821153401651" style="zoom:67%;" />



# Using the model

Click on the model bar or drag the model into the interface to preview the model that will play the Animation.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/image-20250821154505261.png" alt="image-20250821154505261" style="zoom:75%;" /> 


If the model has an Appearance component and suitable rigs and appearances, the preview window will display the model. You can zoom in or out using the mouse wheel, drag the camera using the middle mouse button, or hold down the right mouse button to rotate the camera—just like in the Scene editor.

![image-20250821155656866](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/image-20250821155656866.png) 


![image-20250821154710020](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/image-20250821154710020.png) 


If you want to use the default FreeFire character or pet appearance, you can find suitable appearances in the Library/FFUMA directory under the project directory. These appearances will also be displayed in the selector.

![image-20250825102329060](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/image-20250825102329060.png) 


# Add animation clips

Drag an animation from the project onto the track to add an animation clip. If you don't know which animations are available in the project, use the Add Animation feature to browse all animations. However, you always need to ensure that the animation matches the model. Typically, incompatible animations will not play, but sometimes animations may behave strangely: for example, certain parts of the model may be abnormally stretched or compressed.

![image-20250821173417294](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/image-20250821173417294.png) 


![image-20250821173434033](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/image-20250821173434033.png) 


![image-20250821173458028](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/image-20250821173458028.png) 

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/image-20250821173511604.png" alt="image-20250821173511604" style="zoom:67%;" /> 


## Animation Clip Settings

In Project, you can only view animation clip information. However, after dragging an animation into the track, you can edit the parameters for the current track in the inspector panel.

![image-20250825102727878](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/image-20250825102727878.png)


![image-20250821175211907](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/image-20250821175211907.png) 


- **Clip**: This clip uses the specified animation. You can manually change the animation clip.
- **Playback Speed**: The speed at which the animation plays. 1 is the default speed.
- **Wrap Mode**: After extending the animation clip, this option determines how the extended portion loops.

  - Hold: Maintains the animation pose of the last frame.
  - Loop: Loop the Animation clip in the extended portion.
  - Forever Loop: Continuously loop the Animation clip after it ends, rendering subsequent clips ineffective.
  - None: No action; hard cut back to the default pose.
- **Post-Extrapolate**: How to handle the transition between the current clip and the next clip.

  - None: No action; hard cut back to the default pose.
  - Maintain: Maintain the animation pose of the last frame
  - Loop: Loop the animation segment in the section between two segments
  - When the backward push setting is set to Maintain or Loop, it can be clearly seen at the end of the segment:![image-20250825103745027](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/image-20250825103745027.png)![image-20250825103653150](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/image-20250825103653150.png)


- **Blend Fade Length**: The duration of the transition animation when switching to this animation clip.

  - During the Blend In Duration, the animation system automatically reduces the weight of the previous animation and increases the weight of this animation clip until the fade-in time ends.

    - Play this Animation clip completely when the fade-in time ends
    - If this parameter is set to 0, the transition will occur immediately, which may look strange, but sometimes a hard cut is needed for immediate Animation, such as firing a gun or dodging.

  - When there is a transition from Animation A to Animation B in the track, the fade-in duration for Animation B is automatically set based on the overlap duration of the two clips in the track:

    - ![image-20250825105117055](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/image-20250825105117055.png) 

  - Even if there are no directly connected animation clips on the track, when using the animation controller in practice, there will be cases where the animation “switches to this clip.” For example, when switching from the ‘sitting’ state to the “running” state, if the running state uses only one animation clip, it will transition smoothly from sitting to running based on this parameter. For details on states, please refer to the section below.

- **Start time**: The time at which this animation clip begins playing on the track
- **End time**: Equal to the start time plus the playback duration, cannot be edited, and is automatically determined based on the start time and playback duration
- **Playback length**: The length of the clip's playback. When longer than the resource length, the loop mode parameter takes effect; when shorter than the resource length, the animation is truncated from the end
- **Resource length**: The actual length of the animation resource, cannot be edited, and is determined by the animation resource itself.

## *Stretching and compressing animation clips

![image-20250822155932985](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/image-20250822155932985.png) 

You can change the length of an animation segment by dragging it. If the dragged length is shorter than the segment's length, the animation will be truncated. If the dragged length is longer than the animation segment, an additional segment length will be added after the default animation plays. The handling of this additional segment depends on the Wrap mode set in the segment's Inspector.

## Animation Clip Merging

As mentioned earlier when discussing blend-in duration, when animation clip A transitions to animation clip B, the transition occurs within the blend-in duration of animation clip B.

Now we have two animations: 1 is both hands lifting something, and 2 is one hand:

1:

![bothhands](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/bothhands.gif) 

2:

![singlehand](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/singlehand.gif) 

If we simply concatenate the two, it appears as though the single-hand animation begins immediately after the double-hand animation ends:

![connect](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/connect.gif) 

If we use blending, it appears as though the single-hand animation begins before the double-hand animation has completely ended:

![IK](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/IK.gif) 

As you can see, animation 2 has already started before animation 1 has finished, and the weight gradually shifts toward animation 2, with animation 2 playing completely by the end of the blending.

By using animation blending, you can make the transition between animations more natural.

If we simply concatenate the two, it appears as though the single-hand animation begins immediately after the double-hand animation ends:![connect](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/connect.gif)If we use blending, it appears as though the single-hand animation begins before the double-hand animation has completely ended:![IK](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/IK.gif)As you can see, animation 2 has already started before animation 1 has finished, and the weight gradually shifts toward animation 2. By the time the blending ends, animation 2 is fully played.Animation blending can make Animation transitions more natural.> If you set a fade-in time before the first frame of a state, automatic blending will be applied when transitioning to this state from other states.



# Animation Preview



![image-20250825164106492](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/image-20250825164106492.png) 

When previewing the animation effects, you can make good use of the panel operations and information.

The panel allows you to perform the following operations:

- Jump to the beginning, jump to the end

- Next frame, previous frame

- Pause, play

Additionally, the right side displays the frame number and time starting from the animation segment. Generally, animations play at a fixed rate of 30 frames per second.

# Add keyframes

Click on any point in the track to add a keyframe.



![image-20250825164332074](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/image-20250825164332074.png) 


You can also delete this keyframe by selecting it.

Keyframes are manually marked key points in the Animation. You can also add events to them to serve the script.

## Events

Select Add Animation Event in the inspector panel of the keyframe to broadcast a custom event at the specified frame number in the current Animation:

![image-20250825164543585](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/image-20250825164543585.png) 


![image-20250825164612242](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/image-20250825164612242.png) 

# Body Part Animation

When you need to play an animation on only part of the body, such as different animations for the upper and lower body, you need to use body part animation.

First, you need to create a rig profile:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/image-20250825173052697.png" alt="image-20250825173052697" style="zoom: 67%;" /> 


The rig configuration file can specify a portion of the rig's bone nodes, which we refer to as body parts.

After selecting a specific rig, you can see all the nodes in the rig.

![image-20250825173414360](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/image-20250825173414360.png) 


![image-20250825173945687](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/image-20250825173945687.png) 


By creating body parts, you can specify a specific set of bone nodes to play Animation, thereby achieving the requirement of playing Animation for specific body parts only. For example, we will separate the upper and lower body rigs:

![image-20250826150723496](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/image-20250826150723496.png) 


Override mode means that when multiple Animations exist for the same rig node, the Animation with the highest priority will override the others. In contrast, Additive mode attempts to blend Animations with lower priorities.

![image-20250826151150811](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/image-20250826151150811.png) 


However, the blending mode has higher requirements for Animation resources and adjustments, and even minor issues can result in poor performance. It is recommended to use the Override mode first.

> *Priority: In rig parts, tracks, and states, the lower the priority, the higher the priority. In the above figure, the priority of the Top rig part is higher than that of the Bottom rig part.

Drag the configured rig configuration file into the edit panel, and you will find the newly configured rig parts in the track dropdown menu:

![image-20250826153443435](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/image-20250826153443435.png) 


Each track corresponds to a rig part, and the Base Track is selected by default for all rig parts.

Next, let's use two different Animations to see how it works.

We will take two Animation segments:

Squatting and walking:
![kellyWalking](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/kellyWalking.gif)

Walking with a gun:

![kellyGunWalking](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/kellyGunWalking.gif) 

As you can see, the stride is larger when walking with a gun. Now let's take the upper body animation from squatting and walking and the lower body animation from walking with a gun:

![image-20250826153233979](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/image-20250826153233979.png) 


The animation for walking with a gun is shorter, so let's extend the animation for walking with a gun to align the two, and set the loop mode to “loop.”

![image-20250826153329851](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/image-20250826153329851.png) 

You can see that the Animation has changed to:

![kellyIKWalking](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/kellyIKWalking-1756193932693-4.gif) 

The upper body animation for crouching walk and the lower body animation for gun-holding walk are used simultaneously.

> If some rigs are not assigned any animation when using rig part animations, they will use the IDLE animation.


# State

All of these tracks and animation clips combined form a state, which can be seen in the list of current animation controllers on the left side of the panel:

![image-20250826155139522](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/image-20250826155139522.png) 


When using the animation controller in practice, operations are performed on states. Playing a state means playing all its tracks starting from frame 0.

Therefore, when editing the animation controller, you can plan how many states you want to have and edit the appropriate combination of animation clips for each state. For example, the states of a small animal are: Idle, Moving, Eating, Alert, and Running away.

The IDLE state must exist; it is the default state of an Animation controller, and the IDLE state must be set to loop playback.

# block script

![image-20250826155520392](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/image-20250826155520392.png) 


Using scripts, you can play or stop a specified state for an entity with an animation controller attached, or dynamically modify the weight of body part animation weights.

#  How to use

Drag a suitable model into the Scene:

![image-20250826160815206](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/image-20250826160815206.png) 

Add the Animation Controller Attachable component to it:

![image-20250826161847812](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/image-20250826161847812.png) 

Then add the created Animation controller:

![image-20250826161906877](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/image-20250826161906877.png) 

Now the model will default to playing the IDLE state. Use the script to switch the playback state on the actual device when appropriate:

![image-20250826161958975](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/image-20250826161958975.png) 

>  When the player fires, change the playback state of miniKelly

![PPT3](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/NewAC/PPT3.gif)
