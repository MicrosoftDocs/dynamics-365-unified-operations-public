---
# required metadata

title: Get started with the e-Invoicing service for Mexico
description: This topic provides information about getting started with the e-Invoicing service for Mexico in Dynamics 365 Finance and Dynamics 365 Supply chain management.
author: gionoder
manager: AnnBe
ms.date: 06/24/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 97423
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: janeaug
ms.search.validFrom: 2020-07-08
ms.dyn365.ops.version: AX 10.0.12

---

# Get started with the e-Invoicing service for Mexico

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]


The e-Invoicing service for Mexico may not currently support all the functions that are available in the CFDI document and related integration that is built
into Dynamics 365 Finance or Dynamics 365 Supply chain management.

In this topic, you will learn how to enable e-invoicing services for Mexico, including the configuration steps which are Mexico-dependent in Regulatory Configuration Services (RCS) and in Microsoft Dynamics 365 Finance. This topic also guides you through the process in Finance for submitting CFDI invoices through the service, and how to acknowledge the results of processing over the status in CFDI invoices.

## Prerequisites

To complete these steps, you must first do or verify the following:

- Complete the steps described in Get started with e-invoicing service.

## RCS setup

During the RCS setup you will:

- Import the e-invoicing feature for processing CFDI invoices.
- Review the format configurations required for CFDI invoices generation, submission and response scenarios, and cancellation submission and response.
- Configure the events that will support the CFDI invoice submission scenarios.
- Publish the CFDI invoice e-invoicing feature.

The **e-Invoicing feature** is the generic name of the resource that will be configured and published for consumption of the e-Invoicing service server. In this case, the CFDI invoices (MX) is the e-Invoicing feature we want to set up.

Import e-Invoicing features

1. Sign into your RCS account and go to the **Globalization features workspace**.
2. Select **Features \> e-invoicing**.
3. Select **Import** to import the **CFDI invoices (MX)** feature from the Global repository.

> [!NOTE]
> If you don’t see the feature in the list, select **Synchronize** and then repeat step 3.

![Select import CDFI feature](media/e-Invoicing-services-get-started-MEX-Select-Import-CFDI-feature.png)

If you import the **CFDI invoices (MX)** feature from Global repository, all feature settings, including configurations and actions are imported too.

### Create a new version of the CFDI invoices (MX) feature

You can create a new version, for example, if updating URLs is needed. For more information, see .

1. On the **e-Invoicing Features** page, select the **Versions** tab.
2. Select **New**.

![Select New e-Invoicing feature](media/e-Invoicing-services-get-started-MEX-Select-New-e-Invoicing-feature.png)

### Configuration versions

1. On the **e-Invoicing Features** page, on the **Configurations** tab, select **Add** or **Delete** to manage the configuration versions.

![Manage e-Invoicing feature Configurations](media/e-Invoicing-services-get-started-MEX-Manage-e-Invoicing-feature-Configurations.png)

When you create a new version, all configurations are inherited from the last published version. To process CFDI invoices, the following configurations are required:

   - CFDI invoice (BusinessDocumentService)
   - CFDI response message import
   - CFDI error log import
   - CFDI cancelation request (MX) (BusinessDocumentService)
   - CFDI invoice (BusinessDocumentService)

2. From the list, select a configuration version, and then select **Edit** or **View** to access the **ER format designer** to edit or view a configuration.

![Configuration ER format designer](media/e-Invoicing-services-get-started-MEX-Configuration-ER-format-designer.png)

Use the **Format designer** to edit and view the ER format file configurations. For more information, see [Create electronic document configurations](../../dev-itpro/analytics/electronic-reporting-configuration.md).

![ER format designer](media/e-Invoicing-services-get-started-MEX-ER-format-designer.png)

## Feature setup

1.  On the **e-Invoicing Features** page, select the **Setups** tab.
2.  Select **Add**, **Delete**, or **Edit** to manage the feature setups.

![Manage e-Invoicing feature setup](media/e-Invoicing-services-get-started-MEX-Manage-e-Invoicing-feature-Setup.png)

To submit CFDI invoices for authorization, the Feature setup **Sales invoice** (generate xml, submit xml, processing response), is required.

To submit CFDI invoice cancellation, the Feature setup **Cancellation** and **Cancel** are required.

### Sales invoice event feature setup

1. On the **e-Invoicing Features** page, on the **Setups** tab, in the **Feature setup** group, select **Sales invoice**.
2. Select **Edit** to configure the actions, applicability rules and variables.

![Edit e-Invoicing feature setup](media/e-Invoicing-services-get-started-MEX-Edit-e-Invoicing-feature-setup.png)

3. On the **Feature version setup** page, select the **Actions** tab to manage the **Actions** list.

![Select Actions](media/e-Invoicing-services-get-started-MEX-Select-Actions.png)

: [!NOTE]
> Actions define a list of operations to be executed in a sequential order to accomplish the full execution of the event.

