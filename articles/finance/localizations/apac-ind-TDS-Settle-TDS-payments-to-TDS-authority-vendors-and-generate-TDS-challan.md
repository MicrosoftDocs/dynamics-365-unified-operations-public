---
# required metadata

title: Settle TDS payments to TDS authority vendors and generate TDS challan
description: This topic lists the steps for settling Tax Deducted at Source (TDS) payments to TDS authority vendors.
author: kailiang
manager: AnnBe
ms.date: 03/12/2021
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

# Settle TDS payments to TDS authority vendors and generate TDS challan

[!include [banner](../includes/banner.md)]

This topic lists the steps for settling Tax Deducted at Source (TDS) payments to TDS authority vendors.

Begin by opening the **Vendor payment journal** page (**Accounts payable > Payments > Vendor payment journal**).

[![Vendor payment journal](./media/apac-ind-TDS-51.png)](./media/apac-ind-TDS-51.png)

1.  Click **New** to create a journal line. In the **Account** field, select the TDS authority vendor to settle TDS payments to.

2. Click **Settlement transactions** to open the **Settlement transactions** page to view the settled TDS transactions for the TDS authority vendor.

3. The settled TDS transactions for a settlement period are displayed as follows.

- The TDS transactions with **Company** as the nature of assessee are displayed as one transaction line.
- The TDS transactions with **HUF**, **Firm**, **Individual**, **AOP**, **BOI**, **Local** **authority**, or **Others** as the nature of assessee are displayed as one transaction line.
- In the **Amount** field, the total TDS amount that is due to be paid to the TDS authority vendor is displayed.

4. Click the **Withholding tax transactions** button to view the different TDS transactions that are included for the settlement record. View the split of each TDS transaction that has been included in the settlement process for the settlement period in this page.

5. On the **Overview** tab, select the **Mark** check box for TDS transactions to settle to the TDS authority vendor. View the information for the open TDS transactions in the following fields.

- **Date**: The TDS transaction date.
- **Voucher**: The voucher number.
- **Source** The module that the TDS transaction is posted in.
- **Vendor/Customer**: The vendor or customer account number that the TDS is deducted from.
- **Name of deductee/party**: The vendor or customer name that the TDS is deducted from.
- **Nature of assessee**: The nature of the assessee category that the deductee belongs to.
- **Amount**: The invoice amount that the TDS is calculated on.
- **Tax amount**: The TDS amount calculated for the transaction.

> [!Note]
> Clear the **Mark** check box for  TDS transactions that should not be settled to the TDS authority vendor.  

6. On the **General** tab, in the **PAN** field, the PAN of the deductee is displayed. In the **Date** field, the date of TDS calculation is displayed and in the **Value** field, the total percentage used for TDS calculation is displayed.

7. Click the **Voucher** button to view the voucher entries for the TDS transaction.

8. Close the page.

9. Click the **Withholding tax components** button to view the TDS calculated per TDS tax component for a specific TDS tax code. On the **Overview** tab, in the **Tax** **component** field, view the TDS tax component used for the transaction.

10. In the **Amount** field, view the TDS amount calculated in base currency for the TDS tax component. In the **Accumulated amount** field, view the total TDS amount calculated for the TDS tax component for all settled transactions.

11. In the **Amount** tab, view the TDS amount calculated for the TDS tax component in default currency and secondary currency under the **Default currency** field group and **Secondary currency** field group. Close the **Withholding tax components** page.

12. In the **Amount** field in the **Open transaction editing** page, the total amount to settle to the TDS authority vendor for the settlement period is updated. Select the **Mark** check box to select the transactions of different TDS settlement periods to settle to the TDS authority vendor. Close the **Open transaction editing** page.

>   [!Note]
>   If only a few transactions are selected for settlement on the **Withholding tax transactions** page,  the total TDS amount of the selected transactions is updated in the **Correction**  field in the **Open transaction editing** page. The  correction amount is updated on the journal line in the **Journal voucher** page and the **Open transaction editing** page is closed.  

13. In the **Debit** field in the **Journal voucher** page, view the total amount to pay to the TDS authority vendor. Enter the offset account details. If TDS transactions have different Tax Account Numbers (TAN), journal lines are created per TAN on the **Journal voucher** page.

14. On the **Payment fee** tab, in the **Fee ID** field, select a fee ID with **Interest** or **Others** type of fee type to charge payment fee for delayed payments made to the TDS authority vendor.

15. Click the **Tax information** tab. Under the **Company information** field group, in the **Name** field, view the company name. Under the **Withholding tax** field group, in the **Tax Account Number (TAN)** field, view the TAN attached to the transaction line. 

16. Validate and post the journal.

17. Click **Withholding tax button > challan information** to enter the challan details for the transaction.

18. In the **Voucher** field, the voucher number of the transaction is displayed. Select the **TDS deposited by book entry** check box if the TDS amount is deposited using book entry.

19. In the **Challan number** field, enter the challan number used to make the payment to the TDS authority vendor. In the **Date** field, enter the challan date.

20. In the **Bank name** field, select the bank name to deposit the TDS amount that's payable to the TDS authority vendor. The bank accounts that were set up for the TDS authority vendor in **Accounts payable > All vendors > Set up > Bank accounts** are available for selection in this field.

21. In the **BSR code** field, enter the Basic Statistical Return (BSR) code of the bank. 

22. Close the page. 

### Example:

Suppose that the period 04/01/2009 is settled for the TDS component group-Rent using the periodic TDS settlement process. The total TDS amount of 141625.00 is posted to TDS vendor authority account for the TDS settlement period. You can view this amount in the **Amount** field in the **Open transaction editing** page for the TDS authority vendor.

If yiu click the **Withholding tax transactions** button to view the different TDS transactions settled for the period, the following information is displayed:
 

| TDS  amount |
| ----------- |
| 16,995.00    |
| 22,660.00    |
| 28,325.00    |
| 16,995.00    |
| 28,325.00    |
| 16,995.00    |
| 11,330.00    |

For a specific TDS amount, click the **Withholding tax components** button to view the TDS calculated per TDS tax component for a specific TDS tax code. When you click the **Withholding tax components** button for the TDS amount 16,995.00, the tax amount calculated per component for the transaction is displayed as follows:

| Tax component | Amount   | Accumulated amount |
| ------------- | -------- | ------------------ |
| TDS           | 1,5000.00 | 125,000.00          |
| Surcharge     | 1,500.00  | 12,500.00           |
| PE-Cess       | 330.00   | 2,750.00            |
| SHE Cess      | 165.00   | 1,375.00            |

 

If only the TDS amounts 16,995.00, 22,660.00, and 2,8325.00 are selected for settlement in the **Withholding tax transactions** page, the total amount for settlement is displayed as 67,980.00 in the **Correction** field in the **Open transaction editing** page. If this transaction is marked for settlement and the **Open transaction editing** page is closed, the amount 67,980.00 is displayed in the **Debit** field in the **Journal voucher** page. Now, you can post the journal and generate the TDS challan.

### **Adjustment of Advance Payments made to TDS Authority Vendors**

An advance payment made to the TDS authority vendor is adjusted to an actual payment using **Accounts payable > Vendors > All vendors > Transactions editing**. If the actual payment made is greater than the advance payment, two challan numbers are generated for the transaction. However, only the first challan number is displayed in the TDS inquiry.
