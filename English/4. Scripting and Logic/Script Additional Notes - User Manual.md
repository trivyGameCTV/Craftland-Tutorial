# Script Additional Notes - User Manual

Detailed explanations for certain items:

## Element Script

### Flow Control

#### **Conditional Statements:**

if:

![image-20240719164745076](./img/image-20240719164745076.png)

Execute the nodes under IF if the condition is met. Click the + sign to add ELSE: Execute the nodes under ELSE if the condition is not met:

![image-20240719164848897](./img/image-20240719164848897.png)

Click + again to add ELSEIF, and continue to evaluate the next condition if not met.

![image-20240719164927953](./img/image-20240719164927953.png)

#### Loop Statements:

Foreach:

Execute the nodes below for each KEY in the parameter list/dictionary.

![image-20240719165101469](./img/image-20240719165101469.png)

for index:

The parameter i starts from the minimum value, and with each execution of the nodes below, i increases by the step value until i is greater than or equal to the maximum value.

![image-20240719165143465](./img/image-20240719165143465.png)

> The range [min, max) for this node is left-inclusive and right-exclusive, meaning the nodes below will not execute when i equals the maximum value. In the example shown, this loop will run ten times with i values from 0 to 9.

while loop:

![image-20240719165534132](./img/image-20240719165534132.png)

As long as the condition is met, it will repeatedly execute the nodes below.

break:

![image-20240719170100109](./img/image-20240719170100109.png)

Interrupts the loop and continues executing the nodes after the loop body.

continue:

![image-20240719170413237](./img/image-20240719170413237.png)

Skips this iteration and proceeds to the next iteration of the loop body.

## Code Script

### Basic Syntax

#### Comments

##### Single-line Comment

```go
// Single-line comment
```

##### Multi-line Comment

```go
/* 

Multi-line comment
Multi-line comment

 */
```

##### Identifiers

Identifiers are used to define variables, functions, type names, etc. They consist of letters, numbers, and underscores and cannot start with a number.

##### Keywords

Reserved keywords cannot be used as user-defined identifiers:

| Keyword      | Description                                           | Example                                              |
| ------------ | ----------------------------------------------------- | ---------------------------------------------------- |
| define       | Define a basic type                                   | define AssetID : string                              |
| alias        | Define a type alias, supporting OR/AND expressions    | alias Number = int \| int64 \| float                 |
| enum         | Define an enumeration                                 | enum SortType { AscIgnoreZero = 0 Desc = 1 Asc = 2 } |
| component    | Define a component                                    | component XXX{ … }                                   |
| abstract     | Decorate component definition as abstract             | abstract component XXX { }                           |
| partial      | Decorate component definition to extend it            | partial component XXX { }                            |
| accept       | Decorate type definition for acceptable types         | [accept Vector3]                                     |
| combine      | Decorate component definition to bind components      | [combine Visibility]                                 |
| graph        | Define a script                                       | graph XXX{ … }                                       |
| import       | Import a script                                       | import "StdLibrary.fcc" as stdlibrary                |
| from         | Partially import a script                             | import XXX from "EditorGenLib.fcc"                   |
| static       | Decorate script definition as static                  | static graph XXX                                     |
| readonly     | Declare component properties or variables as read-only| [readonly]                                           |
| event        | Define or listen to events                            | event OnAwake(){ … }                                 |
| func         | Define a function                                     | func Jump(){ … }                                     |
| start        | Asynchronous function call                            | start Jump()                                         |
| wait         | Synchronous function call                             | wait Jump()                                          |
| async        | Declare an asynchronous function                      | async func Jump(){ … }                               |
| var          | Define a local variable                               | var int num = 0                                      |
| out          | Declare function parameters as output parameters      | func Jump(var out speed){ … }                        |
| as           | Type conversion                                       | var hpFloat = GetHP() as float                       |
| thisEntity   | Refer to the current entity                           | var hp = thisEntity<Player>.HP                       |
| globalEntity | Refer to global game entity                           | var tickCount = globalEntity<Globall>.TickCount      |
| typeof       | Get type value                                        | TypeIs(100, typeof(int))                             |

Other keywords:

if, else, for, in, while, break, continue, return,

object, bool, int, float, string, Vector2, Vector3, Quaternion, List, entity,

true, false, nil

#### Member Access Operator

The member access operator is `.`, and its basic syntax is accessing object members via dot notation:

```golang
object.member
```

For example, imported script libraries, enum types, component types can be accessed in this way. It can also be used on specific instances for component or script members.

#### Access Imported Content

Imported content is accessed through aliases in scripts. Each script has independent aliases.

For example, importing a standard library:

```golang
import "StdLibrary.fcc" as std

graph HelloWorldGraph {
    func SayHello(name string) {
        //std is the alias after importing the standard library
        std.LogInfo("Hi, " + name)
    }
}
```

