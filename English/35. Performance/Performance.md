# Performance

# Introduction

You may have heard of the Timeline System. Similar to the Timeline System, the Performance System provides a set of **visual content sequencing tools**. It allows creators to arrange elements like animations, sound effects, camera transitions, and event triggers on a single timeline—just like editing a video—to produce content commonly used in story sequences, level transitions, and cutscenes.

![kellyrun](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/kellyrun.gif) 

# Basic Concepts

## Timeline

As the name suggests, the Timeline is an editing tool centered around chronological order. You'll see a ruler marked with time intervals. The tracks, clips, and other elements introduced below are arranged along this time scale, determining their playback sequence.

![image-20250916173640541](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250916173640541.png) 

## Playhead

The playhead is the time indicator on the timeline, used to mark and control the current preview or operation point.

![image-20250916191828794](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250916191828794.png) 


Drag the playhead to preview all tracks in real time. It also serves as a powerful tool for locating specific frames or moments.

## Tracks

![image-20250916174521004](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250916174521004.png) 

Tracks serve as containers for content, holding elements and their temporal variations. The performance system provides several distinct track types, each designed to carry specific entity types and process them accordingly.

Tracks feature a parent-child hierarchy. For example, an actor track holding an NPC may contain a transform component child track. Child tracks typically hold properties of the parent track's entity or content strongly related to it.

> Tracks currently only support entities already placed in the scene. If an entity is destroyed during a performance, the corresponding track content will fail to activate. Therefore, ensure relevant entities persist throughout the performance.

### Actor Track

The Actor Track can host most entities, such as basic blocks, NPCs, monsters, vehicles, and more. By adding sub-tracks to the Actor Track, you can create distinct tracks for manipulating this entity. 

### Animation Track

Animation Tracks can only exist as child tracks and require the parent track entity to have the “Animation Controller Attachable” component. Animation Tracks allow the parent track entity to play animation clips stored on the track.

### AlongPath Track

AlongPath Tracks can only exist as child tracks and require the parent track entity to have a Transform component. AlongPath Tracks combine custom curve paths (Custom Curve Path) to move the parent track entity along a specified route.

### SignalTrack

Only event frames can be added to a SignalTrack to send custom event signals. See below for details on using events.

### SkyboxTrack

Only one Skybox track can exist per performance file, and Skybox objects cannot be added to the Actor track. Only Skybox frames can be added to the Skybox track to adjust Skybox parameters.

### Camera Switch Track

Only custom camera clips can be added to the Camera Switch track. When the playhead points to a camera clip, the performance uses that camera; when pointing to an empty track, the player camera is used.

Cameras can be added to actor tracks as actors to adjust camera parameters.

### Audio Track

Audio tracks can add audio clips to provide sound for the performance.

## Clip

**Clips are the fundamental units on tracks**, representing the state of content during a specific time period on the timeline. Depending on the type, a clip's inspector displays different properties or settings.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250916192708566.png" alt="image-20250916192708566" style="zoom:67%;" /> 


Generally, clips always have the following properties:

- Start time: The time at which the clip begins playing on the timeline
- End time: The time at which the clip finishes playing on the timeline. This time is automatically calculated based on the start time and duration and cannot be adjusted
- Duration: The total length of the clip's playback
- Resource duration: The length of the resource used by the clip. This field has different meanings depending on the clip type. For example, in an animation clip, it represents the length of the animation resource. In an AlongPath clip, it indicates the time required to traverse the path at the default speed of 1m/s.

### Animation Clip

![image-20250917200536649](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250917200536649.png) 

![image-20250917151234256](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250917151234256.png) 


Animation clips must be placed on animation tracks, with each clip containing one animation. The animation used must be rigged to the parent track entity's skeleton. Animation clips have the following special parameters:

- Clip: The animation resource to play
- Playback Speed: Animation playback rate. Default is 1. Values greater than 1 speed up playback; values less than 1 slow it down.
- Loop Mode: Within the track, a clip's duration may exceed the resource length. After the resource completes one playback, the following actions occur:
- None: No action; the parent track entity returns to its default pose
- Hold: Remains on the last frame of the animation resource until the clip ends
- Loop: Repeats the animation resource until the clip ends
- Loop Forever: Continues looping the animation even after the clip ends, typically used for persistent background elements (e.g., natural environments, looping effects)

### AlongPath Fragment

![image-20250917200453723](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250917200453723.png) 

![image-20250917162604854](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250917162604854.png) 


The AlongPath clip can only be added to an AlongPath track and must use a Custom Curve Path as its content. This clip represents the movement path of the parent track's entity during this time period. The AlongPath clip has the following special parameters:

