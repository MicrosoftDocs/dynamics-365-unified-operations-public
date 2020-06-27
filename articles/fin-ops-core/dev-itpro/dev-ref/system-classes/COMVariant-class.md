---
title: COMVariant class
description: This topic describes the COMVariant class.
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

# Class COMVariant

[!include [banner](../../includes/banner.md)]

```xpp
class COMVariant extends Object
```

The COMVariant class is used as a generic class that can store different types of data. The class is used to pass arguments to the methods or properties of a COM (Component Object Model) Automation object and is used with the COM and COMDispFunction classes.

## Remarks

The data type of the COMVariant object can be set by:

-   The new method
-   The variantType method
-   The createFrom� methods. For example, the createFromBoolean method creates a COMVariant object of type VT\_BOOL (= Boolean).
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

## Examples

The following example instantiates a COM object that exposes a method called multiply which multiplies two floating point numbers passed in as COMVariant parameters.

```xpp
{ 
    COM com; 
    COMVariant varArg1 = new COMVariant(); 
    COMVariant varArg2 = new COMVariant(); 
    COMVariant varRet; 
    real ret; 
    InteropPermission perm; 
```

```xpp
    // Set code access permission to help protect the use  
    // of the COM object. 
    perm = new InteropPermission(InteropKind::ComInterop); 
    if (perm == null) 
    { 
        return; 
    } 
```

```xpp
    // Permission scope starts here 
    perm.assert(); 
```

```xpp
        com = new COM("MyCOM.Object"); 
```

```xpp
    // Specify arguments for the 'multiply' method 
    varArg1.float(123); 
    varArg2.float(456); 
    varRet = com.multiply(varArg1, varArg2); 
```

```xpp
    ret = varRet.double(); 
    // 'ret' is now 56088 (123*456) 
```

```xpp
    // Close the code access permission scope. 
    CodeAccessPermission::revertAssert(); 
}
```

## Methods

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

## Method boolean

Gets or sets the value of a COMVariant object of the VT\_BOOL data type.

```xpp
public boolean boolean([boolean newValue])
```

### Parameters - boolean

newValue  
The new value; optional.

### Return Value - boolean

The current value.

### Remarks - boolean

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. A COMVariant object has a Boolean type if its data type is set to COMVariantType::VT\_BOOL. The COM Boolean data type may also be referred to as "VARIANT\_BOOL".

### Examples - boolean

The following example creates a new COMVariant object of type VT\_BOOL and sets the value to true.

```xpp
{ 
    COMVariant var = new COMVariant( 
        COMVariantInOut::IN_OUT,  
        COMVariantType::VT_BOOL); 
```

```xpp
    // Set value of the object 
    var.boolean(true); 
}
```

## Method bStr

Gets or sets the value of a COMVariant object of the VT\_BSTR data type.

```xpp
public str bStr([str newValue])
```

### Parameters - bStr

newValue  
The new value; optional.

### Return Value - bStr

The current string value.

### Remarks - bStr

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. A COMVariant object has a string data type if its data type is set to COMVariantType::VT\_BSTR. The BStr data type is a COM data type that is used for handling strings.

### Examples - bStr

The following example creates a new COMVariant object of type VT\_BSTR, and sets the value to "Hello World."

```xpp
{ 
    COMVariant var = new COMVariant( 
        COMVariantInOut::IN_OUT,  
        COMVariantType::VT_BSTR); 
```

```xpp
    // Set string value of the object 
    var.bStr("Hello World"); 
}
```

## Method byte

Gets or sets the value of a COMVariant object of the VT\_UI1 data type.

```xpp
public int byte([int newValue])
```

### Parameters - byte

newValue  
The new value; optional.

### Return Value - byte

The current value.

### Remarks - byte

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. A COMVariant object has a byte data type if its data type is set to COMVariantType::VT\_UI1. You can also use "unsigned char" to refer to the COM byte data type.

### Examples - byte

The following example creates a new COMVariant object of the VT\_UI1 type and sets the value to 123.

```xpp
{ 
    COMVariant var = new COMVariant( 
        COMVariantInOut::IN_OUT,  
        COMVariantType::VT_UI1); 
```

```xpp
    // Set value of the object 
    var.byte(123); 
}
```

## Method char

Gets or sets the value of a COMVariant object of the VT\_I1 data type.

```xpp
public int char([int newValue])
```

### Parameters - char

newValue  
The new value; optional.

### Return Value - char

The current value.

### Remarks - char

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. A COMVariant object has a char data type if its data type is set to COMVariantType::VT\_I1.

### Examples - char

The following example creates a new COMVariant object of type VT\_I1 and sets the value to the numeric value of A, which is 65.

```xpp
{ 
    COMVariant var = new COMVariant( 
        COMVariantInOut::IN_OUT,  
        COMVariantType::VT_I1); 
```

```xpp
    // Set value of the object 
    var.char(Char2Num("A", 1)); 
}
```

## Method container

Gets or sets the value of a COMVariant object of the container data type.

```xpp
public container container([container newValue], [COMVariantType newType])
```

### Parameters - container

newValue  
The type of the new container; optional. The default is for the container to store integers.

<!-- -->