#### Access Component Data

Components are data attached to entities. When accessing data on an entity's components, use the following basic syntax:

```golang
entityObject<componentQualifier>.member
```

For example, accessing component data of the current entity:

```golang
func EntityPropModify(input bool) bool {
    thisEntity<Entity>.EnableLogic = input
    return thisEntity<Entity>.EnableLogic
}
```

#### Accessing Script Members

Scripts are behaviors attached to entities. When accessing a script's member on an entity object, the basic syntax is as follows:

```golang
EntityObject<ScriptQualifier>.Member
```

For example, accessing the script of the current entity:

```golang
func MyFunc(){
    //thisEntity is a reserved word, referring to the current entity
    if HasScript(thisEntity, Helper) {
        thisEntity<Helper>.MyHelpFunc()
    } else {
        //Dynamically attach a script to the entity
        AddScript(thisEntity, Helper)
        thisEntity<Helper>.MyHelpFunc()
    }
}
```

### Data Types

#### Basic Types

##### object

The object is the base type for all types.

##### bool

Boolean type has only two possible values: true and false.

```golang
func Demo() {
    var isOK1 = false
    var isOK2 bool = true
    if isOK1 || isOK2 {
        //...
    }
}
```

##### int

The integer type has a range from "-2147483648" to "2147483647".

```golang
func Demo() {
    var num1 = 0
    var num2 int = 5
    if num1 > num2 {
        //...
    }
}
```

##### float

The float type has a range approximately from "-3.4e38" to "3.4e38".

```golang
func Demo() {
    var num1 = 0.5
    var num2 float = 5.6
    if num1 > num2 {
        //...
    }
}
```

##### string

Strings are represented by a pair of double quotes. To represent double quotes themselves, use the escape character `"`.

```golang
func Demo() {
    var str1 = "Hi, "
    var str2 string = "Tim"
    LogInfo(str1 + str2)
}
```

##### Vector2

A 2D vector is composed of two floats representing X and Y.

```golang
func Demo() {
    var vec1 = Vector2{0, 0}
    var vec2 Vector2 = Vector2{1, 1}
    var vec3 = vec1 + vec2
    LogInfo(vec3.Y)
}
```

##### Vector3

A 3D vector is composed of three floats representing X, Y, and Z.

```golang
func Demo() {
    var vec1 = Vector3{0, 0, 0}
    var vec2 Vector3 = Vector3{1, 1, 2}
    var vec3 = vec1 + vec2
    LogInfo(vec3.Z)
}
```

##### Quaternion

A quaternion is composed of four floats representing X, Y, Z, and W.

```golang
func Demo() {
    var qua1 = Quaternion{0, 0, 0, 1}
    var qua2 Quaternion = Quaternion{0, 0, 0, 1}
    LogInfo(qua1.W)
    LogInfo(qua2)
}
```

##### Enum

An enum is a concept of a collection of constant data. For example, an attack mode enum can include options like melee, shooting, explosion, etc. Different enum types cannot be assigned to each other even if their values might be the same due to differing semantics.

```golang
func Demo() {
    var element int = std.ItemGoodsIDType.AC80
    if element == std.ItemGoodsIDType.AC80 {
        LogInfo("suc")
    }
}
```

##### **Color**

The Color type represents color values and consists of a hash # followed by four groups of hexadecimal digits: RR, GG, BB, AA. RR, GG, and BB represent the red, green, and blue channels respectively with a range of [0,255] in decimal. A value of 0 means no color in that channel while 255 means the channel is at its brightest. AA represents transparency with a range of [0,255] in decimal where 0 is fully transparent and 255 is fully opaque.

The standard format for assigning Color type is #RRGGBBAA:

```golang
var a = #112233ff   //#RRGGBBAA == #112233ff
```

You can omit transparency using #RRGGBB format where transparency defaults to ff.

```golang
var a = #112233   //#RRGGBB == #112233ff
```

You can use #RGBA format where each color channel and transparency are repeated:

```golang
var a = #123f   //#RGBA == #112233ff
```

You can also use #RGB format which omits transparency in #RGBA format with transparency defaulting to ff.

```
var a = #123   //#RGB == #112233ff
```

Color type assignment only accepts these four variable lengths: # followed by 8, 6, 4, or 3 hexadecimal digits.

After using # with hexadecimal digits for assignment, the variable becomes Color type.

We provide an interface that returns Color type data: ColorRGB(int a, int b, int c). This interface accepts decimal RGB values as input and returns a hexadecimal #RRGGBBAA standard color type value.

```
var a = ColorRGB(255,255,255)
```

Variable `a` equals #ffffffff at this point.

Color variable values are case-insensitive.

