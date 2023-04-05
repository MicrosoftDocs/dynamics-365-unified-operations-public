---
title: Configure advanced export control
description:
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 07/31/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Configure advanced export control

## Prerequisites

### Enable the feature in Supply Chain Management

To use advanced export control, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management 10.0.34 or later.
- The feature that is named *Advanced export control* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

### Get the Advanced Export Control solution

Install the Advanced Export Control solution for Supply Chain Management from Microsoft AppSource. For instructions, see [Microsoft Dynamics 365 Export Control App](https://appsource.microsoft.com/product/dynamics-365/mscrm.exportcontrol). <!-- KFM: Link doesn't work. Will there be instructions here? -->

## Authentication and authorization

The system makes export control checks using application user calls, which means they can be made regardless of which user is working with the document in Supply Chain Management. Supply Chain Management users don't need to be added to Dataverse nor given extra permissions. To support this service-to-service (S2S) authentication, an Azure Active Directory (Azure AD) application must be created for each environment. You must not share or re-use the Azure AD applications across different environments.

### Register the app in your Azure portal

Follow these steps to create the Azure AD application.

1. Sign in to your [Azure portal](https://portal.azure.com).
1. Go to **Azure Active Directory \> App registrations**.
1. Select **New Registration**.
1. The **Register an application** page opens. Enter the following information:
    - **Name** – Enter a unique name.
    - **Supported account types** – Select *Any Azure AD directory* (single or multi-tenant). <!-- KFM: This doesn't match the options I see. -->
    - **Redirect URI** – Leave blank.

1. Select **Register**.
1. A page opens showing details about your new app. Copy the **Application (client) ID** value to a temporary text file because you will need it later.
1. In the navigation pane, select **Certificates & secrets**.
1. The **Certificates & secrets** page opens. Select **New client secret**.
1. The **Add a client secret** dialog opens. Enter a description and an expiration date and then select **Add**.
1. You return to the **Certificates & secrets** page, which now shows a row with details about your new client secret. Copy the value in the **Value** column to a temporary text file because you will need it later and it will be hidden the next time you open this page.

### Grant application permissions in the Power Platform Admin Center

1. Sign in to your[Power Platform Admin Center](https://admin.powerplatform.microsoft.com).
1. Go to **Select environment \> Settings \> Users \> Application users**.  <!-- KFM: This doesn't match what I see, but I don't have any environments. Can I get a demo of this step? -->
1. Select **New app user**
1. Select the new application that you registered in the previous section. Assign the appropriate business unit. In security roles, assign the **Export control application** security role. <!-- KFM: I'm not sure what we are doing here. We should be more explicit (name field labels, for example.) -->

## Configure the application in Supply Chain Management

1. Go to **Product information management \> Setup \> Country of Origin \> Advanced export control configuration**

1. Enter the **Azure AD application ID** and **application secret** from the previous section and **save**.

1. Turn on the **Advanced export control functionality enabled** and **Validate data in Dataverse** options and select **save**. 

This will validate that it can connect and that the appropriate solution is installed. If you receive any errors in this step, please validate that the Export Control application is successfully installed and that the specified Azure AD application has the **Export control application** security role in Dataverse.

1. Click the **Synchronize country/region list** button to copy the existing list of country/region codes from Finance and Operations to the Dataverse solution. This list will be used when defining rules. This button can be re-clicked in the future if any new country/regions are added or changed. Note: The name of the countries will be synchronized using the language of the user who clicks the button.