newType  
The type of the new container; optional. The default is for the container to store integers.

### Return Value - container

The current container.

### Remarks - container

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

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. When a container is stored in a COMVariant object, the binary representation of the container is stored in a binary array (see the COMVariant.safeArray method). The container property is useful when you need to store data in a database COM object and then later read the data back into a Finance and Operations application without the COM object processing the data. The container property is an advanced property of the COMVariant class. It should be used with caution because the content of the binary array that the container is stored in, inside the COMVariant object, must not be changed by any COM object.

### Examples - container

The following example creates a new COMVariant object of type container. The data in the container is passed to, and used by, a database COM object. Note The code in the following section contains a hypothetical COM object MyDatabaseCOM.Object" and will therefore not run, unless such an object is created outside a Finance and Operations application.

```xpp
{ 
    COM com; 
    COMVariant var = new COMVariant(); 
    container con; 
    InteropPermission perm; 
```

```xpp
    // Set code access permission to help protect use of COM object 
    perm = new InteropPermission(InteropKind::ComInterop); 
    if (perm == null) 
    { 
        return; 
    } 
```

```xpp
    // Permission scope starts here 
    perm.assert(); 
```

```xpp
    // Put some data in the container 
    con = conins(con, 1, "Element 1"); 
    con = conins(con, 2, "Element 2"); 
    // Set value of the object and ensure the data 
    // is stored in a binary array of bytes 
    var.container(con, COMVariantType::VT_UI1); 
```

```xpp
    // Create a database object to store the data in 
    com = new COM("MyDatabaseCOM.Object"); 
    com.writeData(var); 
    // ... 
```

```xpp
    // Close code access permission 
    CodeAccessPermission::revertAssert(); 
}
```

## Method currency

Gets or sets the value of a COMVariant object of the VT\_CY data type.

```xpp
public Real currency([Real newValue])
```

### Parameters - currency

newValue  
The new value; optional.

### Return Value - currency

The current value.

### Remarks - currency

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. A COMVariant object has a currency data type if its data type is set to COMVariantType::VT\_CY. The currency data type is a COM data type that is optimized for currency values. It is a real number with four decimal places. Sometimes "CY" is also used to refer to the COM currency data type.

### Examples - currency

The following example creates a new COMVariant object of type VT\_CY and sets the value to 123.4567.

```xpp
{ 
    COMVariant var = new COMVariant( 
        COMVariantInOut::IN_OUT,  
        COMVariantType::VT_CY); 
```

```xpp
    // Set value of the object 
    var.currency(123.4567); 
}
```

## Method date

Gets or sets the date part of the value of a COMVariant object of the VT\_DATE data type.

```xpp
public Date date([Date newValue])
```

### Parameters - date

newValue  
The new value; optional.

### Return Value - date

The current value.

### Remarks - date

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. A COMVariant object has a date and time data type if its data type is set to COMVariantType::VT\_DATE. When you set the value of the object, you must set the time part of the value in addition to the date. To set the time part of the value, use the time property.

### Examples - date

The following example creates a COMVariant object of type VT\_DATE and sets the date part of the value to 24 December 1998, and the time part of the value to 13.24.

```xpp
{ 
    COMVariant var = new COMVariant( 
        COMVariantInOut::IN_OUT,  
        COMVariantType::VT_DATE); 
```

```xpp
    // Set value of the object 
    var.date(Str2Date("12.24.1998", 213)); 
    var.time(Str2Time("13:24:00")); 
}
```

## Method decimal

Gets or sets the value of a COMVariant object of the VT\_DECIMAL data type.

```xpp
public Real decimal([Real newValue])
```

### Parameters - decimal

newValue  
The new value; optional.

### Return Value - decimal

The current value.

### Remarks - decimal

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. A COMVariant object has a decimal type if its data type is set to COMVariantType::VT\_DECIMAL. The decimal data type is a COM data type that provides size and scale for a number. There is no parallel to the decimal data type in X++.

### Examples - decimal

The following example creates a new COMVariant object of type VT\_DECIMAL and sets the value to 123.456.

```xpp
{ 
    COMVariant var = new COMVariant( 
        COMVariantInOut::IN_OUT,  
        COMVariantType::VT_DECIMAL); 
```

```xpp
    // Set value of the object 
    var.decimal(123.456); 
}
```

## Method double

Gets or sets the value of a COMVariant object of the VT\_R8 data type.

```xpp
public Real double([Real newValue])
```

### Parameters - double

newValue  
The new value; optional.

### Return Value - double

The current value.

### Remarks - double

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. A COMVariant object has a double data type if its data type is set to COMVariantType::VT\_R8.

### Examples - double

The following example creates a new COMVariant object of type VT\_R8 and sets the value to 123.456.

```xpp
{ 
    COMVariant var = new COMVariant( 
        COMVariantInOut::IN_OUT,  
        COMVariantType::VT_R8); 
```

```xpp
    // Set value of the object 
    var.double(123.456); 
}
```

## Method float

Gets or sets the value of a COMVariant object of the VT\_R4 data type.

```xpp
public Real float([Real newValue])
```

### Parameters - float

newValue  
The new value; optional.

### Return Value - float

