---
# required metadata

title: Setup Regulatory Configuration Services (RCS)
description: This topic introduces to the setup of RCS

author: dkalyuzh
ms.date: 12/15/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
---

[!include [banner](../includes/banner.md)]

## Turn on the Globalization features
  1. Sign in to your RCS account.
  2. In the RCS instance, select the **Feature management** tile.
  3. In the **Feature management** workspace, select **Globalization features** in the list, and then select **Enable now**.


After activation you will see Globalization features workspace in the main form.

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


  3. Verify that the **Application ID** field is set to ***0cdb527f-a8d1-4bf8-9436-b352c68682b2***. This value is a fixed value. Make sure that only GUID is entered, and the field doesn't contain any other symbols like space, comma, dot, quotes, etc.
  4. In the **LCS Environment ID** field, enter the ID of your LCS environment. This is the reference to Finance and Supply Chain management environments that you are going to use with Electronic Invoicing service. You can get it in your LCS project (https://lcs.dynamics.com/), **Manage environment** tab, **Environment details**, field **Environment Id**. 

> [!IMPORTANT]
> If you have several Finance and Operations environments in LCS with installed Electronic Invoicing Add-in, you must always use Environment Id of the latest installed environment. If after setup and work with Electronic Invoicing functionality you decide to install Add-in in new environment, you should update **LCS Environment ID** in RCS to the latest value. 
    
 5. Select **Save**, and then close the page.


## Configuration providers
Configuration providers allow you to maintain distinguish of the owners of the Electronic reporting configurations used in e-invoicing processes, as well as Globalization features.
All Globalization features provided by Microsoft and published in Global repository, have a configuration provider parameter set to Microsoft (`http://microsoft.com`). You can't adjust ER configurations or Globalization features, if they don't belong to active Configuration provider.
You can use these configurations and feature as templates for creating configurations and features by active Configuration provider that you can adjust.
First, you should create Configuration providers, then set one of the provider as an active. You can't set Microsoft Configuration provider as an active.

### Create a provider
  1. Go to **Electronic reporting** workspace
  2. Go to **Related links** > **Configuration providers**
  3. Select **New**
  4. In the **Name** field, type a unique name of the configuration provider
  5. In the **Internet address** field, type unique URL of the configuration provider.
  6. Select **Save**, and then close the page.

### Select provider as active
  1. Select your configuration provider
  2. Select **Set active**.

## Import Electronic reporting (ER) configurations from Global repository
  1. From the list of **Configuration providers**, select ***Microsoft*** configuration provider and then select **Repositories**.
  2. Select **Global** and on Action Pane, select **Open**.
  3. Import ER models ***Customer invoice context model***, ***Invoice model***, ***Fiscal documents*** (for Brazilian scenarios, if required), and ***Response message model***.
  4. If ***Invoice model mapping*** was not imported automatically, import it.
  5. Close the form 
