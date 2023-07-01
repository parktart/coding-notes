# C#



NOTE in C#..

```csharp
char myChar = 'a';   // single 'quotes' used for data type char
string firstName = "Parker";   // double "quotes" used for data type string
```



## Data Types

### Intro

In C#, things can be either: **primitive/value** type or **non-primitive/reference** type

1. Primitive/Value Type:

   - Primitive types are basic data types built into the C# language.
   - Primitive types include `int`, `float`, `double`, `char`, `bool`, etc
   - When a variable is assigned a primitive/value type, it stores the actual value of the data.
   - When you assign a primitive type to another variable or pass it as a method parameter, a copy of the value is created (like in JavaScript)
   - Primitive types are allocated on the stack and directly contain their values.

2. Non-Primitive/Reference Type:

   - Non-primitive types are typically defined by the developer or provided by the .NET framework.
   - Examples of non-primitive types include `classes`, `structs`, `interfaces`, `arrays`, `strings`, `delegates`, etc
   - When a variable is assigned a primitive/value type, it stores a reference to the memory location where the data is stored.
   - When you assign a non-primitive type to another variable or pass it as a method parameter, the reference to the object is copied, not the actual object itself.
   - Non-primitive types are allocated on the heap, and variables of non-primitive types store references to their memory locations.

   

Example:

```csharp
// Primitive/Value
int x = 10;
int y = x; // y is assigned the value of x
x = 20; 
Console.WriteLine(x); // 20
Console.WriteLine(y); // 10

// Non-Primitive/Reference
int[] array1 = { 1, 2, 3 };
int[] array2 = array1; // array2 references the same array as array1

array1[0] = 10; 

Console.WriteLine(array1[0]); // 10
Console.WriteLine(array2[0]); // 10
```



### Object Browser in VS

All data types in C# correspond to .NET classes for example data type `int` corresponds to .NET class `System.Int32`

This gives us access to the additional properties and methods provided by .NET for that class



In visual studio we can view all associated properties and methods of a class in our solution using the **Object Browser**

View > Object Browser..

from here you can look up any class, like `System.String` aka `string`, to view all of its associated properties and methods!



### Primitive/value data types

**C# Type** = **.NET Type**

`byte` = `Byte`

`short` = `Int16`

`int` = `Int32`

`long` = `Int64`

`float` = `Single`

`double` = `Double`

`decimal` = `Decimal`

`char` = `Char`

`bool` = `Boolean`

`struct` = `Struct`



NOTE for the **real number** types, the default used by the C# compiler is **double**

so if you wan't to declare, for example, float or decimal..

```csharp
float myNum = 1.2f;
decimal myNum = 1.2m;
```



### Non-primitive/reference types

**C# Type** = **.NET Type**

`string` = `String`

`T[ ]` = `Array`

`class` = `Class`

`enum` = `Enum`

`interface` = `Interface`

`delegate` = `Delegate`





### Type Conversion

three types of type conversion in C#..

1. Implicit type conversion
2. Explicit type conversion (casting)
3. Conversion between non-compatible types



#### Implicit type conversion

Example: byte to int

```csharp
byte myByte = 200;
int myInt = myByte; // works fine bc the types are compatible and no data loss will occur
																// as int.MaxValue is greater than byte.MaxValue (255)

int myInt = 10;
byte myByte = myInt; // works fine bc the number 10 can be stored as either an int or a byte

int myInt = 256;
byte myByte = myInt; // won't compile bc the int can't be converted to byte (byte.MaxValue = 255) without data loss
```

if you want to convert anyway, despite the known data loss that will happen, you can use Explicit type conversion..



#### Explicit type conversion (casting)

Example:

```csharp
float myFloat = 1.2f;
int myInt = (int)myFloat;
Console.WriteLine(myInt); // 1
```

you can explicitly declare that you would like to convert `myFloat` to an `int` regardless of potential data loss



Example:

```csharp
int a = 10;
int b = 3;
  
Console.WriteLine( (double)a / (double)b ); // 3.333333333
```



#### The .NET Convert class

the `Convert` class, provided by .NET framework, is useful in data type conversion

it offers various methods for data type conversion

```csharp
namespace System
{
    public static class Convert
    {
      
    }
}

// includes methods..
Convert.ToInt32(value);
Convert.ToDouble(value);
Convert.ToString(value);
Convert.ToChar(value);
Convert.ToBoolean(value);
Convert.ToDateTime(value);
etc
```



