---
title: Electronic Invoicing service ISV last-mile connector
description: Learn how to configure and use the Electronic Invoicing service ISV connector, including prerequisites and an outline on integration.
author: ikondratenko
ms.author: ikondratenko
ms.topic: concept-article
ms.date: 11/05/2026
ms.reviewer: johnmichalak
ms.collection: get-started
ms.search.region: Global
ms.search.validFrom: 2023-12-01
ms.dyn365.ops.version: AX 10.0.37
ms.custom: sfi-image-nochange
---

# Electronic Invoicing service ISV last-mile connector

[!INCLUDE [banner](../../includes/banner.md)]

The independent software vendor (ISV) last-mile connector complements the standard Electronic Invoicing service functionality when no direct integration with government electronic invoicing platforms or final electronic invoice recipients is supported. In these scenarios, use Microsoft Dynamics 365 Finance to generate electronic documents in legally required formats. Pass the documents to the ISV last-mile connector for further communication. For incoming electronic documents, use the ISV last-mile connector as a source of inbound documents, which Finance then handles.

This article explains how to configure and use the Electronic Invoicing service ISV last-mile connector.

## Prerequisites

Before you begin the procedures in this article, ensure you meet the following prerequisites:

- Your company must have a separate signed service agreement with an ISV that provides electronic document delivery service. Also, obtain the required credentials to enable integration of the Electronic Invoicing service with the ISV last-mile connector.
- Become familiar with Electronic invoicing functionality. For more information, see [Electronic invoicing overview](../global/gs-e-invoicing-service-overview.md).
- Consult the list of available country/region-specific [Electronic invoicing features](e-invoicing-country-specific-availability.md). The capability to use the ISV last-mile connector for submission complements this list.

## Integration with Edicom

