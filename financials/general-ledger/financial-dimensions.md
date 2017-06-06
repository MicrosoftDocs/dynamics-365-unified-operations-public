---
# required metadata

title: Financial dimensions
description: This article explains the different types of financial dimensions and how they are set up.
author: RobinARH
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: DimensionDetails, DimensionValueDetails, SysTranslationDetail
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: RobinARH
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 25871
ms.assetid: af54621c-c8be-4b72-b6df-dcf886c40ce4
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Financial dimensions

[!include[banner](../includes/banner.md)]


This article explains the different types of financial dimensions and how they are set up.

Use the Financial dimensions page to create financial dimensions that you can use as account segments for charts of accounts. There are two types of financial dimensions, custom dimensions and entity backed dimensions. Custom dimensions are shared across legal entities and the values are entered and maintained by the user. Entity backed dimensions are dimensions whose values are defined elsewhere in the system, such as Customers or Stores. Some entity backed dimensions are shared across legal entities, and come entity backed dimensions are company specific. 

After you have created the financial dimensions, use the Financial dimension values page to assign additional properties to each financial dimension. 

Although you can use financial dimensions to represent legal entities without creating the legal entities in Microsoft Dynamics 365 for Operations, financial dimensions aren’t designed to address the operational or business needs of legal entities. The interunit accounting functionality in Microsoft Dynamics 365 for Operations is designed to address only the accounting entries that are created by each transaction. 

Before you set up financial dimensions as legal entities, evaluate your business processes in the following areas to determine if this setup will work for your organization:

-   Inventory
-   Sales and purchases between financial dimensions and legal entities
-   Sales tax calculation and reporting
-   Operational reporting

Some examples of the limitations include the following:

-   You can use sales tax functionality only with legal entities, not with financial dimensions.
-   Some reports don't include financial dimensions, so you can't always report by financial dimension unless those reports are modified.

**Custom dimensions** 

To create a user-defined financial dimension, in the Use values from field, select &lt; Custom dimension &gt;. You can also specify an account mask to limit the amount and type of information that you can enter for dimension values. You can enter characters that remain the same for each dimension value, such as letters or a hyphen. You can also enter number signs (\#) and ampersands (&) as placeholders for letters and numbers that will change every time that a dimension value is created. Use a number sign (\#) as a placeholder for a number and an ampersand (&) as a placeholder for a letter. 

**Example** 

To limit the dimension value to the letters CC and three numbers, you enter CC-\#\#\# as the format mask. This field is available only when you select &lt; Custom dimension &gt; in the Use values from field. 

**Entity backed dimensions** 

To create an entity backed financial dimension, in the Use values from field, select a system-defined entity to base the financial dimension on. Financial dimension values are created from this selection. For example, to create dimension values for projects, select Projects. A dimension value will be created for each project name. The dimension values page shows the values for the entity and if they are company specific, the company for the value. 

**Activating dimensions** 

Activating the financial dimension updates the table with the financial dimension name and removes deleted dimensions. You can enter dimension values before you activate a financial dimension, but a financial dimension cannot be consumed anywhere until it is activated. For example, you cannot add a financial dimension to an account structure until the financial dimension has been activated. Clicking activate will update all dimensions with status changes. 

**Translations** 

The Text translation page allows you to enter text to be displayed in different languages for the selected financial dimension. The Main account translation page is where you can enter text to be displayed in different languages for the main account. 

**Legal entity overrides** 

Not all dimensions are valid for all legal entities and some may only be relevant for a specific time period. In this scenario the Legal entity overrides section can be used to identify which companies the dimension should be suspended for, who the owner is and the time period the dimension is active.





