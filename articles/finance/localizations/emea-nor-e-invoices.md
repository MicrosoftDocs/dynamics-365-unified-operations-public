---
# required metadata

title: Customer electronic invoices in Norway
description: This topic explains how to set up and process customers electronic invoices in Norway.
author: ilkond
manager: AnnBe
ms.date: 10/14/2020
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
ms.search.region: Norway
# ms.search.industry: 
ms.author: ilyako
ms.search.validFrom: 2019-11-01
ms.dyn365.ops.version: 10.0.08

---

# Customer electronic invoices in Norway

[!include [banner](../includes/banner.md)]

To comply with European Union's Directive 2014/55/EU, Norway-specific format of electronic invoices has been imlemented - **EHF Billing 3.0** based on [PEPPOL Billing 3.0](https://docs.peppol.eu/poacc/billing/3.0/) specification.

This article describes how to configure and issue customers electronic invoices in Norway.

## Prerequisites

- The primary address of the legal entity must be in Norway.

## Import Electronic reporting configurations
In the **Electronic reporting** workspace, import the following Electronic reporting (ER) formats from the repository:

- OIOUBL Sales invoice
- OIOUBL Project invoice
- OIOUBL Sales credit note
- OIOUBL Project credit note

> [!NOTE]
> These formats are based on the **Invoice model** configuration, and use the **Invoice model mapping** configuration. All required additional configurations will be automatically imported.

For more information about how to import ER configurations, see [Download Electronic reporting configurations from Lifecycle Services](../../dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

### Make the references to the imported ER formats configurations

1. Go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
2. On the **Electronic documents** tab, define the references to the imported formats:

![Configuring Electronic documents](media/emea-nor-ger-configs.jpg)


## Configure parameters

### Configure Legal entity parameters

1. Go to **Organization administration** \> **Organization** \> **Legal entities**.
2. On the **Tax registration** FastTab, fill in company VAT naumber in **Tax registration number** field.
3. On the **Registrationnumbers** FastTab, turn on the **Print Foretaksregisteret on sales documents** option for Norway.
4. On the **Bank account information** FastTab, 
  - Fill in company organization number in **Routing number** field.
  - Define company bank account in **Bank account** field.
> [!NOTE]
> Company bank account must be preliminary set up in **Cash and bank management** > **Bank accounts** > **Bank accounts**.

