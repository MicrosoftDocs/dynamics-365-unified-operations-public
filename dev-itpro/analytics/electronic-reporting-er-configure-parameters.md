---
# required metadata

title: Configure Electronic reporting framework
description: 
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

This article describes the pages that you use to set up basic functionality for Electronic reporting in Microsoft Dynamics 365 for Operations. It also describes setup steps that you must complete before you start to set up Electronic reporting.

## Prerequisites for Electronic reporting setup

Before you can set up Electronic reporting, you must set up required document types in Document management:

* For using MS Office documents as templates for ER reports;
* For storing outputs of ER reports in jobs archive;
* For storing outputs of ER reports to preview them in other applications;
* For handling files in ER framework for other than mentioned above purposes.

Note that the following attribute’s values can be selected for such document types:

Attribute name | Attribute value
---------------|----------------
Class|**Attach file**
Group|**File**
Location|**Azure storage** or **SharePoint**

## Setup pages for Electronic reporting
Use the following pages to set up the basic functionality of Electronic reporting for all legal entities. The pages are listed in the recommended order of setup.

1.	On the **Electronic reporting parameters** page, define the following:
    1. On the Attachments tab, define the document types to store various kind of files using in ER framework.
    1. On the LCS tab, define the desired number of parallel threads for loading ER configuration from LCS repositories in the most efficient way. The value can vary from 1 to 15 and depends on the available resources of the current Microsoft Dynamics 365 for Operations application. Note that the real number of using threads will be defined automatically depending not only on this setting but also on the number of other tasks, their priorities, etc.
  
2.	On the **Configuration provider table** page, create ER provider records. Each of such provider can be selected as active. Active provider’s name and internet address are stored in any created ER configuration as attributes of the owner of this configuration.

## Optional setup pages for Electronic reporting
In addition to the basic functionality, Electronic reporting has other functionality that you can set up.

1.	On the **Electronic reporting destination** page, define desired ER outputs destinations for each single FILE output of each ER format configuration. Use configured in advance document types of the Document management framework for that. Use this page to set up the optional functionality of Electronic reporting for each single legal entity. Review the dedicated to ER destinations help topic (below) for more details.

2.	Whenever you added new or update existing AOT artifacts that are used in ER as data sources (tables, views, data entities), use the **Organization administration module \ Electronic reporting \ Rebuild table references** menu item to bring your AOT changes to the ER meta data (data model of the Microsoft Dynamics 365 for Operations application for ER).

## Frequently asked questions
**Q**: I use the Microsoft Dynamics 365 for Operations application that is running on a VM with 2 CPUs each of which contains 4 cores. What is the optimal (from standpoint of the overall system performance) value for the number of parallel threads for loading ER configuration from LCS?
**A**: 5 or 6.  The following empirical formula is suggested to get this value: Cores/2 + 1(2).

**Q**: I have added to AOT my new custom table. I created a new ER model mapping configuration for my ER data model one. Designing this model mapping, I tried to add a new data source of the **Table records** type that refers to my table. I could add my table name manually to the **Table** lookup and ER model mapping accepted it with no errors or warnings. But why did not I find my table’s name in list of available choices offered by the **Table** lookup of this data source?
**A**: To have the name of your custom table in this lookup, run the **Rebuild table references** procedure to synchronize the ER meta data (data model of the Microsoft Dynamics 365 for Operations application for ER) using to access application data.

**Q**: In my instance of the Microsoft Dynamics 365 for Operations that was deployed for development and testing purposes, on the ER workspace page I can select Microsoft provider as active. Why I can’t do the same in my production environment?
**A**: Microsoft provider is used to mark ER configurations that have been initially designed and are maintained by Microsoft company. It is expected that new versions of such configurations will be shared by Microsoft in the future. It is the wrong practice to mark the Microsoft provider as active. If you would do this, you would be able to update these configurations: change the content, register new versions for them, etc. That will cause problems with the import and adoption of new versions of these configurations received from Microsoft company in the future. Instead, register a new ER provider for your company and use it for your ER configurations maintenance. To re-use a Microsoft configuration, select it as the base for your derived copy of it. To incorporate provided by Microsoft changes, rebase your configuration to a new version of the Microsoft one whenever it becomes available.

## See also
![Electronic reporting overview](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/analytics/general-electronic-reporting)

![Electronic reporting destinations](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/analytics/electronic-reporting-destinations)
