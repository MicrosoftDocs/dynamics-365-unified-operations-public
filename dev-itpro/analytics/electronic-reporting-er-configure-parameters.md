---
# required metadata

title: Configure Electronic reporting framework
description: How to configure parameters of the Electronic reporting (ER) framework
author: kfend
manager: AnnBe
ms.date: 05/11/2017
ms.topic: article
ms.prod: 
ms.service: Lifecycle Services
ms.technology: 

# optional metadata

ms.search.form: ERSolutionTable, ERVendorTable, ERWorkspace, ERParameters, ERFormatDestinationTable
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: AX 7.1.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 27621
ms.assetid: 3c1291de-230c-4e31-96c4-ba69a310690a
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Configure Electronic reporting framework
This topic provides information about how to set up the basic functionality for Electronic reporting. this topic also provides the steps that you must complete before you set up Electronic reporting.

## Prerequisites for Electronic reporting setup
Before you can set up Electronic reporting (ER), you must set up the required document types in Document management:
- A document type for Microsoft Office documents that are used as templates for ER reports.
- A document type for storing the output of ER reports in the jobs archive.
- A document type for storing the output of ER reports so that they can be viewed in other applications.
- A document type for handling files in the ER framework outside of the purposes mentioned in this list.

The following attribute values can be selected for each document types:

Attribute name | Attribute value
---------------|----------------
Class|**Attach file**
Group|**File**
Location|**Azure storage** or **SharePoint**

## Set up Electronic reporting
Use the following procedure to set up the basic functionality of Electronic reporting for all legal entities.

1.	On the **Electronic reporting parameters** page, on the **Attachments** tab, define the types of documents that will be used for file storage in the ER framework.
2. On the **LCS** tab, define the number of parallel threads for loading an ER configuration from LCS repositories in the most efficient way. The value can vary from 1 to 15 depending on the available resources of the current application. Note that the real number of threads will be defined automatically based on this setting and on the number of other tasks and their priorities.
3.	On the **Configuration provider table** page, create ER provider records. Each of the providers can be marked as **Active**. The active provider’s name and internet address are stored in an ER configuration as attributes of the owner of the configuration.

## Optional setup for Electronic reporting
In addition to the basic functionality, Electronic reporting has other functionality that you can set up.

- On the **Electronic reporting destination** page, define the ER output destinations for each single FILE output of each ER format configuration. Use the document types of the Document management framework taht you previously set up. You can also use this page to set up the optional functionality of Electronic reporting for each single legal entity. Review the dedicated to ER destinations help topic (below) for more details.

- Whenever you add new or update existing AOT artifacts that are used in ER as data sources (tables, views, data entities), use the menu item, **Rebuils table references** (**Organization administration** > **Electronic reporting** > **Rebuild table references**) to bring your AOT changes to the ER meta data.

## Frequently asked questions
**Question**: What is the optional number of parallel threads for loading an ER configuration from LCS?

**Answer**: To calculate the optiomal number of parallel threads, use the following empirical formula: Cores/2 + 1(2). For example, if your application is running on a VM with 2 CPUs and each CPU contains 4 cores, the according to the calculation, five or six threads.


**Question**: I have added a custom table to the AOT. I created a new ER model mapping configuration for my ER data model. During the design of the model mapping, I tried to add a new data source type, **Table records**, that refers to my table. I could add my table name manually to the **Table** lookup and ER model mapping accepted it with no errors or warnings. However, my table’s name isn't included in the list of available choices offered by the **Table** lookup of this data source. How do I include the name of my table?

**Answer**: To include the name of your custom table in the **Table** lookup, complete the procedure, **Rebuild table references** to synchronize the ER metadata which is used to access application data.


**Question**: Why can’t I mark the Microsoft provider as **Active** on the **Electronic reporting workspace** page in my production environment?

**Answer**: The Microsoft provider is used to mark ER configurations that have been designed and maintained by Microsoft. We expect that new versions of the configurations will be released by Microsoft in the future. We do not recomment that you mark the Microsoft provider as Active. If you do, you would then be able to update configurations including changing the content and registering new versions. This would cause problems in the future with the import and adoption of the new versions of these configurations provided by Microsoft. Instead, register a new ER provider for your company and use it for your ER configurations maintenance. To re-use a Microsoft configuration, select it as the base for your derived copy. To incorporate changes that are provided by Microsoft, rebase your configuration to a new version of the Microsoft one whenever it becomes available.


## See also
[Electronic reporting overview](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/analytics/general-electronic-reporting)

[Electronic reporting destinations](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/analytics/electronic-reporting-destinations)
