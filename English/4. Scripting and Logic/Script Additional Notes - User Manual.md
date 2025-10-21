# Additional Notes to Scripts

Line-by-line instructions for some items: 

# Block scripts 

## Process control 

### **Conditional statements:** 

if: 

![image-20240719164745076](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719164745076.png)

Run the node under IF if the condition is met. Click on the + sign to add ELSE: if the condition is not met then run the node under ELSE: 

![image-20240719164848897](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719164848897.png)

Click + again to add ELSEIF, and continue to determine the next condition if it is not met.

![image-20240719164927953](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719164927953.png)

### Loop statement: 

Foreach: 

For each KEY in the parameter list/dictionary, execute the node below once.

![image-20240719165101469](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719165101469.png)

for index: 

Parameter i starts at the minimum value, and i increases in step value every time the node below is run, until i is greater than or equal to the maximum value.

![image-20240719165143465](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719165143465.png)

> The [min,max) interval of this node is left-closed and right-open, i.e., the node below will not be run that time when i is equal to the maximum value. As an example, this loop will run ten times, with i values from 0 to 9. 

while loop: 

![image-20240719165534132](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719165534132.png)

The loop will run for the node below as long as the condition is met.

break: 

![image-20240719170100109](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719170100109.png)

Interrupts the loop and continues to execute the node after the loop body.

continue: 

![image-20240719170413237](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240719170413237.png)

Skips this loop and moves to the next loop in the loop body.

# Code Script 

## Basic Syntax 

### Comments 

#### Single Line Comments 

```go 
// Single Line Comments 
```

#### Multi-Line Comments 

```go 
/* 

Multi-Line Comments 
Multi-Line Comments 

*/ 
```

#### Identifiers 

An identifier is used to define a user-defined item such as a variable, function, or type name. An identifier consists of a letter, number, or underscore, and cannot begin with a number.

##### keyword 

reserved keywords cannot be used as user-defined identifiers: 

| keyword      | description                                                  | example                                              |
| ------------ | ------------------------------------------------------------ | ---------------------------------------------------- |
| define       | Define basic type                                            | define AssetID : string                              |
| alias        | Define type alias, supports or, and expressions              | alias Number = int \| int64 \| float                 |
| enum         | Define enumeration                                           | enum SortType { AscIgnoreZero = 0 Desc = 1 Asc = 2 } |
| component    | define component                                             | component XXX{ ... }                                 |
| abstract     | modifier component definition, abstract component            | abstract component XXX { }                           |
| partial      | modifier component definition, extends component, adds properties to original component definition | partial component XXX { }                            |
| accept       | modifier type definition, other types that are accepted by the modifier type for assignment operations | [accept Vector3]                                     |
| combine      | modifier component definition, binds components              | [ combine Visibility]                                |
| graph        | define script                                                | graph XXX{ ... }                                     |
| import       | import script                                                | import “StdLibrary.fcc” as stdlibrary                |
| from         | partial import script                                        | import XXX from ” EditorGenLib.fcc”                  |
| static       | modifies script definition, static script                    | static graph XXX                                     |
| readonly     | modifies component property or variable, declares read-only  | [readonly]                                           |
| event        | defines or listens for event                                 | event OnAwake(){ ... }                               |
| func         | define function                                              | func Jump(){ ... }                                   |
| start        | asynchronous call function                                   | start Jump()                                         |
| wait         | synchronous call function                                    | wait Jump()                                          |
| async        | asynchronous function declaration                            | async func Jump( ) { ... }                           |
| var          | Define local variable                                        | var int num = 0                                      |
| out          | Declare if function formal parameter is an output parameter  | func Jump(var out speed){ ... }                      |
| as           | Type conversion                                              | var hpFloat = GetHP() as float                       |
| thisEntity   | refers to the current entity                                 | var hp = thisEntity<Player>.HP                       |
| globalEntity | refers to the global game entity                             | var tickCount = globalEntity<Globall>.TickCount      |
| typeof       | Get the value of type                                        | TypeIs(100, typeof(int))                             |

Other keywords: 

if, else, for, in, while, break, continue, return, 

object, bool, int, float, string, Vector2, Vector3, Quaternion, List, entity, 

true, false, nil 

### Member accessor 

The member accessor is `. `, with the following basic syntax for accessing an object member with a point: 

```golang 
Object. Members 
```

such as imported script libraries, enumeration types, component types, etc., can also be component members or script members on a specific instance, and so on.

