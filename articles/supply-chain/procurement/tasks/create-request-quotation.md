---
title: Create a request for quotation
description: Learn how to create a request for quotation (RFQ), including step-by-step processes for preparing new RFQs, adding lines, and adding vendors.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form: PurchRFQCaseTableListPage, PurchCreateRFQCase, InventLocationIdLookup, PurchRFQCaseTable, InventItemIdLookupSimple, EcoResCategorySingleLookup, UnitOfMeasureLookup, PurchRFQEditLines, PurchRFQEditLinesPrintOptions, VendRFQJournal, SrsReportViewerForm
ms.topic: how-to
ms.date: 10/17/2025
ms.custom: 
  - bap-template
---

# Create a request for quotation

[!include [banner](../../includes/banner.md)]

This article shows you how to create a request for quotation. A purchasing agent typically performs this task. You can use this procedure in demo data company USMF or on your own data. You need to set up solicitation types before you start. After you complete this task and create and send a request for quotation (RFQ), you can enter the replies per vendor, compare them, and award the contract.

## Prepare a new RFQ

1. Go to **Procurement and sourcing \> Requests for quotations \> All requests for quotations**.
1. Select **New**. The following purchase types are available:
    - *Purchase order* – A document that confirms the offer to buy products, or the acceptance of an offer to sell products in exchange for payment. This type is the default.
    - *Purchase requisition* – This type is automatically selected if you create an RFQ directly from a purchase requisition. If you manually select this option, you get an error.
    - *Purchase agreement* – An agreement to purchase a specific quantity or value of product over time. If you select this option, you must select the date range that applies to the purchase agreement.  
1. In the **Document title** field, type a value.
1. In the **Solicitation type** field, enter or select a value.
    - If a scoring method is associated with the solicitation type, this method is the default scoring method for the RFQ that you're creating. You can change the scoring method later.  
    - In the **Receipt date** field, enter a date.  
    - Select the date by which you want to receive the items.  
    - In the **Expiration date and time** field, enter a date and time.  
    - Specify the date and time by which vendors must respond to the RFQ.  
1. In the **Warehouse field**, enter or select a value. The delivery address defaults to the warehouse address.  
1. Select **OK**.

## Add lines

After you specify the basic information about your RFQ, specify the goods or services that you want vendors to bid on. Item is the default line type.

1. In the **Item number** field, enter or select a value. If you're using USMF, you can select *T0020*.  
1. In the **Quantity** field, enter a number.
1. Select **Add line**.
1. In the **Line type** field, select *Category*. Use the *Category* line type to create RFQs for noninventory goods or services. Then select the type of goods or services from a hierarchy of procurement categories.  
1. In the **Procurement category** field, enter or select a value.
1. In the **Product name** field, type a value.
1. In the **Quantity** field, enter a number.
1. In the **Unit** field, enter or select a value.

## Add vendors

1. Select **Header** to change from the lines view to the header view.
1. Expand the **Vendor** section.
1. Select **Auto-add vendors**. You can add vendors to the RFQ automatically, based on the procurement category of the items requested. If there are no vendors approved for the categories included in the lines, you can add vendors manually.  
1. Select **Add**.
1. In the **Vendor account** field, enter or select a value.
1. Select **Add**.
1. In the **Vendor account** field, enter or select a value. When you select a vendor, the status is *Created*. This status means that the vendor information is saved in the RFQ, but you didn't yet send the RFQ to the vendor. You can add a vendor to an RFQ regardless of the vendor status.  

## Send the RFQ to vendors

1. On the Action Pane, select **Send**. On the **Sending request for quotation** page, check that the vendors in the list are the ones that you want to receive the RFQ.  
1. Select **Print**. This dialog allows you to print the RFQ. If you choose to print a reply sheet, the contents of this sheet are defined in **Procurement and sourcing parameters**. To choose how to print reply sheets, select **Advanced printing options** in the **Print** dialog. One RFQ is printed for each vendor containing the lines that have the status of *Created* or *Sent*. Canceled lines and lines with registered replies aren't printed.
1. Select **Cancel**.
1. Select **OK**.
1. Close the page.
1. Close the page.

## Send several RFQs at once

To send several RFQs to vendors all at once, follow these steps:

1. Select the checkbox for each RFQ that you'd like to send.
1. On the Action Pane, open the **Quotation** tab and select **Send all lines**.
1. On the **Sending request for quotation** dialog, make sure that the vendors shown are the ones that you want to send the RFQ to.
1. Select **OK**.

You can configure the system to filter the set of vendors listed on the **Sending request for quotation** dialog based on their status. To set this option, follow these steps:

1. Go to **Procurement and sourcing** \> **Setup** \> **Procurement and sourcing parameters**
1. Open the **Request for quotation** tab.
1. Set **Send all lines default status** to one of the following values:
    - *All* – List all vendors regardless of their status.
    - *Created* – Only list vendors that have **Lowest status** or **Highest status** set to *Created*.
    - *Sent* – Only list vendors that have **Lowest status** or **Highest status** set to *Sent*.

1. On the Action Pane, select **Save**.

## View the RFQ journal

1. Go to **Procurement and sourcing \> Requests for quotations \> Request for quotations follow-up \> Request for quotation journals**.
1. Select **Preview/Print**.
1. Select **Original preview**.
1. Close the page.
1. Close the page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
