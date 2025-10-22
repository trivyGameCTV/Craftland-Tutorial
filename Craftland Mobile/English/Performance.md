# Performance

# Feature Overview

The Performance System is a brand-new custom content editing system within the Free Fire CraftLand Editor. It empowers users to act as directors, visually orchestrating various objects within a scene in chronological order.

When utilizing this system, users will edit elements like animations, sound effects, camera transitions, and event triggers on different tracks of a single timeline—much like editing a video—to produce cutscenes, story sequences, scene transitions, short videos, and more.

This document provides a comprehensive overview of the Performance System's operations and potential applications. After learning these techniques, you can freely design and create your own works.

# Feature Access

Click **More** > **Performances** to display the performance management interface

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/1.png" alt="1" style="zoom:67%;" /> 

Here you can manage all performances within your current project

Click **Create Performance** to create a new blank performance (maximum of 10 performances can be created)

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/2.png" alt="2" style="zoom:67%;" /> 

Clicking any **performance** allows the following actions:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/3.png" alt="3" style="zoom:67%;" /> 

1. **Rename**: Click to modify the performance's name
2. **Duration (seconds)**: Read-only. Displays the total duration of the performance, determined by its track content.
3. **Hide Default UI**: Enabled by default. Automatically hides the default UI (e.g., movement wheel, shoot button, jump button) during performance playback. (Recommended to keep enabled to prevent player actions from interfering with the performance.)
4. **Delete**: Click to display a confirmation dialog. Confirming will permanently delete the performance (cannot be undone). 
5. **Copy**: Click to create a duplicate of this performance within the interface.
6. **Open**: Click to enter the performance's editing interface - Scene View

# Interface Overview

The performance editor offers two views: **Scene View**—for precise editing of individual objects—and **Track View**—for simultaneous viewing and linked editing of multiple objects

Select the view that best suits your workflow and switch between them at any time

> All performance edits are automatically saved upon exiting the editor. Do not force-close the game while editing performances

## Scene View

Here, you can freely adjust the camera perspective as in scene editing (e.g., left joystick area controls direction, right side adjusts zoom).

This view optimizes **recording**: after selecting a timeline position, directly adjust scene objects without tweaking specific parameters. The performance system automatically logs altered attributes onto auto-generated sub-tracks and keyframes

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/4.png" alt=“4” style="zoom:67%;" /> 

### Top - Area 1

![5](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/5.png) 

1. **Exit**: Click to exit the current performance's editing interface
2. **Tutorial**: Click to open the tutorial interface, where you can view a simple guide on performances
3. **Tracks**: Click to display the track list. You can create corresponding tracks. See *Track Editing* for details.

![7](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/7.png) 
4. **Performance**: Click to display the performance management interface.
5. **Performance Name**: Read-only. Displays the name of the currently edited performance.
6. **Hints**: Click to display the hint panel. Here you can view relevant rules about performances.

### Bottom - Area 2

![9](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/9.png) 

1. **Track Selection**: Click to display all tracks within the current performance. Select a track to edit it

![10](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/10.png) 

2. **Camera Switch**: Available only after creating a camera switch track. clicking switches to that camera view (Fig. 1 → Fig. 2)

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/11.png" alt="11" style="zoom:67%;" /> 

> Fig. 1

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/12.png" alt="12" style="zoom:67%;" /> 

> Fig. 2

3. **Record**: After selecting a scene object or actor/NPC track, click to enter recording mode

![13](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/13.png) 

You can slide the timeline to determine the insertion timing of keyframes. Click the button shown below to edit the properties of the object attached to the track at that keyframe (e.g., position/scale/rotation/color)

![14](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/14.png) 


Editing any property automatically creates corresponding sub-tracks and keyframes. The properties of the track-mounted object will transition smoothly between consecutive keyframes.

4. **Previous Second, Play/Pause, Next Second**: Click to adjust time to the previous/next second, displaying the state of the track-mounted object at that time. Also enables preview playback/pause.

5. **Timeline**: Swipe left/right (pinch-to-zoom for finer time scales not currently supported). The scene will display performance effects in real time.

6. **Track Details**: This area supports displaying only one main track and its sub-tracks simultaneously. Supports vertical scrolling.

![15](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/15.png) 

7. **View Switch**: Tap to switch to Track View.

### Center - Create Track

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/16.png" alt="16" style="zoom:67%; " /> 

When you click to select an object without an assigned track in this interface, the **Create Track** button appears at the bottom. Clicking it creates a relevant track (Object → Actor Track; NPC → NPC Track).
- Currently, only one track can be created per object.
- After creation, you can edit the track. See *Track Editing* for details.

