---
# required metadata

title: Free text invoices in the public sector
description: This article describes the free text invoice functionality that's available for public sector entities, and answers common questions about using billing classifications and billing codes with free text invoices.
author: v-kiarnd
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: CustBillingClassification, CustBillingCode, CustFreeInvoice
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.assetid: 483e2726-ec48-4d1f-82f5-bffddea301ce
ms.search.region: Global
ms.search.industry: Public sector
ms.author: twheeloc
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Free text invoices in the public sector

[!include [banner](../includes/banner.md)]

This article describes the free text invoice functionality that's available for public sector entities, and answers common questions about using billing classifications and billing codes with free text invoices.

## Do I have to select a billing classification for every free text invoice?

Yes, when billing classifications are enabled, you have to enter a billing classification for every free text invoice. The billing classification controls which billing codes that you can enter on the invoice. It also governs payment terms and conditions, number sequences, and the processing of the invoice. To learn more about billing classifications, see [Billing classifications and billing codes in the public sector](billing-classifications-billing-codes-public-sector.md).

## What happens if I’ve already created free text invoices when I enable billing classifications?
If an invoice was not yet posted when you enabled billing classifications, you have to assign a billing classification to the invoice before you can post it. When you open the page to view the invoice, you'll get a message telling you that the billing classification is required.

## Why should I use billing codes when I create free text invoices?
When you select a billing code, default values are automatically entered in many fields on the invoice line. This makes data entry faster and more accurate. Billing codes are also used with posting definitions to control how Accounts receivable transactions are posted to the ledger.

## I’m creating a free text invoice, and the billing code that I want to use isn’t available. What should I do?
First make sure that the invoice is using the right billing classification. Only certain billing codes can be used with each billing classification. If the billing classification is correct, then you should select one of the billing codes that are available for the free text invoice that you are creating.

## I can change some of the fields on my free text invoices all of the time, and I can change all of the fields some of the time. But some of the fields I can only change some of the time. What’s up with that?
Settings on the billing code control whether you can change certain fields.

-   If the billing code on a free text invoice line doesn’t allow rate changes on the invoice, you can’t change the amount, the unit price, or the amount details on the line. 

> [!TIP] 
> If the **Billing code determines** field is set to unit price, you can’t change the unit price, but you can change the amount indirectly by changing the quantity.

-   If the billing code on a free text invoice line doesn’t allow changes to the ledger accounts, you can’t change the accounting distributions on the line. You can change the main account that displays on the free text invoice line, but that change affects only what is displayed. Changing the main account does not affect the distributions.
-   When there’s a project associated with the invoice line, the billing code controls whether you can change the project ID, category, and ledger account. 

> [!TIP] 
> To change the ledger account for invoice lines related to projects, changes have to be allowed both on the billing code itself and on the Projects section of the Accounts receivable parameters page.

To learn more about billing codes, see [Billing classifications and billing codes in the public sector](billing-classifications-billing-codes-public-sector.md).

## Where does the interest code on a free text invoice come from?
The interest code can be set on the billing code, the billing classification, or the posting profile.







[!INCLUDE[footer-include](../../includes/footer-banner.md)]
