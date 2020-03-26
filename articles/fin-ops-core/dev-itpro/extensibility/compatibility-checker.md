---

# required metadata

title: Add values to enums through extension
description: This topic explains how to add new values to an enum by extending the enum.
author: smithanataraj
manager: AnnBe
ms.date: 06/20/2017
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
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: Platform update 9
---

**Compatibility Checker**

The Compatibility checker tool can detect metadata breaking changes,
hence helping to check for backward compatibility, against a given
baseline release/update. Microsoft has been using the tool to help them
ensure metadata compatibility.

 

The Compatibility checker will be available for use for partners/ISVs
from PU34, as one of the dev tools. With this, the partners can ensure
that their solutions are backwards compatible with their earlier
releases, before installing/pushing updates to customers.

 

**What can the tool detect?**

The tool is comparing metadata of the current version with a baseline
version. It can detect and report metadata breaking changes that have
been identified and added to the tool as breaking by Microsoft.

 

The list of breaking changes detected by the tool is in the last section
below, however note that it is not a comprehensive list of all
compatibility breaking changes.

 

**What can the tool NOT detect?**

The tool does not detect any breaking changes that cannot be identified
by comparing metadata.

 

Some of the most common breaking changes that couldn't be detected by
the tool are:

 

1.  > Removing the reference to a protected/public method.

2.  > Changing the responsibility of a method.

>  

 

**How to use the tool?**

The tool can be used to detect metadata compatibility issues of a new
version, against the previous version that the new version is replacing.
At Microsoft, the tool is used to detect breaking changes for a given
monthly update against the previous monthly update.

 

The Compatibility Checker is available as a dev tool, from PU 34, that
can be run as follows:

 

**Usage:**

CompatibilityChecker.exe -BaselineDirectory=\<Path to baseline
metadata\> -CurrentDirectory=\<Path to current metadata\>
-ModuleName=\<Module name\> -OutputFile=\<Output file path\>
-LogFile=\<Log file path\>

 

Example:

CompatibilityChecker.exe
-BaselineDirectory="[<span class="underline">\\\\servername\\archive\\Build1\\BaselineMetadata</span>](file:///\\\\servername\\archive\\Build1\\BaselineMetadata)"
-CurrentDirectory="E:\\MyCode\\retail\\amd64\\BaselineMetadata"
-ModuleName="Directory"
-OutputFile="E:\\Logs\\Directory\\Diagnostics.xml"
-LogFile="E:\\Logs\\Directory\\Checkerlog.txt");

 

Description:

Compatibility Checker identifies any breaking changes by comparing
current metadata against a given baseline metadata.

*BaselineDirectory* specifies the path of the baseline metadata.

*CurrentDirectory* specifies the path of the current metadata.

A list of breaking changes is created in the file specified in
*OutputFile*.

Please ensure the metadata is compiled and current before running
Compatibility Checker.

 

Note:

1\. OutputFile contains the list of breaking changes identified by
CompatibilityChecker.

2\. Ensure that baseline paths exist with the metadata for the given
module, and its dependencies (if any).

3\. The metadata paths for BaselineDirectory and CurrentDirectory should
have metadata for "StaticMetadata". It should be present inside a folder
named "StaticMetadata" in the given paths.

4\. Any breaking change identified by CompatibilityChecker can be
suppressed by adding an entry in the model's ignore list. This file is
present in "AxIgnoreDiagnosticList" folder for the model.

 

** **

**List of breaking changes detected by the tool:**

**NOTE: Only metadata compatibility changes that have been defined in
the tool as breaking are detected by the tool as breaking changes.**

**Class members**

  - > **Changing access modifier of protected or public class members
    > (including making a member ReadOnly)** – Consumers might have read
    > from or assigned values to the field.

  - > **Deleting or renaming public or protected class-level members** –
    > Consumers might be using these members in some extension classes.

**Methods**

  - > **Changing the method signature of a protected or public methods
    > -** Wrappers/Callers of the method will be broken

  - > **Making a protected or public method obsolete -** Consumers might
    > be wrapping/overriding the methods.

**Classes and interfaces**

  - > **Making a class final** – Consumers might have created a derived
    > type.

  - > **Making a class abstract -**– Consumers might be instantiating
    > the class.

  - > **Adding an abstract method to a class** – Consumers might have
    > created a derived type.

  - > **Adding a method to an interface** – Consumers might have
    > implemented the interface on their own type.

  - > **Making a public class obsolete and stopping instantiation of the
    > class** – Consumers might have overridden, wrapped, or subscribed
    > to the instance methods.

**Delegates**

  - > **Any change in signature** – Consumers might have subscribed
    > dynamically.

**Tables**

  - > **Deleting/renaming table fields, field groups, indexes, table
    > mappings, table relations**

  - > **Modifying table properties - Extends, SuportInheritance,
    > TableType, SaveDataPerCompany.Yes, SaveDataPerPartition**

  - > **Modifying table field properties - ExtendedDataType, Scale,
    > String size**

  - > **Modifying table index properties - AllowDuplicates.No,
    > IndexType**

>  

Any of the above changes will break table extensions and / or any
references to table / table fields.

**Forms**

  - > **Deletion/renaming form controls, form datasources and form
    > datasource fields.**

  - > **All method breaking changes are also breaking for form
    > methods.**

Any of the above changes will break Form Extensions referencing the
controls or the methods.

**Enums**

  - > **Modifying properties IsExtensible or Value**

**EDTs**

  - > **Modifying the properties Extends, EnumType or Scale**

**Entities**

  - > **All breaking changes for tables are all also applicable for
    > entities.**

  - > **Renaming a public entity.**

**Label changes**

  - > **Modifying or deleting a label** – Consumers might be using the
    > label in the current context of the label text and the parameters
    > that were passed. We recommend that, going forward, new labels to
    > be added instead of changing existing ones.

**Application element changes**

  - > **Removing any element** – Consumers might have a compile time
    > dependency on the existence of the element.
