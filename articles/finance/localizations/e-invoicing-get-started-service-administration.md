---
# required metadata

title: Get started with Electronic invoicing service administration
description: This topic explains how to get started with Electronic invoicing.
author: gionoder
ms.date: 03/29/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: ["97423", "intro-internal"]
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: janeaug
ms.search.validFrom: 2020-07-08
ms.dyn365.ops.version: AX 10.0.12

---

# Get started with Electronic invoicing service administration

[!include [banner](../includes/banner.md)]

## Prerequisites

Before you complete the procedures in this topic, the following prerequisites must be in place:

- You must have access to your Microsoft Dynamics Lifecycle Services (LCS) account.
- You must have an LCS project that includes version 10.0.17 or later of Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management. Additionally, these apps must be deployed in one of the following Azure geographies:

    - United States
    - Europe
    - United Kingdom
    - Asia

- You must have access to your Dynamics 365 Regulatory Configuration Services (RCS) account.
- You must activate the Globalization feature for your RCS account in Feature management. For more information, see [Regulatory Configuration Services (RCS) - Globalization features](rcs-globalization-feature.md).
- You must create a key vault and a storage account in Azure. For more information, see [Create an Azure storage account and a key vault](e-invoicing-create-azure-storage-account-key-vault.md).

## Install the add-in for microservices in Lifecycle Services

1. Sign in to your LCS account, and on the LCS project dashboard, select an LCS project.
2. In the project, on the **Environments** dashboard, select your deployed environment. The environment that you select must be running.
3. On the **Power Platform Integration** tab, in the **Environment add-ins** field group, select **Install a new add-in**.
4. Select **Electronic Invoicing**.
5. In the **AAD application ID** field, enter **091c98b0-a1c9-4b02-b62c-7753395ccabe**. This is a fixed value.
6. In the **AAD tenant ID** field, enter the tenant ID of your Azure subscription account. The Azure Active Directory (Azure AD) tenant that you specify should be the same tenant that is used for RCS.
7. Review the terms and conditions, and then select the check box.
8. Select **Install**. Installation can take up to several minutes.


## Set up the parameters for RCS integration with Electronic invoicing

1. Sign in to your RCS account.
2. In the **Globalization features** workspace, in the **Related settings** section, select **Electronic reporting parameters**.
3. On the **Electronic Invoicing** tab, in the **Service endpoint URI** field, enter the appropriate service endpoint for your Azure geography, as shown in the following table.

    | Datacenter Azure geography | Service endpoint URI                                                       |
    |----------------------------|----------------------------------------------------------------------------|
    | United States              | <p>`https://gw.us-il101.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.us-il102.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.us-il103.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.us-il104.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.us-il105.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.us-il106.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.us-il107.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.us-il108.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.us-il109.gateway.prod.island.powerapps.com/electronicinvoicing/`</p> |
    | Europe                     | <p>`https://gw.eu-il101.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.eu-il102.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.eu-il103.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.eu-il104.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.eu-il105.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.eu-il106.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.eu-il107.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.eu-il108.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.eu-il109.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.eu-il110.gateway.prod.island.powerapps.com/electronicinvoicing/`</p> |
    | United Kingdom             | <p>`https://gw.uk-il101.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.uk-il102.gateway.prod.island.powerapps.com/electronicinvoicing/`</p> |
    | Asia                       | <p>`https://gw.as-il101.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.as-il102.gateway.prod.island.powerapps.com/electronicinvoicing/`</p> |
    | Japan                      | <p>`https://gw.jp-il101.gateway.prod.island.powerapps.com/electronicinvoicing/`</p> |
    | Switzerland                | <p>`https://gw.ch-il101.gateway.prod.island.powerapps.com/electronicinvoicing/`</p> |
    | Brazil                     | <p>`https://gw.br-il101.gateway.prod.island.powerapps.com/electronicinvoicing/`</p> <p>`https://gw.br-il102.gateway.prod.island.powerapps.com/electronicinvoicing/`</p> |
    | United Arab Emirates       | <p>`https://gw.ae-il101.gateway.prod.island.powerapps.com/electronicinvoicing/`</p> |
    | Australia                  | <p>`https://gw.au-il101.gateway.prod.island.powerapps.com/electronicinvoicing/`</p> <p>`https://gw.au-il102.gateway.prod.island.powerapps.com/electronicinvoicing/`</p> |
    | Canada                     | <p>`https://gw.ca-il101.gateway.prod.island.powerapps.com/electronicinvoicing/`</p> <p>`https://gw.ca-il102.gateway.prod.island.powerapps.com/electronicinvoicing/`</p> |
    | France                     | <p>`https://gw.fr-il101.gateway.prod.island.powerapps.com/electronicinvoicing/`</p> |
    | India                      | <p>`https://gw.in-il101.gateway.prod.island.powerapps.com/electronicinvoicing/`</p> |


