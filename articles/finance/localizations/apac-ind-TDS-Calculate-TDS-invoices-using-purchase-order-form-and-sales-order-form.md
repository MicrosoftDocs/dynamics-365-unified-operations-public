---
# required metadata

title: Calculate TDS invoices using purchase order form and sales order form
description: This article lists the steps for calculating Tax Deducted at Source (TDS) on various types of invoices.
author: kailiang
ms.date: 02/12/2021
ms.topic: article
ms.prod: 

ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# 
# ms.tgt_pltfrm: 
ms.assetid: b4b406fa-b772-44ec-8dd8-8eb818a921ef
ms.search.region: Global
# ms.search.industry: 
ms.author: kailiang
ms.search.validFrom: 2021-02-12
ms.dyn365.ops.version: AX 10.0.17

---

# Calculate TDS invoices using purchase order form and sales order form

[!include [banner](../includes/banner.md)]

This article lists the steps for calculating Tax Deducted at Source (TDS) on various types of invoices using the **Purchase order**, **Purchase journal**, **Blanket order**, and **Sales order** pages.

1. Create a purchase order, purchase journal, purchase blanket order, or a sales order using the page listed. Enter the required details.

2. Select the **Setup** tab to view the nature of the assessee of the vendor or customer. This information is listed in the **Nature of assessee** field, under the **Withholding tax group** field group.

3. In the **TDS group** field, view or modify the default TDS group defined for the vendor or customer.

   > [!NOTE]
   > The **TCS group** field isn't available when you select a TDS group in the **TDS group** field. TDS is calculated only if the **Calculate withholding tax** check box is selected for the vendor or customer on the **All vendors** or **All customers** page.  

4. Create item lines on the **Lines** tab and enter the required details.

5. Select the **Setup** tab (line-level) to view or change the TDS group defined at the header-level. The TDS group is displayed in the **TDS group** field, which is under the **Withholding tax group** field group.

6. Select the **Tax information** tab and select alternate addresses that are set up for the company name that's displayed in this field. The company name is displayed in the **Name** field, which is under the **Company information** field group. 

   The TAN of the selected company name is displayed in the **Tax Account Number** (**TAN**) field, under the **Withholding tax** field group. 

7. Select **Withholding tax** to open the **Temporary withholding tax transactions** page. View the following fields on the upper pane of the **Temporary withholding tax transactions** page.

   - **Withholding** **tax** **amount** **in** **total** - The total TDS calculated for the transaction for the TDS group.

   - **Value** - The total percentage used to calculate TDS for the transaction. The total percentage is based on the formula that is defined for TDS tax codes attached to the TDS group.

   - **Adjusted withholding tax amount in total** - The total adjusted TDS amount for all tax codes in the TDS group.

   - **TDS** - If selected, a TDS group is attached to the transaction.

The fields on the **Overview**, **General**, and **Adjustment** tabs on the **Temporary withholding tax transactions** page display the calculated TDS amount and adjusted TDS amount details for each TDS tax code attached to the TDS group.

8. Select **Threshold** to open the **Threshold** page. View the threshold limit defined for the TDS tax component attached to a specific TDS tax code on this page.

9. Select **Formula designer** to open the **Formula designer** page. View the formula that is defined for a specific TDS tax code on this page. 

10. Post the invoice. The TDS amount calculated on purchase invoices is posted to the payable account and the TDS amount calculated on sales invoices is posted to the receivable account that is defined for each TDS tax code in the TDS group. The payable accounts or receivable accounts for TDS tax codes are defined on the **Withholding tax codes** page.

11. Select **Inquiry** button **> Invoice > Posted withholding tax** button to open the **Withholding tax transactions** page. You can view the total percentage used to calculate TDS for the transaction in the **Value** field.

The fields on the **Overview**, **General**, and **Amount** tabs on the **Withholding tax transactions** page display the information of TDS calculated for the transaction. View the TDS calculation information for each TDS tax code attached to the TDS group.