The current value.

### Remarks - float

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. A COMVariant object has a float type if its data type is set to COMVariantType::VT\_R4. Sometimes "single" is also used to refer to the COM float data type.

### Examples - float

The following example creates a new COMVariant object of type VT\_R4 and sets the value to 123.456.

```xpp
{ 
    COMVariant var = new COMVariant( 
        COMVariantInOut::IN_OUT,  
        COMVariantType::VT_R4); 
```

```xpp
    // Set value of the object 
    var.float(123.456); 
}
```

## Method iDispatch

Gets or sets the value of a COMVariant object of the VT\_DISPATCH data type.

```xpp
public ComInterface iDispatch([ComInterface newValue])
```

### Parameters - iDispatch

newValue  
The new value; optional.

### Return Value - iDispatch

The current value.

### Remarks - iDispatch

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. A COMVariant object has an IDispatch data type if its data type is set to COMVariantType::VT\_DISPATCH. The IDispatch data type is a COM data type that provides a handle to a COM IDispatch interface.

### Examples - iDispatch

The following example creates a new COMVariant object of type VT\_DISPATCH.

```xpp
{ 
    COMVariant var = new COMVariant( 
        COMVariantInOut::IN_OUT,  
        COMVariantType::VT_DISPATCH); 
    COMInterface comInterface; 
```

```xpp
    // Here, the comInterface variable must be assigned 
    // a COM IDispatch interface 
    //� 
```

```xpp
    // Set value of the object 
    var.iDispatch(comInterface); 
}
```

## Method int

Gets or sets the value of a COMVariant object of the VT\_I4 data type.

```xpp
public int int([int newValue])
```

### Parameters - int

newValue  
The new value; optional.

### Return Value - int

The current value.

### Remarks - int

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. The COMVariantType::VT\_I4 data type is also used for the long variant type. The COMVariant.long method is identical to this method; the two methods exist for completeness.

### Examples - int

The following example creates a COMVariant object of type VT\_I4 and sets the value to 123456.

```xpp
{ 
    COMVariant var = new COMVariant( 
        COMVariantInOut::IN_OUT,  
        COMVariantType::VT_I4); 
```

```xpp
    // Set value of the object 
    var.int(123456); 
}
```

## Method iUnknown

Gets or sets the value of a COMVariant object of the VT\_UNKNOWN (IUnknown) data type.

```xpp
public ComInterface iUnknown([ComInterface newValue])
```

### Parameters - iUnknown

newValue  
The new value; optional.

### Return Value - iUnknown

The current value.

### Remarks - iUnknown

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type value. A COMVariant object has an IUnknown data type if its data type is set to COMVariantType::VT\_UNKNOWN. The IUnknown data type is a COM data type that provides a handle to a COM IUnknown interface.

### Examples - iUnknown

The following example creates a new COMVariant object of type VT\_UNKNOWN.

```xpp
{ 
    COMVariant var = new COMVariant( 
        COMVariantInOut::IN_OUT,  
        COMVariantType::VT_UNKNOWN); 
    COMInterface comInterface; 
```

```xpp
    // comInterface variable is assigned 
    // a COM IUnknown interface 
    // ... 
```

```xpp
    // Set value of the object 
    var.iUnknown(comInterface); 
}
```

## Method long

Gets or sets the value of a COMVariant object of the VT\_I4 data type.

```xpp
public int long([int newValue])
```

### Parameters - long

newValue  
The new value; optional.

### Return Value - long

The current value.

### Remarks - long

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. The COMVariantType::VT\_I4 data type is also used for the int variant type. The COMVariant.int method is identical to this method; the two methods exist for completeness.

### Examples - long

The following example creates a COMVariant object of type VT\_I4 and sets the value to 123456.

```xpp
{ 
    COMVariant var = new COMVariant( 
        COMVariantInOut::IN_OUT,  
        COMVariantType::VT_I4); 
```

```xpp
    // Set value of the object 
    var.long(123456); 
}
```

## Method longLong

Gets or sets the value of a COMVariant object of the VT\_I8 (longlong) data type.

```xpp
public Int64 longLong([Int64 newValue])
```

### Parameters - longLong

newValue  
The new value; optional.

### Return Value - longLong

The current value.

### Remarks - longLong

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the value�s data type. A COMVariant object has a longlong variant type if its data type is set to COMVariantType::VT\_I8.

### Examples - longLong

The following example creates a new COMVariant object of type VT\_I8 and sets the value to 2,305,843,009,213,693,952.

```xpp
{ 
    COMVariant var = new COMVariant( 
        COMVariantInOut::IN_OUT,  
        COMVariantType::VT_BOOL); 
```

```xpp
    // Set value of the object 
    var.longLong(2305843009213693952); 
}
```

## Method safeArray

Gets or sets the value of a COMVariant object of the VT\_SAFEARRAY data type.

```xpp
public Array safeArray([Array newValue], [COMVariantType newType])
```

### Parameters - safeArray

newValue  
The type of the new array; optional.

<!-- -->

newType  
The type of the new array; optional.

### Return Value - safeArray

The current array.

