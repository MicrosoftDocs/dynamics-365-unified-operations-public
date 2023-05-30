---
title: Customization Analysis Report (CAR)
description: This article describes how to generate a Customization Analysis Report for your model and describes some best practice rules that are included in the report.
author: gianugo
ms.date: 06/20/2017
ms.topic: article
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: gianura
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 540b08dd-9af7-42fc-aa0c-ba04af1f8002
---

# Customization Analysis Report (CAR)

[!include [banner](../includes/banner.md)]

This article describes how to generate a Customization Analysis Report for your model. It also describes some best practice rules that are included in the report, and provides suggestions for fixing errors and warnings that are associated with these rules. 

## What is the Customization Analysis Report?

The Customization Analysis Report is a tool that analyzes your customization and extension models, and runs a predefined set of best practice rules. The report is one of the requirements of the solution certification process. The report is in the form of a Microsoft Excel workbook.

## How to generate the report
The xppbp.exe tool is located in c:\\packages\\bin or I:\\AosService\\PackagesLocalDirectory\\bin.
To generate the Customization Analysis Report, run the following command in a development environment.

```Console
xppbp.exe -metadata=<local packages folder> -all -model=<ModelName> -xmlLog=C:\BPCheckLogcd.xml -module=<PackageName> -car=<reportlocation>
```

If your custom model references an ISV model, then you must include the `-PackagesRoot` parameter, for example:

```Console
-packagesroot=K:\AosService\PackagesLocalDirectory
```

### Example

```Console
xppbp.exe -metadata=C:\Packages -all -model="MyAppSuiteCustomizations" -xmlLog=C:\temp\BPCheckLogcd.xml -module="ApplicationSuite" -car=c:\temp\CAReport.xlsx
```


## Issues List
This section describes all best practice rules (errors, warnings, or informational messages) that can appear on the **Issues List** page of the report and provides suggestions for fixing the issues. Issues are of the **metadata** or **code** type. For all **code** issues, keep in mind that, if the warning or error occurs in a method that you've overlaid, the lines of code that violate the rule might belong to a model in a lower layer. In that case, you're not responsible for fixing warnings and errors in code that isn't yours.

### BPCheckPackReturnsConnull

| Description         | This rule applies to all classes that implement the **SysPackable** interface. It makes sure that the **Pack** method doesn't return **Connull()**. |
|---------------------|-------------------------------------|
| Error message       | Container pack method returns connull in a Runbase derived class                |
| Issue type/severity | Code/Warning  |
| How to fix it       | Update the return value of the **Pack** method, or return **Super()** when applicable.                 |

### BPCheckParametersModified

| Description         | This rule fails if a parameter of a method is modified inside a method.                      |
|---------------------|----------------------------------------------------------------------------------------------|
| Error message       | Parameter 1% in method %1 are modified inside the method                                     |
| Issue type/severity | Code/Warning                                                                                 |
| How to fix it       | Refactor your code. Parameters must be modified by the caller, not within the called method. |

### BPCheckSQLCode

| Description         | This rule fails if your X++ code contains direct SQL code.       |
|---------------------|------------------------------------------------------------------|
| Error message       | SQL code found in method %1                                      |
| Issue type/severity | Code/Warning                                                     |
| How to fix it       | Refactor your code to use X++ to access the database. |

### BPCheckNestedLoopInCode

| Description         | This rule fails if it finds a **while select** loop nested within a loop.    |
|---------------------|----------------------------------------------------------------------------|
| Error message       | Nested data access loop found in %1 method                                                |
| Issue type/severity | Code/Warning                   |
| How to fix it       | Refactor your code to use joins instead of nested data access loops. If you can't refactor the code without altering the business logic of your method, document an exception when you submit your Customization Analysis Report to Microsoft. |

### BPCheckInsertMethodInLoop

| Description         | This rules fails if it finds a call to the method **insert** nested inside a loop. We recommend that you use **InsertRecordList**. This rule doesn't apply to InMemory tables. |
|---------------------|-------------------------------|
| Error message       | Insert method can be replaced with RecordInsertList in method %1                       |
| Issue type/severity | Code/Warning           |
| How to fix it       | Refactor your code to use set-based operations, such as **InsertRecordList**.            |

### BPCheckSelectwithJoin

| Description         | This rule fails if it finds nested **select** statements that aren't joined.  |
|---------------------|------------------------------------------------------------------------|
| Error message       | Nested select statement in %1 method can be joined                                |
| Issue type/severity | Code/Warning                                                                          |
| How to fix it       | Refactor your code to use joins instead of a nested **select** statement. If you can't refactor the code without altering the business logic of your method, document an exception when you submit your Customization Analysis Report to Microsoft. |

