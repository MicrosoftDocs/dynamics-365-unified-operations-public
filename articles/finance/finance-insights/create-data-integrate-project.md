---
# required metadata

title: Create a data integrator project (preview)
description: This topic explains how to create a data integrator project.
author: ShivamPandey-msft
ms.date: 07/16/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
ms.custom: 14151
ms.assetid: 3d43ba40-780c-459a-a66f-9a01d556e674
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2020-07-24
ms.dyn365.ops.version: AX 10.0.13

---
# Create a data integrator project (preview)

[!include [banner](../includes/banner.md)]

This topic explains how to create a data integrator project.

1. Sign in to Microsoft Dynamics 365 Finance.
2. Go to **Workspaces \> Data management**, and select **Data entities**. Wait until all the data entities have been refreshed before you move on to the next step.
3. Open the [Power Apps portal](https://make.powerapps.com/), and follow these steps:

    1. Select the appropriate environment.
    2. In the left navigation pane, select **Data \> Connections**.
    3. Connect to appropriate instances of the following items:

        - Dynamics 365
        - Dynamics 365 for Fin & Ops

4. Open the [Power Apps environments](https://admin.powerapps.com/environments), and follow these steps:

    1. Select **Data Integrator**.
    2. Select **Connection sets**.
    3. Select **New connection set**.
    4. Enter a name for the connection.
    5. Select the appropriate connections for the following items:

        - Dynamics 365
        - Dynamics 365 for Fin & Ops

    6. Select the appropriate organization mapping.
    7. Select **Create**.

5. Open the [Power Apps environments](https://admin.powerapps.com/environments), and follow these steps:  

    1. Create data integration projects for the following templates by using the connection set that you just created:

        - Customer payment insights results (CDS to Fin and Ops)
            - If you are using version 10.0.17 or later, you need to use the template named, Customer payment insights result (CDS to Fin and Ops 10.0.17+).
        - Cash flow time series results (CDS to Fin and Ops)
        - Budget time series results (CDS to Fin and Ops)

    2. Set the appropriate scheduling for each project.

> [!NOTE]
> If you do not see the required entities in CDS, please go to **Credit and collections > Setup > Finance Insights > Finance insights parameters**, enable Customer payment predictions feature and click on **Create prediction model** button. When the deployment of AI model is completed (successful or failed), the CDS entities needed to create integration will be deployed in CDS.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
