---
# required metadata

title: O Classes
description: System API classes that start with the letter O.
author: RobinARH
manager: AnnBe
ms.date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: RobinARH
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 52201
ms.assetid: 63f93d3d-54a5-46c2-b356-fe5863b6f927
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# O Classes

System API classes that start with the letter O.

Class Object
------------

    class Object

The Object class is the base class from which all other classes are derived.

### Remarks

Methods in the Object class can be called for any object. The Object class is used to allow assignment and equality checks to be performed without the developer having to know the actual type of the object. The methods can be grouped into three groups:

-   Time out methods - can be used to activate a method after a specified period of time has passed.
-   Process methods, such as the Wait, Notify, and NotifyAll method - used to control process flow and to wait for another object to finish its task.
-   Class methods - return basic information about the object.

### Examples

### Methods

| Method                                                                      | Description                                                                                                 |
|-----------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| public boolean equal(Object object)                                         | Determines whether the specified object is equal to the current one.                                        |
| public int getTimeOutTimerHandle()                                          | Returns the timer handle for the object.                                                                    |
| public ClassId handle()                                                     | Retrieves the handle of the class of the object.                                                            |
| public boolean SysObsoleteAttribute()                                       |                                                                                                             |
| public int SysObsoleteAttribute(str Method, int WaitTime, \[boolean idle\]) |                                                                                                             |
| public str toString()                                                       | Returns a string that represents the current object.                                                        |
| public int usageCount()                                                     | Returns the current number of references, that is, the value of the reference counter, that the object has. |
| public str xml(\[int indent\])                                              | Returns an XML string that represents the current object.                                                   |
| public boolean Equals(System.Object obj)                                    |                                                                                                             |
| public int GetHashCode()                                                    |                                                                                                             |
| public void finalize()                                                      |                                                                                                             |
| public void wait()                                                          | Pauses a process.                                                                                           |
| public void cancelTimeOut(int timerHandle)                                  | Cancels a previous method call to the setTimeOut method.                                                    |
| public void new()                                                           | Initializes a new instance of the Object class.                                                             |
| public void notify()                                                        | Releases the hold on an object that has called the wait method on this object.                              |
| public void notifyAll()                                                     | Releases a lock on the object that was issued by the wait method on this object.                            |

### Method equal

Determines whether the specified object is equal to the current one.

    public boolean equal(Object object)

#### Parameters

object  
The object to compare with the current object.

#### Return Value

true if the specified object is equal to the current object; otherwise, false.

#### Remarks

The default implementation of the Object::equal method supports only reference equality. Derived classes can, however, override the Object::equal method to support value equality.

#### Examples

The following example compares the current instance with another object.

    static void Object_Equal(Args _args) 
    { 
        Object objA = new Object(); 
        Object objB = new Object(); 
        print objA.equal(objA);  // true. 
        print objA.equal(objB);  // false. 
        objA = objB; 
        print objA.equal(objB);  // true. 
     }

### Method getTimeOutTimerHandle

Returns the timer handle for the object.

    public int getTimeOutTimerHandle()

#### Return Value

The timer handle of the object.

#### Remarks

The timer handle of the object is set by calling the setTimeOut method.

#### Examples

The following example sets a timeout, and then cancels it.

    public void myJob() 
    { 
        int timerHandle = 0; 
        this.setTimeOut(identifierstr(workerFunction), 0); 
        //Perform some operations. 
        timerHandle = this.getTimeOutTimerHandle(); 
        this.cancelTimeOut( timerHandle ); 
    }

### Method handle

Retrieves the handle of the class of the object.

    public ClassId handle()

#### Return Value

The handle, that is, the classId property, of the class of the current object.

#### Remarks

There is no guarantee that the handle of a class will remain unchanged in later releases, or after an export or import for user-defined classes. It is strongly advised that the value that is returned by this method will not be used as a persistent constant to refer to the class.

### Method SysObsoleteAttribute

    public boolean SysObsoleteAttribute()

#### Return Value

### Method SysObsoleteAttribute

    public int SysObsoleteAttribute(str Method, int WaitTime, [boolean idle])

#### Parameters

Method  

<!-- -->

WaitTime  

<!-- -->

idle  

#### Return Value

### Method toString

Returns a string that represents the current object.

    public str toString()

#### Return Value

A string that represents the current object.

#### Remarks

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type. For example, an instance of the SysMethodInfo class returns the method name and type of the method, such as instance or static.

#### Examples

The following example prints out the class name of o.

    static void Object_ToString_Job(Args _args) 
    { 
        Object o = new Object(); 
        print o.toString();  // Prints out: "Class Object" 
        pause; 
    }

### Method usageCount

Returns the current number of references, that is, the value of the reference counter, that the object has.

    public int usageCount()

