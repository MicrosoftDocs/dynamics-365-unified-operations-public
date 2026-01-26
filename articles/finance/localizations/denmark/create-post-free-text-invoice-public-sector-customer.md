--- 
title: Create and post a free text invoice for a public sector customer
description: This article describes how to create and post free text invoices for customers using OIOUBL electronic invoicing in Denmark with Microsoft Dynamics 365 Finance.
author: mrolecki
ms.author: egolub
ms.topic: how-to
ms.date: 12/16/2025
ms.reviewer: johnmichalak   
ms.search.region: Denmark
ms.search.validFrom: 2016-06-30
ms.search.form: CustFreeInvoice, CustTableLookup, ContactPersonLookup, CustPostInvoiceJob 
ms.custom: 
  - bap-template
---

# Create and post a free text invoice for a public sector customer

[!include [banner](../../includes/banner.md)]

This article describes how to create and post free text invoices for customers by using Offentlig Information Online Universal Business Language (OIOUBL) electronic invoicing in Denmark with Microsoft Dynamics 365 Finance.

The following procedures walk you through how to create and post free text invoices for customers by using Offentlig Information Online Universal Business Language (OIOUBL) electronic invoicing. The procedures use the demo data company USMF with a legal entity primary address in Denmark.

## Prerequisites

Before you can execute these procedures, complete the following procedures.

- Import OIOUBL electronic invoicing electronic reporting configurations
- Set up OIOUBL electronic invoicing
- Set up a customer account for OIOUBL electronic invoicing

To create and post a free text invoice for a public sector customer, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable \> Invoices \> All free text invoices**.
1. Select **New**.
1. In the **Customer account** field, enter or select a value. You must enable the customer you select for the free text invoice for electronic invoicing.  
1. Select a free text invoice header view.
1. Expand the **Customer** section.
1. In the **Customer requisition** field, enter a value.
1. In the **Customer reference** field, enter a value.
1. In the **Contact** field, enter or select a value.
1. Select a free text invoice lines view.
1. In the list, mark the selected row.
1. In the **Description** field, enter a value.
1. In the **Main account** field, enter a value.
1. In the **Unit price** field, enter a number.
1. Select **Post**.
1. Select **OK**.

## Generate an OIOUBL electronic invoice

To generate an OIOUBL electronic invoice, follow these steps:

1. Select **Send**.
1. Select **Original**.  
1. Go to the **Electronic reporting jobs** page to check the status of the job and download the file.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
