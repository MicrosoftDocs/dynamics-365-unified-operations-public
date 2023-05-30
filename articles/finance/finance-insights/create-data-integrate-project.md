---
# required metadata

title: Create a data integration project
description: This article explains how to create a data integration project.
author: ShivamPandey-msft
ms.date: 05/06/2022
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
ms.assetid: 3d43ba40-780c-459a-a66f-9a01d556e674
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2020-07-24
ms.dyn365.ops.version: AX 10.0.13

---
# Create a data integration project

[!include [banner](../includes/banner.md)]

This article explains how to create a data integration project.

1. Sign in to Microsoft Dynamics 365 Finance.
2. Go to **Workspaces \> Data management**, and select **Data entities**. Wait until all the data entities have been refreshed before you move on to the next step.
3. Open the [Power Apps portal](https://make.powerapps.com/), and follow these steps:

    1. Select the appropriate environment.
    2. In the left navigation pane, select **Dataverse \> Connections**.
    3. Connect to appropriate instances of the following items:

        - Dynamics 365
        - Dynamics 365 for Fin & Ops

4. Open the [Power Apps environments](https://admin.powerapps.com/environments), and follow these steps:

    1. Select **Data integration**.
    2. Select **Connection sets**.
    3. Select **New connection set**.
    4. Enter a name for the connection.
    5. Select the appropriate connections for the following items:

        - Dynamics 365
        - Dynamics 365 for Fin & Ops

    6. Select the appropriate organization mapping.
    7. Select **Create**.

5. Open the [Power Apps environments](https://admin.powerapps.com/environments), and follow these steps:  

    1. Create a single data integration project for each of the following templates by using the connection set that you just created:

        - Customer payment insights result (CDS to Fin and Ops 10.0.17+)
        - Cash flow time series results (CDS to Fin and Ops)
        - Budget time series results (CDS to Fin and Ops)

      > [!NOTE]
      > Creating multiple data integration projects for each template may cause errors that will block the updates.

    2. Set the appropriate scheduling for each project.

> [!NOTE]
> If you don't see the required entities in Dataverse, go to **Credit and collections** > **Setup** > **Finance Insights** > **Finance insights parameters**, enable the feature, **Customer payment predictions**, and then select **Create prediction model**. When the deployment of AI model is complete, the Dataverse entities needed to create integration will be deployed.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