### Remarks - safeArray

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. A COMVariant object has an array Boolean type if its data type is set to COMVariantType::VT\_SAFEARRAY. A safe array is COM's equivalent to an array. Currently only one-dimensional safe arrays are supported.

### Examples - safeArray

The following example creates a new COMVariant object of type VT\_SAFEARRAY and initializes it with an array of shorts.

```xpp
{ 
    int i, result; 
    COM com; 
    COMVariant var = new COMVariant( 
        COMVariantInOut::IN_OUT,  
        COMVariantType::VT_SAFEARRAY); 
    Array arr = new Array(Types::INTEGER); 
```

```xpp
    // Insert 10 values in the array 
    for (i = 1; i <= 10; i++) 
    { 
        arr.value(i, i); 
    } 
```

```xpp
    // Set value of the object and ensure the integer values 
    // are treated as short data types 
    var.safeArray(arr, COMVariantType::VT_I2); 
}
```

## Method sCode

Gets or sets the value of a COMVariant object of the VT\_ERROR data type.

```xpp
public int sCode([int newValue])
```

### Parameters - sCode

newValue  
The new value; optional.

### Return Value - sCode

The current value.

### Remarks - sCode

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. A COMVariant object has an scode data type if its data type is set to COMVariantType::VT\_ERROR. The scode data type is a COM data type that is equivalent to the Win32 HRESULT data type, which is most used as return values for COM functions.

### Examples - sCode

The following example creates a new COMVariant object of type VT\_ERROR and sets the value to 0x80001004.

```xpp
{ 
    COMVariant var = new COMVariant( 
        COMVariantInOut::IN_OUT,  
        COMVariantType::VT_ERROR); 
```

```xpp
    // Set value of the object 
    var.sCode(0x80001004); 
}
```

## Method short

Gets or sets the value of a COMVariant object of the VT\_I2 (short) data type.

```xpp
public int short([int newValue])
```

### Parameters - short

newValue  
The new value; optional.

### Return Value - short

The current value.

### Remarks - short

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. A COMVariant object has a short data type if its data type is set to COMVariantType::VT\_I2.

### Examples - short

The following example creates a new COMVariant object of the VT\_I2 type and sets the value to 123.

```xpp
{ 
    COMVariant var = new COMVariant( 
        COMVariantInOut::IN_OUT,  
        COMVariantType::VT_I2); 
```

```xpp
    // Set value of the object 
    var.short(123); 
}
```

## Method time

Gets or sets the time part of the value of a COMVariant object of the VT\_DATE data type.

```xpp
public int time([int newValue])
```

### Parameters - time

newValue  
The new value; optional.

### Return Value - time

The current value.

### Remarks - time

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. A COMVariant object has a date and time data type if its data type is set to COMVariantType::VT\_DATE. When you set the value of the object, you must set the date part of the value in addition to the time. To set the date part of the value, use the date property.

### Examples - time

The following example creates a COMVariant object of type VT\_DATE and sets the date part of the value to 24 December 1998, and the time part of the value to 13.24.

```xpp
{ 
    COMVariant var = new COMVariant( 
        COMVariantInOut::IN_OUT,  
        COMVariantType::VT_DATE); 
```

```xpp
    // Set value of the object 
    var.date(Str2Date("12.24.1998", 213)); 
    var.time(Str2Time("13:24:00")); 
}
```

## Method toString

Creates a string representation of a COMVariant object. This string representation includes the value and type of the object.

```xpp
public str toString()
```

### Return Value - toString

The string representation of the COMVariant object.

### Remarks - toString

The actual string returned from this method depends on the variant data type of the COMVariant object.

### Examples - toString

The following example creates a COMVariant object and assigns the current date to it. It then prints a description of the object to the Infolog.

```xpp
COMVariant theDay; 
```

```xpp
theDay = COMVariant::createFromDate(today()); 
info(theDay.toString());
```

## Method uInt

Gets or sets the value of a COMVariant object of the VT\_UI4 data type.

```xpp
public int uInt([int newValue])
```

### Parameters - uInt

newValue  
The new value; optional.

### Return Value - uInt

The current value.

### Remarks - uInt

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. The COMVariantType::VT\_UI4 data type is also used for the uLong data type.

### Examples - uInt

The following example creates a new COMVariant object of the VT\_UI4 type and sets the value to 123456.

```xpp
{ 
    COMVariant var = new COMVariant( 
        COMVariantInOut::IN_OUT,  
        COMVariantType::VT_UI4); 
```

```xpp
    // Set value of the object 
    var.uInt(123456); 
}
```

## Method uLong

Gets or sets the value of a COMVariant object of the VT\_UI4 (unsigned long) data type.

```xpp
public int uLong([int newValue])
```

### Parameters - uLong

newValue  
The new value; optional.

### Return Value - uLong

The current value.

### Remarks - uLong

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. The COMVariantType::VT\_UI4 data type is also used for the uInt data type.

### Examples - uLong

The following example creates a new COMVariant object of type VT\_UI4 and sets the value to 123456.

```xpp
{ 
    COMVariant var = new COMVariant( 
        COMVariantInOut::IN_OUT,  
        COMVariantType::VT_UI4); 
```

```xpp
    // set value of the object 
    var.uLong(123456); 
}
```

