# New Rank

## Related Resources

[Introduction to Historical Data Storage Modules](https://ffcraftland.garena.com/en/tutorial/fe/1-35/)

## Data Storage Module

Provides detailed information in the above resource. Here's a brief overview of the Data Storage Module.Data Storage is an optional module. When enabled, it allows map developers to utilize server-based data tables for data storage. It is primarily used for cross-map and cross-match data synchronization, Rank, and similar features. This article focuses on the new data storage tables specifically for Rank functionality.

### Access

Load the Data Storage module from the module list to begin configuring the column information for four types of data tables:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806162055343.png" alt="image-20250806162055343" style="zoom:67%;" /> 


## New Table Introduction

Like all data tables, each table requires you to specify a “Key” column, which serves as the primary key. Key column data must be unique and acts as the index for the entire table. By querying the Key, you can identify a specific data row within the table. When editing multiple rows with the same Key using a block, subsequent edits will always overwrite previous data.

### Rank Datasheet

A rank datasheet is a specialized multi-column table where you can define additional columns to store supplementary information such as points, survival time, total game duration, etc. However, a rank datasheet must include one column (the Value column) used for ascending or descending sorting.

![image-20250806170632723](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806170632723.png) 


Selecting UID as Key will automatically convert the Rank column into player cards:

![image-20250901154851187](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250901154851187.png) 

#### Table Example

Ranking datasheet1

| Rank | Key | Value | Custom Col1 | Custom Col2 | Custom Col…… |
| ---- | ------------ | ----- | -------------------------- | ----------- | ------------ |
| 1 | Player1 UUID | 100 | whatever you want to store | | |
| 2 | Player2 UUID | 90 | | | |

### Multi-column Data Table

Multi-column tables support storing multiple data columns (unlike previous single-column data tables). You can store various data types under a single Key. In the block script, APIs are provided to edit both Rank tables and associated multi-column data tables. When Keys match (e.g., both are player UUIDs), specific blocks can simultaneously edit both Rank tables and multi-column data tables.

![image-20250806170813281](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806170813281.png) 

#### Table Example

Multi-column Data Table1

| Key | Value | Custom Col1 | Custom Col2 | Custom Col…… |
| ------------ | ----- | -------------------------- | ----------- | ------------ |
| Player1 UUID | 100 | whatever you want to store | | |
| Player2 UUID | 90 | | | |



## Rank Feature

### Enabling the Feature

To enable the rank feature, you must activate the Data Storage module in your project and create at least one rank data table.

Once ready, edit the map you intend to publish in the [Creator Center](https://craftland.garena.com/) map publishing UI to access Rank settings:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806164442617.png" alt="image-20250806164442617" style="zoom: 67%;" /> 


Enabling this feature will display a Rank button on your map's details UI, allowing players to view the rank information you've edited:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806171313422.png" alt="image-20250806171313422" style="zoom:67%;" /> 

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806164728942.png" alt="image-20250806164728942" style="zoom:67%;" /> 


### Rank Editor

In the rank editor UI for published maps, you can currently select only one data table to display rank information. (Although you may use multiple tables to store data within the project)
<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806164912096.png" alt="image-20250806164912096" style="zoom:67%;" />


You can edit other aspects of the leaderboard: whether to display it outside the game, which columns to use for the leaderboard layout, and their order.

Selecting multiple languages allows you to manually edit the leaderboard title's multilingual information:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806173701944.png" alt="image-20250806173701944" style="zoom:67%;" /> 


Languages not filled in will use the default table column names.

After editing, the map information page will display a preview of your current Rank. Multilingual text will not appear in this preview:

![image-20250806165547462](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806165547462.png) 

## block

Use the block at appropriate times—such as when a player scores points or at the end of each match—to store data in the Rank data table.

![image-20250806165732042](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806165732042.png) 


Note: The `SheetName` parameter must reference a **leaderboard data sheet** block for the created **leaderboard data sheet** to be read.

To simplify editing the two multi-list tables introduced in this tutorial, a special Tuple data type has been added. This is a unique list format. The Tuple type automatically identifies values from specified data sheets or Rank data sheets to form a special list with elements of the designated data type.

![image-20250806174722968](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806174722968.png) 


The block primitive automatically reads all tables and uses the data type of each table's columns as the data type for its list items:

![image-20250806175459462](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806175459462.png) 


For Rank data tables, once a custom data column is created, the value will actually contain N columns of data, thus forming a tuple:

![image-20250806175601013](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806175601013.png) 

Therefore, in practical usage, tuples may become nested:

![image-20250806180055942](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806180055942.png) 


Tuple blocks do not automatically update table column names or other information. Therefore, any changes require manually refreshing the tuple block.

## Code

Code example:

1. Write

   ```go
   WriteDBLeaderboardAssociationValue(``“rank”``, ``‘test_uid_1’``, {``60``, ``“1:00”``}, ``“”``, out var c, out var d)
   ```

1. Read

   ```go
   ReadDBLeaderboardAssociationValue(“rank”, ‘test_uid_1’, out var data, “”, out var a, out var b)
   var data_normal List<object> = data[2] as List<object>
   LogWarning(data_normal[1])
### Related API List

1. SetTuple
2. GetTuple
3. WriteDBLeaderboardAssociationValue
4. RemoveFromLeaderboardDataStoreByKey
5. ReadDBLeaderboardAssociationValue
6. WriteToLeaderboardDataStore
7. RemoveFromLeaderboardDataStoreByKey
8. ReadFromLeaderboardDataStore

Specifically, for the function: ReadDBLeaderboardAssociationValue, its return value is a tuple:

**Result:** The type is **{rankname_value}Tuple**

- **{rank, key, value}**
- rank: int
- key: string
- value: tuple
- **{value, GameCompletionTime}**

For the function: WriteDBLeaderboardAssociationValue, the Key and Value parameters:

- **Key:** It is recommended to convert the player's UID into a string as the key, so that the player's callsign can be displayed in Craftland
- **Value:** The type is **{rankname} Tuple**. After selecting SheetName, double-click Value to quickly add the corresponding block
For more API parameters and documentation, refer to: [Official Documentation](https://ffcraftland.garena.com/en/docs/api)

## Local Debugging

During map editing, online player data is unavailable. However, Craftland Studio PC allows viewing debug-stored data via local JSON files.

![image-20250806170248163](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806170248163.png) 


After data is stored during debugging, clicking the option shown in the image will navigate to the local JSON folder. Data table information is saved in JSON format, allowing developers to verify the correctness of the logic.

![image-20250806170420358](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806170420358.png)
