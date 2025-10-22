# Point Mode

The **Point Mode** is a widely used competitive gameplay template in CL Editor. Players are divided into two or more teams and engage in intense combat within a designated area. Each time a player defeats an enemy member, their team gains a certain number of points. Players who are killed will respawn after a certain period of time. The match continues until one team reaches the predetermined victory score first, thereby winning the entire match.

![img](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MODE/wps1-1754535919605-1.png) 

# **Mode Rules**

- Players are assigned to different teams;
- Defeating enemy players earns points for the team;
- The team that reaches the set score first wins;
- Customizable respawn rules, time limits, kill scores, and more.
- This mode is suitable for creating gameplay such as **fast-paced gunfights, squad deathmatches, and score competitions**. It supports flexible adjustments to map structure and combat pacing, making it a common template for competitive map creation.

# **Common Mode Parameters**

**Team Assault** provides complete round combat logic and battle rule configuration, and supports the following key parameters:

| Parameter | Function Description |
| ------------ | ------------------------------------------ |
| Number of Rounds | Set the total number of rounds in a match. |
| Round Duration | Set the duration of each round. |
| Team Settings | The default is two teams, but you can manually reset the number of teams and team members. |
| Round Reset | Reset and refresh equipment at the start of each round. |
| **Score Settings** | **Set the victory points and kill points for each round.** |

![img](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/CLWiki2/MODE/wps2-1754535919605-2.png) 

# **Core Objects/Components**

- Spawn Point (must be placed):Both sides must have a suitable spawn area
- Obstacle structures: Use level objects to build shelters, walls, and other scenes
- Supply points: Place weapons, ammunition, medical kits, and other consumable items that can be picked up on the map (weapon points, ammunition points, consumable points, throwable points, armor points, scope points)
- Shop (vending machine): Players can purchase equipment in the shop
