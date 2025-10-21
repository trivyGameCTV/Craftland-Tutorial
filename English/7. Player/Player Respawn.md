# Player Respawn

# Customize Player Respawn Time

Open *GlobalSpawn.eca*

In the **Init** function, change the **RespawnTime** to the duration you want player to wait after being eliminated. For example, if creator want player to wait 3 seconds after respawn, set it to 3000 (miliseconds)

<img src = "https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/1-FFA/respawn.png">

# Customize Player Invincible Time
Open *GlobalSpawn.eca*

In the **Init** function, change the **InvincibleTime** to the duration you want player to be invincible after revived. For example, if creator want player to be invincible for 4 seconds after respawn, set it to 4000 (miliseconds)

<img src = "https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/1-FFA/respawn.png">

# Developing Tutorial
When the map is selected, we need to store the spawnpoint list as a varible.

Create a **GetRandomSpawn** function to get a random spawnpoint from the stored spawnpoint list.

Create a **SpawnPlayer** function to use when ever player is eliminated.

Call the **SpawnPlayer** function when player is eliminated.

<img src = "https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/Template/1-FFA/global-spawn.png"