| **No** | **Action**               | **Action name**                              | **Action description**                                  |
|--------|--------------------------|----------------------------------------------|---------------------------------------------------------|
| 1      | Transform document       | Generate CFDI E-Invoice without digital sign | Generates the CFDI E-Invoice.                           |
| 2      | Sign document            | Digital sign                                 | Digital signing E-Invoice for submission.               |
| 3      | Call Mexican PAC service | Submit CFDI E-Invoice                        | WCF client submits the CFDI E-Invoice.                  |
| 4      | Process response         | Analyze web service response                 | Analyzes the web service response and return error log. |

### Set up the URL for Mexican PAC web services 

1. On the **Feature version setup** page, on the **Actions** tab, in the **Actions** group, select **Call Mexican PAC service**.
2. In the **Parameters** group, in the **URL address** field, enter the web service for CFDI invoice submission.

> [!NOTE]
> Use these steps to update the URL for **Cancel** and **Cancelation request** feature setups (**Call Mexican PAC service** action).

## Assign the Draft version to an e-invoicing environment

1. On the **e-Invoicing Features** page, on the **Environments** tab, select **Enable**.
2. Select the environment and then in the **Effective date from** field, enter the date when the environment will be enabled.
3. Select **Enable**.

![Enable e-Invoicing environment](media/e-Invoicing-services-get-started-MEX-Enable-e-Invoicing-Environment.png)

## Change version status to Completed

1. On the **e-Invoicing Features** page, on the **Versions** tab, select the **Draft** version of the e-invoicing feature.
2. Select **Change status**.
3. Select **Complete.**

## Change the version status to Published

1. On the **e-Invoicing Features** page, select the **Versions** tab.
2. Select **Change status**, and then select **Publish**.

## Publish the e-invoicing feature

1. On the **e-Invoicing Features** page, select the **Versions** tab to manage the status of the feature, **CFDI invoices (MX)**.
2. Select **Change status** to change the status of the feature.

![Change status of e-Invoicing feature](media/e-Invoicing-services-get-started-MEX-Change-status-of-e-Invoicing-feature.png)

## Set up e-Invoicing service integration in Finance

Complete the following steps to set up the e-Invoicing service in Finance.

- Import the ER data model, ER data model mapping, and formats required for CFDI invoices.
- Configure a response type for updating the CFDI invoices, which are used for response from PAC server.

## Import the ER data model, ER data model mapping, and context configurations for CFDI invoices

1. Sign in into Finance and go to **Electronic reporting** workspace
2. On Configuration providers, select **Microsoft** title. Make sure this configuration provider is **Active**. For details about how to set a provider to Active, see Create configuration providers and mark them as active.
3. Select **Repositories** \> **Global resource**.
4. Select **Open**, and import the **Invoice model, Invoice model mapping,** CFDI invoice format (MX), CFDI invoice cancelation request format (MX), CFDI invoice cancel format (MX).

## Enable the feature for processing CFDI invoices

1. Go to **Organization administration \> Setup \> Electronic document parameters**.
2. On the **Features** tab, enable **MX-00010 and MX-00016 Feature references**.

![Enable CFDI feature](media/e-Invoicing-services-get-started-MEX-Enable-CFDI-feature.png)

## Import ER configurations and setup the response types for updating the CFDI invoices

### Import ER configurations

1. Go to **Electronic reporting** workspace.
2. On Configuration providers, select **Microsoft** title.
3. Select **Repositories**.
4. Select **Global resource \> Open**.
5. Import Response message model, CFDI error log import (MX), CFDI error log import (MX), CFDI response message import (MX).

### Set up the response types

1. Go to **Organization administration \> Setup \> Electronic document parameters**.
2. On the **Electronic document** tab, select **Add**, enter the customer invoice journal, and in the **Table name** field, select the project invoice.
3. For each table, define a related document context.

    - For **Customer invoice journal,** enter **Customer invoice context**.
    - For **Project invoice,** enter **Project invoice context**.

4. Select **Response types** to configure the response types for updating the **Customer invoice journal** or **Project invoice** in the response to the return from the e-invoicing service.
5. Select **New**, and in the **Response type** field, select **Response**.
6. In the **Submission status** field, select **Pending**.
7. In the **Model mapping** field, select **Response message import format – Model mapping from response message**.
8. Select **Save**.
9. Select **New**, and in the **Response type** field, select **ResponseData**.
10. In the **Submission status** field, select **Pending**.
11. In the **Model mapping** field, select **CFDI response data import format (details) – Response data import**, and then select **Save**.

## Processing electronic invoices in Finance 

During the processing of CFDI invoices in Finance through e-Invoicing service, you can:

- Submit CFDI invoices
- View the submission execution logs
- Submit the cancellation of a CFDI invoice

## Submit CFDI invoices

