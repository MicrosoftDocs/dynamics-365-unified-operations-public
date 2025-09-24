---
title: Sales authorization code for Latin America
description: Learn how to configure and use the Sales CA functionality for Latin America.
author: Fhernandez0088
ms.date: 02/12/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Sales authorization code for Latin America

This article explains how to configure and use the sales authorization code (Sales CA) functionality for Latin America. This functionality lets you use the field for the Sales CA number in the **LATAM** section of purchase and sales invoices to assign an additional number to a selected invoice.

The Sales CA number can be assigned either manually or automatically.

## Manual assignment of Sales CA numbers

### Prerequisites

Before you can manually assign Sales CA numbers to purchase or sales invoices, the following prerequisites must be met:

- The company/region of the legal entity must be in a LATAM-supported country.
- Both the general LATAM feature and the country/region-specific LATAM feature must be enabled.
- In the **document class** configuration, set the **Require CA number** option to **Yes**.
- In the **document class** configuration, set the entry type of the document mask to **Manual**.

Learn more in [Document classes for Latin America](ltm-core-document-class.md).

### Manually assign a Sales CA number to a sales or purchase invoice

When you manually post a purchase or sales invoice, in the **LATAM** section, set the **CA number** and **CA due date** fields.

After you complete the rest of the required information, post the invoice. The Sales CA number is recorded in the transaction.

## Automatic assignment of Sales CA numbers

### Prerequisites

Before Sales CA numbers can be automatically assigned to purchase or sales invoices, the following prerequisites must be met:

- The company/region of the legal entity must be in a LATAM-supported country.
- Both the general LATAM feature and the country/region-specific LATAM feature must be enabled.
- In the **document class** configuration, set the **Require CA number** option to **Yes**.
- In the **document class** configuration, set the entry type of the document mask to **Auto**.
- In the **sales point prefix** configuration that you want to use, set the **Validate CA** option to **Yes**.

Learn more in [Sales point prefixes for Latin America](ltm-core-sales-point-prefixes.md).

### Configure automatic assignment of Sales CA numbers

1. Go to the document class sales point of the document class that you want to use with the invoice.
1. On the Action Pane, select **Sales CA**.
1. Select **New**.
1. In the **Authorization code (CA)** field, enter the desired authorization code.
1. In the **Date from** and **Date to** fields, define the period when the Sales CA number will be valid.
1. Enter the document number interval that the Sales CA number will be valid for.

Learn more in [Document class sales point for Latin America](ltm-core-document-class-sales-point.md).

### Automatically assign a Sales CA number to a sales or purchase invoice

When you post a purchase or sales invoicee, in the **LATAM** section, select the document class and sales point that are configured in the Sales CA number setup. The **CA number** and **CA due date** fields should automatically be set to the Sales CA number and due date that you previously configured.
