# Time

# Concept description

## Logic frame

The logic frame is the number of calculations that update the state of objects per second, and it runs as the game progresses.

The logic frame update interval (DeltaTime) is the time consumed per frame logic frame update, in milliseconds. On the server, this value is generally 33ms (30 frames per second), and if low frame rate mode is enabled, this value will increase to 66ms (15 frames per second). On the client, this value depends on the performance of the device running the game and the complexity of the logic running in that frame. For devices with different performance, logic frame updates will be performed at benchmark rates of 30, 45, 60, 90 frames per second, etc., however, this is not stable and will fluctuate during actual operation based on the amount of calculations in the current frame.

![image-20241031162541260](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/30-Time/image-20241031162541260.png)

> Server low frame rate mode setting

After each logic frame is successfully updated, the logic under the logic frame update event (OnUpdate) will be attempted, and the update of the next logic frame will begin.

You can find the logic frame update interval property in the global properties, and you can get the time consumed by the last logic frame through this property. As mentioned above, get this property on the server script, and it will always return 66 or 33 depending on whether the server low frame rate mode is enabled; get this property on the client script, and you will get the time consumed by the last logic frame update.

![image-20241031160820759](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/30-Time/image-20241031160820759.png)

## Fixed frame

Fixed frames are updated at regular intervals in real time.

fixed frame update interval (FixedDeltaTime) refers to the length of time set for each fixed frame, in milliseconds. In Craftland Studio PC, whether on the client or the server, fixed frames are always updated at a rate of 30 times per second, which means that the fixed frame update interval is 33ms.

After each fixed frame is successfully updated, the logic under the fixed frame update event (OnFixedUpdate) will be attempted and the update of the next fixed frame will begin.

You can find the fixed frame update interval property in the global properties. As mentioned above, the value of this property is always 33, regardless of whether it is obtained in client-side or server-side scripting.

![image-20241223181242317](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/30-Time/image-20241223181242317.png)

## Game time

In the global properties, you will find the game time property.

![image-20241223181134697](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/30-Time/image-20241223181134697.png)

It represents the real-time length of the game from the beginning, and this time will increase by 33 after each fixed frame update.

The start time of the game on the client and the server will be slightly different, so the game time property value on the client is usually smaller than that on the server.

## Cumulative number of running frames

In the global properties, you will find the cumulative number of running frames property, which records the total number of logic frames that have been updated on the current platform (server or client).

![image-20241223185132371](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/30-Time/image-20241223185132371.png)

## Additional information

The properties of the logic frame update frequency, fixed frame update frequency, game time, and total running frame are all properties that distinguish the client from the server. These properties exist independently on both ends, although the values of some properties may be the same, such as the fixed frame update frequency.

# Using the time module

## Frame update event

For logic frames and fixed frames, you can trigger logic when they are updated through the corresponding events.

![image-20241031163319163](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/30-Time/image-20241031163319163.png)

In the client, for physical movement, it is better to place it under a fixed frame update event, otherwise the movement of objects may become unstable when the speed of the logic frame update fluctuates.

![image-20241031165758933](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/30-Time/image-20241031165758933.png)

> With an update frequency of 30 times per second, the movement of objects will also appear to be stuck. For smoother movement, please use the Playable module

In server 15 frame mode, the fixed frame update event in the server script will run twice before each logic frame update.

![image-20241031165917235](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/30-Time/image-20241031165917235.png)

![image-20241031170114112](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/30-Time/image-20241031170114112.png)

The client is not affected by this setting and is still updated at the current device rendering rate.

![image-20241031183152529](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/30-Time/image-20241031183152529.png)

![image-20241031183233372](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/30-Time/image-20241031183233372.png)

## Pause fixed frame update

Using the pause fixed frame update block will only stop the fixed frame update event trigger on the corresponding platform.
Pausing the fixed frame update will not affect other time module-related content. Game time will still be accumulated normally, and logic frame updates will not be affected.

![image-20241031172523455](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/30-Time/image-20241031172523455.png)

Using the resume fixed frame update block will restart triggering fixed frame update events.

![image-20241031172549272](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/30-Time/image-20241031172549272.png)

After these two APIs are called, the game pause and game resume events will be triggered respectively

![image-20241104112751825](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/30-Time/image-20241104112751825.png)