### BPFunctionCallwithSelect

| Description         | This rule fails if a function call is found within a **select** statement.   |
|---------------------|------------------|
| Error message       | Function call found in select statement in method %1     |
| Issue type/severity | Code/Warning    |
| How to fix it       | Assign the function's return value to a local variable before you call the **select** statement, and use the local variable in the **select** statement. |

### BPCheckinvalidExecuteQuery

| Description         | This rule fails if a call to **addRange** is found after a call to **super()** in the **ExecuteQuery** method. |
|---------------------|-------------------------------------------------------|
| Error message       | Add range after super() should not be added in ExecuteQuery method for form %1               |
| Issue type/severity | Code/Warning                                          |
| How to fix it       | Refactor your code to avoid this pattern.             |

### BPCheckInvalidInitFormMethod

| Description         | This rule makes sure that you don't initialize form controls and data sources in a form's **init** method before you call **super()**. It fails if it finds a statement that uses **element** or **this** before the call to **super()** (**this.aMethod()** or **element.aMethod()**). An informational message is shown only for some allowed patterns, such as initializing number sequences (**numberSeqPreInit**). |
|---------------------|---------------------------------------------------------------------------------------------------------|
| Error message       | Form element statements should not be used before super() in init method of form %1      |
| Issue type/severity | Code/Info or Warning                                   |
| How to fix it       | Refactor your code to access form controls and data after the call to **super()**. If your code doesn't initialize any form control and doesn't access any form data sources before **super()**, document an exception when you submit your Customization Analysis Report to Microsoft.   |

### BPCheckEmptyLoop

| Description         | This rule fails if it finds loops that have no statements. |
|---------------------|------------------------------------------------------------|
| Error message       | Empty loop found in method %1 in class %2                  |
| Issue type/severity | Code/Warning                                               |
| How to fix it       | Remove the loop from your code.                            |

### BPCheckLockQueryRange

| Description         | This rule fails if the code calls **AddRange** in the **init** method of the form, and doesn't set the range as locked or hidden.      |
|---------------------|-------------------------------------------|
| Error message       | Range should be locked or hidden in form %1    |
| Issue type/severity | Code/Warning     |
| How to fix it       | Add **QueryBuildRange.status(RangeStatus::Locked)** or **QueryBuildRange.status(RangeStatus::Hidden)** after the call to **AddRange**. |

### BPCheckSkipStatementValidation

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Description</td>
<td>This rule reports an informational message if it finds a set-based operation that doesn&#39;t have <strong>Skip</strong> statements.
<ul>
<li>When <strong>update_recordset</strong> is found, the rule checks for <strong>skipDataMethods(true)</strong>. The rule applies only when the <strong>update</strong> method on the table is overridden.</li>
<li>When <strong>insert_recordset</strong> is found, the rule checks for <strong>skipDataMethods(true)</strong>. The rule applies only when the <strong>insert</strong> method on the table is overridden.</li>
<li>When <strong>delete_from</strong> is found, the rule checks for <strong>skipDeleteActions(true)</strong>. The rule applies only when the <strong>insert</strong> method on the table is overridden.</li>
</ul>
This is an informational message that highlights the need to call <strong>skip</strong> methods to take full advantage of the performance gains of set-based operations. If <strong>skip</strong> methods are not used, the execution falls back to a row-by-row operation.</td>
</tr>
<tr class="even">
<td>Error message</td>
<td>Set-based operation must invoke Skip statements in method %1 in class %2; otherwise, execution will fall back to a row by row operation.</td>
</tr>
<tr class="odd">
<td>Issue type/severity</td>
<td>Code/Information</td>
</tr>
<tr class="even">
<td>How to fix it</td>
<td>Use <strong>skipDataMethods(true)</strong> or <strong>skipDeleteActions(true)</strong> when applicable.</td>
</tr>
</tbody>
</table>

### BPCheckNoTTSTryBlock

| Description | This rule fails if it finds a <strong>try</strong> statement within a <strong>tts</strong> block that isn&#39;t handled correctly. |
|---|---|
| Error message | Tts block with Try statement does not explicitly catch exceptions in method %1 |
| Issue type/severity | Code/Warning |
| How to fix it | Use the code example that follows this table. |

The following examples show when the rule will fail or pass. Use these examples as guidelines to refactor your code.

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

