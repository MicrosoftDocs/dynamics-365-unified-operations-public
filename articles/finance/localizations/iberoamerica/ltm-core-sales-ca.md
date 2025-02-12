---
title: Sales Authorization Code for Latin America
description: Learn about the required configuration and usage of the Sales CA functionality for Latin America.
author: Fhernandez0088
ms.date: 02/12/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Sales Authorization Code for Latin America

This article explains how to configure and use the **Sales CA** functionality for Latin America.

This functionality allows you to assign an additional number to a purchase or sales invoice in a field named "Sales CA" in the LATAM section from the selected invoice.

This number can be assigned manually or automatically.

## Prerequisites to enter a manual Sales CA number

Before you can assign a manual **Sales CA** number to a purchase or sales invoice, the following prerequisites must be met:

- The company/region of the legal entity must be in a LATAM supported country.
- The LATAM general and the country specific features must be enabled.


- In the **Document class** configuration set the **Require CA number** slider to **Yes**.
- In the **Document class** configuration set the entry type of the document mask to **Manual**.

Learn more in [Document classes for Latin America](https://learn.microsoft.com/dynamics365/finance/localizations/iberoamerica/ltm-core-document-class).

## Enter a manual Sales CA number in a sales or purchase invoice

When posting a purchase or sales invoice in the LATAM section manually complete the **CA number** and the **CA due date** fields.

After completing the rest of the information needed, post the invoice and the number will be recorded in the transaction.

## Prerequisites to enter an automatic Sales CA number

Before you can assign an automatic **Sales CA** number to a purchase or sales invoice, the following prerequisites must be met:

- The company/region of the legal entity must be in a LATAM supported country.
- The LATAM general and the country specific features must be enabled.
- In the **Document class** configuration set the **Require CA number** slider to **Yes**.
- In the **Document class** configuration set the entry type of the document mask to **Auto**.
- In the **Sales point prefix** configuration that you want to use set the **Validate CA** slider to **Yes**.

Learn more in [Sales point prefixes for Latin America](https://learn.microsoft.com/dynamics365/finance/localizations/iberoamerica/ltm-core-sales-point-prefixes).

## Automatic Sales CA configuration

1. Go to the **Document class sales point** of the **Document class** that you want to with the invoice and select **Sales CA** in the top menu.
2. Select **New**.
3. In the **Authorization code (CA)** field enter the authorization code desired.
4. Enter the period when the Sales CA will be valid in the **Date from** and **Date to** fields.
5. Enter the document number interval where the Sales CA will be valid.

Learn more in [Document class sales point for Latin America](https://learn.microsoft.com/dynamics365/finance/localizations/iberoamerica/ltm-core-document-class-sales-point)

## Automatically assign a Sales CA number in a sales or purchase invoice.

When posting an invoice, in the LATAM section select the document class and sales point configured with the Sales CA setup and the fields **CA number** and **CA due date** should appear filled with the Sales CA number and due date previously configured.
