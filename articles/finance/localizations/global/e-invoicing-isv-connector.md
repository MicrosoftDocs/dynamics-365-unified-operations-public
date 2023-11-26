---
title: Use the electronic invoicing service ISV connector
description: This article provides information about how to configure and use the Electronic Invoicing service ISV connector.
author: ikondratenko
ms.date: 11/15/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: 
ms.search.validFrom: 2023-12-01
ms.dyn365.ops.version: AX 10.0.37
ms.collection: get-started
ms.assetid: 
ms.search.form: 
---

# Use the electronic invoicing service ISV last-mile connector

[!include [banner](../../includes/banner.md)]

Independent Software Vendor (ISV) last-mile connector complements the standard Electronic Invoicing Service functionality in the cases when no direct integration with final recepients is supported out of the box. In such scenarios Microsoft D365 Finance is used for the generation of electronic documents in legally required formats and then passes it to the ISV last-mile connector for further communication. In case of incoming electronic documents, the ISV last-mile connector is used as a source inbound documents which then will be handeled by Microsoft D365 Finance.

This article provides information about how to configure and use the Electronic Invoicing service ISV last-mile connector.

## Prerequisites

Before you begin the procedures in this article, complete the following prerequisites:

- The company must be registered in the [Danish Central Business Register (CVR)](https://datacvr.virk.dk/) and in the Danish electronic invoicing infrastructure [NemHandel](https://nemhandel.dk/).
  > [!IMPORTANT]
- The company must have a signed agreement with the provider of electronic documents delivery service and obtain the required credentials to enable integration of the electronic invoicing service with the ISV connector. For more information, see [ Use the electronic invoicing service ISV connectors](../global/e-invoicing-isv-connector.md)
- Become familiar with Electronic invoicing as it's described in [Electronic invoicing overview](../global/e-invoicing-service-overview.md) and [Electronic invoicing components](../global/e-invoicing-administration-integration-components.md).
- Sign up for RCS, and set up Electronic invoicing. For more information, see the following articles:

    - [Sign up for and install the Electronic Invoicing service](../global/e-invoicing-sign-up-install.md)
    - [Set up Electronic invoicing](../global/e-invoicing-set-up-overview.md)  
- Activate the integration between your Finance and the Electronic Invoicing service as described in [Activate and setup integration with Electronic invoicing](../global/e-invoicing-activate-setup-integration.md).
- Create secrets in Azure Key Vault, and set up Key Vault as described in [Customer certificates and secrets](../global/e-invoicing-customer-certificates-secrets.md):

## RCS
...RCS, follow these steps:

1. Consult the list of [generally available Electronic invoicing features](e-invoicing-country-specific-availability.md).



9. <a id="OutputFile"></a>On the 
you [created earlier](#OutputFile).


    > [!NOTE]
    > The **Vendor invoice import (DK)** format configuration is based on the parent **Vendor invoice import** format configuration. The formats use the **Invoice model** configuration and the **Vendor invoice Mapping to destination** configuration. All required additional configurations are automatically imported.

![Property type added on the Electronic document property types page.](../media/emea_dk_format_type_setup.jpg)

## Additional resources

- [Forced electronic invoices generation](../europe/emea-eur-forced-einvoices.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

