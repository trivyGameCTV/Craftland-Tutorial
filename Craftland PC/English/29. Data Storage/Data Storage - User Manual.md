# Data Storage

Data Storage can store data outside the game process and can be used for functions such as archiving, rankings, statistics, and storing game settings.

Data Storage can also share data between different games on the same map.

# Load the Data Storage Module

To use Data Storage, you need to load the Data Storage module first. This is an optional module, and unloading it will cause the previously used related primitives, code, and configurations to become invalid.

![image-20240902154318437](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20240902154318437.png)

# Categories

After loading the data storage module, you will see three configurations: ranking data storage, statistical data storage, and general data storage.

![image-20240902155047574](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20240902155047574.png)

Tables created by the data storage cannot be viewed directly, but the table styles are described in this document.

## Normal data storage

### Parameter description

![image-20240903161258145](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20240903161258145.png)

Add parameters to the normal data storage. Each parameter represents a data table. Each parameter has the following configurable items:

**Table name**: the name of the created table

**Data type**: the data type accepted in the table

It can be found that each data table only accepts input of one data type.

### Table format

DataSheetName

| UUID | Key  | Value |
| ---- | ---- | ----- |
|      |      |       |

**DataSheetName**: The name of the table added in the data storage module.

**UUID**: The unique ID of the player. When writing data, the UUID of the current player needs to be entered.

**Key**: The index created by the script when performing data storage operations.

**Value**: The value filled in by the script when performing data storage operations, which only accepts the types set in the data storage module.

### Usage scenarios

Used for player archiving.

For other scenarios where the data in this table can be used.

## Ranking datastore

### Parameter description

![image-20240903162353099](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20240903162353099.png)

Similar to the structure of a normal data storage, but the ranking data storage only accepts Int type input and provides an additional sorting function. The data in the ranking data storage table will be arranged in the order you configure.

**Table name**: the name of the table created.

**Sorting method**: select whether to sort the entered Int values in ascending or descending order.

### Table style

**DataSheetName**

| Ranking | Key  | Value(Only Int) |
| ------- | ---- | --------------- |
| 1       |      |                 |
| 2       |      |                 |
| 3       |      |                 |

The ranking data storage does not have a UUID, but supports a custom KEY, and only accepts Int-type input for the value. The ranking data storage will sort the entire table based on the data in the value column.

### Usage scenarios

Player rankings, such as kill rankings, point rankings, and racing rankings.

## Statistics storage

### Parameter description

![image-20240903163809392](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20240903163809392.png)

Similar to the structure of a normal data storage, but the statistics data storage also only accepts Int input and must have a preset Key.

**Table name**: the name of the table to be created.

**Key management**: a list of predefined keys.

### Table format

DataSheetName

| **Key**  | **Value (Only Int)** |
| -------- | -------------------- |
| **KEY1** |                      |
| **KEY2** |                      |

The statistics data storage does not have a UUID, and all information with the same key is stored under the same data.

**Key**: the default index.

**Value**: the value, which can only be Int data.

### Usage scenarios

Statistics for the entire service, such as the total number of bosses killed and the total amount of money spent.

# Usage

## Adding and modifying

Adding a data entry to a data storage table is the same as modifying a data entry, and both use the write primitive.

![image-20240903182410828](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20240903182410828.png)

For ranking data storage and statistical data storage, you need to use the corresponding elements.

![image-20240903182534045](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20240903182534045.png)

## Delete

Delete a data record using the delete element.

![image-20240903183709409](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20240903183709409.png)

Different types of data storage use different data indexes.

![image-20240903184115941](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20240903184115941.png)

Statistical data storage does not support deleting entire rows because the keys are set in advance. Only the values corresponding to the keys can be modified.

## Query

To query data, you need to use the read operation. Different types of data stores use different indexes.

![image-20240903184158672](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20240903184158672.png)

![image-20240903184225595](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20240903184225595.png)

In the ranking data storage, multiple rows of data can be retrieved at once based on the ranking, and the data is returned in a list format.

![image-20240905155430325](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20240905155430325.png)

## Batch query

We provide a batch query API to read more data at one time.

![image-20250121160153530](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250121160153530.png)

You must fill in the same number of Account IDs and Keys to return the data of the corresponding entries.

For the following table

| UUID | Key | Value |
| ---- | ---- | ------ |
| 111 | key1 | value1 |
| 222 | key2 | value2 |
| 333 | key3 | value3 |

Required input:

![image-20250121160922575](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250121160922575.png)

