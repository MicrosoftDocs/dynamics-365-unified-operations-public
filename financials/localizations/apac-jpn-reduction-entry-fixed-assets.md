---
# required metadata

title: Set up reduction entries for fixed assets
description: This article provides information about reduction entries for fixed assets and how to set them up in Microsoft Dynamics 365 for Operations. Reduction entries are a special accounting treatment for fixed assets that you acquire by using a government subsidy. You can use them to defer the corporate income tax for those assets throughout their service life. 
author: rake-gui
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: AssetReductionEntryMassUpdate_JP, AssetReductionEntryProfile_JP
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 2871
ms.search.region: Japan
# ms.search.industry: 
ms.author: ralin
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Set up reduction entries for fixed assets

[!include[banner](../includes/banner.md)]


This article provides information about reduction entries for fixed assets and how to set them up in Microsoft Dynamics 365 for Operations. Reduction entries are a special accounting treatment for fixed assets that you acquire by using a government subsidy. You can use them to defer the corporate income tax for those assets throughout their service life. 

When you acquire a fixed asset by using a government subsidy, the subsidy is treated as taxable revenue. However, if you account for the whole government grant as revenue, the result is a large amount of corporate income tax, which reduces the subsidizing effect of the grant. Therefore, a special accounting treatment called a reduction entry is permitted. Basically, reduction entries defer the corporate income tax throughout the service life of the fixed asset that is acquired. Two types of accounting treatment are allowed:

-   **Direct-off method** – The amount of the government subsidy is deducted directly from the acquisition cost of the fixed asset.
-   **Reserve method** – The amount of the government subsidy is maintained as a separate value on the equity side of the balance sheet. The government subsidy amount doesn't affect the net book value of the fixed asset.

You can set up a fixed asset posting profile for reduction entries. You can also set up accounts for the transactions of the **Disposal** type. The transaction amounts are retrieved from these accounts when you post a fixed asset with a reduction entry.

## Prerequisites
The following table shows the prerequisites that must be in place before you start.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Category</th>
<th>Prerequisite</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Country/region</td>
<td>The primary address for the legal entity must be in Japan. Alternatively, the localized functionality region for the legal entity must be in Japan.</td>
</tr>
<tr class="even">
<td>Related setup tasks</td>
<td><ul>
<li>Make sure that you've set up basic fixed asset parameters, such as a default book, reason codes, and number sequences, on the <strong>Fixed assets parameters</strong> page.</li>
<li>Define a fixed asset group on the <strong>Fixed asset groups</strong> page.</li>
<li>Set up currencies and rounding rules to post depreciation amounts.</li>
<li>Set up fixed asset locations on the <strong>Fixed assets locations</strong> page.</li>
<li>Set up a fiscal calendar for depreciation, and assign the calendar to a ledger.</li>
<li>Make sure that you've created a fixed asset record.</li>
<li>Make sure that you've set up a book for the fixed asset on the <strong>Book </strong>page.</li>
</ul></td>
</tr>
</tbody>
</table>

Microsoft Dynamics 365 for Operations implements the reduction entry feature on top of existing fixed asset features. To use reduction entries, you must complete the following tasks in addition to using the existing fixed asset features.

### Assigning a reduction entry document to a fixed asset book

Use the **Fixed assets** page to assign a reduction entry document to a fixed asset.

### Assigning a reduction entry document to multiple fixed asset books

Use the **Mass update for reduction entry document** page to assign a reduction entry document to multiple fixed assets.

### Setting up a fixed asset posting profile for reduction entries

Use the **Fixed asset posting profiles** page to set up a posting profile for reduction entries. You can also set up a posting profile to depreciate the asset that is applied with a reduction entry.

## Technical information for system administrators
If you don't have access to the pages that are used to complete this task, contact your system administrator, and provide the information that is shown in the following table.

| Category           | Prerequisite                                                                                                                                               |
|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Configuration keys | Make sure that the **Asset configuration** key is available under the **Data Dictionary** &gt; **Configuration Keys** node in the Application Object Tree. |


