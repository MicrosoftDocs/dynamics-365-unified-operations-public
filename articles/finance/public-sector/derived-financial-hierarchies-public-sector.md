---
# required metadata

title: Derived financial hierarchies in the public sector
description: This article describes the derived financial hierarchies functionality that is available for the public sector. 
author: v-kiarnd
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: EcoResCategory, EcoResCategoryHierarchyListPage, EcoResCategoryHierarchyRole, LedgerDerivedFinHierarchies, LedgerDerivedFinHierarchyFilterResults, LedgerDerivedFinHierarchyLegalEntities
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.assetid: a1b30d2a-a370-402a-b3bd-d562adca55f0
ms.search.region: Global
ms.search.industry: Public sector
ms.author: twheeloc
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Derived financial hierarchies in the public sector

[!include [banner](../includes/banner.md)]

This article describes the derived financial hierarchies functionality that is available for the public sector. 

To meet Common Government-wide Accounting Classification (CGAC) requirements, public-sector organizations can use derived financial hierarchies to collect and analyze posted transaction data for specific main account numbers, full account numbers, and financial dimension values. 

Typically, category hierarchies are set up to classify transactions for reporting and analysis based on the financial dimensions in an account structure at the time of posting. However, by using category hierarchies with a Derived financial hierarchy category type, you can create filter rules that create financial categories and dimension values that aren't part of the account number. The financial categories and dimension values defined in the filter rules are derived from the account number dimension values that are used in the posted transactions.

Derived financial hierarchies give you a more flexible approach to grouping transactions for as needed analytics. The hierachies let you categorize transactions without having to expand the account structure to include the additional categories or dimensions that you're tracking.

## Example
An organization has an employee wellness program and an employee education program. These programs aren't associated with financial dimensions. To collect account numbers used in the posted transactions for these programs, you could do the following:

-   **Set up the category hierarchies and the derived financial hierarchies:** Create a category hierarchy named “Employee programs” with a parent node named “Programs” and two child nodes named “Employee wellness” and “Employee education.” Assign the **Derived financial hierarchy** category type to the “Employee programs” category hierarchy. Associate the “Employee programs” derived financial hierarchy with the legal entity.
-   **Set up filter rules:** Use the **Derived financial hierarchies** page to create filter rules for the main accounts and financial dimension values associated with the “Employee wellness” and “Employee education” nodes in the “Employee programs” derived financial hierarchy. **Tip:** To enter more than one dimension value in a filter, use a comma without spaces as a separator. For example, enter 100,110 or Benefits,Insurance.
-   **Analyze posted transaction data:** In the filter results, view account numbers and their account and financial dimension details.








[!INCLUDE[footer-include](../../includes/footer-banner.md)]
