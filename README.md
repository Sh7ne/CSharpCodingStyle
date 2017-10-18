# Coding Style and Naming Conventions

Version 0.1  
Author: Yao Zhao  
Last modify date: 2017-10-18  

Something need to say before at the begining

#### **Reference**
[C# Coding Conventions (C# Programming Guide)](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/inside-a-program/coding-conventions)

[C# Coding Standards and Naming Conventions](http://www.dofactory.com/reference/csharp-coding-standards)

[.Net 项目代码风格要求](http://www.cnblogs.com/JimmyZhang/archive/2013/06/05/3118936.html)

## The Basics

### PascalCasing

- First letter of each concatenated word is capitalized. No other characters are used to separate the words, like hyphens or underscores.

### camelCasing

- First letter is lowercase or capitalized and each subsequent concatenated word is capitalized.

### Tab Indent

- Recomment to set Editor Tab and Indent Options as below

![Tab Indent](https://github.com/Sh7ne/CSharpCodingStyle/blob/master/TabIndent.PNG?raw=true)

## Coding Style and Naming Convention

### Comment

- Comment the class, attribute, event, method, or parameters when it is not self-explained clearly by its name.
- Place the comment on a separate line, not at the end of a line of code.
- Begin comment text with an uppercase letter. End comment text with a period.
- Insert one space between the comment delimiter (//) and the comment text.
- Format as shown in the following example.

```csharp

namespace Core.Data
{
    /// <summary>
    /// Manager of data settings (connection string)
    /// </summary>
    public partial class DataSettingsManager
    {
        /// <summary>
        /// Parse settings
        /// </summary>
        /// <param name="text">Text of settings file</param>
        /// <returns>Parsed data settings</returns>
        protected virtual DataSettings ParseSettings(string text)
        {
            var shellSettings = new DataSettings();

            // Old way of file reading. 
            return shellSettings;
        }
    }


    /// <summary>
    /// Repository
    /// </summary>
    public partial interface IRepository<T> where T : BaseEntity
    {
        /// <summary>
        /// Get entity by identifier
        /// </summary>
        /// <param name="id">Identifier</param>
        /// <returns>Entity</returns>
        T GetById(object id);
    }
}
```

### NameSpaces

- Use PascalCasing organize namespaces with a clearly defined structure

```csharp
// Examples
namespace CIK.Models.ViewModels.Marketing
{

}
```

### Class and Method

- Use PascalCasing for class names and method names. 
- Use noun or noun phrases to name a class.

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

## interface

- Prefix interfaces with the letter I. 

```csharp
public interface IShape
{
}
public interface IShapeCollection
{
}
public interface IGroupable
{
}
```

### Field

- Use camelCasing for private and protect member variables with a underscore prefix

```csharp
public class UserLog
{
    protected int _Id;
    private string _username;
}
```

### Local variables and Method

- Use camelCasing for method arguments and local variables.

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

- Prefix the Method name with Is, Has, etc if the type of the return value is bool

```csharp
public bool HasDeposit(int parameter)
{
    return true;
}
```

- Use implicit typing for local variables when the type of the variable is obvious from the right side of the assignment, or when the precise type is not important.

```csharp
// When the type of a variable is clear from the context, use var 
// in the declaration.
var var1 = "This is clearly a string.";
var var2 = 27;
var var3 = Convert.ToInt32(Console.ReadLine());
```

- Do not use var when the type is not apparent from the right side of the assignment.

```csharp
// When the type of a variable is not clear from the context, use an
// explicit type.
int var4 = ExampleClass.ResultSoFar();
```

- Use predefined type names instead of system type names like Int16, Single, UInt64, etc

```csharp
// Correct
string firstName;
int lastIndex;
bool isSaved;

// Avoid
String firstName;
Int32 lastIndex;
Boolean isSaved;
```

### String Data Type

- Use the + operator to concatenate short strings, as shown in the following code.

```csharp
string displayName = nameList[n].LastName + ", " + nameList[n].FirstName;
```

- To append strings in loops, especially when you are working with large amounts of text, use a StringBuilder object.

```csharp
var phrase = "lalalalalalalalalalalalalalalalalalalalalalalalalalalalalala";
var manyPhrases = new StringBuilder();
for (var i = 0; i < 10000; i++)
{
    manyPhrases.Append(phrase);
}
```

### Try-catch-finally

- Use a try-catch-finally statement for most exception handling.

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

### Avoid

- Avoid using Abbreviations. Exceptions: abbreviations commonly used as names, such as Id, Xml, Ftp

```csharp
// Correct
UserGroup userGroup;
Assignment employeeAssignment;
  
// Avoid
UserGroup usrGrp;
Assignment empAssignment;
  
// Exceptions
CustomerId customerId;
XmlDocument xmlDocument;
FtpHelper ftpHelper;
```

- Avoid public Field

> Best practice in Java and C# has long been to use getters/setters or properties to access fields.  
Please use the properties instead.

```csharp
// Correct
public string FirstName { get; set; }

// Avoid
public string firstName;

```
