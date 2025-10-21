# GameFlow

In CraftLand, the specific GameFlow is hidden, but you can still change the gameplay and time of the map by setting or modifying the parameters and processes in the GameFlow.

## Concept Description

> The following concept description is based on the custom mode in CraftLand

![image-20241029163802371](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/image-20241029163802371.png)

Our game process is composed of stages. The game starts from a fixed game start stage, goes through several set stages, and ends at a fixed game end stage. Each stage will automatically enter the next stage according to the process after the set time is over. The minimum duration of each stage is 5 seconds. The two stages of game start and game end must exist and serve as the starting point and end point of the game. A round is a special stage, which is a collection of several stages, and the number of cycles can be specified. Whenever the process enters a round, the several stages it contains will be repeatedly executed in order in the round, and the round will end after the number of cycles is reached and continue to proceed. Rounds cannot contain rounds. In CraftLand, a round has 3 stages by default.

| Phase Name | Diagram | Description |
|------------|---------|-------------|
| Start      | ![Start](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/image-20241104112309485.png) | The start of the game. This stage is usually to wait for players to connect to the game. |
| Preparation| ![Preparation](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/image-20241104112435283.png) | Game preparation phase, this phase is usually to wait for players to load the map. |
| Round      | ![Round](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/image-20241104112457131.png) | The start of the round, representing the beginning of the round cycle. |
| Round Phase 1 | ![Round Phase 1](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/image-20241104112338388.png) | The first phase of a round, usually to give players time to buy weapons. |
| Round Phase 2 | ![Round Phase 2](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/image-20241104112724432.png) | The second phase of a round. This phase is usually the longest and is the main play phase for players in the round. |
| Round Phase 3 | ![Round Phase 3](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/image-20241104112246177.png) | The third phase of the round. This phase is the settlement time, and the winning team of the round will be announced to all players. |
| End        | ![End](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/image-20241104112527845.png) | The end of the game. Entering this stage means the end of the game, and all players will exit the game. |

### Example

> The following is a detailed example of the corresponding stages of the game process based on the Clash Squad template mode.

| Stage name | Diagram | Corresponding game flow | Description |
|------------|---------|--------------------------|-------------|
| Start      | ![Start](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/image-20241029173915493.png) | ![SeaTalk_IMG_20241029_151016](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/SeaTalk_IMG_20241029_151016.jpg) | When all players enter the game, the loading of the Start stage has been completed. The Start stage is mainly used to wait for players to join the game and load the game. |
| Preparation| ![Preparation](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/image-20241029173930698.png) | ![SeaTalk_IMG_20241029_150545](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/SeaTalk_IMG_20241029_150545.jpg) | You will wait for dozens of seconds after entering the game. This is the preparation stage before the game starts. The member information and team information of both teams will be displayed. Players cannot leave the safe zone during the preparation stage. |
| Round Start| ![Round Start](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/image-20241029173940387.png) | ![SeaTalk_IMG_20241029_154256](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/SeaTalk_IMG_20241029_154256.jpg) | At the beginning of a round, a very obvious UI will pop up to remind the player which round it is.|
| Round Phase 1 | ![Round Phase 1](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/image-20241029173955643.png) | ![SeaTalk_IMG_20241029_153132](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/SeaTalk_IMG_20241029_153132.jpg) | The first phase at the beginning of the round is the player's gun-buying time. During this phase, the player cannot leave the safe zone, and the player has dozens of seconds to buy suitable props and guns. |
| Round Phase 2 | ![Round Phase 2](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/image-20241029174022084.png) | ![SeaTalk_IMG_20241029_154713](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/SeaTalk_IMG_20241029_154713.jpg) | In the second phase at the beginning of the round, the safe zone will disappear and the store will be closed. This phase is the main gameplay phase for the players. Both teams need to wipe out the other team to win the round. |
| Round Phase 3 | ![Round Phase 3](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/image-20241029174033802.png) | ![SeaTalk_IMG_20241029_154835](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/SeaTalk_IMG_20241029_154835.jpg) | When any team is wiped out, the second phase will automatically end and enter the third phase of the round. The third phase is the settlement phase. In CS mode, the current scores of the winner and both teams will be displayed through an obvious UI. |
| End        | ![End](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/image-20241029174041012.png) | ![SeaTalk_IMG_20241029_152447](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/SeaTalk_IMG_20241029_152447-1730188100972-13.jpg) | In CS mode, when any team gets the match point first, the game will enter the end phase, the winning team will be displayed on the UI, and after a few seconds, all players will automatically exit the current game. |

## How to modify stage configuration

> Unless otherwise specified, the term "phase" below includes the concept of rounds.

Currently in CraftLand you can change the GameFlow configuration in two ways, **Game Settings** and **Primitives**.

### Game Settings

