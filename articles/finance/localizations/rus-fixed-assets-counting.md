---
# required metadata

title: Fixed asset counting (Russia)
description: This topic provides information about fixed asset counting for Russia.
author: ShylaThompson
ms.date: 09/18/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: RAssetTable, RAssetComponents
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Fixed asset counting (Russia)

[!include [banner](../includes/banner.md)]

The procedure for counting fixed assets is regulated by legislative acts and is one of the procedures that help control the safety of a company's property. Essentially, in fixed asset counting, the actual presence of values (money, equipment, buildings, and obligations) is compared with accounting data.

As a rule, fixed asset counting is done before the annual reporting. To register fixed asset counting, follow these steps.

1. Select **Fixed assets (Russia) \> Journals \> Periodic journals \> FA counting**.
2. Select **New** to create a journal.
3. In the **Counting start date** field, set a date.
4. In the **Fixed asset journal name** field, select a journal name. This journal name is used to create the Fixed asset journal when the counting journal is closed.
5. In the **FA location** field, enter the department that fixed asset counting is being done in.

    The **Counting end date** field is automatically set when the Fixed asset counting journal is closed. It can't be manually updated.

    The **Journal number** field is automatically set if the corresponding number sequence is set up and used in printing forms.

6. On the **General** tab, enter values in the **First responsible** and **Second responsible** fields.
7. On the **Setup** tab, set the **Quantity initialization by fact** option to **Yes**. The **Actual quantity** field is automatically set to the value of **Accounting quantity** field in the journal line when this option is set to **Yes**.
8. Select **Lines**.
9. In the **FA counting line creation** dialog box, in the **Accounting** field, select the value model that the fixed asset counting is being done on.
10. If you must select fixed assets for counting, on the **Records to include** FastTab, select **Filter**, and then set a filter.
11. Select **OK**. The **FA counting lines** page is opened. This page shows which fixed assets were found, based on the filter that you set.

    The **Accounting quantity** field shows the accounting quantity. This field is always set to **1**.

12. If you set the **Quantity initialization by fact** option to **Yes** in step 7, the **Actual quantity** field is automatically set to **1**, the value of **Accounting quantity** field. If you set the option to **No**, enter a value in the **Actual quantity** field.
13. If any fixed assets weren't found during the counting process, you must set the **Actual quantity** field to **0** (zero) for them. If any fixed assets were found but aren't listed on the **FA counting lines** page, you must create new lines for them. Previously, you had to create fixed asset record in the system (**Fixed assets (Russia)** \> **Fixed assets**).
14. On the **FA counting lines** page, select **New** to create a line.
15. In the **Counting lines creation** dialog box, in the **FA inventory number** field, select the fixed asset. In the **Value model** field, select the value model. Then select **OK**.
16. In the **Actual quantity** field, enter **1**.
17. When you've finished making corrections, close the **FA counting lines** page.
18. On the **FA counting** page, on the Action Pane, select **Close**.
19. In the **Closing of inventory journal** dialog box, specify the closing date and the value model.
20. Select **OK**.

    If there were line corrections, the **FA journal** button on the Action Pane of the **FA counting** page becomes available.

21. Select **FA journal** to open the Fixed asset journal, which includes the fixed asset transactions for posting.

    On the **Journal voucher** page, the transactions are automatically created. The transactions have a transaction type of **Writing-off** if they were not found during the counting process (but there is record in the system). If they were found but there is no record in the system, they have a transaction type of **Putting into operation**.

22. Select **Post** \> **Post**.
23. To view the posted transactions, on the **Journal voucher** page, select **Inquiries** \> **Transactions**.
22. On the **FA counting** page, select **Reports** to print reports. You can print the following reports:

    - **INV-1** is used to register the results of counting the company's fixed assets. During the counting process, the commission examines the fixed assets and fixes them in unified primary document form INV-1. 
    - **INV-1a** - is used to to register the results of counting the company's intangible assets.
    - **Collation statement** – INV-18 is a unified form that is used to document discrepancies between inventory results and accounting data on both fixed assets (FP) and intangible assets (NMA).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]