---
# required metadata

title: Setup Regulatory Configuration Services (RCS)
description: This topic introduces the setup of the Regulatory Configuration Service (RCS).
author: dkalyuzh
ms.date: 02/09/2022
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
ms.custom: ["97423", "intro-internal"]
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: janeaug
ms.search.validFrom: 2020-07-08
ms.dyn365.ops.version: AX 10.0.12

---

# Setup Regulatory Configuration Services (RCS)

[!include [banner](../includes/banner.md)]

This topic provides information about how to set up the Regulatory Configuration Service (RCS).

## Turn on Globalization features
1. Sign in to your RCS account.
2. In RCS, select the **Feature management** tile.
3. In the **Feature management** workspace, select **Globalization features** in the list, and then select **Enable now**.

After activation you will see **Globalization features** workspace on the main page.

## Set up the parameters for RCS integration with Electronic invoicing
1. In the **Globalization features** workspace, in the **Related settings** section, select **Electronic reporting parameters**.
2. On the **Electronic Invoicing** tab, in the **Service endpoint URI** field, enter the appropriate service endpoint for your Azure geography, as shown in the following table.

    | Datacenter Azure geography | Service endpoint URI                                                                 |
    |----------------------------|--------------------------------------------------------------------------------------|
    | United States              |  <p>`https://gw.us-il101.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.us-il102.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.us-il103.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.us-il104.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.us-il105.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.us-il106.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.us-il107.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.us-il108.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.us-il109.gateway.prod.island.powerapps.com/electronicinvoicing/`</p> |
    | Europe                     | <p>`https://gw.eu-il101.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.eu-il102.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.eu-il103.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.eu-il104.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.eu-il105.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.eu-il106.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.eu-il107.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.eu-il108.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.eu-il109.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.eu-il110.gateway.prod.island.powerapps.com/electronicinvoicing/`</p> |
    | United Kingdom             | <p>`https://gw.uk-il101.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.uk-il102.gateway.prod.island.powerapps.com/electronicinvoicing/`</p> |
    | Asia                       | <p>`https://gw.as-il101.gateway.prod.island.powerapps.com/electronicinvoicing/`</p><p>`https://gw.as-il102.gateway.prod.island.powerapps.com/electronicinvoicing/`</p> |
    | Japan                      | <p>`https://gw.jp-il101.gateway.prod.island.powerapps.com/electronicinvoicing/`</p>|


3. Verify that the **Application ID** field is set to **0cdb527f-a8d1-4bf8-9436-b352c68682b2**. This is a fixed value. Make sure that only GUID is entered, and the field doesn't contain any other symbols such as a space, comma, dot, or quotes.
4. In the **LCS Environment ID** field, enter the ID of your LCS environment. This is the reference to the Finance or Supply Chain Management environment that you are going to use with the Electronic Invoicing service. You can get your ID in your LCS project (https://lcs.dynamics.com/), on the **Manage environment** tab, in the **Environment details** field group, in the **Environment Id** field. 

   > [!IMPORTANT]
   > If you have several Finance or Supply Chain Management environments in LCS with the Electronic Invoicing add-in installed, always use the Environment ID of the latest installed environment. If, after setup and work with Electronic Invoicing functionality, you decide to install the add-in in a new environment, update the **LCS Environment ID** in RCS to the latest value. 
    
5. Select **Save**, and then close the page.

## Configuration providers
You can use configuration providers to distinguish between the owners of the Electronic reporting (ER) configurations used in electornic invoicing processes and Globalization features.
All Globalization features provided by Microsoft and published in the Global repository have a configuration provider parameter set to Microsoft (`http://microsoft.com`). You can't adjust ER configurations or Globalization features if they don't belong to active Configuration provider. You can use these configurations and features as templates for creating configurations and features by active configuration provider that you can adjust.
First, create the configuration providers and then set one of the providers as **Active**. You can't set the Microsoft configuration provider as **Active**.

### Create a provider
1. Go to the **Electronic reporting** workspace and in the **Related links** section, select **Configuration providers**.
2. Select **New** and in the **Name** field, enter the unique name of the configuration provider.
5. In the **Internet address** field, enter the unique URL of the configuration provider.
6. Select **Save**, and then close the page.

### Select provider as active
1. Select your configuration provider.
2. Select **Set active**.

## Import Electronic reporting (ER) configurations from the Global repository
1. From the list of configuration providers, select **Microsoft**, and then select **Repositories**.
2. Select **Global**, and on the Action Pane, select **Open**.
3. Import the ER models, **Customer invoice context model**, **Invoice model**, **Fiscal documents** (for Brazilian scenarios, if required), and **Response message model**.
4. If **Invoice model mapping** was not imported automatically, import it.
5. Close the page. 
