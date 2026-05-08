---
title: E-invoicing CFDI
description: Learn about creating and posting a customer invoice as an electronic invoice by using the CFDI method, including a step-by-step process.
author: ankviklis
ms.author: ankviklis
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/30/2026
ms.reviewer: johnmichalak
ms.search.region: Mexico
ms.search.validFrom: 2016-06-30
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable, TaxGroupLookup, InventLocationIdLookup, SalesEditLines, EInvoiceCFDIJournal_AR
ms.dyn365.ops.version: Version 7.0.0
---

# E-invoicing CFDI

[!include [banner](../../includes/banner.md)]

This article shows you how to create and post a customer invoice as an electronic invoice by using the CFDI method. You can create and post multiple sales orders as electronic invoices and send the .pdf and .xml files as email attachments to customers. You must be logged into a legal entity with a primary address in Mexico to complete this task. This task uses the MXMF demo company data.

> [!NOTE] 
> Customer invoices that you create by using a general ledger journal aren't included among the CFDI-Accounts Receivable electronic invoices that you find at **Accounts receivable** > **Inquiries and reports** > **CFDI (electronic invoices)**.

1. Go to **Accounts receivable** > **Orders** > **All sales orders**, and select **New**.
1. In the **Customer account** field, select a value. Then select **OK**.
1. On the new row, in the **Item number** field, select a value. In the **Unit price** field, enter a value.
1. In the **Line details** section, on the **Setup** tab, in the **Sales tax group** field, select a value. In the **Item sales tax group** field, select a value.
1. On the **Product** tab, in the **Warehouse** field, select a value. Then select **OK**.
1. In the **Custom number** field, enter the number of the customs document that was generated when the item was imported.
1. In the **Custom date** field, select the date when the item was imported.
1. In the **Custom name** field, enter the name of the customs authority in the country or region that the item was imported from.

    > [!NOTE]
    > If you enter values in the **Custom number**, **Custom date**, and **Custom name** fields, you can't enter a value in the **Property number** field.

1. In the **Unit price** field, enter a value.
1. Expand the **Sales order header** section, and then, on the Action Pane, select **Sell** > **Confirm sales order**.
1. Select **OK**, and then select **OK** again.
1. On the Action Pane, select **Invoice**.
1. In the **Parameters** section, review the parameters before you post the customer invoice. Then select **OK**.

    The customer invoice is posted and scheduled in specific batch processing for issuing electronic invoices (CFDI).

1. Select **OK**.
1. Go to **Accounts receivable** > **Invoices** > **E-Invoices** > **Export/import electronic invoice process**, and select **OK**.

    - This batch job initiates the connection with the PAC web services to get the approval or cancellation of an electronic invoice (CFDI). The task in the batch can run manually or it can be scheduled by specific period of time.
    - After you select **OK**, the validation and the digital signature are retrieved from the PAC. If the electronic invoice is approved, the PAC sends the response XML message and the status of the electronic invoice updates to be Approved. An email is automatically sent to the customer with the XML and PDF file attached. The **Send mail** and **Send report file - PDF** sliders must be set to **Yes** on the **electronic invoice parameters** page. Otherwise, you can email or print PDF report based on the customer's request by using the **Inquire and Reports > CFDI (electronic invoices)** menu.

1. Go to **Accounts receivable** > **Inquiries and reports** > **CFDI (electronic invoices)**, and select the electronic invoice to review.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