## Track View

Here you can view all tracks within the current performance, play and preview the performance on the left, and clearly see the relationships between different tracks and their content on the timeline. This facilitates more precise operations such as aligning keyframes/key clips.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/17.png" alt="17" style="zoom:67%;" /> 

### Top - Area 1

![18](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/18.png) 

1. **Tutorial**: Click to open the tutorial interface, where you can view basic guidance on performances.
2. **Tracks**: Click to display the track list. You can create corresponding tracks; see *Track Editing* for details.

![20](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/20.png) 
3. **Performances**: Click to display the performance management interface

### Left Side - Area 2

![21](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/21.png) 

1. **Scene Preview**: Displays the current scene state and allows playback and preview of the performance
   1. Clicking a track will focus on the object attached to that track within the scene

2. **Track Selection**: Click to display all tracks in the current performance. After selection, edit the track in the Track Overview on the right

![22](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/22.png) 

3. **Camera Switch**: Available only after creating a camera switch track. Clicking switches to that camera view (e.g., Figure 1 → Figure 2)

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/23.png" alt=“23” style="zoom:67%;" /> 

> Figure 1

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/24.png" alt="24" style="zoom:67%;" /> 

> Figure 2

4. **Recording**: After selecting an actor/NPC track, click to enter recording mode. You must switch to the scene view to perform subsequent operations.

5. **Previous Second, Play/Pause, Next Second**: Click to adjust the time to the previous/next second, displaying the state of the corresponding track's attached object at that time. Also enables preview playback/pause.

### Right Side - Area 3

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/25.png" alt="25" style="zoom:67%;" /> 


1. **Track Overview**: View all tracks within the current performance here. Clearly see how different tracks and their content relate on the timeline, enabling precise alignment of keyframes/key clips. This area supports vertical scrolling. Click a track to edit it; see *Track Editing* for details.
2. **View Switch**: Click to switch to Scene View

# Track Editing

Tracks serve as containers for content, holding an object's temporal transformation information.

The performance system provides various master/child tracks, each possessing unique properties. Note that:
- Each master track can only host entities of its specific type
- Certain child tracks can only be attached to designated master tracks

Tracks currently only support entities already placed in the scene. If an entity is destroyed during the performance, its associated track content will cease to function. Therefore, ensure relevant entities remain active during the performance.

Click **Track** to open the track list. Here, you can create different track types and perform various edits (e.g., create sub-tracks, create key clips, create keyframes, etc.).

![26](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/26.png) 

For any parent/child track, click here to rename it

![27](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/27.png) 


## Actor Tracks

![28](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/28.png) 

Click to display the object filter list, which includes all objects in the scene without tracks. You can filter, sort, or search to precisely locate the desired object

If **NPC** is selected, an NPC track will be created for it

Click to confirm creation of an Actor Track

![29](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/29.png) 



For existing Actor Tracks, you can perform the following actions:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/30.png" alt="30" style="zoom:67%;" /> 


1. **Delete Track**: Click to remove the track

> This action cannot be undone. Proceed with caution.
2. **Create Sub-Track**: Click to open the sub-track list. Select the desired sub-track category, then click **+/-** to create/delete the sub-track.

> See *Track Editing - Sub-Tracks* for details.
3. **Create Keyframe**: Click to create a keyframe at the current timeline position

> Keyframes can be deleted/edited. Click Edit to display keyframe settings

![31](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/31.png) 

1. Modifying the **Start Time** will change the keyframe's position on the timeline
2. Modifying **Position/Rotation/Scale/Color** (if applicable) will automatically create corresponding sub-tracks

## Audio Tracks

![32](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/32.png) 

Click to display the sound effects interface (current effects are provided by the official source; custom audio import is not supported at this time). This interface can be scrolled vertically.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/W1.png" alt="W1" style="zoom:67%;" /> 

1. Tap the top-right corner to display the audio category list

![W2](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/W2.png) 
2. Tap the 【▶】 icon to preview audio content
3. Click **Download All** to download all audio resources
4. After selecting an audio file, click Confirm to create an audio track

For existing audio tracks, you can perform the following actions: (Sub-tracks cannot be created for this track type)

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/35.png" alt="35" style="zoom:67%;" /> 

1. **Delete Track**: Click to remove the track

> This action cannot be undone. Proceed with caution.

2. **Create Keyframes**: Click to display the sound effect interface. Repeat the above process. For existing keyframes, you can perform the following actions:
<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/36.png" alt="36" style="zoom:67%;" />