4. Verify that the **Application ID** field is set to **0cdb527f-a8d1-4bf8-9436-b352c68682b2**. This value is a fixed value.
5. In the **LCS Environment ID** field, enter the ID of your LCS environment.
6. Select **Save**, and then close the page.

## Create Key Vault references

1. Sign in to your RCS account.
2. In the **Globalization feature** workspace, in the **Environment** section, select the **Electronic invoicing** tile.
3. On the **Environment setups** page, on the Action Pane, select **Service environments**, and then select **Key Vault parameters**.
4. Select **New** to create a key vault reference.
5. In the **Name** field, enter the name of the key vault reference. In the **Description** field, enter a description.
6. In the **Key Vault URI** field, paste the key vault secret from Azure Key Vault. For more information, see [Create an Azure storage account and a key vault](e-invoicing-create-azure-storage-account-key-vault.md).
7. Select **Save**.

## Create Storage account secret

1. On the **Environment setups** page, on the Action Pane, select **Service environment** > **Key Vault parameters**.
2. Select a **Key Vault reference** and in the **Certificates** section, select **Add**.
3. In the **Name** field, enter the name of the storage account secret. For more information, see [Create an Azure storage account and a key vault](e-invoicing-create-azure-storage-account-key-vault.md).
4. In the **Description** field, enter a description.
5. In the **Type** field, select **Secret**.
6. Select **Save**, and then close the page.

## Create a digital certificate secret

1. On the **Environment setups** page, on the Action Pane, select **Service environment**, and then select **Key Vault parameters**.
2. Select a **Key Vault reference** and then in the **Certificates** section, select **Add**.
3. In the **Name** field, enter the name of the digital certificate secret. For more information, see [Create an Azure storage account and a key vault](e-invoicing-create-azure-storage-account-key-vault.md).
4. In the **Description** field, enter a description.
5. In the **Type** field, select **Certificate**.
6. Select **Save**, and then close the page.

## Create a service environment

1. Sign in to your RCS account.
2. In the **Globalization feature** workspace, in the **Environment** section, select the **Electronic invoicing** tile.
3. On the **Environment setups** page, on the Action Pane, select **Service environment**.
4. Select **New** to create a new service environment.
5. In the **Name** field, enter the name of the e-Invoicing environment. In the **Description** field, enter a description.
6. In the **Storage SAS token secret** field, select the name of the storage account secret that must be used to authenticate access to the storage account.
7. In the **Users** section, select **Add** to add a user who is allowed to submit electronic invoices through the environment and also connect to the storage account.
8. In the **User ID** field, enter the alias of the user. In the **Email** field, enter the user's email address.
9. Select **Save**.
10. If your country/region-specific invoices require a chain of certificates to apply digital signatures, on the Action pane, select **Key Vault parameters**, then select **Chain of certificates**, and follow these steps:

    1. Select **New** to create a chain of certificates.
    2. In the **Name** field, enter the name of the chain of certificate. In the **Description** field, enter a description.
    3. In the **Certificates** section, select **Add** to add a certificate to the chain.
    4. Use the **Up** or **Down** button to change the position of the certificate in the chain.
    5. Select **Save**, and then close the page.
    6. Close the page.

11. On **Service environment** page, on the Action Pane, select **Publish** to publish the environment to the cloud. The value of the **Status** field is changed to **Published**.

## Create a connected application

