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

Independent Software Vendor (ISV) last-mile connector complements the standard Electronic Invoicing Service functionality in the cases when no direct integration with final recepients is supported out of the box. In such scenarios Microsoft Dynamics 365 Finance is used for the generation of electronic documents in legally required formats and then passes it to the ISV last-mile connector for further communication. In case of incoming electronic documents, the ISV last-mile connector is used as a source inbound documents which then will be handeled by Microsoft Dynamics 365 Finance.

This article provides information about how to configure and use the Electronic Invoicing service ISV last-mile connector.

## Prerequisites

Before you begin the procedures in this article, complete the following prerequisites:

  > [!IMPORTANT]
- Your company must have a separate signed service agreement with an Independent Software Vendor (ISV) who will provide electronic documents delivery service and obtain the required credentials to enable integration of the Electronic Invoicing service with the ISV last-mile connector. 
- Become familiar with Electronic invoicing functionality - [Electronic invoicing overview](../global/e-invoicing-service-overview.md).
- Consult the list of available country-specific [Electronic invoicing features](e-invoicing-country-specific-availability.md) which can be complemented with the submission possibility using the ISV last-mile connector.

## Integration with Edicom

This chapter provides the information how to configure and use the Electronic Invoicing ISV last-mile connector's integration with the Global e-Invoicing Platform provided by [Edicom](https://edicomgroup.com/electronic-invoicing).

The following required credentials must be prliminary obtailned from **Edicom** to enable integration of the Electronic Invoicing service with the list-mile connector. 

- The **Service ID** which uniquely identifies the company by Edicom.
- The **Group** which is required for internal routing within the Edicom infrastructure.
- The **Token** which grants the authorization to access the Edicom services.

The obtained **Token** must be uploaded to the secret created in the **Azure Key Vault** managed by your company, for more information see [Customer certificates and secrets](../global/e-invoicing-customer-certificates-secrets.md). Then the secret will be used in the related Electronic Invoicing feature pipeline actions as a parameter.

### Electronic invoices submission

The following pipeline actions are introduced for enabling outbound documents submission via the ISV list-mile connector.

- **Integrate with Edicom** - submits electronic documents generated using preceeding actions to Edicom. You need to configure the action's parameters described in the table below. 

 **Parameter**       | **Description**     |
|---------------------|------------------|
| **Domain** | Use the **Service ID** number provided by Edicom.|
| **Application**                | Use  the same **Service ID** number. |
| **Destination**                | Enter the **Service ID** number concatenated with the **_EDIWIN** value. For example, if the **Service ID** number is *123456* the **Destination** value should be *123456_EDIWIN*. |
| **Group**                  | Use the **Group** code provided by Edicom.  |
| **Auth token**                 | Select the name of the secret that you created for the token provided by Edicom.   |

The following parameters can be left unchanged with their default values provided by Microsoft in related globalization features.

 **Parameter**       | **Description**     |
|---------------------|------------------|
| **Web service URL** | Default value: **https://ipaasgw.edicomgroup.com**.|
| **Http request body**                | Default value: **Generate format: Output file**. |
| **Schema**                 | Default value: **OUT_XML_UBL_INVOICE_2_MICROSOFT_DK**.   |

The rest of the action's parameters can be left empty.
  
- **Waiting for response from Edicom** - waits for the response from Edicom. No specific paramters need to be additionally configured.
- **Process response** - ????????????????.

A new data channel type **Get status from Edicom** is implemented for feature setups of **Export channel and processing pipeline** type. You need to configure the Export channel's parameters described in the table below. 

 **Parameter**       | **Description**     |
|---------------------|------------------|
| **Domain** | Use the **Service ID** number provided by Edicom.|
| **Application**                | Use  the same **Service ID** number. |
| **Data channel**                | Enter the name of the [export channel](../mea/e-invoicing-dk-get-started.md#finance-configuration) configured in paragraph 7 of **Electronic document parameters** in Microsoft Dynamics 365 Finance. |
| **Group**                  | Use the **Group** code provided by Edicom.  |
| **Auth token**                 | Select the name of the secret that you created for the token provided by Edicom.   |

The following parameters can be left unchanged with their default values provided by Microsoft in related globalization features.

 **Parameter**       | **Description**     |
|---------------------|------------------|
| **Web service URL** | Default value: **https://ipaasgw.edicomgroup.com**.|
| **Document limit**                | Default value: **100**. |
| **Schema**                 | Default value: **IN_INVOICE_STATUS_MICROSOFT_DK**.   |

The rest of the action's parameters can be left empty.


### Electronic invoices receiption

A new data channel type **Edicom service** is implemented for feature setups of **Import channel** or **Import channel and processing pipeline** type. You need to configure the Export channel's parameters described in the table below. All remaining parameters can be left unchanged with their default values provided by Microsoft in the related globalization feature.

 **Parameter**       | **Description**     |
|---------------------|------------------|
| **Domain** | Use the **Service ID** number provided by Edicom.|
| **Application**                | Use  the same **Service ID** number. |
| **Data channel**                | Enter the name of the [import channel](../mea/e-invoicing-dk-get-started.md#receive-incoming-electronic-invoices) configured in paragraph 3 of **Electronic document parameters** in Microsoft Dynamics 365 Finance. |
| **Group**                  | Use the **Group** code provided by Edicom.  |
| **Auth token**                 | Select the name of the secret that you created for the token provided by Edicom.   |


### Electronic invoicing in Denmark

For the details of the electronic invoicing in Denmark, including the integration with [NemHandel](https://nemhandel.dk/) electronic invoicing infrastructure, refer to [Get started with Electronic invoicing for Denmark](../mea/e-invoicing-dk-get-started.md)


## Additional resources

- [Electronic invoicing administration and integration components](../global/e-invoicing-administration-integration-components.md)
- [Electronic invoicing setup](../global/e-invoicing-set-up-overview.md)
- [Work with Globalization features](../global/e-invoicing-working-globalization-features.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