## Method uLongLong

Gets or sets the value of a COMVariant object of the VT\_UI8 (unsigned longlong) data type.

```xpp
public Int64 uLongLong([Int64 newValue])
```

### Parameters - uLongLong

newValue  
The new value; optional.

### Return Value - uLongLong

The current value.

### Remarks - uLongLong

If you pass in a value that has a different data type than the object, the object�s data type will be changed to match the value�s data type. A COMVariant object has an unsigned longlong variant type if its data type is set to COMVariantType::VT\_I8.

### Examples - uLongLong

The following example creates a new COMVariant object of type VT\_I8 and sets the value to 9,223,372,036,854,775,808.

```xpp
{ 
    COMVariant var = new COMVariant( 
        COMVariantInOut::IN_OUT,  
        COMVariantType::VT_BOOL); 
```

```xpp
    // Set value of the object 
    var.longLong(9223372036854775808); 
}
```

## Method uShort

Gets or sets the value of a COMVariant object of the VT\_UI2 data type.

```xpp
public int uShort([int newValue])
```

### Parameters - uShort

newValue  
The new value; optional.

### Return Value - uShort

The current value.

### Remarks - uShort

If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. A COMVariant object has an unsigned short data type if its data type is set to COMVariantType::VT\_UI2.

### Examples - uShort

The following example creates a new COMVariant object of type VT\_UI2 and sets the value to 12345.

```xpp
{ 
    COMVariant var = new COMVariant( 
        COMVariantInOut::IN_OUT,  
        COMVariantType::VT_UI2); 
```

```xpp
    // Set value of the object 
    var.uShort(12345); 
}
```

## Method variant

Gets or sets the value of a COMVariant object of the VT\_VARIANT (variant) data type.

```xpp
public COMVariant variant([COMVariant newValue])
```

### Parameters - variant

newValue  
The new value; optional.

### Return Value - variant

The current value.

### Remarks - variant

The variant property is used to nest one COMVariant object in another COMVariant object. When using the parent object as the argument in a call to COMDispFunction.call or in a call to the COM class, the called method will automatically extract the data of the nested object. This nesting facility is useful when a method on a COM object can work with multiple data types. Only one level of variant nesting is allowed. If you pass in a value that has a different data type than the object, the data type of the object will be changed to match the data type of the value. A COMVariant object has a variant type if its data type is set to COMVariantType::VT\_VARIANT.

### Examples - variant

The following example creates a COMVariant object of type VT\_I4 (long), and a COMVariant object of type VT\_VARIANT. The object of type VT\_VARIANT is assigned the value of the object of type VT\_I4. The code below contains a hypothetical COM object ("MyCOM.Object"), and will therefore not run, unless such an object is created outside a Finance and Operations application.

```xpp
{ 
    COM com; 
    COMDispFunction funcShow; 
```

```xpp
    COMVariant var1 = new COMVariant( 
        COMVariantInOut::IN_OUT,  
        COMVariantType::VT_I4); 
```

```xpp
    COMVariant var2 = new COMVariant( 
        COMVariantInOut::IN_OUT,  
        COMVariantType::VT_VARIANT); 
```

```xpp
    InteropPermission perm1; 
    InteropPermission perm2; 
```

```xpp
    // Set code access permission to help protect use of COM object 
    perm1 = new InteropPermission(InteropKind::ComInterop); 
    perm1.assert(); 
```

```xpp
    com = new COM("MyCOM.Object"); 
```

```xpp
    // Close code access permission for COM 
    CodeAccessPermission::revertAssert(); 
```

```xpp
    // Set value of 'var1' 
    var1.Long(123456); 
    // Set value of 'var2' to 'var1' 
    var2.Variant(var1); 
```

```xpp
    // Set code access permission to protect use of 
    // COMDispFunction object 
    perm2 = new InteropPermission(InteropKind::ComInterop); 
    perm2.assert(); 
```

```xpp
    funcShow = new COMDispFunction( 
        com,  
        "Show",  
        COMDispContext::METHOD); 
```

```xpp
    // Call funcShow with a long 
    funcShow.Call(var2); 
    // Change value of 'var1' 
     var1.BStr("Hello World"); 
    // Call funcShow with a string 
    funcShow.Call(var2); 
```

```xpp
    // Close code access permission for COMDispFunction 
    CodeAccessPermission::revertAssert(); 
}
```

## Method variantInOutFlag

Sets or returns the InOutFlag setting for a COMVariant object.

```xpp
public COMVariantInOut variantInOutFlag([COMVariantInOut newValue])
```

### Parameters - variantInOutFlag

newValue  
The new InOutFlag setting; optional.

### Return Value - variantInOutFlag

The current InOutFlag setting.

### Remarks - variantInOutFlag

The following is a list of possible values for the newValue parameter.

-   COMVariantInOut::IN
-   COMVariantInOut::IN\_OUT
-   COMVariantInOut::OUT
-   COMVariantInOut::OUT\_RETVAL.

The InOutFlag setting describes how the data that is stored in the object is treated when the object is used as an argument in the COMDispFunction.call method. The possible values of the InOutFlag setting correspond to the values for COM Automation objects described in the Win32 SDK. The data stored in the COMVariant object is unaffected when the InOutFlag setting is changed.