| Description         | This rule checks for table methods that have no source code. Empty table methods cause record-set operations on the table to fall back to a row-by-row operation. |
|---------------------|-------------------------------------------|
| Error message       | %1 table has an empty %2 method           |
| Issue type/severity | Code/Warning                              |
| How to fix it       | Remove this method from your code.        |

### BPCheckBatchJobsEnabled

| Description         | This rule makes sure that all classes that extend **RunBaseBatch** have a **canGoBatch** method that returns **true**. |
|---------------------|----------------------------------------------------------------|
| Error message       | Custom job is not batch-enabled in class %1         |
| Issue type/severity | Code/Warning       |
| How to fix it       | The **canGoBatch** method must return **true** for all batch classes.     |

### BPCheckDisplayMethodCached

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Description</td>
<td>For each control that is bound to a data method, this rules fails if one of these conditions is met:
<ul>
<li>The <strong>Cache Data Method</strong> property is set to <strong>Auto</strong>, the corresponding table <strong>display</strong>/<strong>edit</strong> method doesn&#39;t have the <strong>SysClientCacheDataMethodAttribute</strong>, and the <strong>init</strong> method of the data source doesn&#39;t use <strong>CacheAddMethod</strong>.</li>
<li>The <strong>Cache Data Method</strong> property is set to <strong>No</strong>, and the <strong>init</strong> method of the data source doesn&#39;t use <strong>CacheAddMethod</strong>.</li>
</ul></td>
</tr>
<tr class="even">
<td>Error message</td>
<td>Display method %1 in form %2 not cached</td>
</tr>
<tr class="odd">
<td>Issue type/severity</td>
<td>Code/Warning</td>
</tr>
<tr class="even">
<td>How to fix it</td>
<td>Use the note that follows this table.</td>
</tr>
</tbody>
</table>

You can fix this warning by using one of the following patterns:

+ Set the **Cache Data Method** property to **Yes**.
+ Set the **Cache Data Method** property to **Auto**, and mark the data method of the table with the **SysClientCacheDataMethodAttribute** attribute. Here is an example.

    ```xp
    [SysClientCacheDataMethodAttribute(true)]
    Display TransDate myDateMethod()
    {
        //...
    }
    ```

+ Use **CacheAddMethod** in the **init** method of the form to mark the method as cached.

### BPCheckSQLQueryInInit

| Description         | This rule fails if a data access query that has a **while** loop is found in the **init** method of a form. This pattern could cause performance issues when the form is initialized. |
|---------------------|--------------------------------------|
| Error message       | SQL query with while loop was found in init method of form %1            |
| Issue type/severity | Code/Warning   |
| How to fix it       | Refactor your code to avoid this pattern.  |

### BPCheckNewQueryWithForm

| Description         | This rule fails if it finds the **new Query()** statement in the **init** or **executeQuery** method of a form. |
|---------------------|--------------------------------------------------|
| Error message       | Data source query overridden in form method %1      |
| Issue type/severity | Code/Warning                                |
| How to fix it       | Refactor your code to avoid this pattern.            |

### BPCheckSelectForUpdateAbsent

| Description         | This rule fails if **Select ForUpdate** is used to select records, but an update isn't being performed. This rules doesn't apply to tables that are enabled for Optimistic Concurrency Control (OCC). |
|---------------------|------------------|
| Error message       | Select ForUpdate not implemented in method %1   |
| Issue type/severity | Code/Warning      |
| How to fix it       | Use **Select** instead of **Select ForUpdate**, or set the **OCC Enabled** property to **Yes** on the table.                                                                                          |

### BPCheckTablePropertyMismatch

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Description</td>
<td>This rule fails when the table belongs to a table group but doesn&#39;t have the appropriate <strong>Cache Lookup</strong> value. The rule fails if one of these conditions is met:
<ul>
<li>The <strong>Table Group</strong> property is set to <strong>Main</strong>, and the <strong>Cache Lookup</strong> property is set to <strong>NotinTTS</strong> or <strong>EntireTable</strong>.</li>
<li>The <strong>Table Group</strong> property is set to <strong>Group</strong> or <strong>Parameter</strong>, and the <strong>Cache Lookup</strong> property is set to <strong>NotinTTS</strong>.</li>
<li>The <strong>Table Group</strong> property is set to <strong>WorksheetHeader</strong>, <strong>WorksheetLine</strong>, or <strong>Transaction</strong>, and the <strong>Cache Lookup</strong> property is set to <strong>Found</strong>, <strong>FoundAndEmpty</strong>, or <strong>EntireTable</strong>.</li>
</ul></td>
</tr>
<tr class="even">
<td>Error message</td>
<td>%1 table has an invalid combination of table group and cache lookup</td>
</tr>
<tr class="odd">
<td>Issue type/severity</td>
<td>MetaData/Warning</td>
</tr>
<tr class="even">
<td>How to fix it</td>
<td>Set an appropriate <strong>Cache Lookup</strong> value on the table.</td>
</tr>
</tbody>
</table>

