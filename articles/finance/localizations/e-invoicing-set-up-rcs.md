---
title: Set up Regulatory Configuration Service (RCS)
description: This article explains how to set up Regulatory Configuration Service (RCS).
author: gionoder
ms.date: 10/21/2022
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: gionoder
ms.search.validFrom: 2020-07-08
ms.dyn365.ops.version: AX 10.0.12
ms.collection: get-started
ms.assetid: 
ms.search.form: 
---

# Set up Regulatory Configuration Service (RCS)

[!include [banner](../includes/banner.md)]

This article explains how to set up Regulatory Configuration Service (RCS).

## Turn on Globalization features

1. Sign in to your RCS account.
2. Select the **Feature management** tile.
3. In the **Feature management** workspace, select **Globalization features** in the list, and then select **Enable now**.

A tile for the **Globalization features** workspace should now  appear on the main RCS dashboard.

## Set up the parameters for RCS integration with Electronic invoicing

1. In the **Globalization features** workspace, in the **Related settings** section, select **Electronic reporting parameters**.
2. The first time you set up the parameters, you will be prompted to connect to Life Cycle Services (LCS). Select **Click here to connect to Lifecycle Services**, and after the connection is established, select **OK**.

    > [!IMPORTANT]
    > In countries or regions where the data residence is enforced, and if your RCS was provisioned in a region different where LCS is provisioned, you may receive the following connection error message in RCS: “No HTTP resource was found that matches the request URI”. Select **OK**. You may receive another error message in RCS: "Failed to generate the user token for Dynamics Lifecycle services on behalf on user (). Please contact your system administrator."
    >  
    > This happens because LCS is a global service and is provisioned in a US region. Because of the data residence policy, the RCS from your current region is unable to connect to LCS. Under these circunstances, there are 2 possible solutions:
    > - Delete RCS from your current region and recreate it in US region.
    > - Ignore the errors and continue with Electronic invoicing setup. These errors have no impact on the Electronic invoicing functionality.

3. On the **Electronic Invoicing** tab, in the **Service endpoint URI** field, enter the appropriate service endpoint for your Microsoft Azure geography, as shown in the following table.

    | Datacenter Azure geography | Service endpoint URI |
    |----------------------------|----------------------|
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
    | Norway                     | <p>`https://gw.no-il101.gateway.prod.island.powerapps.com/electronicinvoicing/`</p> |
    | South Africa               | <p>`https://gw.za-il101.gateway.prod.island.powerapps.com/electronicinvoicing/`</p> |

3. Review and enter in the **Application ID** field the fixed value **0cdb527f-a8d1-4bf8-9436-b352c68682b2**. Make sure that only a globally unique identifier (GUID) is entered, and that the value doesn't include any other symbols, such as spaces, commas, periods, or quotation marks.
4. In the **LCS Environment ID** field, enter the ID of your Microsoft Dynamics Lifecycle Services (LCS) environment. This value is the reference to the Finance or Supply Chain Management environment that you will use with the Electronic Invoicing service. To get your ID, sign in to [LCS](https://lcs.dynamics.com/), open your project, and then, on the **Manage environment** tab, in the **Environment details** section, look in the **Environment Id** field.

    > [!IMPORTANT]
    > If the Electronic Invoicing add-in is installed in multiple Finance or Supply Chain Management environments in LCS, always use the environment ID of the most recently installed environment. If you decide to install the add-in in a new environment After you set up and work with Electronic Invoicing functionality, update the **LCS Environment ID** field in RCS to the latest value.

5. Select **Save**, and then close the page.

## Configuration providers

You can use configuration providers to distinguish the owners of the Electronic reporting (ER) configurations that are used in electronic invoicing processes and the owners Globalization features. For all Globalization features that are provided by Microsoft and published in the Global repository, the configuration provider is set to **Microsoft** (`http://microsoft.com`).

You can adjust only ER configurations and Globalization features that belong to the active configuration provider. You can use these configurations and features as templates to create configurations and features that belong to the active configuration provider, so that you can adjust them.

First, create the configuration providers. Then set one of them as active. You can't set the **Microsoft** configuration provider as active.

### Create a configuration provider

1. In the **Electronic reporting** workspace, in the **Related links** section, select **Configuration providers**.
2. Select **New**.
3. In the **Name** field, enter a unique name for the configuration provider.
4. In the **Internet address** field, enter the unique URL of the configuration provider.
5. Select **Save**, and then close the page.

### Select a configuration provider as active

1. In the list of configuration providers, select the configuration provider that you want to set as active.
2. Select **Set active**.

## Import ER configurations from the Global repository

1. In the **Electronic reporting** workspace, in the **Related links** section, select **Configuration providers**.
2. In the list of configuration providers, select **Microsoft**, and then select **Repositories**.
3. Select **Global**, and then, on the Action Pane, select **Open**.
4. Import the following ER models:

    - **Customer invoice context model**
    - **Invoice model**
    - **Fiscal documents** (for Brazilian scenarios, if required)
    - **Response message model**

5. If **Invoice model mapping** wasn't automatically imported, import it.
6. Close the page.