#### Return Value

The current number of references that the object has.

#### Remarks

When an object is created, its reference counter equals 1. When a new reference is created, its value increases. As a reference goes out of scope, its value decreases.

#### Examples

The following example prints the number of references for objA to the output window.

    static void Object_UsageCount(Args _args) 
    { 
        Object objA = new Object(); 
        Object objB; 
        print objA.usageCount();    // Prints 1. 
        objB = objA;                // objB is a reference to objA. 
        print objA.usageCount();    // prints 2 
        pause; 
    }

### Method xml

Returns an XML string that represents the current object.

    public str xml([int indent])

#### Parameters

indent  
The amount of indentation of the returned XML string; optional.

#### Return Value

An XML string that represents the current object.

#### Remarks

This method can be overridden to return values that are meaningful for that type.

### Method Equals

    public boolean Equals(System.Object obj)

#### Parameters

obj  

#### Return Value

### Method GetHashCode

    public int GetHashCode()

#### Return Value

### Method finalize

    public void finalize()

### Method wait

Pauses a process.

    public void wait()

#### Remarks

The most common use for this method is to start an object that asks the user for some input and then call the wait method on that object, such as a form. The next line of code is not executed until the object has called the notify or notifyAll method. When the wait method is called from a form, you do not have to call the notify methods manually because forms call the Object.notifyAll method when the user either closes the form or presses the Apply button. This method is not meant for thread synchronization. Use the waitUntilSignaled method instead.

#### Examples

The following example opens the GetUserInput dialog, blocks, and waits until the user has closed the form.

    { 
        Args a = new Args("GetUserInput"); 
        formRun fr = new formRun(a); 
        fr.init(); 
        fr.run(); 
        fr.wait(); 
        // Execution will resume at this point, only after 
        // the user has closed the form. 
    }

### Method cancelTimeOut

Cancels a previous method call to the setTimeOut method.

    public void cancelTimeOut(int timerHandle)

#### Parameters

timerHandle  
The handle of the scheduled event to delete. The handle is the value that is returned by the Object.setTimeOut method.

#### Remarks

Any scheduled time-out calls that have not yet been processed are automatically deleted when the object itself is deleted.

#### Examples

The following example calls the Object.setTimeOut method, and then cancels the time-out.

    void Object_cancelTimeOut(Args _args) 
    { 
        int th; // timerHandle. 
        // timedMethod is a worker method. 
        th = this.setTimeOut( "timedMethod", 2000 ); 
        //.... 
        // Remove timeOut later. 
        CancelTimeOut(th); 
    }

### Method new

Initializes a new instance of the Object class.

    public void new()

### Method notify

Releases the hold on an object that has called the wait method on this object.

    public void notify()

#### Examples

The following example locks an object, and then releases it.

    public void doWork() 
    { 
        // Perform some actions. 
        this.setTimeOut(identifierstr(workerFunction), 0); 
        this.wait(); // Lock and wait for notify to be called. 
    } 
    public void workerFunction() 
    { 
        // Perform some actions. 
        // Work is done; unlock the doWork method. 
        this.notify(); 
    }

### Method notifyAll

Releases a lock on the object that was issued by the wait method on this object.

    public void notifyAll()

#### Remarks

In the current implementation of this method, there is no difference between calling the notify method and the notifyAll method. Forms will automatically call the notifyAll method when the user closes the form or presses the Apply button.

#### Examples

The following example demonstrates the usage of the notifyAll method.

    public void doWork() 
    { 
          //Do some work. 
          this.setTimeOut(identifierstr(workerFunction), 0); 
          this.wait(); // block and wait for notify. 
    } 
    public void workerFunction() 
    { 
    // Do some work. 
    //... 
    // Work is done. Notify an unblock. 
    this.notify(); 
    } 

## Class ObjectIdent
    class ObjectIdent extends Object

### Remarks

### Examples

### Methods

| Method                         | Description                                     |
|--------------------------------|-------------------------------------------------|
| public Object object()         |                                                 |
| public void new(Object object) | Initializes a new instance of the Object class. |

### Method object

    public Object object()

#### Return Value

### Method new

Initializes a new instance of the Object class.

    public void new(Object object)

#### Parameters

object  

## Class ObjectRun
    class ObjectRun extends Object

Used as the base class for the FormRun and ReportRun classes.

### Remarks

### Examples

### Methods

| Method                      | Description                                                                                                                                                             |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public xArgs args()         | Returns the arguments that the object was constructed with.                                                                                                             |
| public boolean isDetached() | Communicates whether an ObjectRun.detach method call has been made on this object.                                                                                      |
| public void attach()        | Reverses a call to the method. This is the reverse of calling the ObjectRun.detach method. Reversing the call disallows any further switching of focus between windows. |
| public void detach()        | Allows focus to be switched between windows.                                                                                                                            |

