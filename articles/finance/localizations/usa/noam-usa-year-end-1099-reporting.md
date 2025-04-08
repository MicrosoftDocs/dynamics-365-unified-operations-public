---
title: Year-end 1099 reporting
description: If you do business with vendors subject to United States 1099 tax, you must track the amount paid to each vendor and report that information to US tax authorities.
author: abruer
ms.author: johnmichalak
ms.topic: article
ms.date: 10/31/2017
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: USA
ms.search.validFrom: 2016-02-28
ms.search.form: Tax1099Fields, Tax1099Summary
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 518633aa-b341-47e6-ac7b-7c5841b50dc3
---

# Year-end 1099 reporting

[!include [banner](../../includes/banner.md)]

If you do business with vendors that are subject to United States (US) 1099 tax, you must track the amount that you pay to each vendor and report that information to the US tax authorities at the end of the calendar year. The vendors are typically individuals who aren't employees, and who provide services to your organization. You must also send a statement to each 1099 vendor that you do business with to inform them about the amount that you're reporting to the tax authorities.

When you set up a vendor as a 1099 vendor, the amounts are tracked in Microsoft Dynamics 365 Finance throughout the year. On invoice lines, you use the **1099 box** and **1099 amount** fields to track 1099 amounts. As you settle payments against invoices that contain 1099 information, the 1099 settled values are tracked.

After you settle payments against an invoice, you can modify any 1099 amount on the **Tax 1099 transactions** page. Some invoice lines for a vendor might require 1099 tracking, whereas others might not. You can clear the **1099 settled** option for any invoice line that doesn't require 1099 tracking. 

Additionally, you can create a new 1099 transaction that isn't associated with an invoice. On the **Vendor settlement for 1099s** page, select the **Manual 1099 transactions** option. During the calendar year, if you set up a vendor as a 1099 vendor after you've already processed transactions for that vendor, you can update the previous transactions so that they are 1099 transactions. On the **Vendors** page, select **Update 1099** to update transactions. This action calculates 1099 amounts for paid invoices that are in the specified date range, based on the settings on the **Tax 1099** tab of the **Vendors** page.

> [!NOTE]
> You can run the process to update 1099 amounts for only one vendor at a time.

Before you set up and process 1099 statements, we recommend that you review Internal Revenue Service (IRS) rule changes for the applicable tax year. Then, when you're ready to process 1099 statements, use the **Vendor settlements for 1099s** page.

For information about the most current changes for 1099 reporting for calendar year 2020, see [Year-end activities FAQ](../../general-ledger/faq-year-end-activities.md).

## Example of a typical year-end 1099 process

Follow these steps to generate either an export file or a printed 1099 statement that you can send to a vendor, the IRS, or a tax preparer who will transmit the 1099 forms to the IRS on behalf of your organization.

1. On the **1099 fields** page (**Accounts payable \> Periodic tasks \> Tax 1099 \> 1099 fields**), verify the information in the fields.
2. Verify the minimum amounts that are required for 1099 reporting for the current tax year.
3. Print a **Tax 1099 detail** report to review vendor information and find any vendors that might require changes.

    > [!TIP]
    > To minimize the amount of data that you see, you can select **Select** to apply a filter.

    > [!NOTE]
    > If you notice an issue when you view a report, you can fix it. For example, you might notice that a 1099-G form is no longer required for a vendor because of a new tax regulation.
    >
    > - If the 1099-G form is the only 1099 tax form that the vendor will receive, you can clear the **Report 1099** option on the **Vendors** page. In this case, the vendor won't receive any 1099 forms.
    > - The **Tax 1099 transactions** page contains 1099 information from paid invoices, and you can modify that information.

