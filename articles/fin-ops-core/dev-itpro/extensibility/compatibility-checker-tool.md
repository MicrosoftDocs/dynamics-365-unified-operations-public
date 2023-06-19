---
title: Compatibility checker tool
description: This article provides information about the compatibility checker tool, which finds and reports metadata breaking changes.
author: smithanataraj
ms.date: 03/26/2020
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: smnatara
ms.search.validFrom: 2020-03-26
ms.dyn365.ops.version: Platform update 34
ms.assetid: 
---

# Compatibility checker tool

[!include [banner](../includes/banner.md)]

The compatibility checker tool can detect metadata breaking changes against a specified baseline release or update. In this way, it helps ensure backward compatibility. Microsoft uses the tool to help ensure metadata compatibility.

The compatibility checker tool is available as one of the dev tools in Platform update 34. You can use it to ensure that your solutions are backward-compatible with earlier releases before you install or push updates to customers.

## What the tool detects

The tool compares metadata of the current version with metadata of a baseline version. It detects and reports metadata changes that Microsoft has identified as breaking and added to the tool.

For a list of breaking changes that the tool detects, see the [List of breaking changes detected by the tool](#list-of-breaking-changes-detected-by-the-tool) section later in this article.

> [!NOTE]
> + The list in this article doesn't include all the breaking changes that the tool can detect.
> + The tool doesn't detect all breaking changes.

## What the tool doesn't detect

The tool detects only breaking changes that can be identified by comparing data. For example, it doesn't detect the following breaking changes that often occur:

+ The reference to a protected or public method is removed.
+ The responsibility of a method is changed.

## Using the tool

You can use the tool to detect metadata compatibility issues that a new version has against the version that it's replacing. Microsoft uses the tool to detect any breaking changes that a new monthly update has against the previous monthly update.

### Usage

```console
CompatibilityChecker.exe -BaselineDirectory=\<Path to baseline metadata\> -CurrentDirectory=\<Path to current metadata\> -ModuleName=\<Module name\> -OutputFile=\<Output file path\> -LogFile=\<Log file path\>
```

### Example

```console
CompatibilityChecker.exe -BaselineDirectory="\\servername\archive\Build1\BaselineMetadata" -CurrentDirectory="E:\\MyCode\\retail\\amd64\\BaselineMetadata" -ModuleName="Directory"
-OutputFile="E:\\Logs\\Directory\\Diagnostics.xml" -LogFile="E:\\Logs\\Directory\\Checkerlog.txt"
```

### Description

The tool identifies breaking changes by comparing the current metadata with specified baseline metadata.

You must specify the following paths:

+ **BaselineDirectory** – The path of the baseline metadata.
+ **CurrentDirectory** – The path of the current (new) metadata.
+ **OutputFile** – The path of the file that contains the list of breaking changes.

The following rules apply:

+ You must compile the current metadata before you run the tool.
+ The *OutputFile* file contains the list of breaking changes that the tool identifies.
+ The *BaselineDirectory* directory must exist and must have the metadata for the specified module and its dependencies (if the module has any dependencies).
+ The metadata paths for *BaselineDirectory* and *CurrentDirectory* should have metadata for *StaticMetadata*. This metadata should be present in a folder that is named **StaticMetadata** in the specified paths.
+ You can suppress any breaking change that the tool identifies by adding an entry to the model's ignore list. This file is present in the **AxIgnoreDiagnosticList** folder for the model.

## List of breaking changes detected by the tool

> [!NOTE]
> The tool identifies metadata compatibility changes as breaking changes only if they have been defined as breaking in the tool.

### Class members

+ **Changing the access modifier of protected or public class members (including making a member read-only)** – Consumers might have read from the field or assigned values to it.
+ **Deleting or renaming public or protected class-level members** – Consumers might be using these members in some extension classes.

### Methods

+ **Changing the method signature of a protected or public method** – Wrappers and callers of the method will be broken.
+ **Making a protected or public method obsolete** – Consumers might be wrapping or overriding the methods.

### Classes and interfaces

+ **Making a class final** – Consumers might have created a derived type.
+ **Making a class abstract** – Consumers might be instantiating the class.
+ **Adding an abstract method to a class** – Consumers might have created a derived type.
+ **Adding a method to an interface** – Consumers might have implemented the interface on their own type.
+ **Making a public class obsolete and stopping instantiation of the class** – Consumers might have overridden, wrapped, or subscribed to the instance methods.

### Delegates

+ **Any change in signature** – Consumers might have subscribed dynamically.

### Tables

Any of the following changes will break table extensions and table references to tables and table fields:

+ Deleting or renaming table fields, field groups, indexes, table mappings, or table relations
+ Modifying these table properties: **Extends**, **SupportInheritance**, **TableType**, **SaveDataPerCompany.Yes**, or **SaveDataPerPartition**
+ Modifying these table field properties: **ExtendedDataType**, **Scale**, or **String size**
+ Modifying these table index properties: **AllowDuplicates.No** or **IndexType**

### Forms

Any of the following changes will break form extensions that reference the controls or methods:

+ Deleting or renaming form controls, form data sources, and form data source fields.
+ All changes that are breaking for methods are also breaking for form methods.

### Enumerations (enums)

+ Modifying these properties: **IsExtensible** or **Value**

### Extended data types (EDTs)

+ Modifying these properties: **Extends**, **EnumType**, or **Scale**

### Entities

+ All changes that are breaking for tables are also breaking for entities.
+ Renaming a public entity.

### Labels

+ **Modifying or deleting a label** – Consumers might be using the label in the current context of the label text and the parameters that were passed. We recommend that you add new labels instead of changing existing labels.

### Application elements

+ **Removing any element** – Consumers might have a compile-time dependency on the existence of the element.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
