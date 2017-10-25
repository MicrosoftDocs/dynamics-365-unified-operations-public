---
# required metadata

title: Record templates
description: This article introduces the concept of record templates and explains how they can be used to create records that share information.
author: pvillads
manager: AnnBe
ms.date: 08/18/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 16101
ms.assetid: 61ada2d8-84c3-44bc-b4c5-516b1aeac3d1
ms.search.region: Global
# ms.search.industry: 
ms.author: pvillads
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Record templates

[!include[banner](../includes/banner.md)]


This article introduces the concept of record templates and explains how they can be used to create records that share information.

Record templates can help you to create records more quickly in Microsoft Dynamics 365 for Finance and Operations. You can create record templates for only some of the record types in Microsoft Dynamics 365 for Finance and Operations. 

For example, imagine you are entering rental information for a car rental business that is located in San Francisco. Since most of the customers are likely to be from the San Francisco area, it would be nice if you could automatically fill in the values for the **State**, **Country**, and **City** fields on the rental form. 

> [!Note]
> You can apply templates only for the areas of Finance and Operations that you have access to. However all template titles are visible to you when you create a new record, and to other users as well, if you are creating templates that will be available for all users. Be sure to consider this when naming templates. For example, avoid using names that include words, such as "commission," if is confidential that some employees in the company have commission-based salaries. 

When one or more templates that you have access to exist for a specific form and you attempt to create a new record in the form, the **Select a template for** page is displayed. When you select a template from the list, the new record is created and contains default information that is based on the template that you selected. If you do not want to use templates when you create new records, select the **Do not ask again** check box in the **Select a template for** page. To display the template selection dialog box again, right-click any record, click **Record info**, and then click **Show template selection**.



