---
title: Electronic invoicing service ISV connector
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

# Electronic invoicing service ISV last-mile connector

[!include [banner](../../includes/banner.md)]

Independent Software Vendor (ISV) last-mile connector complements the standard Electronic Invoicing Service functionality in the cases when no direct integration with final recepients is supported out of the box. In such scenarios Microsoft D365 Finance is used for the generation of electronic documents in legally required formats and then passes it to the ISV last-mile connector for further communication. In case of incoming electronic documents, the ISV last-mile connector is used as a source inbound documents which then will be handeled by Microsoft D365 Finance.

This article provides information about how to configure and use the Electronic Invoicing service ISV last-mile connector.

## Prerequisites

Before you begin the procedures in this article, complete the following prerequisites:

  > [!IMPORTANT]
- Your company must have a separate signed service agreement with an Independent Software Vendor (ISV) who will provide electronic documents delivery service and obtain the required credentials to enable integration of the Electronic Invoicing service with the ISV connector. 
- Become familiar with Electronic invoicing functionality - [Electronic invoicing overview](../global/e-invoicing-service-overview.md).
- Consult the list of [available Electronic invoicing features](e-invoicing-country-specific-availability.md).

## Integration with Edicom

This chapter provides the information how to configure and use the Electronic Invoicing ISV last-mile connector's integration with the Global e-Invoicing Platform provided by [Edicom](https://edicomgroup.com/electronic-invoicing).

The following required credentials must be prliminary obtailned from **Edicom** to enable integration of the Electronic Invoicing service with the list-mile connector. 

- The **Service ID** which uniquely identifies the company by Edicom.
- The **Group** which is required for internal routing within the Edicom infrastructure.
- The **Token** which grants the authorization to access the Edicom services.

These credentials must be uploaded to the secrets created in the **Azure Key Vault** managed by your company, for more information see [Customer certificates and secrets](../global/e-invoicing-customer-certificates-secrets.md). Then the secrets will be used in the related Electronic Invoicing feature pipeline actions as parameters.

### Electronic invoices submission

The following pipeline actions are introduced for enabling outbound documents submission via the ISV list-mile connector.

- **Integrate with Edicom**

 **Parameter**                                            | **Value** | **Description**     |
|-----------------------------------------------------------------|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Service URI | ssssss | Default value provided. No change needed.|
| ...                   | ...   |                   |
  
- **Waiting for response from Edicom**
- **Get status from Edicom**

### Electronic invoices receiption

The **Edicom service** feature setup type is introduced for enabling inbound documents receiving via ISV the list-mile connector.

The following pipeline actions are introduced for enabling integration via ISV the list-mile connector.


### Integration with "NemHandel" in Denmark

For the details of the electronic invoicing in Denmark, including the integration with [NemHandel](https://nemhandel.dk/) electronic invoicing infrastructure, refer to [Get started with Electronic invoicing for Denmark](../mea/e-invoicing-dk-get-started.md)

9. <a id="OutputFile"></a>On the 
you [created earlier](#OutputFile).


    > [!NOTE]
    > The **Vendor invoice import (DK)** format configuration is based on the parent **Vendor invoice import** format configuration. The formats use the **Invoice model** configuration and the **Vendor invoice Mapping to destination** configuration. All required additional configurations are automatically imported.

![Property type added on the Electronic document property types page.](../media/emea_dk_format_type_setup.jpg)

## Additional resources

- [Forced electronic invoices generation](../europe/emea-eur-forced-einvoices.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

