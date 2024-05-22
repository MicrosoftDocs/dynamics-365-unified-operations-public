---
title: Enable Inventory Visibility service for Commerce
description: This article describes how to set up Inventory Visibility for Dynamics 365 Dynamics 365 Commerce Commerce Scale Unit so that Commerce e-commerce, POS or other applications on Commerce Scale Units can leverage real-time inventory visibility for their retail business.
author: yufeihuang
ms.author: yufeihuang
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 05/20/2024
audience: Application User
ms.custom: 
  - bap-template
---

# Enable Inventory Visibility for Commerce

This article describes how to set up Inventory Visibility for Dynamics 365 Commerce Commerce Scale Unit (CSU) so that Commerce e-commerce, POS, or other applications on CSUs can leverage real-time inventory visibility for real-time inventory lookup, reservation, and adjustments.

## Business scenario fit

The accuracy of inventory availability is crucial for any retailer running an omnichannel business. The discrepancy between system recorded inventory and physical inventory may cause revenue loss or customer satisfaction issues. Retailers generally expect a holistic view of accurate inventory across channels and locations, throughout sales and supply chain processes, and want to have the ability to query, reserve and adjust on-hand inventory in a performant manner, as real-time as possible.  

Commerce inventory data is living in an async world that the entire system architecture relies on scheduled backend jobs to exchange data between HQ and CSU components. At any point of time, inventory data in HQ is not guaranteed to be 100% accurate to reflect the latest inventory snapshot, thus is not reliable to support omnichannel scenarios.

Therefore if your company is operating on both Commerce and SCM, or you POS/e-commerce business runs on multiple CSUs, or your may also have 3rd party systems that also updates inventory. It is suggested that you enable this feature

![Real-time inventory visibility for Commerce](media/Real-time-inventory-visibility-for-Commerce.png.png "Real time Inventory Visibility for Commerce")

Supply Chain Management Inventory Visibility service is an independent and highly scalable micro-service for real-time on-hand inventory change posting and visibility tracking across data sources, and it provides a set of RESTful APIs for integration. Commerce-IV integration is now natively supported out-of-the-box - Whenever a Commerce channel requests for real-time inventory data from Commerce engine, the data is obtained from IV real-time, and whenever some order action (such as creation, editing, cancellation, return or fulfill) occurs in the system that changes inventory, IV is updated accordingly to reflect the latest inventory snapshot.

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

## Settings

1. Go to Inventory Management > Inventory Visibility integration > on **Inventory Visibility integration** page, go to **Adjustment** tab > **Enable adjustment**

1. Set up Azure application and create Key Vault
    1. Log onto Microsoft Azure portal
    1. Search or select **Key Vault** > select the subscription you have and click **apply** > **Create**
    1. Click into the Key Vault you just created, on the **Overview** tab, you will fine a **Vault URL**, keep of note of it.
    1. Stay with the Key Vault, go to tab **Object** > **Secrets** > **Generate/Import** > you will be able to create a new secret. Click on the **Show Secret Value** and note down the value, you will need it for Supply Chain Management to IV authentication later.
    1. Go back to the home page of Azure portal > App Registrations > New registration. Once created, click into the new app registration > Certificates & secrets > Client secrets > Note down the **Secret Value** (very important it is only visible to you for once). Application (client) ID, Secret ID and Tenant ID. This app is for Supply Chain Management (also referred to as HQ) to access Azure Key Vault.
    1. Go back to Supply Chain Management > System administration > set up > Key Vault Parameters. Make sure the organization ID you configure Key Vault parameters is the same are your Commerce Channel side org ID. For example, make sure they both are 'usrt'.
    1. On the **Key Vault Parameters** > Fill the name as key vault name you just created. On **General** tab, fill the Key Vault URL you noted down. Fill in the **Key Vault Client** with the Application (client) ID and **Key Vault secret key** as the **Secret Value** you noted down previously for App registration on step 3.5
    1. On the **Secret** tab > Add > Enter the name of the secret you created on step 3.4; and enter secret as vault:///<secret name>. Secret type = "Manual". Then click "Validate" and there should be a info message on the top: "Validation successful.".
    For example if your secret name is commerce-iv-01-secret, you should enter Secret in a format as vault:///commerce-iv-01-secret
    1. Save your settings. Be patient, the "Save" will take approximately 2 minutes.

    You can refer to the reference [Set up the Azure Key Vault client](../../finance/localizations/global/setting-up-azure-key-vault-client.md).

1. Set up Commerce-IV integration parameters
    1. Go to **Retail and Commerce**> **Headquarters setup** > **Parameters**
    1. On **Inventory** tab, switch on **Use Inventory Visibility as inventory data provider**. Fill in the tenant ID, app ID you have when setting up the Inventory Visibility add-in during prerequisite settings
    1. For **Microsoft Extra client secret**, select the one you created in step 3.4

1. Go back to Headquarters > Retail and Commerce > Retail and Commerce IT > 1110 Global configurations > Run now.