1. On the **Environments setup** page, on the Action Pane, select **Connected applications**.
2. Select **New** to create a connected application.
3. In the **Name** field, enter the name of the application to connect.
4. In the **Application** field, enter the URL of the Finance and Supply Chain Management environment to connect.
4. In the **Tenant** field, enter the tenant of the Finance and Supply Chain Management environment.
5. Select **Save**.
6. On the Action Pane, select **Check connection** to test the connection with the environment. Then close the page.

## Link connected applications to environments

1. On the **Environments setup** page, select **New** to assign a connected application to an environment.
2. In the **Connected application** field, select a connected application.
3. In the **Service environment** field, select a service environment.
4. Select **Save**, and then close the page.

## Set up Electronic invoicing integration in Finance and Supply Chain Management

### Turn on the Electronic invoicing integration feature

1. Sign in to your Finance or Supply Chain Management instance.
2. In the **Feature management** workspace, search for the **Electronic invoicing integration** feature. If this feature doesn't appear on the page, select **Check for updates**.
3. Select the feature, and then select **Enable now**.

### Set up the service endpoint URL

1. Go to **Organization administration \> Setup \> Electronic document parameters**.
2. On the **Electronic invoicing** tab, in the **Endpoint URL** field, enter the appropriate service endpoint for your Azure geography, as shown in the following table.

    | Datacenter Azure geography | Service endpoint URI                                                       |
    |----------------------------|----------------------------------------------------------------------------|
    | United States              | <p>`https://gw.us-il101.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.us-il102.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.us-il103.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.us-il104.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.us-il105.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.us-il106.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.us-il107.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.us-il108.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.us-il109.gateway.prod.island.powerapps.com/electronicinvoicing/`</p> |
    | Europe                     | <p>`https://gw.eu-il101.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.eu-il102.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.eu-il103.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.eu-il104.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.eu-il105.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.eu-il106.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.eu-il107.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.eu-il108.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.eu-il109.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.eu-il110.gateway.prod.island.powerapps.com/electronicinvoicing/`</p> |
    | United Kingdom             | <p>`https://gw.uk-il101.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.uk-il102.gateway.prod.island.powerapps.com/electronicinvoicing/`</p> |
    | Asia                       | <p>`https://gw.as-il101.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.as-il102.gateway.prod.island.powerapps.com/electronicinvoicing/`</p> |
    | Japan                      | <p>`https://gw.jp-il101.gateway.prod.island.powerapps.com/electronicinvoicing/`</p> |
    | Switzerland                | <p>`https://gw.ch-il101.gateway.prod.island.powerapps.com/electronicinvoicing/`</p> |
    | Brazil                     | <p>`https://gw.br-il101.gateway.prod.island.powerapps.com/electronicinvoicing/`</p> <p>`https://gw.br-il102.gateway.prod.island.powerapps.com/electronicinvoicing/`</p> |
    | United Arab Emirates       | <p>`https://gw.ae-il101.gateway.prod.island.powerapps.com/electronicinvoicing/`</p> |
    | Australia                  | <p>`https://gw.au-il101.gateway.prod.island.powerapps.com/electronicinvoicing/`</p> <p>`https://gw.au-il102.gateway.prod.island.powerapps.com/electronicinvoicing/`</p> |
    | Canada                     | <p>`https://gw.ca-il101.gateway.prod.island.powerapps.com/electronicinvoicing/`</p> <p>`https://gw.ca-il102.gateway.prod.island.powerapps.com/electronicinvoicing/`</p> |
    | France                     | <p>`https://gw.fr-il101.gateway.prod.island.powerapps.com/electronicinvoicing/`</p> |
    | India                      | <p>`https://gw.in-il101.gateway.prod.island.powerapps.com/electronicinvoicing/`</p> |

3. In the **Environment** field, enter the name of the service environment published in Electronic invoicing.
4. Select **Save**, and then close the page.

### Enable Flighting keys for Finance or Supply Chain Management version 10.0.17

1. Execute the following SQL command:

    INSERT INTO SYSFLIGHTING (FLIGHTNAME, ENABLED) VALUES ('BusinessDocumentSubmissionServiceEnabled', 1)
    
    INSERT INTO SYSFLIGHTING (FLIGHTNAME, ENABLED) VALUES ('ElectronicInvoicingServiceIntegrationFeature', 1)

2. Perform an IISreset command for all AOSs.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
