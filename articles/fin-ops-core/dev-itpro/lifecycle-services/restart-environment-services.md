---
# required metadata

title: Restart environment services
description: This topic explains how to restart individual services in environments that are deployed through Microsoft Dynamics Lifecycle Services (LCS).
author: laneswenka
ms.date: 11/01/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global 
# ms.search.industry:
ms.author: laswenka
ms.search.validFrom: 2018-03-05
ms.dyn365.ops.version: 7.3
---

# Restart environment services

[!include [banner](../includes/banner.md)]

You can use the Restart services functionality in Microsoft Dynamics Lifecycle Services (LCS) to restart individual services that are associated with a Tier 2, Tier 3, Tier 4, or Tier 5 standard acceptance test (sandbox) environment of the **Self-service** type. You can use this functionality to restart the following services:

- AX (the whole runtime)
- DIXF (the Data import export framework service)
- MR (the Financial reporting service)

Any user who has been added as a project owner, organization admin, or environment manager in an LCS project has permissions to use this functionality.

## Restart a specific service

To restart a specific service in a deployed environment, follow these steps.

1. In LCS, open the appropriate project, and select the environment to restart the service for.
2. On the **Environment details** page, select **Maintain** &gt; **Restart services**.
3. In the **Restart a service** dialog box, select the service to restart, and then select **OK**.

    The **Environment state** value is updated when the service is restarted.

4. To view the updated status, refresh the page.

    > [!NOTE]
    > Because restart of a service might require only a few seconds, the **Environment state** value might already have been reset to **Deployed**. When the restart is completed, an entry is added to the **History** page.
    

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