After using the Free Fire Craftland Code plugin in VS Code and entering a valid value with hash # followed by hexadecimal input you can activate color preview and palette. Click on color preview to expand the palette; selecting an appropriate color from the palette will automatically modify the value.

### Dynamic Types

##### List<T>

A list represents a collection of data, where T is the type of elements in the list.

For example, List<int> represents a list of integers.

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

##### Map<T1,T2>

A map represents a set of key-value pairs, where T1 is the type of keys and T2 is the type of values.

For example, Map<string, int> represents a dictionary that queries int values using string keys.

```golang
func Demo() {
    var allItems Map<string, int> = Map<string, int>{"a":1, "b":2}
    allItems["a"] = 2
    LogInfo(allItems["a"])
    LogInfo(allItems)
}
```

##### entity\<T>

An entity represents an object where T is the type of attached component.

For example, entity\<Player> represents an entity with a Player component.

```golang
func Demo() {
    thisEntity<Global>.EcoRoundMoney = 100
    LogInfo(thisEntity<Global>.EcoRoundMoney)

    RevivePlayer(thisEntity<Player>)
}
```

### Operators

#### Arithmetic Operators

Assume A is 10 and B is 20.

| Operator | Description      | Example         |
| -------- | ---------------- | --------------- |
| +        | Addition         | A + B outputs 30 |
| -        | Subtraction      | A - B outputs -10 |
| *        | Multiplication   | A * B outputs 200 |
| /        | Division         | B / A outputs 2   |
| %        | Modulus          | B % A outputs 0   |
| ++       | Increment        | A++ outputs 11    |
| --       | Decrement        | A-- outputs 9     |

#### Relational Operators

Assume A is 10 and B is 20.

| Operator | Description                                                  | Example         |
| -------- | ------------------------------------------------------------ | --------------- |
| ==       | Checks if two values are equal. Returns True if equal, otherwise False.         | (A == B) is False |
| !=       | Checks if two values are not equal. Returns True if not equal, otherwise False.     | (A != B) is True  |
| >        | Checks if the left value is greater than the right value. Returns True if true, otherwise False.     | (A > B) is False  |
| <        | Checks if the left value is less than the right value. Returns True if true, otherwise False.     | (A < B) is True   |
| >=       | Checks if the left value is greater than or equal to the right value. Returns True if true, otherwise False. | (A >= B) is False |
| <=       | Checks if the left value is less than or equal to the right value. Returns True if true, otherwise False. | (A <= B) is True  |

#### Logical Operators

Assume A is True and B is False.

| Operator | Description                                                  | Example         |
| -------- | ------------------------------------------------------------ | --------------- |
| &&       | Logical AND operator. If both operands are True, then the condition becomes True; otherwise False. | (A && B) is False |
| \|\|     | Logical OR operator. If any of the operands are True, then the condition becomes True; otherwise False. | (A \|\| B) is True |
| !        | Logical NOT operator. If a condition is True, then Logical NOT condition becomes False; otherwise it becomes True. | !(A && B) is True |

#### Assignment Operators

| Operator | Description                                           | Example                                  |
| -------- | ----------------------------------------------------- | ---------------------------------------- |
| =        | Simple assignment operator, assigns a value to a variable.           | C = A + B assigns the result of A + B to C |
| +=       | Adds and assigns                                   | C += A equals C = C + A                 |
| -=       | Subtracts and assigns                              | C -= A equals C = C - A                 |
| *=       | Multiplies and assigns                             | C *= A equals C = C * A                 |
| /=       | Divides and assigns                                | C /= A equals C = C / A                 |
| %=       | Modulus and assigns                                | C %= A equals C = C % A                 |

#### Operator Precedence

Some operators have higher precedence than others. Binary operators are evaluated from left to right. The table below lists all operators by precedence from highest to lowest:

| Precedence Level   | Operators                   |
| ------------------ | ----------------------------|
| 5                  | *, /, %                     |
| 4                  | +, -                        |
| 3                  | ==, !=, <, <=, >, >=        |
| 2                  | &&                          |
| 1                  |\|\|                         |

### Control Flow

#### Conditional Statements

Conditional statements require developers to specify one or more conditions to decide whether to execute certain statements based on whether the conditions are true or false.

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

In many real-world problems, there are repetitive operations with patterns that require certain statements to be executed repeatedly in programs.

##### for index

```golang
func OddNumSumV1(max int) int {
    var sum = 0
    for i = 1, max, 2 {
        sum += i
    }
    return sum
}
```

##### for range

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

##### while

```golang
func OddNumSumV2(max int) int {
    var sum = 0
    var loopIndex = 0
    while loopIndex < max {
        loopIndex = loopIndex + 1
        sum += loopIndex
    }
    return sum
}
```
