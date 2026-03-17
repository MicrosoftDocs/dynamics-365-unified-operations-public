---
title: Customization Analysis Report (CAR)
description: Learn about how to generate a Customization Analysis Report for your model and describes some best practice rules that are included in the report.
author: josaw1
ms.author: josaw
ms.topic: article
ms.date: 02/26/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 540b08dd-9af7-42fc-aa0c-ba04af1f8002
---

# Customization Analysis Report (CAR)

[!include [banner](../includes/banner.md)]

This article describes how to generate a Customization Analysis Report for your model. It also describes some best practice rules that the report includes, and provides suggestions for fixing errors and warnings that are associated with these rules.

## What is the Customization Analysis Report?

The Customization Analysis Report is a tool that analyzes your customization and extension models, and runs a predefined set of best practice rules. The report is one of the requirements of the solution certification process. The report is in the form of a Microsoft Excel workbook.

## How to generate the report

The xppbp.exe tool is located in `c:\packages\bin` or `I:\AosService\PackagesLocalDirectory\bin`.
To generate the Customization Analysis Report, run the following command in a development environment.

```Console
xppbp.exe -metadata=<local packages folder> -all -model=<ModelName> -xmlLog=C:\BPCheckLogcd.xml -module=<PackageName> -car=<reportlocation>
```

If your custom model references an ISV model, include the `-PackagesRoot` parameter. For example:

```Console
-packagesroot=K:\AosService\PackagesLocalDirectory
```

### Example

```Console
xppbp.exe -metadata=C:\Packages -all -model="MyAppSuiteCustomizations" -xmlLog=C:\temp\BPCheckLogcd.xml -module="ApplicationSuite" -car=c:\temp\CAReport.xlsx
```

## Issues List

This section describes all best practice rules (errors, warnings, or informational messages) that can appear on the **Issues List** page of the report. It provides suggestions for fixing the issues. The issues are of the **metadata** or **code** type. For all **code** issues, keep in mind that if the warning or error occurs in a method that you overlaid, the lines of code that violate the rule might belong to a model in a lower layer. In that case, you're not responsible for fixing warnings and errors in code that isn't yours.

### BPCheckPackReturnsConnull

| &nbsp; | &nbsp; |
|---------------------|-------------------------------------|
| Description         | This rule applies to all classes that implement the **SysPackable** interface. It makes sure that the **Pack** method doesn't return **Connull()**. |
| Error message       | Container pack method returns connull in a Runbase derived class                |
| Issue type/severity | Code/Warning  |
| How to fix it       | Update the return value of the **Pack** method, or return **Super()** when applicable.                 |

### BPCheckParametersModified

| &nbsp; | &nbsp; |
|---------------------|-------------------------------------|
| Description         | This rule fails if a parameter of a method is modified inside a method.                      |
| Error message       | Parameter 1% in method %1 are modified inside the method                                     |
| Issue type/severity | Code/Warning                                                                                 |
| How to fix it       | Refactor your code. Parameters must be modified by the caller, not within the called method. |

### BPCheckSQLCode

| &nbsp; | &nbsp; |
|---------------------|-------------------------------------|
| Description         | This rule fails if your X++ code contains direct SQL code.       |
| Error message       | SQL code found in method %1                                      |
| Issue type/severity | Code/Warning                                                     |
| How to fix it       | Refactor your code to use X++ to access the database. |

### BPCheckNestedLoopInCode

| &nbsp; | &nbsp; |
|---------------------|-------------------------------------|
| Description         | This rule fails if it finds a **while select** loop nested within a loop.    |
| Error message       | Nested data access loop found in %1 method                                                |
| Issue type/severity | Code/Warning                   |
| How to fix it       | Refactor your code to use joins instead of nested data access loops. If you can't refactor the code without altering the business logic of your method, document an exception when you submit your Customization Analysis Report to Microsoft. |

### BPCheckInsertMethodInLoop

| &nbsp; | &nbsp; |
|---------------------|-------------------------------------|
| Description         | This rule fails if it finds a call to the method **insert** nested inside a loop. Use **InsertRecordList** instead. This rule doesn't apply to InMemory tables. |
| Error message       | Insert method can be replaced with RecordInsertList in method %1                       |
| Issue type/severity | Code/Warning           |
| How to fix it       | Refactor your code to use set-based operations, such as **InsertRecordList**.            |