- Path: Which custom curve path is being used
- Playback Speed: The speed multiplier for the entity's movement. Entities move at 1m/s by default in the AlongPath of the performance system. Adjusting this multiplier controls the entity's movement speed. Changes in movement speed also alter the resource length. Movement Speed * Resource Length = Path Length
- TangentFacing: Whether the entity maintains facing toward the path's forward direction while moving along it. When your path is curved, enabling this setting ensures the moving entity always faces forward along the path; disabling it lets the entity maintain its own orientation. Toggling this setting does not affect other operations that manipulate the entity's direction
- Type: Similar to backward extrapolation in animation clips, this determines how the moving entity is handled when the AlongPath clip length exceeds the resource length
- None: No processing; the object stops moving at the path endpoint.
- Loop: After completing one movement, the object restarts movement from the **start point** until the clip ends. This may cause the entity to teleport from the endpoint to the start point.
- Ping-pong: After completing one movement, the object reverses direction from the **end point** toward the **start point**. Upon reaching the start point, it moves back toward the end point, repeating this cycle until the clip ends.

### Camera Fragments

![image-20250917200311855](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250917200311855.png) 

Camera clips can only specify a particular camera to achieve camera switching.

Although camera parameters cannot be adjusted within the clip, the camera can be added as an actor to an actor track to modify its settings. See the relevant section in Advanced Applications.

### Audio Clip

![image-20250917200415730](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250917200415730.png) 

![image-20250917200652225](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250917200652225.png) 


Audio clips are similar to animation clips, with each audio clip containing a segment of audio. Audio clips have the following special parameters:

- Clip: The audio resource to play
- Playback Speed: The rate at which audio plays. Default is 1. Values greater than 1 speed up playback; values less than 1 slow down playback
- Loop: Handling when playback duration exceeds resource length:
- None: No action; audio stops after resource ends
- Loop: Repeats audio until clip ends
- Loop Forever: Continues looping even after clip ends



## Keyframes

![image-20250919114226813](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250919114226813.png) 


Keyframes are anchors on the timeline for a track, capturing the state of an entity or property at a specific moment. The performance system automatically interpolates property values between two keyframes, creating a smooth transition effect over time.

You can add keyframes in the following tracks:

1. Performer Track
2. Performer Track's Property Sub-Tracks
3. Event Track
4. Skybox Track

### Actor Track Keyframes

![image-20250919120921902](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250919120921902.png) 

Actor track keyframes mark moments when certain properties of the actor have keyframes. While you can create keyframes directly on the actor track, they serve no practical purpose if no property changes occur.

When a keyframe is selected, you can see the properties of the actor that can be adjusted in the performance system:

![image-20250919120956960](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250919120956960.png) 

When adjusting a property, the system automatically creates a sub-track for that property and places keyframes on it. For example, setting the block's visibility to False at 1 second:

![image-20250919121206923](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250919121206923.png)

This means the cube becomes invisible one second after the performance begins.

Note that the system only interpolates properties between keyframes. For example, when we raise the white cube's height by 1m at the 2-second mark, it actually maintains its original height until the 2-second point and then instantly rises by 1 meter:

![cube1](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/cube1.gif)

For smooth transitions, add a keyframe at the start of the performance. This enables automatic property interpolation:

![cube2](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/cube2.gif)

### Event Keyframes

Event keyframes are special keyframes that do not record any properties but instead trigger custom events at specific moments. When your performance reaches a certain point, you may want to execute additional game logic—using event keyframes is the best approach:

![image-20250919122418596](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250919122418596.png)


You can create custom events in advance or generate them when adding event keyframes. Custom events created at event frames can also be utilized in other game logic.

![image-20250919122547758](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250919122547758.png) 

### Skybox Keyframe

![image-20250919122629314](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250919122629314.png)


Skybox keyframes are a special type of keyframe that can only be created on skybox tracks and can only adjust specific properties of the skybox.

# First Use

Next, we'll use the example “Have Kelly run 50 meters along the X-axis in 5 seconds” to demonstrate the basic operations of the performance system.

## Creating a Performance File

You always need a performance file for editing. Create one by making a new folder within the assets directory.

![image-20250916171509613](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250916171509613.png) 


Double-click the performance file to enter the performance editor.

![image-20250916172016335](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250916172016335.png)

> Yes, The entire editor is now in performance editing mode.

## Basic Operations

First, we'll place a Kelly NPC in the scene.

![image-20250919143425340](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250919143425340.png)

### Adding a Track

In the Performance Editor panel, add an Actor Track. When adding an Actor Track, it will automatically detect objects in the scene that can serve as actors:

![image-20250919143750026](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250919143750026.png) 


We need Kelly to move and play the sprint animation, so theoretically we'd need to add both a Transform sub-track and an Animation sub-track. However, as mentioned earlier, modifying keyframes automatically creates corresponding property tracks. Therefore, only one Animation track is required here.

![image-20250919144053483](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250919144053483.png) 

For easier management, we can name the newly created animation track according to its actual function: Running Animation.

![image-20250919144732730](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250919144732730.png) 

### Adding Clips

Add a sprint action tailored for the female character to the animation track:

![image-20250919144851061](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250919144851061.png) 

We want Kelly to run for 5 seconds, so extend this clip to 5s. Additionally, Kelly should maintain the running motion continuously, so set the animation clip's extrapolation to “Loop”.

![image-20250919145033605](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250919145033605.png)

### Adding Keyframes

We want Kelly to start from her initial placement and move 50 meters along the X-axis. Therefore, we need to add two keyframes at 0 seconds and 5 seconds in the performance:

![image-20250919145135094](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250919145135094.png) 


![image-20250919145315721](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250919145315721.png) 


> When adding a keyframe by clicking on the timeline, it will be placed at the current playhead position. When adding via right-clicking on the timeline, it will be placed at the mouse cursor location. However, you can always adjust the keyframe position later.

Then select both keyframes one after another and set their X values to -25 and 25 respectively.

![image-20250919145752158](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250919145752158.png) 

> This shows the position at 5 seconds; the X value at 0 seconds is -25

![image-20250919150144071](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250919150144071.png) 


## Preview

Click to play. We can see Kelly correctly moved 50 meters, but the direction seems incorrect:

![ ](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/KellyRun-1758265443608-4.gif) 

We need Kelly facing the positive X-axis direction from the start of the performance. To achieve this, simply adjust the orientation at the 0-second keyframe or modify Kelly's base orientation:

![image-20250919150629503](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250919150629503.png) 

Play it again, and Kelly runs correctly:

![KellyRun2](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/KellyRun2.gif) 

Using an AlongPath track can also achieve the effect of having Kelly travel along a route. In fact, during complex performances, objects don't always move in straight lines, making the AlongPath track the superior choice.

# Common Operations

Next, we'll cover some common operations in the performance system editor.

## Basic Operations

On the control panel, you can perform basic operations on the current performance:

![image-20250919160144169](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250919160144169.png) 

These include:

- Move the playhead to the beginning/end of the performance
- Move the playhead forward/backward by one frame
- Play or pause the performance
- Move the playhead to a specified time

Additionally, you can zoom in or out on the track area using the Ctrl + scroll wheel shortcut for finer adjustments.

![image-20250919174519409](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250919174519409.png) 

## Cursor Preview

During local editing, you don't need to play the entire performance. Simply move the playhead, and the performance will instantly display the state at that moment.

![KellyRun3](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/KellyRun3.gif) 

## Recording

Recording is a convenient way to add keyframes. When you click the record button, the entire performance system enters recording mode. Tracks being recorded will be marked in dark red:

![image-20250919165555612](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250919165555612.png) 


Simply adjust the playhead to select the moment you wish to edit, then modify the object's state at that point in the scene to record a keyframe. All altered properties (position, rotation, scale, etc.) will be automatically captured in the newly created keyframe. Continue adjusting the playhead to modify subsequent states at different points in time.

By repeatedly adjusting the playhead and objects, you'll establish multiple keyframes across the timeline, forming a continuous performance—just like recording a video.

![cubemove1](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/cubemove1.gif) 

![cubemove2](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/cubemove2.gif) 

## Keyframe Parameter Adjustment

Typically, recording only allows for rough adjustments. For highly precise performance, fine-tune parameters directly on keyframes.

![image-20250919171705032](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250919171705032.png)

Select a keyframe to view its adjustable properties.

If the parent track is selected, all adjustable properties appear; if a specific property track is selected, only that property can be adjusted.

Adjustments made to the parent track automatically generate child tracks below, depending on the property type modified.

## Preview

![image-20250919172838584](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250919172838584.png) 


The preview button in the editing area indicates the scene is in performance editing mode when highlighted. To return to the scene editor for game editing, disable preview. Note the status indicator above the scene editor to distinguish between modes.

Though performances occur within game scenes and may appear similar, scene editing and performance editing are distinct systems.

For example, here we set the white cube's initial coordinates in the performance to be 2 meters higher than in the scene. Although they use the same object, the state of the white cube in the scene and in the performance are not consistent.

