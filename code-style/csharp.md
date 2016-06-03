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
