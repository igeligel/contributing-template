# Information
This is heavily related to the official [C# code conventions](https://msdn.microsoft.com/en-us/library/ff926074.aspx)
 by [Microsoft](https://www.microsoft.com).

# Naming Conventions
You should not use namespace qualifications if you are using other parts of the namespace in your project. If it is just used once, you can do it like:

```csharp
var currentPerformanceCounterCategory = new System.Diagnostics.
    PerformanceCounterCategory();
```

# Layout Conventions
- *You should use spaces for indenting. Four spaces for one tab.*

  To have a line break without a paragraph, you will need to use four trailing spaces.
  For example:
  ```csharp
  var currentPerformanceCounterCategory = new System.Diagnostics.
      PerformanceCounterCategory();
  ```
- *Write only one statement per line.*

  Not like:
  ```csharp
  var i = 0; var booleanValueOne = true;
  ```
- *Add at least one blank line between method definitions and property definitions.*

  ```csharp
  public int number1, number2;

  public string text1, text2;

  public int GetNumber() {
      return number1 + number2;  
  }

  public string GetString() {
      return text1 + text2;
  }
  ```
- *Use parentheses to make clauses in an expression apparent, as shown in the following code.*

  For example:
  ```csharp
  if ((booleanValueOne) && (!booleanValueTwo))
  {
      // Take appropriate action.
  }
  ```

# Commenting Conventions
- *You should always start a comment on a seperate line.*
  Not like:

  ```csharp
  var test = 0; // variable test is used for function x.
  ```

  Better use:
  ```csharp
  // Variable Test is used for function x.
  var test = 0;
  ```
- *Begin the text with an uppercase letter.* For reference see last code bracket.
- *End comment with a period.* For reference see last code bracket.
- *Insert space after the delimiter (//).* For reference see last code bracket.

# Language Guidelines

## String Data type
- *Use + operator for concatenate short strings*
  ```csharp
  var personName = "John" + " " + "Doe";
  ```

- *Use StringBuilder to operate with large strings.*
  ```csharp
  var phrase = "testtesttest";
  var manyPhrases = new StringBuilder();
  for (var i = 0; i < 1337; i++) {
      manyPhrases.Append(phrase);  
  }
  ```

## Implicitly Typed Local Variables
- *When type of a variable is clear from the context use var-keyword.*
  ```csharp
  var personName = "John Doe";
  var age = 27;
  var userInput = Convert.ToInt32(Console.ReadLine());
  ```

- *Do not use var-keyword if the type of the variable is not clear by context.*
  ```csharp
  int currentState = getCurrentState();
  ```

- *Do not rely on variable name to get the type of a variable.*
  ```csharp
  var inputInt = Console.ReadLine();
  Console.WriteLine(inputInt);
  ```
- *Avoid using var instead of dynamic*

- *Use implicit type of variables for for- and foreach-loops*
  ```csharp
  for (var i = 0; i < 10; i++) {
      Console.WriteLine(i);
  }
  ```

  ```csharp
  numbers = new List<int> { 5, 10, 23 };
  foreach (var number in numbers) {
      Console.WriteLine(number);
  }
  ```

# Unsigned Data Type
You should avoid using the unsigned data type to secure compability with other libraries.

# Arrays
Be sure if to declare a data type when you instantiate an array implicitly.
```csharp
string[] vowels = { "a", "e", "i", "o", "u" };
```

If you use explicit instantiation, you can use the var-keyword.
```csharp
var vowels = new string[] { "a", "e", "i", "o", "u" };
```

If you want to give your array a size, you need to initialize each element one by one.
```csharp
var vowels = new string[5];
vowels[0] = "a";
vowels[1] = "e";
vowels[2] = "i";
vowels[3] = "o";
vowels[4] = "u";
```

# Delegates
*Use concise syntax to create an instance of delegate type.*
First define the type:
```csharp
public delegate void Del(string message);
```

Then define a method with the matching signature.
```csharp
public void DelMethod(string str) {
    Console.WriteLine("DelMethod was called with argument: " + str);
}
```

It is preferred to create an instance by using the condensed syntax.
```csharp
Del  exampleDel2 = DelMethod;
```

Here is the full syntax:
```csharp
Del exampleDel1 = new Del(DelMethod);
```

# try-catch and using Statements in Exception Handling
*Use a try-catch statement for most exception handling.*

```csharp
static string GetValueFromArray(string[] array, int index)
{
    try
    {
        return array[index];
    }
    catch (System.IndexOutOfRangeException ex)
    {
        Console.WriteLine("Index is out of range: {0}", index);
        throw;
    }
}
```

If a try-catch-finally block will use the dispose method in the finally block, you should use a using statement instead.

```csharp
Font font1 = new Font("Arial", 10.0f);
try
{
    byte charset = font1.GdiCharSet;
}
finally
{
    if (font1 != null)
    {
        ((IDisposable)font1).Dispose();
    }
}
```

Same should be done with a using-statement:
```csharp
using (Font font2 = new Font("Arial", 10.0f))
{
    byte charset = font2.GdoCharSet;
}
```

# && and || Operators
Use ```&&``` and ```||``` instead of ```&``` and ```|``` to avoid performance problems and exceptions.
These keywords should be used when doing comparisons.

```csharp
var isOnlineSince = 16;
var isReadySince = 10;

if ((isOnlineSince >= 15) && (isReadySince >= 5)) 
{
    Console.WriteLine("The person is ready to work");
}
```

# New Operator
Use concise form of object instantiation, with implicit typing.
```csharp
var instance1 = new ExampleClass();
// Equivalent:
ExampleClass instance2 = new ExampleClass();
```

You should always use object initializer to simplify the structure of your program:
```csharp
var instance3 = new ExampleClass 
{
    Name = "Desktop",
    Id = 37414,
    Location = "Redmond",
    Age = 2.3
};

// Instead of:
var instance4 = new ExampleClass();
instance4.Name = "Desktop";
instance4.Id = 37414;
instance4.Location = "Redmond";
instance4.Age = 2.3;
```