### Method args

Returns the arguments that the object was constructed with.

    public xArgs args()

#### Return Value

An Args Class object that contains the arguments for the object.

### Method isDetached

Communicates whether an ObjectRun.detach method call has been made on this object.

    public boolean isDetached()

#### Return Value

true if detach has been called; otherwise, false.

### Method attach

Reverses a call to the method. This is the reverse of calling the ObjectRun.detach method. Reversing the call disallows any further switching of focus between windows.

    public void attach()

### Method detach

Allows focus to be switched between windows.

    public void detach()

#### Remarks

For example, a new form is created from an existing form by calling the new form's run method. Calling a run method changes the focus to the new form. Calling the detach method allows the user to return to the first form without closing the second form. Calling the ObjectRun.attach Method method reverses the effects of the detach method.

## Class OciConnection
    class OciConnection extends Connection

The OciConnection class establishes a database connection that uses Oci (Oracle Call Interface).

### Remarks

In the context of an OciConnection instance, SQL statements are run, and results are returned. If the connection cannot be established based on the information that is specified for the LoginProperty instance, an exception is thrown, and the reason is posted in the Infolog. This class can be used only when Oracle client software is installed.

### Examples

### Methods

| Method                               | Description                                                                                                   |
|--------------------------------------|---------------------------------------------------------------------------------------------------------------|
| public void new(LoginProperty Login) | Establishes a connection to an Oracle database, based on logon properties such as the user name and password. |

### Method new

Establishes a connection to an Oracle database, based on logon properties such as the user name and password.

    public void new(LoginProperty Login)

#### Parameters

Login  
A LoginProperty class instance that contains the user name, password, data source name, database, and so on.

## Class OdbcConnection
    class OdbcConnection extends Connection

The OdbcConnection class establishes a database connection by using ODBC (Open Database Connectivity).

### Remarks

In the context of an OdbcConnection instance, SQL statements are run, and results are returned. If a connection to the ODBC data source cannot be established, an exception is thrown, and the reason is posted in the Infolog. This class works only if the correct ODBC drivers have been installed and configured in ODBC Manager in Control Panel.

### Examples

### Methods

| Method                               | Description                                                                                              |
|--------------------------------------|----------------------------------------------------------------------------------------------------------|
| public void new(LoginProperty Login) | Establishes a connection to a data source, based on logon properties such as the user name and password. |

### Method new

Establishes a connection to a data source, based on logon properties such as the user name and password.

    public void new(LoginProperty Login)

#### Parameters

Login  
A LoginProperty class instance that contains the user name, password, data source name, database, and so on.

## Class OleCommand
    class OleCommand extends Object

### Remarks

### Examples

### Methods

| Method                                                                              | Description                                     |
|-------------------------------------------------------------------------------------|-------------------------------------------------|
| public COMVariant exec(str cmdGroup, int cmdId, int cmdExecOption, COMVariant parm) |                                                 |
| public void finalize()                                                              |                                                 |
| public void new(ComInterface comObject)                                             | Initializes a new instance of the Object class. |

### Method exec

    public COMVariant exec(str cmdGroup, int cmdId, int cmdExecOption, COMVariant parm)

#### Parameters

cmdGroup  

<!-- -->

cmdId  

<!-- -->

cmdExecOption  

<!-- -->

parm  

#### Return Value

### Method finalize

    public void finalize()

### Method new

Initializes a new instance of the Object class.

    public void new(ComInterface comObject)

#### Parameters

comObject  

## Class OuputSection
    class OuputSection extends Object

### Remarks

### Examples

### Methods

| Method                                           | Description                                           |
|--------------------------------------------------|-------------------------------------------------------|
| public int arrangeMethod()                       |                                                       |
| public int backgroundColor()                     |                                                       |
| public LineThickness borderWidth()               |                                                       |
| public int bottomMargin()                        |                                                       |
| public HeadingsStrategy columnHeadingsStrategy() |                                                       |
| public str fontName()                            |                                                       |
| public int leftMargin()                          |                                                       |
| public LineType lineBottom()                     |                                                       |
| public LineType lineLeft()                       |                                                       |
| public LineType lineRight()                      |                                                       |
| public LineType lineTop()                        |                                                       |
| public int nextVerticalPos()                     |                                                       |
| public int rightMargin()                         |                                                       |
| public ReportBlockType sectionType()             |                                                       |
| public int topMargin()                           |                                                       |
| public int type()                                |                                                       |
| public int verticalPos()                         |                                                       |
| public void new()                                | Initializes a new instance of the OuputSection class. |

### Method arrangeMethod

    public int arrangeMethod()

#### Return Value

