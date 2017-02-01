---
# required metadata

title: Data entities - Beginning balances | Microsoft Docs
description: This article provides a list of the data entities that are available for beginning balance functionality that is related to Budget control in Microsoft Dynamics 365 for Operations. If you're using Budget control, you must set it up and activate it before any balances are posted. Any transactional data that is posted before Budget control is activated won't be included.
author: kfend
manager: AnnBe
ms.date: 2016-11-17 16:06:00
ms.topic: reference
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: 51
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 96403
ms.assetid: c2c504c0-23ac-44b0-89b0-3dbdd0c0b085
ms.region: Global
# ms.industry: 
ms.author: kfend

---

# Data entities - Beginning balances

This article provides a list of the data entities that are available for beginning balance functionality that is related to Budget control in Microsoft Dynamics 365 for Operations. If you're using Budget control, you must set it up and activate it before any balances are posted. Any transactional data that is posted before Budget control is activated won't be included.

Suggested data entities to use to import beginning balances
-----------------------------------------------------------

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th>Entity name</th>
<th>Area</th>
<th>Entity type</th>
<th>Description</th>
<th>Notes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>General journal</td>
<td>General ledger</td>
<td>Transaction</td>
<td>Beginning balances for ledger accounts</td>
<td><ul>
<li>This entity exports all <strong>Journal line</strong> account types.</li>
<li>This entity imports only general journal lines of the <strong>Ledger - Ledger</strong> account type.</li>
<li>If a journal batch number exists in the target and matches the <strong>Journal batch number</strong> value in the source file, this entity imports to the existing journal batch number. If the journal batch number doesn't exist in the target, this entity generates a new journal batch number on insert.</li>
</ul></td>
</tr>
<tr class="even">
<td>Bank journal</td>
<td>Bank</td>
<td>Transaction</td>
<td>Beginning balances for bank accounts</td>
<td><ul>
<li>This entity exports and imports only general journal lines of the <strong>Bank - Ledger journals</strong> account type.</li>
<li>A composite entity can use XML format only.</li>
</ul></td>
</tr>
<tr class="odd">
<td>Customer invoice journal</td>
<td>Accounts receivable</td>
<td>Transaction</td>
<td>Beginning balances for customer accounts</td>
<td><ul>
<li>This entity exports and imports only general journal lines of the <strong>Customer - Ledger journals</strong> account type.</li>
<li>A composite entity can use XML format only.</li>
<li>There is a known issue where import is successful only if the <strong>Journal batch number</strong> value in the source file exists in Microsoft Dynamics 365 for Operations. To work around this issue, manually create the general journal batch number before you import the source file.</li>
</ul></td>
</tr>
<tr class="even">
<td>Vendor invoice journal</td>
<td>Accounts payable</td>
<td>Transaction</td>
<td>Beginning balances for vendor accounts</td>
<td><ul>
<li>This entity exports and imports vendor invoice journals.</li>
<li>A composite entity can use XML format only.</li>
</ul></td>
</tr>
<tr class="odd">
<td>Fixed asset journal</td>
<td>Fixed assets</td>
<td>Transaction</td>
<td>Beginning balances for fixed assets</td>
<td><ul>
<li>This entity exports and imports fixed asset journals.</li>
<li>If a journal batch number exists in the target and matches the <strong>Journal batch number</strong> value in the source file, this entity updates the existing journal batch number. If a journal batch number doesn't exist in the target, this entity generates a new journal batch number on insert.</li>
</ul></td>
</tr>
<tr class="even">
<td>Inventory movement journal</td>
<td>Inventory</td>
<td>Transaction</td>
<td>Beginning balances for inventory items</td>
<td><ul>
<li>This entity exports and imports inventory movement journals.</li>
<li>If a journal number is specified in the source file, the journal header must exist in Dynamics 365 for Operations, and it must have fewer than 1,000 lines to import. If a journal number isn't specified in the source file, a new journal is created for every 1,000 lines.</li>
</ul></td>
</tr>
<tr class="odd">
<td>Budget account entries</td>
<td>Budget</td>
<td>Transaction</td>
<td>Establish budget</td>
<td>This entity exports and imports the whole budget for the specified budgetary period.</td>
</tr>
</tbody>
</table>



See also
--------

[Data entities and packages framework](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/data-entities/using-data-entities-and-data-packages)

[Data entities home page](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/data-entities/data-entities-home-page)

