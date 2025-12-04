---
title: Get started with Electronic invoicing for Costa Rica
description: Learn how to set up Microsoft Dynamics 365 Finance to use electronic invoice formats for Costa Rica.
author: Cpicon85
ms.author: v-cpicon
ms.topic: get-started
ms.date: 12/04/2025
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Get started with Electronic invoicing for Costa Rica

[!include [banner](../../includes/banner.md)]

This article provides information to help you get started with Electronic invoicing for Costa Rica. It guides you through the configuration steps that are country/region-dependent in Microsoft Dynamics 365 Finance or Microsoft Dynamics 365 Supply Chain Management. These steps complement the steps that are described in [Electronic invoicing setup](../global/gs-e-invoicing-set-up-overview.md). For the last-mile integration with the Costa Rican Tax Authorities, Microsoft partners with Edicom.

After you configure Electronic invoicing, you can generate, digitally sign, and submit the XML files of electronic invoices to the [Edicom](https://edicomgroup.com/electronic-invoicing/costa-rica) authorized certification provider (PAC) according to the [regulatory requirements in Costa Rica](https://www.hacienda.go.cr/).

:::image type="content" source="ltm-costa-rica-electronic-invoice-workflow.png" alt-text="Screenshot of the electronic invoicing workflow diagram in Costa Rica.":::

> [!NOTE]
> The electronic invoicing approach that this article describes uses an invoicing service that's applicable only to cloud deployments of Finance or Supply Chain Management.

## Prerequisites

Before you begin the procedures in this article, complete the following prerequisites:

1. Ensure that the settings for the Costa Rican legal entity are in place. For more information, see [Set up legal entity and tax information for Costa Rica](set-up-legal-entity-tax-costa-rica.md).
1. [Configure electronic invoice parameters for Costa Rica](ltm-costa-rica-electronic-invoice-conf.md).
1. Gain familiarity with and understanding of Electronic invoicing as it's described in [Electronic Invoicing service overview](../global/gs-e-invoicing-service-overview.md).
1. Complete the common part of Electronic Invoicing service configuration as it's described in [Electronic invoicing configuration](../global/gs-e-invoicing-set-up-overview.md).
1. Enable the following features in Feature management:

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
    - Purchase e-invoice (CRI)
    - Payment Receipt (CRI)
    - Customer invoice context model
    - Edicom source file response import format
    - Edicom Response Processing LATAM
    - Edicom Response Processing CR
    - Edicom response error log import

    > [!NOTE]
    > These formats are based on the corresponding **LATAM** format configurations that use the **Invoice model LATAM** and **Invoice model mapping LATAM** configurations. All other required configurations are automatically imported.

## Country/region-specific configuration for Electronic invoicing for Costa Rica

The **Costa Rica electronic invoice (CRI) "E-Invoicing for Costa Rica: ISV last-mile connector with Edicom"** feature represents an outbound flow for issuing the following sales documents:

| Name            | Code | Original Name                        |
|-----------------|------|--------------------------------------|
| Invoice         | 01   | Factura Electrónica                  |
| Debit note      | 02   | Nota de Débito Electrónica           |
| Credit note     | 03   | Nota de Crédito Electrónica          |
| Purchase invoice| 08   | Factura electrónica de compras       |
| Export invoice  | 09   | Factura de Exportación               |
| Payment receipt | 10   | Recibo Electrónico de Pago           |


Some parameters of the feature are published with default values. Before you deploy the Electronic invoicing feature to the service environment, add a feature that is based on the Microsoft-provided feature, and complete the common parameters on the **Feature parameters** tab. Review the default values, and update them as required, so that they better reflect your business operations.

## Edicom Interactions for Costa Rica

For Costa Rica, the base flow includes at least three core interactions with Edicom:

1. **Invoice submission**  
1. **Signed XML retrieval**  
1. **Status retrieval of the submitted invoice**

Each of these interactions requires common parameters, such as Edicom connection details and the authentication token provided by Edicom. The feature setup for all document types reuses these parameters. Edicom supplies these values during the company's onboarding process.

----
### Costa Rica Electronic Invoice (CR) Edicom integration for Costa Rica

> [!IMPORTANT]
> Microsoft provides the **Costa Rica Electronic Invoice (CR)** feature. Before you can use it, you need to configure it as described in this article. Learn how to configure invoicing features and apply changes in [Work with feature setups](../global/gs-e-invoicing-feature-setup.md). For example, in addition to the connection parameters, you can filter specific legal entities so that they are processed in applicability rules. By default, the feature applies to all legal entities that have a primary address in Costa Rica.

1. Import the latest version of the **Costa Rica Electronic Invoice (CR)** Globalization feature as described in [Import features from the repository](../global/gs-e-invoicing-import-feature-global-repository.md). The following illustrations show what the feature looks like after you import it from Dataverse.

    :::image type="content" source="ltm-costa-rica-electronic-invoice-globalization-feature-imported.png" alt-text="Screenshot of the imported Globalization feature for Costa Rica on the Electronic invoicing features page.":::


    If you go to the Configuration tab, as shown in the previous screenshot, you see a page that displays information similar to the following table:

    | Name                                | Version           | Status     | Country/region code |
    |-------------------------------------|-------------------|------------|---------------------|
    | Edicom Response Processing LATAM    | 13.2.5            | Completed  |                     |
    | Edicom response error log import    | 13.3              | Completed  |                     |
    | Payment Receipt (CRI)               | 296.152.5         | Completed  | CR                  |
    | Purchase e-invoice (CRI)            | 296.152.14        | Completed  | CR                  |
    | Inventory Credit Note (CRI)         | 296.152.55.41     | Completed  | CR                  |
    | Inventory Debit Note (CRI)          | 296.152.55.41     | Completed  | CR                  |
    | Inventory e-invoice (CR)            | 296.152.55.46     | Completed  | CR                  |
    | Inventory Export e-Invoice (CRI)    | 296.152.55.29     | Completed  | CR                  |
    | Project Credit Note (CRI)           | 296.152.27.22     | Completed  | CR                  |
    | Project Debit Note (CRI)            | 296.152.27.21     | Completed  | CR                  |
    | Project e-invoice (CR)              | 296.152.27.22     | Completed  | CR                  |
    | Project Export e-Invoice (CRI)      | 296.152.27.6      | Completed  | CR                  |

    > [!NOTE]
    > The version numbers might change if the formats are updated. The table is for illustrative purposes only.

1. Create a copy of the imported Globalization feature, and select your configuration provider. For more information, see [Create a Globalization feature](../global/gs-e-invoicing-create-new-globalization-feature.md).
1. On the **Versions** tab, confirm that the **Draft** version is selected.
1. On the **Feature parameters** tab, specify values for the following connection and integration parameters that are required for interoperation with Edicom's API.  
These parameters are general-purpose and are used across the different actions in the setups, so you only need to configure them once in this section.


    > [!TIP]
    > The following table provides **example values** for each feature parameter, so you can understand the type of data that you should enter for each one. These values are **illustrative only** and were provided by Edicom to Microsoft for testing purposes. When you're onboarded, Edicom provides you with your own unique values to use in your configuration.





    | Parameter                     | Description              | Data type   | Value                                               |
    |-------------------------------|--------------------------|-------------|-----------------------------------------------------|
    | EdicomApplication             | Application              | String      | <ID_PROVIDED_EDICOM>                                              |
    | EdicomDomain                  | Domain                   | String      | <ID_PROVIDED_EDICOM>                                              |
    | EdicomGetStatusSchema         | Get status schema name   | String      | IN_DOCUMENT_STATUS_MICROSOFT_UY                     |
    | EdicomGroup                   | Group                    | String      | <GROUP_ID>                                           |
    | EdicomSignedXMLSchema         | Signed XML schema name   | String      | EDIWIN-SOURCE-FILE_XML_CFE_ADENDA_<ID_PROVIDED_EDICOM>           |
    | EdicomSubmitInvoiceDestination| Destination name         | String      | <ID_PROVIDED_EDICOM>_EDIWIN                                       |
    | EdicomSubmitInvoiceSchema     | Submit invoice schema name| String     | OUTBOUND_DOCUMENT_MICROSOFT_UY                      |
    | EdicomToken                   | Auth token               | Secret name | EdiwinCosta RicaToken                                  |
    | EdicomWebServiceURL           | Web service URL          | String      | https://ipaasgw.edicomgroup.com

    > [!TIP]
    > When configuring the feature parameters for Edicom integration, follow these steps:
    >
    > - Select **Application**, and enter the service ID number you obtained from Edicom.
    > - Select **Domain**, and enter the same service ID number.
    > - Select **Get status schema name**, and enter the provided schema name.
    > - Select **Group**, and enter the group code you received.
    > - Select **Signed XML schema name**, and enter the appropriate schema name.
    > - Select **Destination name**, and enter the service ID number concatenated with "_EDIWIN". For example, if your service ID is 123456, enter **123456_EDIWIN**.
    > - Select **Submit invoice schema name**, and enter the schema name.
    > - Select **Auth token**, and choose the name of the secret you created for the token.
    > - Select **Web service URL**, and verify the web address is correct.
1. The copy of the feature is always created as a **Draft** version. Regardless of whether you make changes, you must complete, publish, and deploy the feature as described in [Complete and deploy a Globalization feature](../global/gs-e-invoicing-complete-publish-deploy-globalization-feature.md).

### Outbound flow pipeline

The **Costa Rica Electronic Invoice (CR) feature** includes 10 electronic invoice formats for Costa Rica. Each format requires its own setup and configuration. The formats are:

- **Inventory e-invoice (CRI)**
- **Inventory Credit Note (CRI)**
- **Inventory Debit Note (CRI)**
- **Inventory Export e-Invoice (CRI)**
- **Payment Receipt (CRI)**
- **Project e-invoice (CRI)**
- **Project Credit Note (CRI)**
- **Project Debit Note (CRI)**
- **Project Export e-Invoice (CRI)**
- **Purchase e-invoice (CRI)**

The following sections provide guidance on the general configuration steps that apply to all 10 formats. They also explain specific considerations and requirements for each individual format, so you can ensure that each one is configured correctly according to its unique needs.

## Electronic invoice feature

### Setups-View

After you import the feature, the second screenshot shows five tabs: **Versions**, **Configurations**, **Feature parameters**, **Setups**, and **Tags**. Select the **Setups** tab, then select **View**. This action opens the **Feature version setup** page:

## Feature version setup
This page allows you to review and configure the details of the feature setup for Costa Rica. On the left side of this page, you see four sections: **Processing pipeline**, **Applicability rules**, **Variables**, and **Parameters**.

### Processing pipeline

The Setup Actions and Parameters section contain two distinct grids:

#### Top Right – Processing Pipeline

The **Processing pipeline** grid is similar to the following table:

| Action                       | Action name                       | Description                      | Enable retry | Retry action | Export result | Update action |
|------------------------------|-----------------------------------|----------------------------------|--------------|--------------|---------------|--------------|
| Transform document           | Generate invoice XML file          |                                  |              |              |               |              |
| Integrate with Edicom        | Submit invoice                     |                                  |              |              |               |              |
| Get status from Edicom for an invoice | Get signed XML from Edicom         |                                  |              |              |               | **Checked**   |
| Get status from Edicom for an invoice | Get invoice status from Edicom      |                                  |              |              |               |              |
| Process response             | Process invoice status response     |                                  |              |              |               |              |


> [!NOTE]
> The **Get status from Edicom for an invoice** action is crucial in the flow, as it's marked with the **Update action** checkbox. This designation means that this specific step—and all steps following it—repeatedly execute in a loop. The system continues this process until the invoice reaches a final, terminal status, ensuring that the latest status from Edicom is always retrieved and processed.

#### Bottom Right – Parameters
The lower grid shows the Parameters associated with the selected processing action. These parameters allow for fine-tuning of the selected step’s behavior. Each entry includes a parameter name, description, data type, and value, enabling you to configure processing logic according to your business requirements. 

#### Transform document parameters

| Name                   | Description                                                        | Value                          |
|------------------------|--------------------------------------------------------------------|--------------------------------|
| Input file             | Source file that provides the action with the data to execute.        | Variable: BusinessDocumentDataModel |
| Direction              | Direction describes which format is used: import or export     | export                         |
| Configuration          | Configuration describes the format that's executed               | Inventory e-Invoice: Inventory e-Invoice |
| Configuration Integration point | Source file that provides data to the reporting runtime          | InvoiceCustomer                |
| Custom file name       | Custom file name from the client                                   |                                |

#### Linking the correct format in Transform document parameters

When configuring the **Transform document** action in the processing pipeline, ensure the following:
 
- **Configuration**: Set this value to the exact name of the feature format you're configuring.  
    - For example:
        - Inventory e-invoice (CR) → Configuration: Inventory e-invoice (CR)
        - Inventory Credit Note (CRI) → Configuration: Inventory Credit Note (CRI)
        - Inventory Debit Note (CRI) → Configuration: Inventory Debit Note (CRI)
        - Inventory Export e-Invoice (CRI) → Configuration: Inventory Export e-Invoice (CRI)
        - Project e-invoice (CR) → Configuration: Project e-invoice (CR)
        - Project Credit Note (CRI) → Configuration: Project Credit Note (CRI)
        - Project Debit Note (CRI) → Configuration: Project Debit Note (CRI)
        - Project Export e-Invoice (CRI) → Configuration: Project Export e-Invoice (CRI)
        - Payment Receipt (CRI) → Configuration: Payment Receipt (CRI)
        - Purchase e-invoice (CRI) → Configuration: Purchase e-invoice (CRI)
- **Configuration Integration Point**:  
    - Configuration Integration Point:
        - `InvoiceCustomer` — Inventory e-invoice (CRI), Inventory Debit Note (CRI), Inventory Credit Note (CRI), Inventory Export e-Invoice (CRI)
        - `InvoiceProject` — Project e-invoice (CRI), Project Debit Note (CRI), Project Credit Note (CRI), Project Export e-Invoice (CRI)
        - `CustomerPrepayment` — Payment Receipt (CRI)
        - `EInvoiceVendor` — Purchase e-invoice (CRI)

> [!TIP]
> If the feature name contains "Project", use `InvoiceProject`. If it contains "Inventory," use `InvoiceCustomer`. Incorrect settings result in empty XML or missing required data.

#### Integrate with Edicom parameters

| Name             | Description                                  | Value                                               |
|------------------|----------------------------------------------|-----------------------------------------------------|
| Web service URL  | URL address to send request                  | FeatureParameter: EdicomWebServiceURL               |
| Http request body| Http request body (can be empty)             | Generate invoice XML file: Output file              |
| User name        | KeyVault secret name to store user name      |                                                     |
| Password         | KeyVault secret name to store user password  |                                                     |
| Client ID        | Client ID secret name in the KeyVault        |                                                     |
| Client Secret    | Client Secret secret name in the KeyVault    |                                                     |
| Auth token       | Auth token secret name in the KeyVault       | EdiwinCostaRicaToken                                |
| Domain           | Domain                                       | FeatureParameter: EdicomDomain                      |
| Application      | Application                                  | FeatureParameter: EdicomApplication                 |
| Destination      | Destination                                  | FeatureParameter: EdicomSubmitInvoiceDestination    |
| Schema           | Schema                                       | FeatureParameter: EdicomSubmitInvoiceSchema         |
| Duplicates       | Duplicates                                   | 0                                                   |
| Group            | Group                                        | FeatureParameter: EdicomGroup                       |
| Custom file name | Custom file name from the client             | Generate invoice XML file: File name                |

#### Get signed XML from Edicom parameters

| Name            | Description                                    | Value                                    |
|-----------------|------------------------------------------------|------------------------------------------|
| Web service URL | URL address to send request                    | FeatureParameter: EdicomWebServiceURL     |
| User name       | KeyVault secret name to store user name        |                                          |
| Password        | KeyVault secret name to store user password    |                                          |
| Client ID       | Client ID secret name in the KeyVault          |                                          |
| Client Secret   | Client Secret secret name in the KeyVault      |                                          |
| Auth token      | Auth token secret name in the KeyVault         | EdiwinCosta RicaToken                       |
| Domain          | Domain                                         | FeatureParameter: EdicomDomain           |
| Application     | Application                                    | FeatureParameter: EdicomApplication      |
| Schema          | Schema                                         | FeatureParameter: EdicomSignedXMLSchema  |
| Group           | Group                                          | FeatureParameter: EdicomGroup            |
| ERP UUID        | Reference ID of the document submitted to Edicom | Submit invoice: ExternalID              |


#### Get invoice status from Edicom parameters

| Name           | Description                                         | Value                                 |
|----------------|-----------------------------------------------------|---------------------------------------|
| Web service URL| URL address to send request                         | FeatureParameter: EdicomWebServiceURL |
| User name      | KeyVault secret name to store user name             |                                       |
| Password       | KeyVault secret name to store user password         |                                       |
| Client ID      | Client ID secret name in the KeyVault               |                                       |
| Client Secret  | Client Secret secret name in the KeyVault           |                                       |
| Auth token     | Auth token secret name in the KeyVault              | EdiwinCosta RicaToken                   |
| Domain         | Domain                                              | FeatureParameter: EdicomDomain        |
| Application    | Application                                         | FeatureParameter: EdicomApplication   |
| Schema         | Schema                                              | FeatureParameter: EdicomGetStatusSchema|
| Group          | Group                                               | FeatureParameter: EdicomGroup         |
| ERP UUID       | Reference ID of the document submitted to Edicom    | Submit invoice: ExternalID            |

#### Process response parameters

| Name                        | Description                                 | Value                                                                 |
|-----------------------------|---------------------------------------------|-----------------------------------------------------------------------|
| Input file                  | Response to analyze                         | Get invoice status from Edicom: Output file                           |
| Reporting configuration list| List of configurations used for response parsing | Edicom Response Processing LATAM: Edicom Response Processing LATAM    |
| Custom file name            | Custom file name from the client            |                                                                       |
| Reporting configuration list| List of configurations used for response parsing | Edicom response error log import: Edicom response error log import    |


> [!NOTE]  
> - If the status response indicates a failure, the pipeline terminates, and the submission is marked as failed.  
- If the status response indicates successful submission to the Costa Rican Tax Authorities (MH), the pipeline completes automatically.


### Applicability rules and feature setup scope

You must correctly configure applicability rules to provide context, so that the Electronic Invoicing service can find the exact Electronic Invoicing Globalization feature to run. The system provides these applicability rules out of the box by checking the legal entity’s International Organization for Standardization (ISO) country/region code. 

#### Applicability rules for Costa Rican electronic invoice formats

The following table lists the applicability rules for each electronic invoice format for Costa Rica. Replace `<Legal Entity ID>` with the actual ID of your legal entity.

### Inventory e-invoice (CRI)
| And/or | And/or | Field          | Operator type | Value            | Data type |
|--------|--------|----------------|---------------|------------------|-----------|
| And    |        | CountryISOCode | Equals        | CR               | string    |
|        |        | LegalEntityId  | Equals        | CRMF             | string    |
|        |        | DocumentType   | Equals        | Customer invoice | string    |


### Inventory Credit Note (CRI)
| And/or | And/or | Field          | Operator type | Value                 | Data type |
|--------|--------|----------------|---------------|-----------------------|-----------|
| And    |        | CountryISOCode | Equals        | CR                    | string    |
|        |        | LegalEntityId  | Equals        | CRMF                  | string    |
|        |        | DocumentType   | Equals        | Customer credit note  | string    |

### Inventory Debit Note (CRI)
| And/or | And/or | Field          | Operator type | Value                   | Data type |
|--------|--------|----------------|---------------|-------------------------|-----------|
| And    |        | CountryISOCode | Equals        | CR                      | string    |
|        |        | LegalEntityId  | Equals        | CRMF                    | string    |
|        |        | DocumentType   | Equals        | Customer debit note     | string    |

### Inventory Export e-Invoice (CRI)
| And/or | And/or | Field          | Operator type | Value                   | Data type |
|--------|--------|----------------|---------------|-------------------------|-----------|
| And    |        | CountryISOCode | Equals        | CR                      | string    |
|        |        | LegalEntityId  | Equals        | CRMF                    | string    |
|        |        | DocumentType   | Equals        | Customer Export invoice | string    |

### Project e-invoice (CRI)
| And/or | And/or | Field          | Operator type | Value           | Data type |
|--------|--------|----------------|---------------|-----------------|-----------|
| And    |        | CountryISOCode | Equals        | CR              | string    |
|        |        | LegalEntityId  | Equals        | CRMF            | string    |
|        |        | DocumentType   | Equals        | Project invoice | string    |

### Project Credit Note (CRI)
| And/or | And/or | Field          | Operator type | Value              | Data type |
|--------|--------|----------------|---------------|--------------------|-----------|
| And    |        | CountryISOCode | Equals        | CR                 | string    |
|        |        | LegalEntityId  | Equals        | CRMF               | string    |
|        |        | DocumentType   | Equals        | Project credit note| string    |

### Project Debit Note (CRI)
| And/or | And/or | Field          | Operator type | Value             | Data type |
|--------|--------|----------------|---------------|-------------------|-----------|
| And    |        | CountryISOCode | Equals        | CR                | string    |
|        |        | LegalEntityId  | Equals        | CRMF              | string    |
|        |        | DocumentType   | Equals        | Project debit note| string    |

### Project Export e-Invoice (CRI)
| And/or | And/or | Field          | Operator type | Value                    | Data type |
|--------|--------|----------------|---------------|--------------------------|-----------|
| And    |        | CountryISOCode | Equals        | CR                       | string    |
|        |        | LegalEntityId  | Equals        | CRMF                     | string    |
|        |        | DocumentType   | Equals        | Project Export invoice   | string    |

### Payment Receipt (CRI)
| And/or | And/or | Field          | Operator type | Value    | Data type |
|--------|--------|----------------|---------------|----------|-----------|
| And    |        | CountryISOCode | Equals        | CR       | string    |
|        |        | LegalEntityId  | Equals        | CRMF     | string    |
|        |        | DocumentType   | Equals        | Payment  | string    |

### Purchase e-invoice (CRI)
| And/or | And/or | Field          | Operator type | Value        | Data type |
|--------|--------|----------------|---------------|--------------|-----------|
| And    |        | CountryISOCode | Equals        | CR           | string    |
|        |        | LegalEntityId  | Equals        | CRMF         | string    |
|        |        | DocumentType   | Equals        | Self invoice | string    |


### Variables
The outbound data flow actions for the Costa Rican feature use the following variables. The system provides these variables.

- **BusinessDocumentDataModel** – The Business Document Data model variable that Finance or Supply Chain Management sends. The system transforms this variable into the format required for submission.
- **SignedXML** – The signed XML variable that the system sends back to Finance or Supply Chain Management. This variable contains the base64-encoded response body from the **Get Signed XML from Edicom** step. The response types use this variable to save the signed XML that the system gets from Edicom as an attachment to the invoice journal. The system also uses this variable to generate printable reports through QR codes.

| Name                      | Description                                       | Type        | Data type | Value                                           |
|---------------------------|---------------------------------------------------|-------------|-----------|-------------------------------------------------|
| BusinessDocumentDataModel | Contains the electronic document from the client  | From client | file      |                                                 |
| SignedXML                 | Signed XML document in base64-encoded format      | To client   | file      | Get signed XML from Edicom.Base64ResponseBody   |

After you import the **Electronic invoicing for Costa Rica** feature that includes the default feature setup, follow the steps in the next section to configure electronic documents.

### Setups-Application Setup

To configure the mapping between Dynamics 365 Finance source tables and electronic document formats, go to the **Setups** tab within the [**Electronic invoice feature**](#electronic-invoice-feature) section, and then select **Application Setup**. This step lets you define how data from Finance is linked to the correct electronic invoice formats for Costa Rica.

> [!NOTE]
> Although you don't set this configuration at the general feature level, it acts globally for the selected feature setup. You don't need to repeat these steps for each individual format or feature - one configuration is sufficient for all supported document types within the feature.

The following grid defines the link between the source table in Dynamics 365 Finance, the document context model, and the mapping configuration used for electronic invoicing:

| Table name               | Context model / Context                  | Electronic document mapping      | Mapping name         | Description                                                                                  |
|--------------------------|------------------------------------------|----------------------------------|----------------------|----------------------------------------------------------------------------------------------|
| Customer invoice journal | Customer invoice context model / Customer invoice context | Invoice Model mapping LATAM      | Customer E-Invoice   | Maps customer invoices to the LATAM invoice model for electronic submission |
| Project invoice          | Customer invoice context model / Project invoice context  | Invoice Model mapping LATAM      | Project E-Invoice    | Maps project invoices to the LATAM invoice model for electronic submission |
| Vendor invoice journal   | Customer invoice context model / Self invoice context     | Invoice Model mapping LATAM      | Vendor E-Invoice     | Maps vendor invoices to the LATAM invoice model for electronic submission |
| Customer transactions    | Customer invoice context model / Payment invoice          | Invoice Model mapping LATAM      | Customer Payments    | Maps customer payments to the LATAM invoice model for electronic submission |

> [!TIP]
> Ensure that the Context and Mapping name match the document type. Incorrect mappings cause errors in XML generation or submission to DGI.

## Configure electronic document parameters

To configure electronic document parameters, follow these steps.

1. Make sure that you import the country/region-specific ER configurations for the document context and electronic document model mapping that are required for Costa Rica. For more information, see [Set up Electronic document parameters](../global/gs-e-invoicing-set-up-parameters.md#set-up-electronic-document-parameters).
1. Go to **Organization administration** \> **Setup** \> **Electronic document parameters**.
1. In the **Electronic document** section, add records for the **Customer Invoice journal** and **Project invoice** table names.
1. For each table name, set the **Document context** and **Electronic document model mapping** fields in accordance with step 1.

The Electronic Document Parameters page in Dynamics 365 Finance. Shows on the left-hand navigation pane, you can see the following options:

- Electronic Document

- Features

- Electronic Invoicing

- Integration Channels

For the Electronic Document option on the right-hand side, the section labeled Electronic Reporting is displayed.

Within Electronic Reporting, a grid is presented which lists the electronic document configurations. This grid includes important associations between:

- The source table name

- The document context model and context

- The electronic document model mapping

- The final mapping name used for generating the electronic invoice.

This configuration is essential for determining how Dynamics 365 Finance maps internal data models to external electronic formats for submission to tax authorities or service providers.

Configure the grid as follows:

| Table name               | Microsoft-owned | Document context model         | Document context         | Electronic document model mapping | Mapping name        |
|--------------------------|-----------------|--------------------------------|--------------------------|-----------------------------------|---------------------|
| Customer invoice journal | No              | Customer invoice context model | Customer invoice context | Invoice Model mapping LATAM       | Customer E-Invoice  |
| Customer transactions    | No              | Customer invoice context model | Payment invoice          | Invoice Model mapping LATAM       | Customer Payments   |
| Project invoice          | No              | Customer invoice context model | Project invoice context  | Invoice Model mapping LATAM       | Project E-Invoice   |
| Vendor invoice journal   | No              | Customer invoice context model | Vendor invoice journal   | Invoice Model mapping LATAM       | Vendor E-Invoice    |
   
1. Save your changes, and close the page.
1. For each table name, follow these steps:

    1. Select **Response types**, select **New** to create a response type that you get from the back end, and enter the following values:

        - In the **Response type** field, enter **SignedXML** (the default value). (See the [Variables](#variables) section of this article.)
        - In the **Description** field, enter any meaningful name. Alternatively, leave the field blank.
        - In the **Submission status** field, select **Pending**.
        - In the **Model mapping** field, select **Edicom source file response format**.

    1. Repeat the preceding step, but set the **Submission status** field to **Pending update actions execution**. In this way, you can run a subset of the actions in the processing pipeline in a loop to continuously pull updated statuses and other information for the submitted documents from the tax authority.
    In the standard view, you should see a table similar to the following:

    | Response type | Description                        | Submission status                     | Data entity name | Model mapping                             |
    |---------------|------------------------------------|---------------------------------------|------------------|--------------------------------------------|
    | SignedXML     | Signed XML obtained from EDICOM    | Pending                               |                  | Edicom source file response import format  |
    | SignedXML     | Signed XML obtained from EDICOM    | Pending update actions execution      |                  | Edicom source file response import format  |

    > [!NOTE]
    > The response includes the signed XML that you get from Edicom. The system stores this signed XML as an attachment to the corresponding invoice journal. You can use it later to generate printable invoices through QR codes.

## Issue electronic invoices

After you complete all the required configuration steps, you can generate and submit electronic invoices for posted invoices by going to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Submit electronic documents**. For more information about how to generate electronic invoices, see [Submit electronic documents](../global/e-invoicing-submit-electronic-documents.md).

To check the results of a submission, go to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Electronic document submission log**, and select the required document type. For more information, see [Work with Electronic document submission log](../global/e-invoicing-submission-log.md).

For Costa Rica, after you submit the invoice, the submission status is set to **Pending update actions execution**. The response body is probably empty for the signed XML and the call to get the invoice status. An empty response body indicates that the XML isn't available immediately after submission. To address the pending status, use a function named **Execute update actions**. This function resumes the pipeline from the action that is marked as an update action. It then runs all subsequent actions in the pipeline in a loop. The status should change to **Executing** again. Then, after a few seconds, it reverts to **Pending update actions execution**.

:::image type="content" source="ltm-chl-e-invoice-execute-update-action.png" alt-text="Screenshot of the Execute update actions function being selected from the Functions dropdown menu.":::

> [!NOTE]
> By setting a recurrence schedule, you can configure the **Execute update actions** function to run in batch mode on a periodic basis.

When you review the submission details, you should notice that the steps run again. This time, the signed XML is received.

:::image type="content" source="ltm-chl-e-invoice-signed-XML.png" alt-text="Screenshot of the signed XML received.":::

As a result of the completed outbound flow, the signed XML is attached to the invoice journal as **EdicomSourceFile**.

:::image type="content" source="ltm-invoice-attached-source-file.png" alt-text="Screenshot of the attached source file.":::

For Costa Rica, the **Process response** action completes the pipeline after a few minutes.


## More resources

- [Electronic Invoicing service overview](../global/gs-e-invoicing-service-overview.md)
- [Get started with Electronic invoicing service administration](../global/gs-e-invoicing-administration-integration-components.md)
- [Setting up Electronic Invoicing](../global/gs-e-invoicing-set-up-overview.md)
- [Electronic Invoicing service independent software vendor (ISV) last-mile connector](../global/e-invoicing-isv-connector.md)
- [Dynamics 365 Country/Region expansion: localizations for LATAM Countries/Regions | June 27, 2024](https://community.dynamics.com/blogs/post/?postid=7bd2efc7-9344-ef11-840a-6045bdeef618)
- [Dynamics 365 Country/Region expansion: localizations for LATAM Countries/Regions | Dynamics 365 FastTrack Tech Talks (youtube.com)](https://www.youtube.com/watch?v=eK8TJmnhpJo)

- [Finance Localization for LATAM: Update on Additional Countries/Regions | Dynamics 365 Fast Track TechTalk | Jun 23, 2025](https://community.dynamics.com/blogs/post/?postid=f091c202-104b-f011-877a-7c1e52165747)
- [Finance Localization for LATAM: Update on Additional Countries/Regions | Dynamics 365 Fast Track TechTalk (youtube.com)](https://www.youtube.com/watch?v=g3oD3jqsePA)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
