---
title: X++ class library
description: This topic describes the library of classes in X++.
author: RobinARH
ms.date: 06/18/2019
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: tfehr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# X++ class library

[!include [banner](../includes/banner.md)]

This topic describes the library of classes in X++. 

There are two kinds of classes: *application classes* and *system classes*.

- **Application classes** – These classes are implemented in X++. They are available in the **Code > Classes** node in Application Explorer.
- **System classes** – These classes are sometimes known as *kernel classes*. They are listed under the **System Documentation > Classes** node in Application Explorer. The source code for these classes isn't available. For a list of the system classes, see [API, class, and table reference](api-reference.md).

## Typical structure of an application class

The following code block types are standard for application classes:

- **class and variable declarations**: The class declaration contains modifiers, such as **public**, **private**, and **extends**. 
- **variable declarations**: These are the field members for objects that are constructed from the class. When you type the keyword **this** on a class instance variable, IntelliSense can show a list of the members.
- **new** method: This method creates an instance of the class. The constructor can be called only by using the **new** keyword. Derived classes can call the **new** method of their constructor by calling the **super** method reference. For more information, see [X++ inheritance](xpp-inheritance.md).
- **finalize** method: This method finalizes an instance of the class. This method is the destructor method. However, it's a destructor by convention only. The system doesn't automatically call the **finalize** method during garbage collection.

Additional methods for a class have the following types:

+ Instance methods
+ Static methods
+ Main methods

Methods can be created on many kinds of items. Here are some examples:

+ Classes
+ Maps
+ Views
+ Data Sets
+ Forms
+ Queries

## Substituting application classes for system classes

You should use the *substitute application classes* instead of the system classes that they extend. 

In Application Explorer, under **System Documentation > Classes**, several kernel or system classes have names that begin with a lowercase *x*. These classes are known as *x-system classes*. Examples of these system classes are **xApplication** and **xVersionControl**. Some of these classes are extended by application classes. For example, the **Application** class extends the **xApplication** system class. 

The classes that derive from x-system classes are known as *substitute application classes*. In Application Explorer, under the **Classes** node, the icon next to the substitute application classes differs from the standard icon.

### x-system classes

Some of the substitute application classes are associated with a special global variable that represents an instance of the class. For example, the **appl** variable references a pre-instantiated object from the **Application** class. The advantage of the **appl** variable is that the system maintains the object throughout the scope of your session. Your code would be less efficient if it repeatedly used the **new Application()** syntax to obtain an instance of the **Application** class. You should not use the **xApplication** system class. Instead, use the **Application** substitute application class. 

You can reference the static members of the **Application** class by using the following standard syntax: **Application::checkForNewBatchJobs()**. However, to reference the instance members of the **Application** class, you should use that class's **appl** variable, if it exists. This pattern applies to most of the x-system classes. The **Session** substitute application class is one exception, because there is no special global variable for **Session**. 

The following table lists the x-system classes that have a corresponding substitute application class. The special global variables are also shown for those classes that have one.

| Application class | x-system class  | Global variable    |
|-------------------|-----------------|--------------------|
| Args              | xArgs           | Not applicable     |
| Application       | xApplication    | **appl**           |
| ClassFactory      | xClassFactory   | **classFactory**   |
| Company           | xCompany        | **appl.company**   |
| Global            | xGlobal         | Not applicable     |
| Info              | xInfo           | **Infolog**        |
| MenuFunction      | xMenuFunction   | Not applicable     |
| Session           | xSession        | Not applicable     |
| VersionControl    | xVersionControl | **versionControl** |

### Example of x-system classes

The following example shows the syntax for using several special variables that reference instances of the substitute application classes.

```xpp
TreeNode treeNode;
Args     args;
FormRun  formRun;

// appl variable
info(appl.buildNo());

// company variable
appl.company().reloadRights();

// infolog variable
treeNode = infolog.findNode("\\forms\\custTable");
info(treeNode.AOTgetProperty("Name"));
// Output is "CustTable".

// classFactory variable
args = new Args(formstr(Batch));
formRun = classFactory.formRunClass(args);
formRun.init();
formRun.run();
formRun.detach();
info("Method is ending. This is a message in the Infolog.");
// Output is "Method is ending. This is a message in the Infolog."
```

## Batch processing classes
You implement classes by using the batch processing system, and by extending the **RunBase** and **RunBaseBatch** classes. To remove the **Recurrence** button from the **Batch processing** dialog box, you use the **Args::parmEnum** method. We recommend that you designate a class to run as a server-bound batch method. Server-bound batch methods are more secure than batch methods that aren't server-bound for the following reasons:

-   The method is run by using the permissions of the user who submitted the method.
-   The method can use only specific **Info** and **Global** class methods to interact with the client that is processing it. This restriction limits interaction with the client.

### Enable a class to run as a server-bound batch method