## Number

NUMBERS are a PRIMITAVE data type

### Number Data Types

```csharp
int intMin = int.MinValue;
int intMax = int.MaxValue;
Console.WriteLine($"int range of {intMin} to {intMax}");
int intOne = 1;
int intThree = 3;
Console.WriteLine($"int 1/3 = {intOne / intThree}");

Console.WriteLine("");

float floatMin = float.MinValue;
float floatMax = float.MaxValue;
Console.WriteLine($"float range of {floatMin} to {floatMax}");
float floatOne = 1;
float floatThree = 3;
Console.WriteLine($"float 1/3 = {floatOne / floatThree}");

Console.WriteLine("");

double doubleMin = double.MinValue;
double doubleMax = double.MaxValue;
Console.WriteLine($"double range of {doubleMin} to {doubleMax}");
double doubleOne = 1;
double doubleThree = 3;
Console.WriteLine($"double 1/3 = {doubleOne / doubleThree}");

Console.WriteLine("");

decimal decimalMin = decimal.MinValue;
decimal decimalMax = decimal.MaxValue;
Console.WriteLine($"decimal range of {decimalMin} to {decimalMax}");
decimal decimalOne = 1;
decimal decimalThree = 3;
Console.WriteLine($"decimal 1/3 = {decimalOne / decimalThree}");
```



```
int range of -2147483648 to 2147483647
int 1/3 = 0

float range of -3.402823E+38 to 3.402823E+38
float 1/3 = 0.3333333

double range of -1.79769313486232E+308 to 1.79769313486232E+308
double 1/3 = 0.333333333333333

decimal range of -79228162514264337593543950335 to 79228162514264337593543950335
decimal 1/3 = 0.3333333333333333333333333333
```



`int` = integer (worst range and no precision)

`float` = for floating point numbers (decent range but worst precision)

`double` = for floating point numbers (biggest range and decent precision)

`decimal` = for floating point numbers (ok range and best precision)



NOTE for `decimal` type you may need to add the `M` suffix to the number at declaration. When compiled, a number without `M`, like `19.99`, will be created and default to either `integer` or `double` *before* being assigned to the variable - and an `int` or `double` can't be converted to `decimal`

So adding `M` tells C# to *create* that number as a decimal (and then it can be assigned to the variable)

```csharp
decimal price = 19.99;  // Error: Cannot implicitly convert type 'double' to 'decimal'
decimal price = 19.99M;  // no error
```



So unless you are doing some work that requires high decimal precision you will almost always use..

`int`

or

`double`



All Number Types:

1. Integral Types:
   - `sbyte`: Signed 8-bit integer (-128 to 127)
   - `byte`: Unsigned 8-bit integer (0 to 255)
   - `short`: Signed 16-bit integer (-32,768 to 32,767)
   - `ushort`: Unsigned 16-bit integer (0 to 65,535)
   - `int`: Signed 32-bit integer (-2,147,483,648 to 2,147,483,647)
   - `uint`: Unsigned 32-bit integer (0 to 4,294,967,295)
   - `long`: Signed 64-bit integer (-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807)
   - `ulong`: Unsigned 64-bit integer (0 to 18,446,744,073,709,551,615)
2. Floating-Point Types:
   - `float`: Single-precision floating-point type (6-9 decimal digits of precision)
   - `double`: Double-precision floating-point type (15-17 decimal digits of precision)
   - `decimal`: Decimal type for precise decimal calculations (28-29 significant digits)
3. Other Numeric Types:
   - `char`: 16-bit Unicode character (represents a single character)
   - `bool`: Boolean type representing true or false
   - `BigInteger`: Arbitrary precision integer (can represent extremely large numbers)



### Overflow

in C#, if a number variable exceeds the range of it's data type..

```csharp
byte myNum = 255;
myNum = myNum + 1; // 0
```

to prevent this..

```csharp
checked
{
  byte myNum = 255;
  myNum = myNum + 1;
}
```

in this case if overflow were to occur, an execption will be thrown and the program will crash unless you handle the exception

or you could, you know, use a different data type like `int`



## String

STRINGS are actually NON-PRIMITIVE

but they display many of the characteristics of primitive/value type



create a string object and assign it to a variable..

```csharp
string fristName = "Parker";
```



