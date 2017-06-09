---
# required metadata

title: Configure the Electronic reporting framework
description: This topic explains how to configure parameters of the Electronic reporting (ER) framework.
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

# Configure the Electronic reporting framework
This topic explains how to set up the basic functionality for Electronic reporting (ER). It also describes the steps that you must complete before you can set up ER.

## Prerequisites for ER setup
Before you can set up ER, you must set up the required document types in Document management:

- A document type for Microsoft Office documents that are used as templates for ER reports.
- A document type that is used to store the output of ER reports in the jobs archive.
- A document type that is used to store the output of ER reports so that they can be viewed in other programs.
- A document type that is used to handle files in the ER framework for all other purposes.

For each document type, the following attribute values can be selected.

Attribute name | Attribute value
---------------|----------------
Class | **Attach file**
Group | **File**
Location | **Azure storage** or **SharePoint**

## Set up ER
Use the following procedure to set up the basic functionality of ER for all legal entities.

1.	On the **Electronic reporting parameters** page, on the **Attachments** tab, define the types of documents that should be used for file storage in the ER framework.
2. On the **LCS** tab, define the number of parallel threads that should be used to load an ER configuration from repositories in Microsoft Dynamics Lifecycle Services (LCS), so that the configurations are loaded in the most efficient manner. The value can vary from **1** to **15**, depending on the available resources of the current program. Note that the real number of threads will be defined automatically, based on this setting, and on the number of other tasks and their priorities.
3.	On the **Configuration provider table** page, create ER provider records. Each provider can be marked as **Active**. The active provider’s name and Internet address are stored in an ER configuration as attributes of the owner of the configuration.

## Optional setup for ER
In addition to the basic functionality, ER has other functionality that you can set up.

- On the **Electronic reporting destination** page, define the ER output destinations for each file output of each ER format configuration. Use the document types of the Document management framework that you set up earlier. You can also use this page to set up the optional functionality of ER for each legal entity. For more information, see the topic about ER destinations that is linked in the "See also" section of this topic.
- Whenever you add new Application Object Tree (AOT) artifacts or update existing AOT artifacts that are used as data sources (tables, views, or data entities) in ER, use the **Rebuild table references** menu item (**Organization administration** > **Electronic reporting** > **Rebuild table references**) to bring your AOT changes into the ER metadata.

## Frequently asked questions
**Question:** What is the optimal number of parallel threads to use to load an ER configuration from LCS?

**Answer:** To calculate the optimal number of parallel threads, use the following empirical formula: Cores ÷ 2 + 1(2). For example, if the program runs on a virtual machine (VM) that has two CPUs, and each CPU contains four cores, the optimal number is five or six parallel threads.

**Question:** I have added a custom table to the AOT. I created a new ER model mapping configuration for my ER data model. During the design of the model mapping, I tried to add a new data source type, **Table records**, that refers to my table. I could manually add my table name to the **Table** lookup, and the ER model mapping accepted it without errors or warnings. However, my table’s name isn't included in the list of available choices that the **Table** lookup of this data source offers. How do I include the name of my table?

**Answer:** To include the name of your custom table in the **Table** lookup, complete the "Rebuild table references" procedure to synchronize the ER metadata that is used to access application data.

**Question:** Why can’t I mark the Microsoft provider as **Active** in the **Electronic reporting** workspace in my production environment?

**Answer:** The Microsoft provider is used to mark ER configurations that have been designed and maintained by Microsoft. We expect that Microsoft will release new versions of the configurations in the future. We recommend that you not mark the Microsoft provider as **Active**. Otherwise, you can update the configurations. (For example, you can change the content and register new versions.) These updates will cause issues in the future, when Microsoft provides new versions of the configurations, and those new versions must be imported and adopted. Instead, register a new ER provider for your company, and use it for your ER configurations maintenance. To reuse a Microsoft configuration, select it as the base for your derived copy. To incorporate changes that are provided by Microsoft, rebase your configuration to a new version of the Microsoft configuration when it becomes available.

## See also

- [Electronic reporting overview](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/analytics/general-electronic-reporting)
- [Electronic reporting destinations](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/analytics/electronic-reporting-destinations)