1. **Edit**: Click to display the editing interface
1. Here you can edit specific properties of the keyframe, such as: start playback time, duration, sound effect resource, loop type, volume, playback speed
2. You can also adjust the start and end times by directly dragging the left/right handles of the keyframe (Note: Avoid overlapping keyframes, as this will prevent later-starting keyframes from playing)![37](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/37.png)


2. **Delete Track**: Click to remove this track

> This action cannot be undone. Proceed with caution.

3. **Delete Keyframe**: Click to remove this keyframe

> This action cannot be undone. Proceed with caution.


## NPC Tracks

![38](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/38.png) 

Click to display the NPC filter list, containing all NPCs in the scene without created tracks. You can filter/sort/search to accurately locate the desired NPC.

Click Confirm to create an NPC track.

![39](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/39.png) 

For existing NPC tracks, you can perform the following actions (similar to **Actor Tracks**):<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/40.png" alt="40" style="zoom:67%;" />


1. **Delete Track**: Click to remove the track

> This action cannot be undone. Proceed with caution.

2. **Create Sub-Track**: Click to open the sub-track list. Select the desired sub-track type, then click **+/-** to create/delete the sub-track.

> NPC tracks can create specialized sub-tracks: **Animation Tracks**. See *Track Editing - **Sub-Tracks**

3. **Create Keyframe**: Click to create a keyframe at the current timeline position
1. Keyframes can be deleted/edited. Click Edit to display the keyframe settings interface

![41](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/41.png) 

2. Modifying **Start Time** changes the keyframe's position on the timeline

4. Modifying **Position/Rotation/Scale** will automatically create corresponding sub-tracks

## Event Track

![42](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/42.png) 

Click to create an event track (sub-tracks cannot be created for this track type)

For existing camera transition tracks, you can perform the following actions:<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/43.png" alt="43" style="zoom:67%;" /> 

### **Creating Keyframes**

Click to create a keyframe at the selected timeline position. For existing keyframes, you can perform the following actions:<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/44.png" alt="44" style="zoom:67%;" />


1. **Edit**: Click to open the editing interface where you can modify the keyframe's specific properties, such as start time and the custom event sending panel.

1. **Custom Event Sending Panel:**

![45](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/45.png) 

2. **Add Custom Event to Send**: Click to create a new custom event. This event will be sent when the keyframe reaches its specified time.

1. **Select Custom Event to Send**:

![W3](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/W3.png) 

2. Click “Create Custom Event” at the bottom of the list to open the Custom Event Manager. Here you can add/delete custom events, rename them, and adjust their sending parameters.


 <img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/47.png" alt="47" style="zoom: 50%; " /> <img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/48.png" alt="48" style="zoom: 50%;" /> 

2. **Delete Sent Custom Events**:

> This action cannot be undone. Proceed with caution.

4. **Edit Sent Custom Events**:

1. You can edit specific details of sent custom events here, such as: selecting the custom event, sending target, sending platform, and parameters set in the **Custom Event Manager**

![49](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/49.png) ![50](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/50.png) 

5. After completing the above edits, you can locate the corresponding event in the graphic list and drag it into the script for editing

![51](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/51.png) 

### **Deleting Keyframes**

Click to delete this keyframe

> This action cannot be undone. Please click carefully.

## Camera Switch Track

![52](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/52.png) 

Click to create a camera transition track (sub-tracks cannot be created for this track type)

> Only one camera transition track is allowed per performance

You must first create a **Custom Camera** in the scene. This object can be found in the **Object Library > Basic Structure > Performance** section on the right side of the editor.

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/53.png" alt="53" style="zoom:67%;" />  

For existing camera transition tracks, you can perform the following actions:<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/54.png" alt="54" style="zoom:67%;" />


### **Delete Track**

Click to delete this track

> This action cannot be undone. Proceed with caution.

### **Create Keyframes**

Click to display the custom curve path filter list, containing all custom curve paths within the scene. After filtering/sorting/searching to locate the desired object, create a keyframe for it

![55](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/55.png) 

After selecting a custom camera, click to confirm and create a keyframe.

For created keyframes, you can perform the following actions:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/56.png" alt="56" style="zoom:67%;" /> 

1. **Edit** : Click to display the editing interface
1. Here, you can edit the specific properties of this keyframe, such as: start playback time, duration, camera resource

2. You can also adjust the start and end playback timing by directly dragging the left and right handles of the keyframe (Note: Do not overlap keyframes, as this will prevent keyframes with later start times from playing)

![57](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/57.png) 

2. **Delete Track**: Click to remove this track

> This action cannot be undone. Proceed with caution.

3. **Delete Keyframe**: Click to remove this keyframe

