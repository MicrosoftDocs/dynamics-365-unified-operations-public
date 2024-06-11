---
title: Enable Inventory Visibility service for Commerce
description: This article describes how to set up Inventory Visibility for Dynamics 365 Commerce Scale Units (CSUs) so that e-commerce, POS, or other applications on CSUs can leverage inventory visibility for real-time inventory lookup, reservation, and adjustments.
author: yufeihuang
ms.author: yufeihuang
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 06/11/2024
audience: Application User
ms.custom: 
  - bap-template
---

# Enable Inventory Visibility for Commerce

This article describes how to set up Inventory Visibility for Dynamics 365 Commerce Scale Units (CSUs) so that e-commerce, POS, or other applications on CSUs can leverage inventory visibility for real-time inventory lookup, reservation, and adjustments.

## Inventory Visibility for Commerce

Accurate inventory information is crucial for any retailer running an omnichannel business. Discrepancies between system recorded inventory and physical inventory can result in lost revenue or reduced customer satisfaction. Retailers require an accurate, holistic view of inventory across all channels and locations, and throughout all sales and supply-chain processes. They need the ability to query, reserve, and adjust on-hand inventory in near real-time.  

Dynamics 365 Commerce works asynchronously with inventory data. It relies on scheduled backend jobs to exchange data between headquarters and CSU components. At any given time, inventory data available to headquarters might not reflect the latest inventory snapshot, which makes it unreliable to support omnichannel scenarios. We recommend enabling Inventory Visibility for Commerce to provide real-time inventory data across all channels if your company runs any or all of the following scenarios:

- You are running both Dynamics 365 Commerce and Dynamics 365 Supply Chain Management.
- Your point-of-sale or e-commerce business runs on multiple CSUs.
- You have 3rd party systems that also update inventory.

<!-- Image is missing
![Real-time inventory visibility for Commerce](media/Real-time-inventory-visibility-for-Commerce.png.png "Real time Inventory Visibility for Commerce")
-->

The Inventory Visibility Add-in (also referred to as the *Inventory Visibility service*) for Dynamics 365 Supply Chain Management is an independent and highly scalable micro-service for posting on-hand inventory changes and tracking inventory across data sources in real time. It provides a set of RESTful APIs and includes native support for integrating with Dynamics 365 Commerce right out of the box. Whenever a Commerce channel requests real-time inventory data, Inventory Visibility provides it in real-time. Whenever an event occurs in the system that changes inventory (such as order creation, editing, cancellation, return, or fulfill), the event is immediately posted to Inventory Visibility to update its inventory snapshot.

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must have licenses for both Dynamics 365 Supply Chain Management and Dynamics 365 Commerce.
- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.36 or later.
- The Inventory Visibility add-in must be installed and set up as described in [Install and set up Inventory Visibility](inventory-visibility-setup.md). Be sure to take note of the following information from the setup because you will need it when setting up the integration with Dynamics 365 Commerce:
    - Application ID (Client ID)
    - Client secret
    - Tenant ID
- The following features must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
    - *Inventory Visibility integration with inventory adjustment posting*
    - *Inventory Visibility integration with inventory adjustment offset*
    - *Enable warehouse items in Inventory Visibility*
- [Inventory Visibility support for WMS items](inventory-visibility-whs-support.md) must be enabled for your environment.

## Step 1: Enable adjustments in Supply Chain Management

Enable adjustments in Supply Chain Management by following these steps:

1. Sign in to Supply Chain Management
1. Go to **Inventory Management** \> **Inventory Visibility** \> **Inventory Visibility integration**.
1. Open the **Adjustment** tab. On the **Manage inventory adjustment posting and retry** FastTab toolbar, select **Enable adjustment**.

## Step 2: Register an Azure application and set up Key Vault

Register an Azure application and set up Key Vault by following these steps:

1. Sign in to [Microsoft Azure portal](https://portal.azure.com/).
1. Search for or select **Key Vault**. Select your subscription and then select **Apply** \> **Create**. <!--KFM: I couldn't find this. -->
1. Open the key vault you just created. On the **Overview** tab, copy the value shown for **Vault URL** and paste it into a temporary text file. <!--KFM: I couldn't find this. -->
1. Go to **Object** > **Secrets** > **Generate/Import**. Create a new secret. <!--KFM: I couldn't find this. -->
1. Select **Show Secret Value**. Copy the value shown and paste it into your temporary text file. <!--KFM: I couldn't find this. -->
1. Go back to the home page of Azure portal. Then search for or select **App Registrations**.
1. On the toolbar, select **New registration**. Enter a **Name** for your new app registration, and then select **Register**.
1. With your new app registration open, from the navigation pane, select **Certificates & secrets**. On the **Client secrets** tab, select **New client secret**. Enter a **Description** for the secret, select an **Expiration** date, and then select **Add**. Copy the **Value** shown and paste it into your temporary text file.
1. 
1. 
1. 
1. 
1.  > App Registrations > New registration. Once created, click into the new app registration > Certificates & secrets > Client secrets > Note down the **Secret Value** (very important it is only visible to you for once). Application (client) ID, Secret ID and Tenant ID. This app is for Supply Chain Management (also referred to as HQ) to access Azure Key Vault.
1. Go back to Supply Chain Management > System administration > set up > Key Vault Parameters. Make sure the organization ID you configure Key Vault parameters is the same are your Commerce Channel side org ID. For example, make sure they both are 'usrt'.
1. On the **Key Vault Parameters** > Fill the name as key vault name you just created. On **General** tab, fill the Key Vault URL you noted down. Fill in the **Key Vault Client** with the Application (client) ID and **Key Vault secret key** as the **Secret Value** you noted down previously for App registration on step 3.5
1. On the **Secret** tab > Add > Enter the name of the secret you created on step 3.4; and enter secret as vault:///<secret name>. Secret type = "Manual". Then click "Validate" and there should be a info message on the top: "Validation successful.".
For example if your secret name is commerce-iv-01-secret, you should enter Secret in a format as vault:///commerce-iv-01-secret
1. Save your settings. Be patient, the "Save" will take approximately 2 minutes.

You can refer to the reference [Set up the Azure Key Vault client](../../finance/localizations/global/setting-up-azure-key-vault-client.md).

## Step 3: Set up the integration between Inventory Visibility and Commerce

1. Go to **Retail and Commerce**> **Headquarters setup** > **Parameters**
1. On **Inventory** tab, switch on **Use Inventory Visibility as inventory data provider**. Fill in the tenant ID, app ID you have when setting up the Inventory Visibility add-in during prerequisite settings
1. For **Microsoft Extra client secret**, select the one you created in step 3.4

1. Go back to Headquarters > Retail and Commerce > Retail and Commerce IT > 1110 Global configurations > Run now.
