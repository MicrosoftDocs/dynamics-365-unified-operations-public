---
title: Get started with Electronic invoicing for Chile
description: Learn how to set up Microsoft Dynamics 365 Finance and Regulatory Configuration Service (RCS) to use Chilean electronic invoices formats.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: article
ms.date: 02/15/2024 
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Connection configuration for Chilean electronic invoicing

[!include [banner](../../includes/banner.md)]

This article provides information that will help you get started with Electronic invoicing for Chile. It guides you through the configuration steps that are country/region-dependent in Dynamics 365 Finance or Dynamics 365 Supply Chain Management. These steps complement the steps that are described in [Electronic invoicing setup](../global/e-invoicing-set-up-overview.md).
For this, we are partnering with Edicom for the last-mile integration with the Chilean Tax Authorities.

After you configure electronic invoicing, you can generate, digitally sign, and submit the XML files of electronic invoices to the Authorized Certification Provider [**Edicom**](https://edicomgroup.com/electronic-invoicing/chile) according to the [regulatory requirements in Chile](https://www.sii.cl/servicios_online/1039-1182.html).

![Diagram of the electronic invoicing workflow in Chile.](ltm-chl-e-invoice-workflow.jpg)

> [!NOTE]
> The electronic invoicing approach that this article describes is implemented by using an invoicing service that's applicable only to cloud deployments of Finance or Supply Chain Management.

> [!IMPORTANT]
> This new E-Invoicing globalization feature for Chile (outbound flow) requires you to be on MS Dynamics 365 Finance version 10.0.40 specifically on build number 10.0.1935.60 or above. It can only be imported into the new Globalization Studio and it is not supported in RCS.

## <a name="prerequisites"></a>Prerequisites

Before you begin the procedures in this article, the following prerequisites must be met:

1. Ensure that the settings for the Chilean legal entity are in place. For more information, see [Set up legal entity and tax information for Chile ](ltm-chile-set-up-legal-entity-tax-information.md).
1. Gain familiarity with and understanding of Electronic invoicing as it's described in [Electronic invoicing overview](../global/e-invoicing-service-overview.md).
1. Do the common part of electronic invoicing service configuration as described in [Set up electronic invoicing](../global/gs-e-invoicing-set-up-overview.md).
1. You must enable the following features in **Feature management**:
	- **Electronic invoicing integration**
	- **E-Invoicing service workspace designer**
	- **Execute update actions for submitted documents**
1. Make sure that the following Electronic reporting (ER) format configurations are imported. For more information, see [Import Electronic reporting (ER) configurations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-import-ger-configurations.md).
    - Inventory e-invoice (CL)
	- Inventory Export e-Invoice (CL)
    - E-shipping guide (CL)
    - Project e-invoice (CL)
	- Project Export e-Invoice (CL)
	- Edicom source file response import format
    - Edicom response processing (CL)
	- Edicom response error log import
	
    > [!NOTE]
    > These formats are based on the corresponding **LATAM** format configurations that use the **Invoice model** and **Invoice model mapping** configurations. All required additional configurations are automatically imported.

## <a name="countryregion"></a>Configure the electronic invoicing feature

**Chilean electronic invoice (CL) "E-Invoicing for Chile: ISV last-mile connector with Edicom"** feature represents an outbound flow to issue sales documents. Some parameters of the feature are published with default values. Before you deploy the electronic invoicing feature to the service environment, add a feature based on the one provided by Microsoft, complete common parameters on the **Feature parameters** tab, review the default values, and update them as required, so that they better reflect your business operations.

In case of Chile, we interact with Edicom at least three times in the pipeline, first to submit the invoice, next to fetch the signed XML, and finally to fetch the status of the submitted invoice. Each of these interactions requires common parameters such as Edicom connection details and the authentication token provided by Edicom. Also, these common parameters are reused in feature setup for all document types. These values will be provided by Edicom when a company onboards.

> [!NOTE]
> The simplification of configurations of common parameters - it is no longer needed to go to each action and feature setup, and specify these common connection parameters repeatedly - using the **Feature parameters** tab will only be availavle starting from version 10.0.41.

1. Import the latest version of the **Chilean electronic invoice (CL)** Globalization feature as described in [Import features from the repository](../global/gs-e-invoicing-import-feature-global-repository.md). Once you import the feature from Dataverse, this is how it will look.
    ![Screenshot 1 of the imported Globalization feature for Chile.](ltm-chl-e-invoice-glog-feature-imported.png)
	![Screenshot 2 of the imported Globalization feature for Chile.](ltm-chl-e-invoice-glog-feature-imported2.png)
1. Create a copy of the imported Globalization feature, and select your configuration provider. For more information, see [Create a Globalization feature](../global/e-invoicing-create-new-globalization-feature.md).
1. On the **Versions** tab, verify that the **Draft** version is selected.
1. Specify values on the **Feature parameters** tab. These are connection and integration parameters to interoperate with Edicom's API.
    > [!NOTE]
    > The **Chilean electronic invoice (CL)** feature is provided by Microsoft. Before usage, it requires additional configuration as described in this article. For information about how to configure invoicing features and apply changes, see [Work with feature setups](../global/e-invoicing-feature-setup.md). For example, in addition to the connection parameters, you can filter specific legal entities so that they're processed in applicability rules. By default, the feature is applicable to all legal entities that have a primary address in Chile.
1. The copy of the feature is always created as a **Draft** version. Regardless of whether you made changes, you must complete, publish, and deploy the feature as described in [Complete, publish, and deploy a Globalization feature](../global/e-invoicing-complete-publish-deploy-globalization-feature.md).

## Outbound flow pipeline
To review the processing pipeline, go to the **Feature setup** upder the **Setups** tab, select the desired derived document type, and click **Edit**. The outbound flow consist of the following actions:
1. **Transform document**: a format that can be sent to Edicom is generated.
1. **Integrate with Edicom**: the generated invoice is submitted to Edicom
1. **Get status from Edicom for an invoice**: after the submission, the signed XML is fetched from Edicom. This document might not be immediately available as it takes some time for the PAC to generate it.
    > [!NOTE]
    > This is where the concept of update actions comes into play. Notice that the **Update action** checkbox is turned on for this step. This means that this step and all subsequent steps will be executed in a loop until it will be determined that a terminal state has been reached.
1. **Get status from Edicom for an invoice**: next, we fetch the status of the submitted invoice from Edicom in the loop.
1. **Process response**: the received response is then processed to determine if the terminal state has been reached. If the status response indicates a failure, the pipeline will be terminated and the submission marked as failed. If the response indicates a successful submission to the SII Chilean Internal Revenue Service, the pipeline cannot be completed yet because in Chile invoices can be rejected by customers for up to 8 days. During this time, the pipeline will be kept on hold in a state called Pending Execute Update action. If the response indicating that the customer has rejected the invoice is received, this will be detected in the process response step and the pipeline will be marked as failed.
1. **Terminate pipeline**: finally, there is the Terminate pipeline action having the number of days to wait before terminating specified. In the out-of-the-box default setup, the pipeline will terminate with a completed status if more than nine days have passed since the invoice was submitted. If there are no rejections, the terminate pipeline step will mark the pipeline as completed.

    ![Screenshot of the outbound pipeline.](ltm-chl-e-invoice-outbound-pipeline.png)

## Configure applicability rules
To provide context to find the exact Electronic Invoicing Globalization feature to run in the Electronic Invoicing Service, the Applicability rules must be poperly configured. These rules are provided out-of-the box checking the legal entity in the country ISO code. This particular feature setup supports all three types of invoices, customer invoices, debit notes, and credit notes.
![Screenshot of the setup on the Applicability rules.](ltm-chl-e-invoice-applicability-rules.png)

## Configure variables
There are the following Variables used in the outbound data flow actions of the Chilen feature:
- **BusinessDocumentDataModel**: the inbound Business Document Data model variable received from Finance / SCM and transformed into the format required for submission.
- **SignedXML**: the signed XML variable sent back to Finance / SCM, which contains the base 64 encoded response body from the Get Signed XML from Edicom step. As mentioned above, it is used in the response types to save as an attachment to the invoice journal and generate printable reports with QR codes.

![Screenshot of the setup on the Variables.](ltm-chl-e-invoice-variables.png)
	
After you imported the **Electronic invoicing for Chile** feature comprising out-of-the-box default feature setup, follow these remaining steps to configure electronic documents.

## Configure electronic document parameters
1. Make sure that the country/region-specific ER configurations for the document context and electronic document model mapping that are required for Chile are imported. For more information, see [Set up Electronic document parameters](../global/e-invoicing-set-up-parameters.md#set-up-electronic-document-parameters).
1. Go to **Organization administration** \> **Setup** \> **Electronic document parameters**.
1. In the **Electronic document** section, add records for the **Customer Invoice journal**, **Customer packing slip journal**, and **Project invoice** table names.
1. For each table name, set the **Document context** and **Electronic document model mapping** fields in accordance with step 1.

    ![Screenshot of the setup on the Electronic document tab of the Electronic document parameters page.](ltm-chl-e-invoice-documents.png)

1. Save your changes, and close the page.
1. For each table name, select **Response types**, select **New** to create a response type we would get from the back end, and enter the following values:

    - In the **Response type** field, enter **SignedXML** (the default value).
    - In the **Description** field, enter any meaningful name. Alternatively, leave the field blank.
    - In the **Submission status** field, select **Pending** .
    - In the **Model mapping** field, select **Edicom source file response format**.
	- Repeat the above steps for the **Submission status** having the value **Pending update actions execution** to continuously pull for updated statuses, etc. from the tax authority for the submitted documents, by the means of execution of a subset of the actions in the processing pipeline in a loop.
	
	![Screenshot of the setup of the response type for the Customer Invoice journal table name on the Document updates for response types page.](ltm-chl-e-invoice-response-type.png)
	
	> [!NOTE]
    > The response includes the signed XML obtained from Edicom, which will be stored as an attachment to the corresponding invoice journal in the system. It will eventually be used to generate printable invoices with QR codes.

## <a name="issue"></a>Issue electronic invoices

After you complete all the required configuration steps, you can generate electronic invoices for posted invoices. You can inquire about the results of the submission by going to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Electronic document submission log** and selecting the required document type.

To download the XML files of electronic invoices for successfully processed invoices, select **Electronic document** \> **Download file**.

> [!IMPORTANT]
> In current implementations, the standard submission procedure described above only generates electronic invoices and stores their XML files on the service side, but it doesn't submit the invoices. For the submission of Chilean electronic invoices, integration with the [Electronic Invoicing service ISV last-mile connector](../global/e-invoicing-isv-connector.md) is required. However, this connector hasn't been released yet.

## More resources

- [Electronic invoicing overview](../global/e-invoicing-service-overview.md)
- [Get started with Electronic invoicing service administration](../e-invoicing-get-started-service-administration.md)
- [Get started with Electronic invoicing](../e-invoicing-get-started.md)
- [Electronic Invoicing service independent software vendor (ISV) last-mile connector](../global/e-invoicing-isv-connector.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
