---
title: Cross-company data sharing for financial dimensions
description: Learn about cross-company data sharing with financial dimensions.
author: rcarlson
ms.author: rcarlson
ms.topic: article
ms.date: 11/12/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2024-11-11
ms.search.form: SysDataSharingConfiguration
ms.dyn365.ops.version: Platform update 1
ms.assetid: 0bbe7453-624f-4551-a1d0-842484067311
---

# Cross-company data sharing with financial dimensions

[!include [banner](../includes/banner.md)]

This article provides information about cross-company data sharing with default financial dimensions.  

## Overview

Default dimension fields can be shared using cross-company data sharing in limited scenarios. This guide defines when those fields can be shared.

For more information, see [Cross-company data sharing overview](/srs-overview).

## Global dimensions

Financial dimensions utilize the values from various tables in the system. These \"backing\" tables can either store data globally or per company. If they store the data globally, then all records are
accessible no matter which company you view the data from.

The following is a list of the \"backing\" tables that financial dimensions can utilize that are shipped out of the box.

  |Global Dimensions       | Non-global dimensions |
  |------------------------| ----------------------|
  | \< Custom dimension \> | Agreements            |
  | Business units         | Bank accounts         |
  | Cost centers           | Campaigns             |
  | Departments            | Cash accounts         |
  | Jobs                   | Customer groups       |
  | Legal entities         | Customers             |
  | POS registers          | Deferrals             |
  | Positions              | Expense and income codes |
  | Retail channels        | Expense purposes |
  | Stores                 | Fiscal establishments |
  | Value streams          | Fixed asset groups    |
  | Workers                | Fixed assets          |
  |                        | Funds                 |
  |                        | Item groups           |
  |                        | Items                 |
  |                        | Leases                |
  |                        | Project contracts     |
  |                        | Project groups        |
  |                        | Projects              |
  |                        | Prospects             |
  |                        | Resource groups       |
  |                        | Resources             |
  |                        | Tax branches          |
  |                        | Vendor groups         |
  |                        | Vendors               |

### Sharing default dimensions

In order for default dimensions to be shared through data sharing policies, all dimensions in the system must be global. If any non-global dimension exists, the field cannot be shared.

### After a default dimension field has been shared

After the policy is enabled with a shared default dimension field, you can't create new non-global dimensions in the system. You can, however, continue to create new global dimensions.

## FAQs

 - What if I'm using SRS to share table X across all companies? Would this move a dimension from non-global to global?
No, this list is static. Even if you were to share the CustTable using SRS to \"make it global\", it wouldn\'t work. The system uses metadata defined in the table to determine if it is global or not.

 - Can I disable sharing of the default dimension field?

Master company sharing policies cannot be disabled. This includes fields shared on tables in the policy.

## Additional resources

[Configure financial cross-company data sharing](../data-entities/tasks/configure-financial-cross-company-data-sharing.md)





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

