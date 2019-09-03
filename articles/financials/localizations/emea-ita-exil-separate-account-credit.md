---
# required metadata

title: Separate accounts for Credit memos
description: Separate accounts for Credit memos.
author: ilkond
manager: AnnBe
ms.date: 15/08/2019
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

In Italy companies can define accounting policy for posting credit notes amounts to ledger accounts that are different from revenue accounts in order to specificly underline the amount of issued credit notes.

This topic explains how to set up and use separate accounts for credit notes.

## Prerequisites
### Country/region
The primary address of the legal entity must be in Italy.
### Feature activation
In <strong>Feature management</strong> enable <strong>Separate accounts for credit notes</strong> feature.

For more information, see [Feature management overview](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/get-started/feature-management/feature-management-overview)

## Posting accounts setup 
Define specific ledger accounts for Sales orders on the **Posting** form using a new option for **Credit notes**.

You can set up different accounts for various combinations of specific Customers, Items
and related groups.

![Posting accounts setup](media/emea-ita-exil-separate-account-credit-pic1.jpg)


## Posting of credit notes
### Newly created credit note
When you post a credit note, the ledger account from setup above will be used instead of a standard revenue account defined for sales orders.

If no separate ledger account for credit note is defined or a required Customer/Item combination is not found then a standard sales order revenue account will be used when posting.
### Credit note created from a sales order
If you create a credit note based on an existing sales order, make sure **Main account** of each credit note line is cleared up. Initially it is pre-populated with a revenue account from the sales order.

![Main account clearing](media/emea-ita-exil-separate-account-credit-pic2.JPG)

> [!NOTE] 
    > Separate accounts are applicable only for credit notes based on sales orders and not applicable for Free text credit notes because Free text credit notes require a ledger account to be explicitly entered.
