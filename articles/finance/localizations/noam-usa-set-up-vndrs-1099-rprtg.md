---
# required metadata

title: Set up vendors for 1099 reporting
description: This topic describes the steps for setting up vendor records to associate a 1099 box with a main account. 
author: v-kiarnd
manager: Ann Beebe
ms.date: 08/3/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: PSNCanadianHSTTaxFeature
audience: Application User
ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Operations, Core 
ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
ms.search.industry: public sector
ms.author: v-alpavk
ms.search.validFrom: 2020-8-03
ms.dyn365.ops.version: 10.0.13
---

# Set up vendors for 1099 reporting

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic describes the steps for setting up vendor records to associate a 1099 box with a main account. It's best to complete these setup steps before posting vendor transactions. For more information, see [Year-end 1099 reporting](noam-usa-year-end-1099-reporting.md).

> [!Note]
> We recommend that you review Internal Revenue Service (IRS) rule changes for the applicable tax year before you set up and process 1099 statements.
Complete the following steps to set up vendors for 1099 reporting. 

1. Go to **Accounts payable > Vendors > All vendors or Procurement and sourcing > Common > Vendors > All vendors**.
2. Select a vendor account, and then open the **Tax 1099** FastTab.
3. Select the **Report 1099** option to include transaction and 1099 information for the vendor on the 1099 report. If this isn’t selected, 1099 information for the vendor won’t be included on the 1099 report, and the electronic or magnetic files won’t include amounts for the vendor.
4. In the **Federal tax ID** field, enter the taxpayer identification number for the vendor. In the **Tax ID** type field, select the type of tax ID that you used in the **Federal tax ID** field.

  > [!Note]
  > The **Prevent duplicate tax registration numbers** security privilege determines whether you can enter a tax identification number that already been used on another vendor record.

5. In the **1099 box** field, enter the default value that appears on each transaction line that is created for the vendor. This is necessary to include transactions for the vendor on the 1099 report and in electronic or magnetic media files.
6. If the vendor organization is owned by an entity outside the United States, select the **Foreign entity indicator** option.
7. If your organization has been notified twice within three calendar years that the vendor provided an incorrect name, select the **Second TIN** check box.
8. In the **Name to use on the 1099** field, select **Vendor name**. You can select **Doing business as** if the vendor uses an alternate name. If you select **Doing business as**, enter the alternate name in the **DBA** field.
9. In the **Name control** field, enter the alphanumeric name control ID that the IRS requires to be printed on the mailing label to help validate the vendor’s Employer Identification Number (EIN).
10. Select the CUSIP option to indicate that the Committee on Uniform Security Identification Procedures (CUSIP) identification number applies for the debt instrument.
11. In the **CUSIP ID** field, enter the nine-character alphanumeric CUSIP number to identify the debt instrument.
12. In the **CUSIP details** field, enter the abbreviation of the stock exchange and issuer, coupon rate, and year of maturity.

  > [!Note]
  > You can enter the CUSIP details only if the **CUSIP** check box is not selected.
  
13. In the **Nominee details** field, enter the names of the nominee and issuer.
14. In the **Investor type** field, select the type of investor from the following options:
    - **None**
    - **Owner** – The owner of the debt instrument.
    - **Nominee/broker** – A broker who represents the owner of the debt instrument.

15. On the Action Pane, on the **Vendor** tab under setup, click **Vendor state tax IDs**.
16. Create a record for each state in which the vendor receives payments from your organization. Enter the state tax ID and, if tax identification information is available, select the tax ID type.
17. If local income tax was withheld during the year, select the **Local income tax withheld** check box.
18. Close the pages to save your changes.
 
## Associate a 1099 default value with a Main account
Some invoice lines that are identified for 1099 Federal tax reporting might be reported for a different 1099 box than the vendor’s default box. Because it’s possible for vendors to receive payments that correlate with multiple 1099 boxes, using a main account on a line for a funding distribution is optimal for consistently reporting payments to a specific 1099 box. You can now recalculate the 1099 box values for vendors to more accurately report the accumulated balances with the IRS.

> [!Note]
> The Report 1099 check box, on the Tax 1099 FastTab of the vendor details form, must be selected for the 1099 box and amount to be populated on the invoice.

1.	Go to **Accounts payable > Periodic tasks > Tax 1099 > 1099 main account association**.
2.	In the **Main account number** field, select the main account to relate to a 1099 box. You can only select an Expense type main account.
3.	In the **1099 box code** field, select the box code on the 1099 form that the amounts posted to the specified main account should be associated with.
4.	Repeat the preceding steps as needed to add additional main accounts.


## Update 1099 boxes and amounts
You can refresh the 1099 reporting boxes and amounts for all paid invoices for a calendar year according to the current main account assignments to 1099 boxes. 

1. Go to **Accounts payable > Periodic tasks > Tax 1099 > Update 1099 information by main account**.
2. Select a date range and vendor, and then click **OK**.
3. Click **OK** to update the 1099 balances based on the main account, which are used for the vendor’s posted and paid invoices.

The system evaluates any vendor that has the **Report 1099** option selected, and then evaluates all of the vendor's invoices. The 1099 amount is recalculated based on the main accounts on each line (including split distributions if applicable). If the line’s fully paid amount is not associated with the 1099 box, the line is not included in the 1099 amount, as shown in the following examples:

  - Vendor’s default value for 1099 box is different than the one specified on the invoice line <br>
    If one line on a vendor invoice uses a main account that's associated with 1099 box 7, and the default 1099 box for the vendor is a different number, the default for the vendor, and the amount that should be reported for it, will be recalculated for 1099 box 7.
  - Not all invoice lines have 1099 box values <br>
    If two lines on a vendor invoice use one using a main account that's associated with 1099 box 7, and a second line that uses a main account that's not associated with a 1099 box, the default entry for the vendor and the amount that should reported for it, will be recalculated for 1099 box 7.
  - Invoice lines have different 1099 box values <br>
    If one line in a vendor invoice uses a main account associated with 1099 box 7, and another line uses a main account associated with 1099 box 1, the system will ignore the default entry for the vendor, and the 1099 amount be recalculated for the associated main accounts.
  - Invoice has split distributions <br>
    If a vendor invoice includes a line with split distributions, the default entry for the vendor will be recalculated for the 1099 box associated with the main account used in the distributions.
    
> [!Note]
> A new column named Created by the 1099 update process, with check boxes is added to the Tax 1099 transactions page, to show whether the new update process updated the 1099 balance, or the transaction was created with standard functionality. You can locate the form by selecting **Accounts Payable > Periodic tasks > Vendor settlement for 1099s > Vendor 1099 transactions** or **Accounts Payable > Vendors > All vendors > Vendor >** Action Pane, **Vendor tab, ** Tax information** group, **Vendor settlement for 1099s > Vendor 1099 transactions**

