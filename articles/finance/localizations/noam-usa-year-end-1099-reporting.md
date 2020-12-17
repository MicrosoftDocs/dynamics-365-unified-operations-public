---
# required metadata

title: Year-end 1099 reporting
description: If you do business with vendors that are subject to United States 1099 tax, you must track the amount that you pay to each vendor and report that information to the US tax authorities at the end of the calendar year.
author: abruer
manager: AnnBe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: Tax1099Fields, Tax1099Summary
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 6861
ms.assetid: 518633aa-b341-47e6-ac7b-7c5841b50dc3
ms.search.region: USA
# ms.search.industry: 
ms.author: abruer
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Year-end 1099 reporting

[!include [banner](../includes/banner.md)]

If you do business with vendors that are subject to United States (US) 1099 tax, you must track the amount that you pay to each vendor and report that information to the US tax authorities at the end of the calendar year. The vendors are typically individuals who aren't employees, and who provide services to your organization. You must also send a statement to each 1099 vendor that you do business with to inform them about the amount that you're reporting to the tax authorities.

When you set up a vendor as a 1099 vendor, the amounts are tracked in Microsoft Dynamics 365 Finance throughout the year. On invoice lines, you use the **1099 box** and **1099 amount** fields to track 1099 amounts. As you settle payments against invoices that contain 1099 information, the 1099 settled values are tracked.

After you settle payments against an invoice, you can modify any 1099 amount on the **Tax 1099 transactions** page. Some invoice lines for a vendor might require 1099 tracking, whereas others might not. You can clear the **1099 settled** option for any invoice line that doesn't require 1099 tracking. 

Additionally, you can create a new 1099 transaction that isn't associated with an invoice. On the **Vendor settlement for 1099s** page, select the **Manual 1099 transactions** option. During the calendar year, if you set up a vendor as a 1099 vendor after you've already processed transactions for that vendor, you can update the previous transactions so that they are 1099 transactions. On the **Vendors** page, select **Update 1099** to update transactions. This action calculates 1099 amounts for paid invoices that are in the specified date range, based on the settings on the **Tax 1099** tab of the **Vendors** page.

> [!NOTE]
> You can run the process to update 1099 amounts for only one vendor at a time.

Before you set up and process 1099 statements, we recommend that you review Internal Revenue Service (IRS) rule changes for the applicable tax year. Then, when you're ready to process 1099 statements, use the **Vendor settlements for 1099s** page.

For information about the most current changes for 1099 reporting for calendar year 2020, see [Year-end activities FAQ](../general-ledger/faq-year-end-activities.md).

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