### BPCheckMissingDeleteActions

| Description         | This rule validates that the value of either a **delete** action or the **On Delete** property of a table relation isn't equal to **None**. The rule isn't triggered when the related or current table is a tempDB, in memory table, reference table, staging table, or parameter table. |
|---------------------|---------------------------------------------------|
| Error message       | Delete actions missing in table %1 which is related to table %2 with relation name %3      |
| Issue type/severity | MetaData/Warning   |
| How to fix it       | Set a **delete** action value that isn't equal to **None**. |

### BPCheckAddressModel

| Description         | This rule fails if a table field is of the **AddressZipCodeId** or **AddressStateId** type. These types indicate that the code didn't uptake the newer Address framework. |
|---------------------|-------------------------|
| Error message       | Field %1 of table %2 is not part of address location model   |
| Issue type/severity | MetaData/Warning  |
| How to fix it       | Replace these types with any other appropriate EDT type in the Directory model.        |

### BPCheckDimensionModel

| Description         | This rule fails if a table field is of the **Dimension** or **LedgerAccount** type. These types indicate that the code didn't uptake the newer Financial Dimension framework. |
|---------------------|----------|
| Error message       | Field %1 of table %2 is not part of financial dimension framework               |
| Issue type/severity | MetaData/Warning   |
| How to fix it       | Replace these types with any other appropriate EDT type in the Dimensions model.       |

### BPCheckNumberofNewFields

| Description         | This rule verifies that no more than 10 fields were added to a table during the process of customizing or extending that table. This rule doesn't apply to staging tables. |
|---------------------|-------------------------------------|
| Error message       | Number of new fields in table %1 is greater than      |
| Issue type/severity | Metadata/Warning   |
| How to fix it       | Refactor your schema and create related tables instead of adding too many fields to an existing table. |

### BPCheckEnumUpgradeIssue

| Description         | This rule fails when the following condition is met: When you customize an enum (overlayer), new enum values are less than the maximum existing value + 10. This rules doesn't apply to extensible enums. |
|---------------------|--------------------------------------|
| Error message       | Enum %1 will have upgrade issues    |
| Issue type/severity | MetaData/Warning       |
| How to fix it       | Use larger enum values, or extend the enum.       |

### BPCheckPassiveJoinUse

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Description</td>
<td>This rule validates that, when a form allows for pre-loading of data, the link type of tab page data sources is passive. The rule fails if all the following conditions are met:
<ul>
<li>A form has the <strong>AllowPreLoading</strong> property set to <strong>Yes</strong>.</li>
<li>A tab page on the form is bound to a top-level data source.</li>
<li>The data source's <strong>Join Source </strong>property is set.</li>
<li>The data source's <strong>Link Type</strong> property isn&#39;t set to <strong>Passive</strong>.</li>
</ul></td>
</tr>
<tr class="even">
<td>Error message</td>
<td>New message suggest: "Use passive joins on data sources %1 bound to a tab page control in form %2"</td>
</tr>
<tr class="odd">
<td>Issue type/severity</td>
<td>MetaData/Warning</td>
</tr>
<tr class="even">
<td>How to fix it</td>
<td>Set the <strong>AllowPreLoading</strong> property to <strong>No</strong> on the form, or use passive joins on the data source. Passive joins require that you explicitly program when the query of a tab page is run.</td>
</tr>
</tbody>
</table>

### BPCheckAlternateKeyAbsent

| Description         | This rule verifies that tables that have a unique index have at least one alternate key. |
|---------------------|------------------------------------------------------------------------------------------|
| Error message       | Table %1 does not have an alternate key                                                  |
| Issue type/severity | MetaData/Warning                                                                         |
| How to fix it       | Set the **Alternate Key** property to **Yes** on a unique index of the table.            |

### BPCheckBaseTableModified

| Description         | This rule discourages the customization (overlayering) of a list of specific base tables that are shipped by Microsoft. Examples are the SourceDocumentHeader and SourceDocumentLine tables. |
|---------------------|----------------------------|
| Error message       | %1 is a base table and must not be modified   |
| Issue type/severity | MetaData/Warning     |
| How to fix it       | Don't customize the table.    |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
