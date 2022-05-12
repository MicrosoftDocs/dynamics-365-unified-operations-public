---
# required metadata

title: Electronic invoices in Poland
description: This topic explains how to configure and process electronic invoices in Poland.
author: ikond
ms.date: 05/12/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend

# ms.tgt_pltfrm: 
ms.custom: 574537
ms.search.region: Poland
# ms.search.industry: 
ms.author: ilyako
ms.search.validFrom: 2022-07-15
ms.dyn365.ops.version: 10.0.28

---

# Electronic invoices in Poland

[!include [banner](../includes/banner.md)]

According to Polish legal requirements, invoices that are issued to customers must be generated in an electronic format and submitted to the Polish National electronic invoicing system (KSEF). 
To generate electronic invoices, the following two-part system configuration is required.

- **Electronic invoicing service** configuration. For more information, see [Get started with the Electronic invoicing add-in for Poland](e-invoicing-sa-get-started.md).
- **Microsoft Dynamics 365 Finance** configuration, which is covered in this topic.

## Prerequisites

- Electronic invoicing service configuration must be completed, and all required parts for Poland must be ready to use.
- The primary address of the legal entity must be in Poland.
- In the **Feature management** workspace, the **ZZZ** feature must be enabled. For more information, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Configure legal entity data

### Enter a legal entity's address

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
2. Select a legal entity, and then, on the **Addresses** FastTab, add a valid primary address for the legal entity.

### Enter a legal entity's tax registration number

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
2. Select a legal entity, and then, on the **Tax registration** FastTab, in the **Tax registration number** field, enter a valid tax registration number for the legal entity. This number will be used as the seller's value-added tax (VAT) identifier.

## Configure customer data

### Enter a customer's address

1. Go to **Accounts receivable** \> **Customers** \> **All customers**.
2. Select a customer, and then, on the **Addresses** FastTab, add a valid address for the customer.

### Enter a customer's tax registration number

1. Go to **Accounts receivable** \> **Customers** \> **All customers**.
2. Select a customer, and then, on the **Invoice and delivery** FastTab, in the **Tax exempt number** field, enter a valid tax registration number for the customer. This number will be used as the buyer's VAT identifier.

![Invoice printout](media/sau-qr-invoice.jpg)

## Configure additional data

Electronic properties.

## Issue electronic invoices

When you've completed all the required configuration steps, you can generate electronic invoices for posted invoices. For more information about how to generate electronic invoices, see [Issue electronic invoices in Finance and Supply chain management](e-invoicing-issuing-electronic-invoices-finance-supply-chain-management.md).

## Related topics

- [Get started with the Electronic invoicing add-in for Poland](e-invoicing-sa-get-started.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
