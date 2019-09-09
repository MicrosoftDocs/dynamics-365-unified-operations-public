---
# required metadata

title: Separate accounts for credit notes
description: This topic provides information about how to set up and use separate accounts for credit notes.
author: ilkond
manager: AnnBe
ms.date: 09/09/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Italy
# ms.search.industry: 
ms.author: ilyako
ms.search.validFrom: 2019-11-01
ms.dyn365.ops.version: 10.0.7

---

# Separate accounts for credit notes

In Italy, a company can define the accounting policy for posting credit note amounts to ledger accounts that are different from the revenue accounts. This is done to specifically track the amount issued on the credit notes.

## Prerequisites

- The primary address of the legal entity must be in Italy.
- In **Feature management**, enable the feature, **Separate accounts for credit notes**. For more information, see [Feature management overview](../../fin-and-ops/get-started/feature-management/feature-management-overview.md)

## Posting accounts setup 
You can define specific ledger accounts for use with sales orders. To do this, on the **Posting** page, select **Credit notes** and specify the ledger accounts.

You can also use this page to set up different accounts for various combinations of customers, items, and related groups.

![Posting accounts setup](media/emea-ita-exil-separate-account-credit-pic1.jpg)

## Posting credit notes
### New credit note
When you post a new credit note, the ledger account will be used instead of the standard revenue account that is defined in the sales order.

If no separate ledger account for the credit note is defined or a required Customer/Item combination is not found, then a standard sales order revenue account will be used for posting.

### Credit note created from a sales order
If you create a credit note based on an existing sales order, clear the **Main account** field of each credit note line as the field might be pre-populated with a revenue account from the sales order.

![Main account clearing](media/emea-ita-exil-separate-account-credit-pic2.JPG)

> [!NOTE] 
> Separate accounts are applicable only for credit notes that are based on sales orders. Separate accounts are not applicable for free text credit notes because they require a ledger account to be explicitly entered.
