---
# required metadata

title: Configurable posting profiles for banks and remittance types
description: This topic provides information about configuring posting profiles for banks and remittance types.
author: ilkond
manager: AnnBe
ms.date: 03/09/2020
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
ms.search.validFrom: 2020-06-01
ms.dyn365.ops.version: 10.0.10

---

# Configurable posting profiles for banks and remittance types

[!include [banner](../includes/banner.md)]

You can set up different posting profiles for the remittance of a bill of exchange (remit for collection and remit discount) and a promissory note in company bank accounts, in addition to general functionality settings. For more information, see [Set up bills of exchange](../accounts-receivable/set-up-bills-exchange.md). 

## Prerequisites

Before you can post financial transactions for invoices that have a total amount of zero (0), the following prerequisites must be met:

- The primary address of the legal entity must be in Italy.
- The feature, **Configurable posting profiles for banks and remittance types** must be enabled in the **Feature management** workspace. For more information, see [Feature management overview](../../fin-and-ops/get-started/feature-management/feature-management-overview.md).


## Set up a posting profile for a remittance journal line offset account
Open a company bank account to set up posting profiles. The system will use the posting profiles in remittance journal lines for an offset account when posting a bill of exchange or a prommisory note remittance journal.

1. To set up the posting profile, go to **Cash and bank management** \> **Bank accounts** \> **Bank accounts**. 
2. On the **General** FastTab, select the possting profile for **Collection**, **Discount** and **Promissory note**, if necessary.

![Bank account setup](media/emea-ita-exil-different%20accounts%20per%20company%20bank%26remittance%20type.PNG)

## Use posting profiles in remittance journal posting
If posting profiles have been set up in the bank account, the system will use these to specify the offset account when posting a remittance journal. If these posting profiles are not set up, the system selects the posting profile from **Accounts receivable parameters** and **Accounts payable parameters** pages on the **Ledger and sales tax** tab.


