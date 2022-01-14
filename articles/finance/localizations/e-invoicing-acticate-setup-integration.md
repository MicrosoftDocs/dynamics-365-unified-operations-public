---
# required metadata

title: Activate and setup integration with Electronic invoicing
description: This topic provides description of the process of activating the integration of Finance and Supply Chain management with Electronic invoicing.
author: dkalyuzh
ms.date: 12/15/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
---

# Activate and setup integration with Electronic invoicing

[!include [banner](../includes/banner.md)]

You must have an LCS project that includes version 10.0.17 or later of Microsoft Dynamics 365 Finance or Supply Chain Management. Additionally, these apps must be deployed in one of the following Azure geographies:
 - United States
 - Europe
 - United Kingdom
 - Asia
 - Japan

## Electronic invoicing integration feature
To enable communication between Finance and Supply Chain Management and Electronic invoicing, you must turn on the ***Electronic Invoicing integration*** feature.

 1. Sign in to your Finance or Supply Chain Management instance.
 2. In the **Feature management** workspace, search for the **Electronic invoicing integration** feature. If this feature doesn't appear on the page, select **Check for updates**.
 3. Select the feature, and then select **Enable now**.


## Service endpoint and environment
The service endpoint is the URL where Electronic invoicing is located. Before electronic invoices can be issued, the service endpoint must be configured in Finance and Supply Chain management to allow for communication with the service.
The environment name that is entered in Finance and Supply Chain Management refers to the name of the Service environment that is created in RCS and published to Electronic invoicing.

 1. Go to **Organization administration** > **Setup** > **Electronic document parameters**.
 2. On the **Electronic invoicing** tab, in the **Endpoint URL** field, enter the appropriate service endpoint for your Azure geography, as it is set in RCS in **Service endpoint URI** parameter.
 3. In the **Environment** field, enter the name of the service environment published in Electronic invoicing.
 4. Select **Save**, and then close the page.