### BPCheckSelectwithJoin

| &nbsp; | &nbsp; |
|---------------------|-------------------------------------|
| Description         | This rule fails if it finds nested **select** statements that aren't joined.  |
| Error message       | Nested select statement in %1 method can be joined                                |
| Issue type/severity | Code/Warning                                                                          |
| How to fix it       | Refactor your code to use joins instead of a nested **select** statement. If you can't refactor the code without altering the business logic of your method, document an exception when you submit your Customization Analysis Report to Microsoft. |

### BPFunctionCallwithSelect

| &nbsp; | &nbsp; |
|---------------------|-------------------------------------|
| Description         | This rule fails if a function call is found within a **select** statement.   |
| Error message       | Function call found in select statement in method %1     |
| Issue type/severity | Code/Warning    |
| How to fix it       | Assign the function's return value to a local variable before you call the **select** statement, and use the local variable in the **select** statement. |

### BPCheckinvalidExecuteQuery

| &nbsp; | &nbsp; |
|---------------------|-------------------------------------|
| Description         | This rule fails if a call to **addRange** is found after a call to **super()** in the **ExecuteQuery** method. |
| Error message       | Add range after super() shouldn't be added in ExecuteQuery method for form %1               |
| Issue type/severity | Code/Warning                                          |
| How to fix it       | Refactor your code to avoid this pattern.             |

### BPCheckInvalidInitFormMethod

| &nbsp; | &nbsp; |
|---------------------|-------------------------------------|
| Description         | This rule makes sure that you don't initialize form controls and data sources in a form's **init** method before you call **super()**. It fails if it finds a statement that uses **element** or **this** before the call to **super()** (**this.aMethod()** or **element.aMethod()**). An informational message is shown only for some allowed patterns, such as initializing number sequences (**numberSeqPreInit**). |
| Error message       | Form element statements shouldn't be used before super() in init method of form %1      |
| Issue type/severity | Code/Info or Warning                                   |
| How to fix it       | Refactor your code to access form controls and data after the call to **super()**. If your code doesn't initialize any form control and doesn't access any form data sources before **super()**, document an exception when you submit your Customization Analysis Report to Microsoft.   |

### BPCheckEmptyLoop

| &nbsp; | &nbsp; |
|---------------------|-------------------------------------|
| Description         | This rule fails if it finds loops that have no statements. |
| Error message       | Empty loop found in method %1 in class %2                  |
| Issue type/severity | Code/Warning                                               |
| How to fix it       | Remove the loop from your code.                            |

### BPCheckLockQueryRange

| &nbsp; | &nbsp; |
|---------------------|-------------------------------------|
| Description         | This rule fails if the code calls **AddRange** in the **init** method of the form, and doesn't set the range as locked or hidden.      |
| Error message       | Range should be locked or hidden in form %1    |
| Issue type/severity | Code/Warning     |
| How to fix it       | Add **QueryBuildRange.status(RangeStatus::Locked)** or **QueryBuildRange.status(RangeStatus::Hidden)** after the call to **AddRange**. |

### BPCheckSkipStatementValidation

| &nbsp; | &nbsp; |
|---------------------|-------------------------------------|
| Description | This rule reports an informational message if it finds a set-based operation that doesn't have **Skip** statements. When **update_recordset** is found, the rule checks for **skipDataMethods(true)**. The rule applies only when the **update** method on the table is overridden. When **insert_recordset** is found, the rule checks for **skipDataMethods(true)**. The rule applies only when the **insert** method on the table is overridden. When **delete_from** is found, the rule checks for **skipDeleteActions(true)**. The rule applies only when the **insert** method on the table is overridden. This is an informational message that highlights the need to call **skip** methods to take full advantage of the performance gains of set-based operations. If **skip** methods aren't used, the execution falls back to a row-by-row operation. |
| Error message | Set-based operation must invoke Skip statements in method %1 in class %2; otherwise, execution falls back to a row by row operation. |
| Issue type/severity | Code/Information |
| How to fix it | Use **skipDataMethods(true)** or **skipDeleteActions(true)** when applicable. |

### BPCheckNoTTSTryBlock

| &nbsp; | &nbsp; |
|---|---|
| Description | This rule fails if it finds a **try** statement within a **tts** block that isn't handled correctly. |
| Error message | Tts block with Try statement does not explicitly catch exceptions in method %1 |
| Issue type/severity | Code/Warning |
| How to fix it | Use the code example that follows this table. |

