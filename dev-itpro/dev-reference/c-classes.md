---
# required metadata

title: C Classes | Microsoft Docs
description: System API classes that start with the letter C.
author: RobinARH
manager: AnnBe
ms.date: 2016-02-18 20:23:13
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: a:2:{s:4:"name";s:22:"Robin Reynolds-Haertle";s:2:"id";s:0:"";}
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 50962
ms.assetid: 8b79e564-5a3b-40b8-bafb-f287f58db2fd
ms.region: Global
# ms.industry: 
ms.author: robinr

---

# C Classes

System API classes that start with the letter C.

Class ClassNode
---------------

    class ClassNode extends TreeNode

The ClassNode class is a specialization of the TreeNode class that represents a class in the Microsoft Dynamics AX Application Object Tree (AOT).

### Remarks

This class lets you create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                            | Description                                                                                                                                   |
|---------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| public TreeNode AOToverrideMethod(str methodName) |                                                                                                                                               |
| public str changedBy(\[str value\])               | Gets or sets the name of the user who last changed the application object.                                                                    |
| public Date changedDate(\[Date value\])           | Gets or sets the date an application object was last changed.                                                                                 |
| public str changedTime(\[str value\])             | Gets or sets the time an application object was last changed.                                                                                 |
| public str createdBy(\[str value\])               | Gets or sets the name of the user who created the application object.                                                                         |
| public Date creationDate(\[Date value\])          | Gets or sets the date an application object was created.                                                                                      |
| public str creationTime(\[str value\])            |                                                                                                                                               |
| public str extends(\[str value\])                 |                                                                                                                                               |
| public int iD(\[int value\])                      |                                                                                                                                               |
| public boolean isDetached()                       |                                                                                                                                               |
| public int legacyId(\[int value\])                |                                                                                                                                               |
| public str name(\[str value\])                    | Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics AX application object. |
| public Guid origin(\[Guid value\])                |                                                                                                                                               |
| public int runOn(\[int value\])                   |                                                                                                                                               |
| public void AOTedit(\[int Line\], \[int Column\]) | Opens the class so that it can be modified in the editor.                                                                                     |

### Method AOToverrideMethod

    public TreeNode AOToverrideMethod(str methodName)

#### Parameters

methodName  

#### Return Value

### Method changedBy

Gets or sets the name of the user who last changed the application object.

    public str changedBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method changedDate

Gets or sets the date an application object was last changed.

    public Date changedDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was last changed.

### Method changedTime

Gets or sets the time an application object was last changed.

    public str changedTime([str value])

#### Parameters

value  

#### Return Value

The time an application object was last changed.

### Method createdBy

Gets or sets the name of the user who created the application object.

    public str createdBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method creationDate

Gets or sets the date an application object was created.

    public Date creationDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was created.

### Method creationTime

    public str creationTime([str value])

#### Parameters

value  

#### Return Value

### Method extends

    public str extends([str value])

#### Parameters

value  

#### Return Value

### Method iD

    public int iD([int value])

#### Parameters

value  

#### Return Value

### Method isDetached

    public boolean isDetached()

#### Return Value

