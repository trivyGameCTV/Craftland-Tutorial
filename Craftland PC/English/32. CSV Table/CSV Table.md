# CSVTable

When a large amount of configuration data needs to be used, it is inconvenient to use variables for everything. We can use CSV tables to manage configuration data in bulk.

# CSV table

![image-20241030160607322](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/28-CSVTable/image-20241030160607322.png)

The basic unit of a CSV table is a cell, and a row or column of cells constitutes a row or column. The number of rows and columns both start with 1. For example, in the figure, the row and column numbers of the “Key” field are both 1, and the column number and row number of the “200” field are 3 and 3 respectively.

In Craftland Studio PC, we specify that the first line of a CSV table is the column name, and the second line is the type of value. If the second line is filled in legally, the retrieved value will automatically be assigned the corresponding type. Currently, the following data types are supported for the second line:

1. string
2. int
3. float
4. bool

The above data types are not case sensitive.

The default data type is string. If an unrecognized data type is entered in the second row or left blank, the data in the third row and below in the column will be considered to be of type string.

If data of a data type that does not meet the requirements in the second row is entered in a data row from the third row onwards, it will be considered to be the default value of that data type. In some special cases, it will be considered to be a special value, such as an out-of-range value entered for an int type.

In Craftland Studio PC, you can read the data in the CSV table that has been imported into the project and locate the row and column where a certain data is located within the script. However, editing the CSV table must be done outside the editor.

# Importing a CSV table

To use a CSV table in your project, you first need to import the prepared CSV table.

Save the data in the figure above to a CSV table named test and import it into the game project:

![image-20241030145927221](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/28-CSVTable/image-20241030145927221.png)

![image-20241030145941299](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/28-CSVTable/image-20241030145941299.png)

Although you can save multiple csv tables with the same name in different directories, it is not recommended to have duplicate csv table names. This is because when reading the csv table using blocks, for example, only the file name is displayed. Although the program will distinguish between your files at runtime, this is very inconvenient for editing.

![image-20241030151823596](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/28-CSVTable/image-20241030151823596.png)

![image-20241030150344129](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/28-CSVTable/image-20241030150344129.png)

> If there are two csv tables with the same name, their paths must be different.

You can avoid duplicate table names by storing the csv tables in the same folder.

# Reading CSV tables

## Read the entire table

![image-20241030151855629](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/28-CSVTable/image-20241030151855629.png)

When the entire table is read, the return value is a two-dimensional array, with each row of information forming an array that is sequentially used as an element of the entire table array, including the column name row and data type row (rows 1 and 2).

![image-20241030162150418](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/28-CSVTable/image-20241030162150418.png)

If the returned data is used as an array, the index starts from 0, which is different from the following script when retrieving rows and columns in the csv, where the sequence number starts from 1.

![image-20241030153359550](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/28-CSVTable/image-20241030153359550.png)

![image-20241030162058111](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/28-CSVTable/image-20241030162058111.png)

## Read by row and column

![image-20241030153550793](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/28-CSVTable/image-20241030153550793.png)

When reading a CSV table row and column, a list of the rows or columns is returned. The numbering of rows and columns starts at 1.

![image-20241030162324195](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/28-CSVTable/image-20241030162324195.png)

### Reading rows by key

You can retrieve an entire row by specifying the column as the key.

![image-20241030162801059](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/28-CSVTable/image-20241030162801059.png)

![image-20241030162815093](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/28-CSVTable/image-20241030162815093.png)

**Note**: The column used as the key needs to ensure that the values are unique. Usually, the ID column is used as the key column. If there is duplicate data in the key column, only the data found in the first row will be returned.

![image-20241030162916122](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/28-CSVTable/image-20241030162916122.png)

![image-20241030162930986](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/28-CSVTable/image-20241030162930986.png)

In addition, when retrieving data rows using the Key, only data after the third row will be retrieved.

## Read the specified cell

![image-20241030163048093](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/28-CSVTable/image-20241030163048093.png)

![image-20241030163126238](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/28-CSVTable/image-20241030163126238.png)

If the data exceeds the limits of the data type, such as the maximum int value of 2147483647 (2^31-1), the value will still be returned, but it may not be as expected. For example, if the int value exceeds the upper limit, it will restart counting from the minimum value of -2147483648.

![image-20241030163312371](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/28-CSVTable/image-20241030163312371.png)

![image-20241030163353083](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/28-CSVTable/image-20241030163353083.png)

If the value entered does not meet the requirements of the data type, the default value for that data type is returned.

![image-20241030163753450](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/28-CSVTable/image-20241030163753450.png)

![image-20241030163806690](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/28-CSVTable/image-20241030163806690.png)

# Retrieving CSV tables

You can retrieve the number of the specified cell or column by using the column name, which is the data in the first row of the CSV table.

![image-20241030164052368](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/28-CSVTable/image-20241030164052368.png)
![image-20241030164109678](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/28-CSVTable/image-20241030164109678.png)

![image-20241030164157954](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/28-CSVTable/image-20241030164157954.png)
![image-20241030164313967](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/28-CSVTable/image-20241030164313967.png)
