--- 
title: Create and post a project invoice for a public sector customer
description: This article describes how to create and post a project invoice for a customer using OIOUBL electronic invoicing in Denmark with Microsoft Dynamics 365 Finance.
author: mrolecki
ms.author: egolub
ms.topic: how-to
ms.date: 12/16/2025
ms.reviewer: johnmichalak 
ms.search.region: Denmark
ms.search.validFrom: 2016-06-30
ms.search.form: ProjProjectContractsListPage, ProjInvoiceTable, ProjFundingSourceDetail, ContactPersonLookup, ProjSalesItemReq, ProjTableLookup, InventItemIdLookupSimple, SalesEditLines,  ProjInvoiceProposalListPage, ProjInvoiceProposalCreateLines, ProjInvoiceProposalDetail, ProjInvoiceEditLines, ProjInvoiceListPage, ERFormatMappingRunJobTable
ms.custom: 
  - bap-template
---

# Create and post a project invoice for a public sector customer

[!include [banner](../../includes/banner.md)]

This article describes how to create and post a project invoice for a customer using Offentlig Information Online Universal Business Language (OIOUBL) electronic invoicing in Denmark with Microsoft Dynamics 365 Finance.

The following procedures walk you through how to create and post a project invoice for a customer using OIOUBL electronic invoicing. The procedures use the demo data company USMF with the country/region of legal entity primary address updated to Denmark.

Before you can complete this procedure, you must complete the following procedures:

- Import OIOUBL electronic invoicing electronic reporting configurations
- Set up OIOUBL electronic invoicing
- Set up a customer account for OIOUBL electronic invoicing

## Update a project contract

To update a project contract, follow these steps:

1. In Dynamics 365 Finance, go to **Project management and accounting \> Projects \> Project contracts**.
1. Use the Quick Filter to find records. For example, filter on the **Project contract ID** field with a value of "000057". Select a project contract that has a customer funding source that's enabled for electronic invoicing.  
1. Open details for a project contract.
1. Expand the **Funding sources** section.
1. Select **Details**.
1. Expand the **Other** section.
1. In the **Customer requisition** field, enter a value.
1. In the **Customer reference** field, enter a value.
1. In the **Contact ID** field, enter or select a value.
1. Select **Save**.

## Create a project transaction

To create a project transaction, follow these steps:

1. In Dynamics 365 Finance, go to **Project management and accounting \> Item tasks \> Item requirements**.
1. Select **New**.
1. In the **Project ID** field, enter or select a value. For example, you can enter "000057" as a project ID.  
1. In the **Item number** field, enter or select a value. For example, you can enter "D0001" as an item number.  
1. On the Action Pane, select **Manage**.
1. Select **Posting**.
1. Select **Packing slip**.
1. Expand the **Parameters** section.
1. In the **Quantity** field, select **All**.
1. Select **OK**.
1. Select **OK**.

## Create a proposal and post an invoice

To create a proposal and post an invoice, follow these steps:

1. In Dynamics 365 Finance, go to **Project management and accounting \> Project invoices \> Project invoice proposals**.
1. Select **New**.
1. Select **Invoice** proposal.
1. In the **Project** field, enter or select a value.
1. Select **OK**.
1. Select **Post**.
1. Select **OK**.
1. Select **OK**.

## Generate an OIOUBL project invoice

To generate an OIOUBL project invoice, follow these steps:

1. In Dynamics 365 Finance, go to **Project management and accounting \> Project invoices \> Project invoices**.
1. Use the Quick Filter to find records. For example, filter on the **Project contract ID** field with a value of "000057".
1. On the Action Pane, select **Project invoice**.
1. Select **Send**.
1. Select **Original**.

## View an OIOUBL electronic invoice

To view an OIOUBL electronic invoice, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration \> Electronic reporting \> Electronic reporting jobs**.
1. Select **Show files**.
1. Select **Open**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