### Accessing imported content 

Imported content is accessed in scripts as members via aliases, which are independent within each script.

Take the example of importing the standard library: 

```golang 
import “StdLibrary.fcc” as std 

graph HelloWorldGraph { 
	func SayHello(name string) { 
		//std is the alias of the standard library after import 
		std.LogInfo("Hi, ” + name)
	} 
} 
```

### Accessing component data 

Components are data that hangs on an entity, when accessing the data of a component on an entity object, the basic syntax is as follows: 

```golang 
entity object <component qualified>. Members 
```

As an example of accessing component data for the current entity: 

``` golang 
func EntityPropModify(input bool) bool { 
	thisEntity<Entity>.EnableLogic = input 
	return thisEntity<Entity>. EnableLogic 
} 
```

### Accessing script members 

Scripts are behaviors that hang on entities, and when accessing the members of a script on an entity object, the basic syntax is as follows: 

```golang 
EntityObject<script-qualified>. Members 
```

As an example of accessing the script of the current entity: 

```golang 
func MyFunc(){ 
// thisEntity is reserved word, referring to the current entity 
if HasScript(thisEntity, Helper) { 
	thisEntity<Helper>.MyHelpFunc() 
}else { 
	// dynamically hook script for entity 
	AddScript(thisEntity, Helper) 
	thisEntity<Helper>.MyHelpFunc() 
} 
} 
```



## Data types 

### Basic types 

#### object 

object is the base type of all types 

#### bool 

Boolean types have only two optional values: true and false 

```golang 
func Demo() { 
	var isOK1 = false 
	var isOK2 bool = true 
	if isOK1 || isOK2 { 
		//...
	} 
} 
```

#### int 

integer types range from “-2147483648” to “2147483647” 

```golang 
func Demo() { 
var num1 = 0 
var num2 int = 5 
if num1 > num2 { 
//...
} 
} 
```

#### float 

Fractional types range from approximately “-3.4e38” to “3.4e38” 

```golang 
func Demo() { 
	var num1 = 0.5 
	var num2 float = 5.6 
	if num1 > num2 { 
		//...
	} 
} 
```

#### string 

strings are represented by a pair of double quotes, and escape characters can be used when the table double quotes themselves are needed” 

```golang 
func Demo() { 
	var str1 = "Hi,"
	var str2 string = "Tim" 
	LogInfo(str1 + str2) 
} 
```

#### Vector2 

Two-dimensional vector consists of two floats representing X and Y 

```golang 
func Demo() { 
    var vec1 = Vector2{0, 0} 
    var vec2 Vector2 = Vector2{1, 1} 
    var vec3 = vec1 + vec2 
    LogInfo(vec3.Y) 
} 
```

#### Vector3 

A three-dimensional vector consists of three floats denoting X, Y, and Z 

```golang
func Demo() { 
    var vec1 = Vector3{0, 0, 0} 
    var vec2 Vector3 = Vector3{1, 1, 2} 
    var vec3 = vec1 + vec2 
    LogInfo (vec3.Z) 
} 
```

#### Quaternion 

Quaternion consists of four floats denoting X, Y, Z, and W 

```golang 
func Demo() { 
    var qua1 = Quaternion{0, 0, 0, 1} 
    var qua2 Quaternion = Quaternion{0, 0, 0, 1} LogInfo 0, 1} 
    LogInfo(qua1.W) 
    LogInfo(qua2) 
} 
```

#### Enum 

Enumeration is the concept of a collection of constant data, such as an attack style enumeration, which can contain options such as melee, shoot, and explode inside. Different enumeration types cannot be assigned to each other, even though they may have the same value, due to different semantics.

```golang 
func Demo() { 
    var element int = std.ItemGoodsIDType.AC80 
    if element == std.ItemGoodsIDType.AC80 { 
    	LogInfo("suc") 
    } 
} 
```

#### **Color**

The Color type is used to represent a color value and consists of the well sign # plus four sets of hexadecimal digits RR, GG, BB, and AA. Among them, RR, GG, BB represents the red, green, blue three color channel value, the range of decimal under the [0,255], 0 means that there is no the channel color, 255 means that the channel color is the brightest. AA represents the transparency, the range of decimal under the [0,255], 0 is completely transparent, 255 is completely opaque.

The standard assignment format for the Color type is the #RRGGBBAA format: 