4. On the **Vendor settlement for 1099s** page (**Accounts payable \> Periodic tasks \> Tax 1099 \> Vendor settlement for 1099s**), you can print the 1099 tax information as a paper form or transmit it as an electronic file. After you post a payment for an invoice, the invoice amount appears on the **Tax 1099 summary** page. When totals for a box reach the amount in the **1099 fields** list, the **IRS reportable** option is selected. After you load the printer with a blank 1099 tax form, you can print data to the form. You can also create an export file.

    > [!NOTE]
    > If validation errors occur when you try to create an export file, you can select **1099 software vendor** and **1099 transmitter** on the **Tax 1099 validation errors** page to enter missing field values. When you've finished, select **Recheck for errors** to revalidate the file.

## Create a copy of a 1099 form

At any point during the year, vendors might request that you provide a copy of their 1099 form. To print a copy, select **Print** on the **Vendor settlement for 1099s** page. If a vendor asks for a list of all invoices that were included in a 1099 form, you can print the **Tax 1099 detail** report.

## Partial payments and cross-company payment settlements

If you make a partial payment for an invoice, the 1099 amount is saved to reflect the partial payment. For example, the invoice amount is 200.00, the 1099 amount is 50.00, and the payment amount is 100.00 (50 percent of the invoice). In this case, the 1099 amount that is saved is 25.00 instead of 50.00. If an invoice is paid by another company (cross-company payment settlements), the company that makes the payments must create the 1099 statements.

## 1099-G and 1099-S forms

If your organization is in the public sector, you can submit 1099-G or 1099-S forms to the IRS.

> [!NOTE]
> This functionality is available only if the legal entity's address is in the United States, and the **Public Sector 1099G** or **Public Sector 1099S** configuration key is selected.

If you use 1099-G or 1099-S forms, note the following information:

- An individual 1099 report is associated with each 1099-S invoice. You can use the **Tax 1099 detail** report to view detailed 1099-S information.
- On the lines of many journals, you can't enter an S-2 amount. This amount is the same as the value of the **1099 amount** field. However, you can enter S-2 details on the **1099** tab in these forms. Additionally, you can't select S-5 in these forms, because you must manually enter this amount in the **S-5 buyer part of real estate tax** field on the **Vendor settlement for 1099s** page.

## 1099-OID form

An original issue discount (OID) is a type of interest that is created when debt instruments, such as bonds or notes, are issued at a discount. The OID is the difference between the stated *redemption price* of the instrument at maturity and its original *issue price*. The redemption price is the face value of the bond or note, and the issue price is the amount that the issuer first sold the bond or note for. An OID is treated as taxable income for the owner of the debt obligation. The issuer must report the issue of the bonds or notes to the IRS within 30 days of the date of issue, by using the 1099-OID form. If the OID isn't reported, the issuer is liable for a penalty of 1 percent of the issue price, up to a maximum of 50,000 US dollars (USD).

## 1099-NEC form

The IRS has released a new form, 1099-NEC, that is used to report non-employee compensation. Non-employee compensation was previously included in the 1099-MISC form. Additionally, the 1099-MISC form has been revised to meet the IRS regulatory changes for the 2020 tax year.

## 1099-DIV reporting option for total ordinary dividends

You can specify how the total ordinary dividend amounts will be reported for 1099-DIV processing. By specifying whether ordinary dividend amounts should be totaled for 1099-DIV processing, you can help make it easier to ensure regulatory compliance. To run the 1099-DIV reporting process, go to **Accounts payable \> Periodic tasks \> Tax 1099 \> Vendor settlement for 1099s**. To report the summed result in box 1a of the 1099-DIV, select the **Box 1a represents sum of box 1a and 1b** option on the **Vendor settlement for 1099s** page. This feature is available only if the **1099-DIV reporting options** feature on the **Feature management** page is turned on.

## Update tax 1099 information for multiple vendors

You can update the value in the **1099 box** on vendor records and update transactions with this information for multiple vendors in a single step. This process does not support 1099-G or 1099-S box types. If your organization is in the public sector, you can update 1099-G or 1099-S records one vendor record at a time. To do this, go to **Accounts payable > Vendors > All vendors > Vendor tab > Update 1099**. 