we can concat with `+`..

```csharp
string name = firstName + " " + lastName;
```

or use string.Format()..

```csharp
string name = string.Format("{0} {1}", firstName, lastName);
```

or create a string from an array..

```csharp
int[ ] numbers = {1, 2, 3};
string list = string.Join(",", numbers);
// "1,2,3"
```

string characters can be accessed by index..

```csharp
string name = "Parker";
char firstChar = name[0]; // "P"
```

and because strings immutable we cannot change individual characters of a string object..

```csharp
name[0] = 'D'; // will not run
name = "Darker"; // is ok
```



Special Characters:

`\n` = new line

`\t` = tab

`\\` = backslash

`\'` = escape single quote

`\"` = escape double quote



note if you have many special characters in a string, you can just use a **verbatim string**..

```csharp
string path = @"c:\projects\project1\folder1";
```

which is prefixed with an `@` symbol

and respects line breaks



## Class

CLASS is NON-PRIMITIVE

Classes combine and package related properties and methods together

A class is not a data type itself but a construct that allows you to define your own data types and create objects of those types



### Create Class

To create a class..

```csharp
         public                     class                  Person
// (access modifier)   (class keyword)    (class name)
```

**access modifier** = who can access this class (public makes it accessable anywhere in the app)



to add a property to the class..

```csharp
public class Person
{
    public string Name;
}
```



to add a method to the class..

```csharp
public class Person
{
    public string Name;   // property
  
    public void SayHi()    // method
    {
        Console.WriteLine("Hi, my name is " + Name);
    }
}
```

**void** means the method does not return a value



another example:

```csharp
public class Calculator
{
    public int Add(int a, int b)
    {
        return a + b;
    }
}
```

instead of **void**, the Add method here returns an **int**



### Create Object

An object is an instance of a class..

let's create an object..

```csharp
Person person = new Person( );
```

this creates a new object of class Person() that is of class Person() called person



recall how we created a new string object..

```csharp
string myString = "hi";
```

we can also create a string object using..

```csharp
string myString = new string("hi");
```

but note using the `new` keyword is not necessary when creating a string using a string literal because the language provides implicit support for creating string objects without explicitly invoking a constructor.

Also note string objects are immutable in C#.

An immutable object is an object whose state (the values of its properties) cannot be modified after it is created. Once an immutable object is created, its state remains fixed throughout its lifetime.

so we just use..

```csharp
string myString = "hi";
```

note we are not saying the myString variable is immutable (constant) but rather the string object "hi" is immutable

```csharp
string myString = "hi";
myString = "bye";
```

in this case, the `myString` variable is updated to reference the newly created `string` object which has the value "bye"



ok back to creating an object of user-defined data type (class)..

```csharp
Person person = new Person( );
```

this creates a new object of class Person() that is of class Person() called person



we can clean this up by simply saying..

```csharp
var person = new Person( );
```

this creates a new object of class Person() called person, that C# automatically determines is of class Person()

```csharp
person.Name = "Parker";
person.SayHi(); // Hi, my name is Parker
```



### The Static Modifier

note with our calculator class..

```csharp
public class Calculator
{
    public int Add(int a, int b)
    {
        return a + b;
    }
}
```

we would have to 'new up' a calculator object in order to use it's `Add` method



instead we can add the **static modifier** to our method definition within our class..

```csharp
public class Calculator
{
    public static int Add(int a, int b)
    {
        return a + b;
    }
}
```

this means we can access the `Add` method directly from the class (no object needed)

```csharp
int result = Calculator.Add(1, 2);
```



## Struct

STRUCT is PRIMITIVE

A struct is not considered a data type itself but rather a value type that represents a composite structure. A struct defines the structure and behavior of instances of that struct.

Structs are value types that contain data members (fields) and can also include methods and properties. They are typically used to represent small, lightweight objects that are commonly used to hold a few related values.

to declare a struct..

```csharp
public struct RgbColor
{
    public int Red;
    public int Green;
    public int Blue;
}
```

similar to classes, structs combine related properties and methods together

and their differences with classes are subtle enough that you may never need them

Structs become advantageous when you want to create simple, small objects like the example of RgbColor, above

Since structs are more lightweight than classes, when you need maybe thousands of instances of an object, a struct may be the more appropriate way to define its properties and methods



## Array

ARRAY is NON-PRIMITIVE

