--- 
# required metadata 
 
title: Create a request for quotation
description: This procedure shows you how to create a request for quotation. 
author: GalynaFedorova
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: PurchRFQCaseTableListPage, PurchCreateRFQCase, InventLocationIdLookup, PurchRFQCaseTable, InventItemIdLookupSimple, EcoResCategorySingleLookup, UnitOfMeasureLookup, PurchRFQEditLines, PurchRFQEditLinesPrintOptions, VendRFQJournal, SrsReportViewerForm   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: gfedorova
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create a request for quotation

[!include [banner](../../includes/banner.md)]

This procedure shows you how to create a request for quotation. This would typically be done by a purchasing agent. You can use this procedure in demo data company USMF or on your own data. You need to have set up solicitation types before you start. Once you've completed this task and you've created and sent an RFQ you can then enter the replies per vendor, compare them, and award the contract.


## Prepare a new RFQ
1. Go to **Procurement and sourcing > Requests for quotations > All requests for quotations**.
2. Click **New**.
    The following purchase types are available: Purchase order (this is the default): a document that confirms the offer to buy products, or the acceptance of an offer to sell products in exchange for payment. Purchase requisition: this type is automatically selected if you create an RFQ directly from a purchase requisition. If you manually select this option, you'll get an error. Purchase agreement: an agreement to purchase a specific quantity or value of product over time. If you select this option, you must select the date range that applies to the purchase agreement.  
3. In the **Document title** field, type a value.
4. In the **Solicitation type** field, enter or select a value.
    + If a scoring method is associated with the solicitation type, this will be the default scoring method for the RFQ that you're creating. It is possible to change the scoring method later.  
    + In the **Delivery date** field, enter a date.  
    + Select the date by which you want to receive the items.  
    + In the **Expiration date and time** field, enter a date and time.  
    + Specify the date and time by which vendors must respond to the RFQ.  
5. In the **Warehouse field**, enter or select a value. The delivery address will default to the warehouse address.  
6. Click **OK**.

## Add lines

After you've specified the basic information about your RFQ, you specify the goods or services that you want vendors to bid on. Item is the default line type.

1. In the **Item number** field, enter or select a value. If you're using USMF, you can select T0020.  
2. In the **Quantity** field, enter a number.
3. Click **Add line**.
4. In the **Line type** field, select 'Category'. You can use the Category line type to create RFQs for non-inventory goods or services. You then need to select the type of goods or services from a hierarchy of procurement categories.  
5. In the **Procurement category** field, enter or select a value.
6. In the **Product name** field, type a value.
7. In the **Quantity** field, enter a number.
8. In the **Unit** field, enter or select a value.

## Add vendors
1. Click **Header** to change from the Lines view to the Header view. 
2. Expand the **Vendor** section.
3. Click **Auto-add vendors**. You can add vendors to the RFQ automatically, based on the procurement category of the items requested. If there are no vendors approved for the categories included in the lines you can add vendors manually.  
4. Click **Add**.
5. In the **Vendor account** field, enter or select a value.
6. Click **Add**.
7. In the **Vendor account** field, enter or select a value. Once you've selected a vendor, the status is Created. This means that the vendor information has been saved in the RFQ, but you have not sent the RFQ to the vendor. You can add a vendor to an RFQ regardless of the vendor status.  

## Send the RFQ to vendors
1. On the **Action Pane**, click **Send**. In the Sending request for quotation page, check that the vendors in the list are the ones that you want to receive the RFQ.  
2. Click **Print**. This dialog allows you to print the RFQ. If you choose to print a reply sheet, the contents of this are defined in Procurement and Sourcing parameters. To choose how to print reply sheets, once you've opened the Print dialog, click Advanced printing options. One RFQ will be printed for each vendor containing the lines that have the status of Created or Sent. Canceled lines and lines with registered replies will not be printed.   
3. Click **Cancel**.
4. Click **OK**.
5. Close the page.
6. Close the page.

## View the RFQ journal
1. Go to **Procurement and sourcing > Requests for quotations > Request for quotations follow-up > Request for quotation journals**.
2. Click **Preview/Print**.
3. Click **Original preview**.
4. Close the page.
5. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]