### Method backgroundColor

    public int backgroundColor()

#### Return Value

### Method borderWidth

    public LineThickness borderWidth()

#### Return Value

### Method bottomMargin

    public int bottomMargin()

#### Return Value

### Method columnHeadingsStrategy

    public HeadingsStrategy columnHeadingsStrategy()

#### Return Value

### Method fontName

    public str fontName()

#### Return Value

### Method leftMargin

    public int leftMargin()

#### Return Value

### Method lineBottom

    public LineType lineBottom()

#### Return Value

### Method lineLeft

    public LineType lineLeft()

#### Return Value

### Method lineRight

    public LineType lineRight()

#### Return Value

### Method lineTop

    public LineType lineTop()

#### Return Value

### Method nextVerticalPos

    public int nextVerticalPos()

#### Return Value

### Method rightMargin

    public int rightMargin()

#### Return Value

### Method sectionType

    public ReportBlockType sectionType()

#### Return Value

### Method topMargin

    public int topMargin()

#### Return Value

### Method type

    public int type()

#### Return Value

### Method verticalPos

    public int verticalPos()

#### Return Value

### Method new

Initializes a new instance of the OuputSection class.

    public void new()

## Class OutputAutoLabelField
    class OutputAutoLabelField extends OutputField

### Remarks

### Examples

### Methods

| Method                  | Description                                                   |
|-------------------------|---------------------------------------------------------------|
| public boolean leadIn() |                                                               |
| public str toString()   | Returns a string that represents the current object.          |
| public str value()      |                                                               |
| public void new()       | Initializes a new instance of the OutputAutoLabelField class. |

### Method leadIn

    public boolean leadIn()

#### Return Value

### Method toString

Returns a string that represents the current object.

    public str toString()

#### Return Value

A string that represents the current object.

#### Remarks

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type. For example, an instance of the SysMethodInfo class returns the method name and the type of the method, such as instance or static.

### Method value

    public str value()

#### Return Value

### Method new

Initializes a new instance of the OutputAutoLabelField class.

    public void new()

## Class OutputBitmapField
    class OutputBitmapField extends OutputField

### Remarks

### Examples

### Methods

| Method                     | Description                                                |
|----------------------------|------------------------------------------------------------|
| public str imageFileName() |                                                            |
| public boolean resize()    |                                                            |
| public int resourceId()    |                                                            |
| public str toString()      | Returns a string that represents the current object.       |
| public container value()   |                                                            |
| public void new()          | Initializes a new instance of the OutputBitmapField class. |

### Method imageFileName

    public str imageFileName()

#### Return Value

### Method resize

    public boolean resize()

#### Return Value

### Method resourceId

    public int resourceId()

#### Return Value

### Method toString

Returns a string that represents the current object.

    public str toString()

#### Return Value

A string that represents the current object.

#### Remarks

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type. For example, an instance of the SysMethodInfo class returns the method name and the type of the method, such as instance or static.

### Method value

    public container value()

#### Return Value

### Method new

Initializes a new instance of the OutputBitmapField class.

    public void new()

## Class OutputBodySection
    class OutputBodySection extends OuputSection

### Remarks

### Examples

### Methods

| Method             | Description                                                |
|--------------------|------------------------------------------------------------|
| public int recId() |                                                            |
| public int table() |                                                            |
| public void new()  | Initializes a new instance of the OutputBodySection class. |

### Method recId

    public int recId()

#### Return Value

### Method table

    public int table()

#### Return Value

### Method new

Initializes a new instance of the OutputBodySection class.

    public void new()

## Class OutputColumnHeadingsSection
    class OutputColumnHeadingsSection extends OuputSection

### Remarks

### Examples

### Methods

| Method             | Description                                                          |
|--------------------|----------------------------------------------------------------------|
| public str table() |                                                                      |
| public void new()  | Initializes a new instance of the OutputColumnHeadingsSection class. |

### Method table

    public str table()

#### Return Value

### Method new

Initializes a new instance of the OutputColumnHeadingsSection class.

    public void new()

## Class OutputDateField
    class OutputDateField extends OutputField

### Remarks

### Examples

### Methods

| Method                | Description                                              |
|-----------------------|----------------------------------------------------------|
| public str toString() | Returns a string that represents the current object.     |
| public Date value()   |                                                          |
| public void new()     | Initializes a new instance of the OutputDateField class. |

### Method toString

Returns a string that represents the current object.

    public str toString()

#### Return Value

A string that represents the current object.

#### Remarks

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type. For example, an instance of the SysMethodInfo class returns the method name and the type of the method, such as instance or static.

### Method value

    public Date value()

#### Return Value

### Method new

Initializes a new instance of the OutputDateField class.

    public void new()

## Class OutputDateTimeField
    class OutputDateTimeField extends OutputField

