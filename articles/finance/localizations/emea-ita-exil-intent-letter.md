---
# required metadata

title: Intent letters - Invoicing usual exporters
description: This topic provides information about how to set up intent letters and use them when issuing invoices.
author: ilkond
manager: AnnBe
ms.date: 02/03/2020
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
ms.search.validFrom: 2020-01-01
ms.dyn365.ops.version: 10.0.9

---

# Intent letters - Invoicing of usual exporters

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

To be able to receive a supply of goods or services free of sales tax in Italy, companies that are considered usual exporters must send an intent declaration (a numbered and dated letter) to the Italian tax authorities and to compamies' contragents. 
 

## Prerequisites

The following prerequisites must be met before invoicing.

- The primary address of the legal entity must be in Italy.
- The feature **Intent letters - invoicing of usual exporters** must be enabled. Go to the **Feature management** workspace to enable the feature. For more information, see [Feature management overview](../../fin-and-ops/get-started/feature-management/feature-management-overview.md).

## Set up Accounts receivable parameters

1. Go to **Accounts receivable** > **Setup** > **Accounts receivable parameters**.
2. On the **Ledger and sales tax** tab, in **Usual exporters** section, in **Usual exporter sales tax group** field, define a salex tax group specific for usual exportrs.
3. Additionally, if you want to activate the automatic assignment of intent letters during invoicing, enable the **Automatic intent letter assignment** parameter.

![Set up AR parameters](media/emea-ita-exil-intent-AR-parm.jpg)

## Set up Sales tax codes

In **Tax > Indirect taxes > Sales tax > Sales tax code**, for the selected Sales tax code, in **General** section, turn on **Affect intent letters** parameter.

![Set up Sales tax code](media/emea-ita-exil-intent-tax-setup.jpg)

## Set up Customers

1. Go to **Accounts receivable** > **Customers** > **All customers**.
2. Select a customer in the list, and in the **Invoice and delivery** section, mark the **Usual exporter** field to specify that the customer belongs to the group of usual exporters.

## Set up intent letters number sequence

1. Go to **Accounts receivable** > **Setup** > **Accounts receivable parameters**.
2. On the **Number sequences** tab, in **Internal letter number** field, specify the reference to the number sequence that will be used for intent letters numbering.

## Create intent letters
You can create a new intent letter for a selected customer. 

1. Go to **Accounts receivable** > **Customers** > **All customers**.
2. Select a customer in the list, select the **Sell** tab, and in the **Setup** group, select **Setup** > **Intent letters**.

![Intent letter](media/emea-ita-exil-intent-new-cust.jpg)

3. Select **New** and enter the data of a new intent letter.

![New intent letter](media/emea-ita-exil-intent-new-cust2.jpg)

Alternatively, you can create a new intent letter for any applicable customer by going to **Accounts receivable** > **Intent letters** > **Intent letters**.

The following actions are available for existing intent letters:
-	**Close intent letter** - Close an open intent letter.
-	**Cancel intent letter** - Cancel an intent letter. This operation will require a reason for cancellation.
-	**Update sales orders** - Update existing applicable sales orders with the reference to the intent letter.
-	**Open intent letter**  - Open a close intent letter.
-	**Posted sales tax** - Show the sales tax transactions related to the selected intent letter.

## Use intent letters
When you create a new sales order or a new free text invoice for a customer who is categorized as usual exporter, and the creation date is whithin the intent letter validity period, then the **Usual exporter Sales Tax Group** will be used in the order/invoice and the intent letter number will be populated if the automatic intent letters assignment parameter is activated.

![New order](media/emea-ita-exil-intent-new-order.jpg)

If the amount of the invoice transaction does not exceed the amount of the intent letter, it will not be the subject for the sales tax calculation. 

The details of the intent letter will be also included into a printable layout of the invoice. 

![Print invoice](media/emea-ita-exil-intent-inv-print.jpg)

