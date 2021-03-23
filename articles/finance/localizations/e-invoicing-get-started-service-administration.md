---
# required metadata

title: Get started with Electronic invoicing add-in service administration
description: This topic explains how to get started with the Electronic invoicing add-in.
author: gionoder
manager: AnnBe
ms.date: 03/12/2021
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
ms.custom: 97423
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: janeaug
ms.search.validFrom: 2020-07-08
ms.dyn365.ops.version: AX 10.0.12

---

# Get started with Electronic invoicing add-in service administration

[!include [banner](../includes/banner.md)]

## Prerequisites

Before you complete the procedures in this topic, the following prerequisites must be in place:

- You must have access to your Microsoft Dynamics Lifecycle Services (LCS) account.
- You must have an LCS project that includes version 10.0.17 or later of Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management. Additionally, these apps must be deployed in one of the following Azure geographies:

    - East US
    - West US
    - North EU
    - West EU

- You must have access to your Dynamics 365 Regulatory Configuration Services (RCS) account.
- You must activate the Globalization feature for your RCS account in Feature management. For more information, see [Regulatory Configuration Services (RCS) - Globalization features](rcs-globalization-feature.md).
- You must create a key vault and a storage account in Azure. For more information, see [Create an Azure storage account and a key vault](e-invoicing-create-azure-storage-account-key-vault.md).

## Install the add-in for microservices in Lifecycle Services

1. Sign in to your LCS account.
2. Select the **Preview feature management** tile.
3. In the **Public Preview Features** section, select **e-Invoicing service**.
4. Make sure that the **Preview feature enabled** option is set to **Yes**.
5. On your LCS dashboard, select your LCS deployment project. The LCS project must be running.
7. On the **Environment add-ins** tab, select **Install a new add-in**.
8. Select **e-invoicing Services** and in the **AAD application ID** field, enter **091c98b0-a1c9-4b02-b62c-7753395ccabe**. This is a 
fixed value.
10. In the **AAD tenant ID** field, enter the tenant ID of your Azure subscription account.
11. Review the terms and conditions, and then select the check box.
12. Select **Install**.


## Set up the parameters for RCS integration with the Electronic invoicing add-in

1. Sign in to your RCS account.
2. In the **Electronic reporting** workspace, in the **Related links** section, select **Electronic reporting parameters**.
3. On the **e-Invoicing service** tab, in the **Service endpoint URI** field, enter the appropriate service endpoint for your Azure geography, as shown in the following table.

    | Datacenter Azure geography | Service endpoint URI                                                       |
    |----------------------------|----------------------------------------------------------------------------|
    | East US                    | `https://electronicinvoicing.eus-il301.gateway.prod.island.powerapps.com/` |
    | West US                    | `https://electronicinvoicing.wus-il301.gateway.prod.island.powerapps.com/` |
    | North EU                   | `https://electronicinvoicing.neu-il301.gateway.prod.island.powerapps.com/` |
    | West EU                    | `https://electronicinvoicing.weu-il301.gateway.prod.island.powerapps.com/` |

4. Verify that the **Application Id** field is set to **0cdb527f-a8d1-4bf8-9436-b352c68682b2**. This value is a fixed value.
5. In the **LCS Environment Id** field, enter the ID of your LCS subscription account.
6. Select **Save**, and then close the page.

## Create Key Vault secret

1. Sign in to your RCS account.
2. In the **Globalization feature** workspace, in the **Environment** section, select the **Electronic invoicing add-in** tile.
3. On the **Environment setups** page, on the action Pane, select **Service environment**, and then select **Key Vault parameters**.
4. Select **New** to create a key vault secret.
5. In the **Name** field, enter the name of the key vault secret. In the **Description** field, enter a description.
6. In the **Key Vault URI** field, paste the secret from Azure Key Vault.
7. Select **Save**.

## Create Storage account secret

1. Go to **System administration** > **Setup** > **Key Vault parameters**, and select a Key vault secret.
2. In the **Certificates** section, select **Add**.
3. In the **Name** field, enter the name of the storage account secret and in the **Description** field, enter a description.
4. In the **Type** field, select **Certificate**.
5. Select **Save**, and then close the page.

