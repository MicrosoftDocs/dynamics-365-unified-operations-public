---
# required metadata

title: Fixed assets depreciation for Poland | Microsoft Docs
description: This topic provides information about fixed assets depreciation for legal entities in Poland.
author: ShylaThompson
manager: AnnBe
ms.date: 2016-12-16 21:17:30
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

keywords: AssetBook, AssetDepreciationGroup_W, AssetParameters, AssetPosting
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: 81
ms.suite: Released- Dynamics AX application 7.0.1
# ms.tgt_pltfrm: 
ms.custom: 264274
ms.assetid: 0afd95b2-d02d-4f51-83b8-34e21d0c6f4c
ms.region: Poland
# ms.industry: 
ms.author: v-elgolu

---

# Fixed assets depreciation for Poland

This topic provides information about fixed assets depreciation for legal entities in Poland.

The Fixed assets depreciation features that are based on legal requirements in Poland include:

-   Depreciation methods
-   Depreciation percent level
-   Depreciation groups
-   The same date, which is an option in the depreciation proposal to fill in the **Date** field value in all journal lines with a **To date** value that is defined in the Depreciation proposal.

## Polandspecific depreciation methods
For legal entities in Poland there are additional depreciation methods, rules, and settings that are used to meet specific fixed asset accounting requirements. According to Polish regulations, depreciation is calculated using a yearly depreciation rate. For more information about depreciation methods, see [Fixed asset depreciation](https://docs.microsoft.com/en-us/dynamics365/operations/financials/fixed-assets/fixed-asset-depreciation). The following depreciation methods are available for legal entities in Poland:

-   **Reducing balance (Poland)** – This depreciation method considers special local legal requirements about the value of fixed assets changing during the fiscal year and cost part recognition. The base for this depreciation method includes the following transaction types:
    -   Acquisition
    -   Acquisition adjustment
    -   Write up
    -   Write down
    -   Revaluation
    -   Previous depreciation
-   **Straight line (Poland)** – Depreciation is calculated for the first period based on the number of days that the asset was used. For example, if a fixed asset was purchased on January 15 and the depreciation period starts on January 1, depreciation will be calculated for half of the period. The base for this depreciation method includes the following transaction types:
    -   Acquisition
    -   Acquisition adjustment
    -   Write up
    -   Write down
    -   Revaluation
-   **Straight line percentage (Poland)** – The service life is calculated by entering a percentage and dividing 100 percent by the percentage entered. For example, if you entered 20 percent, 100 percent divided by 20 percent is 5 service years. The base for this depreciation method includes the following transaction types:
    -   Acquisition
    -   Acquisition adjustment
    -   Write up
    -   Write down
    -   Revaluation

For more information about depreciation methods, see [Fixed asset depreciation](https://docs.microsoft.com/en-us/dynamics365/operations/financials/fixed-assets/fixed-asset-depreciation).

## Depreciation percent level parameter
Reducing balance (Poland) and Straight line percentage (Poland) depreciation methods use the **Depreciation percent level** field on the **Fixed assets parameters** page. This field allows you to choose if the depreciation percent level should be taken from either the depreciation method or an individual fixed asset to calculate depreciation:

-   **Profile (standard)** – Select this option to use the percentage from the** **depreciation profile.
-   **Fixed asset book** –** ** Select this option to use the same depreciation method. The depreciation will be calculated using the percentage on the Fixed assets book.

## Depreciation groups
Legal entities in Poland can link fixed assets to depreciation groups. Depreciation groups are defined for a fixed asset book to specify fixed asset details such as increasing factor, alternative factor, or cost limit. If a depreciation group is assigned to a fixed asset, the depreciation group controls the depreciation amount, using an increasing factor by which the depreciation amount is multiplied. Create or edit the following depreciation groups on the **Depreciation group** page.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Field name</strong></td>
<td><strong>Description</strong></td>
</tr>
<tr class="even">
<td><strong>Start date</strong></td>
<td>Date that the Increasing factor and cost limit value will be used.</td>
</tr>
<tr class="odd">
<td><strong>Increasing factor</strong></td>
<td>Factor which multiplies the depreciation amount. An increasing factor can be set up if an alternative depreciation profile (alternative factor) or extraordinary depreciation profile (extraordinary factor) are used.</td>
</tr>
<tr class="even">
<td><strong>Alternative factor</strong></td>
<td>The alternative factor of the depreciation value.</td>
</tr>
<tr class="odd">
<td><strong>Cost limit</strong></td>
<td>Amount of acquisition price, which will be posted to a separate account for non-cost depreciation. Amounts to be posted to the account for non-cost depreciation are calculated during depreciation proposal, which splits the full depreciation calculation into two lines:
<ul>
<li><strong>(Adjusted) Depreciation</strong> -The full depreciation amount calculated based on fixed asset book setup minus the portion related to non-cost depreciation (Portion = Cost limit divided by Depreciation base). This depreciation is posted to accounts for depreciation.</li>
<li><strong>Non-cost part of Depreciation</strong> - A portion of depreciation related to the cost limit. This depreciation is posted to accounts for non-cost depreciation. To set up accounts for non-cost depreciation, open <strong>Fixed assets</strong> &gt; <strong>Setup</strong> &gt; <strong>Fixed asset posting</strong> profiles, and select <strong>Non-cost depreciation</strong> in the <strong>Ledger account</strong> FastTab.</li>
</ul></td>
</tr>
</tbody>
</table>

 

