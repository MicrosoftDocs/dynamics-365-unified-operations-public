---
title: Configurable posting profiles for banks and remittance types
description: Learn about how to configure posting profiles for banks and remittance types, including an outline on setting up a posting profile for a remittance journal.
author: mrolecki
ms.author: johnmichalak
ms.topic: article
ms.date: 12/16/2025
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Italy
ms.search.validFrom: 2020-06-01
ms.search.form: 
ms.dyn365.ops.version: 10.0.10
---

# Configurable posting profiles for banks and remittance types

[!include [banner](../../includes/banner.md)]

In addition to defining general functionality settings, you can set up different posting profiles for the remittance of a bill of exchange (remit for collection and remit for discount) and the remittance of a promissory note in company bank accounts. For more information, see [Set up bills of exchange](../../accounts-receivable/set-up-bills-exchange.md).

## Prerequisites

Before you can use different posting profiles for the remittance of a bill of exchange and the remittance of a promissory note in company bank accounts, the following prerequisites must be met:

- The primary address of the legal entity must be in Italy.
- The **Configurable posting profiles for banks and remittance types** feature is turned on in the **Feature management** workspace. For more information, see [Feature management overview](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview).

## Set up a posting profile for a remittance journal line offset account

To set up posting profiles, open a company bank account. When the system posts a bill of exchange or a promissory note remittance journal, it uses the posting profiles on remittance journal lines for an offset account.

1. To set up the posting profile, go to **Cash and bank management** > **Bank accounts** > **Bank accounts**.
1. On the **General** FastTab, in the **Posting profiles** section, in the **Remit for collection**, **Remit for discount**, and **Remit promissory note** fields, select a posting profile, as you require.

:::image type="content" source="../media/emea-ita-exil-different-accounts-per-company-bank.png" alt-text="Screenshot of the bank account setup page showing posting profiles section with Remit for collection, Remit for discount, and Remit promissory note fields.":::

## Use posting profiles in remittance journal posting

If you set up posting profiles in the bank account, the system uses them to specify the offset account when you post a remittance journal. If you don't set up posting profiles, the system selects the posting profile from the **Ledger and sales tax** tab on the **Accounts receivable parameters** and **Accounts payable parameters** pages.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