### Method legacyId

    public int legacyId([int value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in the code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Does not exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enumerations, classes, and so on.

### Method origin

    public Guid origin([Guid value])

#### Parameters

value  

#### Return Value

### Method runOn

    public int runOn([int value])

#### Parameters

value  

#### Return Value

### Method AOTedit

Opens the class so that it can be modified in the editor.

    public void AOTedit([int Line], [int Column])

#### Parameters

Line  
A value that is ignored; optional.

<!-- -->

Column  
A value that is ignored; optional.

#### Remarks

All methods are loaded into the editor. The arguments are included in the signature for backward compatibility only; they are ignored.

#### Examples

    static void example() 
    { 
        ClassNode classNode; 
     
        classNode = infolog.findNode('\Classes\SysClassWizard'); 
        classNode.AOTedit(); 
    }

## Class ClientPrintJobSettings
    class ClientPrintJobSettings extends PrintJobSettings

### Remarks

### Examples

### Methods

| Method                                                                                                                  | Description                                     |
|-------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------|
| public container getFontDimension(container container)                                                                  |                                                 |
| public container getInfoStrings()                                                                                       |                                                 |
| public int getNextLineOffset(container container)                                                                       |                                                 |
| public container getPageInfo()                                                                                          |                                                 |
| public container getPrinterNames()                                                                                      |                                                 |
| public int getTextWidth(str text, str fontName, int charSet, int fontHeight, int style, int weight)                     |                                                 |
| public container getTextWidthExt(container container)                                                                   |                                                 |
| public container getWordWrapInfo(str text, int width, str fontName, int charSet, int fontHeight, int style, int weight) |                                                 |
| public container getWordWrapInfoExt(container container)                                                                |                                                 |
| public container printerSettingsExt(str formName, \[xArgs args\], \[ReportRun reportRun\], \[int showWhat\])            |                                                 |
| public container setOrientationGetPageInfo(PrinterOrientation orientation)                                              |                                                 |
| public void new(\[container Settings\], \[boolean infoOnly\])                                                           | Initializes a new instance of the Object class. |

### Method getFontDimension

    public container getFontDimension(container container)

#### Parameters

container  

#### Return Value

### Method getInfoStrings

    public container getInfoStrings()

#### Return Value

### Method getNextLineOffset

    public int getNextLineOffset(container container)

#### Parameters

container  

#### Return Value

### Method getPageInfo

    public container getPageInfo()

#### Return Value

### Method getPrinterNames

    public container getPrinterNames()

#### Return Value

### Method getTextWidth

    public int getTextWidth(str text, str fontName, int charSet, int fontHeight, int style, int weight)

#### Parameters

text  

<!-- -->

fontName  

<!-- -->

charSet  

<!-- -->

fontHeight  

<!-- -->

style  

<!-- -->

weight  

#### Return Value

### Method getTextWidthExt

    public container getTextWidthExt(container container)

#### Parameters

container  

#### Return Value

### Method getWordWrapInfo

    public container getWordWrapInfo(str text, int width, str fontName, int charSet, int fontHeight, int style, int weight)

#### Parameters

text  

<!-- -->

width  

<!-- -->

fontName  

<!-- -->

charSet  

<!-- -->

fontHeight  

<!-- -->

style  

<!-- -->

weight  

#### Return Value

### Method getWordWrapInfoExt

    public container getWordWrapInfoExt(container container)

#### Parameters

container  

#### Return Value

### Method printerSettingsExt

    public container printerSettingsExt(str formName, [xArgs args], [ReportRun reportRun], [int showWhat])

#### Parameters

formName  

<!-- -->

args  

<!-- -->

reportRun  

<!-- -->

showWhat  

#### Return Value

### Method setOrientationGetPageInfo

    public container setOrientationGetPageInfo(PrinterOrientation orientation)

#### Parameters

orientation  

#### Return Value

### Method new

Initializes a new instance of the Object class.

    public void new([container Settings], [boolean infoOnly])

#### Parameters

Settings  

<!-- -->

infoOnly  

## Class CLRInterop
    class CLRInterop extends Object

The ClrInterop class is a utility class that provides functionality for type marshaling and exception handling. Because all the methods are static, no instantiation of the class is required.

### Remarks

### Examples

### Methods

| Method                                                                               | Description                                                                                                                              |
|--------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| ::public static AnyType getAnyTypeForObject(CLRObject clrObject)                     | Converts a common language runtime (CLR) object to a value of the X++ anytype data type.                                                 |
| ::public static CLRObject getLastException()                                         | Retrieves the most recent CLR exception.                                                                                                 |
| ::public static CLRObject getObjectForAnyType(AnyType anyType)                       | Converts a value of the X++ anytype data type to a value of the CLRObject data type.                                                     |
| ::public static CLRObject getType(str clrTypeName)                                   |                                                                                                                                          |
| ::public static boolean isNull(CLRObject clrObject)                                  | Confirms whether the specified CLRObject instance is set to nullNothingnullptrunita null reference (Nothing in Visual Basic).            |
| ::public static CLRObject Null(str clrTypeName)                                      | Returns a CLR data type that has a value of nullNothingnullptrunita null reference (Nothing in Visual Basic).                            |
| ::public static CLRObject parseClrEnum(str clrEnumTypeName, str enumValues)          | Converts the string representation of the name or numeric value of one or more enumerated constants to an equivalent CLRObject instance. |
| ::public static CLRObject staticInvoke(str className, str methodName, VarArg params) | Calls a static method on a CLR data type.                                                                                                |
| ::public static void loadAssembly(str clrAssemblyName)                               |                                                                                                                                          |
| public void new()                                                                    | Initializes a new instance of the CLRInterop class.                                                                                      |

### Method getAnyTypeForObject

Converts a common language runtime (CLR) object to a value of the X++ anytype data type.

    public static AnyType getAnyTypeForObject(CLRObject clrObject)

#### Parameters

clrObject  
The CLR object to convert to an X++ data type.

#### Return Value

An X++ anytype date type that has the value of the \_object argument.

#### Remarks

If an attacker can control input to the getAnyTypeForObject method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method. If the argument cannot be converted to an X++ data type, an exception of the Exception::ClrError type is thrown.

#### Examples

The following example sets the value of a CLR string to an X++ str data type.

    { 
        CLRObject clrObj; 
        InteropPermission perm; 
        System.String   clrStr = "Calculate total"; 
        str             s; 
         
        perm = new InteropPermission(InteropKind::ClrInterop); 
        if (perm == null) 
        { 
            return; 
        } 
        perm.assert(); 
      
        s = ClrInterop::getAnyTypeForObject(clrStr); 
        CodeAccessPermission::revertAssert(); 
    }

### Method getLastException

Retrieves the most recent CLR exception.

    public static CLRObject getLastException()

#### Return Value

The most recent exception of the Exception::ClrError type; otherwise, nullNothingnullptrunita null reference (Nothing in Visual Basic).

#### Remarks

If an attacker can control input to the getLastException method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

#### Examples

The following example tries to pass in a date that has an invalid format. The CLR exception that is thrown is converted to an X++ exception and then printed to the Infolog. Any nested exceptions are also printed to the Infolog.

    static void Job2(Args _args) 
    { 
        CLRObject clrObj; 
        InteropPermission perm; 
         
        try 
        { 
            System.DateTime::Parse( "-1/-1/-1"); 
        } 
        catch( Exception::CLRError ) 
        { 
            perm = new InteropPermission(InteropKind::ClrInterop); 
            if (perm == null) 
            { 
                return; 
            } 
            perm.assert(); 
      
            e = ClrInterop::getLastException(); 
             
            CodeAccessPermission::revertAssert(); 
      
            while( e ) 
            { 
                info( e.get_Message() ); 
                e = e.get_InnerException(); 
            } 
        } 
         
    }

### Method getObjectForAnyType

Converts a value of the X++ anytype data type to a value of the CLRObject data type.

    public static CLRObject getObjectForAnyType(AnyType anyType)

#### Parameters

anyType  
The X++ value to convert to a value of the CLRObject data type.

#### Return Value

The CLR object that has the value of the \_anytype argument.

#### Remarks

If an attacker can control input to the getObjectForAnyType method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method. If the argument cannot be converted to the CLRObject type, an exception of the Exception::CLRError type is thrown.

#### Examples

The following example converts a string value to a CLR string object.

    static void Job3(Args _args) 
    { 
        CLRObject clrObj; 
        InteropPermission perm; 
        System.String s; 
     
        perm = new InteropPermission(InteropKind::ClrInterop); 
        if (perm == null) 
        { 
            return; 
        } 
        perm.assert(); 
         
        s = CLRInterop::getObjectForAnyType("Calculate total"); 
      
        CodeAccessPermission::revertAssert(); 
    }

### Method getType

    public static CLRObject getType(str clrTypeName)

#### Parameters

clrTypeName  

#### Return Value

### Method isNull

Confirms whether the specified CLRObject instance is set to nullNothingnullptrunita null reference (Nothing in Visual Basic).

    public static boolean isNull(CLRObject clrObject)

#### Parameters

clrObject  
The CLRObject instance to evaluate.

#### Return Value

true if the specified CLRObject instance is set to nullNothingnullptrunita null reference (Nothing in Visual Basic) or has not been initialized.

#### Remarks

The isNull method should be used instead of the X++ nullNothingnullptrunita null reference (Nothing in Visual Basic) in conditional statements that evaluate whether a CLR data type is nullNothingnullptrunita null reference (Nothing in Visual Basic).

#### Examples

The following example sets the CLR string data type to nullNothingnullptrunita null reference (Nothing in Visual Basic) and assigns the type value to the CLR object. It then calls the isNull method and prints the result in the Infolog.

    static void Job5(Args _args) 
    { 
        System.String nullStr; 
         
        nullStr = CLRInterop::Null("System.String"); 
         
        print CLRInterop::isNull(nullStr); 
    }

### Method Null

Returns a CLR data type that has a value of nullNothingnullptrunita null reference (Nothing in Visual Basic).

    public static CLRObject Null(str clrTypeName)

#### Parameters

clrTypeName  
The CLR data type to set to nullNothingnullptrunita null reference (Nothing in Visual Basic).

#### Return Value

A CLRObject instance of the specified CLR data type.

#### Remarks

If you directly set CLR data types to nullNothingnullptrunita null reference (Nothing in Visual Basic) in X++, you only set the kernel reference to nullNothingnullptrunita null reference (Nothing in Visual Basic). This will make it impossible to use the type as a CLR data type. If you assign the CLR data type to CLRInterop:null("yourType"),, the type can be parsed at run time as a parameter of a static method invocation.

#### Examples

The following example sets the CLR string type to nullNothingnullptrunita null reference (Nothing in Visual Basic) and assigns the type value to a CLR object.

    static void Job5(Args _args) 
    { 
        System.String nullStr; 
         
        nullStr = CLRInterop::Null("System.String"); 
         
        print CLRInterop::isInitialized(nullStr); 
        print CLRInterop::isNull(nullStr); 
    }

### Method parseClrEnum

Converts the string representation of the name or numeric value of one or more enumerated constants to an equivalent CLRObject instance.

    public static CLRObject parseClrEnum(str clrEnumTypeName, str enumValues)

#### Parameters

clrEnumTypeName  
A string that contains the name or value to convert.

<!-- -->

enumValues  
A string that contains the name or value to convert.

#### Return Value

The CLRObject instance that contains the specified CLR enumerator values.

#### Remarks

The \_enumValues parameter contains a value, a named constant, or a list of named constants that are delimited by commas (,). One or more blanks spaces can precede or follow each value, name, or comma in \_enumValues. If \_enumValues is a list, the return value is the value of the specified names combined with a bitwise OR operation.

#### Examples

The following example converts the enumerator value to the string value of Monday and prints the value in the Infolog.

    static void Job6(Args _args) 
    { 
        System.DayOfWeek    dayOfWeek; 
        System.Type         dayOfWeekType; 
         
        dayOfWeek = CLRInterop::parseClrEnum( "System.DayOfWeek", "Monday"); 
         
        dayOfWeekType = dayOfWeek.GetType(); 
     
        info( dayOfWeek.ToString() ); 
    }

### Method staticInvoke

Calls a static method on a CLR data type.

    public static CLRObject staticInvoke(str className, str methodName, VarArg params)

#### Parameters

className  
The arguments, if there are any, to the method that is specified in the \_methodName parameter.

<!-- -->

methodName  
The arguments, if there are any, to the method that is specified in the \_methodName parameter.

<!-- -->

params  
The arguments, if there are any, to the method that is specified in the \_methodName parameter.

#### Return Value

The CLRObject that contains the value that is returned by the static CLR method; otherwise, nullNothingnullptrunita null reference (Nothing in Visual Basic).

#### Remarks

If an attacker can control input to the staticInvoke method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method. If an error occurs when you call the get\_Now method, the Exception::ClrError exception is thrown.

#### Examples

The following example calls the get\_Now method on the System.DateTime CLR class and prints the results in the Infolog.

    static void Job7(Args _args) 
    { 
        CLRObject clrObj; 
        InteropPermission perm; 
        System.DateTime dateTime; 
     
        perm = new InteropPermission(InteropKind::ClrInterop); 
        if (perm == null) 
        { 
            return; 
        } 
        perm.assert(); 
     
        dateTime = CLRInterop::staticInvoke( 
                       "System.DateTime", 
                       "get_Now" ); 
        info(dateTime.ToString()); 
        CodeAccessPermission::revertAssert(); 
         
        pause; 
         
        // This is the same code using CLR syntax. 
        // dateTime = System.DateTime::get_Now(); 
        // info(dateTime.ToString()); 
    }

### Method loadAssembly

    public static void loadAssembly(str clrAssemblyName)

#### Parameters

clrAssemblyName  

### Method new

Initializes a new instance of the CLRInterop class.

    public void new()

#### Remarks

All members of the CLRInterop class are static. There is no requirement to instantiate this class. If an attacker can control input to the new method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission from the InteropPermission class.

## Class CLRObject
    class CLRObject extends Object

The CLRObject class holds a reference to an instance of a common language runtime (CLR) object and dispatches calls from X++ to the corresponding wrapped managed instance.

### Remarks

### Examples

### Methods

| Method                                            | Description                                   |
|---------------------------------------------------|-----------------------------------------------|
| private CLRObject dispatch(VarArg )               | Reserved: Do not explicitly call this method. |
| public void new(str className, \[VarArg params\]) | Creates an instance of the CLRObject class.   |

### Method dispatch

Reserved: Do not explicitly call this method.

    private CLRObject dispatch(VarArg )

#### Parameters

  

#### Return Value

#### Remarks

If an attacker can control input to the dispatch method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission from the InteropPermission class.

### Method new

Creates an instance of the CLRObject class.

    public void new(str className, [VarArg params])

#### Parameters

className  
The arguments for the constructor of the CLR class to instantiate.

<!-- -->

params  
The arguments for the constructor of the CLR class to instantiate.

#### Remarks

Instances of the CLRObject class are used to wrap values that are returned from calls to CLR methods. If an attacker can control input to the new method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission from the InteropPermission class. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls the new method. If a new ClrObject object cannot be instantiated, the Exception:Internal exception is thrown. To obtain the original CLR exception, call the CLRInterop::getLastException method.

#### Examples

This example creates a new System.Int32 CLR object.

    void ClrObjectExample() 
    { 
        CLRObject clrObj; 
        InteropPermission perm; 
        anytype retVal; 
      
        perm = new InteropPermission(InteropKind::ClrInterop); 
        if (perm == null) 
        { 
            return; 
        } 
      
        perm.assert(); 
      
        clrObj = new CLRObject("System.Int32"); 
      
        CodeAccessPermission::revertAssert(); 
    }

## Class CodeAccessPermission
    class CodeAccessPermission extends Object

The CodeAccessPermission class defines the underlying structure of code access permissions.

### Remarks

The following classes extend the CodeAccessPermission class: ExecutePermission, FileIOPermission, InteropPermission, RunAsPermission, SkipAOSValidationPermission, SqlDataDictionaryPermission, SqlStatementExecutePermission, and SysDatabaseLogPermission.

### Examples

The following code example shows a class that is derived from the CodeAccessPermission class.

    final class SysTestCodeAccessPermission extends CodeAccessPermission 
    { 
        str data; 
    }

This code example illustrates a step in the process of protecting an API.

### Methods

| Method                                                 | Description                                                                                                                                       |
|--------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| public CodeAccessPermission copy()                     | Creates and returns a copy of a permission class object.                                                                                          |
| public boolean isSubsetOf(CodeAccessPermission target) | Determines whether a current permission is a subset of the specified permission when it is overridden by a derived class.                         |
| public void new()                                      | Initializes a new instance of the CodeAccessPermission class.                                                                                     |
| public void assert()                                   | Declares that the calling code can invoke an API that is protected by a permission.                                                               |
| public void demand()                                   | Checks the call stack to determine whether the permission that is required to invoke an API has been granted to the calling code.                 |
| ::public static void revertAssert()                    | Causes a previous call to the CodeAccessPermission.assert and CodeAccessPermission::assertMultiple methods to be removed and no longer in effect. |
| ::public static void assertMultiple(Set permissionSet) | Declares that the calling code can invoke an API that is protected by any of the permissions in a specified collection.                           |

### Method copy

Creates and returns a copy of a permission class object.

    public CodeAccessPermission copy()

#### Return Value

A copy of the derived class object.

#### Remarks

You can override this method as part of the process of making an API more secure.

#### Examples

The following code example shows how to override the copy method to create and return a copy of a class that is derived from the CodeAccessPermission class.

    public CodeAccessPermission copy() 
    { 
        return new SysTestCodeAccessPermission(_data); 
    }

### Method isSubsetOf

Determines whether a current permission is a subset of the specified permission when it is overridden by a derived class.

    public boolean isSubsetOf(CodeAccessPermission target)

#### Parameters

target  
A CodeAccessPermission class object.

#### Return Value

true if a current permission is a subset of a specified permission; otherwise, false.

#### Remarks

You can override the method as part of the process of making an API more secure.

#### Examples

The following example shows how to override the isSubsetOf method to determine whether permissions that are stored in the current object are located in \_target.

    public boolean isSubsetOf(CodeAccessPermission _target) 
    { 
        SysTestCodeAccessPermission sysTarget = _target; 
        return this.handle() == _target.handle(); 
    }

### Method new

Initializes a new instance of the CodeAccessPermission class.

    public void new()

### Method assert

Declares that the calling code can invoke an API that is protected by a permission.

    public void assert()

#### Remarks

You must call the assert method in the derived class for a protected API before you invoke the API. For more information about APIs that are protected by permissions, see Secured APIs. You must call the assert method on the same tier, usually the server tier, that the corresponding CodeAccessPermission::demand method is called on before the protected API is executed. Call a method on the server tier from one of the following:

-   A server static method
-   A class instance method that is set to run on the server by using the RunOn class property

Microsoft Dynamics AX does not support multiple, successive calls to the assert method in the same calling code. Either call the CodeAccessPermission::revertAssert method between each call to the assert method, or call the CodeAccessPermission::assertMultiple method. If you make multiple, successive calls to the assertmethod, the Infolog displays an error when you execute the code.

#### Examples

The following code example shows a call to the assert method before the AsciiIo Class class that is protected by a permission is invoked. The assert method is a member of the FileIOPermission class that is derived from the CodeAccessPermission class.

    server static void main(Args args) 
    { 
        FileIoPermission _perm; 
        AsciiIo a; 
      
         
        _perm = new FileIoPermission("c:\File.txt",'r'); 
        _perm.assert(); 
      
        // Invoke the protected API. 
        a = new AsciiIo("c:\File.txt",'r'); 
    }

### Method demand

Checks the call stack to determine whether the permission that is required to invoke an API has been granted to the calling code.

    public void demand()

#### Examples

The following code example shows a call to the demand method before the API functionality is executed, to determine whether permission to access the resource that is specified by the data variable has been granted to code that is calling the API.

    public static void main(str data) 
    { 
        SysTestCodeAccessPermission p = new SysTestCodeAccessPermission(data); 
        p.demand(); 
     
        //Add functionality 
    }

This code example illustrates a step in the process of protecting an API.

### Method revertAssert

Causes a previous call to the CodeAccessPermission.assert and CodeAccessPermission::assertMultiple methods to be removed and no longer in effect.

    public static void revertAssert()

#### Remarks

When you have multiple calls to the assert method in the same calling code, you must call the revertAssert method between each call. Otherwise, the Infolog displays an error when you execute the code. When you call the assert method only one time, or when you call the CodeAccessPermission::assertMultiple method, we recommend that you still call the revertAssert method after you invoke the protected API to limit the scope of the assert.

#### Examples

The following code example shows a call to the CodeAccessPermission::revertAssert method after the user calls the CodeAccessPermission.assert method and the AsciiIo class that is protected by a permission.

    server static void main(Args args) 
    { 
        FileIoPermission _perm; 
        AsciiIo a; 

         
        _perm = new FileIoPermission("c:\File.txt",'r'); 
        _perm.assert(); 
      
        //invoke protected API 
        a = new AsciiIo("c:\File.txt",'r'); 
         
        // Optionally call revertAssert() to limit scope of assert. 
        CodeAccessPermission::revertAssert(); 
    }

### Method assertMultiple

Declares that the calling code can invoke an API that is protected by any of the permissions in a specified collection.

    public static void assertMultiple(Set permissionSet)

#### Parameters

permissionSet  
A Set class object that contains a collection of permissions.

#### Remarks

You call the assertMultple method instead of making multiple, successive calls to the CodeAccessPermission.assert and CodeAccessPermission::revertAssert methods in the same calling code.

#### Examples

The following code example calls the CodeAccessPermission::assertMultple method. Then the code example calls the WinAPIServer::createFile method, which would fail without the previous call to the CodeAccessPermission::assertMultple method. The code example is a static method that you can add to a new class that you create. You can call this static method from an X++ job by using one line of code that resembles MyClass::RunOnServerPermissionTest. In the code example, the WinAPIServer class has several secure methods. The WinAPIServer class runs on the server tier, not on the client tier. Therefore the code example method must also run on the server tier. Otherwise, any permission asserts that are made on the client tier are ignored by methods that run on the server tier. This is why the server keyword is included in the method declaration of the code example. The server keyword on the method takes precedence over the RunOn property value that is specified on the class.

    server
        static public void RunOnServerPermissionTest()
    {
        Set permissionSet;
        str fileName = @"C:TestFile75a.txt";
        boolean boolFileDeleted;
     
        permissionSet =  new Set(Types::Class);
        permissionSet.add(new FileIoPermission(fileName,'rw'));

        CodeAccessPermission::assertMultiple(permissionSet);
        //--- Permissions are set, now perform file operations.

        WinAPIServer::createFile(fileName);
        boolFileDeleted = WinAPI::deleteFile(fileName);

        if (boolFileDeleted)
        {
            info("The file was deleted. Good.");
        }
        else
        {
            error("The file was not deleted. Error.");
        }
    }

## Class COM
    class COM

The COM class is use to create Component Object Model (COM) objects.

### Remarks

The COM class also supports Distributed Component Object Model (DCOM). DCOM enables objects that support DCOM to run on remote computers. When a COM object has been instantiated by using the COM class, its methods and properties can be accessed by using either the COMDispFunction class or the extended syntax for the COM class. The extended syntax enables methods and properties to be directly called on the COM object, even though they don't appear in the Lookup list (for example, com.comMethod("Hello World");). The extended syntax supports calls to methods and properties that take any number of arguments. Some COM objects support the concept of optional arguments. Only optional variant arguments can be omitted. If optional arguments are omitted, the COM object uses its default values. To omit an argument for the COM object and force it to use its default value, specify the COMArgument::NoValue enumeration, as shown in the following example.

    com.comMethod(COMArgument::NoValue, "Hello Another World");

 

If the arguments to omit from the COM object appear at the end of the argument list, omit them from the code. The following types are supported for the extended syntax for the COM class argument type and return type:

-   array
-   COM
-   COMVariant
-   date
-   enum
-   int
-   real
-   str

If a COM object returns a date, and if the extended syntax is used, the return value of the COM method should be assigned to a COMVariant class variable. The actual date and time (format) can then be extracted from the COMVariant class by using the date and time properties. If the date return value is assigned to a date variable instead of a COMVariant class, the time component of the date is lost. When the extended syntax is used, you can still call the COM class methods (the methods that appear in the Lookup list) on the objects. The COM class methods have a higher priority than the methods on the actual COM object. If a method on the COM object has the same name as a method on the COM class (for example, attach), you cannot call that method on the COM object. To enable Microsoft Dynamics AX to call the method on the COM object instead of the method that has the same name on the COM class, prefix the duplicate method name with an underscore (for example, com.\_detach();). The extended syntax for the COM class is evaluated at run time, not compile time, which causes a slight decrease in performance. If high-performance code is required, consider using the COMDispFunction class. This class offers performance improvements over the extended syntax for the COM class.

### Examples

This example calls the GetFileName method from the Scripting.FileSystemObject COM object.

    void COMExample() 
    { 
        COM               com; 
        str               result; 
        InteropPermission perm; 
        ; 
      
        // Set code access permission to help protect the use of the 
        // COM object. 
        perm = new InteropPermission(InteropKind::ComInterop); 
        if (perm == null) 
        { 
            return; 
        } 
        // Permission scope starts here. 
        perm.assert(); 
      
        com = new COM("Scripting.FileSystemObject"); 
        if (com != null) 
        { 
            result = com.GetFileName(@"c:boot.ini"); 
        } 
      
        // Close code access permission scope. 
        CodeAccessPermission::revertAssert(); 
    }

### Methods

| Method                                                                                                      | Description                                                                                                                                  |
|-------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| public AnyType dispatch(VarArg )                                                                            | Reserved. Do not explicitly call this method.                                                                                                |
| public str documentationName()                                                                              | Returns the textual name of the COM object that is associated with the instance of the COM class.                                            |
| public COMError error()                                                                                     | Returns a COMError object that is associated with the instance of the COM class.                                                             |
| public ComInterface interface()                                                                             | Returns the interface that is associated with the COM object.                                                                                |
| public int lcid(\[int lcid\])                                                                               |                                                                                                                                              |
| public str toString()                                                                                       | Returns a string that represents the instance of the COM class.                                                                              |
| ::public static COM createFromInterface(ComInterface interface)                                             | Creates an instance of the COM class by using the specified COM interface.                                                                   |
| ::public static COM createFromObject(COM object)                                                            | Creates an instance of the COM class by using the specified COM object.                                                                      |
| ::public static COM createFromVariant(COMVariant variant)                                                   | Creates an instance of the COM class by using the specified instance of the COMVariant class.                                                |
| ::public static COM getObject(str className)                                                                | Returns an instance of a COM object that is running.                                                                                         |
| ::public static COM getObjectEx(str fileName)                                                               | Returns an instance of a COM object that is specified by its file name.                                                                      |
| ::public static AnyType unsupported(int action, \[AnyType param1\], \[AnyType param2\], \[AnyType param3\]) | Reserved.                                                                                                                                    |
| public void finalize()                                                                                      | Frees resources that are associated with the instance of the COM class.                                                                      |
| public void new(\[str className\], \[str computerName\])                                                    | Creates an instance of the COM class that can be attached to the COM class and optionally instantiates a COM object on a specified computer. |
| public void attach(ComInterface interface)                                                                  | Attaches an instance of the COM class to a COM interface.                                                                                    |
| public void detach()                                                                                        | Detaches a COM object from the class that it was associated with.                                                                            |

### Method dispatch

Reserved. Do not explicitly call this method.

    public AnyType dispatch(VarArg )

#### Parameters

  

#### Return Value

### Method documentationName

Returns the textual name of the COM object that is associated with the instance of the COM class.

    public str documentationName()

#### Return Value

The textual name of the COM object that is associated with the instance of the COM class; an empty string if there is no documentation name for the COM object.

#### Remarks

The textual name of a class is used by the class to describe itself. The textual name differs from the class name that is used to instantiate the class.

#### Examples

The following example shows how to retrieve the documentation name for a COM object.

    str docName; 
    ; 
    // The obj that was previously instantiated. 
    docName = obj.documentationName(); 
    info(strfmt("documentationName: %1", docName));

### Method error

Returns a COMError object that is associated with the instance of the COM class.

    public COMError error()

#### Return Value

A COMError value that represents the error that is associated with the instance of the COM class.

#### Examples

The following example shows how to retrieve the error object that is associated with an instance of the COM class.

    COMError err; 
     
    // The obj variable was previously instantiated. 
    err = obj.error(); 
     
    // Output the error number. 
    info(strfmt("Error: %1", err.number()))

### Method interface

Returns the interface that is associated with the COM object.

    public ComInterface interface()

#### Return Value

The interface that is associated with the COM object; 0 (zero) if no interface is associated with the COM object.

#### Examples

The following example shows how to retrieve the interface that is associated with a COM object.

    // The obj variable was previously instantiated. 
    info(strfmt("Interface: %1", obj.interface()));

### Method lcid

    public int lcid([int lcid])

#### Parameters

lcid  

#### Return Value

### Method toString

Returns a string that represents the instance of the COM class.

    public str toString()

#### Return Value

A string that contains a description of the instance of the COM class.

#### Examples

The following example shows how to use the toString method.

    print objCOM.toString();

### Method createFromInterface

Creates an instance of the COM class by using the specified COM interface.

    public static COM createFromInterface(ComInterface interface)

#### Parameters

interface  
The interface to use to create the new instance of the COM class.

#### Return Value

An instance of the COM class for the COM interface that is specified by the interface parameter; nullNothingnullptrunita null reference (Nothing in Visual Basic) if the instance of the COM class could not be created.

#### Remarks

To help reduce security risks that are associated with unmanaged code, make sure that you validate the objects that are passed to this method, and that all DLLs used for your COM objects are protected by access control lists.

### Method createFromObject

Creates an instance of the COM class by using the specified COM object.

    public static COM createFromObject(COM object)

#### Parameters

object  
The instance of the COM class to use to create the new instance of the COM class.

#### Return Value

An instance of the COM class for the COM object that is specified by the object parameter; nullNothingnullptrunita null reference (Nothing in Visual Basic) if the instance of the COM class could not be created.

#### Remarks

To help reduce security risks that are associated with unmanaged code, make sure that you validate the objects that are passed to this method, and that all DLLs used for your COM objects are protected by access control lists.

### Method createFromVariant

Creates an instance of the COM class by using the specified instance of the COMVariant class.

    public static COM createFromVariant(COMVariant variant)

#### Parameters

variant  
The instance of the COMVariant class to use to create the new instance of the COM class.

#### Return Value

An instance of the COM class for the COM object that is specified by the variant parameter; nullNothingnullptrunita null reference (Nothing in Visual Basic) if the instance of the COM class could not be created.

#### Remarks

To help reduce security risks that are associated with unmanaged code, make sure that you validate the objects that are passed to this method, and that all DLLs used for your COM objects are protected by access control lists.

### Method getObject

Returns an instance of a COM object that is running.

    public static COM getObject(str className)

#### Parameters

className  
The ProgID value or class name of the COM object that is used to create the instance of the COM class.

#### Return Value

An instance of the COM class for the class that is specified by the className parameter; nullNothingnullptrunita null reference (Nothing in Visual Basic) if the instance could not be created.

#### Remarks

If multiple instances of the specified COM object are running, we cannot guarantee which instance will be returned by the getObject method. Some COM objects do not support the extended features that enable calls to this method.

#### Examples

The following example shows how to retrieve an instance of a running COM object.

    COM objExcel, objWorkBook, objWorkBooks; 
    InteropPermission perm; 
      
    // Set code access permission to help protect the use of COM.new. 
    perm = new InteropPermission(InteropKind::ComInterop); 
    perm.assert(); 
      
    objExcel = COM::getObject("Excel.Application"); 
      
    if (!objExcel) 
    { 
        // Unable to connect to a running instance of Microsoft Excel. 
        // Try starting it. 
        objExcel = new COM("Excel.Application"); 
        if (!objExcel) 
        { 
            Info ("Unable to find or create an instance of Excel"); 
            return;  // Or other error action. 
        }  
    } 
    // Close code access permission scope. 
    CodeAccessPermission::revertAssert(); 
      
    objExcel.visible(true); 
    objWorkBooks = objExcel.workbooks(); 
    if (objWorkBooks) 
    { 
        objWorkBook = objWorkBooks.open("d:\mydata\book1.xls"); 
    }

### Method getObjectEx

Returns an instance of a COM object that is specified by its file name.

    public static COM getObjectEx(str fileName)

#### Parameters

fileName  
The name of the file that provides the functionality for the COM object that is used to create the instance of the COM class.

#### Return Value

An instance of the COM class that is specified by the filename parameter; nullNothingnullptrunita null reference (Nothing in Visual Basic) if the instance could not be created.

#### Remarks

To help reduce security risks that are associated with unmanaged code, make sure that you validate the objects that are passed to this method, and that all DLLs used for your COM objects are protected by access control lists.

### Method unsupported

Reserved.

    public static AnyType unsupported(int action, [AnyType param1], [AnyType param2], [AnyType param3])

#### Parameters

action  

<!-- -->

param1  

<!-- -->

param2  

<!-- -->

param3  

#### Return Value

### Method finalize

Frees resources that are associated with the instance of the COM class.

    public void finalize()

#### Examples

The following example how to use the finalize method.

    objCOM.finalize();

### Method new

Creates an instance of the COM class that can be attached to the COM class and optionally instantiates a COM object on a specified computer.

    public void new([str className], [str computerName])

#### Parameters

className  
The name of the remote computer on which to instantiate the COM object; optional. If this parameter is omitted, the COM object is instantiated on the local computer. If the computer name is specified, the DCOM system component must be installed on both the local computer and the remote computer. The specific COM object must support DCOM, and it must be correctly configured on both the local computer and the remote computer. The system component is a standard component of MicrosoftWindows 98, Windows NT, and later versions. In Windows 95, the DCOM system component must be installed.

<!-- -->

computerName  
The name of the remote computer on which to instantiate the COM object; optional. If this parameter is omitted, the COM object is instantiated on the local computer. If the computer name is specified, the DCOM system component must be installed on both the local computer and the remote computer. The specific COM object must support DCOM, and it must be correctly configured on both the local computer and the remote computer. The system component is a standard component of MicrosoftWindows 98, Windows NT, and later versions. In Windows 95, the DCOM system component must be installed.

#### Remarks

The class name of a COM object is either its programmatic identifier (ProgID) or its class identifier (CLSID):

-   ProgIDs have the following format: program.component.version
-   CLSIDs are 128-bit values and have the following format: {xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx}

If an attacker can control input to the new method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission from the InteropPermission class. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

#### Examples

This example calls the GetFileName method from the Scripting.FileSystemObject COM object.

    void COMExample() 
    { 
        COM               com; 
        str               result; 
        InteropPermission perm; 
      
        // Set the code access permission to help protect the use of the 
        // COM object. 
        perm = new InteropPermission(InteropKind::ComInterop); 
        if (perm == null) 
        { 
            return; 
        } 
        // Permission scope starts here. 
        perm.assert(); 
      
        com = new COM("Scripting.FileSystemObject"); 
        if (com != null) 
        { 
            result = com.GetFileName(@"c:boot.ini"); 
        } 
      
        // Close the code access permission scope. 
        CodeAccessPermission::revertAssert(); 
    }

### Method attach

Attaches an instance of the COM class to a COM interface.

    public void attach(ComInterface interface)

#### Parameters

interface  
The interface to attach to the instance of the COM class.

#### Remarks

This method is provided because some COM objects can be instantiated only by other COM objects and cannot be instantiated directly by the COM class.

### Method detach

Detaches a COM object from the class that it was associated with.

    public void detach()

#### Remarks

For example, this method can be called to detach a COM object from a call to the attach or new method.

## Class COMDispFunction
    class COMDispFunction extends Object

### Remarks

### Examples

### Methods

| Method                                                                   | Description                                                                                          |
|--------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------|
| public int call(VarArg )                                                 |                                                                                                      |
| public AnyType callContainerOfParms(container parms)                     |                                                                                                      |
| public str toString()                                                    | Returns a string that represents the current object.                                                 |
| public void finalize()                                                   |                                                                                                      |
| public void new(COM comObject, str functionName, COMDispContext context) | Creates a COMDispFunction object, which is used to access the functionality in an Automation object. |

### Method call

    public int call(VarArg )

#### Parameters

  

#### Return Value

#### Remarks

If an attacker can control input to the call method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission from the InteropPermission class. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

### Method callContainerOfParms

    public AnyType callContainerOfParms(container parms)

#### Parameters

parms  

#### Return Value

### Method toString

Returns a string that represents the current object.

    public str toString()

#### Return Value

A string that represents the current object.

#### Remarks

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type. For example, an instance of the SysMethodInfo class returns the method name and type of the method, such as instance or static.

### Method finalize

    public void finalize()

### Method new

Creates a COMDispFunction object, which is used to access the functionality in an Automation object.

    public void new(COM comObject, str functionName, COMDispContext context)

#### Parameters

comObject  
The context of the functionality to access. The following values are used: COMDispContext::METHOD, COMDispContext::PROPERTYGET, COMDispContext::PROPERTYPUT, and COMDispContext::PROPERTYPUTREF

<!-- -->

functionName  
The context of the functionality to access. The following values are used: COMDispContext::METHOD, COMDispContext::PROPERTYGET, COMDispContext::PROPERTYPUT, and COMDispContext::PROPERTYPUTREF

<!-- -->

context  
The context of the functionality to access. The following values are used: COMDispContext::METHOD, COMDispContext::PROPERTYGET, COMDispContext::PROPERTYPUT, and COMDispContext::PROPERTYPUTREF

#### Remarks

It is important that you specify the correct context of the functionality in the COM object that you want to access, because a COM object can supply up to four functions that use the same name. Because of the possible name clashing, the context is used to distinguish the method or properties. To specify the correct context, see the documentation for the COM object that you want to access.

#### Examples

 

    { 
        InteropPermission perm; 
        COM com; 
        COMDispFunction funcShow; 
        COMDispFunction getValue; 
        COMDispFunction putValue; 
        ; 
      
        perm = new InteropPermission(InteropKind::ComInterop); 
        perm.assert(); 
        com = new COM("MyCOM.Object"); 
        funcShow = 
            new COMDispFunction(com, "show",  COMDispContext::METHOD); 
        getValue = 
            new COMDispFunction(com, "value", COMDispContext::PROPERTYGET); 
        putValue = 
            new COMDispFunction(com, "value", COMDispContext::PROPERTYPUT); 
    }

## Class COMError
    class COMError extends Object

The COMError class wraps any COM errors that occur during a COM method call.

### Remarks

When an error occurs during a COM method call, the error code and the error description are stored in the COMError object. The COMError object that is associated with a COM class is retrieved from the COM class by using the COM.error method.

### Examples

### Methods

| Method                   | Description                                                                                                               |
|--------------------------|---------------------------------------------------------------------------------------------------------------------------|
| public str description() | Returns a description of the error that occurred when the COM object was called.                                          |
| public int helpContext() | Returns the Help context ID for the error that occurred when the COM object was called.                                   |
| public str helpFile()    | Returns the name of the Help file that contains information about the error that occurred when the COM object was called. |
| public int number()      | Returns the error code of the error that occurred when the COM object was called.                                         |
| public str source()      | Returns the name of the component that caused the error that occurred when the COM object was called.                     |
| public str toString()    | Returns a string that contains the class handle and name, and sometimes additional information.                           |
| public void clear()      | Clears the properties of the COMError object.                                                                             |
| public void new()        | Initializes an instance of the COMError class.                                                                            |
| public void finalize()   |                                                                                                                           |

### Method description

Returns a description of the error that occurred when the COM object was called.

    public str description()

#### Return Value

The error description.

#### Remarks

The description might be empty if the COM object does not support handing out textual error messages. The description property is read-only.

### Method helpContext

Returns the Help context ID for the error that occurred when the COM object was called.

    public int helpContext()

#### Return Value

The Help context ID.

#### Remarks

The Help context ID might be 0 (zero) if the COM object does not support Help for its errors. The helpContext property is read-only.

### Method helpFile

Returns the name of the Help file that contains information about the error that occurred when the COM object was called.

    public str helpFile()

#### Return Value

The name of the Help file.

#### Remarks

The Help file might be empty if the COM object does not support Help for its errors. The helpFile property is read-only.

### Method number

Returns the error code of the error that occurred when the COM object was called.

    public int number()

#### Return Value

The error code; 0 (zero) if no error occurred when the COM object was called.

#### Remarks

The number property is read-only.

### Method source

Returns the name of the component that caused the error that occurred when the COM object was called.

    public str source()

#### Return Value

The source of the error.

#### Remarks

The source might be empty if the COM object does not support handing out the source of the error. The source property is read-only.

### Method toString

Returns a string that contains the class handle and name, and sometimes additional information.

    public str toString()

#### Return Value

A textual description of the class.

#### Remarks

For most classes, the string that is returned contains the class handle and name. However, for some classes, additional information is included in the string.

### Method clear

Clears the properties of the COMError object.

    public void clear()

#### Remarks

The properties of the COMError object are usually read-only, but they can be cleared by using this method.

### Method new

Initializes an instance of the COMError class.

    public void new()

### Method finalize

    public void finalize()

## Class CommaIo
    class CommaIo extends Io

The CommaIo class provides functionality for reading and writing comma-separated files.

### Remarks

This class has been replaced by the CommaTextIo class.

### Examples

### Methods

| Method                                       | Description                                                                                                                  |
|----------------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
| public int filePosition()                    |                                                                                                                              |
| public str inFieldDelimiter(\[str value\])   | Determines the delimiter used to separate fields in records accessed by the \*Io classes.                                    |
| public str inRecordDelimiter(\[str value\])  | Determines to the \*Io classes what character or characters to search for to determine whether a full record has been read.  |
| public int inRecordLength(\[int value\])     | Gets or sets the number of characters to read for each record in a file.                                                     |
| public str outFieldDelimiter(\[str value\])  | Gets or sets the sequence of characters that are written to a file that is used to separate the fields of a record.          |
| public str outRecordDelimiter(\[str value\]) | Gets or sets the sequence of characters that is written to the output files, which separate the records in the output files. |
| public container read()                      | Reads the next full record from the Io object.                                                                               |
| public IO\_Status status()                   | Retrieves the status of the last operation that was performed on the Io object.                                              |
| public boolean write(VarArg values)          | Writes values of a simple type.                                                                                              |
| public boolean writeExp(container data)      | Writes the content of a container to a file.                                                                                 |
| public void new(str filename, str mode)      | Creates a new object of the CommaIo class.                                                                                   |
| public void finalize()                       | Closes the file and, if data was written, flushes the file buffers to disk.                                                  |

### Method filePosition

    public int filePosition()

#### Return Value

### Method inFieldDelimiter

Determines the delimiter used to separate fields in records accessed by the \*Io classes.

    public str inFieldDelimiter([str value])

#### Parameters

value  

#### Return Value

The delimiter used to separate fields in records accessed by the \*Io classes.

### Method inRecordDelimiter

Determines to the \*Io classes what character or characters to search for to determine whether a full record has been read.

    public str inRecordDelimiter([str value])

#### Parameters

value  

#### Return Value

The character or characters that indicate whether a full record has been read.

#### Remarks

For standard text, the delimiter is a newline character.

### Method inRecordLength

Gets or sets the number of characters to read for each record in a file.

    public int inRecordLength([int value])

#### Parameters

value  

#### Return Value

The number of characters to read for each record in the file.

#### Remarks

For files that have a fixed-length format, use the inRecordLength property to guarantee that no more than the specified number of characters are read for each record.If the record format is overruled by a specified inRecordDelimiter property value , that is the inRecordDelimiter value is met before the fixed length is read, the record is accepted, and no additional data is read. To ensure that a fixed number of characters are read, set the inRecordDelimiter property value to an empty string. When no inRecordDelimiter property value is found, the inRecordDelimiter property value is the maximum limit of characters to read. Set the inRecordDelimiter property value to zero to disable the record length check.

### Method outFieldDelimiter

Gets or sets the sequence of characters that are written to a file that is used to separate the fields of a record.

    public str outFieldDelimiter([str value])

#### Parameters

value  

#### Return Value

The sequence of characters that are written to a file that is used to separate the fields of a record.

### Method outRecordDelimiter

Gets or sets the sequence of characters that is written to the output files, which separate the records in the output files.

    public str outRecordDelimiter([str value])

#### Parameters

value  

#### Return Value

The sequence of characters that is written to the output files.

#### Remarks

For standard text files, the delimiter is a newline character.

### Method read

Reads the next full record from the Io object.

    public container read()

#### Return Value

The next full record from the Io object.

#### Remarks

The definition of the next full record is controlled by the inFieldDelimiter, inRecordDelimiter, and inRecordLength properties. The record is returned as a container. Each entry in the container equals one field in the record. Each specialized Io class has default settings for the inFieldDelimiter, inRecordDelimiter, and inRecordLength properties to enable input and output in the most common formats. However, you might have to adjust these settings to support the desired format.

### Method status

Retrieves the status of the last operation that was performed on the Io object.

    public IO_Status status()

#### Return Value

The status of the last operation, in the form of a system enumeration.

#### Remarks

The return value is represented by the IO\_Status system enumeration. The range of possible IO\_Status values varies among Io classes.

#### Examples

This example shows how to use the status method. However, this example will not compile in a job, because it must be run in the context of a class, form, or other object.

    { 
        // Create an Io object and perform some operations. 
        if (myIo.status() == IO_Status::OK) 
        { 
            // Go ahead - the last operation was successful. 
        } 
    }

### Method write

Writes values of a simple type.

    public boolean write(VarArg values)

#### Parameters

values  
One or more values, each of a simple type, separated by a field delimiter. The simple types are string, integer, real, enum, and date.

#### Return Value

true if the write operation succeeds; otherwise, false. If the operation fails, you can check the status to learn the cause of the failure.

#### Remarks

The method accepts a variable number of arguments. Each value that is specified is put into the output record as a field. The first argument becomes the first field, the second argument becomes the second field, and so on. Fields are separated by the field delimiter that is specified in the outFieldDelimiter method. Records are separated by the delimiter that is specified by using the outRecordDelimiter method. To write complete containers, use the writeExp method.

### Method writeExp

Writes the content of a container to a file.

    public boolean writeExp(container data)

#### Parameters

data  
The container that holds data for the record.

#### Return Value

true if the operation succeeds; otherwise, false. If the operation fails, you can check the status to learn the cause of the failure.

#### Remarks

The entries in the container are treated as fields. The container itself is treated as a full record. Fields are separated by the delimiter that is specified by using the outFieldDelimiter method. Records are separated by the delimiter that is specified by using the outRecordDelimiter method.

#### Examples

This example uses a CommaIO object to read from the example file.

    { 
        container c; 
        CommaIo myfile; 
        FileIoPermission perm; 
      
        #define.ExampleFile(@"c:myfile.txt") 
        #define.ExampleOpenMode("w") 
      
        // Set code access permission to help protect the use 
        // of CommaIO.new 
        perm = new FileIoPermission(#ExampleFile, #ExampleOpenMode); 
        perm.assert(); 
      
        myfile = new CommaIo(#ExampleFile, #ExampleOpenMode); 
      
        // Assign the entries in the container according to record layout. 
        c = [1,"MyText",1.324,"Last field"]; 
        // Write this record according to file format  
        // (record/field delimiters). 
        myfile.writeExp(c); 
         
        // Close the code access permission. 
        CodeAccessPermission::revertAssert(); 
    }

### Method new

Creates a new object of the CommaIo class.

    public void new(str filename, str mode)

#### Parameters

filename  
The mode that the file should be opened in. Specify the mode as follows:

<!-- -->

mode  
The mode that the file should be opened in. Specify the mode as follows:

#### Remarks

A run-time error occurs if the file is accessed by using a method that does not correspond to the current mode. For example, an error occurs if a user tries to write to a file that is opened in read mode. If an attacker can control input to this method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission from the FileIOPermission class. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

#### Examples

The following example uses a CommaIO object to read from the ExampleFile file.

    { 
        CommaIo         io; 
        container       con; 
        FileIoPermission perm; 
      
        #define.ExampleFile(@"c:test.txt") 
        #define.ExampleOpenMode("r") 
      
        perm = new FileIoPermission(#ExampleFile, #ExampleOpenMode); 
        if (perm == null) 
        { 
            return; 
        } 
        // Grants permission to execute the CommaIo.new method. 
        // CommaIo.new runs under code access security. 
        perm.assert(); 
      
        io = new CommaIo(#ExampleFile, #ExampleOpenMode); 
        if (io != null) 
        { 
            con = io.read(); 
        } 
      
        // Close the code access permission scope. 
        CodeAccessPermission::revertAssert(); 
    }

### Method finalize

Closes the file and, if data was written, flushes the file buffers to disk.

    public void finalize()

#### Remarks

This method is not usually called directly; instead, the object is finalized by leaving the scope. The written output is not valid until the object is finalized.

## Class CommaTextIo
    class CommaTextIo extends Io

### Remarks

### Examples

### Methods

| Method                                                    | Description                                                                                                                  |
|-----------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
| public int filePosition()                                 |                                                                                                                              |
| public str inFieldDelimiter(\[str value\])                | Determines the delimiter used to separate fields in records accessed by the \*Io classes.                                    |
| public str inRecordDelimiter(\[str value\])               | Determines to the \*Io classes what character or characters to search for to determine whether a full record has been read.  |
| public int inRecordLength(\[int value\])                  | Gets or sets the number of characters to read for each record in a file.                                                     |
| public str outFieldDelimiter(\[str value\])               | Gets or sets the sequence of characters that are written to a file that is used to separate the fields of a record.          |
| public str outRecordDelimiter(\[str value\])              | Gets or sets the sequence of characters that is written to the output files, which separate the records in the output files. |
| public container read()                                   | Reads the next full record from the Io object.                                                                               |
| public IO\_Status status()                                | Retrieves the status of the last operation that was performed on the Io object.                                              |
| public boolean write(VarArg values)                       | Writes values of a simple type.                                                                                              |
| public boolean writeExp(container data)                   | Writes the content of a container to a file.                                                                                 |
| public void finalize()                                    | Closes the file and, if data was written, flushes the file buffers to disk.                                                  |
| public void new(str filename, str mode, \[int codepage\]) | Initializes a new instance of the Object class.                                                                              |

### Method filePosition

    public int filePosition()

#### Return Value

### Method inFieldDelimiter

Determines the delimiter used to separate fields in records accessed by the \*Io classes.

    public str inFieldDelimiter([str value])

#### Parameters

value  

#### Return Value

The delimiter used to separate fields in records accessed by the \*Io classes.

### Method inRecordDelimiter

Determines to the \*Io classes what character or characters to search for to determine whether a full record has been read.

    public str inRecordDelimiter([str value])

#### Parameters

value  

#### Return Value

The character or characters that indicate whether a full record has been read.

#### Remarks

For standard text, the delimiter is a newline character.

### Method inRecordLength

Gets or sets the number of characters to read for each record in a file.

    public int inRecordLength([int value])

#### Parameters

value  

#### Return Value

The number of characters to read for each record in the file.

#### Remarks

For files that have a fixed-length format, use the inRecordLength property to guarantee that no more than the specified number of characters are read for each record.If the record format is overruled by a specified inRecordDelimiter property value , that is the inRecordDelimiter value is met before the fixed length is read, the record is accepted, and no additional data is read. To guarantee that a fixed number of characters are read, set the inRecordDelimiter property value to an empty string. When no inRecordDelimiter property value is found, the inRecordDelimiter property value is the maximum limit of characters to read. Set the inRecordDelimiter property value to zero to disable the record length check.

### Method outFieldDelimiter

Gets or sets the sequence of characters that are written to a file that is used to separate the fields of a record.

    public str outFieldDelimiter([str value])

#### Parameters

value  

#### Return Value

The sequence of characters that are written to a file that is used to separate the fields of a record.

### Method outRecordDelimiter

Gets or sets the sequence of characters that is written to the output files, which separate the records in the output files.

    public str outRecordDelimiter([str value])

#### Parameters

value  

#### Return Value

The sequence of characters that is written to the output files.

#### Remarks

For standard text files, the delimiter is a newline character.

### Method read

Reads the next full record from the Io object.

    public container read()

#### Return Value

A container that holds the next full record from the Io object.

#### Remarks

The definition of the next full record is controlled by the inFieldDelimiter, inRecordDelimiter, and inRecordLength method properties. The record is returned as a container. Each entry in the container equals one field in the record. Each specialized Io class has default settings for the inFieldDelimiter, inRecordDelimiter, and inRecordLength properties. These default settings enable input and output in the most common formats. However, you might have to adjust these settings to support the desired format.

### Method status

Retrieves the status of the last operation that was performed on the Io object.

    public IO_Status status()

#### Return Value

The status of the last operation, as an IO\_Status system enumeration value.

#### Remarks

The range of IO\_Status values that can be returned varies, depending on the Io class.

### Method write

Writes values of a simple type.

    public boolean write(VarArg values)

#### Parameters

values  
A value of a simple type. The simple types are string, integer, real, enum, and date.

#### Return Value

true if the write operation is successful; otherwise, false. If the write operation fails, you can use the status method to determine the cause.

#### Remarks

The method accepts a variable number of arguments. Each value that is specified is put into the output record as a field. The first argument is the first field, the second argument is the second field, and so on. Fields are separated by the delimiter that is specified in the outFieldDelimiter method. Records are separated by the delimiter that is specified in the outRecordDelimiter method. To write complete containers, use the writeExp method.

### Method writeExp

Writes the content of a container to a file.

    public boolean writeExp(container data)

#### Parameters

data  
The container that holds data for the record.

#### Return Value

true if the operation is successful; otherwise, false.

#### Remarks

If this method returns false, check the status method for the cause. The entries in the container are treated as fields, and the container is treated as a full record. The field separator is defined in the outFieldDelimiter method. The record separator is defined in the outRecordDelimiter method.

### Method finalize

Closes the file and, if data was written, flushes the file buffers to disk.

    public void finalize()

#### Remarks

This method is not usually called directly. Instead, the object is usually finalized by leaving the scope. Written output is not valid until the object is finalized.

### Method new

Initializes a new instance of the Object class.

    public void new(str filename, str mode, [int codepage])

#### Parameters

filename  

<!-- -->

mode  

<!-- -->

codepage  

#### Remarks

If an attacker can control input to the new method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission from the FileIOPermission class. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

## Class CompileOutputInfos
    class CompileOutputInfos extends Object

### Remarks

### Examples

### Methods

| Method                               | Description |
|--------------------------------------|-------------|
| ::public static void NotifyChanges() |             |

### Method NotifyChanges

    public static void NotifyChanges()

## Class COMVariant
    class COMVariant extends Object

The COMVariant class is used as a generic class that can store different types of data. The class is used to pass arguments to the methods or properties of a COM (Component Object Model) Automation object and is used with the COM and COMDispFunction classes.

### Remarks

The data type of the COMVariant object can be set by:

-   The new method
-   The variantType method
-   The createFrom… methods. For example, the createFromBoolean method creates a COMVariant object of type VT\_BOOL (= Boolean).
-   The property methods. For example, if you set a new value by using the boolean property, and the object is not of type VT\_BOOL (= Boolean), it will be changed to this type.

The value of the data type is set by one of the property methods. For example, the value of a COMVariant object of type VT\_BOOL is set by the boolean method. The possible data types and the methods that set their values are listed in the Remarks section. The data types that the COMVariant class supports are not X++ data types, but data types defined by the COM Automation standard. The COMVariant class is based on the VARIANT structure found in the Win32 SDK. For more information see the Win32 SDK documentation. The property methods of the COMVariant class map to the COMVariantType values in the following way:

|             |               |                                                                                           |
|-------------|---------------|-------------------------------------------------------------------------------------------|
| boolean     | VT\_BOOL      |                                                                                           |
| bStr        | VT\_BSTR      | String data type                                                                          |
| byte        | VT\_UI1       |                                                                                           |
| char        | VT\_I1        |                                                                                           |
| currency    | VT\_CY        |                                                                                           |
| date, time  | VT\_DATE      | Date/time data type; both properties must be set.                                         |
| decimal     | VT\_DECIMAL   |                                                                                           |
| double      | VT\_R8        |                                                                                           |
| float       | VT\_R4        |                                                                                           |
| iDispatch   | VT\_DISPATCH  |                                                                                           |
| int, long   | VT\_I4        | VT\_I4 is used for both the int and the long data types                                   |
| iUnknown    | VT\_UNKNOWN   |                                                                                           |
| sCode       | VT\_ERROR     | The scode data type is a COM data type that is equivalent to the Win32 HRESULT data type. |
| short       | VT\_I2        |                                                                                           |
| uInt, uLong | VT\_UI4       | VT\_UI4 is used for both the uInt and the uLong data types                                |
| uShort      | VT\_UI2       |                                                                                           |
| variant     | VT\_VARIANT   |                                                                                           |
| safeArray   | VT\_SAFEARRAY | Array data type                                                                           |

### Examples

The following example instantiates a COM object that exposes a method called multiply which multiplies two floating point numbers passed in as COMVariant parameters.

    { 
        COM com; 
        COMVariant varArg1 = new COMVariant(); 
        COMVariant varArg2 = new COMVariant(); 
        COMVariant varRet; 
        real ret; 
        InteropPermission perm; 
      
        // Set code access permission to help protect the use  
        // of the COM object. 
        perm = new InteropPermission(InteropKind::ComInterop); 
        if (perm == null) 
        { 
            return; 
        } 
      
        // Permission scope starts here 
        perm.assert(); 
      
            com = new COM("MyCOM.Object"); 
      
        // Specify arguments for the 'multiply' method 
        varArg1.float(123); 
        varArg2.float(456); 
        varRet = com.multiply(varArg1, varArg2); 
      
        ret = varRet.double(); 
        // 'ret' is now 56088 (123*456) 
      
        // Close the code access permission scope. 
        CodeAccessPermission::revertAssert(); 
    }

### Methods

| Method                                                                                                    | Description                                                                                                                                                                 |
|-----------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public boolean boolean(\[boolean newValue\])                                                              | Gets or sets the value of a COMVariant object of the VT\_BOOL data type.                                                                                                    |
| public str bStr(\[str newValue\])                                                                         | Gets or sets the value of a COMVariant object of the VT\_BSTR data type.                                                                                                    |
| public int byte(\[int newValue\])                                                                         | Gets or sets the value of a COMVariant object of the VT\_UI1 data type.                                                                                                     |
| public int char(\[int newValue\])                                                                         | Gets or sets the value of a COMVariant object of the VT\_I1 data type.                                                                                                      |
| public container container(\[container newValue\], \[COMVariantType newType\])                            | Gets or sets the value of a COMVariant object of the container data type.                                                                                                   |
| public Real currency(\[Real newValue\])                                                                   | Gets or sets the value of a COMVariant object of the VT\_CY data type.                                                                                                      |
| public Date date(\[Date newValue\])                                                                       | Gets or sets the date part of the value of a COMVariant object of the VT\_DATE data type.                                                                                   |
| public Real decimal(\[Real newValue\])                                                                    | Gets or sets the value of a COMVariant object of the VT\_DECIMAL data type.                                                                                                 |
| public Real double(\[Real newValue\])                                                                     | Gets or sets the value of a COMVariant object of the VT\_R8 data type.                                                                                                      |
| public Real float(\[Real newValue\])                                                                      | Gets or sets the value of a COMVariant object of the VT\_R4 data type.                                                                                                      |
| public ComInterface iDispatch(\[ComInterface newValue\])                                                  | Gets or sets the value of a COMVariant object of the VT\_DISPATCH data type.                                                                                                |
| public int int(\[int newValue\])                                                                          | Gets or sets the value of a COMVariant object of the VT\_I4 data type.                                                                                                      |
| public ComInterface iUnknown(\[ComInterface newValue\])                                                   | Gets or sets the value of a COMVariant object of the VT\_UNKNOWN (IUnknown) data type.                                                                                      |
| public int long(\[int newValue\])                                                                         | Gets or sets the value of a COMVariant object of the VT\_I4 data type.                                                                                                      |
| public Int64 longLong(\[Int64 newValue\])                                                                 | Gets or sets the value of a COMVariant object of the VT\_I8 (longlong) data type.                                                                                           |
| public Array safeArray(\[Array newValue\], \[COMVariantType newType\])                                    | Gets or sets the value of a COMVariant object of the VT\_SAFEARRAY data type.                                                                                               |
| public int sCode(\[int newValue\])                                                                        | Gets or sets the value of a COMVariant object of the VT\_ERROR data type.                                                                                                   |
| public int short(\[int newValue\])                                                                        | Gets or sets the value of a COMVariant object of the VT\_I2 (short) data type.                                                                                              |
| public int time(\[int newValue\])                                                                         | Gets or sets the time part of the value of a COMVariant object of the VT\_DATE data type.                                                                                   |
| public str toString()                                                                                     | Creates a string representation of a COMVariant object. This string representation includes the value and type of the object.                                               |
| public int uInt(\[int newValue\])                                                                         | Gets or sets the value of a COMVariant object of the VT\_UI4 data type.                                                                                                     |
| public int uLong(\[int newValue\])                                                                        | Gets or sets the value of a COMVariant object of the VT\_UI4 (unsigned long) data type.                                                                                     |
| public Int64 uLongLong(\[Int64 newValue\])                                                                | Gets or sets the value of a COMVariant object of the VT\_UI8 (unsigned longlong) data type.                                                                                 |
| public int uShort(\[int newValue\])                                                                       | Gets or sets the value of a COMVariant object of the VT\_UI2 data type.                                                                                                     |
| public COMVariant variant(\[COMVariant newValue\])                                                        | Gets or sets the value of a COMVariant object of the VT\_VARIANT (variant) data type.                                                                                       |
| public COMVariantInOut variantInOutFlag(\[COMVariantInOut newValue\])                                     | Sets or returns the InOutFlag setting for a COMVariant object.                                                                                                              |
| public COMVariantType variantType(\[COMVariantType newValue\])                                            | Queries a COMVariant object for its variant data type or changes the data type.                                                                                             |
| ::public static COMVariant createDateFromYMD(int year, int month, int day, \[COMVariantInOut inOutFlag\]) | Creates a new COMVariant object and initializes it with a date value in one operation.                                                                                      |
| ::public static COMVariant createFromArray(Array value, \[COMVariantInOut inOutFlag\])                    | Creates a new COMVariant object and initializes it with an array in one operation.                                                                                          |
| ::public static COMVariant createFromBoolean(boolean value, \[COMVariantInOut inOutFlag\])                | Creates a new COMVariant object and initializes it with a Boolean value in one operation.                                                                                   |
| ::public static COMVariant createFromCOM(COM value, \[COMVariantInOut inOutFlag\])                        | Creates a new COMVariant object and initializes it with a COM class in one operation.                                                                                       |
| ::public static COMVariant createFromDate(Date value, \[COMVariantInOut inOutFlag\])                      | Creates a new COMVariant object and initializes it with a date value in one operation.                                                                                      |
| ::public static COMVariant createFromDateAndTime(Date date, int time, \[COMVariantInOut inOutFlag\])      | Creates a new COMVariant object and initializes it with a date and time in one operation.                                                                                   |
| ::public static COMVariant createFromInt(int value, \[COMVariantInOut inOutFlag\])                        | Creates a new COMVariant object and initializes it with an integer value in one operation.                                                                                  |
| ::public static COMVariant createFromInt64(Int64 value, \[COMVariantInOut inOutFlag\])                    | Creates a new COMVariant object and initializes it with an int64 value (longLong or uLongLong) in one operation.                                                            |
| ::public static COMVariant createFromReal(Real value, \[COMVariantInOut inOutFlag\])                      | Creates a new COMVariant object and initializes it with a real value in one operation.                                                                                      |
| ::public static COMVariant createFromStr(str value, \[COMVariantInOut inOutFlag\])                        | Creates a new COMVariant object and initializes it with a string in one operation.                                                                                          |
| ::public static COMVariant createFromTime(int value, \[COMVariantInOut inOutFlag\])                       | Creates a new COMVariant object and initializes it with a time value in one operation.                                                                                      |
| ::public static COMVariant createFromUtcDateTime(DateTime value, \[COMVariantInOut inOutFlag\])           |                                                                                                                                                                             |
| ::public static COMVariant createNoValue()                                                                | Creates a COMVariant object of the VT\_ERROR variant type with no value.                                                                                                    |
| public void new(\[COMVariantInOut inOutFlag\], \[COMVariantType type\])                                   | Creates a COMVariant object that can be used to pass arguments to the methods or properties of a COM Automation object.                                                     |
| public void noValue()                                                                                     | Deletes the contents of an existing COMVariant object and enables it to act as an unspecified argument when it is used in the COMDispFunction.call method or the COM class. |
| public void finalize()                                                                                    | Not implemented. You can override this method if you need to explicitly destruct an object.                                                                                 |

### Method boolean

Gets or sets the value of a COMVariant object of the VT\_BOOL data type.

    public boolean boolean([boolean newValue])

#### Parameters

newValue  
The new value; optional.

#### Return Value

The current value.

#### Remarks

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. A COMVariant object has a Boolean type if its data type is set to COMVariantType::VT\_BOOL. The COM Boolean data type may also be referred to as "VARIANT\_BOOL".

#### Examples

The following example creates a new COMVariant object of type VT\_BOOL and sets the value to true.

    { 
        COMVariant var = new COMVariant( 
            COMVariantInOut::IN_OUT,  
            COMVariantType::VT_BOOL); 
     
        // Set value of the object 
        var.boolean(true); 
    }

### Method bStr

Gets or sets the value of a COMVariant object of the VT\_BSTR data type.

    public str bStr([str newValue])

#### Parameters

newValue  
The new value; optional.

#### Return Value

The current string value.

#### Remarks

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. A COMVariant object has a string data type if its data type is set to COMVariantType::VT\_BSTR. The BStr data type is a COM data type that is used for handling strings.

#### Examples

The following example creates a new COMVariant object of type VT\_BSTR, and sets the value to "Hello World."

    { 
        COMVariant var = new COMVariant( 
            COMVariantInOut::IN_OUT,  
            COMVariantType::VT_BSTR); 
      
        // Set string value of the object 
        var.bStr("Hello World"); 
    }

### Method byte

Gets or sets the value of a COMVariant object of the VT\_UI1 data type.

    public int byte([int newValue])

#### Parameters

newValue  
The new value; optional.

#### Return Value

The current value.

#### Remarks

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. A COMVariant object has a byte data type if its data type is set to COMVariantType::VT\_UI1. You can also use "unsigned char" to refer to the COM byte data type.

#### Examples

The following example creates a new COMVariant object of the VT\_UI1 type and sets the value to 123.

    { 
        COMVariant var = new COMVariant( 
            COMVariantInOut::IN_OUT,  
            COMVariantType::VT_UI1); 
      
        // Set value of the object 
        var.byte(123); 
    }

### Method char

Gets or sets the value of a COMVariant object of the VT\_I1 data type.

    public int char([int newValue])

#### Parameters

newValue  
The new value; optional.

#### Return Value

The current value.

#### Remarks

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. A COMVariant object has a char data type if its data type is set to COMVariantType::VT\_I1.

#### Examples

The following example creates a new COMVariant object of type VT\_I1 and sets the value tothe numeric value of A, which is 65.

    { 
        COMVariant var = new COMVariant( 
            COMVariantInOut::IN_OUT,  
            COMVariantType::VT_I1); 
      
        // Set value of the object 
        var.char(Char2Num("A", 1)); 
    }

### Method container

Gets or sets the value of a COMVariant object of the container data type.

    public container container([container newValue], [COMVariantType newType])

#### Parameters

newValue  
The type of the new container; optional. The default is for the container to store integers.

<!-- -->

newType  
The type of the new container; optional. The default is for the container to store integers.

#### Return Value

The current container.

#### Remarks

The possible values for the newType parameter are a subset of the values that are supplied by the COMVariantType system enum:

-   VT\_I2
-   VT\_I4
-   VT\_R4
-   VT\_R8
-   VT\_CY
-   VT\_DATE
-   VT\_BSTR
-   VT\_ERROR
-   VT\_BOOL
-   VT\_DECIMAL
-   VT\_I1
-   VT\_UI1
-   VT\_UI2
-   VT\_UI4
-   VT\_I8
-   VT\_UI8
-   VT\_INT
-   VT\_UINT

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. When a container is stored in a COMVariant object, the binary representation of the container is stored in a binary array (see the COMVariant.safeArray method). The container property is useful when you need to store data in a database COM object and then later read the data back into Microsoft Dynamics AX without the COM object processing the data. The container property is an advanced property of the COMVariant class. It should be used with caution because the content of the binary array that the container is stored in, inside the COMVariant object, must not be changed by any COM object.

#### Examples

The following example creates a new COMVariant object of type container. The data in the container is passed to, and used by, a database COM object. Note The code in the following section contains a hypothetical COM object MyDatabaseCOM.Object" and will therefore not run in Microsoft Dynamics AX, unless such an object is created outside Microsoft Dynamics AX.

    { 
        COM com; 
        COMVariant var = new COMVariant(); 
        container con; 
        InteropPermission perm; 
      
        // Set code access permission to help protect use of COM object 
        perm = new InteropPermission(InteropKind::ComInterop); 
        if (perm == null) 
        { 
            return; 
        } 
      
        // Permission scope starts here 
        perm.assert(); 
      
        // Put some data in the container 
        con = conins(con, 1, "Element 1"); 
        con = conins(con, 2, "Element 2"); 
        // Set value of the object and ensure the data 
        // is stored in a binary array of bytes 
        var.container(con, COMVariantType::VT_UI1); 
      
        // Create a database object to store the data in 
        com = new COM("MyDatabaseCOM.Object"); 
        com.writeData(var); 
        // ... 
      
        // Close code access permission 
        CodeAccessPermission::revertAssert(); 
    }

### Method currency

Gets or sets the value of a COMVariant object of the VT\_CY data type.

    public Real currency([Real newValue])

#### Parameters

newValue  
The new value; optional.

#### Return Value

The current value.

#### Remarks

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. A COMVariant object has a currency data type if its data type is set to COMVariantType::VT\_CY. The currency data type is a COM data type that is optimized for currency values. It is a real number with four decimal places. Sometimes "CY" is also used to refer to the COM currency data type.

#### Examples

The following example creates a new COMVariant object of type VT\_CY and sets the value to 123.4567.

    { 
        COMVariant var = new COMVariant( 
            COMVariantInOut::IN_OUT,  
            COMVariantType::VT_CY); 
      
        // Set value of the object 
        var.currency(123.4567); 
    }

### Method date

Gets or sets the date part of the value of a COMVariant object of the VT\_DATE data type.

    public Date date([Date newValue])

#### Parameters

newValue  
The new value; optional.

#### Return Value

The current value.

#### Remarks

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. A COMVariant object has a date and time data type if its data type is set to COMVariantType::VT\_DATE. When you set the value of the object, you must set the time part of the value in addition to the date. To set the time part of the value, use the time property.

#### Examples

The following example creates a COMVariant object of type VT\_DATE and sets the date part of the value to 24 December 1998, and the time part of the value to 13.24.

    { 
        COMVariant var = new COMVariant( 
            COMVariantInOut::IN_OUT,  
            COMVariantType::VT_DATE); 
      
        // Set value of the object 
        var.date(Str2Date("12.24.1998", 213)); 
        var.time(Str2Time("13:24:00")); 
    }

### Method decimal

Gets or sets the value of a COMVariant object of the VT\_DECIMAL data type.

    public Real decimal([Real newValue])

#### Parameters

newValue  
The new value; optional.

#### Return Value

The current value.

#### Remarks

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. A COMVariant object has a decimal type if its data type is set to COMVariantType::VT\_DECIMAL. The decimal data type is a COM data type that provides size and scale for a number. There is no parallel to the decimal data type in X++.

#### Examples

The following example creates a new COMVariant object of type VT\_DECIMAL and sets the value to 123.456.

    { 
        COMVariant var = new COMVariant( 
            COMVariantInOut::IN_OUT,  
            COMVariantType::VT_DECIMAL); 
      
        // Set value of the object 
        var.decimal(123.456); 
    }

### Method double

Gets or sets the value of a COMVariant object of the VT\_R8 data type.

    public Real double([Real newValue])

#### Parameters

newValue  
The new value; optional.

#### Return Value

The current value.

#### Remarks

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. A COMVariant object has a double data type if its data type is set to COMVariantType::VT\_R8.

#### Examples

The following example creates a new COMVariant object of type VT\_R8 and sets the value to 123.456.

    { 
        COMVariant var = new COMVariant( 
            COMVariantInOut::IN_OUT,  
            COMVariantType::VT_R8); 
      
        // Set value of the object 
        var.double(123.456); 
    }

### Method float

Gets or sets the value of a COMVariant object of the VT\_R4 data type.

    public Real float([Real newValue])

#### Parameters

newValue  
The new value; optional.

#### Return Value

The current value.

#### Remarks

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. A COMVariant object has a float type if its data type is set to COMVariantType::VT\_R4. Sometimes "single" is also used to refer to the COM float data type.

#### Examples

The following example creates a new COMVariant object of type VT\_R4 and sets the value to 123.456.

    { 
        COMVariant var = new COMVariant( 
            COMVariantInOut::IN_OUT,  
            COMVariantType::VT_R4); 
      
        // Set value of the object 
        var.float(123.456); 
    }

### Method iDispatch

Gets or sets the value of a COMVariant object of the VT\_DISPATCH data type.

    public ComInterface iDispatch([ComInterface newValue])

#### Parameters

newValue  
The new value; optional.

#### Return Value

The current value.

#### Remarks

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. A COMVariant object has an IDispatch data type if its data type is set to COMVariantType::VT\_DISPATCH. The IDispatch data type is a COM data type that provides a handle to a COM IDispatch interface.

#### Examples

The following example creates a new COMVariant object of type VT\_DISPATCH.

    { 
        COMVariant var = new COMVariant( 
            COMVariantInOut::IN_OUT,  
            COMVariantType::VT_DISPATCH); 
        COMInterface comInterface; 
      
        // Here, the comInterface variable must be assigned 
        // a COM IDispatch interface 
        //… 
     
        // Set value of the object 
        var.iDispatch(comInterface); 
    }

### Method int

Gets or sets the value of a COMVariant object of the VT\_I4 data type.

    public int int([int newValue])

#### Parameters

newValue  
The new value; optional.

#### Return Value

The current value.

#### Remarks

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. The COMVariantType::VT\_I4 data type is also used for the long variant type. The COMVariant.long method is identical to this method; the two methods exist for completeness.

#### Examples

The following example creates a COMVariant object of type VT\_I4 and sets the value to 123456.

    { 
        COMVariant var = new COMVariant( 
            COMVariantInOut::IN_OUT,  
            COMVariantType::VT_I4); 
      
        // Set value of the object 
        var.int(123456); 
    }

### Method iUnknown

Gets or sets the value of a COMVariant object of the VT\_UNKNOWN (IUnknown) data type.

    public ComInterface iUnknown([ComInterface newValue])

#### Parameters

newValue  
The new value; optional.

#### Return Value

The current value.

#### Remarks

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type value. A COMVariant object has an IUnknown data type if its data type is set to COMVariantType::VT\_UNKNOWN. The IUnknown data type is a COM data type that provides a handle to a COM IUnknown interface.

#### Examples

The following example creates a new COMVariant object of type VT\_UNKNOWN.

    { 
        COMVariant var = new COMVariant( 
            COMVariantInOut::IN_OUT,  
            COMVariantType::VT_UNKNOWN); 
        COMInterface comInterface; 
      
        // comInterface variable is assigned 
        // a COM IUnknown interface 
        // ... 
      
        // Set value of the object 
        var.iUnknown(comInterface); 
    }

### Method long

Gets or sets the value of a COMVariant object of the VT\_I4 data type.

    public int long([int newValue])

#### Parameters

newValue  
The new value; optional.

#### Return Value

The current value.

#### Remarks

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. The COMVariantType::VT\_I4 data type is also used for the int variant type. The COMVariant.int method is identical to this method; the two methods exist for completeness.

#### Examples

The following example creates a COMVariant object of type VT\_I4 and sets the value to 123456.

    { 
        COMVariant var = new COMVariant( 
            COMVariantInOut::IN_OUT,  
            COMVariantType::VT_I4); 
      
        // Set value of the object 
        var.long(123456); 
    }

### Method longLong

Gets or sets the value of a COMVariant object of the VT\_I8 (longlong) data type.

    public Int64 longLong([Int64 newValue])

#### Parameters

newValue  
The new value; optional.

#### Return Value

The current value.

#### Remarks

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the value’s data type. A COMVariant object has a longlong variant type if its data type is set to COMVariantType::VT\_I8.

#### Examples

The following example creates a new COMVariant object of type VT\_I8 and sets the value to 2,305,843,009,213,693,952.

    { 
        COMVariant var = new COMVariant( 
            COMVariantInOut::IN_OUT,  
            COMVariantType::VT_BOOL); 
      
        // Set value of the object 
        var.longLong(2305843009213693952); 
    }

### Method safeArray

Gets or sets the value of a COMVariant object of the VT\_SAFEARRAY data type.

    public Array safeArray([Array newValue], [COMVariantType newType])

#### Parameters

newValue  
The type of the new array; optional.

<!-- -->

newType  
The type of the new array; optional.

#### Return Value

The current array.

#### Remarks

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. A COMVariant object has an array Boolean type if its data type is set to COMVariantType::VT\_SAFEARRAY. A safe array is COM's equivalent to an array. Currently only one-dimensional safe arrays are supported.

#### Examples

The following example creates a new COMVariant object of type VT\_SAFEARRAY and initializes it with an array of shorts.

    { 
        int i, result; 
        COM com; 
        COMVariant var = new COMVariant( 
            COMVariantInOut::IN_OUT,  
            COMVariantType::VT_SAFEARRAY); 
        Array arr = new Array(Types::INTEGER); 
      
        // Insert 10 values in the array 
        for (i = 1; i <= 10; i++) 
        { 
            arr.value(i, i); 
        } 
      
        // Set value of the object and ensure the integer values 
        // are treated as short data types 
        var.safeArray(arr, COMVariantType::VT_I2); 
    }

### Method sCode

Gets or sets the value of a COMVariant object of the VT\_ERROR data type.

    public int sCode([int newValue])

#### Parameters

newValue  
The new value; optional.

#### Return Value

The current value.

#### Remarks

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. A COMVariant object has an scode data type if its data type is set to COMVariantType::VT\_ERROR. The scode data type is a COM data type that is equivalent to the Win32 HRESULT data type, which is most used as return values for COM functions.

#### Examples

The following example creates a new COMVariant object of type VT\_ERROR and sets the value to 0x80001004.

    { 
        COMVariant var = new COMVariant( 
            COMVariantInOut::IN_OUT,  
            COMVariantType::VT_ERROR); 
      
        // Set value of the object 
        var.sCode(0x80001004); 
    }

### Method short

Gets or sets the value of a COMVariant object of the VT\_I2 (short) data type.

    public int short([int newValue])

#### Parameters

newValue  
The new value; optional.

#### Return Value

The current value.

#### Remarks

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. A COMVariant object has a short data type if its data type is set to COMVariantType::VT\_I2.

#### Examples

The following example creates a new COMVariant object of the VT\_I2 type and sets the value to 123.

    { 
        COMVariant var = new COMVariant( 
            COMVariantInOut::IN_OUT,  
            COMVariantType::VT_I2); 
      
        // Set value of the object 
        var.short(123); 
    }

### Method time

Gets or sets the time part of the value of a COMVariant object of the VT\_DATE data type.

    public int time([int newValue])

#### Parameters

newValue  
The new value; optional.

#### Return Value

The current value.

#### Remarks

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. A COMVariant object has a date and time data type if its data type is set to COMVariantType::VT\_DATE. When you set the value of the object, you must set the date part of the value in addition to the time. To set the date part of the value, use the date property.

#### Examples

The following example creates a COMVariant object of type VT\_DATE and sets the date part of the value to 24 December 1998, and the time part of the value to 13.24.

    { 
        COMVariant var = new COMVariant( 
            COMVariantInOut::IN_OUT,  
            COMVariantType::VT_DATE); 
      
        // Set value of the object 
        var.date(Str2Date("12.24.1998", 213)); 
        var.time(Str2Time("13:24:00")); 
    }

### Method toString

Creates a string representation of a COMVariant object. This string representation includes the value and type of the object.

    public str toString()

#### Return Value

The string representation of the COMVariant object.

#### Remarks

The actual string returned from this method depends on the variant data type of the COMVariant object.

#### Examples

The following example creates a COMVariant object and assigns the current date to it. It then prints a description of the object to the Infolog.

    COMVariant theDay; 
     
    theDay = COMVariant::createFromDate(today()); 
    info(theDay.toString());

### Method uInt

Gets or sets the value of a COMVariant object of the VT\_UI4 data type.

    public int uInt([int newValue])

#### Parameters

newValue  
The new value; optional.

#### Return Value

The current value.

#### Remarks

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. The COMVariantType::VT\_UI4 data type is also used for the uLong data type.

#### Examples

The following example creates a new COMVariant object of the VT\_UI4 type and sets the value to 123456.

    { 
        COMVariant var = new COMVariant( 
            COMVariantInOut::IN_OUT,  
            COMVariantType::VT_UI4); 
      
        // Set value of the object 
        var.uInt(123456); 
    }

### Method uLong

Gets or sets the value of a COMVariant object of the VT\_UI4 (unsigned long) data type.

    public int uLong([int newValue])

#### Parameters

newValue  
The new value; optional.

#### Return Value

The current value.

#### Remarks

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. The COMVariantType::VT\_UI4 data type is also used for the uInt data type.

#### Examples

The following example creates a new COMVariant object of type VT\_UI4 and sets the value to 123456.

    { 
        COMVariant var = new COMVariant( 
            COMVariantInOut::IN_OUT,  
            COMVariantType::VT_UI4); 
      
        // set value of the object 
        var.uLong(123456); 
    }

### Method uLongLong

Gets or sets the value of a COMVariant object of the VT\_UI8 (unsigned longlong) data type.

    public Int64 uLongLong([Int64 newValue])

#### Parameters

newValue  
The new value; optional.

#### Return Value

The current value.

#### Remarks

If you pass in a value that has a different data type than the object, the object’s data type will be changed to match the value’s data type. A COMVariant object has an unsigned longlong variant type if its data type is set to COMVariantType::VT\_I8.

#### Examples

The following example creates a new COMVariant object of type VT\_I8 and sets the value to 9,223,372,036,854,775,808.

    { 
        COMVariant var = new COMVariant( 
            COMVariantInOut::IN_OUT,  
            COMVariantType::VT_BOOL); 
      
        // Set value of the object 
        var.longLong(9223372036854775808); 
    }

### Method uShort

Gets or sets the value of a COMVariant object of the VT\_UI2 data type.

    public int uShort([int newValue])

#### Parameters

newValue  
The new value; optional.

#### Return Value

The current value.

#### Remarks

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. A COMVariant object has an unsigned short data type if its data type is set to COMVariantType::VT\_UI2.

#### Examples

The following example creates a new COMVariant object of type VT\_UI2 and sets the value to 12345.

    { 
        COMVariant var = new COMVariant( 
            COMVariantInOut::IN_OUT,  
            COMVariantType::VT_UI2); 
      
        // Set value of the object 
        var.uShort(12345); 
    }

### Method variant

Gets or sets the value of a COMVariant object of the VT\_VARIANT (variant) data type.

    public COMVariant variant([COMVariant newValue])

#### Parameters

newValue  
The new value; optional.

#### Return Value

The current value.

#### Remarks

The variant property is used to nest one COMVariant object in another COMVariant object. When using the parent object as the argument in a call to COMDispFunction.call or in a call to the COM class, the called method will automatically extract the data of the nested object. This nesting facility is useful when a method on a COM object can work with multiple data types. Only one level of variant nesting is allowed. If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. A COMVariant object has a variant type if its data type is set to COMVariantType::VT\_VARIANT.

#### Examples

The following example creates a COMVariant object of type VT\_I4 (long), and a COMVariant object of type VT\_VARIANT. The object of type VT\_VARIANT is assigned the value of the object of type VT\_I4. The code below contains a hypothetical COM object ("MyCOM.Object"), and will therefore not run in Microsoft Dynamics AX, unless such an object is created outside Microsoft Dynamics AX.

    { 
        COM com; 
        COMDispFunction funcShow; 
      
        COMVariant var1 = new COMVariant( 
            COMVariantInOut::IN_OUT,  
            COMVariantType::VT_I4); 
      
        COMVariant var2 = new COMVariant( 
            COMVariantInOut::IN_OUT,  
            COMVariantType::VT_VARIANT); 
      
        InteropPermission perm1; 
        InteropPermission perm2; 
      
        // Set code access permission to help protect use of COM object 
        perm1 = new InteropPermission(InteropKind::ComInterop); 
        perm1.assert(); 
      
        com = new COM("MyCOM.Object"); 
      
        // Close code access permission for COM 
        CodeAccessPermission::revertAssert(); 
      
        // Set value of 'var1' 
        var1.Long(123456); 
        // Set value of 'var2' to 'var1' 
        var2.Variant(var1); 
      
        // Set code access permission to protect use of 
        // COMDispFunction object 
        perm2 = new InteropPermission(InteropKind::ComInterop); 
        perm2.assert(); 
      
        funcShow = new COMDispFunction( 
            com,  
            "Show",  
            COMDispContext::METHOD); 
     
        // Call funcShow with a long 
        funcShow.Call(var2); 
        // Change value of 'var1' 
         var1.BStr("Hello World"); 
        // Call funcShow with a string 
        funcShow.Call(var2); 
      
        // Close code access permission for COMDispFunction 
        CodeAccessPermission::revertAssert(); 
    }

### Method variantInOutFlag

Sets or returns the InOutFlag setting for a COMVariant object.

    public COMVariantInOut variantInOutFlag([COMVariantInOut newValue])

#### Parameters

newValue  
The new InOutFlag setting; optional.

#### Return Value

The current InOutFlag setting.

#### Remarks

The following is a list of possible values for the newValue parameter.

-   COMVariantInOut::IN
-   COMVariantInOut::IN\_OUT
-   COMVariantInOut::OUT
-   COMVariantInOut::OUT\_RETVAL.

The InOutFlag setting describes how the data that is stored in the object is treated when the object is used as an argument in the COMDispFunction.call method. The possible values of the InOutFlag setting correspond to the values for COM Automation objects described in the Win32 SDK. The data stored in the COMVariant object is unaffected when the InOutFlag setting is changed.

#### Examples

The following example creates a COMVariant object that has the InOutFlag setting set to IN, and then uses the variantInOutFlag method to change the setting to OUT.

    { 
        COMVariant var = new COMVariant(COMVariantInOut::IN); 
      
        // Change the 'var' object to be used as an out argument 
        var.variantInOutFlag(COMVariantInOut::OUT); 
    }

### Method variantType

Queries a COMVariant object for its variant data type or changes the data type.

    public COMVariantType variantType([COMVariantType newValue])

#### Parameters

newValue  
The new variant data type; optional.

#### Return Value

The current variant data type.

#### Remarks

The possible values for the newValue parameter are:

-   COMVariantType::VT\_I2
-   COMVariantType::VT\_I4
-   COMVariantType::VT\_R4
-   COMVariantType::VT\_R8
-   COMVariantType::VT\_CY
-   COMVariantType::VT\_DATE
-   COMVariantType::VT\_BSTR
-   COMVariantType::VT\_DISPATCH
-   COMVariantType::VT\_ERROR
-   COMVariantType::VT\_BOOL
-   COMVariantType::VT\_VARIANT
-   COMVariantType::VT\_UNKNOWN
-   COMVariantType::VT\_DECIMAL
-   COMVariantType::VT\_I1
-   COMVariantType::VT\_UI1
-   COMVariantType::VT\_UI2
-   COMVariantType::VT\_UI4

The variant data type describes how the data that is stored in the object is treated when the object is used as an argument in a call to the COMDispFunction.call method or a call to the COM class. If you change the data type, the data that is held in the object is deleted. See the \[COMVariant.new\] for information about the available variant data types.

#### Examples

The following example creates a new COMVariant object and sets it to be of long (VT\_I4) data type. The variantType method is then used to change the data type to VT\_DATE (date). The data that is held by the object is discarded.

    { 
        COMVariant var = new COMVariant(); 
      
        // Set the 'var' object to be a long 
        var.long(123); 
      
        // Change var so that it can store a date 
        var.variantType(COMVariantType::VT_DATE); 
    }

### Method createDateFromYMD

Creates a new COMVariant object and initializes it with a date value in one operation.

    public static COMVariant createDateFromYMD(int year, int month, int day, [COMVariantInOut inOutFlag])

#### Parameters

year  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are: COMVariantInOut::OUT\_RETVAL

<!-- -->

month  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are: COMVariantInOut::OUT\_RETVAL

<!-- -->

day  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are: COMVariantInOut::OUT\_RETVAL

<!-- -->

inOutFlag  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are: COMVariantInOut::OUT\_RETVAL

#### Return Value

The new COMVariant object.

#### Remarks

The COMVariant object that is created by this method has the data type VT\_DATE (date/time). This method allows you to use dates that are outside the range for the Microsoft Dynamics AXdate data type (0111901 to 31122154). For dates within the date range, you can use the COMVariant.createFromDate method.

#### Examples

The following example creates a COMVariant object and initializes it with the date 01 January 4015.

    COMVariant myDate; 
     
    myDate = COMVariant::createDateFromYMD(4015,1,1);

### Method createFromArray

Creates a new COMVariant object and initializes it with an array in one operation.

    public static COMVariant createFromArray(Array value, [COMVariantInOut inOutFlag])

#### Parameters

value  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

<!-- -->

inOutFlag  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

#### Return Value

The new COMVariant object.

#### Remarks

The COMVariant object that is created by this method has the data type VT\_SAFEARRAY (array). You can change the data type of an existing COMVariant object to VT\_SAFEARRAY by using the variantType method or by passing in an array value by using the safeArray property method.

#### Examples

The following example creates a new COMVariant object and initializes it with an array of integers.

    { 
        int i; 
        COMVariant var; 
        Array arr = new Array(Types::INTEGER); 
      
        for (i = 1; i <= 10; i++) 
            // Insert 10 values in the array 
            arr.value(i, i); 
      
        // Create and initialize a COMVariant object  
        var = COMVariant::createFromArray(arr); 
    }

### Method createFromBoolean

Creates a new COMVariant object and initializes it with a Boolean value in one operation.

    public static COMVariant createFromBoolean(boolean value, [COMVariantInOut inOutFlag])

#### Parameters

value  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

<!-- -->

inOutFlag  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

#### Return Value

The new COMVariant object.

#### Remarks

The COMVariant object that is created by this method has the data type VT\_BOOL (Boolean). You can change the data type of an existing COMVariant object to VT\_BOOL by using the variantType method or by passing in a Boolean value by using the boolean property method.

#### Examples

The following example creates a COMVariant object of the VT\_BOOL variant data type (Boolean), and sets the value to true.

    { 
        COMVariant var; 
      
        var = COMVariant::createFromBoolean(TRUE); 
    }

### Method createFromCOM

Creates a new COMVariant object and initializes it with a COM class in one operation.

    public static COMVariant createFromCOM(COM value, [COMVariantInOut inOutFlag])

#### Parameters

value  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

<!-- -->

inOutFlag  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

#### Return Value

The new COMVariant object.

#### Remarks

Possible values of the inOutFlag parameter are as follows:

-   COMVariantInOut::IN
-   COMVariantInOut::IN\_OUT
-   COMVariantInOut::OUT
-   COMVariantInOut::OUT\_RETVAL

#### Examples

The following example creates a new COMVariant object and initializes it with a COM object.

    { 
        COMVariant var; 
        COM com = new COM("MyCOM.Object"); 
      
        var = COMVariant::createFromCOM(com); 
    }

### Method createFromDate

Creates a new COMVariant object and initializes it with a date value in one operation.

    public static COMVariant createFromDate(Date value, [COMVariantInOut inOutFlag])

#### Parameters

value  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

<!-- -->

inOutFlag  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

#### Return Value

The new COMVariant object.

#### Remarks

The COMVariant object that is created by this method has the data type VT\_DATE (date/time). You can change the data type of an existing COMVariant object to VT\_DATE by using the variantType method or by passing in a time value by using the date property method. If you want to use a date that is outside the range for the Axapta date type (0111901 to 31122154), use the COMVariant.createDateFromYMD method.

#### Examples

The following example creates a COMVariant object and initializes it with the current date.

    COMVariant theDay; 
     
    theDay = COMVariant::createFromDate(today()); 
    info(theDay.toString());

### Method createFromDateAndTime

Creates a new COMVariant object and initializes it with a date and time in one operation.

    public static COMVariant createFromDateAndTime(Date date, int time, [COMVariantInOut inOutFlag])

#### Parameters

date  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

<!-- -->

time  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

<!-- -->

inOutFlag  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

#### Return Value

The new COMVariant object.

#### Remarks

The COMVariant object that is created by this method has the data type VT\_DATE (date/time). You can change the data type of an existing COMVariant object to VT\_DATE by using the variantType method.

#### Examples

The following example creates a COMVariant object and assigns it the current date, and a time of 10 seconds past midnight.

    date theDay; 
    COMVariant theDayAndTime; 
     
    theDay = today(); 
    theDayAndTime = COMVariant::createFromDateAndTime(theDay, 10); 
    info(theDayAndTime.toString());

### Method createFromInt

Creates a new COMVariant object and initializes it with an integer value in one operation.

    public static COMVariant createFromInt(int value, [COMVariantInOut inOutFlag])

#### Parameters

value  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

<!-- -->

inOutFlag  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

#### Return Value

The new COMVariant object.

#### Remarks

The COMVariant object that is created by this method has the data type VT\_I4 (integer). You can change the data type of an existing COMVariant object to VT\_I4 by using the variantType method or by passing in an integer value by using the int property method.

#### Examples

The following example creates a COMVariant object of the VT\_I4 variant data type (integer), and sets the value to 123.

    { 
        COMVariant var; 
      
        var = COMVariant::createFromInt(123); 
    }

### Method createFromInt64

Creates a new COMVariant object and initializes it with an int64 value (longLong or uLongLong) in one operation.

    public static COMVariant createFromInt64(Int64 value, [COMVariantInOut inOutFlag])

#### Parameters

value  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

<!-- -->

inOutFlag  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

#### Return Value

The new COMVariant object.

#### Remarks

The COMVariant object that is created by this method has the data type VT\_I8 (int64). You can change the data type of an existing COMVariant object to VT\_I8 by using the variantType method or by passing in an int64 value by using the longLong or uLongLong property method.

#### Examples

The following example creates a COMVariant object of the VT\_I8 variant data type (integer), and sets the value to 123456.

    { 
        COMVariant var; 
      
        var = COMVariant::createFromInt64(123456); 
    }

### Method createFromReal

Creates a new COMVariant object and initializes it with a real value in one operation.

    public static COMVariant createFromReal(Real value, [COMVariantInOut inOutFlag])

#### Parameters

value  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

<!-- -->

inOutFlag  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

#### Return Value

The new COMVariant object.

#### Remarks

The COMVariant object that is created by this method has the data type VT\_R8 (real). You can change the data type of an existing COMVariant object to VT\_R8 by using the variantType method or by passing in a Boolean value by using the double property method.

#### Examples

The following example creates a COMVariant object of the VT\_R8 variant data type (real) and sets the value to 123.456.

    { 
        COMVariant var; 
       
        var = COMVariant::createFromReal(123.456); 
    }

### Method createFromStr

Creates a new COMVariant object and initializes it with a string in one operation.

    public static COMVariant createFromStr(str value, [COMVariantInOut inOutFlag])

#### Parameters

value  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

<!-- -->

inOutFlag  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

#### Return Value

The new COMVariant object.

#### Remarks

The COMVariant object that is created by this method has the data type VT\_BSTR (string). You can change the data type of an existing COMVariant object to VT\_BSTR by using the variantType method or by passing in a string value by using the bStr property method.

#### Examples

The following example creates a COMVariant object of the VT\_BSTR variant data type and sets the value to "Hello World."

    { 
        COMVariant var; 
       
        var = COMVariant::createFromStr("Hello World"); 
    }

### Method createFromTime

Creates a new COMVariant object and initializes it with a time value in one operation.

    public static COMVariant createFromTime(int value, [COMVariantInOut inOutFlag])

#### Parameters

value  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

<!-- -->

inOutFlag  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

#### Return Value

The new COMVariant object.

#### Remarks

The COMVariant object that is created by this method has the data type VT\_DATE (date/time). You can change the data type of an existing COMVariant object to VT\_DATE by using the variantType method or by passing in a time value by using the time property method.

#### Examples

The following example will create a COMVariant object and set the time part to 10 seconds past midnight.

    COMVariant theTime; 
     
    theTime = COMVariant::createFromTime(10); 
    info(theTime.toString());

### Method createFromUtcDateTime

    public static COMVariant createFromUtcDateTime(DateTime value, [COMVariantInOut inOutFlag])

#### Parameters

value  

<!-- -->

inOutFlag  

#### Return Value

### Method createNoValue

Creates a COMVariant object of the VT\_ERROR variant type with no value.

    public static COMVariant createNoValue()

#### Return Value

The new COMVariant object.

#### Remarks

A COMVariant object with no value can be used for COM parameters which are optional.

#### Examples

The following example creates an empty COMVariant object.

    COMVariant noValue; 
     
    noValue = COMVariant::createNoValue(); 
    info(noValue.toString());

### Method new

Creates a COMVariant object that can be used to pass arguments to the methods or properties of a COM Automation object.

    public void new([COMVariantInOut inOutFlag], [COMVariantType type])

#### Parameters

inOutFlag  
A type of data to store; optional. These are the possible values that are supplied by the COMVariantType system enum:

<!-- -->

type  
A type of data to store; optional. These are the possible values that are supplied by the COMVariantType system enum:

#### Remarks

If the type parameter is omitted, no internal memory will be allocated until it is needed by one of the property methods of the COMVariant object. For a list of the property methods, see \[COMVariant Class\]. You can change the variant data type after it has been set by passing in a new value of a different type (by using one of the property methods). The data types that are defined by the COMVariantType enum are equivalent to the variant data types that are defined by the Win32 SDK.

#### Examples

The following example creates three COMVariant objects:

-   varIn is for passing data to a COM method; it has a string stored in it and then a short (integer).
-   varOut is to receive data of type VT\_I4 (long).
-   varOutRetval can pass in or receive data; its data type can be set by the COMDispFunction.call method.

<!-- -->

    { 
        COMVariant varIn  = new COMVariant(); 
        COMVariant varOut = new COMVariant( 
            COMVariantInOut::OUT,  
            COMVariantType::VT_I4); 
        COMVariant varOutRetval = new COMVariant( 
            COMVariantInOut::OUT_RETVAL); ; 
      
        // Store a text string in the varIn object 
        varIn.bStr("Hello World"); 
      
        // Change varIn to a short. 
        // Text string stored in varIn is automatically released 
        varIn.short(123);  
    }

### Method noValue

Deletes the contents of an existing COMVariant object and enables it to act as an unspecified argument when it is used in the COMDispFunction.call method or the COM class.

    public void noValue()

#### Remarks

A no-value variant can be used when a COM method has parameters that can be null. It indicates to the COM object that the argument has not been specified and that it must use its own default value. When you are calling methods on a COM object, the unspecified argument can also be specified by using the COMArgument::NoValue enum. Note that this enum cannot be used when calling through the COMDispFunction class.

#### Examples

The following example shows how to call the COM.multiply method with the third argument unspecified. The code below contains a hypothetical COM object ("MyCOM.Object"), and will therefore not run in Microsoft Dynamics AX, unless such an object is created outside Microsoft Dynamics AX.

    { 
        COM        com; 
        COMVariant varArg1 = new COMVariant(); 
        COMVariant varArg2 = new COMVariant(); 
        COMVariant varArg3 = new COMVariant(); 
        COMVariant varRet  = new COMVariant(COMVariantInOut::OUT_RETVAL); 
        real       ret; 
        InteropPermission perm; 
      
        // Set code access permission to help protect use of COM object 
        perm = new InteropPermission(InteropKind::ComInterop); 
        if (perm == null) 
        { 
            return; 
        } 
      
        // Permission scope starts here 
        perm.assert(); 
      
        com = new COM("MyCOM.Object"); 
      
        // Specify arguments for the multiply method 
        varArg1.float(123); 
        varArg2.float(456); 
        varArg3.noValue(); 
        varRet = com.multiply(varArg1, varArg2, varArg3); 
        // …or… 
        varRet = com.multiply(varArg1, varArg2, COMArgument::NoValue); 
         ret = varRet.double(); 
        // ret is now 56088 (123*456) 
      
        // Close code access permission 
        CodeAccessPermission::revertAssert(); 
    }

### Method finalize

Not implemented. You can override this method if you need to explicitly destruct an object.

    public void finalize()

#### Remarks

You must call finalize methods to execute any statements in them; there are no implicit calls to finalize methods.

## Class ConfigurationKeySet
    class ConfigurationKeySet extends Object

The ConfigurationKeySet class enables working with a tree of configuration keys.

### Remarks

When a new ConfigurationKeySet is created, a tree of configuration keys is created, where all keys are set by default to "enabled". The cnt method is used to loop through all configuration keys and count them. The cntID method is used to retrieve the IDs of the configuration keys. In situations in which a configuration key has been deleted and the key IDs are ID1, ID2, ID5, and so on, this method will distinguish the number of configuration keys compared to their IDs. When a new ConfigurationKeySet is created, all configuration keys are enabled. The system will then call the loadSystemSetup method, which scans the SysConfig table where the configuration types are stored. It loops through the configuration key setup and identifies what is enabled. Next, the enabled method is called. Every time a configuration key is disabled, all sub-configuration keys are also automatically disabled. In a situation in which a top node is enabled and one of the sub-nodes is disabled, the kernel will remember which configuration key sub-nodes were previously disabled whenever a top node is disabled.

### Examples

### Methods

| Method                                                                            | Description                                                                                                             |
|-----------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| public int cnt()                                                                  | Retrieves the number of configuration keys that are defined in the Microsoft Dynamics AX Application Object Tree (AOT). |
| public ConfigurationKeyId cnt2Id(int cnt)                                         | Retrieves the ID of the *n*th configuration key.                                                                        |
| public boolean enabled(ConfigurationKeyId configurationKeyId, \[boolean enable\]) | Determines whether to enable or disable the object.                                                                     |
| public container pack()                                                           | Serializes the current instance of the ConfigurationKeySet class.                                                       |
| public boolean touchedByUser(ConfigurationKeyId configurationKeyId)               |                                                                                                                         |
| public void new(\[container container\])                                          | Initializes a new instance of the Object class.                                                                         |
| public void loadSystemSetup()                                                     |                                                                                                                         |

### Method cnt

Retrieves the number of configuration keys that are defined in the Microsoft Dynamics AX Application Object Tree (AOT).

    public int cnt()

#### Return Value

The number of configuration keys that are defined in the AOT.

### Method cnt2Id

Retrieves the ID of the *n*th configuration key.

    public ConfigurationKeyId cnt2Id(int cnt)

#### Parameters

cnt  
The index of the configuration key, which must be between 1 and the number of configuration keys.

#### Return Value

The ID of the specified configuration key.

#### Remarks

To find the number of configuration keys, use the cnt method. In general, the index and ID will differ, because not all the IDs are used.

#### Examples

    ConfigurationKeySet configKeySet = new ConfigurationKeySet(); 
    DictConfigurationKey dictConfigurationKey; 
    int i; 
     
    configKeySet.loadSystemSetup(); 
    for (i=1; i<= configKeySet.cnt(); i++) 
    { 
        setPrefix('Disabled configurationkeys'); 
        if (!configKeySet.enabled( configKeySet.cnt2Id(i) )) 
        { 
            dictConfigurationKey =  
                new DictConfigurationKey(configKeySet.cnt2id(i)); 
            info (dictConfigurationKey.name()); 
        } 
    }

### Method enabled

Determines whether to enable or disable the object.

    public boolean enabled(ConfigurationKeyId configurationKeyId, [boolean enable])

#### Parameters

configurationKeyId  
The value to which to set the state of the configuration key; optional.

<!-- -->

enable  
The value to which to set the state of the configuration key; optional.

#### Return Value

true if the object is enabled; otherwise, false.

#### Remarks

The enabled property allows controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

#### Examples

This example demonstrates the use of the ConfigurationKeySet.enabled method.

    static void testConfigKey(Args _args) 
    { 
        ConfigurationKeySet configKey = new ConfigurationKeySet(); 
     
        configKey.loadSystemSetup(); 
     
        // Set the enable value to false. 
        configKey.enabled(configurationkeynum(RouteApprove), false); 
        SysDictConfigurationKey::save(configKey.pack()); 
        SysSecurity::reload(true); 
        print isConfigurationkeyEnabled(configurationkeynum(RouteApprove)); 
     
        // Set the enable value to true. 
        configKey.enabled(configurationkeynum(RouteApprove), true); 
        //Save the configuration key setup. 
        SysDictConfigurationKey::save(configKey.pack()); 
        SysSecurity::reload(true); 
     
        print isConfigurationkeyEnabled(configurationkeynum(RouteApprove)); 
     
        pause; 
    }

### Method pack

Serializes the current instance of the ConfigurationKeySet class.

    public container pack()

#### Return Value

A container that contains the current instance of the ConfigurationKeySet class.

### Method touchedByUser

    public boolean touchedByUser(ConfigurationKeyId configurationKeyId)

#### Parameters

configurationKeyId  

#### Return Value

### Method new

Initializes a new instance of the Object class.

    public void new([container container])

#### Parameters

container  

### Method loadSystemSetup

    public void loadSystemSetup()

## Class Connection
    class Connection extends Object

The Connection class establishes a current database session that you can use to execute SQL statements and return results.

### Remarks

The following classes extend the Connection class:

-   OdbcConnection
-   OciConnection
-   UserConnection

### Examples

In the following example, the createStatement method initializes the Statement object. The Statement.executeQuery method executes an SQL statement and then stores the retrieved data in the ResultSet object.

    server static void main(Args args) 
    { 
        Connection con = new Connection(); 
        Statement stmt = con.createStatement(); 
        ResultSet r; 
        str sql; 
        SqlStatementExecutePermission perm; 
      
        sql = strfmt('SELECT VALUE FROM SQLSYSTEMVARIABLES'); 
      
        // Set code access permission to help protect the use of 
        // Statement.executeUpdate. 
        perm = new SqlStatementExecutePermission(sql); 
        perm.assert(); 
      
        try 
        { 
            r = stmt.executeQuery(sql); 
            while (r.next()) 
            { 
                print r.getString(1); 
                pause; 
            } 
        } 
        catch (exception::Error) 
        { 
            print "An error occured in the query."; 
            pause; 
        } 
        // Code access permission scope ends here. 
        CodeAccessPermission::revertAssert(); 
    }

### Methods

| Method                                                                                                           | Description                                                                                                                                                                             |
|------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public Statement createStatement(\[ResultSetType resultSetType\], \[ResultSetConcurrency resultSetConcurrency\]) | Creates a Statement object that is used to execute an SQL statement.                                                                                                                    |
| public int odbcGetInfoInt(int InfoId)                                                                            | Provides an interface to the SQLGetInfo Open Database Connectivity (ODBC) function to retrieve information about the ODBC driver and data source that are associated with a connection. |
| public int odbcGetInfoLong(int InfoId)                                                                           | Provides an interface to the SQLGetInfo ODBC function to retrieve information about the ODBC driver and data source that are associated with a connection.                              |
| public str odbcGetInfoStr(int InfoId)                                                                            | Provides an interface to the SQLGetInfo ODBC function to retrieve information, in string format, about the ODBC driver and data source that are associated with a connection.           |
| public str toString()                                                                                            | Converts the Connection object to a string.                                                                                                                                             |
| public int ttsLevel()                                                                                            | Returns the number for the last call to the ttsbegin method that is used to begin a transaction.                                                                                        |
| public boolean isInTransactionScope()                                                                            |                                                                                                                                                                                         |
| public void finalize()                                                                                           |                                                                                                                                                                                         |
| public void transactionScopeAbort()                                                                              |                                                                                                                                                                                         |
| public void ttsNotifyCommit()                                                                                    | Is called when the ttscommit method is called.                                                                                                                                          |
| public void transactionScopeBegin()                                                                              |                                                                                                                                                                                         |
| public void transactionScopeCommit()                                                                             |                                                                                                                                                                                         |
| public void ttsNotifyBegin()                                                                                     |                                                                                                                                                                                         |
| public void ttsbegin()                                                                                           | Begins a transaction.                                                                                                                                                                   |
| public void ttsabort()                                                                                           | Discards changes that are associated with a transaction and rolls the database back to the original state.                                                                              |
| public void new()                                                                                                | Initializes a new instance of the Connection class.                                                                                                                                     |
| public void ttsNotifyAbort()                                                                                     | Is called when an exception is thrown.                                                                                                                                                  |
| public void ttscommit()                                                                                          | Commits the changes that are associated with a transaction to the database.                                                                                                             |

### Method createStatement

Creates a Statement object that is used to execute an SQL statement.

    public Statement createStatement([ResultSetType resultSetType], [ResultSetConcurrency resultSetConcurrency])

#### Parameters

resultSetType  
A ResultSetConcurrency enumeration that specifies ReadOnly by default.

<!-- -->

resultSetConcurrency  
A ResultSetConcurrency enumeration that specifies ReadOnly by default.

#### Return Value

A data type value that is a new Statement object.

#### Remarks

There is risk of an SQL injection threat when you use the createStatement method to create an SQL statement and then allow a user to control input to the statement. For information about SQL injection, see http://go.microsoft.com/fwlink/?LinkId=114986. You can use Query Elements in the AOT, views, and X++ Select statements as safer alternatives to executing SQL statements.

### Method odbcGetInfoInt

Provides an interface to the SQLGetInfo Open Database Connectivity (ODBC) function to retrieve information about the ODBC driver and data source that are associated with a connection.

    public int odbcGetInfoInt(int InfoId)

#### Parameters

InfoId  
An integer that specifies an ID for the requested information according to the ODBC standard.

#### Return Value

An integer value for the information that is retrieved.

#### Examples

In the following example, the odbcGetInfoInt method returns an integer value for the maximum length of the column name.

    void getConnection() 
    { 
        Connection con; 
        Statement stmt; 
        int info; 
     
        #define.SQL_MAX_COLUMN_NAME_LEN(30) 
        con = new Connection(); 
     
        try 
        { 
            info = con.odbcGetInfoInt(#SQL_MAX_COLUMN_NAME_LEN); 
     
            print info; 
            pause; 
         } 
     
        catch(exception::Error) 
        { 
            print "An error occurred."; 
     
        } 
     
    }

### Method odbcGetInfoLong

Provides an interface to the SQLGetInfo ODBC function to retrieve information about the ODBC driver and data source that are associated with a connection.

    public int odbcGetInfoLong(int InfoId)

#### Parameters

InfoId  
An Integer data type that specifies an ID for the requested information, according to the ODBC standard.

#### Return Value

An Integer data type value for the information that is retrieved.

#### Remarks

This method retrieves a 32-bit integer and returns it as an integer.

#### Examples

In the following example, the odbcGetInfoLong method returns an integer for the maximum row size.

    void getConnection() 
    { 
        Connection con; 
        Statement stmt; 
        int info; 
     
        #define.SQL_MAX_ROW_SIZE(104) 
        con = new Connection(); 
     
        try 
        { 
            info = con.odbcGetInfoLong(#SQL_MAX_ROW_SIZE); 
     
            print info; 
            pause; 
         } 
     
        catch(exception::Error) 
        { 
            print "An error occurred."; 
     
        } 
     
    }

### Method odbcGetInfoStr

Provides an interface to the SQLGetInfo ODBC function to retrieve information, in string format, about the ODBC driver and data source that are associated with a connection.

    public str odbcGetInfoStr(int InfoId)

#### Parameters

InfoId  
An Integer data type that specifies an ID for the requested information, according to the ODBC standard.

#### Return Value

A String data type value for the information that is retrieved.

#### Examples

In the following example, the odbcGetInfoStr method returns the name of the database management system.

    void getConnection() 
    { 
        Connection con; 
        str info; 
     
        #define.SQL_DBMS_NAME(17) 
        con = new Connection(); 
      
        try 
        { 
            info = con.odbcGetInfoStr(#SQL_DBMS_NAME); 
      
            print info; 
            pause; 
         } 
      
        catch(exception::Error) 
        { 
            print "An error occurred."; 
        } 
    }

### Method toString

Converts the Connection object to a string.

    public str toString()

#### Return Value

A string value for the Connection object.

### Method ttsLevel

Returns the number for the last call to the ttsbegin method that is used to begin a transaction.

    public int ttsLevel()

#### Return Value

An integer value that indicates the number for the last call to the ttsbegin method. For example, if the ttsLevel method is called after the third call to the ttsbegin method, the return value is 3.

### Method isInTransactionScope

    public boolean isInTransactionScope()

#### Return Value

### Method finalize

    public void finalize()

### Method transactionScopeAbort

    public void transactionScopeAbort()

### Method ttsNotifyCommit

Is called when the ttscommit method is called.

    public void ttsNotifyCommit()

### Method transactionScopeBegin

    public void transactionScopeBegin()

### Method transactionScopeCommit

    public void transactionScopeCommit()

### Method ttsNotifyBegin

    public void ttsNotifyBegin()

### Method ttsbegin

Begins a transaction.

    public void ttsbegin()

### Method ttsabort

Discards changes that are associated with a transaction and rolls the database back to the original state.

    public void ttsabort()

### Method new

Initializes a new instance of the Connection class.

    public void new()

### Method ttsNotifyAbort

Is called when an exception is thrown.

    public void ttsNotifyAbort()

### Method ttscommit

Commits the changes that are associated with a transaction to the database.

    public void ttscommit()

## Class ContainerClass
    class ContainerClass extends Object

### Remarks

### Examples

### Methods

| Method                                                              | Description                                          |
|---------------------------------------------------------------------|------------------------------------------------------|
| public int length()                                                 |                                                      |
| public container toBlob()                                           |                                                      |
| public str toString()                                               | Returns a string that represents the current object. |
| public container value()                                            |                                                      |
| ::public static container blob2Container(container blob\_container) |                                                      |
| ::public static int containerLength(container container)            |                                                      |
| public void new(container container)                                | Initializes a new instance of the Object class.      |

### Method length

    public int length()

#### Return Value

### Method toBlob

    public container toBlob()

#### Return Value

### Method toString

Returns a string that represents the current object.

    public str toString()

#### Return Value

A string that represents the current object.

#### Remarks

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type. For example, an instance of the SysMethodInfo class returns the method name and type of the method, such as instance or static.

### Method value

    public container value()

#### Return Value

### Method blob2Container

    public static container blob2Container(container blob_container)

#### Parameters

blob\_container  

#### Return Value

### Method containerLength

    public static int containerLength(container container)

#### Parameters

container  

#### Return Value

### Method new

Initializes a new instance of the Object class.

    public void new(container container)

#### Parameters

container  

## Class ControlFilterValue
    class ControlFilterValue extends FilterValue

### Remarks

### Examples

### Methods

| Method                                                | Description                                     |
|-------------------------------------------------------|-------------------------------------------------|
| public FormControl control()                          |                                                 |
| public void new(FormControl control, str filterValue) | Initializes a new instance of the Object class. |

### Method control

    public FormControl control()

#### Return Value

### Method new

Initializes a new instance of the Object class.

    public void new(FormControl control, str filterValue)

#### Parameters

control  

<!-- -->

filterValue  

## Class ControlNode
    class ControlNode extends TreeNode

The ControlNode class lets you create, read, update, and delete X++ code and metadata.

### Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                         | Description                                       |
|------------------------------------------------|---------------------------------------------------|
| public void new(str name, \[TreeNode parent\]) | Initializes a new instance of the TreeNode class. |

### Method new

Initializes a new instance of the TreeNode class.

    public void new(str name, [TreeNode parent])

#### Parameters

name  

<!-- -->

parent  

## Class CryptoAPI
    class CryptoAPI extends Object

### Remarks

### Examples

### Methods

| Method                                   | Description                                     |
|------------------------------------------|-------------------------------------------------|
| public container decrypt(container blob) |                                                 |
| public container encrypt(container blob) |                                                 |
| public container getKey()                |                                                 |
| public Int64 salt()                      |                                                 |
| public void new(Int64 salt)              | Initializes a new instance of the Object class. |
| ::public static void resetKey()          |                                                 |

### Method decrypt

    public container decrypt(container blob)

#### Parameters

blob  

#### Return Value

### Method encrypt

    public container encrypt(container blob)

#### Parameters

blob  

#### Return Value

### Method getKey

    public container getKey()

#### Return Value

### Method salt

    public Int64 salt()

#### Return Value

### Method new

Initializes a new instance of the Object class.

    public void new(Int64 salt)

#### Parameters

salt  

### Method resetKey

    public static void resetKey()

## Class Cue
    class Cue extends TreeNode

### Remarks

### Examples

### Methods

| Method                                         | Description                                                                                                                               |
|------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public str changedBy(\[str value\])            | Gets or sets the name of the user who last changed the application object.                                                                |
| public Date changedDate(\[Date value\])        | Gets or sets the date an application object was last changed.                                                                             |
| public str changedTime(\[str value\])          | Gets or sets the time an application object was last changed.                                                                             |
| public str createdBy(\[str value\])            | Gets or sets the name of the user who created the application object.                                                                     |
| public Date creationDate(\[Date value\])       | Gets or sets the date an application object was created.                                                                                  |
| public str creationTime(\[str value\])         |                                                                                                                                           |
| public int cueMax(\[int value\])               |                                                                                                                                           |
| public str dataField(\[str value\])            |                                                                                                                                           |
| public str label(\[str value\])                | Gets or sets the label for a control.                                                                                                     |
| public str LabelId()                           |                                                                                                                                           |
| public str menuItemName(\[str value\])         |                                                                                                                                           |
| public str name(\[str value\])                 | Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics AX application object. |
| public Guid origin(\[Guid value\])             |                                                                                                                                           |
| public str previewPartReference(\[str value\]) |                                                                                                                                           |
| public boolean showAlert(\[boolean value\])    |                                                                                                                                           |
| public int showAlertValue(\[int value\])       |                                                                                                                                           |
| public int showAlertWhen(\[int value\])        |                                                                                                                                           |
| public boolean showSum(\[boolean value\])      |                                                                                                                                           |
| public str table(\[str value\])                | Gets or sets the table ID associated with the object.                                                                                     |
| public void new(str cueName)                   | Initializes a new instance of the TreeNode class.                                                                                         |

### Method changedBy

Gets or sets the name of the user who last changed the application object.

    public str changedBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method changedDate

Gets or sets the date an application object was last changed.

    public Date changedDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was last changed.

### Method changedTime

Gets or sets the time an application object was last changed.

    public str changedTime([str value])

#### Parameters

value  

#### Return Value

The time an application object was last changed.

### Method createdBy

Gets or sets the name of the user who created the application object.

    public str createdBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method creationDate

Gets or sets the date an application object was created.

    public Date creationDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was created.

### Method creationTime

    public str creationTime([str value])

#### Parameters

value  

#### Return Value

### Method cueMax

    public int cueMax([int value])

#### Parameters

value  

#### Return Value

### Method dataField

    public str dataField([str value])

#### Parameters

value  

#### Return Value

### Method label

Gets or sets the label for a control.

    public str label([str value])

#### Parameters

value  

#### Return Value

The current value of the label string.

#### Remarks

The label determines which text is displayed in the control or adjacent to it. The label property value cannot exceed 250 characters.

### Method LabelId

    public str LabelId()

#### Return Value

### Method menuItemName

    public str menuItemName([str value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enumeration types, and classes.

### Method origin

    public Guid origin([Guid value])

#### Parameters

value  

#### Return Value

### Method previewPartReference

    public str previewPartReference([str value])

#### Parameters

value  

#### Return Value

### Method showAlert

    public boolean showAlert([boolean value])

#### Parameters

value  

#### Return Value

### Method showAlertValue

    public int showAlertValue([int value])

#### Parameters

value  

#### Return Value

### Method showAlertWhen

    public int showAlertWhen([int value])

#### Parameters

value  

#### Return Value

### Method showSum

    public boolean showSum([boolean value])

#### Parameters

value  

#### Return Value

### Method table

Gets or sets the table ID associated with the object.

    public str table([str value])

#### Parameters

value  

#### Return Value

The current value of the table ID associated with the object.

### Method new

Initializes a new instance of the TreeNode class.

    public void new(str cueName)

#### Parameters

cueName  

## Class CueGroup
    class CueGroup extends TreeNode

### Remarks

### Examples

### Methods

| Method                                   | Description                                                                                                                                   |
|------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| public str changedBy(\[str value\])      | Gets or sets the name of the user who last changed the application object.                                                                    |
| public Date changedDate(\[Date value\])  | Gets or sets the date an application object was last changed.                                                                                 |
| public str changedTime(\[str value\])    | Gets or sets the time an application object was last changed.                                                                                 |
| public str createdBy(\[str value\])      | Gets or sets the name of the user who created the application object.                                                                         |
| public Date creationDate(\[Date value\]) | Gets or sets the date an application object was created.                                                                                      |
| public str creationTime(\[str value\])   |                                                                                                                                               |
| public str label(\[str value\])          | Gets or sets the label for a control.                                                                                                         |
| public str LabelId()                     |                                                                                                                                               |
| public str name(\[str value\])           | Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics AX application object. |
| public Guid origin(\[Guid value\])       |                                                                                                                                               |
| public void new(str cueGroupName)        | Initializes a new instance of the TreeNode class.                                                                                             |

### Method changedBy

Gets or sets the name of the user who last changed the application object.

    public str changedBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method changedDate

Gets or sets the date an application object was last changed.

    public Date changedDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was last changed.

### Method changedTime

Gets or sets the time an application object was last changed.

    public str changedTime([str value])

#### Parameters

value  

#### Return Value

The time an application object was last changed.

### Method createdBy

Gets or sets the name of the user who created the application object.

    public str createdBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method creationDate

Gets or sets the date an application object was created.

    public Date creationDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was created.

### Method creationTime

    public str creationTime([str value])

#### Parameters

value  

#### Return Value

### Method label

Gets or sets the label for a control.

    public str label([str value])

#### Parameters

value  

#### Return Value

The current value of the label string.

#### Remarks

The label determines which text is displayed in the control or adjacent to it. The label property value cannot exceed 250 characters.

### Method LabelId

    public str LabelId()

#### Return Value

### Method name

Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in the code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enumeration types, and classes.

### Method origin

    public Guid origin([Guid value])

#### Parameters

value  

#### Return Value

### Method new

Initializes a new instance of the TreeNode class.

    public void new(str cueGroupName)

#### Parameters

cueGroupName  

## Class CueReference
    class CueReference extends TreeNode

### Remarks

### Examples

### Methods

| Method                                | Description                                                                                                                       |
|---------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| public str cue(\[str value\])         |                                                                                                                                   |
| public str name(\[str value\])        | Gets or sets the name used in code to identify a form, report, table, query, or another Microsoft Dynamics AX application object. |
| public void new(str cueReferenceName) | Initializes a new instance of the TreeNode class.                                                                                 |

### Method cue

    public str cue([str value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name used in code to identify a form, report, table, query, or another Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Does not exceed 250 characters.
-   Can include numbers and underscore characters.
-   Does not include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enumerations, classes, and other public objects.

### Method new

Initializes a new instance of the TreeNode class.

    public void new(str cueReferenceName)

#### Parameters

cueReferenceName  
The name to use to identify this form, report, table, query, or other application object.

 

