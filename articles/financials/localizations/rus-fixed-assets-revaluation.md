---
# required metadata

title: Fixed assets cost and depreciation revaluation (Russia)
description: 
author: anasyash
manager: AnnBe
ms.date: 10/28/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
ms.search.industry: 
ms.author: anasyash
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Fixed assets cost and depreciation revaluation (Russia)

[!include [banner](../includes/banner.md)]

The operation of changing the value of the fixed asset can be carried out by the organization independently, but not more often than once a year as of January 1 of the reporting year. Revaluation of fixed assets can also be carried out by decision of the state. Revaluation of fixed assets, as a rule, is accompanied by a revaluation of depreciation. The change in the value of an operating entity, as a result of FA value revaluation, can be made using the following methods:

-   Indexing - with the use of indices, usually set by the state. In this case, the initial value of the object and the amount of accrued depreciation are multiplied by the corresponding indices.

-   Direct recalculation (direct evaluation) - according to documented data on the market price of the facility. At the same time, the amount of depreciation is subject to indexation by the conversion factor, calculated as a result of the ratio of the new value of the object to the old value.

As a result of revaluation of FA cost (depreciation):

-   Ledger and fixed asset transactions are created. Fixed asset transactions are created with transaction types **Cost revaluation** and **Depreciation revaluation**

-   In the **Balance by FA** form the **Cost revaluation** and **Depreciation revaluation** fields are filled in and the value in the **Net book value** field is updated (increased or decreased by revaluation transaction values).

To revaluate fixed asset cost and depreciation, complete the following steps.

1.  Open the **FA revaluation (Fixed asset (Russia)** \> **Periodic journals** \> **FA revaluation**).

2.  Click the **New** button to create a new revaluation journal.

3.  The **Revaluation period** and **State on** are filled in automatically with the current period and date. You may update these fields (if needed). Value in the **State on** field is the date when depreciation revaluation is calculated from.

4.  Select fixed asset journal name. This journal name is used for creating FA journal when closing the revaluation journal.

5.  The **FA journal** field is filled in automatically according the number sequence setting, when closing the revaluation journal.

6.  Click the **Lines** button and select RAP value model in the **Revaluation lines creation** form. If necessary, set filter for selecting fixed assets for revaluation (**Records to include/ filter**). Then click OK button.

7.  In the **FA revaluation lines** form the system creates lines for fixed assets with the selected value model.

8.  **Net book value** is displayed In the **Balance cost** field and the fixed asset cost with revaluation is displayed in the **Replacement cost** field. Balance cost value corresponds to the value in **Net book value** field in **Balance by FA form** (**Fixed asset (Russia)** \> **Fixed assets** \> **Value models** \> **Balance**).

    > [!NOTE] You may enter **Replacement cost** manually (in this case the system  recalculates the factor) or enter the factor (in this case the system recalculates the replacement cost).

9.  If it is necessary, you may remove lines form the form or add new ones. To add a new line click the **New** button, select FA inventory number and value model in the **Revaluation lines creation** form and then click the **OK** button. If the value model is not specified in this form, the system creates lines for all value models which set up in the fixed asset.

10. To revaluate FA cost and depreciation with direct revaluation method, enter the FA market cost in the **Replacement cost** field.

11. To revaluate FA cost and depreciation of all fixed assets in this form, using Indexing method , click the Revaluation button.

12. Select the value model in the **Group revaluation** form, which the revaluation should be calculated for.

13. Enter the factor and set filter to select fixed assets for revaluation (**Records to include/ filter**). Then click the **OK** button. The **Factor** and Replacement cost fields are filled in for all lines.

14. Close the **FA revaluation lines** form.

15. Click the **Close** button in the **FA revaluation** form for confirming revaluation results. After FA revaluation journal is closing the FA journal is created, the FA journal number is filled in and **FA journal** button becomes active.

16. Click the **FA journal** button and then the **Lines** button. Revaluation transactions are displayed in the **Voucher transaction** form. If it is necessary, correct these transactions.

17. Click **Post** \> **Post** button to post the journal.

18. Validate balance in the value model (**Fixed asset (Russia)** \> **Fixed assets** \> **Value models** \> **Balance**). Values are updated in **Cost revaluation** and **Depreciation revaluation** fields.
