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

## RCS
...RCS, follow these steps:

1. Consult the list of [generally available Electronic invoicing features](../e-invoicing-configuration-rcs.md#generally-available-features).
2. Select and import the Electronic invoicing feature. For more information, see [Import an Electronic invoicing feature from Microsoft configuration provider](../e-invoicing-get-started.md#import-an-electronic-invoicing-feature-from-the-microsoft-configuration-provider).
3. Create an Electronic invoicing feature for your organization. For more information, see [Create an Electronic invoicing feature under your organization provider](../e-invoicing-get-started.md#create-an-electronic-invoicing-feature-under-your-organization-provider).


## Additional resources

- [Forced electronic invoices generation](../europe/emea-eur-forced-einvoices.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

