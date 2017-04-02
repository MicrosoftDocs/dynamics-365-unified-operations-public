---
# required metadata

title: Fixed assets disposal for Poland
description: This topic provides information about fixed asset disposal functionality for users in legal entities in Poland. 
author: ShylaThompson
manager: AnnBe
ms date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: AssetParameters, AssetPosting, CustFreeInvoice, LedgerJournalTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 81
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 266964
ms.assetid: 99f3a20c-2e2e-4fc7-b846-3d86802174c4
ms.search.region: Poland
# ms.search.industry: 
ms.author: v-elgolu
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1

---

# Fixed assets disposal for Poland

This topic provides information about fixed asset disposal functionality for users in legal entities in Poland. 

Fixed assets can be sold using disposal functionality through a free text invoice, fixed asset journal, or general journal in General ledger. For more information about fixed asset disposal, see [Fixed asset disposal posting accounts](../fixed-assets/fixed-asset-disposal-posting-accounts.md). For users in legal entities in Poland, the fixed assets disposal functionality extension includes:

-   A template for asset disposal on the **Fixed asset posting profiles** page.
-   Two additional parameters on the **Permission to sell fixed asset** page. A **Check whether asset can be sold** check box and a **Permission to sell fixed asset** check box on the **Reference and notes** FastTab of a fixed asset. If the **Check whether asset can be sold** check box is selected, only assets marked as **Permission to sell fixed asset** can be sold.
-   A sales account for fixed assets disposal, which includes an additional parameter on the **Sales** FastTab on the **Fixed assets parameters** page. Use this parameter to set up a default ledger account for posting of fixed asset sales.
-   An additional field on the** Partial disposal** page for users to enter a percentage. This percentage will be used for calculation of a line amount as a selected fixed asset net book value multiplied on the percentage.

## Templates for fixed asset disposal
You can use a template for fixed asset disposal as an option to simplify setting up accounts for asset disposal for posting profiles. To create or edit a template for fixed asset disposal, complete the following steps.

1.  Click **Fixed assets** &gt; **Setup** &gt; **Fixed asset posting profiles**.
2.  In the **Disposal** section, click **Create template** and select a fixed asset posting profile.
3.  Complete the following fields
    |                    |                                                                                                                                |
    |--------------------|--------------------------------------------------------------------------------------------------------------------------------|
    | **Field**          | **Description**                                                                                                                |
    | **Book**           | Select the book that you want to set up or update posting accounts for asset disposal.                                         |
    | **Main account**   | The selected account will automatically be used as **Main account** in setup or update of accounts for disposal posting.       |
    | **Offset account** | The selected account will automatically be used as the **Offset account** in setup or update of accounts for disposal posting. |
    | **Overwrite**      | If selected, the system will replace existing disposal accounts for the selected **Book**.                                     |

4.  Click **OK**. The system automatically creates or updates posting rules for the selected book for the following fixed asset disposal components (transaction types):
    -   Depreciation (prior years)
    -   Depreciation (this year)
    -   Depreciation adjustment (prior years)
    -   Depreciation adjustment (this year)
    -   Extraordinary depreciation (prior years)
    -   Extraordinary depreciation (this year)
    -   Accumulated depreciation (last years)
    -   Accumulated depreciation (this year)
    -   Revaluation of accumulated depreciation (last years)
    -   Revaluation of accumulated depreciation (this year)

## Permission to sell
Permission to sell functionality extends basic disposal by sale functionality for users in legal entities in Poland with two additional parameters:

-   **Check whether asset can be sold** – Use this check box to activate an additional filter on the lookup field when selecting a fixed asset to be sold in a free text invoice or a journal line. The additional filter affects transactions with type **Disposal - sale** only. To edit the **Check whether asset can be sold** field, open the **Sale** FastTab on the **Fixed assets** &gt; **Setup** &gt; **Fixed assets parameters** page.
-   **Permission to sell fixed asset** – Use this check box to select whether an individual parameter for each fixed asset can be sold. To edit this field, open the **Reference and notes** FastTab for the selected fixed asset.

## Sales account for fixed assets disposal
When a sales disposal transaction is created using a fixed asset journal or general journal in General ledger, a sales account defaults to the journal line from the setup on the **Fixed asset posting profiles** page. When a sales disposal transaction is created using a free text invoice, a user should fill in the **Main account** field with a sales account. Sales account for fixed assets disposal functionality lets users in legal entities in Poland set up a ledger account which will be taken as a sales account for sales disposal transaction created using a Free text invoice, by default. To set up a sales account for fixed assets disposal, open the **Sale** FastTab on the **Fixed assets** &gt; **Setup** &gt; **Fixed assets parameters** page.

## Partial sales of fixed assets
A sale or scrap disposal of a fixed asset allows disposal of an entire fixed asset only. Partial sales of fixed assets functionality allows users in legal entities in Poland to dispose partially of a fixed asset through both sale or scrap types of transactions. Partial sale of fixed assets is available through a free text invoice, fixed asset journal or general journal in General ledger. To partially dispose a fixed asset, enter a percentage (an integer between 0 and 100) in the **Partial sales** field in one of the following locations:

-   **General** tab on the **Fixed asset journal** line.
-   **Fixed assets** tab on the **General journal** line.
-   **General** tab on the **Free text invoice** line.

By default, the **Partial sales** field value is **100**. When a user selects the **Disposal scrap** or **Disposal sale** transaction type and an asset in a journal, the net book value will default on the journal line. If the user changes the percentage, the net book value on the journal line is reduced. The user can also manually change the net book value, after which the percentage in the **Partial sales** field will be recalculated. **Example** A fixed asset has been acquired at USD 10.000, depreciation USD 1.000, net book value USD 9.000. First partial sale 50% - net book value calculated for the journal line is 50% of USD 9.000 = USD 4.500. Second partial sale 50% - net book value calculated for the journal line is 50% of the remaining net book value USD 4.500 = USD 2.250. If a user wants to expense the remaining net book value of USD 2.250, he must enter a percentage of 100 on a journal or a free text invoice line.

