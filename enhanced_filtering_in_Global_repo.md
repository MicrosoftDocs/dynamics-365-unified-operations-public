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

# Allow users to leverage enhanced filtering options to search configuration in the Global repository.

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

Filtering capabilities for RCS Global repository have been improved to include the option to filter using the following: 
- Country/region - ISO country codes and 
- Tags - for functional/feature area; Industry; Business document type 

Filters can be applied, either singularly or multi-select, to allow the user to easily find specific or related configuration. 
For example, if a user wants to find all configurable business documents related to 'vendor invoice' they can select this filter & apply to see all related configurations. 
They can also overlay country/region code if they want to refine the search further by selecting country code & clicking apply filters.  
For example - Filtering section and options:

[![Filter section for Global repository](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/417079-enhanced-filtering/RCS_Enhanced%20filter_section.JPG)](./media/ER-ExtLookup-Lookup1.gif)

Applied filtering on 'Business document type' = Vendor invoice: 

[![Applied filter for business document type](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/417079-enhanced-filtering/RCS_Enhanced%20filtering_Applied.JPG)](./media/ER-ExtLookup-Lookup1.gif)

Filtered results can then be imported either individually or as a set by selecting the group of configuration & clicking 'import'.




