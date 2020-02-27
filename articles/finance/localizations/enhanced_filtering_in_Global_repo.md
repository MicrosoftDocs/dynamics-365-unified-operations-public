---
# required metadata

title: Enhanced filtering in the RCS/Global repository
description: This topic describes enhanced filtering capabilities for the RCS Global repository, which have been improved to include the additional filters.
author: JaneAugustin      
manager: AnnBe
ms.date: 02/10/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: ERSolutionTable, ERWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 97423
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: janeaug
ms.search.validFrom: 2020-02-01
ms.dyn365.ops.version: AX 10.0.9

---

# Enhanced filtering options for finding configurations in the Global repository

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic describes enhanced filtering capabilities for Regulatory Configuration Services (RCS) Global repository, which have been improved to include the following filters: 
- **Country/region** - based on ISO country codes  
- **Tags** - for functional/feature area; Industry; Business document type 

You can apply filters, either individually or in groups, to find specific or related configurations. For example, to find all configurable business documents related to vendor invoices, you can apply the **Business document type** filter. 

You can further refine a search by selecting the country code and clicking **Apply filter**.  

[![Filter section for Global repository](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/417079-enhanced-filtering/RCS_Enhanced%20filter_section.JPG)](./media/ER-ExtLookup-Lookup1.gif)

The following example shows the results when filtering on **Business document type**. 

[![Applied filter and Import for business document type] (https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/417079-Enhanced-filtering/RCS_Global%20repo_Filtering%20+%20import.JPG).](./media/ER-ExtLookup-Lookup1.gif)

Filtered results can be imported into users RCS or Dynamics 365 Finance environment, either individually or as a set (by selecting the group of configurations) and clicking **Import**.