```golang 
var a = #112233ff // #RRGGBBAA ==#112233ff 
```

You can omit the transparency, and use the #RRGGBB format, where the transparency is the default value of ff. 

```golang 
var a = #112233 // #RRGGBB ==#112233ff 
```

You can use the #RGBA format, where all three color channels and transparency are duplicates of their own values: 

```golang 
var a = #123f //#RGBA ==#112233ff 
```

You can also use the #RGB format, where transparency is omitted in the #RGBA format, where transparency is the default value of ff. 

``` golang
var a = #123 //#RGB ==#112233ff 
```

Color type assignment only accepts variables of the above four lengths, i.e., # plus 8, 6, 4, and 3 hexadecimal digits.

After assignment using # plus hexadecimal digits, the variable is of type Color.

We provide an interface that returns data of type Color: ColorRGB(int a, int b, int c). This interface accepts decimal RGB values as input and returns hexadecimal #RRGGBBAA standard color type values.

``` golang
var a = ColorRGB(255,255,255) 
```

Variable a is equal to #ffffffff at this point. 

Color variable values are case insensitive.

With the Free Fire Craftland Code plugin, you can activate the color preview and palette in VS Code by entering a legal value using the well sign # plus hexadecimal. Clicking on the color preview expands the color palette, and selecting the appropriate color in the palette automatically modifies the value.

![image-20240821115716695](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/04-Scripts/image-20240821115716695.png)

### Dynamic types 

#### List\<T> 

A list that represents a set of data, where T is the type of the elements in the list 

For example, List\<int>, which means it's a list of integers 

```golang 
func Demo() { 
    var allItems = List<object>{"a", "b"} 
    allItems[0] = "A" 
    LogInfo(allItems[0]) 
    for index, element in allItems{ 
    	LogInfo(element) 
    } 
} 
```

#### Map\<T1,T2> 

dictionary, denoting a set of key-value mapped data, where T1 is the type of the key and T2 is the type of the value 

e.g. Map\<string, int>, which means that this is a dictionary that looks up the value of int by string Key 

```golang 
func Demo() { 
    var allItems Map<string, int> = Map<string, int>{"a":1 , "b":2} 
    allItems["a"] = 2 
    LogInfo(allItems["a"]) 
    LogInfo(allItems) 
} 
```

#### entity\<T> 

entity, which denotes an object, where T is the type of the component the entity is attached to 

For example, entity\<Player>, which denotes this is an entity with a Player component 

```golang 
func Demo() { 
    thisEntity<Global>.EcoRoundMoney = 100 
    LogInfo(thisEntity<Global>.EcoRoundMoney) 

    RevivePlayer( thisEntity<Player>) 
} 
```

## Operators 

### Arithmetic operators 

Assume that the value of A is 10 and the value of B is 20. 

| Operators | Description | Examples          |
| --------- | ----------- | ----------------- |
| +         | Sum         | A + B outputs 30  |
| -         | Subtract    | A - B outputs -10 |
| \*        | Multiply    | A \* B Output 200 |
| /         | Divide      | B / A Output 2    |
| %         | Balance     | B % A Output 0    |
| ++        | Increment   | A++ Output 11     |
| --        | Subtract    | A- Output 9       |

### Relational operators

assumes that the value of A is 10 and that the value of B is 20. 

| Operators | Description                                                  | Examples          |
| --------- | ------------------------------------------------------------ | ----------------- |
| ==        | Check if two values are equal, if equal return True else return False | (A == B) is False |
| !=        | Check if two values are not equal, if not return True otherwise return False | (A != B) is True  |
| >         | Check if left value is greater than right value, if so return True else return False | (A > B) is False  |
| <         | Check if left value is less than right value, if so return True else return False | (A < B) is True   |
| >=        | Check if left value is greater than or equal to right value, if so return True Otherwise return False | (A >= B) is False |
| <=        | Checks if the left value is less than or equal to the right value, if so returns True otherwise returns False | (A <= B) is True  |

### Logical operators

assumes that the value of A is True and the value of B is False. 

| Operator | Description                                                  | Example           |
| -------- | ------------------------------------------------------------ | ----------------- |
| &&       | The logical AND operator. Conditional True if both operands are True, False otherwise | (A && B) is False |
| \|\|     | Logical OR operator. Condition True if one of the operands on either side is True, False otherwise | (A \|\|B) is True |
| !        | logical NOT operator. If the condition is True, then the logical NOT condition False, otherwise True | !(A && B) is True |