### Remarks

### Examples

### Methods

| Method                  | Description                                                  |
|-------------------------|--------------------------------------------------------------|
| public str toString()   | Returns a string that represents the current object.         |
| public DateTime value() |                                                              |
| public void new()       | Initializes a new instance of the OutputDateTimeField class. |

### Method toString

Returns a string that represents the current object.

    public str toString()

#### Return Value

A string that represents the current object.

#### Remarks

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type. For example, an instance of the SysMethodInfo class returns the method name and the type of the method, such as instance or static.

### Method value

    public DateTime value()

#### Return Value

### Method new

Initializes a new instance of the OutputDateTimeField class.

    public void new()

## Class OutputEnumField
    class OutputEnumField extends OutputField

### Remarks

### Examples

### Methods

| Method                 | Description                                              |
|------------------------|----------------------------------------------------------|
| public str getString() |                                                          |
| public void new()      | Initializes a new instance of the OutputEnumField class. |

### Method getString

    public str getString()

#### Return Value

### Method new

Initializes a new instance of the OutputEnumField class.

    public void new()

## Class OutputEpilogSection
    class OutputEpilogSection extends OuputSection

### Remarks

### Examples

### Methods

| Method            | Description                                                  |
|-------------------|--------------------------------------------------------------|
| public void new() | Initializes a new instance of the OutputEpilogSection class. |

### Method new

Initializes a new instance of the OutputEpilogSection class.

    public void new()

## Class OutputField
    class OutputField extends Object

### Remarks

### Examples

### Methods

| Method                         | Description                                          |
|--------------------------------|------------------------------------------------------|
| public Alignment alignment()   |                                                      |
| public int backgroundColor()   |                                                      |
| public int borderWidth()       |                                                      |
| public str CSSClass()          |                                                      |
| public int dateFormat()        |                                                      |
| public int decimals()          |                                                      |
| public int extendedDataType()  |                                                      |
| public FieldId fieldHandle()   |                                                      |
| public str fieldName()         |                                                      |
| public int fontHeight()        |                                                      |
| public str fontName()          |                                                      |
| public int foregroundColor()   |                                                      |
| public str formatValue()       |                                                      |
| public int height()            |                                                      |
| public int heightMode()        |                                                      |
| public boolean hideZeros()     |                                                      |
| public boolean isOneline()     |                                                      |
| public boolean isOverlapping() |                                                      |
| public boolean italic()        |                                                      |
| public LateEvalMode lateEval() |                                                      |
| public LineType lineBottom()   |                                                      |
| public LineType lineLeft()     |                                                      |
| public LineType lineRight()    |                                                      |
| public LineType lineTop()      |                                                      |
| public str menuFunctionHelp()  |                                                      |
| public str menuFunctionName()  |                                                      |
| public int menuFunctionType()  |                                                      |
| public str menuFunctionWeb()   |                                                      |
| public str name()              |                                                      |
| public int recId()             |                                                      |
| public boolean showPrompt()    |                                                      |
| public boolean strikeThrough() |                                                      |
| public TableId tableHandle()   |                                                      |
| public str tableName()         |                                                      |
| public boolean turnSign()      |                                                      |
| public int type()              |                                                      |
| public boolean underline()     |                                                      |
| public str webMenuItemName()   |                                                      |
| public int webMenuItemType()   |                                                      |
| public str webTarget()         |                                                      |
| public int weight()            |                                                      |
| public int width()             |                                                      |
| public int widthMode()         |                                                      |
| public int xPos()              |                                                      |
| public int yPos()              |                                                      |
| public void new()              | Initializes a new instance of the OutputField class. |

### Method alignment

    public Alignment alignment()

#### Return Value

### Method backgroundColor

    public int backgroundColor()

#### Return Value

### Method borderWidth

    public int borderWidth()

#### Return Value

### Method CSSClass

    public str CSSClass()

#### Return Value

### Method dateFormat

    public int dateFormat()

#### Return Value

### Method decimals

    public int decimals()

#### Return Value

### Method extendedDataType

    public int extendedDataType()

#### Return Value

### Method fieldHandle

    public FieldId fieldHandle()

#### Return Value

### Method fieldName

    public str fieldName()

#### Return Value

### Method fontHeight

    public int fontHeight()

#### Return Value

### Method fontName

    public str fontName()

#### Return Value

### Method foregroundColor

    public int foregroundColor()

#### Return Value

### Method formatValue

    public str formatValue()

#### Return Value

### Method height

    public int height()

#### Return Value

### Method heightMode

    public int heightMode()

#### Return Value

### Method hideZeros

    public boolean hideZeros()

#### Return Value

### Method isOneline

    public boolean isOneline()

#### Return Value

### Method isOverlapping

    public boolean isOverlapping()