An array is not considered a data type itself, but rather a data structure that can hold multiple elements *of the same type*.



to declare an array..

```csharp
// instead of..
int number1;
int number2;
int number3;

// use..
int[ ] numbers = new int[3];
```

NOTE in C# arrays have a **fixed size** that must be specified during declaration and **cannot be changed**

we always need to 'new up' array objects, unlike with primitive classes like `int`



we can simultaneously declare and define an array with..

```csharp
int[ ] numbers = new int[3] {1, 2, 3};
```

again we can simplify this by using simply..

```csharp
var numbers = new int[3] {1, 2, 3};
```

note..

```csharp
int[ ] numbers = {1, 2, 3};
```

is also valid, but only with C# 3.0 and later





## Variables

### Intro

Declaring a variable:

```csharp
int number; // declaration - if a variable is only declared and not used, the app will run but warn you about the unused variable
Console.WriteLine(number); // the app will not run - "use of unassigned local variable"
number = 5; // assignment
Console.WriteLine(number) // 5
```

Declaring a constant variable:

```csharp
const int myConst = 10;
```



Variables..

- cannot start with a number
- cannot be a C# reserved word
- can start with/contain @ like `@int`
- should use **c**amel**C**ase for local variables
- should use **P**ascal**C**ase for constants



The keyword `var` makes variable declaration easier..

```csharp
var myNum = 5;  // the C# compiler will automatically detect and assign an appropriate data type for this variable
```

you can hover over the variable in VS to see which data type will be assigned





### Variable Scope

variables are block scope..

```csharp
{
  byte a = 1;
  {
    byte b = 2;
    {
      byte c = 3;
    }
  }
}
```





## Try Catch

in C# errors are called `exceptions` and these exceptions are what will cause your application to crash

for example..

```csharp
string myString = "1234";
byte myByte = Convert.ToByte(myString);
Console.WriteLine(myByte);

Console.WriteLine("hi");

// Unhandled exception occured
```

will throw an exception, and crash, because "1234" cannot be easily converted to data type `byte` (which has a max value of 255)



you can prevent your program from crashing by handling the exception using a `Try Catch` block..

```csharp
try
{
    string myString = "1234";
    byte myByte = Convert.ToByte(myString);
    Console.WriteLine(myByte);
}
catch (Exception)
{
    Console.WriteLine("That didn't work");
}

Console.WriteLine("hi");

// That didn't work
// hi
```

where you can essentially define custom error code for when the code in the `try` block fails



##  C# Operators

C# operator types..

1. Arithmetic operators
2. Comparison operators
3. Assignment operators
4. Logical operators
5. Bitwise operatros



### Arithmetic Operators

```csharp
+
-
*
/
%
++ (prefix and postfix)
--   (prefix and postfix)
```



### Comparison Operators

```csharp
==
!=
>
<
>=
<=
```



### Assignment Operators

```csharp
=
+=
-=
*=
/=
```



### Logical Operators

```csharp
&&
||
!
```







## Loops

WHILE

```csharp
int counter = 0;
while (counter < 10)
{
  Console.WriteLine($"counter = {counter}");
  counter++;
}
```

DO .. WHILE

```csharp
int counter = 0;
do
{
  Console.WriteLine($"counter = {counter}");
  counter++;
} while (counter < 10);
```

FOR

```csharp
for (int i = 0;  i < 10;  i++)
{
  Console.WriteLine($"counter = {i}");
}
```

FOR EACH

`foreach` repeats its code for every item in a sequence of items

```csharp
string[] fruits = { "Apple", "Banana", "Orange", "Mango" };

foreach (string fruit in fruits)
{
    Console.WriteLine(fruit);
}
```



NESTED FOR LOOP

```csharp
for (int row = 1;  row < 11;  row++)
{
  for (char column = 'a';  column < 'k';  column++)
  {
    Console.WriteLine($"cell ({row}, {column})");
  }
}
```





## Lambda Expression

In C#, a lambda expression is a concise way to define anonymous functions. Lambda expressions allow you to create inline functions without explicitly declaring a separate method. They are commonly used in functional programming, LINQ queries, and event handling.

Lambda expression syntax:

```csharp
(parameter_list) => expression_or_statement_block
```

```csharp
Func<int, int, int> add = (a, b) => a + b;
int result = add(3, 4);  // result = 7
```







