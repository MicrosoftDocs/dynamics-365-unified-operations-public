---
# required metadata

title: Enhanced filtering in the RCS/Global repository
description: This topic describes how a user can use enhanced filtering in the RCS/Global repository to search for configurations.
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

This topic describes enhanced filtering capabilities for RCS Global repository, which have been improved to include the following filters: 
- Country/region - ISO country codes  
- Tags - for functional/feature area; Industry; Business document type 

You can apply filters, either individually or in groups, to find specific or related configurations. For example, to find all configurable business documents related to vendor invoices, you can select and apply the **Business document type** filter to see all related configurations. 

You can also overlay a country/region code to further refine a search by selecting the country code & clicking **Apply filter**.  
For example - Filtering section and options:

[![Filter section for Global repository](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/417079-enhanced-filtering/RCS_Enhanced%20filter_section.JPG)](./media/ER-ExtLookup-Lookup1.gif)

Applied filtering on 'Business document type' = Vendor invoice: 

[![Applied filter for business document type](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/417079-enhanced-filtering/RCS_Enhanced%20filtering_Applied.JPG)](./media/ER-ExtLookup-Lookup1.gif)

Filtered results can then be imported, either individually or as a set, by selecting the group of configurations, and then clicking **Import**.




