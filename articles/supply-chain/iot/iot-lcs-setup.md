---
# required metadata

title: Install the IoT Intelligence add-in in LCS
description: This topic explains how to install the IoT Intelligence add-in in Microsoft Dynamics Lifecycle Services (LCS).
author: robinarh
manager: tfehr
ms.date: 07/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: 
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: 
ms.search.validFrom: 2020-04-04
ms.dyn365.ops.version: 10.0.5

---

# Install the IoT Intelligence add-in in LCS

[!include [banner](../../includes/banner.md)]

This topic explains how to install the IoT Intelligence add-in in Microsoft Dynamics Lifecycle Services (LCS). Note that add-ins cannot be installed on a demo/trial environment. Before you can install the add-in, you must [create the Azure resources](iot-azure-setup.md).

## Set up the LCS environment

1. Open LCS, and go to your Microsoft Dynamics 365 Supply Chain Management environment.
2. Scroll to the **Environment add-ins** section.
3. Select **Install a new add-in** to show the list of add-ins that have been enabled for the environment.
4. In the **Select an add-in to install** dialog box, select **IoT Intelligence**.
5. In the **Setup add-in** dialog box, provide the details of your IoT hub and Redis cache. You can find the required values in the key vault that you created in [Create Azure resources](iot-azure-setup.md).

    + **Tenant ID** – In the Azure portal, go to the key vault, and then, in the left navigation pane, select **Overview**, and copy the **Directory ID** value. Paste that value in the **Setup add-in** dialog box.
    + **IoT Event Hub-compatible endpoint Key Vault URI** – Go to the key vault, and then, in the left navigation pane, select **Overview**, and copy the **DNS name** value. Paste that value in the **Setup add-in** dialog box.
    + **IoT Event Hub-compatible endpoint secret name** – Go to the key vault, and then, in the left navigation pane, select **Secrets**, and copy the name of the secret where the event hub connection string for the IoT hub is stored. Paste that value in the **Setup add-in** dialog box.
    + **Redis cache key vault URI** – Go to the key vault, and then, in the left navigation pane, select **Overview**, and copy the **DNS name** value. Paste that value in the **Setup add-in** dialog box.
    + **Redis cache endpoint secret name** – Go to the key vault, and then, in the left navigation pane, select **Secrets**, and copy the name of the secret where the connection string for the Redis cache is stored. Paste that value in the **Setup add-in** dialog box.

6. Select the check box to accept the terms and conditions.
7. Select **Install**.
8. A message box appears that states, "Add-in has been successfully triggered for installation." Select **OK**.

LCS setup is now completed. The next step is to [set up the scenarios](iot-scenario-setup.md).

## <a id="uninstall-addin"></a>Uninstall the add-in

1. In Supply Chain Management, [disable the scenarios](iot-scenario-setup.md#how-to-disable-a-scenario).
2. In LCS, go to your Supply Chain Management environment details.
3. Scroll to the **Environment add-ins** section.
4. Select **Uninstall** for the IoT Intelligence add-in.
