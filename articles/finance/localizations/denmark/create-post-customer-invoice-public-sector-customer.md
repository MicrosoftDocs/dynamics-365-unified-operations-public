--- 
title: Create and post a customer invoice for a public sector customer
description: This article describes how to create and post a sales order invoice for a customer using OIOUBL electronic invoicing in Denmark with Microsoft Dynamics 365 Finance.
author: mrolecki
ms.author: egolub
ms.topic: how-to
ms.date: 12/16/2025
ms.reviewer: johnmichalak 
ms.search.region: Denmark
ms.search.validFrom: 2016-06-30
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable, ContactPersonLookup, SalesEditLines,  CustInvoiceJournal, ERFormatMappingRunJobTable
ms.custom: 
  - bap-template
---

# Create and post a customer invoice for a public sector customer

[!include [banner](../../includes/banner.md)]

This article describes how to create and post a sales order invoice for a customer using Offentlig Information Online Universal Business Language (OIOUBL) electronic invoicing in Denmark with Microsoft Dynamics 365 Finance.

The following procedures walk you through creating and posting a sales order invoice for a customer using OIOUBL electronic invoicing. The procedures are based on an OIOUBL e-invoice example that's common for Denmark, Austria, and Norway. The example uses the demo data company USMF with a legal entity primary address in Denmark.

## Prerequisites

Before you can execute the following procedures, complete the following tasks:

- Import OIOUBL electronic invoicing electronic reporting configurations.
- Set up OIOUBL electronic invoicing.
- Set up a customer account for OIOUBL electronic invoicing.

## Create a sales order

To create a sales order, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts receivable \> Orders \> All sales orders**.
1. Select **New**.
1. In the **Customer account** field, enter or select a customer enabled for electronic invoicing.  
1. Select **OK**.
1. Select a sales order header view.
1. In the **Contact** field, enter or select a value.
1. In the **Customer requisition** field, enter a value.
1. In the **Customer reference** field, enter a value.
1. Expand the **Setup** section.
1. Select a sales order line view.
1. In the **Item number** field, enter or select a value. You can use the item number "D0001."  
1. Select **Save**.

## Post an invoice for a sales order

To post an invoice for a sales order, follow these steps.

1. In Dynamics 365 Finance, on the Action Pane, select **Invoice**.
1. Select **Invoice**.
1. Expand the **Parameters** section.
1. In the **Quantity** field, select **All**.
1. Select **OK**.
1. Select **OK**.

## Generate OIOUBL electronic invoice

To generate an OIOUBL electronic invoice, follow these steps.

1. In Dynamics 365 Finance, select **Invoice**.
1. On the Action Pane, select **Invoice**.
1. Select **Send**.
1. Select **Original**.

## View an OIOUBL electronic invoice

To view an OIOUBL electronic invoice, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration \> Electronic reporting \> Electronic reporting jobs**.
1. Select **Show files**.
1. Select **Open**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