### Examples - variantInOutFlag

The following example creates a COMVariant object that has the InOutFlag setting set to IN, and then uses the variantInOutFlag method to change the setting to OUT.

```xpp
{ 
    COMVariant var = new COMVariant(COMVariantInOut::IN); 
```

```xpp
    // Change the 'var' object to be used as an out argument 
    var.variantInOutFlag(COMVariantInOut::OUT); 
}
```

## Method variantType

Queries a COMVariant object for its variant data type or changes the data type.

```xpp
public COMVariantType variantType([COMVariantType newValue])
```

### Parameters - variantType

newValue  
The new variant data type; optional.

### Return Value - variantType

The current variant data type.

### Remarks - variantType

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

### Examples - variantType

The following example creates a new COMVariant object and sets it to be of long (VT\_I4) data type. The variantType method is then used to change the data type to VT\_DATE (date). The data that is held by the object is discarded.

```xpp
{ 
    COMVariant var = new COMVariant(); 
```

```xpp
    // Set the 'var' object to be a long 
    var.long(123); 
```

```xpp
    // Change var so that it can store a date 
    var.variantType(COMVariantType::VT_DATE); 
}
```

## Method createDateFromYMD

Creates a new COMVariant object and initializes it with a date value in one operation.

```xpp
public static COMVariant createDateFromYMD(int year, int month, int day, [COMVariantInOut inOutFlag])
```

### Parameters - createDateFromYMD

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

### Return Value - createDateFromYMD

The new COMVariant object.

### Remarks - createDateFromYMD

The COMVariant object that is created by this method has the data type VT\_DATE (date/time). This method allows you to use dates that are outside the range for the date data type (0111901 to 31122154). For dates within the date range, you can use the COMVariant.createFromDate method.

### Examples - createDateFromYMD

The following example creates a COMVariant object and initializes it with the date 01 January 4015.

```xpp
COMVariant myDate; 
```

```xpp
myDate = COMVariant::createDateFromYMD(4015,1,1);
```

## Method createFromArray

Creates a new COMVariant object and initializes it with an array in one operation.

```xpp
public static COMVariant createFromArray(Array value, [COMVariantInOut inOutFlag])
```

### Parameters - createFromArray

value  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

<!-- -->

inOutFlag  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

### Return Value - createFromArray

The new COMVariant object.

### Remarks - createFromArray

The COMVariant object that is created by this method has the data type VT\_SAFEARRAY (array). You can change the data type of an existing COMVariant object to VT\_SAFEARRAY by using the variantType method or by passing in an array value by using the safeArray property method.

### Examples - createFromArray

The following example creates a new COMVariant object and initializes it with an array of integers.

```xpp
{ 
    int i; 
    COMVariant var; 
    Array arr = new Array(Types::INTEGER); 
```

```xpp
    for (i = 1; i <= 10; i++) 
        // Insert 10 values in the array 
        arr.value(i, i); 
```

```xpp
    // Create and initialize a COMVariant object  
    var = COMVariant::createFromArray(arr); 
}
```

## Method createFromBoolean

Creates a new COMVariant object and initializes it with a Boolean value in one operation.

```xpp
public static COMVariant createFromBoolean(boolean value, [COMVariantInOut inOutFlag])
```

### Parameters - createFromBoolean

value  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

<!-- -->

inOutFlag  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

### Return Value - createFromBoolean

The new COMVariant object.

### Remarks - createFromBoolean

The COMVariant object that is created by this method has the data type VT\_BOOL (Boolean). You can change the data type of an existing COMVariant object to VT\_BOOL by using the variantType method or by passing in a Boolean value by using the boolean property method.

### Examples - createFromBoolean

The following example creates a COMVariant object of the VT\_BOOL variant data type (Boolean), and sets the value to true.

```xpp
{ 
    COMVariant var; 
```

```xpp
    var = COMVariant::createFromBoolean(TRUE); 
}
```

## Method createFromCOM

Creates a new COMVariant object and initializes it with a COM class in one operation.

```xpp
public static COMVariant createFromCOM(COM value, [COMVariantInOut inOutFlag])
```

### Parameters - createFromCOM

value  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

<!-- -->

inOutFlag  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

### Return Value - createFromCOM

The new COMVariant object.

### Remarks - createFromCOM

Possible values of the inOutFlag parameter are as follows:

-   COMVariantInOut::IN
-   COMVariantInOut::IN\_OUT
-   COMVariantInOut::OUT
-   COMVariantInOut::OUT\_RETVAL

### Examples - createFromCOM

The following example creates a new COMVariant object and initializes it with a COM object.

```xpp
{ 
    COMVariant var; 
    COM com = new COM("MyCOM.Object"); 
```

```xpp
    var = COMVariant::createFromCOM(com); 
}
```

## Method createFromDate

Creates a new COMVariant object and initializes it with a date value in one operation.

```xpp
public static COMVariant createFromDate(Date value, [COMVariantInOut inOutFlag])
```

### Parameters - createFromDate

value  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

<!-- -->

inOutFlag  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

### Return Value - createFromDate

The new COMVariant object.

