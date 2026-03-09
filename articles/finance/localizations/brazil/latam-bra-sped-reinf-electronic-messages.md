---
title: Set up electronic messages for SPED-Reinf events
description: Learn how to set up electronic messages for SPED-Reinf events for Brazil, including an outline on importing the configuration from data entries.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.date: 03/05/2026
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2016-11-30
ms.custom:
  - bap-template
  - sfi-image-nochange
---

# Set up electronic messages for SPED-Reinf events

Microsoft Dynamics 365 Finance introduces electronic message functionality. By using this functionality, you can maintain and track various processes for electronic messages when there's an exchange of information between Finance and tax authority web services.

Before you issue SPED-Reinf events to the government website, use the predefined configuration that Microsoft prepared to meet SPED-Reinf requirements. Microsoft delivers this configuration as a data entity. After you import it into Finance, you can generate, validate, and deliver all events that are described in the SPED-Reinf scope.

## Import the configuration from the data entity

To set up electronic message functionality for communication of SPED-Reinf events, use the predefined configuration that's available in Microsoft Dynamics Lifecycle Services.

1. Sign in to [Lifecycle Services](https://lcs.dynamics.com).
1. Select the **Shared asset library** tile.
1. Select **Data package** as the asset type, and then select the package for the SPED-REINF event communication data entities. (The file name is **SPEDREINF_EMSettings Layout 2.1.2.zip**.)
1. Save the file in the location where you store data entities.
1. Sign in to Finance, and go to **Workspaces** > **Data management**.
1. Select the **Import** tile.
1. Enter a description and a name to identify the job, such as **SpedReinf**.
1. In the **Source data format** field, select **Package**.
1. Select **Upload**, and then select the file that you saved from Lifecycle Services (**SPEDReinf_EMSettings Layout 2.1.2.zip**).
1. Select **Save**, and wait until all data entities are shown on the page.
1. Select **Import**.

    You receive a notification about the import process. You can also manually refresh the page to view the progress of the import process. When the process finishes, you can view the **Execution summary** page.

    :::image type="content" source="../media/bra-execution-summary-page21.png" alt-text="Screenshot of the Execution summary page.":::

## Structure of electronic messages

Every event that you create, deliver, and receive is represented by a message and a message item.

The XML event message represents the message item. It includes the following information that's stored in the message or updated in Finance:

- The full National Registry of Legal Entities (CNPJ) number of the fiscal establishment
- The root CNPJ
- The booking period
- The start date of the period that the message is valid for
- The receipt protocol number
- A value that indicates whether the message is registered in Dynamics 365

You can find this configuration on the **Additional fields** page (**Tax** > **Setup** > **Electronic messages** > **Additional fields**).

:::image type="content" source="../media/bra-electronic-messaging-additional-fields21.png" alt-text="Screenshot of the configuration on the Additional fields page.":::

> [!NOTE]
> Don't remove this configuration. The package includes this configuration.

You classify the message item types by the type of event on the **Message item types** page (**Tax** > **Setup** > **Electronic messages** > **Message item types**).

:::image type="content" source="../media/bra-message-types21.png" alt-text="Screenshot of the Message item types page.":::

> [!NOTE]
> Don't remove this configuration. The package includes this configuration.

- To set up the number sequence for message items, go to **Tax** > **Setup** > **Parameters** > **General ledger parameters**. On the **Number sequences** tab, select a number sequence for the **Message** and **Message item** references.

:::image type="content" source="../media/bra-electronic-messages-number-sequences21.png" alt-text="Screenshot of the Number sequences tab on the General ledger parameters page.":::

> [!NOTE]
> You must define the number sequence as non-continuous.

## Certificates

Finance requires trusted certificates because you must always sign SPED-Reinf with an e-CNPJ certificate that ICP-Brasil authorizes, regardless of any other signatures. This e-CNPJ certificate should match the first eight digits of the root fiscal establishment's CNPJ number, because the report is issued by the root fiscal establishment and the related fiscal establishments.

In Finance, register the Key Vault certificate in Azure.

For information about how to set up a Key Vault client, see [Setting up Azure Key Vault Client](https://support.microsoft.com/help/4040305).

1. Go to **System administration** > **Setup** > **Key Vault parameters**.
1. Enter the following information:

    - Key Vault URL
    - Key Vault client
    - Key Vault secret key
    - Key Vault secret ID

After registration, associate the certificate in the setup parameters for the **Report generation** action, as described in the next section.

## Set up parameters 

Every time you create, prepare, validate, deliver, or receive a message, you must identify the related action through an X++ class on the **Executable class settings** page (**Tax** > **Setup** > **Electronic messages** > **Executable class settings**).

- **Preparation items (Preparacao dos eventos)** – Use this action to create and prepare the XML message. The action requests more parameters, such as **Booking date**, **CNPJ**, and **CNPJ root**, because the events are generated based on this information.

    :::image type="content" source="../media/bra-preparation-items21.png" alt-text="Screenshot of the Preparation items parameters.":::

- **Process response (Processo de reposta)** – Use this action to update the delivered message when the government approves it by using a protocol number. Additionally, use this action to update the message as registered on the government website.

    :::image type="content" source="../media/bra-preparation-items-process-response21.png" alt-text="Screenshot of the Preparation items process response parameters.":::

- **Report generation (Geracao de relatório)** – Use this action to send and receive the message item.

    :::image type="content" source="../media/bra-generate-reports-parameters21.png" alt-text="Screenshot of the Generate reports parameters.":::

> [!NOTE]
> Don't remove this configuration. The package includes this configuration.

## Specific actions

Before you deliver a message, set up XML schema validation to help prevent rejections from the government website.

1. Go to **Organization administration** > **Document management** > **Document management parameters**, and enable .xsd files by adding **XSD** as a new file type.

    :::image type="content" source="../media/bra-document-management-parameters21.png" alt-text="Screenshot of the Document management parameters page.":::

1. Go to **Tax** > **Setup** > **Electronic messages** > **Message processing actions**, and select **New** > **File** to attach the schemas (.xsd files) to the following actions:

    - Verify (Validar)
    - Re-Verify (Re-Validar)
    - Cancel-Verify (Exclusão-Validar)

1. Select the **Attachments** button (paper clip symbol) to attach the schemas of the events (XSD) that the SPED-Reinf makes available.

    :::image type="content" source="../media/bra-processing-actions21.png" alt-text="Screenshot of the Attachments button on the Message processing actions page.":::

1. Select **New** > **File** > **Add all schemas**.

    :::image type="content" source="../media/bra-add-schema21.png" alt-text="Screenshot of adding schemas.":::

1. Go to **Tax** > **Setup** > **Electronic messages** > **Message processing actions**, and select **Populate** (**Incluir**).
1. In the **Populate records action** field, select **Registrar transacões**.
 
    :::image type="content" source="../media/bra-message-processing-actions21.png" alt-text="Screenshot of the Populate records action field set on the Message processing actions page.":::

1. Go to **Tax** > **Setup** > **Electronic messages** > **Web service settings**, and set up a web services connection and certificates to issue and inquire about events.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]