--- 
# required metadata 
 
title: Enter sales agreements
description: This article explains how to create a sales agreement that commits one of your customers to buy a product for an agreed amount over time in exchange for special discounts. 
author: Henrikan
ms.date: 08/08/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: SalesAgreementListPage, SalesAgreementCreate, SalesAgreement, InventItemIdLookupSimple, AgreementConfirmRunForm, SrsReportViewerForm, SalesAgreementCustomerReferencesPart
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Service industries
ms.author: henrikan
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Enter sales agreements

[!include [banner](../../includes/banner.md)]

This article explains how to create a sales agreement that commits one of your customers to buy a product for an agreed amount over time in exchange for special discounts. You can run this procedure in demo data company USMF or on your own data.


## Set up sales agreement header
1. Go to **Sales and marketing > Sales agreements > Sales agreements**.
2. Select **New**.
3. In the **Customer account** field, select the desired record from the drop-down menu.
4. In the **Sales agreement classification** field, select the desired record from the drop-down menu.
5. Expand the **General** section.
6. In the **Default commitment** field, select **Product value commitment**. A commitment type is a mandatory criterion that you must assign to the agreement to define how the agreement contract will be fulfilled. The four predefined types let you set up the customer's commitment target, expressed as a quantity or a value. The quantity commitment type can only be applied to a specific product, but the value-based types are applicable to sales of both specific and non-specific products.  
7. In the **Expiration date** field, set the date to a future date when you want the agreement to expire.
8. Select **OK**.

## Set up product value commitment lines
1. Select **Add line**.
2. In the **Item number** field, select the desired record from the drop-down menu. The type of commitment that you have chosen for the agreement affects the kind of information you can enter for the agreement lines. For example, for a value-based agreement you must specify the total net amount (in the agreed currency) for which the customer commits to buys goods from you. In this example the **Quantity** and **Unit** fields on the line are unavailable because you're creating an agreement for the customer to buy a specific value of a product.   
3. In the **Net amount** field, enter the monetary amount that the customer has committed to buying.
4. In the **Discount percent** field, enter a percentage value that will apply to the customer's sales order lines that are linked to this agreement.
5. Expand the **Line details** section.
6. Select **Yes** in the **Max is enforced** field.
    - Selecting **Max is enforced** means that the total amount of all the sales order lines that use the commitment's special prices, discounts and/or payment terms must not exceed the amount specified on the commitment.  
    - The minimum and maximum release amounts specify a range of values that must be sold on each sales order that uses the selected agreement.   
7. Expand the **Sales agreement header** section. Unless the status of the agreement is set to **Effective**, sales orders cannot be associated with the agreement and can therefore not contribute to the fulfilment of that agreement. You can change the status manually at this stage. However, the status would normally be changed when you confirm the agreement for the customer.  
8. On the Action Pane, select **Sales agreement**.
9. Select **Confirmation**. Make sure that the **Mark agreement as effective** option is set to **Yes**.  
10. Select **Yes** in the **Print report** field.
11. Select **OK**.
12. Close the page. The agreement is now effective. You can start linking the customer's orders to the agreement to offset against the committed target.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]