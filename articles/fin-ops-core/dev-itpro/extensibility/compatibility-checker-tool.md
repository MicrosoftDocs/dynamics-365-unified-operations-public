---

# required metadata

title: compatibility checker tool
description: The compatibility checker tool finds and reports metadata breaking changes.
author: smithanataraj
manager: AnnBe
ms.date: 03/26/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 89563
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: smnatara
ms.search.validFrom: 2020-03-26
ms.dyn365.ops.version: Platform update 34
---

# compatibility checker tool

[!include [banner](../includes/banner.md)]

The compatibility checker tool can detect metadata breaking changes against a given baseline release or update, helping to ensure backward compatibility. Microsoft has been using the tool to help them ensure metadata compatibility.

The compatibility checker tool is available for use for partners and ISVs from Platform update 34, as one of the dev tools. By using the tool, you can ensure that your solutions are backwards compatible with their earlier releases, before you install or push updates to customers.

## What the tool detects

The tool compares metadata of the current version with a baseline version. It detects and reports metadata breaking changes that have been identified and added to the tool as breaking by Microsoft.

The list of breaking changes detected by the tool is shown in the [List of breaking changes detected by the tool](#list-of-breaking-changes-detected-by-the-tool), though the list is not comprehensive list of all compatibility breaking changes.

## What the tool does not detect

The tool detects only breaking changes that can be identified by comparing data.

For example, these common breaking changes aren't detected by the tool:

+ Removing the reference to a protected or public method.
+ Changing the responsibility of a method.

## How to use the tool

You can use the tool to detect metadata compatibility issues of a new version against the  version that the new version is replacing. At Microsoft, we use the tool to detect breaking changes for a given monthly update against the previous monthly update.

### Usage

```console
CompatibilityChecker.exe -BaselineDirectory=\<Path to baseline metadata\> -CurrentDirectory=\<Path to current metadata\> -ModuleName=\<Module name\> -OutputFile=\<Output file path\> -LogFile=\<Log file path\>
```

### Example

```console
CompatibilityChecker.exe -BaselineDirectory="\\servername\archive\Build1\BaselineMetadata" -CurrentDirectory="E:\\MyCode\\retail\\amd64\\BaselineMetadata" -ModuleName="Directory"
-OutputFile="E:\\Logs\\Directory\\Diagnostics.xml" -LogFile="E:\\Logs\\Directory\\Checkerlog.txt");
```

### Description

The tool identifies breaking changes by comparing current metadata against a given baseline metadata.

You must specify these paths:
+ *BaselineDirectory* specifies the path of the baseline metadata.
+ *CurrentDirectory* specifies the path of the current (new) metadata.
+ *OutputFile* specifies the path to the file with the list of breaking changes.

The following apply:

+ You must compile the current metadata before running the tool.
+ *OutputFile* contains the list of breaking changes identified by the tool.
+ The *BaselineDirectory* must exist with the metadata for the given module and its dependencies (if any).
+ The metadata paths for *BaselineDirectory* and *CurrentDirectory* should have metadata for *StaticMetadata*. It should be present inside a folder named **StaticMetadata** in the given paths.
+ You can suppress any breaking change identified by the tool by adding an entry in the model's ignore list. This file is present in **AxIgnoreDiagnosticList** folder for the model.

## List of breaking changes detected by the tool

> [!NOTE]
> Only metadata compatibility changes that have been defined in the tool as breaking are detected by the tool as breaking changes.

### Class members

+ Changing the access modifier of protected or public class members (including making a member **ReadOnly**) – Consumers might have read from or assigned values to the field.
+ Deleting or renaming public or protected class-level members – Consumers might be using these members in some extension classes.

## Methods

+ Changing the method signature of a protected or public method - Wrappers and callers of the method will be broken.
+ Making a protected or public method obsolete - Consumers might be wrapping or overriding the methods.

## Classes and interfaces

+ Making a class final – Consumers might have created a derived type.
+ Making a class abstract – Consumers might be instantiating the class.
+ Adding an abstract method to a class – Consumers might have created a derived type.
+ Adding a method to an interface – Consumers might have implemented the interface on their own type.
+ Making a public class obsolete and stopping instantiation of the class – Consumers might have overridden, wrapped, or subscribed to the instance methods.

## Delegates

+ Any change in signature – Consumers might have subscribed dynamically.

## Tables

+ Deleting or renaming table fields, field groups, indexes, table mappings, table relations.
+ Modifying these table properties - **Extends**, **SuportInheritance**, **TableType**, **SaveDataPerCompany.Yes**, **SaveDataPerPartition**.
+ Modifying these table field properties - **ExtendedDataType**, **Scale**, String size.
+ Modifying these table index properties - **AllowDuplicates.No**, **IndexType**.

Any of the above changes will break table extensions and tables references to tables and table fields.

## Forms

+ Deletion or renaming form controls, form datasources, and form datasource fields.
+ All method breaking changes are also breaking for form methods.

Any of the above changes will break form extensions that reference the controls or the methods.

## Enums

+ Modifying these properties: **IsExtensible** or **Value**.

## EDTs

+ Modifying these properties: **Extends**, **EnumType**, or **Scale**.

## Entities

+ All breaking changes for tables are all also breaking for entities.
+ Renaming a public entity.

## Label changes

+ Modifying or deleting a label – Consumers might be using the label in the current context of the label text and the parameters that were passed. We recommend that that you add new labels instead of changing existing labels.

## Application element changes

+ Removing any element – Consumers might have a compile time dependency on the existence of the element.