> This action cannot be undone. Please click carefully

## Sub-Tracks

### Entity Tracks

![58](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/58.png) 

This track contains the following 4 track types. Depending on the object mounted to the parent track, different tracks may be created.

1. **Position Track**: After creation, you can add keyframes to this track. By adjusting the XYZ axis values of these keyframes, the world position of the attached object transitions smoothly between consecutive keyframes.
2. **Rotation Track**: After creation, keyframes can be added to this track. By adjusting the XYZ axis property values of keyframes, the rotation angle of the attached object can smoothly transition between two consecutive keyframes over time.
3. **Scale Track**: After creation, keyframes can be added to this track. By adjusting the XYZ axis property values of keyframes, the scale factor of the attached object can smoothly transition between two consecutive keyframes.
4. **Color Track**: After creation, you can create keyframes on this track. By adjusting the values of the color property in keyframes, you can achieve a smooth transition of the mounted object's color between two consecutive keyframes.

### Path Follow Track

![59](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/59.png) 


This track currently functions solely as a sub-track of the **NPC Track**, enabling the NPC to play the assigned animation for the duration of the keyframed segment within the track.

For existing animation tracks, you can perform the following actions:<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/60.png" alt="60" style="zoom:67%;" />


1. **Delete Track**: Click to remove the track

> This action cannot be undone. Proceed with caution.
2. **Create Keyframe**: Click to display the custom curve path filter list, which contains all custom curve paths in the scene. After filtering/sorting/searching to locate the desired object, create a keyframe for it.

![61](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/61.png) 


After selecting a custom curve path, click Confirm to create a keyframe.



For existing keyframes, you can perform the following actions:<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/62.png" alt="62" style="zoom:67%;" /> 

1. **Edit**: Click to display the editing interface
1. Here you can edit the specific properties of this keyframe, such as: start playback time, duration, path resource, loop type, volume, playback speed, and whether it faces tangent.

2. You can also adjust the start and end timing of playback by directly dragging the left and right handles of the keyframe (Note: Do not overlap keyframes, as this will prevent keyframes with later start times from playing).

![63](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/63.png) 

2. **Delete Track**: Click to delete this track

> This action cannot be undone. Click with caution.

3. **Delete Keyframe**: Click to delete the selected keyframe

> This action cannot be undone. Proceed with caution.

### Animation Track

![64](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/64.png) 

This track currently functions solely as a **sub-track** for NPC tracks, enabling the NPC to play the assigned animation during the duration of keyframes within the track.

For existing animation tracks, you can perform the following actions:<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/65.png" alt="65" style="zoom:67%;" />


1. **Delete Track**: Click to remove this track

> This action cannot be undone. Proceed with caution.

2. **Create Keyframe**: Click to display the animation interface (current animations are provided by the platform; custom animation import is not supported at this time). This interface can be scrolled vertically. 

1. Tap the animation category list in the top-right corner
![67](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/67.png)
2. After selecting an animation, tap Confirm to create a keyframe



For created keyframes, you can perform the following actions:<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/68.png" alt="68" style="zoom:67%;" />


1. **Edit**: Click to display the editing interface
1. Here you can edit the specific properties of this keyframe, such as: start time, duration, loop type, animation resource, playback speed
2. You can also adjust the playback start and end timing by directly dragging the left and right handles of the keyframe (Note: Do not overlap keyframes, as this will prevent later keyframes from playing)![69](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/69.png)

2. **Delete Track**: Click to delete the track

> This action cannot be undone. Click with caution.

3. **Delete Keyframe**: Click to delete the keyframe

> This action cannot be undone. Click with caution.

# Performance Playback

After creating and editing your performance, you have two methods to trigger playback during gameplay:

## Performance Trigger

Click **Object Library > Function Objects > Triggers** on the right side of the editor, select **Performance Trigger**, and drag it into the scene

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/Q1.png" alt="Q1" style="zoom:67%; " /> 



Click **Edit** to configure the performance to play when players enter this trigger during gameplay, along with its destruction time.

You can also perform standard operations like **Move/Rotate/Scale** on this object. <img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/Q2.png" alt="Q2" style="zoom:67%;" />


1. **Performance Resource**: Click to open the performance resource selection interface. Choose the performance to trigger when players enter this trigger during gameplay. You can also create new performance resources here:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/W4.png" alt="W4" style="zoom:67% ;" /> 

2. **Destruction Time**: Drag the slider or manually enter a time (in seconds) to set how long the performance will play before it is destroyed.
1. The default value is 300. It is recommended to set this value equal to the total duration of the performance.
2. If this value is less than the total duration of the performance, the performance will stop playing before the set destruction time.
3. If this value exceeds the performance's total duration, re-entering this trigger after the time has elapsed will not re-trigger the performance until the destruction time is reached

