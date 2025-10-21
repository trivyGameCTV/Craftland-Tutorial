# First Person

First Person mode is one of the core perspective gameplay templates supported by the CL Editor. When enabled, players will play the game in first person view, with the camera positioned close to the character's eyes, emphasizing immersion and precision. This mode is widely used in the creation of shooting, survival, and puzzle games.

![img](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MODE/wps1.png)



## **Mode Rules and Mechanics**

● When enabled, players will default to first-person view, which cannot be switched to third-person view;

● All character-related animations (jumping, shooting, running) will be displayed in first-person view.

● Players have higher aiming and interaction accuracy in first-person view, which is suitable for gameplay designs that require precise controls and a more immersive experience.



## **Common Mode Parameters**

![img](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MODE/wps2.png)

**The first-person template supports adjusting parameters related to first-person team assault**:

| Parameter | Function Description |
| ---------- | ------------------------------------------------ |
| Number of Rounds | Sets the total number of rounds in a match |
| Round duration | Time limit for each round, including preparation time and match time |
| Team settings | Two teams by default, the number of teams and team members can be manually reset |
| Round reset | Resets health and status at the start of each round, with the option to keep or refresh equipment status |



## **Suitable game types**

- Immersive gunfight experience (FPS)
- Horror survival / escape room puzzle
- First-person parkour/jumping challenge
- Story-driven exploration game (more closely aligned with the character's perspective**)**



## **Development recommendations**

- Fine-tune the perspective to match the scene size: First-person perspective requires a higher tolerance for collisions and jumps, so we recommend using reasonable collision volumes and platform designs.
- Use a simple UI layout: The first-person UI has a limited field of view, so we recommend reducing the HUD coverage area.
- Adapt sound effects and interactive prompts: Players cannot directly see the characters' animations, so use sounds and highlighted prompts to compensate for blind spots.
