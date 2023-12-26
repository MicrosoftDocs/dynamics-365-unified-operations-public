---
title: Cross-company data sharing
description: This article describes cross-company data sharing, which is a mechanism for sharing reference and group data among companies in a deployment.
author: peakerbl
ms.date: 06/03/2020
ms.topic: article
ms.prod: 
ms.technology: 
audience: IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: peakerbl
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: Platform update 1
ms.assetid: 0bbe7453-624f-4551-a1d0-842484067311
ms.search.form: SysDataSharingConfiguration
---

# Cross-company data sharing

[!include [banner](../includes/banner.md)]

This article provides information about cross-company data sharing. Cross-company sharing is a mechanism for sharing reference and group data among companies in a finance and operations deployment. This feature resembles the virtual companies feature in Microsoft Dynamics AX 2012.

## What is this feature and how does it work?

Cross-company data sharing lets you replicate (share) reference and group data among companies. Data integrity is verified before replication occurs. 

Here are some examples of cross-company data sharing and the basic logic:

-   The same payment terms and payment day definitions are used across 15 legal entities.
-   The same terms of delivery are used across seven legal entities in three countries/regions.
-   Records created, updated, and deleted in any of the companies within the policy will be replicated immediately, across all the companies.
-   Fields that are not selected for sharing are maintained in each company and will not trigger any replication.
-   As part of enabling a policy, it is optional to copy any existing records.


Cross-company data sharing has the following limitations:

-   It can’t be used to share transactional data between companies.
-   Only reference and group data can be shared, or tables that have specifically been enabled. For example, **Data Sharing Type** is set to **Duplicate**.
-   It supports replication of fewer than one million total records per job. This total is calculated as the number of shared records × the number of shared companies. The limit is increased to two million records from the Platform Update for version 10.0.10.
-   It supports replication for up to 100 companies per policy. The limit is increased to 300 companies from the Platform Update for version 10.0.10.
-   Only one level of child relationships is exposed. To protect data consistency, replication doesn't occur if another level is required.
- 	Fields that reference Financial dimensions, for example **Ledger** or **Default** dimension, can't be shared across companies. 
      o	Dimensions hold a loose foreign key reference to the backing dimension data, which can reference both company-specific and non-company specific data. Determining the appropriate action to be taken for each dimension value has inherent complexity and would require a change from the current implementation, which could dramatically impact performance.
-   It can’t be used with [dual-write](../data-entities/dual-write/dual-write-home-page.md).


### Policies

Data sharing is managed by defined policies that are saved in data packages. Templates that Microsoft has tested and supports are available as downloadable data packages on Microsoft Dynamics Lifecycle Services (LCS). Policies let you control the following aspects of data sharing:

-   The fields that are replicated
-   The entities that participate in the replication
-   The companies that participate in the sharing

The same company and table can only be in one policy. It is possible to share the same table in more than one policy. This can happen when the limits of records or companies are reached, or to create policies for tables that need to be shared differently for different country/regions. 

> [!NOTE]
> Only required foreign key fields are selected by default. Optional foreign keys need to be selected manually to be included. The best practice is to add one or more tables when selecting a foreign key field, unless the table has already been added.

Policy templates that Microsoft has tested and supports are available as downloadable data packages on Lifecycle Services (LCS). 


> [!IMPORTANT]
> Although customers can modify the Microsoft data templates that are available from LCS, this scenario isn't supported.

### Conflict resolution

Validation rules are run when a sharing policy is enabled. If inconsistencies are detected, the user who implements the system can choose which records from which company should win.

### Considerations for successful data sharing

Several entities in the Microsoft data packages have references that you must consider when you enable the entities. Some data sharing policies can't be enabled if references don't match. Other policies can be enabled, but you should use the Find inconsistency checker tool to verify that your data is consistent. Here are some examples:

-   The Production group sharing policy has a reference to a company's chart of accounts. Therefore, all companies that are added to this sharing policy must use the same chart of accounts.
-   If you want to enable entities that use number sequences, the number sequence types must be the same across all companies in a sharing policy for those entities.
-   Setup options must be the same across the companies that are involved in the sharing policy. Examples of setup options include the setting that specifies whether tax is included by default.

## When should I use cross-company data sharing?
Use cross-company data sharing for the following business scenarios:

-   Sharing of simple reference and group data in a single deployment
-   Sharing among companies that have very similar configurations
-   Sharing scenarios that have been explicitly tested by Microsoft

Cross-company data sharing isn't supported for the following scenarios:

-   Franchising solutions, where thousands of records are shared across thousands of companies.
-   Sharing of transactional records for reporting or management purposes, such as consolidations.
-   Sharing across deployments.
-   Complex scenarios, such as replication of subtype/supertype tables or tables that have date effectivity rules.
-   Tables that do not have a unique index. 


## Customer and vendor master data sharing
Customer and vendor master data sharing allows you to share customer and vendor data across multiple companies. If you would like to be considered for this feature, complete the [Data sharing application](https://aka.ms/MSDYN365FODataSharing) and contact Support.

With the release of Platform update for version 10.0.12, customer and vendor master data sharing can be enabled using the **Customer and vendor master data sharing** feature in the **Feature management** module. There is no need to complete a survey first. It is important to consider limits in the number of records and companies stated above.

> [!NOTE]
> Default dimensions set up against a customer or vendor cannot be shared across companies. When configuring the customer or vendor record for cross-company data sharing, the **DefaultDimension** field is disabled, and cannot be included in the data sharing policy.

> Default dimensions hold a loose foreign key reference to the backing dimension data, which can reference both company-specific and non-company specific data. Determining the appropriate action to be taken for each dimension value has inherent complexity and would require a change from the current implementation, which could dramatically impact performance.

## Download a cross-company data sharing template from LCS
1.  Sign in to LCS.
2.  On the home page, click **Shared asset library**.
3.  In the **Asset type** list, click **Data package**.
4.  Click any of the available data package files to download them.

For details about how to use a template, see [Configure financial cross-company data sharing](../data-entities/tasks/configure-financial-cross-company-data-sharing.md).

## Currently supported cross-company data sharing templates
<table>
<thead>
<tr class="header">
<th>Package name on LCS</th>
<th>Data sharing policies</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Financial data sharing templates</td>
<td><ul>
<li>Bank parameters</li>
<li>Ledger journal names</li>
<li>Payment days</li>
<li>Payment schedules</li>
<li>Payment terms</li>
<li>Tax exempt codes</li>
</ul></td>
</tr>
<tr class="even">
<td>Supply chain data sharing templates</td>
<td><ul>
<li>Barcode parameters</li>
<li>Barcode setup</li>
<li>Buyer group</li>
<li>Charges group</li>
<li>Commission</li>
<li>Destination code</li>
<li>Non-conformance type</li>
<li>Order entry deadline group</li>
<li>Order origin code</li>
<li>Order pool</li>
<li>Production group</li>
<li>Production pool</li>
<li>Reason for delivery</li>
<li>Supplementary item group</li>
<li>Terms of delivery</li>
<li>Work time calendar</li>
</ul></td>
</tr>
</tbody>
</table>


## Additional resources

[Configure financial cross-company data sharing (Task guide)](../data-entities/tasks/configure-financial-cross-company-data-sharing.md)





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

