---
# required metadata

title: Fixed assets counting (Russia)
description: This topic provides information about fixed assets counting for Russia.
author: ShylaThompson
manager: AnnBe
ms.date: 09/18/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Fixed assets counting (Russia)

[!include [banner](../includes/banner.md)]

The procedure for carrying out of counting fixed assets is regulated by legislative acts and is one of the procedures for control over the safety of the company's property. Its essence in comparison of actual presence of values (money, the equipment, buildings, and also obligations) with accounting data.

As a rule, counting fixed assets is carried out before the annual reporting. To count fixed assets, complete the following steps:

1.  Go to **Fixed Assets (Russia) \>Journals \> Periodic journals \> FA
    counting**.

2.  Press the **New** button for creating a new journal.

3.  Fill in **Counting start date** field.

4.  Select **Fixed asset journal name**, which will be created after FA counting journal.

5.  Fill in **FA location** field, the department, FA counting is executing in.

6.  The **Counting end date** field is filled in automatically when closing FA counting journal and not available for updating.

7.  The **Journal number** field is filled in automatically if the corresponding number sequence is set up and used in printing forms.

8.  Fill in **First responsible** and **Second responsible** fields on the **General** tab.

9.  On the **Setup** tab set **Quantity initialization by fact** option to **Yes**. In this case **Actual quantity** field is filled in automatically on **Accounting quantity** field.

10. Press the **Lines** button.

11. In the **FA counting line creation** form, in the **Accounting** field select the value model, the FA counting is executed on.

12. If it is necessary to select fixed assets for counting, press **Records to include/ Filter**.

13. Click OK. The **FA counting lines** page is open. On this page you may see, which fixed assets were found according to the set filter.

14. Accounting quantity is display in the **Accounting quantity** field. The value of this field is always equal to 1.

15. **Actual quantity** field. If **Quantity initialization by fact** option is set to **Yes** then this field value is always equal to 1, otherwise, this field should be filled in manually.

16. If any fixed assets were not found in the counting process then it is necessary to set zero for these fixed assets in the **Actual quantity** field, in the **FA counting lines** form.

17. If any fixed assets were found in the counting process and not listed in the **FA counting lines** form, then it is necessary to create new lines for them in this form. Previously it is necessary to create fixed asset cards in the system (**Fixed assets (Russia)** \> **Fixed assets**).

18. Use the **New** button to create a new line in the **FA counting lines** form. Select the fixed asset in the **FA inventory number** field and the value model, then press **OK**.

19. Enter actual quantity equal to 1.

20. Close the **FA counting lines** form after all corrections.

21. In the **FA counting** form press the **Close** button. Specify the closing date and the value model in the **Closing of inventory journal** form.

22. Click OK. If there were line corrections, the **FA journal** button be active.

23. Click **FA journal** to open the FA journal with FA transactions for posting.

24. On the **Journal voucher** page, the transactions are created automatically with **Write-off** and **Putting into operation** types (not found and found in the counting process).

25. Click **Post** \> **Post**.

26. You may check posted transactions, pressing **Inquiries** \> **Transactions** button in the **Journal voucher** form.

27. In the **FA counting** form press the **Reports** button to print reports.
    You may print the following reports:

    -   INV-1 serves for registration of the results of counting fixed assets of the company. In the counting process, the commission examines the fixed assets and fixes them in the unified primary document form of INV-1. Intangible assets are registered in INV-1a unified primary document form.

    -   Collation statement. INV-18 is a unified form that is used to document discrepancies between inventory results and accounting data on fixed assets (FP), as well as intangible assets (NMA).
