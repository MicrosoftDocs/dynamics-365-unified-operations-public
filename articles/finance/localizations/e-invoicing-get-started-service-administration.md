---
# required metadata

title: Get started with the Electronic invoicing add-on service administration
description: This topic explains how to get stared with the electronic invoicing add-on. 
author: gionoder
manager: AnnBe
ms.date: 01/22/2021
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
# ms.tgt_pltfrm: 
ms.custom: 97423
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: janeaug
ms.search.validFrom: 2020-07-08
ms.dyn365.ops.version: AX 10.0.12

---

# Get started with the Electronic invoicing add-on service administration

[!include [banner](../includes/banner.md)]

## Prerequisites

Before you complete the steps in this topic, you must have the following prerequisites in place:

   - Access to your LCS account.
   - An LCS project that includes Dynamics 365 Finance and Dynamics 365 Supply Chain Management:
    
        - Version 10.0.13 or later
        - Deployed in one of those Azure geographies:
             - East US
             - West US
             - North EU
             - West EU

   - Access to your RCS account
   - Activate the Globalization feature for your RCS account through the Feature management module. For more information, see [Regulatory Configuration Services (RCS) - Globalization features](rcs-globalization-feature.md).
   - Create a key vault resource and a storage account in Azure. For more information, see [Create Azure Storage Account and Key Vault](e-invoicing-create-azure-storage-account-key-vault.md).

## Install the add-on for microservices in Lifecycle Services 

1. Sign in to your Lifecycle Services (LCS) account.
2. Select the **Preview feature management** tile and in the **Public Preview Features** field group, select **e-Invoicing service.**
3. Make sure the toggle **Preview feature enabled** is set to **Yes**.

## Set up the RCS integration parameters with Electronic invoicing add-on 

1. Sign in to your RCS account.
2. In the **Electronic reporting** workspace, in the **Related links** section, select the **Electronic reporting parameters** link.
3. On the **e-Invoicing service** tab, in the **Service endpoint URI** field, type the service end point according to your Azure geography as shown in the table below:

|  Datacenter Azure geography      | Service endpoint URI                                                       |
|----------------------------------|----------------------------------------------------------------------------|
| East US                          | `https://electronicinvoicing.eus-il301.gateway.prod.island.powerapps.com/` |
| West US                          | `https://electronicinvoicing.wus-il301.gateway.prod.island.powerapps.com/` |
| North EU                         | `https://electronicinvoicing.neu-il301.gateway.prod.island.powerapps.com/` |
| West EU                          | `https://electronicinvoicing.weu-il301.gateway.prod.island.powerapps.com/ `|

4. In the **Application Id** field, verify that it shows the ID **0cdb527f-a8d1-4bf8-9436-b352c68682b2**. This value is a fixed value.
5. In the **LCS Environment Id** field, type the ID of your LCS subscription account.
6. Select **Save** and then close the page.


## Create an Electronic invoicing add-on environment

1. Sign in to your RCS account.
2. In the **Globalization feature** workspace, in the **Environment** section, select the **e-Invoicing** tile.

## Create a service environment

1. On the Action Pane select **Service environment** and then select **Key Vault parameters**.
2. Select **New** to create a new key vault secret.
3. In the **Name** field, type the name of the key vault secret and in the **Description** field, enter the description.
4. In the **Key Vault URI** field, paste the secret from Azure Keyvault.
5. In the **Certificates** section, enter all the digital certificate names and key vault secrets that are needed to establish trustable connections. Select **Add** to add a new certificate or secret.
6. In the **Name** field, type the name of the certificate or secret and in the **Description** field, type the description.
7. In the **Type** field, select if it is a certificate or a secret. Both sets of values are configured on the key vault resource in Azure.
8. If your country/region-specific invoices require a chain of certificates to apply digital signatures, on the Action Pane, select **Chain of certificates**.

    1. Select **New** to create a chain of certificates.
    2. In the **Name** field, enter the name of the chain of certificate and in the **Description** field, type the description.
    3. In the **Certificates** section, select **Add** to add a new certificate to the chain.
    4. Use **Up** or **Down** to move the position of the certificate in the chain. 
    5. Select **Save** and then close the page.

9. Close the page and then select **New** to create a new e-Invoicing environment.
10. In the **Name** field, type the name of the e-Invoicing environment and in the **Description** field, type the description.
11. In the **Storage SAS token secret**, select the certificate that must be use to authenticate the access to the storage account.
12. In the **Users** section, select **Add** to the allow a user to submit electronic invoices through this environment.
13. In the **User ID** field, enter the alias of the user and in the **Email** field, enter the user's e-mail.
14. Select **Save**, and on the Action Pane, select **Publish** to publish the environment to the cloud. The **Status** field is changed to **Published**.


## Create a connected application

1. On the Action Pane, select **Connected applications**.
2. Select **New** to create a new connected application and in the **Name** field, type the name of the application to connect.
3. In the **Application** field, enter the URL of the Finance and Supply Chain Management environment to connect.
4. In the **Tenant** field, type the Tenant of the Finance and Supply Chain Management environment.
5. Select **Save**.
6. On the Action Pane, select **Check connection** to test the connection with the environment and then close the page. 

## Link connected applications to environments

1. Select **New** to assign a connected application to an environment.
2. In the **Connected application** field, select a connected application and in the **Service environment** field, select a Service environment.
3. Select **Save** and then close the page.

## Set up the Electronic invoicing add-on integration in Finance and Supply Chain Management

### Turn on the Electronic invoicing add-on integration feature

1. Sign in to your Finance or Supply Chain Management instance.
2. In the **Feature management** workspace, search for the feature, **Electronic invoicing add-on integration**. If the feature isn't shown on the **Feature management** page, select **Check for updates**.
3. Locate and select the feature, and then select **Enable now**.

### Set up the service endpoint URL

1. Go to **Organization administration** > **Setup** **Electronic document parameters**.
2. On the **Submission service** tab, in the **Service endpoint URL** field, type the service end point according to your Azure geography as shown in the table below:

|  Datacenter Azure geography      | Service endpoint URL                                                       |
|----------------------------------|----------------------------------------------------------------------------|
| East US                          | `https://electronicinvoicing.eus-il301.gateway.prod.island.powerapps.com/` |
| West US                          | `https://electronicinvoicing.wus-il301.gateway.prod.island.powerapps.com/` |
| North EU                         | `https://electronicinvoicing.neu-il301.gateway.prod.island.powerapps.com/` |
| West EU                          | `https://electronicinvoicing.weu-il301.gateway.prod.island.powerapps.com/ `|

3. In the **Environment** field, type the name of the Electronic invoicing add-on Environment.
4. Select **Save** and then close the page.