1.  Create a class that extends the **RunBaseBatch** class.
2.  Override the **RunBaseBatch.runsImpersonated** method to return a value of **true**, as shown in the following example.

    ```xpp
    public boolean runsImpersonated()
    {
        return true;
    }
    ```
    
3.  Confirm that the class calls only the following **Info** and **Global** class methods:
    -   add
    -   Info.copy
    -   Info.cut
    -   Info.import
    -   Info.export
    -   Info.line
    -   Info.num
    -   Global::error
    -   Global::info
    -   Global::warning

    The **Info.line** and **Info.num** methods are inherited from the **xInfo** class.

### Removing the Recurrence button from the batch processing dialog box

When you implement a class by using the batch processing system, you can remove the **Recurrence** button by calling the **Args.parmEnum** method and passing the **NoYes::Yes** system enumeration value. The **NoYes** system enumeration determines whether the **Recurrence** button is removed from the dialog box. The default value is **NoYes::No**. 

In the following example, the **InventTransferMultiShip** class is implemented. The **BatchDialog::main** method creates the **Batch processing** dialog box.

```xpp
static void noRecurrenceButton(Args _args)
{
    Args a;
    InventTransferMultiShip inventTransferMultiShip;
    a = new Args();
    inventTransferMultiShip = InventTransferMultiShip::construct();
    a.caller(inventTransferMultiShip);
    a.parmEnum(NoYes::Yes);
    BatchDialog::main(a);
}
```

## Image manipulation classes
Two system classes let you to manipulate graphics and icons: **Image** and **Imagelist**.

- **Image** – This class lets you load, save, and manipulate individual images. For example, you can capture a screen and save it as an image, crop or rotate an image, or manipulate the color depth.
- <strong>Imagelist</strong> – This class lets you work with a set of images that have common properties, such as the size and transparency color. You can view the image lists that are used in the **ImageListAppl** application classes.

## Query object model
The query object model contains classes that are used to define and run a query. The query objects are used to define the query data source, the fields that are returned, record ranges, and relations to child data sources. The query classes are more visible when you create a dynamic query in code, but they are also used behind the scenes when you create a static query in Application Explorer. 

The following table describes the classes in the query object model.

| System class         | Description      |
|----------------------|------------------|
| QueryRun             | This class runs the query and fetches the data. |
| Query                | This class holds some properties, and has one or more related data sources. It's the top level of the query definition.    |
| QueryBuildDataSource | This class defines access to a single data source in the query. If there is more than one data source at the same level in a query, separate SQL statements are produced and are run sequentially. If one data source is a child of another data source, a join is created between the two data sources. |
| QueryBuildFieldList  | This class defines the fields that are returned from the database. By default, the field list is dynamic, and all fields are returned from the data source table, map, or view. Each data source has only one **QueryBuildFieldList** object. This object contains information about all selected fields. You can specify aggregate functions, such as **SUM**, **COUNT**, and **AVG**, on the field list object. |
| QueryBuildRange      | This class defines a subset of records that is returned, based on a single field. A range is translated into a **WHERE** clause in the query SQL statement. If more than one field is used to limit the query (**WHERE** clause), the data source will contain more than one range. |
| QueryBuildDynalink   | This class contains information about a relation (limitation) to an external record. When the query is run, this information is converted to additional entries in the **WHERE** clause of the query SQL statement. This class can exist only on the parent data source of a query. Forms use the function when two data sources are synchronized. The child data source will then contain one or more DLLs to the parent data source. The function is used even if the two data sources are put in two different forms but are still synchronized. |
| QueryBuildLink       | This class specifies the relation between the two data sources in the join. This class can exist only on a child data source. |

You can also use the [SysDa API](sysda.md) to query data.

## System classes overview
The source for system classes isn't available. A system class can have the following characteristics:

+ Static methods (or class methods)
+ Dynamic methods
+ Properties – These properties are member functions that are used to set properties. An example is **LeftMargin**.

You can't override system class methods. It isn't our intention that you will use the system classes to design your application objects from scratch. Instead, use them to extend or modify the default functionality in Application Explorer. For example, you can dynamically add extra information to an existing report. Alternatively, you can change the options that are available on a page, based on the user's selection on a previous page.

### Collection classes

The *collection classes* let you create lists, sets, structs, maps, and arrays.

### Application object classes

These system classes hold functions that are activated whenever you use Application Explorer to create your application. For example, the system uses the **FormDesign** class when you define the layout of your form in the **Designs** node in Application Explorer. These classes also let you to create and modify application objects.

### Integration classes

The integration with the environment is typically implemented by classes. Here are some examples of the classes in this category:

-   **COM** – The call of methods on COM objects.
-   **DLL** – The call of Microsoft Windows DLL functions.
-   **IO** – Read and write external files.
-   **ODBCConnection** – An Open Database Connectivity (ODBC) interface to a foreign database.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]