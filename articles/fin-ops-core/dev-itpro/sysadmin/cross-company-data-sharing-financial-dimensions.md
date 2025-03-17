---
title: Cross-company data sharing for financial dimensions
description: Learn about cross-company data sharing for financial dimensions.
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

# Cross-company data sharing for financial dimensions

[!include [banner](../includes/banner.md)]

In limited scenarios, default dimension fields can be shared by using cross-company data sharing. This article explains when those fields can be shared.

Learn more in [Cross-company data sharing overview](srs-overview.md).

## Backing tables that can be used by financial dimensions

Financial dimensions use the values from various tables in the system. These tables are known as *backing tables*. Backing tables can store data either globally or per company. If they store the data globally, all records are accessible, regardless of the company that you view the data from.

The following backing tables are included out of the box and can be used by financial dimensions.

| Global dimensions | Nonglobal dimensions |
|-------------------|----------------------|
| <ul><li>\<Custom dimension\></li><li>Business units</li><li>Cost centers</li><li>Departments</li><li>Jobs</li><li>Legal entities</li><li>POS registers</li><li>Positions</li><li>Retail channels</li><li>Stores</li><li>Value streams</li><li>Workers</li></ul> | <ul><li>Agreements</li><li>Bank accounts</li><li>Campaigns</li><li>Cash accounts</li><li>Customer groups</li><li>Customers<li>Deferrals</li><li>Expense and income codes</li><li>Expense purposes</li><li>Fiscal establishments</li><li>Fixed asset groups</li><li>Fixed assets</li><li>Funds</li><li>Item groups</li><li>Items</li><li>Leases</li><li>Project contracts</li><li>Project groups</li><li>Projects</li><li>Prospects</li><li>Resource groups</li><li>Resources</li><li>Tax branches</li><li>Vendor groups</li><li>Vendors</li></ul> |

## Sharing default dimensions

Default dimension fields can be shared through data sharing policies only if all dimensions in the system are global. If any nonglobal dimension exists, the field can't be shared.

### After a default dimension field is shared

After the policy is enabled with a shared default dimension field, you can't create new nonglobal dimensions in the system. However, you can continue to create new global dimensions.

## FAQ

**If I use Microsoft SQL Server Reporting Services (SSRS) to share a table across all companies, can a dimension be changed from nonglobal to global?**

No. The list is static. Even if you share a custom table by using SSRS, and you try to "make it global," the table remains nonglobal. The system uses metadata that is defined in the table itself to determine whether that table is global or nonglobal.

**Can I disable sharing of a default dimension field?**

Master company sharing policies can't be disabled. This rule applies to fields that are shared on tables in the policy.

## Additional resources

[Configure financial cross-company data sharing](../data-entities/tasks/configure-financial-cross-company-data-sharing.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
