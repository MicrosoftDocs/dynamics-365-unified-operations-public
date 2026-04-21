---
title: ER Use Document Management files in format outputs (Part 4 - Run format)
description: This article describes how to configure an Electronic reporting format to use Document Management files in ER output. (Part 4)
author: kfend
ms.date: 04/10/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: CustOpenInvoicesListPage, CustInvoiceJournal, SalesTable, ERSolutionTable
---

# ER Use Document Management files in format outputs (Part 4 - Run format)

[!include [banner](../../includes/banner.md)]

The following steps explain how a user assigned to the system administrator or electronic reporting developer role can configure an Electronic reporting (ER) format to use Document Management files (attachments) in ER output. You can perform these steps in the DEMF company.

To complete these steps, you must first complete the steps in the "ER Use Document Management files in format outputs (Part 3: Create format)" procedure.

This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.

## Add necessary attachments for sales order of a single invoice

1. Go to **Accounts receivable** > **Invoices** > **Open customer invoices**.
1. Use the Quick Filter to find records. For example, filter on the **Invoice** field with a value of `CIV-000148`.
    * CIV-000148  
1. Select the invoice link.
    * CIV-000148  
1. Select the link in the **Sales order** field.
    * 000148  
1. In the **Lines or header** field, select the option of **Header**.
    * Select **Header** to indicate that this sales order is the target for adding attachments.  
1. Select **Attach**.
    * Add a few files as attachments for this sales order. Use the files of the document types that are supported by the Document Management system, such as DOCX, PDF, XML, JPG, and more. Browse and select files to attach and further process with the related invoice in the ER electronic message.  
1. Select **New**.
1. Select **File**.
1. Select **New**.
1. Select **File**.
1. Close the page.
1. Close the page.
1. Close the page.
1. Close the page.

## Run the designed report for the selected invoice

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. In the tree, expand **Customer invoice model**.
1. In the tree, expand **Customer invoice model\Customer invoice model (custom)**.
1. In the tree, select **Customer invoice model\Customer invoice model (custom)\Electronic invoice sample message**.
1. Select **Run**.
1. Expand the **Records to include** section.
1. Select **Filter**.
1. Select the row of the **Customer invoice journal** and the **Sales order** field.
1. In the **Criteria** field, type `000148`.
    * In the criteria **Sales order** field, type the order number `000148`.  
1. Select **OK**.
1. Select **OK**.
    * Review the generated output. For each attachment, the report creates a single XML node. The attachment's content is added to the XML output in MIME (base64) text format.    

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
