---
title: Set up basic tax integration profile for China
description: This article describes how to set up a tax integration profile, update customer settings for issuing VAT invoices, and set up VAT invoice descriptions for China in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/05/2025
ms.reviewer: johnmichalak
ms.search.region: China (PRC)
ms.search.validFrom: 2016-06-30
ms.search.form: TaxProfileTable_CN, HcmWorkerLookUp, UnitOfMeasureLookup, CustTable, LogisticsPostalAddress, TaxGroupLookup, VATInvoiceDescTable_CN
ms.custom: 
  - bap-template
---

# Set up basic tax integration profile for China

[!include [banner](../../includes/banner.md)]

This article describes how to set up a tax integration profile, update customer settings for issuing VAT invoices, and set up VAT invoice descriptions for China in Microsoft Dynamics 365 Finance.

This procedure uses the demo data company CNMF.

Before you can execute the procedure, you must complete the following procedures:

- Golden tax integration import setup
- Maintain golden tax export format procedure

To set up basic tax integration profile for China, follow these steps:

1. In Dynamics 365 Finance, go to **Tax \> Setup \> Tax integration \> Tax integration profiles**.
1. Select **New**.
1. In the **Profile ID** field, enter a value.
1. In the **Profile name** field, enter a value.
1. In the **Sales tax code** field, enter or select a value.
1. In the **Validate amount limit** field, select **Yes**.
1. In the **Maximum invoice amount** field, enter a number.
1. In the **Include tax** field, select **Yes**.
1. In the **Default commodity** field, enter a value.
1. In the **Invoice auditor** field, enter or select a value.
1. In the **Payment collector** field, enter or select a value.
1. In the **Format mapping** field, enter or select a value.
1. In the **Non-deductible VAT invoices** field, select **Yes**.
1. Expand the **Default value of description and unit** section.
1. Select **New**.
1. In the list, mark the selected row.
1. In the **Description** field, enter a value.
1. In the **Unit** field, enter or select a value.
1. Go to **Accounts receivable \> Customers \> All customers**.
1. Select a customer.
1. Select **Registration IDs**.
1. Select **Add**.
1. In the **Registration type** field, enter or select a value.
1. In the **Registration number** field, enter a value.
1. Select **Save**.
1. Close the page.
1. Expand the **Invoice and delivery** section.
1. Select **Edit**.
1. In the **Sales tax group** field, enter or select a value.
1. Go to **Tax \> Setup \> Tax integration \> VAT invoice description**.
1. Select **New**.
1. In the **VAT invoice description ID** field, enter a value.
1. In the **Description** field, enter a value.
1. In the **Unit** field, enter or select a value.
1. Select **Save**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