### Remarks - createFromDate

The COMVariant object that is created by this method has the data type VT\_DATE (date/time). You can change the data type of an existing COMVariant object to VT\_DATE by using the variantType method or by passing in a time value by using the date property method. If you want to use a date that is outside the range for the Axapta date type (0111901 to 31122154), use the COMVariant.createDateFromYMD method.

### Examples - createFromDate

The following example creates a COMVariant object and initializes it with the current date.

```xpp
COMVariant theDay; 
```

```xpp
theDay = COMVariant::createFromDate(today()); 
info(theDay.toString());
```

## Method createFromDateAndTime

Creates a new COMVariant object and initializes it with a date and time in one operation.

```xpp
public static COMVariant createFromDateAndTime(Date date, int time, [COMVariantInOut inOutFlag])
```

### Parameters - createFromDateAndTime

date  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

<!-- -->

time  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

<!-- -->

inOutFlag  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

### Return Value - createFromDateAndTime

The new COMVariant object.

### Remarks - createFromDateAndTime

The COMVariant object that is created by this method has the data type VT\_DATE (date/time). You can change the data type of an existing COMVariant object to VT\_DATE by using the variantType method.

### Examples - createFromDateAndTime

The following example creates a COMVariant object and assigns it the current date, and a time of 10 seconds past midnight.

```xpp
date theDay; 
COMVariant theDayAndTime; 
```

```xpp
theDay = today(); 
theDayAndTime = COMVariant::createFromDateAndTime(theDay, 10); 
info(theDayAndTime.toString());
```

## Method createFromInt

Creates a new COMVariant object and initializes it with an integer value in one operation.

```xpp
public static COMVariant createFromInt(int value, [COMVariantInOut inOutFlag])
```

### Parameters - createFromInt

value  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

<!-- -->

inOutFlag  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

### Return Value - createFromInt

The new COMVariant object.

### Remarks - createFromInt

The COMVariant object that is created by this method has the data type VT\_I4 (integer). You can change the data type of an existing COMVariant object to VT\_I4 by using the variantType method or by passing in an integer value by using the int property method.

### Examples - createFromInt

The following example creates a COMVariant object of the VT\_I4 variant data type (integer), and sets the value to 123.

```xpp
{ 
    COMVariant var; 
```

```xpp
    var = COMVariant::createFromInt(123); 
}
```

## Method createFromInt64

Creates a new COMVariant object and initializes it with an int64 value (longLong or uLongLong) in one operation.

```xpp
public static COMVariant createFromInt64(Int64 value, [COMVariantInOut inOutFlag])
```

### Parameters - createFromInt64

value  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

<!-- -->

inOutFlag  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

### Return Value - createFromInt64

The new COMVariant object.

### Remarks - createFromInt64

The COMVariant object that is created by this method has the data type VT\_I8 (int64). You can change the data type of an existing COMVariant object to VT\_I8 by using the variantType method or by passing in an int64 value by using the longLong or uLongLong property method.

### Examples - createFromInt64

The following example creates a COMVariant object of the VT\_I8 variant data type (integer), and sets the value to 123456.

```xpp
{ 
    COMVariant var; 
```

```xpp
    var = COMVariant::createFromInt64(123456); 
}
```

## Method createFromReal

Creates a new COMVariant object and initializes it with a real value in one operation.

```xpp
public static COMVariant createFromReal(Real value, [COMVariantInOut inOutFlag])
```

### Parameters - createFromReal

value  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

<!-- -->

inOutFlag  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

### Return Value - createFromReal

The new COMVariant object.

### Remarks - createFromReal

The COMVariant object that is created by this method has the data type VT\_R8 (real). You can change the data type of an existing COMVariant object to VT\_R8 by using the variantType method or by passing in a Boolean value by using the double property method.

### Examples - createFromReal

The following example creates a COMVariant object of the VT\_R8 variant data type (real) and sets the value to 123.456.

```xpp
{ 
    COMVariant var; 
```

```xpp
    var = COMVariant::createFromReal(123.456); 
}
```

## Method createFromStr

Creates a new COMVariant object and initializes it with a string in one operation.

```xpp
public static COMVariant createFromStr(str value, [COMVariantInOut inOutFlag])
```

### Parameters - createFromStr

value  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

<!-- -->

inOutFlag  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

### Return Value - createFromStr

The new COMVariant object.

### Remarks - createFromStr

The COMVariant object that is created by this method has the data type VT\_BSTR (string). You can change the data type of an existing COMVariant object to VT\_BSTR by using the variantType method or by passing in a string value by using the bStr property method.

### Examples - createFromStr

The following example creates a COMVariant object of the VT\_BSTR variant data type and sets the value to "Hello World."

```xpp
{ 
    COMVariant var; 
```

```xpp
    var = COMVariant::createFromStr("Hello World"); 
}
```

## Method createFromTime

Creates a new COMVariant object and initializes it with a time value in one operation.

```xpp
public static COMVariant createFromTime(int value, [COMVariantInOut inOutFlag])
```

### Parameters - createFromTime

value  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

<!-- -->

inOutFlag  
A flag that determines whether the object can be used to pass data to a COM method or COM property, to receive data, or both. This parameter is optional. Possible values are:

