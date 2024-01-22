---
title: How to set up ClientId and ClientSecret
description: This article explains how to set up ClientId and ClientSecret for the universal tax rate API.
author: Kai-Cloud
ms.date: 01/20/2024
ms.topic: overview
ms.custom: 
  - bap-template
ms.prod: 
ms.technology: 
audience: Application user
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: hailxu
ms.search.validFrom: 2024-02-01
ms.dyn365.ops.version: 10.0.39
ms.search.form: 
uid: D365.CFO.FunctionalTraining.Finance.Tax.TaxCalculationService.TaxCalculationConnector.Desgin.SetupClientIdClientSecreteGTEPlus
---

# Set up Client ID and Client Secret

[!INCLUDE[banner](../../includes/banner.md)]

This article explains how to set up ClientId and ClientSecret for the universal tax rate API.

## Prerequisites

Before you can access a tax provider's service, you must set up your ClientId and ClientSecret for the Universal tax rate API. Your tax provider supplies you with the Client ID and Client Secret. When you recieve them, store them in an Azure key vault and configure the key vault parameters for Dynamics 365 finance and operations apps. After these are set up in the key vault, you can select the corresponding key vault secrets name in the tax feature setup.

:::image type="content" source="../media/CustomerISVFeatureCredential-GTEPlus.png.png" alt-text="Screenshot of the General setting section with the Credential section highlighted."::: 

## Create an Azure key vault in the Azure portal

All of the secrets and certificates used in the Tax Calculation service must be stored in a Microsoft Azure key vault. This approach helps ensure that you don't work directly with the secrets, and that the secrets are securely stored. When you must use digital signing or secure a connection to external web services, set the reference to the Key Vault secrets instead of using the secrets and certificates directly. For more information, see [About Azure Key Vault](/azure/key-vault/general/overview).

### Create a Key vault

To create a Key vault, follow these steps.