Through the game settings, click **Setting** in the upper left corner of the editor, then click **GAMEPLAY SETTINGS** on the right, and click **Edit GamePlay Rules**, you can see that we provide some simple and commonly used modification options for CraftLand creators in the game settings, and the adjustable configurations displayed will be different according to different preset templates. ![SeaTalk_IMG_20241021_114123](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/SeaTalk_IMG_20241021_114123.jpg)

### Primitives

#### Phase Index

In CraftLand, each stage will get a unique ID according to the process order. We can use the primitives to determine whether the current stage is the specified stage ID to modify the parameters and events of the corresponding stage.

#### How to get the stage index id?

We can know the index id of all stages through two simple lines of primitives. The following is an example of primitives.

First, we place the two elements 'Phase Start' and 'Print Log' in the global script.

![SeaTalk_IMG_20241028_105014](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/SeaTalk_IMG_20241028_105014.jpg)

Then we close the element editor, click the **debug** button, and try out the map.

![image-20241028105605176](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/image-20241028105605176.png)

After entering the trial, click the **Log** entry in the upper right corner of the interface to enter the log interface![image-20241029173316947](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/image-20241029173316947.png)

In the log, as the game progresses, the stage index id will be automatically printed in the log interface. Each printed id corresponds to the current stage in progress![SeaTalk_IMG_20241029_173008](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/SeaTalk_IMG_20241029_173008.jpg)

**Graphic:**

According to the above figure, we can know the index id corresponding to each stage. The stages in a round do not get new ids due to repeated cycles. For example, if all the stage indexes in the first round are 3, 4, 5, 6, then all the stage indexes in the second round will still be 3, 4, 5, 6. The round index starts from 0.

![image-20250609201418434](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/image-20250609201418434.png)

#### Editing Phase Elements

In the graphic element, we provide 4 events to monitor the start and end of rounds or stages. Reasonable use of these 4 events can effectively change the map mode and achieve the creator's goals more quickly.

| List | Example Image |
|------|--------------|
| When the round starts; | ![RoundStart](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/RoundStart.png) |
| When the round ends; | ![RoundEnd](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/RoundEnd.png) |
| When the phase starts; | ![PhaseStart](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/PhaseStart.png) |
| When the phase ends; | ![PhaseEnd](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/PhaseEnd.png) |

'When the phase starts' will make a judgment at the beginning of each stage. 'When the phase ends' will make a judgment at the end of each stage.

![image-20241029172434141](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/image-20241029172434141.png)

'When the round starts' will only be judged once at the beginning of each round phase. 'When the round ends' will only be judged once at the end of the last phase of each round.

![image-20241029171124108](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/image-20241029171124108.png)

Here, the turn is distinguished from the stage. When the stage starts/ends, only the **When the phase starts** and **When the phase ends** events will be triggered; the **When the round starts** and **When the round ends** events will not be triggered. The round logic is the same.

**Example 1:** When the specified phase starts

![OnPhaseStart](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/OnPhaseStart.jpg)

**Example 2:** When the specified phase ends

![OnPhaseEnd](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/OnPhaseEnd.jpg)

**Example 3:** When the specified round starts

![OnRoundStart](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/OnRoundStart.jpg)

**Example 4:** When the specified round ends

![OnRoundEnd](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/OnRoundEnd.jpg)

## Practical Application

The preparation time and settlement time of a player in a single round are set to 5 seconds, and the game time is set to 90 seconds. Each kill caused by the player during the game time can earn 1 point for his team. When either team reaches 20 points first within the game time, that team wins the current round and ends the current round.

1. Create parameters and modify basic settings

First, adjust the round time to 90 seconds.

![SeaTalk_IMG_20241025_110312](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/SeaTalk_IMG_20241025_110312.jpg)

Click **Setting** in the upper left corner of the interface, then click **Edit Gameplay Rules** on the right to enter the setting interface, then click **Property Settings** to enter the rule editing interface, and then we add a 'TeamKills' parameter in the **Team Rules** column as the basis for subsequent judgment of the number of kills of both teams.

![SeaTalk_IMG_20241025_110310](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/SeaTalk_IMG_20241025_110310.jpg)

2. Create graphic elements

**Graphic logic:** When the stage with stage index 5 starts, the 'TeamKills' parameter of both teams is traversed. If the TeamKills of either team reaches 20, the stage ends.

First, we add a conditional judgment in the **When stage starts** event and find the stage we want to add the method to by stage index (stage index 5).

![SeaTalk_IMG_20241025_112428](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/SeaTalk_IMG_20241025_112428-1729826730554-8.jpg)

When the kill count of any team, the parameter 'TeamKills' we just added, is greater than or equal to 20, the current stage ends.

![SeaTalk_IMG_20241025_113716](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/SeaTalk_IMG_20241025_113716.jpg)

![SeaTalk_IMG_20241025_113719](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/9_Workflow/SeaTalk_IMG_20241025_113719.jpg)
