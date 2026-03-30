---
title: MX-00010 Post a free text invoice
description: Learn how to create and post a customer invoice as an electronic invoice in Microsoft Dynamics 365 Finance.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/10/2025
ms.reviewer: johnmichalak
ms.search.region: Mexico
ms.search.validFrom: 2016-06-30
ms.search.form: CustFreeInvoice, CustTableLookup, CustPostInvoiceJob, EInvoiceCFDIJournal_AR
---

# MX-00010 Post a free text invoice

[!include [banner](../../includes/banner.md)]

This article explains how to use the **Free text invoice** form to create and post an electronic Comprobante Fiscal Digital por Internet (CFDI) customer invoice in Microsoft Dynamics 365 Finance.

To use the following procedure, you must be signed in to a Mexican legal entity. 

The procedure was created using the MXMF demo data company.

## Post and issue a CFDI electronic invoice

To post and issue a CFDI electronic invoice, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable \> Invoices \> All free text invoices**.
1. Select **New**.
1. In the **Customer account** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the **Description** field, enter a value.
1. In the **Main account** field, enter a value.
1. In the **Sales tax group** field, enter a value.
1. In the **tem sales tax group** field, enter a value.
1. In the **Unit price** field, enter a number.
1. Expand or collapse the **Line details** section.
1. Select the **Electronic invoices** tab.
1. In the **Property number** field, enter a value. When you create the free text invoice for a leasing service, you must specify the property registration number provided by the Mexican government.  
1. Select **Post**.
1. Select **OK**. The customer invoice is posted and scheduled in a specific batch processing job for issuing electronic invoices.  
1. Close the page.
1. Go to **Accounts receivable \> Invoices \> E-Invoices \> Export/import electronic invoice process**.
1. Select **OK**.
    > [!NOTE]
    > - This batch job executes the connection with the Proveedor autorizado de certificación (PAC) web service to obtain the approval or cancellation of a CFDI electronic invoice. The task in the batch job can run manually, or be scheduled by specific period of time. After you select **OK**, a web connection with the PAC is established in order to get the validation and digital signature. If the electronic invoice is approved, the PAC sends the response XML message and the status of the electronic invoice is set to **Approved**. An email is automatically sent out to the customer with the XML and PDF file attached.
    > - You can select the **Send mail** and **Send report file - PDF** in the electronic invoice parameters. Alternatively, you can email or print a PDF report based on customer's request by using the **Inquire and Reports \> CFDI (electronic invoices)** menu.    
1. Go to **Accounts receivable \> Inquiries and reports \> CFDI (electronic invoices)**.
1. In the list, mark the selected row.
1. In the list, select the link in the selected row.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
