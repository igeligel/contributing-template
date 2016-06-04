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
