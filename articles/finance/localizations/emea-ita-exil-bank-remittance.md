---
# required metadata

title: Configurable posting profiles for banks and remittance types
description: Configurable posting profiles for banks and remittance types.
author: ilkond
manager: AnnBe
ms.date: 01/14/2020
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

This functionality allows a user to set up different posting profiles for remittance of bills of exchange (remit for collection and remit discount) and promissory note in company bank accounts in addition to general functionality settings (See [Set up bills of exchange](https://docs.microsoft.com/en-us/dynamics365/finance/accounts-receivable/set-up-bills-exchange)). 

## Prerequisites

Before you can post financial transactions for invoices that have a total amount of 0 (zero), the following prerequisites must be met:

- The primary address of the legal entity must be in Italy.
- In the **Feature management** workspace, turn on the **Configurable posting profiles for banks and remittance types** feature. For more information, see [Feature management overview](../../fin-and-ops/get-started/feature-management/feature-management-overview.md).


## Setup of posting profile for remittance journal line offset account
Open a company bank account to set up posting profiles, which the system will use in remittance journal lines for offset account, when posting (Bill of exchange/ Prommisory note remittance journal):

**Cash and bank management** \> **Bank accounts** \> **Bank accounts**, **General** FastTab and select the possting profile for Collection, Discount and Promissory note (if needed).

![Bank account setup](media/emea-ita-exil-different%20accounts%20per%20company%20bank%26remittance%20type.PNG)

## Using set up posting profiles in remittance journal posting
If a user's set up posting profiles in the bank account the system will use these posting profiles for specifying the offset account when posting a remittance journal. If these posting profiles are not set up, the system selects the posting profile from Accounts receivable / Accounts payable parameters (**Accounts receivable** / **Accounts payable** \> **Setup**, **Ledger and sales tax** tab).   