## Create a digital certificate secret

1. Go to **System administration** > **Setup** > **Key Vault parameters**, and select a Key vault secret.
2. In the **Certificates** section, select **Add**.
3. In the **Name** field, enter the name of the digital certificate secret and in the **Description** field, enter a description.
4. In the **Type** field, select **Certificate**.
5. Select **Save**, and then close the page.

## Create an Electronic invoicing add-in environment

1. Sign in to your RCS account.
2. In the **Globalization feature** workspace, in the **Environment** section, select the **Electronic invoicing add-in** tile.

## Create a service environment

1. On the **Environment setups** page, on the Action Pane, select **Service environment**.
2. Select **New** to create a new service environment.
3. In the **Name** field, enter the name of the e-Invoicing environment. In the **Description** field, enter a description.
4. In the **Storage SAS token secret** field, select the name of the storage account secret that must be used to authenticate access to the storage account.
5. In the **Users** section, select **Add** to add a user who is allowed to submit electronic invoices through the environment and also connect to the storage account.
6. In the **User ID** field, enter the alias of the user. In the **Email** field, enter the user's email address.
7. Select **Save**.
8. If your country/region-specific invoices require a chain of certificates to apply digital signatures, on the Action pane, select **Key Vault parameters**, then select **Chain of certificates**, and follow these steps:

    1. Select **New** to create a chain of certificates.
    2. In the **Name** field, enter the name of the chain of certificate. In the **Description** field, enter a description.
    3. In the **Certificates** section, select **Add** to add a certificate to the chain.
    4. Use the **Up** or **Down** button to change the position of the certificate in the chain.
    5. Select **Save**, and then close the page.
    6. Close the page.
9. On **Service environment** page, on the Action Pane, select **Publish** to publish the environment to the cloud. The value of the **Status** field is changed to **Published**.

## Create a connected application

1. On the **Environment setups** page, on the action Pane, select **Connected applications**.
2. Select **New** to create a connected application.
3. In the **Name** field, enter the name of the application to connect.
4. In the **Application** field, enter the URL of the Finance and Supply Chain Management environment to connect.
4. In the **Tenant** field, enter the tenant of the Finance and Supply Chain Management environment.
5. Select **Save**.
6. On the Action Pane, select **Check connection** to test the connection with the environment. Then close the page.

## Link connected applications to environments

1. On the **Environment setups** page, select **New** to assign a connected application to an environment.
2. In the **Connected application** field, select a connected application.
3. In the **Service environment** field, select a service environment.
4. Select **Save**, and then close the page.

## Set up the Electronic invoicing add-in integration in Finance and Supply Chain Management

### Turn on the Electronic invoicing add-in integration feature

1. Sign in to your Finance or Supply Chain Management instance.
2. In the **Feature management** workspace, search for the **Electronic invoicing add-in integration** feature. If this feature doesn't appear on the page, select **Check for updates**.
3. Select the feature, and then select **Enable now**.

### Set up the service endpoint URL

1. Go to **Organization administration \> Setup \> Electronic document parameters**.
2. On the **Submission service** tab, in the **Service endpoint URL** field, enter the appropriate service endpoint for your Azure geography, as shown in the following table.

    | Datacenter Azure geography | Service endpoint URL                                                       |
    |----------------------------|----------------------------------------------------------------------------|
    | East US                    | `https://electronicinvoicing.eus-il301.gateway.prod.island.powerapps.com/` |
    | West US                    | `https://electronicinvoicing.wus-il301.gateway.prod.island.powerapps.com/` |
    | North EU                   | `https://electronicinvoicing.neu-il301.gateway.prod.island.powerapps.com/` |
    | West EU                    | `https://electronicinvoicing.weu-il301.gateway.prod.island.powerapps.com/` |

3. In the **Environment** field, enter the name of the Electronic invoicing add-in environment.
4. Select **Save**, and then close the page.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
