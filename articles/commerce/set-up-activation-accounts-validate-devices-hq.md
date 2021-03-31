---
# required metadata

title: Manage activation accounts and validate devices
description: This topic explains how an IT Pro can set up Commerce activation accounts for workers to activate Modern POS or Cloud POS devices.
author: athinesh99
ms.date: 07/15/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: HcmWorker, RetailDeviceActivationValidation, RetailPositionPosPermission
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 20471
ms.assetid: 5394e10c-539c-4e26-a097-504c6950cd56
ms.search.region: Global
ms.search.industry: Retail

ms.author: athinesh
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update

---

# Manage activation accounts and validate devices

[!include [banner](includes/banner.md)]

This topic explains how an IT Pro can set up Commerce activation accounts for workers to activate Modern POS or Cloud POS devices.

## Setting up a device activation account for a single worker

This procedure should be completed before you activate Cloud POS.

1. In Commerce, from the **Workers** page, open the **Worker details** page for the worker to assign AAD device activation privileges to. Click **Edit**.
2. On the **Commerce** tab, click the **POS permissions** link. Make sure that the worker is in the Manager Permission group, or that **Manage Devices** is set to **Yes** for the worker.
3. On the **Commerce** tab, under **External identity**, update the values for the following fields:

    - Alias
    - UPN
    - External identifier

4. You can update the **External identity** fields by using an existing AAD account or creating a new AAD account. To update the fields, access the **External identity** options from the **Commerce** main menu (**Commerce** &gt; **Associate existing identity** or **Commerce** &gt; **Create new identity**).
5. To use an existing AAD account, select **Commerce** &gt; **Associate existing identity**. In the slider, click the AAD account that has the correct name, and then click **OK**. The AAD account that is associated with that name and alias is the user's Activation account for Modern POS.
6. Complete and save the changes on the **Workers** page, and then refresh the page. The section that contains external identity information should be updated with the new information. The mapped AAD account is now your Activation account for Cloud POS and Modern POS. This account is mapped to a worker for the required POS permissions. You can use this AAD account for Modern POS or Cloud POS activation.
7. The Create external identity feature creates a new AAD account for you by using the alias that you enter. To update the fields, access the **External identity** options from the **Commerce** main menu (**Commerce** &gt; **Create new identity**).
8. You can either manually enter the alias to generate or use the **Reset to default** button. Then manually enter a strong password, and click **OK**.
9. If the worker is created successfully, you receive a message on the **Workers** page. The mapped AAD account is now the user's Activation account for Cloud POS and Modern POS. This account is mapped to a worker for the required POS permissions. You can use this AAD account for Modern POS or Cloud POS activation.

## Setting up device activation accounts for multiple workers

You can set up activation accounts for multiple workers in bulk. However, this functionality is supported only if you're creating new external identities, not if you're associating identities.

1. In the workers form, select the list of workers to set the activation account for.
2. Click **Commerce** &gt; **Create external identity** to update the fields. Any AAD accounts that are associated with the workers appear in this pane.

    > [!NOTE]
    > These accounts aren't device activation accounts until you map them by using the external identity flow options.

3. If you want to use the existing AAD accounts as activation accounts, you can't map them in bulk. Cancel the selection of those workers, and then map them individually by using **Use existing external identity**.
4. To create new AAD accounts and associate them with the workers, so that they can be used as activation accounts, update the **Alias** and **Password** fields, and then click **OK**. In the main worker form, you receive a message as activation accounts are created for each worker.

## Run the Validate Devices for Activation check at headquarters

Before handing an activation account to a worker, an IT Pro must run the Validate devices check for the devices assigned to the worker. This will help identify any potential failures of device activation in advance and fix it before it is given to the worker.

1. Open the **Device** page in HQ (**Retail and commerce** &gt; **Channel setup** &gt; **POS setup** &gt; **Devices**).
2. Select the device to validate for device activation, and then click **Validate devices for activation**. For example, select device **HOUSTON-2**.
3. In the dialog box that appears, select the worker to validate the device for (that is, the worker that you mapped to the AAD account in the previous procedure). For example, select worker **000160**.
4. Click **OK**, and make sure that you receive a message similar to the following: "Pre-Activation validation completed for Device HOUSTON-2 and Staff 000160. Validation: Passed"

## Checklist to follow before activation

1. Complete the **Validate devices for activation** check in HQ, and make sure that the device passes validation.
2. On the client machine where you're activating the device, access the Commerce Scale Unit URL health check, and make sure that the health check is passed. Use the following format: `https://clxtestax404ret.cloud.test.dynamics.com/en/healthcheck?testname=ping`
3. The worker must be mapped to an AAD account (under **External identity**).
4. The AAD account to map must belong to the same tenant.
5. To map the worker to the AAD account, sign in to HQ by using the Admin account for Microsoft Dynamics Lifecycle Services (LCS).
6. Make sure that the worker is set up as a Commerce user in the Manager role (checked by validation).
7. Make sure that the channel data is present in the channel database.
8. Set up the hardware profile under **Registers** &gt; **Register** (checked by validation).
9. Make sure that the register and store have a screen layout (checked by validation).
10. Make sure that a primary address is set up for the legal entity.
11. Make sure that the electronic funds transfer (EFT) configuration value is present.


[!INCLUDE[footer-include](../includes/footer-banner.md)]