1. From the [Azure portal](https://ms.portal.azure.com/) menu, or from the **Home** page, select **Create a resource**.
2. In the Search box, enter **Key vault**.
3. From the results list, choose **Key vault**.
4. On the Key Vault section, choose **Create**.
5. On the **Create key vault** section provide the following information:
    - **Subscription**: Choose a subscription.
    - **Resource group**: Choose a Resource group or Create new.
    - **Name**: A unique name is required. E.g., we use **TaxProvider-vault**.
    - In the **Location** pull-down menu, choose a location.
    - Leave the other options to their defaults.
      
    > [!NOTE]
    > The **Name** above will be referred in the section [Setup Key Vault parameters in Dynamics 365 finance and operations apps](#setup-key-vault-parameters-in-dynamics-365-finance-and-operations-apps) as **\<KeyVaultName\>**.
    
6. Select next and set the **Permission model** to **Vault access policy**.
7. Select **Review + Create**.
8. After the deployment completes, expand the **Deployment details** section and select the **Key vault** detail.

   :::image type="content" source="../media/items.png" alt-text="Screenshot of the TaxProvider-vault Overview page with the Deployment details expanded and the key vault highlighted.":::

   > [!NOTE]
   > Copy and save the **Vault URI**, you need it when you complete the [Setup Key Vault parameters in Dynamics 365 finance and operations apps](#setup-key-vault-parameters-in-dynamics-365-finance-and-operations-apps) section for the **\<Key Vault URI\>** value.
    
   :::image type="content" source="../media/items1.png" alt-text="creenshot of the TaxProvider-vault Secrets page with the Secrets object and Generate/Import highlighted.":::

10. Select next and set the **Permission model** to **Vault access policy**.
11. Select **Secrets**, and then select **Generate/Import**. Next, complete the following fields.
    - **Upload options**: **Manual**.
    - **Name**: A name for the seceret. For example, **ClientID**.
    - **Secret value**: Enter the Client ID that you get from the Tax provider.
12. Select **Create**.

    > [!NOTE]
    > The **Secret Name** is a mandatory parameter for integration with the key vault, therefore it should be specified in the application. It is referred in [Setup Key Vault parameters in Dynamics 365 finance and operations apps](#setup-key-vault-parameters-in-dynamics-365-finance-and-operations-apps) as **SecretName** parameter.
    
    :::image type="content" source="../media/items2.png" alt-text="Screenshot of the TaxProvider-vault Secrets page with the ClientSecret and ClientID highlighted.":::

13. Repeate step 10 for Client secret.

    :::image type="content" source="../media/items3.png" alt-text="Screenshot of the TaxProvider-vault Secrets page with the Deployment details expanded and the key vault highlighted.":::

### Setup Permissions

This section explains how to complete the following procedures.

- Create App registration
- Set Access policy of the Key Vault
- Setup Key Vault parameters in Dynamics 365 finance and operations apps

#### Create App registration

To access Azure key vault you need to create App registration in Azure Active Directory. To create an App registration, follow these steps.

1. In Azure Active Directory search for **register**, and then select **App registrations**.
   
   :::image type="content" source="../media/items5.png" alt-text="Screenshot of the App registrations page with add New registation highlighted.":::

2. Set the **Name** and **Supported account types**, and then select **Register**
3. Copy and save the **Application (Client) ID**. It should be specified in the application, and referred in [Setup Key Vault parameters in Dynamics 365 finance and operations apps](#setup-key-vault-parameters-in-dynamics-365-finance-and-operations-apps) as the **\<Key Vault client\>** parameter.

   :::image type="content" source="../media/items6.png" alt-text="Screenshot of the TaxProviderKeyVaultAccess page with the Application (client) ID highlighted.":::

4. Create a new **Client secret**.
   > [!NOTE]
   > The **Client secret** is a mandatory parameter for integration with the key vault. It should be copied and then specified in the application. It is referred in [Setup key vault parameters in Dynamics 365 finance and operations apps](#setup-key-vault-parameters-in-dynamics-365-finance-and-operations-apps) as **\<Key vault secret key\>** parameter.

   :::image type="content" source="../media/items7.png" alt-text="Screenshot of the Certificates & secrets page with add New client secret highlighted.":::

#### Set the Access policy of the Key vault

You must set up the access policy to grant the App registration above the correct level of secure access to the secret that you created.

1. Open the Key vault storage that you created above.
2. Go to **Settings** \> **Access policies**, and select **Create**.
3. In the **Secret permissions**, select the **Get** and **List** operations.
   
   :::image type="content" source="../media/items8.png" alt-text="Screenshot of the Creat an access policy page with Secret permissions highlighted.":::

4. Select **Next**, in the **Select principal**, select the App registration that you created above.
   
   :::image type="content" source="../media/items9.png" alt-text="Screenshot of the Principal tab on the Create and access policy page.":::

5. Select **Next** till to "Review + create" and the select **Create**.

## Setup Key vault parameters in Dynamics 365 finance and operations apps

After finishing the prerequisite steps, you setup the key vault parameters to link to the azure key vault in Dynamics 365 finance and operations apps.

1. Go to **System administration** \> **Setup** \> **Key vault parameters**.
2. Select **New** to create a new instance.
3. Enter a name and description, and then, on the **General** FastTab, set the fields that are required for the integration with Key vault storage:
   - **Key vault URL** – The vault URI that was saved in the section [Create a Key vault](#create-a-key-vault).
   - **KeyvVault client** – Enter the interactive client ID of the Microsoft Entra ID application that is associated with the Key vault storage for authentication.
   - **Key vault secret key** – Enter the secret key that is associated with the Entra ID application that is used for authentication with the Key vault storage.
4. On the **Secrets** FastTab, select **Add** to add your secret. For each secret, set the following fields:
    - **Name**
    - **Description**
    - **Secret** – Enter a secret reference to the key vault secret.

    The format of a secret must resemble the following example:
    **vault://<KeyVaultName*>/<SecretName*>/<SecretVersion*>**

    Attributes that are marked with an asterisk (*) are **optional**. However, the **\<SecretName>** attribute is required. In most cases, you can define a Key Vault secret key in the following format:
    **vault:///\<SecretName>**

    If the secret version isn't defined in the Key vault secret key, the system retrieves the active secret that has the latest expiration date.
    ![Key vault parameters](../media/items10.png)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