![cubemove3](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/cubemove3.gif) 

### Audience View

![image-20250919181801554](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250919181801554.png) 

When the Audience View is enabled, the preview window plays the performance from the actual audience perspective, allowing you to check its real-world presentation. When disabled, the preview window plays in scene editing mode, facilitating overall adjustments.

Note that event effects cannot be displayed in the preview. When using events, you'll need to use your imagination or check the effects during game debugging.

## Playback

You must use a **client-side** script to play the performance.

![image-20250929173212725](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250929173212725.png) 

At the appropriate moment (e.g., using a trigger), use the **client-side** script to play the specified performance file.

# Advanced Applications

## Multi-Track Collaboration

You may have noticed that when we made Kelly run, we didn't add an audio track. This means the actual performance playback will lack running sounds.

When editing performances, we need to use multi-track collaboration to achieve better performance results.

By adding camera and audio tracks, we can create a performance with additional effects:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250919181121516.png" alt="image-20250919181121516" style="zoom:67%;" /> 


![KELLYRUN4](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/KELLYRUN4.gif) 

> It has sound!

## Track Operations

As the performance incorporates more objects, the number of tracks increases, raising the risk of accidental operations.

You can:

### Lock Tracks

![image-20250919182517590](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250919182517590.png) 

Locked tracks will still play normally during the performance but cannot be edited. If certain tracks have been temporarily finalized, try locking them.

### Disabling Tracks

![image-20250919182703686](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250919182703686.png) 

Disabled tracks will no longer participate in performances, though their settings remain preserved. Unlocking a track will immediately restore it to the performance. Disabling a track is recommended when you're unsure about permanent deletion or wish to preview the performance without it.

## Events

Events help you:

1. Create effects not supported by the performance system
2. Implement game logic within performances

For example, while the performance system currently doesn't support plot dialogues, we can achieve this effect by creating a dialogue UI + event:

Create a dialogue UI:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250922140523800.png" alt="image-20250922140523800" style="zoom:67%;" /> 

Send custom events at specified times during the performance using Event Tracks:

![image-20250922113643309](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250922113643309.png)

Events are sent to the client's global entity, so a client-side script must be created globally to receive them:

![image-20250922140538997](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250922140538997.png) 

When played:

![KELLYRUN5](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/KELLYRUN5.gif) 



Additionally, you can use events to equip players with weapons, reset mechanisms, or handle loading-related tasks during performance playback.

## Camera Control

Without adding a camera, the performance will play directly on the scene. Players must actively focus on the performance area to view it. For cutscene-style performances, adding an extra camera is highly recommended. Simply place the custom camera on a camera switch track, and the performance system will automatically switch the player's camera during the event, reverting to the default player camera afterward.

When using multiple overlapping camera tracks, the camera from the lowermost track takes precedence:

![image-20250919184520353](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250919184520353.png) 


As mentioned earlier, switching camera tracks only switches to the specified camera. To achieve time-based camera effects, you must additionally create an actor track that holds the camera entity:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250919184800825.png" alt="image-20250919184800825" style="zoom:67%;" /> 

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250919184946219.png" alt="image-20250919184946219" style="zoom:67%;" /> 


## Actor Grouping

You might be wondering: If you need a camera to follow Kelly and create a tracking effect, does that mean adding multiple tracks and manually adjusting their transforms to synchronize their movements?

In some cases, you might indeed need to spend considerable time fine-tuning every detail of the performance. However, for basic tracking, you can simply group actors within a scene into a parent-child structure.

![image-20250919185333372](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250919185333372.png) 


Performances do not disrupt parent-child hierarchies. Applying a transform operation to Kelly will synchronize to her child objects. Treating effects and follow cameras as child objects is a highly efficient workflow.

Note, however, that child objects can still be added to performance tracks as actors. In this case, the child object's transform properties operate in a local coordinate system—meaning their position, rotation, and scale are relative to the parent object.

![image-20250919185605246](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineFE/image-20250919185605246.png) 

## Hiding Actors

All performers in a show are sourced from the scene. You can hide them by setting their visibility to False beforehand or moving them to distant locations.

At the start of the show, enable their visibility or move them to their designated positions.

Note that preemptively disabling visibility may cause collision issues, as hidden objects still retain collision volumes.

## Performance Optimization

A performance may involve a significant number of entities used purely for presentation. Since these entities are no longer needed in the game after the performance ends, you can use events to destroy them post-performance.

When implementing the actor hiding method described above, avoid rendering too many entities in a single frame at the start of the performance, as this severely impacts performance. Use camera artistry or transitions to prevent rendering excessive entities at once.
