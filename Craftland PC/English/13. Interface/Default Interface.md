# UI

# Player Default HUD

## Customize Start Banner Information
Open **PlayerDefaultHUD.eca**

In the **InitPlayerStartHUD** function, Creator can adjust **Title**, **Description** and **Icon** of the map.

<img src = "https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/1-FFA/StartHUD.png">
<img src = "https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/1-FFA/StartHUD2.png">

# Developing Tutorial
Create **PlayerDefaultHUD.eca** attach it to **Player** entity in Module.

## Timer HUD
<img src = "https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/1-FFA/timer-hud.png">

Each time phase start, call **DisplayTimer** function to display the countdown for that phase.

<img src = "https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/1-FFA/timer.png">


## Objective HUD

<img src = "https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/1-FFA/objective-hud-2.png">

<img src = "https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/1-FFA/objective-hud.png">

## PlayerStart HUD
<img src = "https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/1-FFA/start-hud.png">

<img src = "https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/1-FFA/StartHUD.png">

## Initialize the HUD
Calling **Init** with the **On Awake** event will initialize the HUD when match start.

<img src = "https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/1-FFA/hud-init.png">

## Player Scoreboard

### Player Scoreboard
<img src = "https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/1-FFA/score-board-2.png">

Create **PlayerScoreBoard.eca** attach it to **Player** entity in Module.

First, we need to initialize the scoreboard.

<img src = "https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/1-FFA/score-board.png">

To update the scoreboard, we need to create a sort function to get the player list sorted by score. This function will return *Player List sorted by score, score list, rank list, and List of Player List sorted by score (this is the format use for updating the scoreboard)*

<img src = "https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/1-FFA/get-player-list.png">

Update scoreboard when player is eliminated.


<img src = "https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/1-FFA/update-score.png">

### Player Scoreboard Button
Create **ScoreBoardBtn.ui** and **ScoreBoardBtnHUD.eca**. Attach **ScoreBoardBtnHUD.eca** to **ScoreBoardBtn.ui**

Create a Button in the **ScoreBoardBtn.ui** file, place it where you want the player to click to open the scoreboard. In this case, we want it to be at the timer position.

<img src = "https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/1-FFA/scoreboard-btn.png">

In **ScoreBoardBtnHUD.eca**, create a callback function to display the scoreboard whenever the button is pressed. Then, attach the callback function to the created button above.

<img src = "https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/1-FFA/scoreboard-btn-callback.png">
<img src = "https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/1-FFA/btn-callback.png">

## Player Result HUD
<img src = "https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/1-FFA/result-hud.png">

Open **PlayerScoreBoard.eca**

Create a DisplayResultScoreBoard function and set the parameters. Call it when Phase **End** start.

<img src = "https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/1-FFA/result.png">

## Player Ranking HUD

<img src = "https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/1-FFA/rank-hud.png">

### Ranking UI

Create **Ranking.ui** file as bellow.

<img src = "https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/1-FFA/rank-ui.png">

### Ranking HUD Logic

Create **PlayerRankingHUD.eca** file. Attach it to **Player** module.

Create **Init** and **Update** function.

<img src = "https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/1-FFA/rank-init.png">

Update required current player's score, objective, and current player's ranking. In this case, player score is player Elimination.
To get player ranking, can use the logic bellow.

<img src = "https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/1-FFA/get-ranking.png">

<img src = "https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/1-FFA/rank-update.png">

Call Update whenever a player is eliminated. Overall, the file should look like this.

<img src = "https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/1-FFA/ranking-overall.png">
