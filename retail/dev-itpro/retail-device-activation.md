---
# required metadata

title: Retail POS device activation
description: This article explains the new guided device activation for Retail Cloud POS and Retail Modern POS, and explains the client simplifications that help users easily activate devices without having to manually enter register and device ID information. 
author: MargoC
manager: AnnBe
ms date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
# ms.reviewer: robinr
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 18341
ms.assetid: 3dc4c413-e341-4d01-bc49-dc24e35dd8a7
ms.search.region: Global
# ms.search.industry: 
ms.author: athinesh
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Retail POS device activation

This article explains the new guided device activation for Retail Cloud POS and Retail Modern POS, and explains the client simplifications that help users easily activate devices without having to manually enter register and device ID information. 

Checklist to follow before activation
-------------------------------------

1.  Complete the **Validate devices for activation** check in HQ, and make sure that the device passes validation.
2.  On the client machine where you're activating the device, access the Retail Server URL health check, and make sure that the health check is passed. Use the following format: https://clxtestax404ret.cloud.test.dynamics.com/en/healthcheck?testname=ping
3.  The worker must be mapped to a Microsoft Azure Active Directory (AAD) account (under **External identity**).
4.  The AAD account to map must belong to the same tenant.
5.  To map the worker to the AAD account, sign in to HQ by using the Admin account for Microsoft Dynamics Lifecycle Services (LCS).
6.  Make sure that the worker is set up as a Dynamics 365 for Operations user in the Manager role (checked by validation).
7.  Make sure that the channel is published (checked by validation).
8.  Make sure that the channel database has the synced data from HQ, and that download jobs are running. To check this, run the following command in the channel database for the store.

        select * from crt.STORAGELOOKUPVIEW

    Make sure that data is returned, and that the result isn't empty.

9.  Set up the hardware profile under **Register** (checked by validation).
10. Make sure that the register and store have a screen layout (checked by validation).
11. Make sure that a primary address is set up for the legal entity.
12. Make sure that the language is set up for the Commerce Data Exchange: Real-time Service user profile (JBB in the demo data).
13. Make sure that the Real-time Service profile has the correct access.
14. Make sure that the electronic funds transfer (EFT) configuration value is present.

## Activate a Modern POS or Cloud POS device by using guided activation
1.  Open the initial device activation page for Modern POS or Cloud POS. You're prompted to sign in.
2.  On the **Before you start** page, follow the instructions, and then click **Next**.

    ![p24](./media/p24.png)

3.  Start Cloud POS or Modern POS.
4.  Use your AAD credentials to sign in. The AAD account must already be mapped. For instructions, see [Retail Modern POS self-service and device activation](..\retail-modern-pos-device-activation.md). For Cloud POS, the server URL is automatically entered in the address bar. For Modern POS, you must copy and paste the server URL.

    [![p18](./media/p18.png)](./media/p18.png)

5.  Click **Next** to populate the list of stores.
6.  Select the correct store in the list.

    [![p20](./media/p20.png)](./media/p20.png)

7.  Select the correct register and device. **Note:** The device can be **Pending**, **De-activated**, or **Activated**. Alternatively, if you turned on the Retail HQ **Allow devices to be associated to registers from store** setting, you might see a list of registers that have no device associated with them. 

    [![p22](./media/p22.png)](./media/p22.png)

8.  Click **Activate**. The device should be activated. 

    [![p23](./media/p23.png)](./media/p23.png)

## Create a device ID from Modern POS and Cloud POS
We have added features to create a device (that is, automatically generate a device ID) from Modern POS or Cloud POS, so that the device can be associated with a register that doesn't yet have devices mapped to it. This functionality can be used in Modern POS only if you set the HQ settings as follows.

1.  Go to **Retail and commerce** &gt; **Headquarters setup** &gt; **Parameters** &gt; **Retail shared parameters** &gt; **General**.
2.  Under **Devices,** set **Allow register association from device** to **Yes**.
3.  In the Modern POS client, you can now add a device when you select a register that is listed as **No associated devices** in the guided activation flow.
4.  After you select the register, you can either select a device that doesn't have register mapping or use the **Or, Add a Device** link.
5.  Click the **Or, Add a Device** link, and then either enter the new device ID or select **Automatically create a new device ID for me**.
6.  Click **Activate** to create a new device ID, associate it with the selected register, and complete the activation.

## Activate the device for Modern POS by using a configuration file
IT Pros can now easily configure device activation for Modern POS by using a configuration file that can be downloaded together with Modern POS. This file is now available on the **Devices** page for the appropriate Modern POS device (**Retail and commerce** &gt; **Channel setup** &gt; **POS setup** &gt; **Devices**). 

[![Configuration file download](./media/p16_11_16-1024x481.png)](./media/p16_11_16.png) 

The configuration file is used to enter the Retail Server URL, device ID, and register number for device activation. During installation, the installer selects this file and populates the values for device activation. **Important:** The user must put the file in the same folder as the Modern POS self-service package and run the .exe file. 

[![Configuration file](./media/p17_11_16-1024x532.png)](./media/p17_11_16.png) 

Modern POS starts in Manual entry mode, and the Retail Server URL, device ID, and register ID are pre-populated for activation.

## Activate the device for Cloud POS by using syntactic sugar
IT Pros can now configure device activation for Cloud POS by providing the device ID and register ID as the part of the Cloud POS URL. The link is available in the **Cloud POS URL** field on the **Devices** page. (**Retail and commerce** &gt; **Channel setup** &gt; **POS setup** &gt; **Devices**). 

[![Cloud POS URL field](./media/p15_11_16.png)](./media/p15_11_16.png) 

Cloud POS starts in Manual entry mode, and the Retail Server URL, device ID, and register ID are pre-populated for activation.