Result returned: {value1, value2, value3}

If the number or order of input parameters does not match, unexpected results may be returned.

# Usage restrictions

The data storage has some usage restrictions.

1. There is a limit on read and write operations per minute, supporting 60 read operations and 75 write operations per minute. When using the data storage, you need to minimize the frequency of read and write operations and check whether the read and write operations are successful.
2. The maximum size of a key value stored in the data storage is 4k.
3. The maximum number of rows that can be stored in each table in the ranking data storage is 150, and no additional data will be recorded at all.
4. The maximum number of tables that can be created in the statistical data storage is 120.

# Data center

Published custom maps with data storage enabled can be viewed in the data center:

![image-20240904142856003](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20240904142856003.png)

Open the data storage for the corresponding map to view the data currently stored for the map:

![image-20240904143215503](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20240904143215503.png)

In the data center, the data is displayed in tabular form, allowing you to visually view the various data stores:

![image-20240904143742323](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20240904143742323.png)

![image-20240904143759543](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20240904143759543.png)

In the Ranking Data Storage and Statistics Data Storage, you can set up regular data deletion:

![image-20240904143845497](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20240904143845497.png)

![image-20240904145512656](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20240904145512656.png)

In the data center, ranking data and statistics can be queried by entering Key or Value:

![image-20240905155637099](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20240905155637099.png)

However, to query a normal data table, you must enter both the UID and the Key:

![image-20240905155720217](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20240905155720217.png)

Fuzzy search is not supported for queries in the data center.

Changes can also be made directly to stored data in the data center:

![image-20240905155912501](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20240905155912501.png)

# Example

The following is a simple example of how to use data storage to archive player data.

We plan to create a simple mini-game where the player gets 1 point for each time they hit the target cylinder.

In the archive, we will record the player's position, orientation, and points, and the player will inherit the data in the archive when they enter the map again.

## Creating the game

First, create a simple game:

Place a target cylinder in the scene and add three decorations for positioning:

![image-20240904145226220](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20240904145226220.png)

The player gains 1 point for each hit on the white cylinder, and the player's current points are displayed on the custom UI:

![image-20240904152614172](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20240904152614172.png)

## Creating an archive

In this example, we only store the player's position, orientation and the player's score.

The points have been set as a custom attribute of the player, and all three pieces of data can be obtained from the player entity.

The data types of the position and orientation are Vector3, and the data type of the points is Int. Try to avoid using multiple tables to store player data, because each additional table will increase the number of data reads and writes for the player. To avoid exceeding the usage limit, we store two different types of data in the archive table as a list of any type.

Select Normal data storage for data storage and set the accepted value type to List of any type.

You can also store data using any type and separate it into three keys, but position and orientation are often used together. Here, a list is used to store both data as the player's initial position and orientation information.

![image-20240904160024238](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20240904160024238.png)

In the global script:

Save the player at the end of each game round and when the player quits:

![image-20240904162233250](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20240904162233250.png)

When the player joins, set their points, position and orientation as the archived data, and display the current player's points in the UI that displays the points.

![image-20240905163436774](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20240905163436774.png)

If the data fails to be read for some reason, a read failure handling needs to be added, and here only the failure error is printed:

![image-20240905163445878](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20240905163445878.png)

Run the game with two debug clients:

![image-20240904162520514](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20240904162520514.png)

![image-20240904162502315](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20240904162502315.png)

After gaining a certain number of points, exit the game, then re-enter, and you will find that the exiting player's points and position are the same as before exiting.

At the end of the round, the player data is normally saved, so if you wait until the game naturally ends, and then turn on debugging, the player's points and position before the game is closed will be the same.

# Locally view data storage

Data storage is used for published maps and can normally only be viewed in the data center.

However, we provide a developer tool for local testing:

![image-20240904164139928](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20240904164139928.png)

After you have used data storage in your project and have already stored data, clicking this option will open a local file browser with a generated .jason file:

![image-20240904164246223](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20240904164246223.png)

If no data storage has been used or no data has been stored in the data storage, a message will be displayed saying that the file does not exist:

![image-20240904165514472](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20240904165514472.png)

This .jason file is exported from the data storage and can be used to check the stored data:

![image-20240904164357173](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20240904164357173.png)

> A part of the player's saved game stored in the example above

This .jason file's data is the data source for local debugging. Legitimately modifying the .jason file will directly change the data stored in the data storage read in the game.

![image-20240904164653457](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20240904164653457.png)

![image-20240904164734872](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20240904164734872.png)
