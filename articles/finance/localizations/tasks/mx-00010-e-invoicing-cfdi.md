--- 
# required metadata 
 
title: E-invoicing CFDI
description: This topic walks you through creating and posting a customer invoice as an electronic invoice by using the CFDI method. 
author: sndray
ms.date: 08/03/2021
ms.topic: business-process 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable, TaxGroupLookup, InventLocationIdLookup, SalesEditLines,  EInvoiceCFDIJournal_AR   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Mexico
# ms.search.industry: 
ms.author: sndray
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# E-invoicing CFDI

[!include [banner](../../includes/banner.md)]

This topic walks you through creating and posting a customer invoice as an electronic invoice by using the CFDI method. You can create and post multiple sales orders as electronic invoices and send the .pdf and .xml files as email attachments to customers. This task can only be completed if you are logged into a legal entity with a primary address in Mexico. This task uses the MXMF demo company data.

> [!NOTE] 
> Customer invoices that are created by using a general ledger journal aren't included in the CFDI-Accounts Receivable Electronic Invoices which are located under **Accounts receivable** > **Inquiries and reports** > **CFDI (electronic invoices)**.

1. In the navigation pane, go to **Modules** > **Accounts receivable** > **Orders** > **All sales orders**, and then select **New**.
2. In the **Customer account** field, select the a record from the drop-down menu and then select **OK**.
3. In the **Item number** field of the new row, select an option, and in the **Unit price** field, enter a number.
4. In the **Line details** section, select the **Setup** tab, and in the **Sales tax group** field, select a row from the drop-down menu.
5. In the **Item sales tax group** field, select a record from the drop-down menu.
6. Select the **Product** tab, and in the **Warehouse** field, select a record from the drop-down menu. Select **OK**.
7. In the **Custom number** field, type a value. Enter the number of the customs document that was generated when the item was imported.  
8. In the **Custom date** field, enter a date. Select the date when the item was imported.  
9. In the **Custom name** field, type a value. Enter the name of the customs authority in the country/region that the item was imported from. If you enter values in the **Custom number**, **Custom date**, and **Custom name** fields, you cannot enter a value in the **Property number** field.  
10. In the **Unit price** field, enter a number.
11. Expand the **Sales order header** section, and on the Action Pane, select **Sell** > **Confirm sales order**.
12. Select **OK**, then select **OK** again.
13. On the Action Pane, select **Invoice** and expand the **Parameters** section to review the parameters before posting.
14. Select **OK**. After you press **OK**, the customer invoice is posted and scheduled in a specific batch processing for issuing electronic invoices (CFDI).  
15. Select **OK**.
16. In the navigation pane, go to **Accounts receivable** > **Invoices** > **E-Invoices** > **Export/import electronic invoice process**, and then select **OK**.
    - This batch job initiates the connection with the PAC web services to get the approval or cancellation of an electronic invoice (CFDI). The task in the batch can run manually or it can be scheduled by specific period of time.  
    - After you select **OK**, the validation and the digital signature will be retrieved from the PAC. If the electronic invoice is approved, the PAC send the response XML message and the status of the electronic invoice will update to be Approved. An email is automatically sent out to the customer with the XML and PDF file attached. The **Send mail** and **Send report file - PDF** sliders must be set to **Yes** on the **electronic invoice parameters** page. Otherwise, you can email or print PDF report based on the customer's request by using the **Inquire and Reports > CFDI (electronic invoices)** menu.  
17. In the navigation pane, go to **Accounts receivable** > **Inquiries and reports** > **CFDI (electronic invoices)** and select the electronic invoice to review.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
