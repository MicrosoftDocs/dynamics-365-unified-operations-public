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

The following required credentials must be prliminary obtailned from **Edicom** to enable integration of the Electronic Invoicing service with the last-mile connector. 

- The **Service ID** which uniquely identifies the company by Edicom.
- The **Group** which is required for internal routing within the Edicom infrastructure.
- The **Token** which grants the authorization to access the Edicom services.

The obtained **Token** must be uploaded to the secret created in the **Azure Key Vault** managed by your company, for more information see [Customer certificates and secrets](../global/e-invoicing-customer-certificates-secrets.md). Then the secret will be used in the related Electronic Invoicing feature pipeline actions as a parameter.

### Electronic invoices submission

The following pipeline actions are introduced or updated for enabling outbound documents submission via the ISV last-mile connector.

- **Integrate with Edicom** - a new action that submits electronic documents generated using preceeding actions to Edicom. You need to configure the action's parameters described in the table below. 

  ![Edicom connector actions.](../media/isv_connector_actions.jpg)

  **Parameter**       | **Description**     |
  |---------------------|------------------|
  | **Domain** | Use the **Service ID** number provided by Edicom.|
  | **Application**                | Use  the same **Service ID** number. |
  | **Destination**                | Enter the **Service ID** number concatenated with the **_EDIWIN** value. For example, if the **Service ID** number is *123456* the **Destination** value should be *123456_EDIWIN*. |
  | **Group**                  | Use the **Group** code provided by Edicom.  |
  | **Auth token**                 | Select the name of the secret that you created for the token provided by Edicom.   |

  The following parameters are Edicom-specific and can be left unchanged with their default values provided by Microsoft in related globalization features.

  **Parameter**       | **Description**     |
  |---------------------|------------------|
  | **Web service URL** | Default value for Edicom: **https://ipaasgw.edicomgroup.com**.|
  | **Http request body**                | Default value: **Generate format: Output file**. |
  | **Schema**                 | Default value for Edicom: **OUT_XML_UBL_INVOICE_2_MICROSOFT_DK**.   |

  The rest of the action's parameters can be left empty.
  
  
- **Waiting for response from Edicom** - a new action that waits for the response from Edicom. No specific paramters need to be additionally configured.
  
- **Process response** - for this existing action new Electronic Reporting configurations **Edicom Response Processing** and **Error log import Json** were created for handeling the response received from Edicom by the preceding **Waiting for response from Edicom** action.

  The following parameters are Edicom-specific and can be left unchanged with their default values provided by Microsoft in related globalization features.

  **Parameter**       | **Description**     |
  |---------------------|------------------|
  | **Input file** | Default value for Edicom: **Waiting for response from Edicom: Output file**.|
  | **Reporting configuration list**                | Default value for Edicom: **Edicom Response Processing: Edicom Response Processing**. |
  | **Reporting configuration list**             | The second configuration, default value for Edicom: **Error log import Json: Error log import Json**.   |

   ![Edicom process response action.](../media/isv_connector_response.jpg)


A new data channel type **Get status from Edicom** is implemented for feature setups of **Export channel and processing pipeline** type. You need to configure the Export channel's parameters described in the table below. 

![Edicom get status.](../media/isv_connector_get_status.jpg)

 **Parameter**       | **Description**     |
|---------------------|------------------|
| **Domain** | Use the **Service ID** number provided by Edicom.|
| **Application**                | Use  the same **Service ID** number. |
| **Data channel**                | Enter the same name of the export channel which will be used in: <li>In the parent's feature setup applicability rules</li><li>In the used **Customer invoice context model** ER configuration, in the **DataChannel** definition, in the **$Context_Channel** variable's value</li><li>**Organization administration** > **Setup** > **Electronic document parameters** > **Integration channels** in Microsoft Dynamics 365 Finance</li>  |
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


ResponseXML ????????????????????????
![Edicom import channel.](../media/isv_connector_import_channel.jpg)

### Electronic invoicing in Denmark

For the details of the electronic invoicing in Denmark, including the integration with [NemHandel](https://nemhandel.dk/) electronic invoicing infrastructure, refer to [Get started with Electronic invoicing for Denmark](../mea/e-invoicing-dk-get-started.md)


## Additional resources

- [Electronic invoicing administration and integration components](../global/e-invoicing-administration-integration-components.md)
- [Electronic invoicing setup](../global/e-invoicing-set-up-overview.md)
- [Work with Globalization features](../global/e-invoicing-working-globalization-features.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

