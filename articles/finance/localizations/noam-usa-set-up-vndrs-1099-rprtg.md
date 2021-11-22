---
# required metadata

title: Set up vendors for 1099 reporting
description: This topic explains how to set up vendor records so that a 1099 box is associated with a main account. 
author: v-kiarnd
ms.date: 09/11/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: PSNCanadianHSTTaxFeature
audience: Application User
ms.devlang: 
ms.reviewer: roschlom
ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
ms.search.industry: public sector
ms.author: v-kiarnd
ms.search.validFrom: 2020-8-03
ms.dyn365.ops.version: 10.0.13
---

# Set up vendors for 1099 reporting

[!include [banner](../includes/banner.md)]

This topic explains how to set up vendor records so that a 1099 box is associated with a main account. It's best to complete these setup steps before you post vendor transactions. For more information, see [Year-end 1099 reporting](noam-usa-year-end-1099-reporting.md).

> [!NOTE]
> We recommend that you review Internal Revenue Service (IRS) rule changes for the applicable tax year before you set up and process 1099 statements.

Follow these steps to set up vendors for 1099 reporting.

1. Go to **Accounts payable \> Vendors \> All vendors** or **Procurement and sourcing \> Common \> Vendors \> All vendors**.
2. Select a vendor account.
3. On the **Tax 1099** FastTab, select the **Report 1099** option to include transaction and 1099 information for the vendor on the 1099 report. If this option isn't selected, 1099 information for the vendor won't be included on the 1099 report, and the electronic or magnetic files won't include amounts for the vendor.
4. In the **Federal tax ID** field, enter the vendor's taxpayer identification number. Then, in the **Tax ID type** field, select the type of tax ID that you just entered.

    > [!NOTE]
    > The **Prevent duplicate tax registration numbers** security privilege determines whether you can enter a taxpayer identification number that already been used in another vendor record.

5. In the **1099 box** field, enter the default value that should appear on every transaction line that is created for the vendor. This setting is required so that transactions for the vendor can be included on the 1099 report and in electronic or magnetic media files.
6. If the vendor organization is owned by an entity outside the United States, select the **Foreign entity indicator** option.
7. If your organization has been notified two times in three calendar years that the vendor provided an incorrect name, select the **Second TIN** check box.
8. In the **Name to use on the 1099** field, select **Vendor name**. If the vendor uses an alternate name, you can select **Doing business as**. In that case, enter the alternate name in the **DBA** field.
9. In the **Name control** field, enter the alphanumeric name control ID that the IRS requires to be printed on the mailing label to help validate the vendor's Employer Identification Number (EIN).
10. Select the **CUSIP** option to indicate that the Committee on Uniform Security Identification Procedures (CUSIP) identification number applies for the debt instrument.
11. In the **CUSIP ID** field, enter the nine-character alphanumeric CUSIP number to identify the debt instrument.
12. In the **CUSIP details** field, enter the abbreviation of the stock exchange and issuer, the coupon rate, and the year of maturity.

    > [!NOTE]
    > You can enter the CUSIP details only if the **CUSIP** check box is cleared.

13. In the **Nominee details** field, enter the names of the nominee and the issuer.
14. In the **Investor type** field, select the type of investor:

    - **None**
    - **Owner** – The investor is the owner of the debt instrument.
    - **Nominee/broker** – The investor is a broker who represents the owner of the debt instrument.

15. On the Action Pane, on the **Vendor** tab, in the **Setup** group, select **Vendor state tax IDs**.
16. Create a record for each state where the vendor receives payments from your organization. Enter the state tax ID. Additionally, if tax identification information is available, select the tax ID type.
17. If local income tax was withheld during the year, select the **Local income tax withheld** check box.
18. Close the pages to save your changes.

## Associate a 1099 default value with a main account

Some invoice lines that are identified for 1099 federal tax reporting might be reported for a different 1099 box than the vendor's default box. 

> [!Note]
> This functionality is available only if you're using Public sector. 

Because vendors can receive payments that correlate with multiple 1099 boxes, it's best to use a main account on a line for a funding distribution. This approach ensures consistent reporting of payments to a specific 1099 box. You can now recalculate the 1099 box values for vendors to more accurately report the accumulated balances to the IRS.

> [!NOTE]
> The 1099 box and amount can be filled in on the invoice only if the **Report 1099** check box on the **Tax 1099** FastTab of the vendor details page is selected.

1. Go to **Accounts payable \> Periodic tasks \> Tax 1099 \> 1099 main account association**.
2. In the **Main account number** field, select the main account to relate to a 1099 box. You can select only a main account of the **Expense** type.
3. In the **1099 box code** field, select the box code on the 1099 form that amounts that are posted to the selected main account should be associated with.
4. Repeat the preceding steps to add any other main accounts that are required.

## Update 1099 boxes and amounts

You can update the 1099 reporting boxes and amounts for all paid invoices for a calendar year, based on the current assignment of main accounts to 1099 boxes.

> [!Note]
> This functionality is available only if you're using Public sector. 

1. Go to **Accounts payable \> Periodic tasks \> Tax 1099 \> Update 1099 information by main account**.
2. Select a date range and a vendor, and then select **OK**.
3. Select **OK** to update the 1099 balances based on the main account, which are used for the vendor's posted and paid invoices.

The system evaluates any vendor where the **Report 1099** option selected. It then evaluates all the vendor's invoices. The 1099 amount is recalculated based on the main accounts on each line, including any line that has split distributions. If the line's fully paid amount isn't associated with the 1099 box, the line isn't included in the 1099 amount, as shown in the following examples:

- The vendor's default value for the 1099 box differs from the value that is specified on the invoice line.

    If one line on a vendor invoice uses a main account that is associated with 1099 box 7, and the default 1099 box for the vendor is a different number, the default entry for the vendor, and the amount that should be reported for it, will be recalculated for 1099 box 7.

- Not all invoice lines have 1099 box values.

   If one line on a vendor invoice uses a main account that is associated with 1099 box 7, and another line uses a main account that isn't associated with a 1099 box, the default entry for the vendor, and the amount that should reported for it, will be recalculated for 1099 box 7.

- Invoice lines have different 1099 box values.

     If one line on a vendor invoice uses a main account that is associated with 1099 box 7, and another line uses a main account that is associated with 1099 box 1, the system will ignore the default entry for the vendor, and the 1099 amount will be recalculated for the associated main accounts.

- The invoice has split distributions.

    If a vendor invoice includes a line that has split distributions, the default entry for the vendor will be recalculated for the 1099 box that is associated with the main account that is used in the distributions.

> [!NOTE]
> A new column that is named **Created by the 1099 update process** has been added to the **Tax 1099 transactions** page. The check boxes in this column are selected to show that the new update process updated the 1099 balance. If the check box for a row is cleared, standard functionality was used to create the transaction. To open the **Tax 1099 transactions** page, go to **Accounts payable \> Periodic tasks \> Vendor settlement for 1099s \> Vendor 1099 transactions**. Alternatively, go to **Accounts payable \> Vendors \> All vendors**, select a vendor, and then, on the Action Pane, on the **Vendor** tab, in the **Tax information** group, select **Vendor settlement for 1099s \> Vendor 1099 transactions**.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]