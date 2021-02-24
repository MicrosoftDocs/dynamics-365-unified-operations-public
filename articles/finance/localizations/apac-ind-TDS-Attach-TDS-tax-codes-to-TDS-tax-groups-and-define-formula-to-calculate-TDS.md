---
# required metadata

title: Attach TDS tax codes to TDS tax groups and define formula to calculate TDS
description: This topic lists the steps for setting up Tax Deducted at Source (TDS) tax groups and attaching TDS tax codes to TDS tax groups. To calculate TDS for the TDS tax group, you must define the formula for TDS tax codes that are attached to the TDS tax group.
author: kailiang
manager: AnnBe
ms.date: 02/12/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 15721
ms.assetid: b4b406fa-b772-44ec-8dd8-8eb818a921ef
ms.search.region: Global
# ms.search.industry: 
ms.author: kailiang
ms.search.validFrom: 2021-02-12
ms.dyn365.ops.version: AX 10.0.17

---

# Attach TDS tax codes to TDS tax groups and define formula to calculate TDS

[!include [banner](../includes/banner.md)]

This topic lists the steps for setting up Tax Deducted at Source (TDS) tax groups and attaching TDS tax codes to TDS tax groups. To calculate TDS for the TDS tax group, you must define the formula for TDS tax codes that are attached to the TDS tax group.

Complete the following steps to set up TDS tax groups, attach TDS tax codes to the TDS tax group, and define formula to calculate TDS.

 Begin by opening the **Withholding tax groups** page (**Tax > Indirect taxes > Withholding tax > Withholding tax groups**).

[![Withholding tax groups](./media/apac-ind-TDS-29.png)](./media/apac-ind-TDS-29.png)

1. Click **NEW** to create a withholding tax group for TDS and enter the required details.

2. In the **Tax** **type** field, select the **TDS** option.

3. Click the **Setup** tab and press Add Button to create a new line. In the **Withholding tax code** field, select the TDS tax code for the TDS tax group. In the **Withholding tax name** field and **Value** field, the name and the value for the TDS tax code are displayed. 

4. Select the **Overlook threshold** check box to ignore the threshold limit and exception threshold limit defined for the TDS tax component attached to the TDS tax code in TDS transactions.

5. Select the **Exempt** check box to prevent calculating the tax group in transactions. 

6. Click the **Designer** button to open the **Formula designer** form to define formula for calculation of TDS for the TDS tax group. The TDS tax codes that are selected for the TDS tax group are displayed on the **Taxes** tab of the **Formula designer** page. 

[![Designer](./media/apac-ind-TDS-30.png)](./media/apac-ind-TDS-30.png)

7. On the **Calculation** tab, press ALT+N to create a new line. In the **ID** field, the auto-generated priority ID for TDS calculation is displayed.

8. In the **Tax code** field, select the TDS tax code to define the formula for. The TDS tax codes that are selected for the TDS tax group are available for selection in this field.

9. In the **Taxable** **basis** field, select the basis to calculate TDS from the following options:

   - **Gross amount** – TDS is calculated on the gross transaction amount, that is, the invoice amount using the calculation expression defined for the tax code.

   - **Excl Gross amount** – TDS is calculated based on the calculation expression defined for the tax code.

      > [!NOTE]
      > Taxable basis cannot be set to **Excl Gross amount** for the TDS tax code with priority ID 1. 

10. Click the **+** button, **-** button, ***** button, or **/** button to insert the calculation expression for TDS tax code in the **Calculation** **expression** field. The TDS calculation is based on the formula defined in the **Calculation** **expression** field for the tax codes attached to the TDS tax group.

    > [!Note]
    > The calculation expression cannot be  defined for TDS tax code with priority ID 1.  

11. To define the calculation expression for the TDS tax code in the **Calculation** **expression** field, add TDS tax codes that are available on the **Taxes** tab using the drag-drop method, double click on the tax code, or right click on the tax code and select the **Add tax code** option.

>   [!Note]
>
>   Insert a calculation expression before  each TDS tax code.  View the TDS tax codes added to the calculation  expression within brackets.  

12. Click the **C** button to clear the calculation expression defined for a tax code in the **Calculation expression** field.

13. Click the **Delete** button to delete a record on the **Calculation** tab.

14. Close the page.
