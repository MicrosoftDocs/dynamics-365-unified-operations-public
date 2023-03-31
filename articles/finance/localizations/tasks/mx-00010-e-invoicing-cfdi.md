---
title: E-invoicing CFDI
description: This article walks you through creating and posting a customer invoice as an electronic invoice by using the CFDI method.
author: AdamTrukawka
ms.date: 08/03/2021
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Mexico
ms.author: atrukawk
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable, TaxGroupLookup, InventLocationIdLookup, SalesEditLines, EInvoiceCFDIJournal_AR
---
# E-invoicing CFDI

[!include [banner](../../includes/banner.md)]

This article walks you through creating and posting a customer invoice as an electronic invoice by using the CFDI method. You can create and post multiple sales orders as electronic invoices and send the .pdf and .xml files as email attachments to customers. This task can only be completed if you are logged into a legal entity with a primary address in Mexico. This task uses the MXMF demo company data.

> [!NOTE] 
> Customer invoices that are created by using a general ledger journal aren't included among the CFDI-Accounts Receivable electronic invoices that are found at **Accounts receivable** \> **Inquiries and reports** \> **CFDI (electronic invoices)**.

1. Go to **Accounts receivable** \> **Orders** \> **All sales orders**, and select **New**.
2. In the **Customer account** field, select a value. Then select **OK**.
3. On the new row, in the **Item number** field, select a value. In the **Unit price** field, enter a value.
4. In the **Line details** section, on the **Setup** tab, in the **Sales tax group** field, select a value. In the **Item sales tax group** field, select a value.
6. On the **Product** tab, in the **Warehouse** field, select a value. Then select **OK**.
7. In the **Custom number** field, enter the number of the customs document that was generated when the item was imported.
8. In the **Custom date** field, select the date when the item was imported.
9. In the **Custom name** field, enter the name of the customs authority in the country or region that the item was imported from.

    > [!NOTE]
    > If you enter values in the **Custom number**, **Custom date**, and **Custom name** fields, you can't enter a value in the **Property number** field.

10. In the **Unit price** field, enter a value.
11. Expand the **Sales order header** section, and then, on the Action Pane, select **Sell** \> **Confirm sales order**.
12. Select **OK**, and then select **OK** again.
13. On the Action Pane, select **Invoice**.
14. In the **Parameters** section, review the parameters before you post the customer invoice. Then select **OK**.

    The customer invoice is posted and scheduled in specific batch processing for issuing electronic invoices (CFDI).

16. Select **OK**.
17. Go to **Accounts receivable** \> **Invoices** \> **E-Invoices** \> **Export/import electronic invoice process**, and select **OK**.

    - This batch job initiates the connection with the PAC web services to get the approval or cancellation of an electronic invoice (CFDI). The task in the batch can run manually or it can be scheduled by specific period of time.
    - After you select **OK**, the validation and the digital signature will be retrieved from the PAC. If the electronic invoice is approved, the PAC send the response XML message and the status of the electronic invoice will update to be Approved. An email is automatically sent out to the customer with the XML and PDF file attached. The **Send mail** and **Send report file - PDF** sliders must be set to **Yes** on the **electronic invoice parameters** page. Otherwise, you can email or print PDF report based on the customer's request by using the **Inquire and Reports > CFDI (electronic invoices)** menu.

18. Go to **Accounts receivable** \> **Inquiries and reports** \> **CFDI (electronic invoices)**, and select the electronic invoice to review.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
