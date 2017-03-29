---
# required metadata

title: Cross-company data sharing
description: This article provides information about cross-company data sharing. Cross-company sharing is a mechanism for sharing reference and group data among companies in a Microsoft Dynamics 365 for Operations deployment. This feature resembles the virtual companies feature in Microsoft Dynamics AX 2012.
author: RobinARH
manager: AnnBe
ms.date: 2016-06-06 22 - 00 - 56
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: SysDataSharingConfiguration
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
# ms.reviewer: 11
ms.search.scope: Core
# ms.tgt_pltfrm: 
ms.custom: 89071
ms.assetid: 0bbe7453-624f-4551-a1d0-842484067311
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: Platform update 1

---

# Cross-company data sharing

This article provides information about cross-company data sharing. Cross-company sharing is a mechanism for sharing reference and group data among companies in a Microsoft Dynamics 365 for Operations deployment. This feature resembles the virtual companies feature in Microsoft Dynamics AX 2012.

What is this feature and how does it work?
------------------------------------------

Cross-company data sharing lets you replicate (share) reference and group data among companies in a Dynamics 365 for Operations deployment. Data integrity is verified before replication occurs. 

Here are some examples of cross-company data sharing:

-   The same payment terms and payment day definitions are used across 15 legal entities.
-   The same terms of delivery are used across seven legal entities in three countries/regions.

Cross-company data sharing has the following limitations:

-   It can’t be used to share transactional data between companies.
-   Only reference and group data can be shared.
-   It supports replication of fewer than one million total records per job. (This total is calculated as the number of shared records × the number of shared companies.)
-   Only one level of child relationships is exposed. To protect data consistency, replication doesn't occur if another level is required.

### Policies

Data sharing is managed by defined policies that are saved in data packages. Templates that Microsoft has tested and supports are available as downloadable data packages on Microsoft Dynamics Lifecycle Services (LCS). Policies let you control the following aspects of data sharing:

-   The fields that are replicated
-   The entities that participate in the replication

**Important:** Although customers can modify the Microsoft data templates that are available from LCS, this scenario isn't supported.

### Conflict resolution

Validation rules are run when a sharing policy is enabled. If inconsistencies are detected, the user who implements the system can choose which records from which company should win.

### Considerations for successful data sharing

Several entities in the Microsoft data packages have references that you must consider when you enable the entities. Some data sharing policies can't be enabled if references don't match. Other policies can be enabled, but you should use the Find inconsistency checker tool to verify that your data is consistent. Here are some examples:

-   The Production group sharing policy has a reference to a company's chart of accounts. Therefore, all companies that are added to this sharing policy must use the same chart of accounts.
-   If you want to enable entities that use number sequences, the number sequence types must be the same across all companies in a sharing policy for those entities.
-   Setup options must be the same across the companies that are involved in the sharing policy. Examples of setup options include the setting that specifies whether tax is included by default.

## When should I use crosscompany data sharing?
Use cross-company data sharing for the following business scenarios:

-   Sharing of simple reference and group data in a single deployment
-   Sharing among companies that have very similar configurations
-   Sharing scenarios that have been explicitly tested by Microsoft

Cross-company data sharing isn't supported for the following scenarios:

-   Franchising solutions, where thousands of records are shared across thousands of companies.
-   Sharing of transactional records for reporting or management purposes, such as consolidations
-   Sharing across deployments
-   Complex scenarios, such as replication of subtype/supertype tables or tables that have date effectivity rules
-   Master data management

## Download a crosscompany data sharing template from LCS
1.  Sign in to LCS.
2.  On the home page, click **Shared asset library**.
3.  In the **Asset type** list, click **Data package**.
4.  Click any of the available data package files to download them.

For details about how to configure Dynamics 365 for Operations to use a template, see [Configure financial cross-company data sharing](http://ax.help.dynamics.com/en/wiki/configure-financial-cross-company-data-sharing/).

## Currently supported crosscompany data sharing templates
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
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



See also
--------

[Configure financial cross-company data sharing](http://ax.help.dynamics.com/en/wiki/configure-financial-cross-company-data-sharing/)

