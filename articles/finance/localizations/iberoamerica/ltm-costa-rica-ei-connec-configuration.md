---
title: Get started with Electronic invoicing for Costa Rica
description: Learn how to set up Microsoft Dynamics 365 Finance to use electronic invoice formats for Costa Rica.
author: Cpicon85
ms.author: v-cpicon
ms.topic: article
ms.date: 02/15/2024 
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Get started with Electronic invoicing for Costa Rica

[!include [banner](../../includes/banner.md)]

This article provides information to help you get started with Electronic invoicing for Costa Rica. It guides you through the configuration steps that are country/region-dependent in Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management. These steps complement the steps that are described in [Electronic invoicing setup](../global/gs-e-invoicing-set-up-overview.md). For the last-mile integration with the Costa Rican Tax Authorities, Microsoft is partnering with Edicom.

After you configure Electronic invoicing, you can generate, digitally sign, and submit the XML files of electronic invoices to the [Edicom](https://edicomgroup.com/electronic-invoicing/costa-rica) authorized certification provider (PAC) according to the [regulatory requirements in Costa Rica](https://www.hacienda.go.cr/).

![Diagram of the electronic invoicing workflow in Costa Rica.](ltm-CosRic-e-invoice-workflow.png)

> [!NOTE]
> The electronic invoicing approach that this article describes is implemented by using an invoicing service that is applicable only to cloud deployments of Finance or Supply Chain Management.

> [!IMPORTANT]
> The new Electronic invoicing Globalization feature for Costa Rica (outbound flow) requires that you run 365 Finance version 10.0.40 or later.

## Prerequisites

Before you begin the procedures in this article, the following prerequisites must be met:

1. Ensure that the settings for the Costa Rican legal entity are in place. For more information, see [Set up legal entity and tax information for Costa Rica](set-up-legal-entity-tax-costa-rica.md).
1. [Configure electronic invoice parameters for Costa Rica](ltm-costa-rica-electronic-invoice-conf.md).
1. Gain familiarity with and understanding of Electronic invoicing as it's described in [Electronic Invoicing service overview](../global/gs-e-invoicing-service-overview.md).
1. Do the common part of Electronic Invoicing service configuration as it's described in [Electronic invoicing configuration](../global/gs-e-invoicing-set-up-overview.md).
1. You must enable the following features in Feature management:

    - Electronic invoicing integration
    - Electronic invoicing integration resubmit document from failed action
    - Execute update actions for submitted documents

1. Make sure that the following Electronic reporting (ER) format configurations are imported.  For more information, see:
[Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md),
[Import Electronic reporting (ER) configurations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-import-ger-configurations.md).

    - Inventory e-invoice (CR)
    - Inventory Credit Note (CRI)
    - Inventory Debit Note (CRI)
    - Inventory Export e-Invoice (CRI)
    - Project e-invoice (CR)
    - Project Credit Note (CRI)
    - Project Debit Note (CRI)
    - Project Export e-Invoice (CRI)
    - Customer invoice context model
    - Edicom source file response import format
    - Edicom Response Processing LATAM
    - Edicom Response Processing CR
    - Edicom response error log import

    > [!NOTE]
    > These formats are based on the corresponding **LATAM** format configurations that use the **Invoice model LATAM** and **Invoice model mapping LATAM** configurations. All required additional configurations are automatically imported.

## Country/region-specific configuration for Electronic invoicing for Costa Rica

The **Costa Rica electronic invoice (CRI) "E-Invoicing for Costa Rica: ISV last-mile connector with Edicom"** feature represents an outbound flow for issuing the following sales documents:

|Name|Code|Original Name|
|----|----|-------------|
|Invoice|01|Factura Electrónica|
|Debit note|02|Nota de Débito Electrónica|
|Credit note|03|Nota de Crédito Electrónica|
|Export invoice|09|Factura de Exportación|

Some parameters of the feature are published with default values. Before you deploy the Electronic invoicing feature to the service environment, add a feature that is based on the Microsoft-provided feature, and complete the common parameters on the **Feature parameters** tab. Review the default values, and update them as required, so that they better reflect your business operations.

For Costa Rica, there are at least three interactions with Edicom in the pipeline: first to submit the invoice, then to fetch the signed XML, and finally to fetch the status of the submitted invoice. Each interaction requires common parameters, such as Edicom connection details and the authentication token that Edicom provides. These common parameters are reused in the feature setup for all document types. Edicom provides the values when a company is onboarded.

> [!NOTE]
> The configuration for common parameters is simplified. You no longer have to go to each action and feature setup, and repeatedly specify the common connection parameters. Use of the **Feature parameters** tab is available only as of version 10.0.41.

> [!IMPORTANT]
> The **Costa Rica electronic invoice (CRI)** feature is provided by Microsoft. Before it can be used, additional configuration is required, as described in this article. For information about how to configure invoicing features and apply changes, see [Work with feature setups](../global/gs-e-invoicing-feature-setup.md). For example, in addition to the connection parameters, you can filter specific legal entities so that they are processed in applicability rules. By default, the feature is applicable to all legal entities that have a primary address in Costa Rica.

1. Import the latest version of the **Costa Rica electronic invoice (CRI)** Globalization feature as described in [Import features from the repository](../global/gs-e-invoicing-import-feature-global-repository.md).
1. Create a copy of the imported Globalization feature, and select your configuration provider. For more information, see [Create a Globalization feature](../global/gs-e-invoicing-create-new-globalization-feature.md).
1. On the **Versions** tab, confirm that the **Draft** version is selected.
1. On the **Feature parameters** tab, specify values for the following connection and integration parameters that are required for interoperation with Edicom's API:

    - Select **Application**, and then enter the service ID number that you obtained.
    - Select **Domain**, and then enter the same service ID number.
    - Select **Get status schema name**, and then enter the schema name.
    - Select **Group**, and then enter the group code that you obtained.
    - Select **Signed XML schema name**, and then enter the schema name.
    - Select **Destination name**, and then enter the service ID number concatenated with the string "_EDIWIN." For example, if the service ID number is 123456, enter **123456_EDIWIN**.
    - Select **Submit invoice schema name**, and then enter the schema name.
    - Select **Auth token**, and then select the name of the secret that you created for the token.
    - Select **Web service URL**, and confirm the web address.

    > [!NOTE]
    > For illustrations showing examples of feature parameters and other settings of the ISV last-mile connector with Edicom, see [Get started with Electronic invoicing for Chile](ltm-chile-elec-invo-conncection.md) and/or [Get started with Electronic invoicing for Panama](ltm-panama-eI-connec-configuration.md). Just replace the values with the Costa Rican ones Edicom provides when you're onboarded.

1. The copy of the feature is always created as a **Draft** version. Regardless of whether you made changes, you must complete and deploy the feature as described in [Complete and deploy a Globalization feature](../global/gs-e-invoicing-complete-publish-deploy-globalization-feature.md).

### Outbound flow pipeline

To review the processing pipeline, on the **Setups** tab, go to **Feature setup**, select the derived document type that you want, and then select **Edit**. The outbound flow consists of the following actions:

1. **Transform document** – Generate a format that can be sent to Edicom.
1. **Integrate with Edicom** – Submit the generated invoice to Edicom.
1. **Get status from Edicom for an invoice** – Fetch the signed XML from Edicom. This document might not be immediately available, because the PAC needs time to generate it.

    > [!NOTE]
    > At this point in the flow, the concept of *update actions* comes into play. Notice that the **Update action** checkbox is selected for this step. Therefore, this step and all subsequent steps run in a loop until the system determines that a terminal state has been reached.

1. **Get status from Edicom for an invoice** – Fetch the status of the submitted invoice from Edicom.
1. **Process response** – Process the received response to determine whether a terminal state has been reached.

    - If the status response indicates a failure, the pipeline is terminated, and the submission is marked as failed.
	- If the status response indicates successful submission to the Costa Rican virtual tax administration (ATV), the pipeline is terminated. 
    > [!NOTE]
    > Customers or buyers in Costa Rica can reject invoices for up to eight days. But there is not a standar way to get this information from Costa Rican virtual tax administration (ATV). So the **Costa Rica electronic invoice (CRI)** globalization feature doesn't not support this scenario. 

> [!NOTE]
> For each format included in the **Costa Rica electronic invoice (CRI)** feature there is a similiar setup. For Costa Rica there are eight. All for sales documents (Outbound flow).

So in case for Costa Rica the setups are:
- Inventory Export Invoice
- Project Invoice
- Project Debit Note
- Project Credit Note
- Project Export Invoice
- Sales Invoice
- Inventory Debit Note
- Inventory Credit Note

### Applicability rules

Applicability rules must be correctly configured to provide context, so that the exact Electronic invoicing Globalization feature that must run in Electronic Invoicing service can be found. Applicability rules are provided out of the box by checking the legal entity in the International Organization for Standardization (ISO) country/region code. This particular feature setup supports all four types of invoices: customer invoices, debit notes, credit notes and export invoices. 

> [!NOTE]
> The reason for having so much rules is beacuse the electronic invoice feature covers 4 types of documents 
and each type can be generated in two places - sales and project orders - so user will have to configure formats to cover this for each type of document.

### Variables

The following variables are used in the outbound data flow actions of the Costa Ricaan feature (these variables are provided out of the box):
- **BusinessDocumentDataModel** – The Business Document Data model variable that is received from Finance or Supply Chain Management and transformed into the format that is required for submission.
- **SignedXML** – The signed XML variable that is sent back to Finance or Supply Chain Management. This variable contains the base64-encoded response body from the **Get Signed XML from Edicom** step. It's used in the response types to save the signed XML that is obtained from Edicom as an attachment to the invoice journal. It's also used to generate printable reports through QR codes.

After you import the **Electronic invoicing for Costa Rica** feature that includes the out-of-box default feature setup, follow the steps in the next section to configure electronic documents.

## Configure electronic document parameters

1. Make sure that the country/region-specific ER configurations for the document context and electronic document model mapping that are required for Costa Rica are imported. For more information, see [Set up Electronic document parameters](../global/gs-e-invoicing-set-up-parameters.md#set-up-electronic-document-parameters).
1. Go to **Organization administration** \> **Setup** \> **Electronic document parameters**.
1. In the **Electronic document** section, add records for the **Customer Invoice journal** and **Project invoice** table names.
1. For each table name, set the **Document context** and **Electronic document model mapping** fields in accordance with step 1.
1. Save your changes, and close the page.
1. For each table name, follow these steps:

    1. Select **Response types**, select **New** to create a response type that you will get from the back end, and enter the following values:

        - In the **Response type** field, enter **SignedXML** (the default value, see the [Variables](#variables) section of this article).
        - In the **Description** field, enter any meaningful name. Alternatively, leave the field blank.
        - In the **Submission status** field, select **Pending**.
        - In the **Model mapping** field, select **Edicom source file response format**.

    1. Repeat the preceding step, but set the **Submission status** field to **Pending update actions execution**. In this way, you can run a subset of the actions in the processing pipeline in a loop to continuously pull updated statuses and other information for the submitted documents from the tax authority.

    > [!NOTE]
    > The response includes the signed XML that is obtained from Edicom. This signed XML is stored in the system as an attachment to the corresponding invoice journal. It will eventually be used to generate printable invoices through QR codes.

## Issue electronic invoices

After you complete all the required configuration steps, you can generate and submit electronic invoices for posted invoices by going to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Submit electronic documents**. For more information about how to generate electronic invoices, see [Submit electronic documents](../global/e-invoicing-submit-electronic-documents.md).

To inquire about the results of a submission, go to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Electronic document submission log**, and select the required document type. For more information, see [Work with Electronic document submission log](../global/e-invoicing-submission-log.md).

For Costa Rica, after you submit the invoice, the submission status is set to **Pending update actions execution**. The response body is probably empty for the signed XML and the call to get the invoice status. An empty response body indicates that the XML wasn't available immediately after submission. To address the pending status, a function that is named **Execute update actions** is used. This function resumes the pipeline from the action that is marked as an update action, and then runs all subsequent actions in the pipeline in a loop. The status should change to **Executing** again. Then, after a few seconds, it reverts to **Pending update actions execution**.

> [!NOTE]
> By setting a recurrence schedule, you can configure the **Execute update actions** function to run in batch mode on a periodic basis.

When you review the submission details, you should notice that the steps run again. This time, the signed XML is received.

As a result of the completed outbound flow, the signed XML is attached to the invoice journal as **EdicomSourceFile**.

## More resources

- [Electronic Invoicing service overview](../global/gs-e-invoicing-service-overview.md)
- [Electronic Invoicing administration and integration components](../global/gs-e-invoicing-administration-integration-components.md)
- [Electronic invoicing configuration](../global/gs-e-invoicing-set-up-overview.md)
- [Globalization feature components](../global/gs-e-invoicing-working-globalization-features.md)
- [Electronic Invoicing service independent software vendor (ISV) last-mile connector](../global/e-invoicing-isv-connector.md)
- [Dynamics 365 Country expansion: localizations for LATAM countries | June 27, 2024](https://community.dynamics.com/blogs/post/?postid=7bd2efc7-9344-ef11-840a-6045bdeef618)
- [Dynamics 365 Country expansion: localizations for LATAM countries | D365 FastTrack Tech Talks (youtube.com)](https://www.youtube.com/watch?v=eK8TJmnhpJo)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
