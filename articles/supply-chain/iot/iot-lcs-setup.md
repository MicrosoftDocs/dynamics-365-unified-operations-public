---
# required metadata

title: Install the IoT Intelligence add-in in LCS
description: This topic describes how to install the IoT Intelligence add-in in LCS.
author: robinarh
manager: AnnBe
ms.date: 08/16/2019
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

This topic describes how to install the IoT Intelligence add-in in Lifecycle Services (LCS). Before you can install the add-in, you must [create the Azure resources](iot-azure-setup.md).

## LCS Environment setup

1. Open Lifecycle Services (LCS) and navigate to your Supply Chain Management environment.
2. Scroll to the **Environment add-ins** section.
3. Click **Install a new add-in** to populate the list of add-ins that have been enabled for the environment.
4. In the **Select an add-in to install** dialog, click **IoT Intelligence**.
5. In the **Setup add-in** dialog, provide the details of your IoT hub and Redis cache. You can find the values that you need in the key vault you created in the [create the Azure resources](iot-azure-setup.md).
    + **Tenant ID**: In the Azure key vault, in the left navigation, click **Overview**. Copy the **Directory ID**. In the **Setup add-in** dialog, paste in the value.
    + **IoT Event Hub-compatible endpoint Key Vault URI**: In the Azure key vault, in the left navigation, click **Overview**. Copy the **DNS name**. In the **Setup add-in** dialog, paste in the value.
    + **IoT Event Hub-compatible endpoint secret name**: In the Azure key vault, in the left navigation, click **Secrets**. Copy the secret name where the IoT hub connection string is stored. In the **Setup add-in** dialog, paste in the value.
    + **Redis cache key vault URI**: In the Azure key vault, in the left navigation, click **Overview**. Copy the **DNS name**. In the **Setup add-in** dialog, paste in the value.
    + **Redis cache endpoint secret name**: In the Azure key vault, in the left navigation, click **Secrets**. Copy the secret name where the Redis cache connection string is stored. In the **Setup add-in** dialog, paste in the value.
6. Select the checkbox to accept the terms and conditions.
7. Click **Install**.
8. A dialog appears that says **Add-in has been successfully triggered for installation**. Click **OK**.

LCS setup is complete. The next step is to [setup the scenarios](iot-scenario-setup.md).

## How to uninstall the add-in

1. In Supply Chain Management, [disable the scenarios](iot-scenario-setup#how-to-disable-a-scenario.md).
2. In Lifecycle Services (LCS), navigate to your Supply Chain Management environment.
3. Scroll to the Environment add-ins section.
4. Click **Uninstall** for the IoT Intelligence add-in.
