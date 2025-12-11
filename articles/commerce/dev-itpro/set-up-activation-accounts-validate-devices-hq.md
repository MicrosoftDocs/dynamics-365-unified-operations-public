---
title: Manage activation accounts and validate devices
description: This article explains how an IT Pro can set up Commerce activation accounts for workers to activate Store Commerce devices.
author: josaw1
ms.date: 06/27/2025
ms.topic: how-to
audience: IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update
ms.assetid: 5394e10c-539c-4e26-a097-504c6950cd56
ms.search.industry: Retail
ms.search.form: HcmWorker, RetailDeviceActivationValidation, RetailPositionPosPermission
---

# Manage activation accounts and validate devices

[!include [banner](../includes/banner.md)]
> [!WARNING]
> Due to security compliance, the feature **Commerce \> Create new identity** was deprecated in release 10.0.44 (PU68).
> 
> New users should be created directly through Microsoft Entra ID's [new user workflow](https://entra.microsoft.com/#view/Microsoft_AAD_UsersAndTenants/CreateUser.ReactView).

This article explains how an IT Pro can set up Commerce activation accounts for workers to activate Store Commerce devices.

## Setting up a device activation account for a single worker

This procedure should be completed before you activate Store Commerce for web.

1. In Commerce, from the **Workers** page, open the **Worker details** page for the worker to assign Microsoft Entra device activation privileges to. Select **Edit**.
2. On the **Commerce** tab, select the **POS permissions** link. Make sure that the worker is in the Manager Permission group, or that **Manage Devices** is set to **Yes** for the worker.
3. On the **Commerce** tab, under **External identity**, update the values for the following fields:

    - Alias
    - UPN
    - External identifier

4. To use an existing Microsoft Entra account, select **Commerce \> Associate existing identity**. In the slider, select the Microsoft Entra account that has the correct name, and then select **OK**. The Microsoft Entra account that’s associated with that name and alias is the user's activation account for the Store Commerce app.
5. Complete and save the changes on the **Workers** page and then refresh the page. The section that contains external identity information should be updated with the new information. The mapped Microsoft Entra account is now your activation account for the Store Commerce app and Store Commerce for web. This account is mapped to a worker for the required POS permissions. You can use this Microsoft Entra account for Store Commerce app and Store Commerce for web activation.
6. You can either manually enter the alias to generate or use the **Reset to default** button. Then manually enter a strong password and select **OK**.
7. If the worker is created successfully, you receive a message on the **Workers** page. The mapped Microsoft Entra account is now the user's activation account for the Store Commerce app and Store Commerce for web. This account is mapped to a worker for the required POS permissions. You can use this Microsoft Entra account for Store Commerce app or Store Commerce for web activation.

## Run the Validate Devices for activation check at headquarters

Before you give an activation account to a worker, an IT Pro must run the Validate devices check for the devices assigned to the worker. This check helps identify any potential failures of device activation in advance and fix it before it's given to the worker.

1. Open the **Device** page in HQ (**Retail and Commerce \> Channel setup \> POS setup \> Devices**).
2. Select the device to validate for device activation, and then select **Validate devices for activation**. For example, select device **HOUSTON-2**.
3. In the dialog box that appears, select the worker to validate the device for (that is, the worker that you mapped to the Microsoft Entra account in the previous procedure). For example, select worker **000160**.
4. Select **OK**, and make sure that you receive a message similar to the following: "Pre-Activation validation completed for Device HOUSTON-2 and Staff 000160. Validation: Passed"

## Checklist to follow before activation

1. Complete the **Validate devices for activation** check in HQ, and make sure that the device passes validation.
2. On the client machine where you're activating the device, access the Commerce Scale Unit URL health check, and make sure that the health check is passed. Use the following format: `https://clxtestax404ret.cloud.test.dynamics.com/en/healthcheck?testname=ping`
3. The worker must be mapped to a Microsoft Entra account (under **External identity**).
4. The Microsoft Entra account to map must belong to the same tenant.
5. To map the worker to the Microsoft Entra account, sign in to HQ by using the Admin account for Microsoft Dynamics Lifecycle Services (LCS).
6. Make sure that the worker is set up as a Commerce user in the Manager role (checked by validation).
7. Make sure that the channel data is present in the channel database.
8. Set up the hardware profile under **Registers \> Register** (checked by validation).
9. Make sure that the register and store have a screen layout (checked by validation).
10. Make sure that a primary address is set up for the legal entity.
11. Make sure that the electronic funds transfer (EFT) configuration value is present.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
