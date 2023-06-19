---
title: Construction Industry Scheme for the United Kingdom
description: The Construction Industry Scheme (CIS) is a scheme in the United Kingdom that specifies the rules that contractors and deemed contractors in the construction industry must follow when they make payments to subcontractors for construction work. This article describes functionality in Microsoft Dynamics 365 Finance that supports the requirements from these regulations.
author: AdamTrukawka
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: United Kingdom
ms.author: atrukawk
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.search.form: LedgerJournalTransVendPaym, TaxAuthority, TaxWithholdGroup, TaxWithholdItemGroup_TH, TaxWithholdPeriod_TH, TaxWithholdTable, VendTable
---

# Construction Industry Scheme for the United Kingdom

[!include [banner](../includes/banner.md)]

The Construction Industry Scheme (CIS) is a scheme in the United Kingdom that specifies the rules that contractors and deemed contractors in the construction industry must follow when they make payments to subcontractors for construction work. This article describes functionality that supports the requirements from these regulations.

The Construction Industry Scheme (CIS) is a scheme that is issued by Her Majesty’s Revenue & Customs (HMRC) in the United Kingdom. CIS specifies the rules that contractors and deemed contractors in the construction industry must follow when they make payments to subcontractors for construction work. Deemed contractors are organizations that don't have construction as their core business, but their annual spending on construction is high. The contractors and deemed contractors must complete these steps:

-   Register with HMRC as contractors or deemed contractors.
-   Verify the employment status of the subcontractors, verify that the subcontractors are registered with HMRC, and verify the tax status of the subcontractors.
-   Make payments to the subcontractors, and make the deductions that are specified under CIS.
-   Pay HMRC the amount that is deducted from the subcontractor payments.
-   Issue payment and deduction statements to the subcontractors.
-   Send HMRC a monthly return statement that has the details of the payments and deductions.
-   Maintain records of the details of the payments and deductions. The records must include the following information:
    -   The gross amount (excluding value-added tax \[VAT\]) of each payment that was made to a subcontractor.
    -   The amount of any deductions that the contractor withheld from a payment before it made the payment.
    -   The amount (excluding VAT) of any material costs, if the contractor made a deduction.

## CIS deductions from subcontractor payments
You must complete the following setup before you make CIS deductions from subcontractor payments:

-   On the **Withholding tax authorities** page, set up a withholding tax authority for HMRC, and specify **English report layout** as the report layout.
-   On the **Withholding tax settlement periods** page, create a settlement period for CIS that uses monthly intervals. You must also add the HMRC tax authority to the settlement period.
-   On the **Item withholding tax groups** page, create an item withholding tax group for CIS, and assign the withholding tax codes that you created for CIS to the group.
-   Set up a legal entity as a CIS contractor, and specify **Account office reference**.
-   Set up a ledger posting group for CIS, and specify ledger accounts for **Withholding tax payable**, **Withholding tax receivable**, and **Withholding tax settlement** postings.
-   On the **Withholding tax codes** and **Withholding tax values** pages, set up withholding tax codes for CIS, and specify the deduction rates. You must set up withholding tax codes for the deduction rates that can be applied to the subcontractors, based on the verification information that you receive for the subcontractors from HMRC. The following deduction rates can be applied:
    -   **Gross deduction** – No deductions are made from the payments.
    -   **Standard deduction** – Deductions are made from the payments at the standard rate of 20 percent.
    -   **Higher deduction** – Deductions are made from the payments at a higher rate, 30 percent. This rate is applied when the subcontractor isn't registered or could not be verified with HMRC.
-   On the **Withholding tax groups** page, create withholding tax groups, and assign the withholding tax codes that you created for CIS to the group.
-   On the **Vendors** page, set up a vendor as a CIS subcontractor by entering the verification information that you received from HMRC. You must verify the status of the subcontractor with HMRC before you can set up the vendor as a CIS subcontractor, and then select one of following options in the **Status** field:
    -   **None** – This is the default option for a new vendor that isn't a registered subcontractor with CIS.
    -   **Gross** – No deductions are made from the payments.
    -   **Standard** – Deductions are made from the payments at the standard rate of 20 percent.
    -   **Higher** – Deductions are made from the payments at a higher rate, 30 percent. This rate is applied when the subcontractor isn't registered or could not be verified with HMRC.
-   Create a released product that includes withholding tax information.
    -   On the **New released product** page, create a released product that withholding tax is calculated for, and select the default item withholding tax group that applies to the released product.
    -   On the **Released products** page, specify whether the withholding tax is calculated for an existing released product, and select the default item withholding tax group that applies to the released product.
-   On the **Procurement categories** page, set up withholding tax information for a procurement category hierarchy. Specify whether the withholding tax is calculated for a procurement category hierarchy, and select the default item withholding tax group that applies to the products in the selected category.

## Working with CIS
Complete the following procedures to make CIS deductions from the payments that are made to subcontractors, settle the withholding taxes, generate the monthly CIS report for a subcontractor and HMRC, and correct posted withholding taxes.

### Make a payment to a subcontractor and settle an invoice

Use the **Vendor payments** page to make payments to a subcontractor that include the deductions that are specified by CIS, and settle the invoices. When you make the payments, the deductions are calculated and deducted based on the CIS deduction rate that is specified for the vendor and the withholding tax group that is assigned to the vendor. After you settle the invoice, you can generate the withholding tax slip/statement to the subcontractor. This statement includes the details of the payments and CIS deductions. You must create and post a purchase order before you can make a payment and settle an invoice. To make a payment, settle an invoice, and print the statement to the subcontractor, follow these steps:

-   Make a payment to the subcontractor that includes the deductions that are specified by CIS, and settle the invoice, on the **Vendor payment** page.
-   Print the statement to that subcontractor after you make the payment and settle the invoice. On the **Vendor payment** page, click **Print** &gt; **Statement to subcontractors**. The statement includes information about the payment that was made to the subcontractor and the deductions.

### Generate the monthly CIS statement for a subcontractor

Use the **Vendor monthly CIS statement** report to generate the monthly CIS statement for a subcontractor. The monthly CIS statement includes the details of the payments that were made to the subcontractor and the details of the deductions.

### Settle the withholding taxes and generate the monthly CIS statement for HMRC

Use the **Withholding tax payments** page to settle the withholding taxes to a withholding tax settlement account. The amount that is settled to the withholding tax settlement account is the amount that must be paid to HMRC. You can use the **CIS monthly statement** report to generate the monthly return statement that includes the details of the payments and deductions. The monthly return statement is submitted to HMRC. **Note:** You can open the **CIS monthly statement** report only if **English report layout** is selected as the report layout for the withholding tax authority for the settlement period on the **Withholding tax authorities** page.

### Correct posted withholding taxes

Use the **Undo settlement**, **Vendors**, and **Vendor payments** pages to correct the posted withholding taxes.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
