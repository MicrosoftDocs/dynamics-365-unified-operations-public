---
# required metadata

title: TDS calculation on invoices using free text invoice form
description: This topic describes the process for calculating Tax Deducted at Source (TDS) on invoices using the **Free** **text** **invoice** page.
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
# TDS calculation on invoices using free text invoice form

[!include [banner](../includes/banner.md)]

This topic describes the process for calculating Tax Deducted at Source (TDS) on invoices using the **Free** **text** **invoice** page.

 Go to **Accounts receivable > Invoices > All free text invoices**

[![Free text invoices](./media/apac-ind-TDS-57-1.png)](./media/apac-ind-TDS-57-1.png)

2. Click **New** to create a new free text invoice and enter the required details.

3. Click the **Invoice** tab. View the nature of the assessee of the customer in the **Nature of assessee** field under the **Withholding tax group** field group.

4. In the **TDS** **group** field, view or modify the default TDS group that's defined for the customer. 

> [!Note]
> The **TCS group** field will become unavailable when you select a TDS group in the **TDS group** field. TDS is calculated only if the **Calculate withholding tax** check box is selected for the customer on the **All customers** page.   

4. Open the **Tax information** tab. View the company name in the **Name** field under the **Company information** field group. Select the company name for an alternate address that's been set up for the company in this field.  

5. View the tax account number for the selected company in the **Tax Account Number (TAN)** field under the **Withholding tax** field group.

6. Create invoice lines on the **Invoice lines** tab and enter the required details. View the tax account number in the **Tax Account Number (TAN)** field under the **Withholding tax group** field group. In the **TDS group** field, view the TDS group.

7. Click the **Withholding tax** button to open **Temporary withholding tax transactions**. The following fields are displayed on the upper pane of the page.

   - **Withholding tax amount in total** field: The total TDS calculated for the transaction for the TDS group.
   - **Value** field: The total percentage used to calculate TDS for the transaction. The total percentage is based on the formula that's defined for TDS tax codes attached to the TDS group.
   - **Adjusted withholding tax amount in total** field: The total adjusted TDS amount for all tax codes in the TDS group.
   - **TDS** check box: This check box will be selected if a TDS group is attached to the transaction.

> [!Note]
> The fields on the **Overview** tab, **General** tab, and **Adjustment** tab on the **Temporary withholding tax transactions** page display the calculated TDS amount and details of the adjusted TDS amount for each TDS tax code that's attached to the TDS group.

8. Click the **Threshold** button to open the **Threshold** page. View the threshold limit defined for the TDS tax component attached to a specific TDS tax code.

9. Click the **Formula designer** button to open the **Formula designer** page. View the formula defined for a specific TDS tax code.

10. Post the free text invoice. The TDS amount that's calculated for the free text invoice is posted to the receivable account that is defined for each TDS tax code in the TDS group. The receivable accounts for TDS tax codes are defined on the **Withholding tax codes** page.

11. Click **Posted withholding tax** button to open the **Withholding tax transactions** page. View the total percentage used to TDS for the transaction in the **Value** field.

The fields on the **Overview** tab, **General** tab, and **Amount** tab on the **Withholding tax transactions** page display the TDS calculated on the invoice lines. View the TDS calculation information for each TDS tax code attached to the TDS group.
