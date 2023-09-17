---
title: Manage activation accounts and validate devices
description: This article explains how an IT Pro can set up Commerce activation accounts for workers to activate Store Commerce devices.
author: josaw1
ms.date: 02/03/2023
ms.topic: article
ms.prod: 
ms.technology: 
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

[!include [banner](includes/banner.md)]

This article explains how an IT Pro can set up Commerce activation accounts for workers to activate Store Commerce devices.

## Setting up a device activation account for a single worker

This procedure should be completed before you activate Store Commerce for web.

1. In Commerce, from the **Workers** page, open the **Worker details** page for the worker to assign Azure Active Directory (Azure AD) device activation privileges to. Select **Edit**.
2. On the **Commerce** tab, select the **POS permissions** link. Make sure that the worker is in the Manager Permission group, or that **Manage Devices** is set to **Yes** for the worker.
3. On the **Commerce** tab, under **External identity**, update the values for the following fields:

    - Alias
    - UPN
    - External identifier

4. You can update the **External identity** fields by using an existing Azure AD account or creating a new Azure AD account. To update the fields, access the **External identity** options from the **Commerce** main menu (**Commerce \> Associate existing identity \> Commerce \> Create new identity**).
5. To use an existing Azure AD account, select **Commerce \> Associate existing identity**. In the slider, select the Azure AD account that has the correct name, and then select **OK**. The Azure AD account that is associated with that name and alias is the user's activation account for the Store Commerce app.
6. Complete and save the changes on the **Workers** page, and then refresh the page. The section that contains external identity information should be updated with the new information. The mapped Azure AD account is now your activation account for the Store Commerce app and Store Commerce for web. This account is mapped to a worker for the required POS permissions. You can use this Azure AD account for Store Commerce app and Store Commerce for web activation.
7. The Create external identity feature creates a new Azure AD account for you by using the alias that you enter. To update the fields, access the **External identity** options from the **Commerce** main menu (**Commerce \> Create new identity**).
8. You can either manually enter the alias to generate or use the **Reset to default** button. Then manually enter a strong password, and select **OK**.
9. If the worker is created successfully, you receive a message on the **Workers** page. The mapped Azure AD account is now the user's activation account for the Store Commerce app and Store Commerce for web. This account is mapped to a worker for the required POS permissions. You can use this Azure AD account for Store Commerce app or Store Commerce for web activation.

## Setting up device activation accounts for multiple workers

You can set up activation accounts for multiple workers in bulk. However, this functionality is supported only if you're creating new external identities, not if you're associating identities.

1. In the workers form, select the list of workers to set the activation account for.
2. Select **Commerce \> Create external identity** to update the fields. Any Azure AD accounts that are associated with the workers appear in this pane.

    > [!NOTE]
    > These accounts aren't device activation accounts until you map them by using the external identity flow options.

3. If you want to use the existing Azure AD accounts as activation accounts, you can't map them in bulk. Cancel the selection of those workers, and then map them individually by using **Use existing external identity**.
4. To create new Azure AD accounts and associate them with the workers, so that they can be used as activation accounts, update the **Alias** and **Password** fields, and then select **OK**. In the main worker form, you receive a message as activation accounts are created for each worker.

## Run the Validate Devices for activation check at headquarters

Before handing an activation account to a worker, an IT Pro must run the Validate devices check for the devices assigned to the worker. This will help identify any potential failures of device activation in advance and fix it before it is given to the worker.

1. Open the **Device** page in HQ (**Retail and Commerce \> Channel setup \> POS setup \> Devices**).
2. Select the device to validate for device activation, and then select **Validate devices for activation**. For example, select device **HOUSTON-2**.
3. In the dialog box that appears, select the worker to validate the device for (that is, the worker that you mapped to the Azure AD account in the previous procedure). For example, select worker **000160**.
4. Select **OK**, and make sure that you receive a message similar to the following: "Pre-Activation validation completed for Device HOUSTON-2 and Staff 000160. Validation: Passed"

## Checklist to follow before activation

1. Complete the **Validate devices for activation** check in HQ, and make sure that the device passes validation.
2. On the client machine where you're activating the device, access the Commerce Scale Unit URL health check, and make sure that the health check is passed. Use the following format: `https://clxtestax404ret.cloud.test.dynamics.com/en/healthcheck?testname=ping`
3. The worker must be mapped to an Azure AD account (under **External identity**).
4. The Azure AD account to map must belong to the same tenant.
5. To map the worker to the Azure AD account, sign in to HQ by using the Admin account for Microsoft Dynamics Lifecycle Services (LCS).
6. Make sure that the worker is set up as a Commerce user in the Manager role (checked by validation).
7. Make sure that the channel data is present in the channel database.
8. Set up the hardware profile under **Registers \> Register** (checked by validation).
9. Make sure that the register and store have a screen layout (checked by validation).
10. Make sure that a primary address is set up for the legal entity.
11. Make sure that the electronic funds transfer (EFT) configuration value is present.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
