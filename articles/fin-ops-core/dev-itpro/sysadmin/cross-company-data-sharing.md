---
title: Cross-company data sharing
description: Learn about cross-company data sharing, which is a mechanism for sharing reference and group data among companies in a deployment.
author: pnghub
ms.author: johnmichalak
ms.topic: article
ms.date: 01/21/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2016-05-31
ms.search.form: SysDataSharingConfiguration
ms.dyn365.ops.version: Platform update 1
ms.assetid: 0bbe7453-624f-4551-a1d0-842484067311
---

# Cross-company data sharing

[!include [banner](../includes/banner.md)]

This article provides information about cross-company data sharing. Cross-company sharing is a mechanism for sharing reference and group data among companies in a finance and operations deployment. This feature resembles the virtual companies feature in Microsoft Dynamics AX 2012.

## What is this feature and how does it work?

Cross-company data sharing lets you replicate (share) reference and group data among companies. The system verifies data integrity before replication occurs.

Here are some examples of cross-company data sharing and the basic logic:

* The same payment terms and payment day definitions are used across 15 legal entities.
* The same terms of delivery are used across seven legal entities in three countries/regions.
* Records created, updated, and deleted in any of the companies within the policy are replicated immediately, across all the companies.
* Fields that you don't select for sharing are maintained in each company and don't trigger any replication.
* As part of enabling a policy, you can optionally copy any existing records.

Cross-company data sharing has the following limitations:

* You can't use it to share transactional data between companies.
* You can only share reference and group data, or tables that you specifically enable. For example, set **Data Sharing Type** to **Duplicate**.
* It supports replication of fewer than 1 million total records per job. This total is calculated as the number of shared records multiplied by the number of shared companies. The limit is increased to 2 million records starting with Platform update for version 10.0.10.
* It supports replication for up to 100 companies per policy. The limit is increased to 300 companies starting with Platform update for version 10.0.10.
* Only one level of child relationships is exposed. To protect data consistency, replication doesn't occur if another level is required.
* You can't share fields that reference financial dimensions across companies. For example, **Ledger** or **Default** dimension.
  Dimensions hold a loose foreign key reference to the backing dimension data, which can reference both company-specific and non-company specific data. Determining the appropriate action to be taken for each dimension value has inherent complexity and would require a change from the current implementation, which could dramatically impact performance.
* You can't use it with [dual-write](../data-entities/dual-write/dual-write-home-page.md).

### Policies

Defined policies that you save in data packages manage data sharing. You can find templates that Microsoft has tested and supports as downloadable data packages on Microsoft Dynamics 365 Lifecycle Services. By using policies, you can control the following aspects of data sharing:

* The fields that are replicated
* The entities that participate in the replication
* The companies that participate in the sharing

The same company and table can only be in one policy. You can share the same table in more than one policy. This sharing occurs when the limits of records or companies are reached, or to create policies for tables that need to be shared differently for different countries or regions.

> [!NOTE]
> Only required foreign key fields are selected by default. You need to manually select optional foreign keys to include them. Add one or more tables when selecting a foreign key field, unless the table is already added.

You can find policy templates that Microsoft has tested and supports as downloadable data packages on Lifecycle Services.

> [!IMPORTANT]
> Although customers can modify the Microsoft data templates that are available from Lifecycle Services, this scenario isn't supported.

### Conflict resolution

Validation rules run when you enable a sharing policy. If the validation rules detect inconsistencies, the user who implements the system can choose which records from which company should win.

### Considerations for successful data sharing

Several entities in the Microsoft data packages have references that you must consider when you enable the entities. You can't enable some data sharing policies if references don't match. You can enable other policies, but you should use the Find inconsistency checker tool to verify that your data is consistent. Here are some examples:

* The Production group sharing policy has a reference to a company's chart of accounts. Therefore, all companies that you add to this sharing policy must use the same chart of accounts.
* If you want to enable entities that use number sequences, the number sequence types must be the same across all companies in a sharing policy for those entities.
* Setup options must be the same across the companies that are involved in the sharing policy. Examples of setup options include the setting that specifies whether tax is included by default.

## When should I use cross-company data sharing?

Use cross-company data sharing for the following business scenarios:

* Sharing simple reference and group data in a single deployment.
* Sharing among companies that have similar configurations.
* Sharing scenarios that Microsoft explicitly tested.

Cross-company data sharing isn't supported for the following scenarios:

* Franchising solutions, where thousands of records are shared across thousands of companies.
* Sharing transactional records for reporting or management purposes, such as consolidations.
* Sharing across deployments.
* Complex scenarios, such as replication of subtype or supertype tables or tables that have date effectivity rules.
* Tables that don't have a unique index.

## Customer and vendor master data sharing

Customer and vendor master data sharing allows you to share customer and vendor data across multiple companies. If you want to be considered for this feature, complete the [Data sharing application](https://aka.ms/MSDYN365FODataSharing) and contact Support.

With the release of Platform update for version 10.0.12, you can enable customer and vendor master data sharing by using the **Customer and vendor master data sharing** feature in the **Feature management** module. There's no need to complete a survey first. Consider the limits in the number of records and companies stated earlier.

> [!NOTE]
> As of version 10.0.43, the **default dimensions** that you set up against a customer or vendor can be shared across companies only if the full set of financial dimensions is defined as global, such as Department or Business unit. For more information, see [Default financial dimension data sharing](cross-company-data-sharing-financial-dimensions.md).
>
> Default dimensions hold a loose foreign key reference to the backing dimension data, which can reference both company-specific and non-company specific data. Determining the appropriate action to take for each dimension value has inherent complexity and would require a change from the current implementation, which could dramatically impact performance.

## Download a cross-company data sharing template from Lifecycle Services

1. Sign in to Lifecycle Services.
1. On the home page, select **Shared asset library**.
1. In the **Asset type** list, select **Data package**.
1. Select any of the available data package files to download them.

## Currently supported cross-company data sharing templates

| Package name on Lifecycle Services | Data sharing policies |
|---|---|
| Financial data sharing templates | <ul><li>Bank parameters</li><li>Ledger journal names</li><li>Payment days</li><li>Payment schedules</li><li>Payment terms</li><li>Tax exempt codes</li></ul> |
| Supply chain data sharing templates | <ul><li>Barcode parameters</li><li>Barcode setup</li><li>Buyer group</li><li>Charges group</li><li>Commission</li><li>Destination code</li><li>Nonconformance type</li><li>Order entry deadline group</li><li>Order origin code</li><li>Order pool</li><li>Production group</li><li>Production pool</li><li>Reason for delivery</li><li>Supplementary item group</li><li>Terms of delivery</li><li>Work time calendar</li></ul> |

## Additional resources

[Configure financial cross-company data sharing (Task guide)](../data-entities/tasks/configure-financial-cross-company-data-sharing.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
