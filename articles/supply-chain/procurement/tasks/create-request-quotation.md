---
title: Create a request for quotation
description: Learn how to create a request for quotation, including step-by-step processes for preparing new RFQs, adding lines, and adding vendors.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form: PurchRFQCaseTableListPage, PurchCreateRFQCase, InventLocationIdLookup, PurchRFQCaseTable, InventItemIdLookupSimple, EcoResCategorySingleLookup, UnitOfMeasureLookup, PurchRFQEditLines, PurchRFQEditLinesPrintOptions, VendRFQJournal, SrsReportViewerForm
ms.topic: how-to
ms.date: 08/26/2024
ms.custom: 
  - bap-template
---

# Create a request for quotation

[!include [banner](../../includes/banner.md)]

This procedure shows you how to create a request for quotation. This would typically be done by a purchasing agent. You can use this procedure in demo data company USMF or on your own data. You need to have set up solicitation types before you start. Once you've completed this task and you've created and sent an RFQ you can then enter the replies per vendor, compare them, and award the contract.

## Prepare a new RFQ

1. Go to **Procurement and sourcing > Requests for quotations > All requests for quotations**.
2. Select **New**.
    The following purchase types are available: Purchase order (this is the default): a document that confirms the offer to buy products, or the acceptance of an offer to sell products in exchange for payment. Purchase requisition: this type is automatically selected if you create an RFQ directly from a purchase requisition. If you manually select this option, you'll get an error. Purchase agreement: an agreement to purchase a specific quantity or value of product over time. If you select this option, you must select the date range that applies to the purchase agreement.  
3. In the **Document title** field, type a value.
4. In the **Solicitation type** field, enter or select a value.
    + If a scoring method is associated with the solicitation type, this will be the default scoring method for the RFQ that you're creating. It's possible to change the scoring method later.  
    + In the **Receipt date** field, enter a date.  
    + Select the date by which you want to receive the items.  
    + In the **Expiration date and time** field, enter a date and time.  
    + Specify the date and time by which vendors must respond to the RFQ.  
5. In the **Warehouse field**, enter or select a value. The delivery address will default to the warehouse address.  
6. Select **OK**.

## Add lines

After you've specified the basic information about your RFQ, you specify the goods or services that you want vendors to bid on. Item is the default line type.

1. In the **Item number** field, enter or select a value. If you're using USMF, you can select T0020.  
2. In the **Quantity** field, enter a number.
3. Select **Add line**.
4. In the **Line type** field, select 'Category'. You can use the Category line type to create RFQs for noninventory goods or services. You then need to select the type of goods or services from a hierarchy of procurement categories.  
5. In the **Procurement category** field, enter or select a value.
6. In the **Product name** field, type a value.
7. In the **Quantity** field, enter a number.
8. In the **Unit** field, enter or select a value.

## Add vendors

1. Select **Header** to change from the Lines view to the Header view.
2. Expand the **Vendor** section.
3. Select **Auto-add vendors**. You can add vendors to the RFQ automatically, based on the procurement category of the items requested. If there are no vendors approved for the categories included in the lines, you can add vendors manually.  
4. Select **Add**.
5. In the **Vendor account** field, enter or select a value.
6. Select **Add**.
7. In the **Vendor account** field, enter or select a value. Once you've selected a vendor, the status is Created. This means that the vendor information has been saved in the RFQ, but you haven't sent the RFQ to the vendor. You can add a vendor to an RFQ regardless of the vendor status.  

## Send the RFQ to vendors

1. On the **Action Pane**, select **Send**. In the Sending request for quotation page, check that the vendors in the list are the ones that you want to receive the RFQ.  
2. Select **Print**. This dialog allows you to print the RFQ. If you choose to print a reply sheet, the contents of this are defined in Procurement and Sourcing parameters. To choose how to print reply sheets, once you've opened the Print dialog, select Advanced printing options. One RFQ will be printed for each vendor containing the lines that have the status of Created or Sent. Canceled lines and lines with registered replies won't be printed.
3. Select **Cancel**.
4. Select **OK**.
5. Close the page.
6. Close the page.

## View the RFQ journal

1. Go to **Procurement and sourcing > Requests for quotations > Request for quotations follow-up > Request for quotation journals**.
2. Select **Preview/Print**.
3. Select **Original preview**.
4. Close the page.
5. Close the page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