#### Return Value

### Method italic

    public boolean italic()

#### Return Value

### Method lateEval

    public LateEvalMode lateEval()

#### Return Value

### Method lineBottom

    public LineType lineBottom()

#### Return Value

### Method lineLeft

    public LineType lineLeft()

#### Return Value

### Method lineRight

    public LineType lineRight()

#### Return Value

### Method lineTop

    public LineType lineTop()

#### Return Value

### Method menuFunctionHelp

    public str menuFunctionHelp()

#### Return Value

### Method menuFunctionName

    public str menuFunctionName()

#### Return Value

### Method menuFunctionType

    public int menuFunctionType()

#### Return Value

### Method menuFunctionWeb

    public str menuFunctionWeb()

#### Return Value

### Method name

    public str name()

#### Return Value

### Method recId

    public int recId()

#### Return Value

### Method showPrompt

    public boolean showPrompt()

#### Return Value

### Method strikeThrough

    public boolean strikeThrough()

#### Return Value

### Method tableHandle

    public TableId tableHandle()

#### Return Value

### Method tableName

    public str tableName()

#### Return Value

### Method turnSign

    public boolean turnSign()

#### Return Value

### Method type

    public int type()

#### Return Value

### Method underline

    public boolean underline()

#### Return Value

### Method webMenuItemName

    public str webMenuItemName()

#### Return Value

### Method webMenuItemType

    public int webMenuItemType()

#### Return Value

### Method webTarget

    public str webTarget()

#### Return Value

### Method weight

    public int weight()

#### Return Value

### Method width

    public int width()

#### Return Value

### Method widthMode

    public int widthMode()

#### Return Value

### Method xPos

    public int xPos()

#### Return Value

### Method yPos

    public int yPos()

#### Return Value

### Method new

Initializes a new instance of the OutputField class.

    public void new()

## Class OutputFooterSection
    class OutputFooterSection extends OuputSection

### Remarks

### Examples

### Methods

| Method                                | Description                                                  |
|---------------------------------------|--------------------------------------------------------------|
| public int level()                    |                                                              |
| public int level2field(\[int level\]) |                                                              |
| public int niveau()                   |                                                              |
| public int table()                    |                                                              |
| public void new()                     | Initializes a new instance of the OutputFooterSection class. |

### Method level

    public int level()

#### Return Value

### Method level2field

    public int level2field([int level])

#### Parameters

level  

#### Return Value

### Method niveau

    public int niveau()

#### Return Value

### Method table

    public int table()

#### Return Value

### Method new

Initializes a new instance of the OutputFooterSection class.

    public void new()

## Class OutputHeaderSection
    class OutputHeaderSection extends OuputSection

### Remarks

### Examples

### Methods

| Method             | Description                                                  |
|--------------------|--------------------------------------------------------------|
| public int table() |                                                              |
| public void new()  | Initializes a new instance of the OutputHeaderSection class. |

### Method table

    public int table()

#### Return Value

### Method new

Initializes a new instance of the OutputHeaderSection class.

    public void new()

## Class OutputIntegerField
    class OutputIntegerField extends OutputField

### Remarks

### Examples

### Methods

| Method                        | Description                                                 |
|-------------------------------|-------------------------------------------------------------|
| public int displaceNegative() |                                                             |
| public boolean negative()     |                                                             |
| public str toString()         | Returns a string that represents the current object.        |
| public int value()            |                                                             |
| public void new()             | Initializes a new instance of the OutputIntegerField class. |

### Method displaceNegative

    public int displaceNegative()

#### Return Value

### Method negative

    public boolean negative()

#### Return Value

### Method toString

Returns a string that represents the current object.

    public str toString()

#### Return Value

A string that represents the current object.

#### Remarks

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type. For example, an instance of the SysMethodInfo class returns the method name and the type of the method, such as instance or static.

### Method value

    public int value()

#### Return Value

### Method new

Initializes a new instance of the OutputIntegerField class.

    public void new()

## Class OutputLabelField
    class OutputLabelField extends OutputField

### Remarks

### Examples

### Methods

| Method                | Description                                               |
|-----------------------|-----------------------------------------------------------|
| public str toString() | Returns a string that represents the current object.      |
| public str value()    |                                                           |
| public void new()     | Initializes a new instance of the OutputLabelField class. |

### Method toString

Returns a string that represents the current object.

    public str toString()

#### Return Value

A string that represents the current object.

#### Remarks

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type. For example, an instance of the SysMethodInfo class returns the method name and the type of the method, such as instance or static.

### Method value

    public str value()

#### Return Value

### Method new

Initializes a new instance of the OutputLabelField class.

    public void new()

## Class OutputPage
    class OutputPage extends Object

### Remarks

### Examples