After you enable the **Configurable e-Invoicing Service integration** feature, the **Export/Import electronic invoice process** (**Accounts receivable** \>
**Invoices** \> **E-invoices**) for submitting CFDI invoices can no longer be used and it is replaced by the new process, **Submit electronic documents**.

> [!NOTE]
> Before you use the new **Submit electronic documents** process, verify that the setup required for Mexican e-invoices was completed. For more information, see [CFDI layout version 3.3](latam-mex-cfdi-3-3.md).

1. Go to **Organization administration \> Periodic \> Electronic documents \> Submit electronic documents**.
2. For the first submission of the document, always set the **Resubmit documents** field to **No**. Set the **Resubmit documents** field to **Yes** if you need to resubmit a document through the service
3. Expand the **Records to include** FastTab, and select **Filter** to build the query and select documents for submission.

![Submit CFDI document](media/e-Invoicing-services-get-started-MEX-Submit-CFDI-document.png)

When you first attempt to submit a document through the services, you will be asked to confirm the connection with the e-Invoicing service. Select **Click here to connect to Electronic Document Submission Service**.

## View submission logs

You can view submission log for all submitted documents or for just one.

### View all submission logs

After you enable the **Configurable e-Invoicing Service integration** feature, a new page is available that you can use to follow up on the document submission process. Through this page you can see the submission logs for all submitted documents.

1. Go to **Organization administration \> Periodic \> Electronic documents \> Electronic document submission log**.
2. In the **Document type** field, select **Customer invoice journal** to filter required electronic documents.

![Select document type for viewing submission log](media/e-Invoicing-services-get-started-MEX-Select-document-type-for-viewing-submission-log.png)

3. Select **Inquires** \> **Submission details** to view the details of submission execution logs.

![View submission log details](media/e-Invoicing-services-get-started-MEX-View-submission-log-details.png)

The submission log is shown by three groups of information:

- **Processing actions**: The execution log of the actions that were configured in the **Feature version set up** in RCS. The **Status** column shows if the action was successfully executed or not.
- **Action files**: The intermediate files generated with the execution of the actions. Select **View** to download and view the file .
- **Processing action log**: The results of the communication between the e-Invoicing service with the target web service, and what was returned of the processing from the web service. The **Error code** column contains the return code that was returned by the authorization web service.
- When the submitted CFDI invoice is authorized, the status of CFDI invoice is updated to **Approved**.

### View submission logs through the CFDI (electronic invoices)

After you enable the **Configurable e-Invoicing Service integration** feature, you can also see the submission logs through the CFDI (electronic invoices).

1. Go to **Accounts receivable \> Inquires and reports \> CFDI (electronic invoices)**.
2. Select a CFDI invoice that was submitted after the **Configurable e-Invoicing Service integration** feature was enabled.
3. Select **History \> Electronic document log**.

![View submission log from CFDI invoice](media/e-Invoicing-services-get-started-MEX-View-submission-log-from-CFDI-invoice.png)
> [!NOTE]
> For CFDI invoices that were submitted before the **Configurable e-Invoicing Service integration** feature was enabled, the **History** button is enabled. For CFDI invoices which were submitted after enabling the **Configurable e-Invoicing Service integration** feature, the **History** button is not enabled.

## Submit cancellation of CFDI invoices

After you enable the **Configurable e-Invoicing Service integration** feature, the legacy process for cancelling CFDI invoices no longer works as it is replaced by a new cancellation process that is embedded on **Electronic document submission log.**

1. Go to **Accounts receivable \> Inquires and reports \> CFDI (electronic invoices)**.
2. If the CFDI invoice has the status **Approved**, select **Function \> Cancel CFDI**.
3. Go to **Organization administration \> Periodic \> Electronic documents \> Electronic document submission log**.
4. Select the CFDI invoice, and then select **Functions** \> **Send related submissions**.
5. Enter a **Description** for the related submission and then select **OK**.

### View cancellation submission logs

1. Go to **Organization administration \> Periodic \> Electronic documents \> Electronic document submission log**.
2. In the **Document type** field, select **Customer invoice journal** to filter only customer invoice journal documents.
3. Select the CFDI invoice and then select **Inquires** \> **Related submission**.

> [!NOTE]
> This page shows all related submissions and the submission status, for a given CFDI invoice. In the following graphic, the first line represents the
submission that requested the approval of the CFDI invoice, and the second line represents the submission that cancelled that CFDI invoice.

![View cancellation submission log](media/e-Invoicing-services-get-started-MEX-View-cancellation-submission-log.png)

1. Select **Inquire** \> **Submission details** to view the details of the submission execution logs.

![View cancellation submission log details](media/e-Invoicing-services-get-started-MEX-View-cancellation-submission-log-details.png)

## Related articles

- [E-Invoicing service overview](e-invoicing-service-overview.md)
- [Get started with e-Invoicing services](e-invoicing-get-started.md)
- [Set up e-Invoicing](e-invoicing-setup.md)

