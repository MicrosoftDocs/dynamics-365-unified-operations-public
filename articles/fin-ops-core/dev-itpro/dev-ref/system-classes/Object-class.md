---
title: Object class
description: This topic describes the Object class.
author: robinarh
manager: tonyafehr
ms.date: 06/25/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

audience: Developer
ms.reviewer: rhaertle
ms.search.scope: Operations
ms.search.region: Global
ms.author: rhaertle
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Class Object

[!include [banner](../../includes/banner.md)]


```xpp
class Object
```

The Object class is the base class from which all other classes are derived.

## Remarks

Methods in the Object class can be called for any object. The Object class is used to allow assignment and equality checks to be performed without the developer having to know the actual type of the object. The methods can be grouped into three groups:

-   Time out methods - can be used to activate a method after a specified period of time has passed.
-   Process methods, such as the Wait, Notify, and NotifyAll method - used to control process flow and to wait for another object to finish its task.
-   Class methods - return basic information about the object.

## Examples

## Methods

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

## Method equal

Determines whether the specified object is equal to the current one.

```xpp
public boolean equal(Object object)
```

### Parameters - equal

object  
The object to compare with the current object.

### Return Value - equal

true if the specified object is equal to the current object; otherwise, false.

### Remarks - equal

The default implementation of the Object::equal method supports only reference equality. Derived classes can, however, override the Object::equal method to support value equality.

### Examples - equal

The following example compares the current instance with another object.

```xpp
static void Object_Equal(Args _args) 
{ 
    Object objA = new Object(); 
    Object objB = new Object(); 
    print objA.equal(objA);  // true. 
    print objA.equal(objB);  // false. 
    objA = objB; 
    print objA.equal(objB);  // true. 
 }
```

## Method getTimeOutTimerHandle

Returns the timer handle for the object.

```xpp
public int getTimeOutTimerHandle()
```

### Return Value - getTimeOutTimerHandle

The timer handle of the object.

### Remarks - getTimeOutTimerHandle

The timer handle of the object is set by calling the setTimeOut method.

### Examples - getTimeOutTimerHandle

The following example sets a timeout, and then cancels it.

```xpp
public void myJob() 
{ 
    int timerHandle = 0; 
    this.setTimeOut(identifierstr(workerFunction), 0); 
    //Perform some operations. 
    timerHandle = this.getTimeOutTimerHandle(); 
    this.cancelTimeOut( timerHandle ); 
}
```

## Method handle

Retrieves the handle of the class of the object.

```xpp
public ClassId handle()
```

### Return Value - handle

The handle, that is, the classId property, of the class of the current object.

### Remarks - handle

There is no guarantee that the handle of a class will remain unchanged in later releases, or after an export or import for user-defined classes. It is strongly advised that the value that is returned by this method will not be used as a persistent constant to refer to the class.

## Method SysObsoleteAttribute

```xpp
public boolean SysObsoleteAttribute()
```

### Return Value - SysObsoleteAttribute

## Method SysObsoleteAttribute

```xpp
public int SysObsoleteAttribute(str Method, int WaitTime, [boolean idle])
```

### Parameters - SysObsoleteAttribute

Method  

<!-- -->

WaitTime  

<!-- -->

idle  

### Return Value - SysObsoleteAttribute

## Method toString

Returns a string that represents the current object.

```xpp
public str toString()
```

### Return Value - toString

A string that represents the current object.

### Remarks - toString

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type. For example, an instance of the SysMethodInfo class returns the method name and type of the method, such as instance or static.

### Examples - toString

The following example prints out the class name of o.

```xpp
static void Object_ToString_Job(Args _args) 
{ 
    Object o = new Object(); 
    print o.toString();  // Prints out: "Class Object" 
    pause; 
}
```

## Method usageCount

Returns the current number of references, that is, the value of the reference counter, that the object has.

```xpp
public int usageCount()
```

### Return Value - usageCount

The current number of references that the object has.

### Remarks - usageCount

When an object is created, its reference counter equals 1. When a new reference is created, its value increases. As a reference goes out of scope, its value decreases.

### Examples - usageCount

The following example prints the number of references for objA to the output window.

```xpp
static void Object_UsageCount(Args _args) 
{ 
    Object objA = new Object(); 
    Object objB; 
    print objA.usageCount();    // Prints 1. 
    objB = objA;                // objB is a reference to objA. 
    print objA.usageCount();    // prints 2 
    pause; 
}
```

## Method xml

Returns an XML string that represents the current object.

```xpp
public str xml([int indent])
```

### Parameters - xml

indent  
The amount of indentation of the returned XML string; optional.

### Return Value - xml

An XML string that represents the current object.

### Remarks - xml

This method can be overridden to return values that are meaningful for that type.

## Method Equals

```xpp
public boolean Equals(System.Object obj)
```

### Parameters - Equals

obj  

### Return Value - Equals

## Method GetHashCode

```xpp
public int GetHashCode()
```

### Return Value - GetHashCode

## Method finalize

```xpp
public void finalize()
```

## Method wait

Pauses a process.

```xpp
public void wait()
```

### Remarks - wait

The most common use for this method is to start an object that asks the user for some input and then call the wait method on that object, such as a form. The next line of code is not executed until the object has called the notify or notifyAll method. When the wait method is called from a form, you do not have to call the notify methods manually because forms call the Object.notifyAll method when the user either closes the form or presses the Apply button. This method is not meant for thread synchronization. Use the waitUntilSignaled method instead.

### Examples - wait

The following example opens the GetUserInput dialog, blocks, and waits until the user has closed the form.

```xpp
{ 
    Args a = new Args("GetUserInput"); 
    formRun fr = new formRun(a); 
    fr.init(); 
    fr.run(); 
    fr.wait(); 
    // Execution will resume at this point, only after 
    // the user has closed the form. 
}
```

## Method cancelTimeOut

Cancels a previous method call to the setTimeOut method.

```xpp
public void cancelTimeOut(int timerHandle)
```

### Parameters - cancelTimeOut

timerHandle  
The handle of the scheduled event to delete. The handle is the value that is returned by the Object.setTimeOut method.

### Remarks - cancelTimeOut

Any scheduled time-out calls that have not yet been processed are automatically deleted when the object itself is deleted.

### Examples - cancelTimeOut

The following example calls the Object.setTimeOut method, and then cancels the time-out.

```xpp
void Object_cancelTimeOut(Args _args) 
{ 
    int th; // timerHandle. 
    // timedMethod is a worker method. 
    th = this.setTimeOut( "timedMethod", 2000 ); 
    //.... 
    // Remove timeOut later. 
    CancelTimeOut(th); 
}
```

## Method new

Initializes a new instance of the Object class.

```xpp
public void new()
```

## Method notify

Releases the hold on an object that has called the wait method on this object.

```xpp
public void notify()
```

### Examples - notify

The following example locks an object, and then releases it.

```xpp
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
```

## Method notifyAll

Releases a lock on the object that was issued by the wait method on this object.

```xpp
public void notifyAll()
```

### Remarks - notifyAll

In the current implementation of this method, there is no difference between calling the notify method and the notifyAll method. Forms will automatically call the notifyAll method when the user closes the form or presses the Apply button.

### Examples - notifyAll

The following example demonstrates the usage of the notifyAll method.

```xpp
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
```

