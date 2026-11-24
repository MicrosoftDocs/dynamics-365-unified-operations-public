---
title: Enable Inventory Visibility for Commerce
description: This article describes how to set up Inventory Visibility for Microsoft Dynamics 365 Commerce Scale Units (CSUs).
author: yufei-huang
ms.author: yufeihuang
ms.reviewer: kamaybac
ms.search.form: InventInventoryDataService, KeyVaultParameters
ms.topic: how-to
ms.date: 10/27/2026
ms.custom: 
  - bap-template
---

# Enable Inventory Visibility for Commerce

[!INCLUDE [banner](../includes/banner.md)]

This article describes how to set up Inventory Visibility for Microsoft Dynamics 365 Commerce Scale Units (CSUs) so that e-commerce, point of sale (POS), or other applications on CSUs can use it for real-time inventory lookup, reservation, and adjustments.

## Inventory Visibility for Commerce

Accurate inventory information is crucial for any retailer that runs an omnichannel business. Discrepancies between system-recorded inventory and physical inventory can lead to lost revenue or reduced customer satisfaction. Retailers require an accurate, holistic view of inventory across all channels and locations, and throughout all sales and supply chain processes. They must be able to query, reserve, and adjust on-hand inventory in near-real time.

Dynamics 365 Commerce works asynchronously with inventory data. It relies on scheduled back-end jobs to exchange data between Commerce headquarters and CSU components. Because the inventory data that's available to headquarters at any given time might not reflect the latest inventory snapshot, it can't reliably support omnichannel scenarios.

If your company runs any or all of the following scenarios, we recommend that you enable Inventory Visibility so that Commerce can provide real-time inventory data across all channels:

- You're running both Dynamics 365 Commerce and Dynamics 365 Supply Chain Management.
- Your POS or e-commerce business runs on multiple CSUs.
- You have third-party systems that also update inventory.

The Inventory Visibility add-in (also referred to as the *Inventory Visibility service*) is an independent and highly scalable microservice for posting on-hand inventory changes and tracking inventory across data sources in real time. It provides a set of RESTful APIs and includes native support for integrating with Commerce directly out of the box. Whenever a Commerce channel requests real-time inventory data, Inventory Visibility provides it in real time. Whenever an event that changes inventory occurs in the system (such as order creation, editing, cancellation, return, or fulfillment), the event is immediately posted to Inventory Visibility to update its inventory snapshot.

The following illustration shows a system that implements most of the previously mentioned integration scenarios (but just a single CSU).

:::image type="content" source="media/commerce-ivs-integration.svg" alt-text="Block diagram of an integrated system." lightbox="media/commerce-ivs-integration.svg":::

For more information about Inventory Visibility, see [Inventory Visibility Add-in overview](inventory-visibility.md).

## Prerequisites

Before you can use the features that this article describes, ensure your system meets the following requirements:

- You have licenses for both Supply Chain Management and Commerce.
- You're running Dynamics 365 Commerce version 10.0.36 or later.
- The Inventory Visibility add-in is installed and set up as described in [Install and set up Inventory Visibility](inventory-visibility-setup.md).
- The following features are turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md):

    - *Inventory Visibility integration with inventory adjustment posting* (As of Dynamics 365 Commerce version 10.0.45, this feature is mandatory and can't be turned off.)
    - *Inventory Visibility integration with inventory adjustment offset* (As of Dynamics 365 Commerce version 10.0.45, this feature is mandatory and can't be turned off.)
    - *Enable warehouse items in Inventory Visibility* (As of Dynamics 365 Commerce version 10.0.45, this feature is turned on by default. As of version 10.0.49, it's mandatory and can't be turned off.)

- The following feature is optional but recommended. It lets you turn on Inventory Visibility integration by using the Commerce Scale Unit managed identity without providing the Microsoft Entra application ID, secret, or tenant ID. This feature requires Dynamics 365 Commerce version 10.0.50, Commerce Scale Units version 10.0.50, and that the Inventory Visibility service is fully deployed to all regions. The feature is turned on by default, but you can turn it off in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) if you need to use the client secret setup path instead. Learn more in [Set up the integration by using CSU managed identity](#managed-identity).

    - *Inventory Visibility integration with Commerce Scale unit managed identity*

- [Inventory Visibility support for WMS items](inventory-visibility-whs-support.md) is enabled for your environment.

<a name="setup-path"></a>

## Choose a setup path

How Commerce Scale Units authenticate to Inventory Visibility depends on whether the *Inventory Visibility integration with Commerce Scale unit managed identity* feature is available and turned on for your system.

| Your environment | Setup path to use |
|---|---|
| You meet the [prerequisites](#prerequisites) for the *Inventory Visibility integration with Commerce Scale unit managed identity* feature and the feature is turned on | [Managed identity (recommended)](#managed-identity). The CSU uses its managed identity to authenticate to Inventory Visibility. You don't have to create a key vault, register a Microsoft Entra application, or enter credentials in Commerce shared parameters. |
| You don't meet the [prerequisites](#prerequisites) for the *Inventory Visibility integration with Commerce Scale unit managed identity* feature or the feature is turned off | [Client secret](#client-secret). The CSU authenticates by using a Microsoft Entra application ID and a client secret that's stored in Azure Key Vault. |

> [!NOTE]
> The managed identity setup path changes only how Commerce Scale Units authenticate to Inventory Visibility. It doesn't change the requirements for installing Inventory Visibility or the authentication requirements of other Inventory Visibility integrations.

Regardless of the setup path that you choose, complete the following procedures:

1. [Enable adjustments in Commerce](#enable-adjustments).
1. Set up the integration by using either the [managed identity](#managed-identity) or the [client secret](#client-secret) setup path.
1. [Run the global configuration job](#global-configuration).

<a name="enable-adjustments"></a>

## Enable adjustments in Commerce

To enable adjustments in Commerce, follow these steps:

1. Sign in to Commerce.
1. Go to **Inventory Management** > **Inventory Visibility** > **Inventory Visibility integration**.
1. On the **Adjustment** tab, on the **Manage inventory adjustment posting and retry** FastTab, on the toolbar, select **Enable adjustment**.

<a name="managed-identity"></a>

## Set up the integration by using CSU managed identity (version 10.0.50 and later)

Use this setup path if your system meets the [prerequisites](#prerequisites) for the *Inventory Visibility integration with Commerce Scale unit managed identity* feature and the feature is turned on. To use this setup path to set up the integration between Inventory Visibility and Commerce, follow these steps:

1. Sign in to Commerce.
1. Go to **Retail and Commerce** > **Headquarters setup** > **Parameters** > **Commerce shared parameters**.
1. On the **Inventory** tab, set the **Use Inventory Visibility as inventory data provider** option to *Yes*.
1. On the Action Pane, select **Save**.

> [!NOTE]
> In Commerce version 10.0.50, the **Microsoft Entra tenant ID**, **Microsoft Entra app ID**, and **Microsoft Entra client secret** fields still appear on the **Inventory** tab, but you don't have to set them when you use the managed identity setup path. As of version 10.0.51, these credential fields are hidden while the *Inventory Visibility integration with Commerce Scale unit managed identity* feature is turned on. If you turn off the feature, the fields are shown again. Any credentials that you previously entered are kept, and the **Use Inventory Visibility as inventory data provider** option isn't affected.

When you use this setup path, you don't have to complete any of the procedures in the [Set up the integration by using a client secret](#client-secret) section. Continue with [Run the global configuration job](#global-configuration).

<a name="client-secret"></a>

## Set up the integration by using a client secret (version 10.0.49 and earlier)

Use this setup path if your system doesn't meet the [prerequisites](#prerequisites) for the *Inventory Visibility integration with Commerce Scale unit managed identity* feature or the feature is turned off. If you're using the [managed identity](#managed-identity) setup path, skip this section.

For this setup path, make a note of the following information from the Inventory Visibility add-in installation, because you need it in the following procedures:

- Application ID (Client ID)
- Client secret
- Tenant ID

<a name="key-vault"></a>

### Create a key vault to hold the client secret for Inventory Visibility

To create a key vault to hold the client secret for Inventory Visibility, follow these steps:

1. Sign in to the [Azure portal](https://portal.azure.com/).
1. Search for or select **Key vaults** to open the **Key vaults** page.
1. On the toolbar, select **Create**.
1. Work through the **Create key vault** wizard to create a key vault.
1. Open the key vault that you just created.
1. On the navigation pane, select **Overview**.
1. Copy the **Vault URI** value, and paste it into a temporary text file. Label the value so that you can identify it later.
1. While your key vault is still open, on the navigation pane, select **Object** > **Secrets**.
1. On the toolbar, select **Generate/Import**.
1. On the **Create a secret** page, set the following fields:

    - **Upload options** – Select *Manual*.
    - **Name** – Enter a name for the secret (for example, *commerce-iv-01-secret*). Copy the value, paste it into your temporary text file, and label it.
    - **Secret value** – Enter the client secret value that you used when you installed the Inventory Visibility add-in (as mentioned in the [Set up the integration by using a client secret](#client-secret) section).
    - **Content type** – This field is optional. The suggested value is *application/vnd.ms-StorageConnectionString*.
    - **Set activation date** – Select this checkbox, and then enter the first date when this secret should be valid.
    - **Set expiration date** – Select this checkbox, and then enter the last date when this secret should be valid.
    - **Enabled** – Set this option to *Yes*.

    > [!IMPORTANT]
    > If the client secret value that you used when you installed the Inventory Visibility add-in expires, then the **Secret value** in this step also becomes invalid. If this happens, then you  must create a new client secret value for the Inventory Visibility application registration and update the **Secret value** mentioned in this step accordingly.

1. Select **Create** to create and save the secret.

<a name="app-registration"></a>

### Register a Microsoft Entra application to provide access to the key vault

A Microsoft Entra application enables Supply Chain Management and Commerce to access the key vault. To register a Microsoft Entra application, follow these steps:

1. In the [Azure portal](https://portal.azure.com/), return to the home page.
1. Search for or select **App registrations** to open the **App registrations** page.
1. On the toolbar, select **New registration**.
1. On the **Register an application** page, set the following fields:

    - **Name** – Enter a name.
    - **Supported account types** – Specify who can use the new application. For more information about this setting, see [Identity and account types for single- and multitenant apps](/security/zero-trust/develop/identity-supported-account-types).
    - **Redirect URI** – Leave this field blank.

1. Select **Register** to register the application.
1. The new app registration opens. On the navigation pane, select **Manage** > **Certificates & secrets**.
1. On the **Client secrets** tab, select **New client secret**.
1. In the **Add a client secret** dialog box, select an expiration date that meets your needs, and then select **Add**.
1. The **Certificates & secrets** page now shows details about the new client secret. These details show only once and are hidden when the page reloads. Therefore, you must copy them now. Copy the **Value** value, paste it into your temporary text file, and label it.
1. On the navigation pane, select **Overview**. Copy the following values, paste them into your temporary text file, and label them:

    - **Application (client) ID**
    - **Directory (tenant) ID**

After the application is registered, create an access policy to enable it to access the key vault.

1. Open the key vault you created in [Create a key vault to hold the client secret for Inventory Visibility](#key-vault).
1. On the navigation pane, select **Access policies**.
1. On the toolbar, select **Create** to open the **Create an access policy** page.
1. On the **Permissions** tab, under **Secret permissions** > **Secret Management Operations**, select the **Get** checkbox. You don't need a template.
1. Select **Next**.
1. On the **Principal** tab, select the application you registered in this section.
1. Select **Next**.
1. The **Application** tab is optional.
1. Select **Next**.
1. On the **Review + create** tab, review your settings and then select **Create**.

<a name="scm-vault-setup"></a>

### Set up Commerce to access the new key vault

To set up Commerce to access the new key vault through the new application, follow these steps:

1. Sign in to Commerce.
1. Use the company picker to select the same company (legal entity ID) as your Dynamics 365 Commerce channel.
1. Go to **System administration** > **Setup** > **Key Vault parameters**.
1. On the Action Pane, select **New** to add a record. Set the following fields for it:

    - **Name** – Enter a name for the Key Vault record.
    - **Description** – Enter a short description.
    - **Key Vault URL** – Paste the **Vault URI** value that you copied when you created the key vault. (See step 7 in the [Create a key vault to hold the client secret for Inventory Visibility](#key-vault) section.)
    - **Key Vault client** – Enter the **Application (client) ID** value that you copied when you created the app registration. (See step 10 in the [Register a Microsoft Entra application to provide access to the key vault](#app-registration) section.)
    - **Key Vault secret key** – Enter the secret **Value** value that you copied when you created the app registration. (See step 9 in the [Register a Microsoft Entra application to provide access to the key vault](#app-registration) section.)

1. On the **Secrets** FastTab, on the toolbar, select **Add** to add a row to the grid. Set the following fields for it:

    - **Name** – Enter a name to identify the secret. You need this value later. Therefore, copy it, paste it into your temporary text file, and label it.
    - **Description** – Enter a short description.
    - **Secret** – Enter a value using the following format:

        *vault://\<KeyVaultName\>/\<SecretName\>/\<SecretVersion\>*

        The *\<KeyVaultName\>* and *\<SecretVersion\>* attributes are optional. However, the *\<SecretName\>* attribute is required, and is the **Name** value that you copied when you created the secret for the key vault (see step 10 in the [Create a key vault to hold the client secret for Inventory Visibility](#key-vault) section). If the secret version isn't defined in the Key Vault secret key, the system retrieves the active secret that has the latest expiration date. In most cases, you can define a Key Vault secret key in the following format:

        *vault:///\<SecretName\>*

        For example, if the name of your key vault secret is *commerce-iv-01-secret*, enter *vault:///commerce-iv-01-secret*.

    - **Secret type** – Select *Manual*.

    After filling in all the necessary fields, select **Validate** to verify your secret.

1. On the **Secrets** FastTab, on the toolbar, select **Validate**. If you correctly entered all the values, you receive the following informational message: "Validation successful." If you receive an error message, double-check your settings, and try again.
1. On the Action Pane, select **Save**. The save operation takes about two minutes.

For more information about the settings that are mentioned in this procedure, see [Set up the Azure Key Vault client](../../finance/localizations/global/setting-up-azure-key-vault-client.md).

### Configure Commerce shared parameters

To set up the integration between Inventory Visibility and Commerce by using a client secret, follow these steps:

1. Sign in to Commerce.
1. Go to **Retail and Commerce** > **Headquarters setup** > **Parameters** > **Commerce shared parameters**.
1. On the **Inventory** tab, set the following fields:

    - **Microsoft Entra tenant ID** – Enter the **Directory (tenant) ID** value that you used when you installed the Inventory Visibility add-in (as mentioned in the [Set up the integration by using a client secret](#client-secret) section).
    - **Microsoft Entra app ID** – Enter the **Application (client) ID** value that you used when you installed the Inventory Visibility add-in (as mentioned in the [Set up the integration by using a client secret](#client-secret) section).
    - **Microsoft Entra client secret** – Select the **Name** value that you copied when you specified the secret for the key vault on the **Key Vault parameters** page in Commerce. (See step 5 in the [Set up Commerce to access the new key vault](#scm-vault-setup) section.)
    - **Use Inventory Visibility as inventory data provider** – Set this option to *Yes*.

1. On the Action Pane, select **Save**.

<a name="global-configuration"></a>

## Run the global configuration job

To synchronize the configuration to your channels, run the global configuration job by following these steps:

1. Go to **Retail and Commerce** > **Retail and Commerce IT** > **Distribution schedule**.
1. In the list pane, select the record that's named *1110 Global configuration*.
1. On the Action Pane, select **Run now**.