Before you can update 1099 information for multiple vendors, the feature must be turned on in the **Feature management** workspace. Select **Update tax 1099 information for multiple vendors** and select **Enable now**. You can use the **Update 1099 information for multiple vendors** page to update the **1099 box** on a vendor record, and to update transactions with the 1099 box information. You can open this page by going to **Accounts payable > Periodic task > Tax 1099**. You must be assigned to the **Update 1099 box and transactions for multiple vendors** security privilege to access the page.

Specific parameters are used to update 1099 information for multiple vendors in one step. The following parameters are available:
- **Update vendor’s 1099 box** – If you set this option to **Yes**, the **1099 box** information for the selected vendors will be updated to the value specified in the **New 1099 box value** parameter. To be updated, the selected vendor records must have the **Report 1099** parameter enabled on the **All vendors** page. Vendors that haven't had the **Report 1099** parameter turned on won't be updated when the process runs. If this option is set to **No**, the vendor **1099 box** won't be changed. 

- **New 1099 box value** – Select the 1099 field value that will be used to update the vendor’s 1099 box information. The **New 1099 box value** option is available only if the **Update vendor’s 1099 box** option is selected. 1099-S and 1099-G values are not included for processing.

- **Update 1099 transactions** – If you set this option to **Yes**, the 1099 transactions will be updated with the **1099 box** information specified on the **All vendors** page. The process will run for selected vendors that have the **Report 1099** parameter enabled, and that have a value specified for the **1099 box** on the **All vendors** page. If you enable both the **Update vendor’s 1099 box** and the **Update 1099 transactions** parameters, the system will update the selected vendor’s **1099 box** value first, and then will update the existing 1099 transactions with the newly updated **1099 box** information.

- **From date and To date** – Specify the date range for the 1099 transactions that will be updated. The **From date** must not be before January 1 of the previous calendar year. For example, assume that today’s date is January 2, 2022. The **From date** must not be prior to January 1, 2021. The **From date** and **To date** option is available only if the **Update 1099 transactions** option is selected.

- **Update all** - If you set this option to **Yes**, the 1099 transactions will be updated with the **1099 box** information specified on the **All vendors** page. The 1099 amount for the transactions will be set to the amount that was specified on the settled invoice. The **Update all** option is available only if the **Update 1099 transactions** option is selected. Manual 1099 transactions will not be updated. To update Manual 1099 transaction, go to **Accounts payable > Periodic tasks > Tax 1099 > Vendor settlement for 1099s > Manual 1099 transactions** to edit the information.

- **Recalculate existing 1099 amount** – If you set this option to **Yes**, the 1099 amount on the 1099 transactions will be reset to the total paid values. This option is used in conjunction with the **Update all** parameter. For example, assume that you posted an invoice valued at $1,000. At the time the invoice was recorded, the Accounts payable clerk modified the 1099 value to $500. When the invoice is paid, the system will update the settled 1099 value to $500. Assume that you run the **Update 1099 information for multiple vendors** process and set both the **Update all** and the **Recalculate existing 1099 amount** parameters to **Yes**. The settled 1099 value will be changed from $500 to $1,000. The **Recalculate existing 1099 amount** option is available only if the **Update 1099 transactions** option is selected.

- **Records to include** – You can filter the vendors that are selected for inclusion when the update is run. Vendors that have the **Report 1099** parameter set to **No** on the **All vendors** page will not be updated when the update process runs, even if they fall into the range of vendors that you defined.

Select **OK** to run the process. Before committing the process to run in a batch job, the system will display the number of vendors that will be updated. To make changes, based on the reported count, you can cancel the process. If you are satisfied with the reported count, you can confirm the process. After the count is confirmed, the process will run using a batch job. The results of the batch job can be viewed when the process is complete.




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]