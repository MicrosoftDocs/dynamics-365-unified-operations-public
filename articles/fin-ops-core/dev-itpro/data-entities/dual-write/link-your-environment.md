---

title: "How to use the dual-write wizard to link your environments"
description: Describes how to use the dual-write wizard to link the Finance and Operation app environment to your Common Data Service environment.
author: sabinn-msft

ms.technology: 
ms.topic: conceptual
ms.date: 03/20/2020
ms.author: v-douklo

LocalizationGroup: 
---

# How-to use the dual-write wizard to link your environments

[!include [banner](../../includes/banner.md)]

[!include [banner](../../includes/preview-banner.md)]

1. Sign in to the Finance and Operation app environment that you want to link to your Common Data Service environment, select **Data Management**, and then select the **Dual Write** tile.

    <kbd>![Navigating to data management](media/navigate-to-data-management.png)

2. Select the **New link to environment** button to link your Finance and Operations app and the Common Data Service environments.

3. At this point, the Common Data Service environments are automatically fetched for the logged-in user, where user is an environment admin. Once the environments are discovered, under the **Choose environment** step, select the Common Data Service environment that you want to link to, and then select **Next**.

    <kbd>![Selecting the common data service environment](media/data-service-environment.png)

4. Choose your legal entities and select **Next**.

    <kbd>![Selecting your legal entities](media/select-legal-entities.png)

5. At this point, a Health check is run to make sure that your system meets the requirements to enable dual-write and all the prerequisites are complete.

    <kbd>![Running a health check](media/health-check.png)

    If any of the health checks fails, ensure that you've completed all the prerequisites before you move to the next step.

    In this example, the health check shows that the check for granting access to connect the apps failed. First, you'll need to grant the access to connect the apps by the creating the respective application IDs, and then rerun the dual-write wizard. 

6. Review the summary and privacy notice and consent, and then select **Create**.

7. That's it&mdash;you've just linked your Finance and Operations app to the Common Data Service environment. The next step is to enable entity maps for dual-write.

    <kbd>![Linking entity maps successful](media/entity-maps-linked.png)

   >[!Note]
   >If you don't see your entity maps or see a blank screen, make sure to install the Finance and Operations app entity map solution.

## Next steps

[Enable entity map for dual-write](enable-entity-map.md)