After completing the above steps, when players enter this trigger while experiencing your work, the selected performance resource will automatically play

## Client Metadata - Creating a Performance

After selecting the appropriate client script, click **Game > Story > Create Performance** on the left side of the script library and drag it into the script editor.

![Q4](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/Q4.png) 

For this **Create Performance** element, you can configure the following properties:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/Q5.png" alt="Q5" style="zoom:67%;" /> 

1. **Performance Resource**: Click to open the performance resource selection interface. Choose the performance that will trigger and play when the player enters this trigger during gameplay. You can also create a new performance resource here: <img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/W5.png" alt="W5" style="zoom:67%;" /> 
2. **Auto-Play**: Click to select **True/False**. This determines whether the performance starts playing immediately after creation. We recommend setting this value to **True**.

You can then connect the corresponding event element **above** this element based on your desired trigger method, and connect other required elements **below** it.

After completing the above steps, when players experience your work, the selected performance resource will automatically play upon triggering the event element you set.

# Key Concepts

| Name | Reference Image | Definition |
| -------- | -- ----------------- | ------------------------------------------------------------ |
| Timeline | ![70](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/70.png) | The timeline is a reference system organized chronologically, resembling a ruler marked in seconds. <br />All content within a performance (e.g., tracks, keyframes, etc.) are arranged based on this time scale, determining their playback sequence |
| Track | ![71](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/71.png) | Tracks serve as containers for content, holding an object's change information along the timeline<br />Tracks are categorized by hierarchy into main tracks and sub-tracks, each possessing distinct properties<br / >Each master track can only host entities of its corresponding type; some child tracks can only be attached to specific master tracks |
| Keyframe | ![72](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/72.png) | Keyframes serve as anchor points for tracks on the timeline, recording the state of an object or its properties at a specific moment within the track<br />The performance system automatically interpolates property differences between consecutive keyframes, ensuring smooth transitions across the interval between them |
| Key Fragments | ![73](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/73.png) | Keyframes are the fundamental units of a track on the timeline, displaying the state of an element over time. <br />Keyframes possess distinct properties depending on the track they reside on. <br />Each type of keyframe can only be attached to a specific track. |
| Recording | ![74](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/TimelineCL/74.png) | Recording allows you to adjust scene objects directly after selecting a timeline position, bypassing manual parameter tweaking. The performance system automatically logs these changes to auto-generated sub-tracks and keyframes.<br />*Note: This is not screen recording. Upon completion, no media files are saved to your device's gallery or files. |

# Q&A

Q: How can I switch background skyboxes during performance playback to enhance the atmosphere?

A: Craftland mobile currently lacks skybox-related track functionality. For this feature, please use Craftland Studio on desktop.



Q: After creating a camera transition track, how do I create a camera movement sequence?

A: First, create a **Key Clip** on that track (select an existing **Custom Camera** within the scene to execute the camera movement). Then, create an **Actor Track** for that **Custom Camera**. Based on your camera movement needs, create and edit the following sub-tracks: **Position/Rotation/Path Follow**. You can then preview the camera movement by clicking **Camera Switch, Play**.



Q: Why doesn't the object/NPC change as expected after I create a keyframe at a specific point on the timeline?

A: Creating a single keyframe alone won't change the object/NPC. Only when two or more keyframes exist on the same track will the object/NPC undergo smooth transition changes in attributes like position/rotation/scale/color during the interval between consecutive keyframes.



Q: How can the Performance System integrate with the existing Dialogue System to display character dialogue boxes and lines during performance clips?

A: You can edit character dialogue in the **Dialogue Settings* * to edit character dialogue. Then create an event track → set keyframes at specific timeline positions → edit the sent event → connect the dialogue playback element under that event to integrate both systems.



Q: Can I play two or more performances simultaneously?

A: While currently supported, this is not recommended. Simultaneous playback may overload system resources. Additionally, errors may occur if tracks share bound objects, potentially disrupting performance.



Q: Occasional freezes or device overheating occur during performance editing/playback. How can this be resolved?

A: This is an occasional occurrence. If it happens frequently, we recommend deleting some performance assets to reduce system power consumption. In future versions, we will continue to optimize performance to ensure a smooth player experience.



Q: What methods are currently available to optimize performance power consumption?

A: If you've set up numerous one-time objects/NPCs exclusively for this performance, you can use event primitives to destroy these one-time objects/NPCs upon the performance's completion.
