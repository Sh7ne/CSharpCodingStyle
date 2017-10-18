# C# Coding Style and Naming Convention

something need to say before everything
#### **Reference**
[C# Coding Conventions (C# Programming Guide)](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/inside-a-program/coding-conventions)

## The Basics

PascalCasing: First letter of each concatenated word is capitalized. No other characters are used to separate the words, like hyphens or underscores.

camelCasing: First letter is lowercase or capitalized and each subsequent concatenated word is capitalized.


## DO

### using PascalCasing organize namespaces with a clearly defined structure

```csharp
// Examples
namespace CIK.Models.ViewModels.Marketing
{

}
```
### use PascalCasing for class names and method names.

```csharp
public class ClientActivity
{
    public void ClearStatistics()
    {
        //...
    }
    public void CalculateStatistics()
    {
        //...
    }
}
```

### use camelCasing for method arguments and local variables.

```csharp
public class UserLog
{
    public void Add(LogEvent logEvent)
    {
        int itemCount = logEvent.Items.Count;
        // ...
    }
}
```

### Use a try-catch-finally statement for most exception handling.

```csharp
    try
    {

    }
    catch (Exception e)
    {
        throw new Exception("", e);
    }
    finally
    {
        // Just for example
        oConn.Close();
        oConn.Dispose();
    }
```