The following examples show when the rule fails or passes. Use these examples as guidelines to refactor your code.

```xpp
ttsbegin;
try {
}
// fail
catch {
}
try {
}
// pass
catch(Exception::UpdateConflict) {
}
try {
}
// pass
catch(Exception::UpdateConflictNotRecovered) {}
```

### BPCheckEmptyTableMethod

| &nbsp; | &nbsp; |
|---------------------|-------------------------------------|
| Description         | This rule checks for table methods that have no source code. Empty table methods cause record-set operations on the table to fall back to a row-by-row operation. |
| Error message       | %1 table has an empty %2 method           |
| Issue type/severity | Code/Warning                              |
| How to fix it       | Remove this method from your code.        |

### BPCheckBatchJobsEnabled

| &nbsp; | &nbsp; |
|---------------------|-------------------------------------|
| Description         | This rule makes sure that all classes that extend **RunBaseBatch** have a **canGoBatch** method that returns **true**. |
| Error message       | Custom job is not batch-enabled in class %1         |
| Issue type/severity | Code/Warning       |
| How to fix it       | The **canGoBatch** method must return **true** for all batch classes.     |

### BPCheckDisplayMethodCached

| &nbsp; | &nbsp; |
|---------------------|-------------------------------------|
| Description | For each control that binds to a data method, this rule fails if one of these conditions is met: The **Cache Data Method** property is set to **Auto**, the corresponding table **display**/**edit** method doesn't have the **SysClientCacheDataMethodAttribute**, and the **init** method of the data source doesn't use **CacheAddMethod**. The **Cache Data Method** property is set to **No**, and the **init** method of the data source doesn't use **CacheAddMethod**. |
| Error message | Display method %1 in form %2 not cached |
| Issue type/severity | Code/Warning |
| How to fix it | Use the note that follows this table. |

You can fix this warning by using one of the following patterns:

+ Set the **Cache Data Method** property to **Yes**.
+ Set the **Cache Data Method** property to **Auto**, and mark the data method of the table with the **SysClientCacheDataMethodAttribute** attribute. Here's an example.

    ```xp
    [SysClientCacheDataMethodAttribute(true)]
    Display TransDate myDateMethod()
    {
        //...
    }
    ```

+ Use **CacheAddMethod** in the **init** method of the form to mark the method as cached.

### BPCheckSQLQueryInInit

| &nbsp; | &nbsp; |
|---------------------|-------------------------------------|
| Description         | This rule fails if a data access query that has a **while** loop is found in the **init** method of a form. This pattern could cause performance issues when the form is initialized. |
| Error message       | SQL query with while loop was found in init method of form %1            |
| Issue type/severity | Code/Warning   |
| How to fix it       | Refactor your code to avoid this pattern.  |

### BPCheckNewQueryWithForm

| &nbsp; | &nbsp; |
|---------------------|-------------------------------------|
| Description         | This rule fails if it finds the **new Query()** statement in the **init** or **executeQuery** method of a form. |
| Error message       | Data source query overridden in form method %1      |
| Issue type/severity | Code/Warning                                |
| How to fix it       | Refactor your code to avoid this pattern.            |

### BPCheckSelectForUpdateAbsent

| &nbsp; | &nbsp; |
|---------------------|-------------------------------------|
| Description         | This rule fails if **Select ForUpdate** is used to select records, but an update isn't being performed. This rule doesn't apply to tables that are enabled for Optimistic Concurrency Control (OCC). |
| Error message       | Select ForUpdate not implemented in method %1   |
| Issue type/severity | Code/Warning      |
| How to fix it       | Use **Select** instead of **Select ForUpdate**, or set the **OCC Enabled** property to **Yes** on the table.                                                                                          |

### BPCheckTablePropertyMismatch

| &nbsp; | &nbsp; |
|---------------------|-------------------------------------|
| Description | This rule fails when the table belongs to a table group but doesn't have the appropriate **Cache Lookup** value. The rule fails if one of these conditions is met: The **Table Group** property is set to **Main**, and the **Cache Lookup** property is set to **NotinTTS** or **EntireTable**. The **Table Group** property is set to **Group** or **Parameter**, and the **Cache Lookup** property is set to **NotinTTS**. The **Table Group** property is set to **WorksheetHeader**, **WorksheetLine**, or **Transaction**, and the **Cache Lookup** property is set to **Found**, **FoundAndEmpty**, or **EntireTable**. |
| Error message | %1 table has an invalid combination of table group and cache lookup |
| Issue type/severity | MetaData/Warning |
| How to fix it | Set an appropriate **Cache Lookup** value on the table. |

### BPCheckMissingDeleteActions

| &nbsp; | &nbsp; |
|---------------------|-------------------------------------|
| Description         | This rule checks that the value of either a **delete** action or the **On Delete** property of a table relation isn't set to **None**. The rule doesn't trigger when the related or current table is a tempDB, in-memory table, reference table, staging table, or parameter table. |
| Error message       | Delete actions missing in table %1 which is related to table %2 with relation name %3      |
| Issue type/severity | MetaData/Warning   |
| How to fix it       | Set a **delete** action value that isn't **None**. |

### BPCheckAddressModel

| &nbsp; | &nbsp; |
|---------------------|-------------------------------------|
| Description         | This rule fails if a table field is of the **AddressZipCodeId** or **AddressStateId** types. These types indicate that the code doesn't use the newer Address framework. |
| Error message       | Field %1 of table %2 is not part of address location model   |
| Issue type/severity | MetaData/Warning  |
| How to fix it       | Replace these types with any other appropriate EDT type in the Directory model.        |

### BPCheckDimensionModel

| &nbsp; | &nbsp; |
|---------------------|-------------------------------------|
| Description         | This rule fails if a table field is of the **Dimension** or **LedgerAccount** types. These types indicate that the code doesn't use the newer Financial Dimension framework. |
| Error message       | Field %1 of table %2 is not part of financial dimension framework               |
| Issue type/severity | MetaData/Warning   |
| How to fix it       | Replace these types with any other appropriate EDT type in the Dimensions model.       |

### BPCheckNumberofNewFields

| &nbsp; | &nbsp; |
|---------------------|-------------------------------------|
| Description         | This rule verifies that more than 10 fields aren't added to a table during the process of customizing or extending that table. This rule doesn't apply to staging tables. |
| Error message       | Number of new fields in table %1 is greater than      |
| Issue type/severity | Metadata/Warning   |
| How to fix it       | Refactor your schema and create related tables instead of adding too many fields to an existing table. |

### BPCheckEnumUpgradeIssue

| &nbsp; | &nbsp; |
|---------------------|-------------------------------------|
| Description         | This rule fails when the following condition is met: When you customize an enum (overlayer), new enum values are less than the maximum existing value + 10. This rule doesn't apply to extensible enums. |
| Error message       | Enum %1 will have upgrade issues    |
| Issue type/severity | MetaData/Warning       |
| How to fix it       | Use larger enum values, or extend the enum.       |

### BPCheckPassiveJoinUse

| &nbsp; | &nbsp; |
|---------------------|-------------------------------------|
| Description | This rule validates that, when a form preloads data, the link type of tab page data sources is passive. The rule fails if all the following conditions are met: A form has the **AllowPreLoading** property set to **Yes**. A tab page on the form is bound to a top-level data source. The data source's **Join Source** property is set. The data source's **Link Type** property isn't set to **Passive**. |
| Error message | New message suggest: "Use passive joins on data sources %1 bound to a tab page control in form %2" |
| Issue type/severity | MetaData/Warning |
| How to fix it | Set the **AllowPreLoading** property to **No** on the form, or use passive joins on the data source. Passive joins require that you explicitly program when the query of a tab page is run. |

### BPCheckAlternateKeyAbsent

| &nbsp; | &nbsp; |
|---------------------|-------------------------------------|
| Description         | This rule verifies that tables that have a unique index have at least one alternate key. |
| Error message       | Table %1 doesn't have an alternate key                                                  |
| Issue type/severity | MetaData/Warning                                                                         |
| How to fix it       | Set the **Alternate Key** property to **Yes** on a unique index of the table.            |

### BPCheckBaseTableModified

| &nbsp; | &nbsp; |
|---------------------|-------------------------------------|
| Description         | This rule discourages the customization (overlayering) of a list of specific base tables that are shipped by Microsoft. Examples are the SourceDocumentHeader and SourceDocumentLine tables. |
| Error message       | %1 is a base table and must not be modified   |
| Issue type/severity | MetaData/Warning     |
| How to fix it       | Don't customize the table.    |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
