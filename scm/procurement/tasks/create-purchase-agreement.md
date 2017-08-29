--- 
# required metadata 
 
title: Create a purchase agreement
description: This procedure guides you through the creation of a purchase agreement. 
author: mkirknel
manager: AnnBe 
ms.date: 11/14/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: bis
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create a purchase agreement

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure guides you through the creation of a purchase agreement. This would typically be done by a purchasing manager. You can use this procedure in demo data company USMF or on your own data. You need to have set up purchase agreement classifications before you start. Once you've created an agreement you can use it when you create a PO, and this will copy the purchase agreement conditions to the header and to any lines in the order that are affected by the agreement.


## Create a new purchase agreement
1. Go to Procurement and sourcing > Purchase agreements > Purchase agreements.
2. Click New.
3. In the Vendor account field, click the drop-down button to open the lookup.
4. In the list, find and select the desired record.
5. In the list, click the link in the selected row.
6. In the Purchase agreement classification field, click the drop-down button to open the lookup.
7. In the list, find and select the desired record.
8. In the list, click the link in the selected row.
9. Expand the General section.
10. In the Expiration date field, enter a date.
    * This expiration date will be the default for all commitment lines and will determine how long each specific commitment is valid.  
11. In the Document title field, type a name for your purchase agreement.
    * Leave the Default commitment field set to Product quantity commitment (or change it if it’s not set to this).  
    * The default commitment value determines your options on the agreement lines. If you need a new commitment type when you’re creating the agreement lines, you need to change the default commitment on the header.  There are 4 types of commitments: Product quantity commitment - for a specific quantity of a product; Product value commitment - for a specific currency amount of a product; Product category value commitment - for a specific currency amount in a procurement category where the amount can be for a catalog item or a non-catalog item; Value commitment - for a specific currency amount which can be fulfilled by any product or by any procurement category.  
12. Click OK.

## Add a commitment
1. Click Add line.
2. In the list, mark the selected row.
3. In the Item number field, click the drop-down button to open the lookup.
4. Select the product you want to add a commitment for.
5. In the list, click the link in the selected row.
6. In the Quantity field, enter a number.
    * This is the total quantity that you have agreed to buy from your vendor.  
7. In the Unit price field, enter a number.
8. Expand the Line details section.
9. Set the Max is enforced option to Yes.
    * The Max is enforced option limits the use of the commitment. You can only purchase up to the quantity that's specified in the Quantity field for the line.  
10. Collapse the Line details section.

## Add header conditions
1. On the Action Pane, click Options.
2. Click Change view.
3. Click Header view.
4. Expand the Terms section.
5. In the Method of payment field, click the drop-down button to open the lookup.
    * The payment terms from the vendor account are shown here by default.       
6. In the list, find and select the desired record.
7. In the list, click the link in the selected row.
8. In the Mode of delivery field, click the drop-down button to open the lookup.
9. In the list, click the link in the selected row.
10. In the Delivery terms field, click the drop-down button to open the lookup.
11. In the list, click the link in the selected row.

## Confirm and activate the agreement
1. On the Action Pane, click Purchase agreement.
2. Click Confirmation.
    * Set the Mark agreement as effective option to Yes.  
3. Click OK.
4. On the Action Pane, click Purchase agreement.
5. Click Purchase agreement confirmations.
    * The Preview/Print option allows you to generate a document for the purchase agreement which you can then print or send to the vendor. If you update the agreement later on and re-confirm it, both versions will be shown here.  
6. Close the page.