### Methods

| Method                        | Description                                         |
|-------------------------------|-----------------------------------------------------|
| public int bottomMargin()     |                                                     |
| public str fontName()         |                                                     |
| public int height()           |                                                     |
| public boolean layoutRTL()    |                                                     |
| public int leftMargin()       |                                                     |
| public str pageNumber()       |                                                     |
| public int rightMargin()      |                                                     |
| public int sectionNo()        |                                                     |
| public int topMargin()        |                                                     |
| public int unusedBottom()     |                                                     |
| public int unusedLeft()       |                                                     |
| public int unusedRight()      |                                                     |
| public int unusedTop()        |                                                     |
| public int virtualPageWidth() |                                                     |
| public int width()            |                                                     |
| public void new()             | Initializes a new instance of the OutputPage class. |

### Method bottomMargin

    public int bottomMargin()

#### Return Value

### Method fontName

    public str fontName()

#### Return Value

### Method height

    public int height()

#### Return Value

### Method layoutRTL

    public boolean layoutRTL()

#### Return Value

### Method leftMargin

    public int leftMargin()

#### Return Value

### Method pageNumber

    public str pageNumber()

#### Return Value

### Method rightMargin

    public int rightMargin()

#### Return Value

### Method sectionNo

    public int sectionNo()

#### Return Value

### Method topMargin

    public int topMargin()

#### Return Value

### Method unusedBottom

    public int unusedBottom()

#### Return Value

### Method unusedLeft

    public int unusedLeft()

#### Return Value

### Method unusedRight

    public int unusedRight()

#### Return Value

### Method unusedTop

    public int unusedTop()

#### Return Value

### Method virtualPageWidth

    public int virtualPageWidth()

#### Return Value

### Method width

    public int width()

#### Return Value

### Method new

Initializes a new instance of the OutputPage class.

    public void new()

## Class OutputPageFooterSection
    class OutputPageFooterSection extends OuputSection

### Remarks

### Examples

### Methods

| Method            | Description                                                      |
|-------------------|------------------------------------------------------------------|
| public void new() | Initializes a new instance of the OutputPageFooterSection class. |

### Method new

Initializes a new instance of the OutputPageFooterSection class.

    public void new()

## Class OutputPageHeaderSection
    class OutputPageHeaderSection extends OuputSection

### Remarks

### Examples

### Methods

| Method            | Description                                                      |
|-------------------|------------------------------------------------------------------|
| public void new() | Initializes a new instance of the OutputPageHeaderSection class. |

### Method new

Initializes a new instance of the OutputPageHeaderSection class.

    public void new()

## Class OutputProgrammableSection
    class OutputProgrammableSection extends OuputSection

### Remarks

### Examples

### Methods

| Method              | Description                                                        |
|---------------------|--------------------------------------------------------------------|
| public str number() |                                                                    |
| public void new()   | Initializes a new instance of the OutputProgrammableSection class. |

### Method number

    public str number()

#### Return Value

### Method new

Initializes a new instance of the OutputProgrammableSection class.

    public void new()

## Class OutputPrologSection
    class OutputPrologSection extends OuputSection

### Remarks

### Examples

### Methods

| Method            | Description                                                  |
|-------------------|--------------------------------------------------------------|
| public void new() | Initializes a new instance of the OutputPrologSection class. |

### Method new

Initializes a new instance of the OutputPrologSection class.

    public void new()

## Class OutputRealField
    class OutputRealField extends OutputField

### Remarks

### Examples

### Methods

| Method                        | Description                                              |
|-------------------------------|----------------------------------------------------------|
| public int displaceNegative() |                                                          |
| public boolean negative()     |                                                          |
| public str toString()         | Returns a string that represents the current object.     |
| public Real value()           |                                                          |
| public void new()             | Initializes a new instance of the OutputRealField class. |

### Method displaceNegative

    public int displaceNegative()

#### Return Value

### Method negative

    public boolean negative()

#### Return Value

### Method toString

Returns a string that represents the current object.

    public str toString()

#### Return Value

A string that represents the current object.

#### Remarks

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type. For example, an instance of the SysMethodInfo class returns the method name and the type of the method, such as instance or static.

### Method value

    public Real value()

#### Return Value

### Method new

Initializes a new instance of the OutputRealField class.

    public void new()

## Class OutputShapeField
    class OutputShapeField extends OutputField

### Remarks

### Examples

### Methods

| Method                       | Description                                               |
|------------------------------|-----------------------------------------------------------|
| public int borderWidth()     |                                                           |
| public LineType lineType()   |                                                           |
| public ShapeType shapeType() |                                                           |
| public str toString()        | Returns a string that represents the current object.      |
| public int value()           |                                                           |
| public void new()            | Initializes a new instance of the OutputShapeField class. |

