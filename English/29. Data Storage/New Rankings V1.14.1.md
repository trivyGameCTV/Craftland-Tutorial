# New Rankings - Internal

## Related Information

[Introduction to the data storage module for historical versions: Simplified Chinese](https://ffcraftland-pre.garena.com/zh-cn/tutorial/fe/1-35/)

[Introduction to the data storage module for historical versions: English](https://ffcraftland.garena.com/en/tutorial/fe/1-35/)

[Introduction to the data storage module in previous versions: Vietnamese](https://ffcraftland.garena.com/vn/tutorial/fe/1-35/)

The English and Vietnamese translations are based on Google Translate results for the simplified Chinese version, and their accuracy is questionable.



## Data storage module

The above information provides a detailed introduction to the data storage module. Here is a brief introduction.Data storage is an optional module that, when enabled, allows map developers to use data tables located on the server for data storage. It is mostly used for cross-map and cross-game synchronization of data information, rankings, and other functions. This article will focus on the use of the new data storage table for the ranking function.

### Entry

Load the data storage module from the module list to start configuring the column information for the four data tables:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806162055343.png" alt="image-20250806162055343" style="zoom:67%;" />

## Introduction to new tables

As with all data tables, you need to specify a “Key” column for each table, which is the primary key of the table. The data in the Key column must be unique and is the index column for the entire table. By searching for the Key, you can determine the specified data row of the specified table. When you edit the same Key multiple times using blocks, the data edited later will always overwrite the previous data.

### Ranking datasheet

A ranking table is a special multi-list table where you can customize several columns to store additional information, such as points, survival time, total game time, etc. However, a ranking table must have a column (Value column) used for ascending or descending sorting.

![image-20250806170632723](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806170632723.png)

Select UID as Key, and the ranking will automatically convert the Key column to player cards:

![image-20250806170721219](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806170721219.png)

#### Table example

Ranking datasheet1

| Rank | Key | Value | Custom Col1 | Custom Col2 | Custom Col… |
| ---- | ------------ | ----- | -------------------------- | ----------- | ------------ |
| 1 | Player1 UUID | 100 | whatever you want to store | | |
| 2 | Player2 UUID | 90 | | | |

### Multi-column Data Table

A multi-list is a table that supports multiple columns of data (unlike the previous data table, which only supports one column of data). You can store multiple types of data under one key. In the block script, there is also an API for editing ranking tables and associated tables. When the keys are the same (for example, both are player UUIDs), you can edit the ranking table and multi-column data table together using a specific block.

![image-20250806170813281](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806170813281.png)

#### Table example

Multi-column Data Table1

| Key | Value | Custom Col1 | Custom Col2 | Custom Col… |
| ------------ | ----- | -------------------------- | ----------- | ------------ |
| Player1 UUID | 100 | whatever you want to store | | |
| Player2 UUID | 90 | | | |



## Rankings Function

### Enable Function

To enable the rankings function, you must enable the data storage module in your project and create at least one rankings data table.

Once you are ready, edit the map to be released in the [Creator Center](https://craftland.garena.com/) release map UI to see the leaderboard settings:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806164442617.png" alt="image-20250806164442617" style="zoom: 67%;" />

Enable this feature, and a ranking button will appear on your map details UI, where players can browse the ranking information you have edited:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806171313422.png" alt="image-20250806171313422" style="zoom:67%;" />

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806164728942.png" alt="image-20250806164728942" style="zoom:67%;" />

### Edit Rankings

In the map rankings editing UI above, you can only select one data table as the rankings information to be displayed (although you can use multiple tables to store data in the project).

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806164912096.png" alt="image-20250806164912096" style="zoom:67%;" />

Then you can edit other contents of the ranking: whether to display the ranking outside the table, which columns to use as the ranking style, and their order.

Select multiple languages, and you can manually edit the multilingual information of the ranking title:

<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806173701944.png" alt="image-20250806173701944" style="zoom:67%;" />

Languages that are not filled in will use the default table column names.

After editing, your current ranking will be displayed on the map information page. Multiple languages will not be displayed in the summary:

![image-20250806165547462](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806165547462.png)

## Internal image transfer tool

In addition, you can also edit the ranking table in the internal image transfer tool, which is similar to the data center:



<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250808170839804.png" alt="image-20250808170839804" style="zoom:67%;" />



<img src="https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250808170852777.png" alt="image-20250808170852777" style="zoom: 67%;" />

## Blocks

Use blocks at appropriate times, such as when a player scores or at the end of each game, to store data in the ranking table.

![image-20250806165732042](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806165732042.png)

Note that it must be a block related to the ranking table, otherwise the SheetName parameter will not read the created ranking data table.

In order to make it easier to edit the two multi-list tables introduced in this tutorial, a special list type called Tuple has been added. The Tuple type supports automatic recognition of the value of a specified data table or ranking data table to form a special list of a specified data type.

![image-20250806174722968](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806174722968.png)

The tuple block automatically reads all tables and uses the data types of the table columns as the data types of the list items:

![image-20250806175459462](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806175459462.png)

For ranked data tables, once a custom data column is created, the value will actually contain N columns of data, so it will also form a tuple:

![image-20250806175601013](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806175601013.png)

Therefore, in actual use, tuples may be nested:

![image-20250806180055942](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806180055942.png)

The tuple block does not automatically update information such as table column names, so once a change occurs, you need to manually refresh the tuple block.

## Code

Code example:

1. Write

   ```go
   WriteDBLeaderboardAssociationValue(``“rank”``, ``‘test_uid_1’``, {``60``, ``“1:00”``}, ``“”``, out var c, out var d)
   ```

1. Read

   ```go
   ReadDBLeaderboardAssociationValue(``"rank"``, ``"test_uid_1"``, out var data, ``""``, out var a, out var b)``var data_normal List<object> = data[``2``] as List<object>``LogWarning(data_normal[``1``])
   ```



### Related API list

1. SetTuple
2. GetTuple
3. WriteDBLeaderboardAssociationValue
4. RemoveFromLeaderboardDataStoreByKey
5. ReadDBLeaderboardAssociationValue
6. WriteToLeaderboardDataStore
7. RemoveFromLeaderboardDataStoreByKey
8. ReadFromLeaderboardDataStore

Special note for the function ReadDBLeaderboardAssociationValue: its return value is a tuple:

**Result:** The type is **{rankname_value}Tuple**: 

**{rank, key, value}**

- rank: int
- key: string
- value: tuple
  - **{value, GameCompletionTime}**

For the function: WriteDBLeaderboardAssociationValue, for the parameters Key and Value:

- **Key:** It is recommended to convert the player's UID into a string as the key, so that the player's callsign can be displayed in craftland
- **Value:** The type is **{rankname} Tuple**. After selecting SheetName, double-click Value to quickly add the corresponding block

For more API parameters and descriptions, please refer to: [Official Documentation](https://ffcraftland.garena.com/en/docs/api)



## Local Debugging

When editing maps, you cannot obtain data from online players, but Craftland Studio PC provides a way to view debugging data stored locally via JSON.

![image-20250806170248163](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806170248163.png)

After data is stored during debugging, click the option shown in the image to navigate to the local JSON folder. The data table information is stored in JSON format, allowing developers to verify the logic.

![image-20250806170420358](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/29-DataStorage/image-20250806170420358.png)
