---
# required metadata

title: Year-end 1099 reporting
description: If you do business with vendors that are subject to United States 1099 tax, you must track the amount that you pay to each vendor and report that information to the U.S. tax authorities at the end of the calendar year. The vendors are typically individuals who are not employees and who provide services to your organization. You must also send a statement to each 1099 vendor that you do business with, informing them of the amount that you are reporting to the tax authorities.
author: twheeloc
manager: AnnBe
ms.date: 2015-09-14 19 - 03 - 00
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: Tax1099Fields, Tax1099Summary
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 6861
ms.assetid: 518633aa-b341-47e6-ac7b-7c5841b50dc3
ms.search.region: United States
# ms.search.industry: 
ms.author: abruer
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Year-end 1099 reporting

If you do business with vendors that are subject to United States 1099 tax, you must track the amount that you pay to each vendor and report that information to the U.S. tax authorities at the end of the calendar year. The vendors are typically individuals who are not employees and who provide services to your organization. You must also send a statement to each 1099 vendor that you do business with, informing them of the amount that you are reporting to the tax authorities.

When you set up a vendor to be a 1099 vendor, the amounts are tracked within Microsoft Dynamics 365 for Operations throughout the year. On invoice lines, you use the 1099 box and 1099 amount fields to track 1099 amounts. As you settle payments against these invoices that contain 1099 information, the 1099 settled values are tracked.
After you settle payments against an invoice, you can modify any 1099 amount using the Tax 1099 transactions page. Some invoice lines for a vendor might need 1099 tracking whereas others do not. You can clear the 1099 settled option for any invoice line that needs no 1099 tracking. You can also create a new 1099 transaction that is not associated with an invoice by selecting the Manual 1099 transactions option on the Vendor settlement for 1099s page. If you set up a 1099 vendor during the calendar year after you have already processed transactions for that vendor, you can update the previous transactions to be 1099 transactions. On the Vendors page, select the action Update 1099 to update transactions. This calculates 1099 amounts for paid invoices that are in the specified date range, according to the settings on the Tax 1099 tab on the Vendors page.
> [!NOTE]
> You can run the process to update 1099 amounts for only one vendor at a time. 

We recommend that you review IRS rule changes for the applicable tax year before you set up and process 1099 statements. When you are ready to process 1099 statements, use the Vendor settlements for 1099s page.

## Example of a typical yearend 1099 process
You might follow these steps to generate either an export file or a printed 1099 statement to send to the vendor, IRS, or tax firm that transmits the 1099 forms to the IRS on behalf of your organization.
1.  Verify the 1099 fields in the periodic tasks area for Tax 1099 . Then verify the minimum amounts that are required for 1099 reporting for the current tax year.
2.  Print a Tax 1099 summary report and a Tax 1099 detail report  to review vendor information and locate any vendors who might need changes.
   > [!NOTE]
   > To minimize the amount of data that you see, you can click Select to apply a filter.

   > If you view a report and notice a problem, you can fix it. Example Because of a new tax regulation, you notice that a 1099-G form is not required for a vendor.
   > -   If the 1099-G form is the only 1099 tax form that the vendor will receive, you can clear the Report 1099 option in the Vendors page so the vendor will not receive any 1099 forms.
   > -   The Tax 1099 transactions page contains 1099 information from paid invoices, and you can modify that information.

3.   You can print the 1099 tax information in paper form or transmit 1099 tax information by electronic or magnetic filing using the Vendor settlement for 1099s page. After you post a payment for an invoice, the invoice amount appears in the Tax 1099 summary page. When totals for a box reach the amount in the 1099 fields page, the IRS reportable option is selected. After you load the printer with blank 1099 tax forms, you can print data to the form. You can also create an export file.
  > [!NOTE]
  > If you try to create an export file and a form opens that displays validation errors, you can click 1099 software vendor and 1099 transmitter in the Tax 1099 validation errors form to enter missing field values. Then click Recheck for errors to revalidate the file. 

## Create a copy of a 1099 form
At any point during the year, a vendor might request that you provide a copy of their 1099 form. To print a copy, click Print on the Vendor settlement for 1099s page. If a vendor asks for a list of all invoices that were included on a 1099 form, you can print the Tax 1099 detail report.

## Partial payments and crosscompany payment settlements
If you make a partial payment for an invoice, the 1099 amount is saved to reflect the partial payment. For example, if the invoice amount is 200.00 and the 1099 amount is 50.00, and the payment is 100.00 (50 percent of the invoice), the 1099 amount that is saved is 25.00 instead of 50.00. If an invoice is paid by another company (cross-company payment settlements), the company that makes the payments must create the 1099 statements.

## 1099G and 1099S forms
If your organization is in the public sector, you can submit 1099-G or 1099-S forms to the IRS.
> [!NOTE]
> This functionality is available only if the legal entity’s address is in the United States and the Public Sector 1099G or Public Sector 1099S configuration keys are selected.

If you use these forms, the following tips provide more information:
-   An individual 1099 report is associated with each 1099-S invoice. You can use the Tax 1099 detail report to view detailed 1099-S information.
-   In the lines of many journals, you cannot enter an S-2 amount. This amount is the same as the 1099 amount field. However, you can enter S-2 details on the 1099 tab in these forms. Also, you cannot select S-5 in these forms because you must manually enter this amount in the S-5 buyer part of real estate tax field. Click Accounts payable &gt; Periodic &gt; Vendor settlement for 1099s.

## 1099OID form
An original issue discount (OID) is a type of interest that is created when debt instruments, such as bonds or notes, are issued at a discount. The OID is the difference between the stated redemption price of the instrument at maturity and its original issue price. The redemption price is the face value of the bond or note, and the issue price is the amount for which the bond or note was first sold by the issuer. An OID is treated as taxable income for the owner of the debt obligation. The issuer must report the issue of the bonds or notes to the Internal Revenue Service (IRS) using the 1099-OID form within 30 days of the date of issue. The issuer is liable for a penalty of one percent of the issue price, up to a maximum of USD 50,000, if the OID is not reported.