> [!NOTE]
> The integration of the Electronic Invoicing service with the ISV last-mile connector is based on the **Danish electronic invoicing** example. For other countries and regions, see the respective section in the [Country/region-specific scenarios implemented via Edicom](#Countries/regions) article.

You can configure and use the Electronic Invoicing service ISV last-mile connector's integration with the Global e-Invoicing Platform that [Edicom](https://edicomgroup.com/electronic-invoicing) provides. For more information, see [Edicom integration with Microsoft Dynamics 365](https://edicomgroup.com/connectors/microsoft).

To enable the integration of the Electronic Invoicing service with the ISV last-mile connector, you must get the following credentials from Edicom:

- **Service ID** – The service ID number identifies your company to Edicom.
- **Group** – The group code is used for internal routing within the Edicom infrastructure.
- **Token** – The token grants authorization to access the Edicom services.

Upload the token you get to the secret you create in the Azure Key Vault that your company manages. For more information, see [Customer certificates and secrets](../global/e-invoicing-customer-certificates-secrets.md). You use the secret as a parameter in the related Electronic Invoicing feature pipeline actions.

> [!NOTE]
> By using this integration, you can submit generated e-invoice files either in the **OIOUBL** format to the Danish electronic invoicing infrastructure, **NemHandel**, or in the **PEPPOL** format to the PEPPOL Delivery Network. Edicom dynamically analyzes the format of a submitted file and routes it accordingly.

### Electronic invoice submission

The following pipeline actions are introduced or updated to enable outbound document submission via the ISV last-mile connector.

- **Integrate with Edicom** – This new action submits electronic documents that preceding actions generate to Edicom. Configure the parameters for this action as described in the following table.

    | Parameter | Description |
    |-----------|-------------|
    | Domain | Enter the service ID number that Edicom provides.|
    | Application | Enter the same service ID number. |
    | Destination | Enter the service ID number concatenated with the string **\_EDIWIN**. For example, if the service ID number is **123456**, enter **123456\_EDIWIN**. |
    | Group | Enter the group code that Edicom provides. |
    | Auth token | Select the name of the secret that you created for the token that Edicom provides. |

    The following parameters are Edicom-specific. Leave them set to the default values that Microsoft provides in related Globalization features.

    | Parameter | Description |
    |-----------|-------------|
    | Web service URL | Default value for Edicom: `https://ipaasgw.edicomgroup.com`. |
    | Http request body | Default value: **Generate format: Output file**. |
    | Schema | Default value for Edicom: **OUTBOUND\_DOCUMENT\_MICROSOFT\_DK**. |

    Leave all remaining parameters blank.

    :::image type="content" source="../media/isv_connector_actions.jpg" alt-text="Screenshot that shows the parameters for the Integrate with Edicom action.":::

- **Waiting for response from Edicom** – This new action waits for the response from Edicom. You don't need to configure any specific parameters.
- **Process response** – For this existing action, two new Electronic reporting (ER) configurations, **Edicom Response Processing** and **Error log import Json**, were created to handle the response that the **Waiting for response from Edicom** action receives from Edicom.

    The following parameters are Edicom-specific. You can leave them set to the default values that Microsoft provides in related Globalization features.

    | Parameter | Description |
    |-----------|-------------|
    | Input file | Default value for Edicom: **Waiting for response from Edicom: Output file**. |
    | Reporting configuration list | The first new ER configuration. Default value for Edicom: **Edicom Response Processing: Edicom Response Processing**. |
    | Reporting configuration list | The second new ER configuration. Default value for Edicom: **Error log import Json: Error log import Json**. |

    :::image type="content" source="../media/isv_connector_response.jpg" alt-text="Screenshot that shows the parameters for the Process response action.":::

A new data channel type, **Get status from Edicom**, is implemented for feature setups of the **Export channel and processing pipeline** type. You must create a new feature setup where you select **Get status from Edicom** as the data channel.

:::image type="content" source="../media/isv_connector_get_status.jpg" alt-text="Screenshot that shows a Get status feature setup of the Export channel and processing pipeline type being created.":::

Configure the export channel's parameters as described in the following table.

| Parameter | Description |
|-----------|-------------|
| Domain | Enter the service ID number that Edicom provided.|
| Application | Enter the same service ID number. |
| Data channel | <p>Enter the name of the export channel to use. Enter the same name in each of the following places:</p><ul><li>In the applicability rules of the parent's feature setup</li><li>In the value of the **$Context\_Channel** variable in the **DataChannel** definition in the **Customer invoice context model** ER configuration that's used</li><li>At **Organization administration** \> **Setup** \> **Electronic document parameters** \> **Integration channels** in Finance</li></ul> |
| Group | Enter the group code that Edicom provided. |
| Auth token | Select the name of the secret that you created for the token that Edicom provided. |

Leave the following parameters set to the default values that Microsoft provides in related Globalization features.

| Parameter | Description |
|-----------|-------------|
| Web service URL | Default value: `https://ipaasgw.edicomgroup.com`. |
| Document limit | Default value: **100**. |
| Schema | Default value: **IN\_DOCUMENT\_STATUS\_MICROSOFT\_DK**. |

You can leave all remaining parameters blank.

### Electronic invoice receipt

A new data channel type, **Edicom service**, is implemented for feature setups of the **Import channel** or **Import channel and processing pipeline** type. You must create a new feature setup where you select **Edicom service** as the data channel.

:::image type="content" source="../media/isv_connector_import_channel_new.jpg" alt-text="Screenshot that shows an Import invoices feature setup of the Import channel and processing pipeline type being created.":::

Configure the import channel's parameters as described in the following table.

| Parameter | Description |
|-----------|-------------|
| Domain | Enter the service ID number that Edicom provided. |
| Application | Enter the same service ID number. |
| Data channel | <p>Enter the name of the import channel to use. Enter the same name in each of the following places:</p><ul><li>In the applicability rules of the parent's feature setup<li><p>In the value of the **$Context\_Channel** variable in the **DataChannel** definition in the derived version of the **Customer invoice context model** ER configuration that's used for the import scenario.</p><p>> [!IMPORTANT]<br>> The derived configuration must differ from the configuration that's used for the invoice *submission* setup.</p></li><li>At **Organization administration** \> **Setup** \> **Electronic document parameters** \> **Integration channels** in Finance</li></ul> |
| Group | Enter the group code that Edicom provided. |
| Auth token | Select the name of the secret that you created for the token that Edicom provided. |

You can leave all remaining parameters set to the default values that Microsoft provides in related Globalization features.

Additionally, you must configure the following feature setup variable to use for the decoded file:

- **Name:** ResponseXml
- **Description:** Decoded file
- **Type:** From client
- **Data type:** file

:::image type="content" source="../media/isv_connector_responseXML.jpg" alt-text="Screenshot that shows the ResponseXml variable for the Edicom import channel.":::

The name of this variable must be used as the name of the import source for the import channel on **Integration channels** tab of the **Electronic document parameters** page in Finance.

:::image type="content" source="../media/isv_connector_import_channel.jpg" alt-text="Screenshot that shows the ResponseXml import source on the Electronic document parameters page.":::

### <a id="Countries/regions"></a>Country or region-specific scenarios implemented via Edicom

To learn more about electronic invoicing for a specific country or region, select the appropriate article from the following table.

| Country or region | Documentation article |
|-----------|-------------|
| Belgium | [Electronic invoicing for Belgium](../belgium/emea-bel-e-invoices.md) |
| Chile | <ul><li>[Get started with Electronic invoicing for Chile](../iberoamerica/ltm-chile-elec-invo-conncection.md)</li><li>[Vendor electronic invoice import in Chile](../iberoamerica/ltm-chl-vend-e-invoice.md)</li></ul> |
| Colombia | [Get started with Electronic invoicing for Colombia](../iberoamerica/ltm-costa-rica-ei-connect-configuration.md)|
| Costa Rica | [Get started with Electronic invoicing for Costa Rica](../iberoamerica/ltm-costa-rica-ei-connect-configuration.md) |
| France | [Electronic invoicing for France](../france/emea-fra-einv-ereport.md)|
| Denmark | [Use electronic invoicing for Denmark](../denmark/gs-e-invoicing-dk-get-started.md)|
| Panama | [Get started with Electronic invoicing for Panama](../iberoamerica/ltm-panama-ei-connec-configuration.md) |
| Paraguay |  [Get started with electronic invoicing for Paraguay](../iberoamerica/ltm-paraguay-electronic-invoice-configuration.md). |
| Singapore | [Electronic invoicing for Singapore](../singapore/apac-singapore-electronic-invoices.md) |
| Uruguay | [Get started with Electronic invoicing for Uruguay](../iberoamerica/ltm-uruguay-electronic-invoice-configuration.md) |

## Additional resources

- [Electronic invoicing administration and integration components](../global/gs-e-invoicing-administration-integration-components.md)
- [Electronic invoicing setup](../global/gs-e-invoicing-set-up-overview.md)
- [Work with Globalization features](../global/gs-e-invoicing-working-globalization-features.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
