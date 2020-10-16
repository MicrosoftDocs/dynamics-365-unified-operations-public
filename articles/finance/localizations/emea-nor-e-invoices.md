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
2. On the **Tax registration** FastTab, fill in company VAT number in **Tax registration number** field.
3. On the **Registration numbers** FastTab, turn on the **Print Foretaksregisteret on sales documents** option for Norway.
4. On the **Bank account information** FastTab, 
  - Fill in company organization number in **Routing number** field.
  - Define company bank account in **Bank account** field.
> [!NOTE]
> Company bank account must be preliminary set up in **Cash and bank management** > **Bank accounts** > **Bank accounts**.

### Configure Customer parameters


### Units of measure configuration

1. Go to **Organization administration** \> **Setup** \> **Units** > **Units**.
2. Open **External codes** for a selected unit.
3. In **Overview** section, in **Code** field, enter a code which coincides selected unit id.
4. In **Value** section, in **Value** field, enter an external code will be used as international trade units of measure codes recommended by United Nations Economic Commission for Europe ([UN/ECE](https://docs.peppol.eu/poacc/billing/3.0/codelist/UNECERec20/)).

![Units of measure configuration](media/emea-nor-ger-units.jpg)

### Sales tax codes transformation
When generating electronic invoices, the rates of the sales tax codes are being analyzed and transformed to [UNCL5305-compliant codes](https://docs.peppol.eu/pracc/catalogue/1.0/codelist/UNCL5305/) according to the following logic:

...
