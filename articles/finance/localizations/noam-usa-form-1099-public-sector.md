---
title: Form 1099 in the public sector
description: This article provides tips and information about how to set up Form 1099 functionality for Accounts payable in the public sector.
author: brpotter
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: USA
ms.author: brpotter
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 10f56dea-ea2d-48ea-9622-4ef715eb1179
ms.search.industry: Public sector
ms.search.form: LedgerTransVoucher, SysConfiguration, Tax1099Summary, VendTableListPage
---

# Form 1099 in the public sector

[!include [banner](../includes/banner.md)]

This article provides tips and information about how to set up Form 1099 functionality for Accounts payable in the public sector.

The 1099 tax form is required if you do business with vendors that are subject to United States 1099 tax. This article describes the 1099 functionality that is available for the public sector. We also recommend that you review Internal Revenue Service (IRS) rule changes for the applicable tax year before you set up and process 1099 statements. If you do business with vendors that are subject to United States 1099 tax, you must track the amount that you pay to each vendor and report that information to the U.S. tax authorities at the end of the calendar year. The vendors are typically organizations that provide services to your organization. The vendors can also be people who aren't employees. You must also send a statement to each 1099 vendor that you do business with, to inform the vendor of the amount that you're reporting to the tax authorities. Legal public sector organizations that have a primary address in the United States can submit Form 1099-G or Form 1099-S to the IRS. The 1099-G income tax form is used to report income from government sources, such as state or local tax refunds, unemployment benefits, grants, or subsidies. The 1099-S income tax form is used to report income from the sale or exchange of certain types of real estate. In Dynamics 365 Finance, the 1099 setup procedures must typically be completed only one time. However, you can use this information later if you want to modify or view existing entries.

## Tips
-   On many pages, you might notice that the **S-2 gross proceeds** field doesn't appear. This field doesn't appear if the amount is the same as the amount in the **Settled federal 1099** field.
-   An individual 1099 report is associated with each 1099-S invoice. You can use the **Tax 1099 detail** report to view detailed 1099-S information.
-   On the lines of many journals, you can't enter an S-2 amount. This amount is the same as the 1099 amount field. However, you can enter S-2 details on the **1099** tab on these pages. Additionally, you can't select **S-5** on these pages, because you must manually enter this amount in the **S-5 buyer part of real estate tax** field.

## How do I view or specify vendor settlement for 1099s?
Use the **Vendor settlement for 1099s** page to enter or view the 1099 amounts that apply to your vendors, prepare 1099 statements, print copies for vendors, and create export files. The person or organization that is designated as the 1099 transmitter can send the 1099 statements to the IRS by using magnetic media or by filing them electronically. Alternatively, you can select a vendor account on the **All vendors** page in either Accounts payable or Procurement and sourcing, click **Vendor** on the Action Pane, and then click **Vendor settlement for 1099s**. **Notes**

-   You can change value in the **1099 box** field on the **Report 1099** FastTab on the vendor details page. If you select **G-2** and try to update all vendor records, you're prompted to confirm the update. Typically, G-2 information is entered only after a careful analysis of an individual vendor.
-   On the **Vendor settlement for 1099s** page, even if an S-2 amount is less than the minimum requirement, it might still have to be reported to the IRS. For example, the S-2 amount is 0 (zero), and the **S-4 transfer or received property or services** option is selected. In this case, the **IRS reportable** option is also selected.

## How do I update 1099 information?
You also use the **Vendor settlement for 1099s** page to enter or update 1099 information for a vendor. You can update the default minimum amounts for 1099-G or 1099-S form fields, if they are included. **Notes**

-   Some fields are intentionally omitted. For example, the **S-5** field is omitted, because it's used for real estate taxes, and an IRS minimum amount doesn't apply. Additionally, you can set up 1099-G and 1099-S amounts on this page, but still won't be able to track and print 1099-G or 1099-S vendor information.
-   The IRS might require that, if just one amount on a page exceeds the minimum amount, all amounts must be reported, even if all the other amounts are less than the minimum amount.


## Additional resources

[Accounts payable in the public sector overview](../public-sector/accounts-payable-public-sector.md)





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