### Assignment Operators 

| Operators | Description                                      | Examples                                                 |
| --------- | ------------------------------------------------ | -------------------------------------------------------- |
| =         | Assigns the value of an expression to a variable | C = A + B assigns the result of an A + B expression to C |
| +=        | Adds and assigns                                 | C += A equals C = C + A                                  |
| -=        | Subtracts and assigns                            | C -= A equals C = C - A                                  |
| \*=       | Multiplies and assigns                           | C \*= A equals C = C * A                                 |
| /=        | Divides and assigns                              | C /= A equals C = C / A                                  |
| %=        | Modulus and assigns                              | C %= A equals C = C % A                                  |
| &=        | Bitwise AND and assigns                          | C &= A equals C = C & A                                  |
| \|=       | Bitwise OR and assigns                           | C \|= A equals C = C \| A                                |
| ^=        | Bitwise XOR and assigns                          | C ^= A equals C = C ^ A                                  |
| <<=       | Left shift and assigns                           | C <<= A equals C = C << A                                |
| >>=       | Right shift and assigns                          | C >>= A equals C = C >> A                                |

## Bitwise Operators

Bitwise operators apply only to integer (`int`) type values.

| Operator | Description                                                  | Example                                           |
| -------- | ------------------------------------------------------------ | ------------------------------------------------- |
| &        | Bitwise AND operator. Compares each binary bit of two numbers; if both corresponding bits are 1, the result bit is 1, otherwise 0. | A & B                                             |
| \|       | Bitwise OR operator. Compares each binary bit of two numbers; if at least one corresponding bit is 1, the result bit is 1, otherwise 0. | A \| B                                            |
| ^        | Bitwise XOR (exclusive OR) operator. Compares each binary bit of two numbers; if the corresponding bits are different, the result bit is 1, otherwise 0. | A ^ B                                             |
| ~        | Bitwise NOT operator. Inverts each binary bit of a number; turns 0s into 1s and 1s into 0s. | ~A                                                |
| <<       | Left shift operator. Shifts the binary bits of a number to the left by a specified number of positions; high bits are discarded, and low bits are filled with zeros. | A << 2 equals A multiplied by 2 to the power of 2 |
| >>       | Right shift operator. Shifts the binary bits of a number to the right by a specified number of positions; high bits are filled with the sign bit. | A >> 2 equals A divided by 2 to the power of 2    |



### Operator Priority 

Some operators have a higher priority than others, and the binary operators all operate from left to right. The following table lists all operators and their priorities, from top to bottom, representing highest to lowest priority: 

| Priority | Operator                                                     |
| -------- | ------------------------------------------------------------ |
| highest  | + (Unary plus operator)、- (Unary minus operator)、!、~      |
|          | *、 /、 %                                                    |
|          | + (Binary addition operator)、 - (Binary subtraction operator) |
|          | <<、>>                                                       |
|          | &                                                            |
|          | ^                                                            |
|          | \|                                                           |
|          | == 、!=、 <、 <=、 >、>=                                     |
|          | &&                                                           |
| lowest   | \|\|                                                         |

### Process Control 

### Conditional Statements 

Conditional statements require the developer to decide whether or not to execute the specified statement by specifying one or more conditions and testing the condition to see if the condition is true, and executing another statement if the condition is false.

```golang 
func Max(left Number, right Number) Number { 
    if left > right { 
    	return left 
    }else if left < right { 
    	return right 
    } else{ 
    	return left 
    } 
} 
```

#### Loop Statements 

In quite a number of In many real-world problems, there are a lot of repetitive operations with regularity, so it is necessary to repeat certain statements in a program.

#### for index 

```golang 
func OddNumSumV1(max int) int { 
	var sum = 0 
	for i = 1, max, 2 { 
		sum += i 
	} 
	return sum 
} 
```

#### for range 

```golang 
func SumOfPrimesUpTo10V3() int { 
    var sum = 0 
    var nums = List<int>{2, 3, 5, 7} 
    for i, num in nums { 
    	sum += num 
    } 
    return sum 
} 
```

#### while 

```golang 
func OddNumSumV2( max int) int { 
    var sum = 0 
    var loopIndex = 0 
    while loopIndex < max { 
    	loopIndex = loopIndex + 1 
    	sum += loopIndex 
    } 
    return sum 
} 
```