### Return Value - createFromTime

The new COMVariant object.

### Remarks - createFromTime

The COMVariant object that is created by this method has the data type VT\_DATE (date/time). You can change the data type of an existing COMVariant object to VT\_DATE by using the variantType method or by passing in a time value by using the time property method.

### Examples - createFromTime

The following example will create a COMVariant object and set the time part to 10 seconds past midnight.

```xpp
COMVariant theTime; 
```

```xpp
theTime = COMVariant::createFromTime(10); 
info(theTime.toString());
```

## Method createFromUtcDateTime

```xpp
public static COMVariant createFromUtcDateTime(DateTime value, [COMVariantInOut inOutFlag])
```

### Parameters - createFromUtcDateTime

value  

<!-- -->

inOutFlag  

### Return Value - createFromUtcDateTime

## Method createNoValue

Creates a COMVariant object of the VT\_ERROR variant type with no value.

```xpp
public static COMVariant createNoValue()
```

### Return Value - createNoValue

The new COMVariant object.

### Remarks - createNoValue

A COMVariant object with no value can be used for COM parameters which are optional.

### Examples - createNoValue

The following example creates an empty COMVariant object.

```xpp
COMVariant noValue; 
```

```xpp
noValue = COMVariant::createNoValue(); 
info(noValue.toString());
```

## Method new

Creates a COMVariant object that can be used to pass arguments to the methods or properties of a COM Automation object.

```xpp
public void new([COMVariantInOut inOutFlag], [COMVariantType type])
```

### Parameters - new

inOutFlag  
A type of data to store; optional. These are the possible values that are supplied by the COMVariantType system enum:

<!-- -->

type  
A type of data to store; optional. These are the possible values that are supplied by the COMVariantType system enum:

### Remarks - new

If the type parameter is omitted, no internal memory will be allocated until it is needed by one of the property methods of the COMVariant object. For a list of the property methods, see \[COMVariant Class\]. You can change the variant data type after it has been set by passing in a new value of a different type (by using one of the property methods). The data types that are defined by the COMVariantType enum are equivalent to the variant data types that are defined by the Win32 SDK.

### Examples - new

The following example creates three COMVariant objects:

-   varIn is for passing data to a COM method; it has a string stored in it and then a short (integer).
-   varOut is to receive data of type VT\_I4 (long).
-   varOutRetval can pass in or receive data; its data type can be set by the COMDispFunction.call method.

<!-- -->

```xpp
{ 
    COMVariant varIn  = new COMVariant(); 
    COMVariant varOut = new COMVariant( 
        COMVariantInOut::OUT,  
        COMVariantType::VT_I4); 
    COMVariant varOutRetval = new COMVariant( 
        COMVariantInOut::OUT_RETVAL); ; 
```

```xpp
    // Store a text string in the varIn object 
    varIn.bStr("Hello World"); 
```

```xpp
    // Change varIn to a short. 
    // Text string stored in varIn is automatically released 
    varIn.short(123);  
}
```

## Method noValue

Deletes the contents of an existing COMVariant object and enables it to act as an unspecified argument when it is used in the COMDispFunction.call method or the COM class.

```xpp
public void noValue()
```

### Remarks - noValue

A no-value variant can be used when a COM method has parameters that can be null. It indicates to the COM object that the argument has not been specified and that it must use its own default value. When you are calling methods on a COM object, the unspecified argument can also be specified by using the COMArgument::NoValue enum. Note that this enum cannot be used when calling through the COMDispFunction class.

### Examples - noValue

The following example shows how to call the COM.multiply method with the third argument unspecified. The code below contains a hypothetical COM object ("MyCOM.Object"), and will therefore not run, unless such an object is created outside a Finance and Operations application.

```xpp
{ 
    COM        com; 
    COMVariant varArg1 = new COMVariant(); 
    COMVariant varArg2 = new COMVariant(); 
    COMVariant varArg3 = new COMVariant(); 
    COMVariant varRet  = new COMVariant(COMVariantInOut::OUT_RETVAL); 
    real       ret; 
    InteropPermission perm; 
```

```xpp
    // Set code access permission to help protect use of COM object 
    perm = new InteropPermission(InteropKind::ComInterop); 
    if (perm == null) 
    { 
        return; 
    } 
```

```xpp
    // Permission scope starts here 
    perm.assert(); 
```

```xpp
    com = new COM("MyCOM.Object"); 
```

```xpp
    // Specify arguments for the multiply method 
    varArg1.float(123); 
    varArg2.float(456); 
    varArg3.noValue(); 
    varRet = com.multiply(varArg1, varArg2, varArg3); 
    // �or� 
    varRet = com.multiply(varArg1, varArg2, COMArgument::NoValue); 
     ret = varRet.double(); 
    // ret is now 56088 (123*456) 
```

```xpp
    // Close code access permission 
    CodeAccessPermission::revertAssert(); 
}
```

## Method finalize

Not implemented. You can override this method if you need to explicitly destruct an object.

```xpp
public void finalize()
```

### Remarks - finalize

You must call finalize methods to execute any statements in them; there are no implicit calls to finalize methods.

