---
title: Enable Inventory Visibility for Commerce
description: This article describes how to set up Inventory Visibility for Microsoft Dynamics 365 Commerce Scale Units (CSUs).
author: yufeihuang
ms.author: yufeihuang
ms.reviewer: kamaybac
ms.search.form: InventInventoryDataService, KeyVaultParameters
ms.topic: how-to
ms.date: 06/21/2024
ms.custom: 
  - bap-template
---

# Enable Inventory Visibility for Commerce

This article describes how to set up Inventory Visibility for Microsoft Dynamics 365 Commerce Scale Units (CSUs) so that e-commerce, point of sale (POS), or other applications on CSUs can use it for real-time inventory lookup, reservation, and adjustments.

## Inventory Visibility for Commerce

Accurate inventory information is crucial for any retailer that runs an omnichannel business. Discrepancies between system-recorded inventory and physical inventory can lead to lost revenue or reduced customer satisfaction. Retailers require an accurate, holistic view of inventory across all channels and locations, and throughout all sales and supply chain processes. They must be able to query, reserve, and adjust on-hand inventory in near-real time.

Dynamics 365 Commerce works asynchronously with inventory data. It relies on scheduled back-end jobs to exchange data between Commerce headquarters and CSU components. Because the inventory data that's available to headquarters at any given time might not reflect the latest inventory snapshot, it can't reliably support omnichannel scenarios.

If your company runs any or all of the following scenarios, we recommend that you enable Inventory Visibility so that Commerce can provide real-time inventory data across all channels:

- You're running both Dynamics 365 Commerce and Dynamics 365 Supply Chain Management.
- Your POS or e-commerce business runs on multiple CSUs.
- You have third-party systems that also update inventory.

The Inventory Visibility add-in (also referred to as the *Inventory Visibility service*) for Supply Chain Management is an independent and highly scalable microservice for posting on-hand inventory changes and tracking inventory across data sources in real time. It provides a set of RESTful APIs and includes native support for integrating with Commerce directly out of the box. Whenever a Commerce channel requests real-time inventory data, Inventory Visibility provides it in real time. Whenever an event that changes inventory occurs in the system (such as order creation, editing, cancellation, return, or fulfillment), the event is immediately posted to Inventory Visibility to update its inventory snapshot.

The following illustration shows a system that implements most of the previously mentioned integration scenarios (but just a single CSU).

:::image type="content" source="media/commerce-ivs-integration.svg" alt-text="Block diagram of an integrated system." lightbox="media/commerce-ivs-integration.svg":::

For more information about Inventory Visibility, see [Inventory Visibility Add-in overview](inventory-visibility.md).

## Prerequisites

Before you can use the features that this article describes, your system must meet the following requirements:

- You must have licenses for both Supply Chain Management and Commerce.
- You must be running Supply Chain Management version 10.0.36 or later.
- The Inventory Visibility add-in must be installed and set up as described in [Install and set up Inventory Visibility](inventory-visibility-setup.md). Be sure to make a note of the following information from the setup, because you'll need it when you set up the integration with Commerce:

    - Application ID (Client ID)
    - Client secret
    - Tenant ID

- The following features must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md):

    - *Inventory Visibility integration with inventory adjustment posting*
    - *Inventory Visibility integration with inventory adjustment offset*
    - *Enable warehouse items in Inventory Visibility*

- [Inventory Visibility support for WMS items](inventory-visibility-whs-support.md) must be enabled for your environment.

## Enable adjustments in Supply Chain Management

To enable adjustments in Supply Chain Management, follow these steps.

1. Sign in to Supply Chain Management.
1. Go to **Inventory Management** \> **Inventory Visibility** \> **Inventory Visibility integration**.
1. On the **Adjustment** tab, on the **Manage inventory adjustment posting and retry** FastTab, on the toolbar, select **Enable adjustment**.

## <a name="key-vault"></a>Create a key vault to hold the client secret for Inventory Visibility

To create a key vault to hold the client secret for Inventory Visibility, follow these steps.

