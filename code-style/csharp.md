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

   To have a line break without a paragraph, you will need to use two trailing spaces.
   For example:
   ```csharp
var currentPerformanceCounterCategory = new System.Diagnostics.
    PerformanceCounterCategory();
```
- *Write only one statement per line.*

   not like:
   ```csharp
   var i = 0; var booleanValueOne = true;
   ```
- *Add at least one blank line between method definitions and property definitions.*

   ```csharp
public int number1, number2;

 public string text1, text2;
```
- *Use parentheses to make clauses in an expression apparent, as shown in the following code.*

  For example:
  ```csharp
  if ((booleanValueOne) && (!booleanValueTwo))
  {
    // Take appropriate action.
  }
  ```
