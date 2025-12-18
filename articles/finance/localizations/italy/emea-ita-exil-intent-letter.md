---
title: Intent letters - Invoicing usual exporters
description: Learn about how to set up intent letters and how to use them when you issue invoices, including a process for setting up accounts receivable parameters.
author: mrolecki
ms.author: johnmichalak
ms.topic: article
ms.date: 12/16/2025
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Italy
ms.search.validFrom: 2020-01-01
ms.search.form: 
ms.dyn365.ops.version: 10.0.9
---

# Intent letters - Invoicing of usual exporters

[!include [banner](../../includes/banner.md)]

To receive a supply of goods or services free of sales tax in Italy, companies that are categorized as usual exporters must send an intent declaration (a numbered and dated letter) to the Italian tax authorities and to company counteragents.

## Prerequisites

Before you invoice, make sure that the following prerequisites are met:

- The primary address of the legal entity is in Italy.
- The **Intent letters - invoicing of usual exporters** feature is turned on in the **Feature management** workspace. For more information, see [Feature management overview](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Set up Accounts receivable parameters

1. Go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
1. On the **Ledger and sales tax** tab, on the **Usual exporters** FastTab, in the **Usual exporter sales tax group** field, define a sales tax group that you use only for usual exporters.
1. Set the **Automatic intent letter assignment** option to **Yes** to turn on the automatic assignment of intent letters during invoicing.

:::image type="content" source="../media/emea-ita-exil-intent-AR-parm.jpg" alt-text="Screenshot of the Accounts receivable parameters page.":::

## Set up sales tax codes

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax code**.
1. Select a sales tax code. On the **General** FastTab, in the **Invoicing** section, set the **Affect intent letters** option to **Yes**.

:::image type="content" source="../media/emea-ita-exil-intent-tax-setup.jpg" alt-text="Screenshot of the sales tax code setup page.":::

## Set up customers

1. Go to **Accounts receivable** \> **Customers** \> **All customers**.
1. Select a customer. In the **Invoice and delivery** section, select the **Usual exporter** option to indicate that the customer belongs to the group of usual exporters.

## Set up a number sequence for intent letters

1. Go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
1. On the **Number sequences** tab, in the **Internal letter number** field, specify the reference to the number sequence that you want to use to number intent letters.

## Create an intent letter

Follow these steps to create an intent letter for a selected customer.

1. Go to **Accounts receivable** \> **Customers** \> **All customers**.
1. Select a customer. On the Action Pane, on the **Sell** tab, in the **Setup** group, select **Setup** \> **Intent letters**.
1. Select **New**.
1. Enter the data for the new intent letter.

Alternatively, you can create an intent letter for any applicable customer by going to **Accounts receivable** \> **Intent letters** \> **Intent letters**.

The following actions are available for existing intent letters:

- **Close intent letter** – Close an open intent letter.
- **Cancel intent letter** – Cancel an intent letter. This operation requires a reason for cancellation.
- **Update sales orders** – Update existing applicable sales orders with the reference to an intent letter.
- **Open intent letter** – Open an intent letter that was closed.
- **Posted sales tax** – Show the sales tax transactions that are related to the selected intent letter.

## Using intent letters

When you create a sales order or a free text invoice for a customer who is categorized as a usual exporter, if the creation date is in the validity period of the intent letter, the system uses the **Usual exporter sales tax group** value in the order or invoice. If you set the **Automatic intent letter assignment** option to **Yes**, the intent letter number is entered automatically.

:::image type="content" source="../media/emea-ita-exil-intent-new-order.jpg" alt-text="Screenshot of a new sales order.":::

The system calculates sales tax on the invoice transaction amount only if it doesn't exceed the amount of the intent letter.

The printable layout of the invoice also includes the details of the intent letter.

:::image type="content" source="../media/emea-ita-exil-intent-inv-print.jpg" alt-text="Screenshot of the print invoice layout.":::

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
