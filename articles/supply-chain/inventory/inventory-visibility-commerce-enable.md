---
title: Enable Inventory Visibility for Commerce
description: This article describes how to set up Inventory Visibility for Dynamics 365 Commerce Scale Units (CSUs) so that e-commerce, POS, or other applications on CSUs can use inventory visibility for real-time inventory lookup, reservation, and adjustments.
author: yufeihuang
ms.author: yufeihuang
ms.reviewer: kamaybac
ms.search.form: InventInventoryDataService, KeyVaultParameters
ms.topic: how-to
ms.date: 06/21/2024
audience: Application User
ms.custom: 
  - bap-template
---

# Enable Inventory Visibility for Commerce

This article describes how to set up Inventory Visibility for Dynamics 365 Commerce Scale Units (CSUs) so that e-commerce, POS, or other applications on CSUs can use inventory visibility for real-time inventory lookup, reservation, and adjustments.

## Inventory Visibility for Commerce

Accurate inventory information is crucial for any retailer running an omnichannel business. Discrepancies between system recorded inventory and physical inventory can result in lost revenue or reduced customer satisfaction. Retailers require an accurate, holistic view of inventory across all channels and locations, and throughout all sales and supply-chain processes. They need the ability to query, reserve, and adjust on-hand inventory in near real-time.  

Dynamics 365 Commerce works asynchronously with inventory data. It relies on scheduled backend jobs to exchange data between headquarters and CSU components. At any given time, inventory data available to headquarters might not reflect the latest inventory snapshot, which makes it unreliable to support omnichannel scenarios. We recommend enabling Inventory Visibility for Commerce to provide real-time inventory data across all channels if your company runs any or all of the following scenarios:

- You're running both Dynamics 365 Commerce and Dynamics 365 Supply Chain Management.
- Your point-of-sale or e-commerce business runs on multiple CSUs.
- You have third-party systems that also update inventory.

The Inventory Visibility Add-in (also referred to as the *Inventory Visibility service*) for Dynamics 365 Supply Chain Management is an independent and highly scalable micro-service for posting on-hand inventory changes and tracking inventory across data sources in real time. It provides a set of RESTful APIs and includes native support for integrating with Dynamics 365 Commerce right out of the box. Whenever a Commerce channel requests real-time inventory data, Inventory Visibility provides it in real-time. Whenever an event occurs in the system that changes inventory (such as order creation, editing, cancellation, return, or fulfill), the event is immediately posted to Inventory Visibility to update its inventory snapshot.

The following illustration shows a system that implements most of the mentioned integration scenarios (but just a single CSU).

:::image type="content" source="media/commerce-ivs-integration.svg" alt-text="Block diagram of an integrated system." lightbox="media/commerce-ivs-integration.svg":::

For more information about Inventory Visibility, see [Inventory Visibility Add-in overview](inventory-visibility.md).

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must have licenses for both Dynamics 365 Supply Chain Management and Dynamics 365 Commerce.
- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.36 or later.
- The Inventory Visibility add-in must be installed and set up as described in [Install and set up Inventory Visibility](inventory-visibility-setup.md). Be sure to take note of the following information from the setup because you'll need it when setting up the integration with Dynamics 365 Commerce:
    - Application ID (Client ID)
    - Client secret
    - Tenant ID
- The following features must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
    - *Inventory Visibility integration with inventory adjustment posting*
    - *Inventory Visibility integration with inventory adjustment offset*
    - *Enable warehouse items in Inventory Visibility*
- [Inventory Visibility support for WMS items](inventory-visibility-whs-support.md) must be enabled for your environment.

## Enable adjustments in Supply Chain Management

Enable adjustments in Supply Chain Management by following these steps:

1. Sign in to Supply Chain Management.
1. Go to **Inventory Management** \> **Inventory Visibility** \> **Inventory Visibility integration**.
1. Open the **Adjustment** tab. On the **Manage inventory adjustment posting and retry** FastTab toolbar, select **Enable adjustment**.

## <a name="key-vault"></a>Create a key vault to hold the client secret for Inventory Visibility

Create a key vault to hold the client secret for Inventory Visibility by following these steps:

1. Sign in to [Microsoft Azure portal](https://portal.azure.com/).
1. Search for or select **Key vaults** and open the **Key vaults** page.
1. Select **Create** from the toolbar.
1. Work through the **Create key vault** wizard to create a new key vault.
1. Open the key vault you just created. On the navigation pane, select **Overview**. Then copy the value shown for **Vault URI** and paste it into a temporary text file (and label the value so you can identify it later).
1. With your key vault still open, on the navigation pane, select **Object** > **Secrets**.
1. From the toolbar, select **Generate/Import** to open the **Create a secret** page. Make the following settings here:
    - **Upload options** – Select *Manual*.
    - **Name** – Enter a name for the secret (for example, *commerce-iv-01-secret*). Copy and label this value in your temporary text file
    - **Secret value** – Enter the client secret value that you used when installing the Inventory Visibility add-in (as mentioned in the [prerequisites](#prerequisites)).
    - **Content type** – Enter *application/vnd.ms-StorageConnectionString*.
    - **Set activation date** – Select this checkbox and then enter the first date on which this secret should be valid.
    - **Set expiration date** – Select this checkbox and then enter the last date on which this secret should be valid.
    - **Enabled** – Set to *Yes*.

1. Select **Create** to create and save the secret.

## <a name="app-registration"></a>Register a Microsoft Entra application to provide access to the key vault

Register a Microsoft Entra application to enable Supply Chain Management and Commerce to access the key vault by following these steps:

1. Go back to the home page of [Azure portal](https://portal.azure.com/).
1. Search for or select **App registrations** and open the **App registrations** page.
1. On the toolbar, select **New registration**.
1. On the **Register an application** page, set the following fields:
    - **Name** – Enter a name.
    - **Supported account types** – Specify who can use the new application. For more information about this setting, see [Identity and account types for single- and multitenant apps](/security/zero-trust/develop/identity-supported-account-types).
    - **Redirect URI** – Leave this field blank.

1. Select **Register** to register the application.
1. The new app registration opens. From the navigation pane, select **Manage** \> **Certificates & secrets**.
1. Open the **Client secrets** tab and select **New client secret**.
1. In the **Add a client secret** dialog box, select an expiration date that meets your needs, and then select **Add**.
1. The **Certificates & secrets** page now shows details about the new client secret. These details are shown only once and will be hidden when the page is reloaded. Therefore, you must copy them now. Copy and label the following value in your temporary text file:
    - **Value**

1. On the navigation pane, select **Overview**. Copy and label the following values in your temporary text file:
    - **Application (client) ID**
    - **Directory (tenant) ID**

## <a name="scm-vault-setup"></a>Set up Supply Chain Management to access the new key vault

Set up Supply Chain Management to access the new key vault through the new application by following these steps:

1. Sign in to Supply Chain Management.
1. From the company picker, select the same company (legal entity ID) as your Dynamics 365 Commerce channel.
1. Go to **System administration** \> **Setup** \> **Key Vault parameters**.
1. On the Action Pane, select **New** to add a new record. Fill in the following fields:
    - **Name** – Enter a name for the Key Vault record.
    - **Description** – Enter a short description.
    - **Key Vault URL** – Paste the **Vault URI** value you copied earlier when creating the key vault (see [Create a key vault to hold the client secret for Inventory Visibility](#key-vault), step 5).
    - **Key Vault client** – Enter the **Application (client) ID** value you copied earlier when creating the app registration (see [Register a Microsoft Entra application to provide access to the key vault](#app-registration), step 10).
    - **Key Vault secret key** – Enter the secret **Value** you copied earlier when creating the app registration (see [Register a Microsoft Entra application to provide access to the key vault](#app-registration), step 9).

1. From the **Secrets** FastTab toolbar, select **Add** to add a new row to the grid and make the following settings for it:
    - **Name** – Enter a name to identify the secret. You'll need this value later, so copy and label it in your temporary text file.
    - **Description** – Enter a short description.
    - **Secret** – Enter a value using the form *vault:///\<SecretName\>*, where *\<SecretName\>* is the **Name** value you copied earlier when creating the secret for the key vault (see [Create a key vault to hold the client secret for Inventory Visibility](#key-vault), step 7). For example, if your key vault secret name is *commerce-iv-01-secret*, you should enter *vault:///commerce-iv-01-secret*.
    - **Secret type** – Select *Manual*.
1. From the **Secrets** FastTab toolbar, select **Validate**. If you've entered all the values correctly, you should see an info message that says "Validation successful." If you get an error, double-check your settings and try again.
1. On the Action Pane, select **Save**. Be patient; the save operation takes about two minutes.

For more information about the settings mentioned in this procedure, see [Set up the Azure Key Vault client](../../finance/localizations/global/setting-up-azure-key-vault-client.md).

## Set up the integration between Inventory Visibility and Commerce

Set up the integration between Inventory Visibility and Commerce by following these steps:

1. Sign in to Supply Chain Management.
1. Go to **Retail and Commerce** \> **Headquarters setup** \> **Parameters** \> **Commerce shared parameters**.
1. Open the **Inventory** tab and make the following settings:
    - **Microsoft Entra tenant ID** – Enter the **Directory (tenant) ID** value that you used when installing the Inventory Visibility add-in (as mentioned in the [prerequisites](#prerequisites)).
    - **Microsoft Entra app ID** – Enter the **Application (client) ID** value that you used when installing the Inventory Visibility add-in (as mentioned in the [prerequisites](#prerequisites)).
    - **Microsoft Entra client secret** – Select the name you copied earlier when specifying the secret for the key vault on the **Key Vault parameters** page in Supply Chain Management (see [Set up Supply Chain Management to access the new key vault](#scm-vault-setup), step 5).
    - **Use Inventory Visibility as inventory data provider** – Set to *Yes*.

1. On the Action Pane, select **Save**.

## Run the global configuration job

Run the global configuration job by following these steps:

1. Go to **Retail and Commerce** \> **Retail and Commerce IT** \> **Distribution schedule**.
1. From the list pane, select the record named *1110 Global configuration*.
1. On the Action Pane, select **Run now**.