### Method borderWidth

    public int borderWidth()

#### Return Value

### Method lineType

    public LineType lineType()

#### Return Value

### Method shapeType

    public ShapeType shapeType()

#### Return Value

### Method toString

Returns a string that represents the current object.

    public str toString()

#### Return Value

A string that represents the current object.

#### Remarks

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type. For example, an instance of the SysMethodInfo class returns the method name and the type of the method, such as instance or static.

### Method value

    public int value()

#### Return Value

### Method new

Initializes a new instance of the OutputShapeField class.

    public void new()

## Class OutputStaticTextField
    class OutputStaticTextField extends OutputField

### Remarks

### Examples

### Methods

| Method                | Description                                                    |
|-----------------------|----------------------------------------------------------------|
| public str toString() | Returns a string that represents the current object.           |
| public str value()    |                                                                |
| public void new()     | Initializes a new instance of the OutputStaticTextField class. |

### Method toString

Returns a string that represents the current object.

    public str toString()

#### Return Value

A string that represents the current object.

#### Remarks

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type. For example, an instance of the SysMethodInfo class returns the method name and the type of the method, such as instance or static.

### Method value

    public str value()

#### Return Value

### Method new

Initializes a new instance of the OutputStaticTextField class.

    public void new()

## Class OutputStringField
    class OutputStringField extends OutputField

### Remarks

### Examples

### Methods

| Method                | Description                                                |
|-----------------------|------------------------------------------------------------|
| public str toString() | Returns a string that represents the current object.       |
| public str value()    |                                                            |
| public void new()     | Initializes a new instance of the OutputStringField class. |

### Method toString

Returns a string that represents the current object.

    public str toString()

#### Return Value

A string that represents the current object.

#### Remarks

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type. For example, an instance of the SysMethodInfo class returns the method name and the type of the method, such as instance or static.

### Method value

    public str value()

#### Return Value

### Method new

Initializes a new instance of the OutputStringField class.

    public void new()

## Class OutputSumField
    class OutputSumField extends OutputField

### Remarks

### Examples

### Methods

| Method                | Description                                             |
|-----------------------|---------------------------------------------------------|
| public str toString() | Returns a string that represents the current object.    |
| public Real value()   |                                                         |
| public void new()     | Initializes a new instance of the OutputSumField class. |

### Method toString

Returns a string that represents the current object.

    public str toString()

#### Return Value

A string that represents the current object.

#### Remarks

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type. For example, an instance of the SysMethodInfo class returns the method name and the type of the method, such as instance or static.

### Method value

    public Real value()

#### Return Value

### Method new

Initializes a new instance of the OutputSumField class.

    public void new()

## Class OutputTimeField
    class OutputTimeField extends OutputField

### Remarks

### Examples

### Methods

| Method                | Description                                              |
|-----------------------|----------------------------------------------------------|
| public str toString() | Returns a string that represents the current object.     |
| public int value()    |                                                          |
| public void new()     | Initializes a new instance of the OutputTimeField class. |

### Method toString

Returns a string that represents the current object.

    public str toString()

#### Return Value

A string that represents the current object.

#### Remarks

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type. For example, an instance of the SysMethodInfo class returns the method name and the type of the method, such as instance or static.

### Method value

    public int value()

#### Return Value

### Method new

Initializes a new instance of the OutputTimeField class.

    public void new()

## Class OverwriteSystemfieldsPermission
    class OverwriteSystemfieldsPermission extends CodeAccessPermission

### Remarks

### Examples

### Methods

| Method                                                 | Description                                                                                                               |
|--------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------|
| public CodeAccessPermission copy()                     | Creates and returns a copy of a permission class object.                                                                  |
| public boolean isSubsetOf(CodeAccessPermission target) | Determines whether a current permission is a subset of the specified permission when it is overridden by a derived class. |
| public void new()                                      | Initializes a new instance of the OverwriteSystemfieldsPermission class.                                                  |

### Method copy

Creates and returns a copy of a permission class object.

    public CodeAccessPermission copy()

#### Return Value

A copy of the derived class object.

#### Remarks

You can override this method as part of the process of making an API more secure. For more information, see “Securing an API that Executes on the Server Tier.”

### Method isSubsetOf

Determines whether a current permission is a subset of the specified permission when it is overridden by a derived class.

    public boolean isSubsetOf(CodeAccessPermission target)

#### Parameters

target  
A CodeAccessPermission class object.

#### Return Value

true if a current permission is a subset of a specified permission; otherwise, false.

#### Remarks

You can override the method as part of the process of making an API more secure. For more information, see “Securing an API that Executes on the Server Tier.”

### Method new

Initializes a new instance of the OverwriteSystemfieldsPermission class.

    public void new()

