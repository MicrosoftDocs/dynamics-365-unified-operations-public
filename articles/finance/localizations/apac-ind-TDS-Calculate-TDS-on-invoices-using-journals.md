---
# required metadata

title: Calculate TDS on invoices using journals
description: This topic lists the steps for calculating Tax Deducted at Source (TDS) on invoices.
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

# Calculate TDS on invoices using journals

[!include [banner](../includes/banner.md)]

This topic lists the steps for calculating Tax Deducted at Source (TDS) on invoices.

Go to **General ledger > Journal entries > General journals**

[![General journals](./media/apac-ind-TDS-57.png)](./media/apac-ind-TDS-57.png)

1. Create journal lines using the journal forms that are listed in the table. Select the account type and offset account type and enter the amount for the transaction. 

   > [!Note]
   > In the **Invoice** **approval** **journal**  form, click the **Find vouchers** button and select invoices to  calculate TDS on. View the invoices created in the **Invoice** **register** form in the **Find vouchers** form.  

2. On the **General** tab of the **Journal** **voucher** form, in the **TDS** **group** field, view or modify the default TDS group defined for the vendor or customer. The TDS calculated on journal lines is based on the formula defined for the TDS tax codes in the TDS group. 

   > [!Note]
   > The **Withholding** **tax** **group**  field and the **TCS** **group** field become unavailable when you  select a TDS group in the **TDS** **group** field. The **Withholding**  **tax** **group** field is available only in the **General** **journal**  form.  TDS is calculated only if the **Calculate** **withholding**  **tax** check box is selected for the vendor or customer in the **Vendors**  form or **Customers** form.   

3. Click the **Tax** **information** tab. Under the **Company** **information** field group, in the **Name** field, view the company name. Select a company name of alternate addresses that are set up for the company in this field, if required. 

4. Under the **Withholding** **tax** field group, in the **Nature** **of** **assessee** field, view the nature of assessee category of the vendor or customer. In the **Tax** **Account** **Number** (**TAN**) field, view the TAN of the selected company name is displayed.  

5. Click **Withholding tax** in **Withholding tax** menu to open the **Temporary** **withholding** **tax** **transactions** form. The following fields are displayed on the upper pane of the **Temporary** **withholding** **tax** **transactions** form.

- **Withholding** **tax** **amount** **in** **total** field: The total TDS calculated for the transaction for the TDS group.

- **Value** field: The total percentage used to calculate TDS for the transaction. The total percentage is based on the formula that is defined for TDS tax codes attached to the TDS group.

- **Adjusted** **withholding** **tax** **amount** **in** **total** field: The total adjusted TDS amount for all tax codes in the TDS group.

- **TDS** check box: This check box is displayed as selected if a TDS group is attached to the transaction.

  The fields on the **Overview** tab, **General** tab, and **Adjustment** tab in the **Temporary** **withholding** **tax** **transactions** form display the calculated TDS amount and adjusted TDS amount details for each TDS tax code attached to the TDS group.

6. Click the **Threshold** button to open the **Threshold** form. View the threshold limit and exception threshold limit defined for the TDS tax component attached to a specific TDS tax code in this form.

   Click the **Formula** **designer** button to open the **Formula** **designer** form. View the formula defined for a specific TDS tax code in this form. Close the Formula designer form and Temporary withholding tax transactions form to return to the Journal voucher form.

8. Enter the other required details. Validate and post the journal. The TDS amount calculated on purchase invoices is posted to the payable account and the TDS amount calculated on sales invoices is posted to the receivable account that is defined for each TDS tax code in the TDS group. The payable accounts or receivable accounts for TDS tax codes are defined in the **Withholding** **tax** **codes** form.

9. Click **Posted withholding tax** button to open the **Withholding** **tax** **transactions** form. In the **Value** field, the total percentage used to calculate TDS for the transaction is displayed.

   The fields on the **Overview** tab, **General** tab, and **Amount** tab in the Withholding tax transactions form display the display the calculated TDS amount and adjusted TDS amount details for each TDS tax code attached to the TDS group.
