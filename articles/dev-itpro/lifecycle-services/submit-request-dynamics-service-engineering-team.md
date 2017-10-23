---
# required metadata

title: Submit a request to the Dynamics Service Engineering team
description: You can submit requests directly to the Dynamics Service Engineering team by using LCS. 
author: manalidongre
manager: AnnBe
ms.date: 08/29/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations, Platform, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 254564
ms.assetid: 43ea0eae-34c8-4f97-8c98-c711844534d9
ms.search.region: Global
# ms.search.industry: 
ms.author: manado
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Platform update 3

---

# Submit a request to the Dynamics Service Engineering team

[!include[banner](../includes/banner.md)]

You can now submit requests directly to the Dynamics Service Engineering (DSE) team by using Lifecycle Services (LCS) instead of using Connect or LCS, depending on the request. This functionality, which was added in the September release of LCS, allows you to submit requests using a single portal and view the status of your requests in LCS. You can also audit which requests are submitted and executed on your environment. There are two ways to submit a request.

-   On the project dashboard, in the **Environments** pane, select **Service requests**. [![request-submission-01](https://msdnshared.blob.core.windows.net/media/2016/11/Request-submission-01-1024x509.png)](https://msdnshared.blob.core.windows.net/media/2016/11/Request-submission-01.png)
-   On the LCS menu, click **Support**, and on the **Work items** page, select the **Service requests** tab. [![request-submission-02](https://msdnshared.blob.core.windows.net/media/2016/11/Request-submission-02.png)](https://msdnshared.blob.core.windows.net/media/2016/11/Request-submission-02.png)

The following request types are supported by this functionality:

-   **Other requests** – This includes requests other than those listed above or automated flow requests. For example, you might use this request type for upgrade or to request the system be put into maintenance mode. Note, this should not be used to submit support requests.
-   **Package application** – To apply a package to the production environment, on the **Environment details** page, click **Maintain** to select the package to apply, and then select **Schedule**.
-   **Environment deployment** – To set the deployment options and submit a request to the Dynamics Service Engineering team to deploy a new environment, click **Configure** on the **Environments** pane.
-   **Database point-in-time restore** – This includes, for example, restoring a non-production database to a specific point in time.
-   **Database refresh** – This includes, for example, the ability to refresh a database from production to sandbox. 
