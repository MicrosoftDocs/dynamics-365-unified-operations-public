---
title: Create a data integration project
description: Learn how to create a data integration project, including a step-by-step process detailing the creation of data integration projects.
author: ShivamPandeyMSFT
ms.author: shpandey
ms.topic: how-to
ms.date: 06/23/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-07-24
ms.search.form: 
ms.dyn365.ops.version: AX 10.0.13
ms.assetid: 3d43ba40-780c-459a-a66f-9a01d556e674
---

# Create a data integration project

[!include [banner](../includes/banner.md)]

This article explains how to create a data integration project.

1. Sign in to Microsoft Dynamics 365 Finance.
1. Go to **Workspaces \> Data management**, and select **Data entities**. Wait until all the data entities refresh before you move on to the next step.
1. Open the [Power Apps portal](https://make.powerapps.com/), and follow these steps:

    1. Select the appropriate environment.
    1. In the left navigation pane, select **Dataverse \> Connections**.
    1. Connect to appropriate instances of the following items:

        - Dynamics 365
        - Dynamics 365 for Fin & Ops

1. Open the [Power Apps environments](https://admin.powerapps.com/environments), and follow these steps:

    1. Select **Data integration**.
    1. Select **Connection sets**.
    1. Select **New connection set**.
    1. Enter a name for the connection.
    1. Select the appropriate connections for the following items:

        - Dynamics 365
        - Dynamics 365 for Fin & Ops

    1. Select the appropriate organization mapping.
    1. Select **Create**.

> [!NOTE]
> The use of Dynamics 365 Data Integration connections is deprecated. You can continue using existing connections, but you can't create new connections.
> Update your data integration projects to use the **Dataverse (Legacy)** connector.

1. Open the [Power Apps environments](https://admin.powerapps.com/environments), and follow these steps:  

    1. Create a single data integration project for each of the following templates by using the connection set that you just created:

        - Customer payment insights result (CDS to Fin and Ops 10.0.17+)
        - Cash flow time series results (CDS to Fin and Ops)
        - Budget time series results (CDS to Fin and Ops)

      > [!NOTE]
      > Creating multiple data integration projects for each template can cause errors that block the updates.

    1. Set the appropriate scheduling for each project.

> [!NOTE]
> If you don't see the required entities in Dataverse, go to **Credit and collections** > **Setup** > **Finance Insights** > **Finance insights parameters**, enable the feature, **Customer payment predictions**, and then select **Create prediction model**. When the deployment of AI model is complete, the Dataverse entities needed to create integration are deployed.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