1. Sign in to the [Azure portal](https://portal.azure.com/).
1. Search for or select **Key vaults** to open the **Key vaults** page.
1. On the toolbar, select **Create**.
1. Work through the **Create key vault** wizard to create a key vault.
1. Open the key vault that you just created.
1. On the navigation pane, select **Overview**.
1. Copy the **Vault URI** value, and paste it into a temporary text file. Label the value so that you can identify it later.
1. While your key vault is still open, on the navigation pane, select **Object** \> **Secrets**.
1. On the toolbar, select **Generate/Import**.
1. On the **Create a secret** page, set the following fields:

    - **Upload options** – Select *Manual*.
    - **Name** – Enter a name for the secret (for example, *commerce-iv-01-secret*). Copy the value, paste it into your temporary text file, and label it.
    - **Secret value** – Enter the client secret value that you used when you installed the Inventory Visibility add-in (as mentioned in the [Prerequisites](#prerequisites) section).
    - **Content type** – This is an optional field. The suggested value is *application/vnd.bag-3rdPartyHostedSecretNoRotation*.
    - **Set activation date** – Select this checkbox, and then enter the first date when this secret should be valid.
    - **Set expiration date** – Select this checkbox, and then enter the last date when this secret should be valid.
    - **Enabled** – Set this option to *Yes*.

1. Select **Create** to create and save the secret.

## <a name="app-registration"></a>Register a Microsoft Entra application to provide access to the key vault

To register a Microsoft Entra application to enable Supply Chain Management and Commerce to access the key vault, follow these steps.

1. In the [Azure portal](https://portal.azure.com/), return to the home page.
1. Search for or select **App registrations** to open the **App registrations** page.
1. On the toolbar, select **New registration**.
1. On the **Register an application** page, set the following fields:

    - **Name** – Enter a name.
    - **Supported account types** – Specify who can use the new application. For more information about this setting, see [Identity and account types for single- and multitenant apps](/security/zero-trust/develop/identity-supported-account-types).
    - **Redirect URI** – Leave this field blank.

1. Select **Register** to register the application.
1. The new app registration is opened. On the navigation pane, select **Manage** \> **Certificates & secrets**.
1. On the **Client secrets** tab, select **New client secret**.
1. In the **Add a client secret** dialog box, select an expiration date that meets your needs, and then select **Add**.
1. The **Certificates & secrets** page now shows details about the new client secret. These details are shown only once and will be hidden when the page is reloaded. Therefore, you must copy them now. Copy the **Value** value, paste it into your temporary text file, and label it.
1. On the navigation pane, select **Overview**. Copy the following values, paste them into your temporary text file, and label them:

    - **Application (client) ID**
    - **Directory (tenant) ID**

## <a name="scm-vault-setup"></a>Set up Supply Chain Management to access the new key vault

To set up Supply Chain Management to access the new key vault through the new application, follow these steps.

1. Sign in to Supply Chain Management.
1. Use the company picker to select the same company (legal entity ID) as your Dynamics 365 Commerce channel.
1. Go to **System administration** \> **Setup** \> **Key Vault parameters**.
1. On the Action Pane, select **New** to add a record. Set the following fields for it:

    - **Name** – Enter a name for the Key Vault record.
    - **Description** – Enter a short description.
    - **Key Vault URL** – Paste the **Vault URI** value that you copied when you created the key vault. (See step 7 in the [Create a key vault to hold the client secret for Inventory Visibility](#key-vault) section.)
    - **Key Vault client** – Enter the **Application (client) ID** value that you copied when you created the app registration. (See step 10 in the [Register a Microsoft Entra application to provide access to the key vault](#app-registration) section.)
    - **Key Vault secret key** – Enter the secret **Value** value that you copied when you created the app registration. (See step 9 in the [Register a Microsoft Entra application to provide access to the key vault](#app-registration) section.)

1. On the **Secrets** FastTab, on the toolbar, select **Add** to add a row to the grid. Set the following fields for it:

    - **Name** – Enter a name to identify the secret. You'll need this value later. Therefore, copy it, paste it into your temporary text file, and label it.
    - **Description** – Enter a short description.
    - **Secret** – Enter a value in the form *vault:///\<SecretName\>*, where *\<SecretName\>* is the **Name** value that you copied when you created the secret for the key vault. (See step 10 in the [Create a key vault to hold the client secret for Inventory Visibility](#key-vault) section.) For example, if the name of your key vault secret is *commerce-iv-01-secret*, enter *vault:///commerce-iv-01-secret*.
    - **Secret type** – Select *Manual*.

1. On the **Secrets** FastTab, on the toolbar, select **Validate**. If you correctly entered all the values, you receive the following informational message: "Validation successful." If you receive an error message, double-check your settings, and try again.
1. On the Action Pane, select **Save**. Be patient, because the save operation takes about two minutes.

For more information about the settings that are mentioned in this procedure, see [Set up the Azure Key Vault client](../../finance/localizations/global/setting-up-azure-key-vault-client.md).

## Set up the integration between Inventory Visibility and Commerce

To set up the integration between Inventory Visibility and Commerce, follow these steps.

1. Sign in to Supply Chain Management.
1. Go to **Retail and Commerce** \> **Headquarters setup** \> **Parameters** \> **Commerce shared parameters**.
1. On the **Inventory** tab, set the following fields:

    - **Microsoft Entra tenant ID** – Enter the **Directory (tenant) ID** value that you used when you installed the Inventory Visibility add-in (as mentioned in the [Prerequisites](#prerequisites) section).
    - **Microsoft Entra app ID** – Enter the **Application (client) ID** value that you used when you installed the Inventory Visibility add-in (as mentioned in the [Prerequisites](#prerequisites) section).
    - **Microsoft Entra client secret** – Select the **Name** value that you copied when you specified the secret for the key vault on the **Key Vault parameters** page in Supply Chain Management. (See step 5 in the [Set up Supply Chain Management to access the new key vault](#scm-vault-setup) section.)
    - **Use Inventory Visibility as inventory data provider** – Set this option to *Yes*.

1. On the Action Pane, select **Save**.

## Run the global configuration job

To run the global configuration job, follow these steps.

1. Go to **Retail and Commerce** \> **Retail and Commerce IT** \> **Distribution schedule**.
1. In the list pane, select the record that's named *1110 Global configuration*.
1. On the Action Pane, select **Run now**.
