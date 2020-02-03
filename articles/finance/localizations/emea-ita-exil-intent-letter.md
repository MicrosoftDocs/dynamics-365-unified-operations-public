---
# required metadata

title: Intent letters - invoicing of usual exporters
description: Intent letters - invoicing of usual exporters.
author: ilkond
manager: AnnBe
ms.date: 11/11/2019
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

# Intent letters - invoicing of usual exporters

[!include [banner](../includes/banner.md)]

In Italy, companies that are considered as usual exporters must send an intent declaration (a numbered and dated letter) to the Italian tax authorities and to compamies' contragents in order to receive a supply of goods or services free of sales tax. 

This article explains how to setup intent letters and use it during invoices issuing.
 

## Prerequisites

- The primary address of the legal entity must be in Italy.
- In the **Feature management** workspace, turn on the **Intent letters - invoicing of usual exporters** feature. For more information, see [Feature management overview](../../fin-and-ops/get-started/feature-management/feature-management-overview.md).

## Set up Accounts receivable parameters
In **Accounts receivable > Setup > Accounts receivable parameters**, in **Ledger and sales tax**, in **Usual exporters** section, in **Usual exporter sales tax group** field define a salex tax group specific for usual exportrs.

Additionally, turn on **Automatic intent letter assignment** parameter if you want to activate automatic assignment of intent letters when invoicing.

![Set up AR parameters](media/emea-ita-exil-intent-AR-parm.jpg)
## Set up Sales tax codes
In **Tax > Indirect taxes > Sales tax > Sales tax code**, for the selected Sales tax code, in **General** section, turn on **Affect intent letters** parameter.
![Set up Sales tax code](media/emea-ita-exil-intent-tax-setup.jpg)

## Set up Customers
In **Accounts receivable > Customers > All customers**, for the selected Customer, in **Invoice and delivery** section, turn on **Usual exporter** parameter to specify that the customer belongs to usual exporters.

## Set up intent letters number sequence
In **Accounts receivable > Setup > Accounts receivable parameters**, in **Number sequences** tab, in **Internal letter number** field specify the reference to the number sequence that will be used for intent letters numbering.

## Create intent letters
You can create a new intent letter for a selected customer. In **Accounts receivable > Customers > All customers**, for the selected Customer, in **Sell** menu section, select **Setup > Intent letters**.

![Intent letter](media/emea-ita-exil-intent-new-cust.jpg)

Then click on **New** button and enter the data of a new intent letter.
![New intent letter](media/emea-ita-exil-intent-new-cust2.jpg)

Alternatively, you can create a new intent letter for any applicable customer in **Accounts receivable > Intent letters > Intent letters**.

The following actions are available for existing intent letters:
-	Close intent letter - will close an open intent letter;
-	Cancel intent letter - will cancel an intent letter. This operation will require to enter a reason of cancellation;
-	Update sales orders - user can update existing applicable sales orders with the reference to the intent letter;
-	Open intent letter  - will open a close intent letter;
-	Posted sales tax - will show the Sales tax transactions related to the selected intent letter.

## Use intent letters
When you create a new sales order or a new free text invoice for a customer who is categorized as usual exporter and the creation date is whithin the intent letter validity period then **Usual exporter Sales Tax Group** will be used in the order/invoice and the intent letter number will be populated if automatic intent letters assignment parameter is activated.

![New order](media/emea-ita-exil-intent-new-order.jpg)


> [!NOTE]
> Warning...
