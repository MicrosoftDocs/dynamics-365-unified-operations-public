---
title: Reset button functionality
description: This article describes the reset button functionality of dual-write
author: ramasri
ms.date: 12/12/2022
ms.topic: article
audience: Administrator
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: ramasri
ms.search.validFrom: 12/12/2022
ms.dyn365.ops.version: F&O 10.0.30 PU54
---


# Reset functionality

Today, you do "Link" and "Unlink" dual-write connection between Finance and Operations applications and Dataverse when you either want to wipe out the configuration and start from scratch or you encounter a stuck state. During this process, most of the time you end up choosing a different dataverse organization by mistake resulting in data corruption. In order to avoid this mistake, we are removing these buttons from dual-write administration UI inside Finance and Operations applications starting 10.0.30 PU54. All dual-write connections will take place from LCS using the power platform integration setup. In addition to it, we are introducing a new "Reset" button on dual-write administration UI which will help you to refresh the connection as necessary without changing the underlying dataverse organization id.

# Pre-requisites

- You must have Finance and Operations version 10.0.30 PU54 and above to see the "Reset" button.
- You must stop all dual-write maps before clicking on "Reset" button.

# What does the reset button do? 

When you click on Reset button, dual-write service does the following things at the backend:

- Clears out all dual-write runtime configuration data from the following tables

Finance and Operations tables namely

    - DualWriteProjectConfiguration
    - DualWriteProjectFieldConfiguration
    - BusinessEventsDefinition

Dataverse table namely

    - Dual Write Runtime Configurations

- Wipes out all dual-write maps including their metadata like integration keys, filters, status etc., static data like legal entities configured for dual-write, default settings and transformations on map etc., and runtime data like activity logs, version history etc.

- Restores the dual-write connection set between F&O and Dataverse from power platform integration setup.

Post reset, you need to apply the required solutions using "Apply Solution" functionality to bring the maps and start over from scratch. So, unless you are sure about resetting dual-write, please don't click this button.

# Reset scenarios

Based on your Finance and Operations environment type (production/sandbox/cloud hosted) and its status of the power platform integration setup, you will be experiencing a slight variation when you click on Reset button. These variations are detailed as follows:

**Scenario #1:** The dataverse organization id used by dual-write is the one setup for power platform integration.

Clicking "Reset" button shows the following window with environment details displayed for your reference.

![reset-image-1](media/reset-image-1.png)

- By choosing the "Acknowledge Reset" checkbox, you are acknowledging to reset the dual-write configuration setup.
- By choosing the "Force Reset" checkbox, you are asking to stop any maps in running state before initiating reset. We have restored this checkbox and associated behavior from the "Unlink" functionality for familarity reasons.
- Click Next to proceed further
- On "Select legal entities" screen, please select the legal entities to which you wish to reset your dual-write connection. By default, none will be selected.
- After selecting the legal entities, click Next will take you to "Health check" screen followed by summary screen.

In case, before clicking the Reset button you forgot to stop the running dual-write maps and also inside the "Reset" screen you forgot to select the "Force Reset" checkbox, your reset action will fail with a "Failed" message as shown below:

![reset-image-2](media/reset-image-2.png)

**Scenario #2:** The dataverse organization id used by dual-write is different from the one setup for power platform integration.

Clicking "Reset" button shows the following window with **Current Dataverse Environment** and **Power Platform Linked Dataverse Environment** as shown below.

![reset-image-3](media/reset-image-3.png)

The **Current Dataverse Environment** refers to the dataverse database associated with your dual-write connection. **Power Platform Link Dataverse Environment** refers to the dataverse database associated with your Finance and Operations environment's power platform integration setup. As you can see, both are different.

Similar to scenario #1, you should choose "Acknowledge Reset" and "Force Reset" checkboxes before clicking the Next button.

Since the dataverse databases are different, clicking the Next button will replace the **Current Dataverse Environment** with thedataverse database mentioned under **Power Platform Link Dataverse Environment.** If you'd like to continue dual-write with the dataverse database mentioned under **Current Dataverse Environment** and the environment type is production, then you should cancel the reset action by clicking the "Cancel" button. Raise a support case with Microsoft by referring to ICM 349669515 and we will help you with the replacement.

> [!Note] 
> Backend replacement through Microsoft support cases is facilitated only for Finance and Operations production environments. Not for other types of environments.

Similar to scenario #1, clicking next will allow you to choose the legal entities to which you wish to reset your dual-write connection followed by Health check and Summary screens. In case one or more table maps are in running state and you forgot to stop them before reset and you also forgot to select "Force Reset" checkbox, then your reset action will fail with a "Failed" message.

**Scenario #3:** Your power platform integration setup is blank and doesn't have a dataverse organization id configured

Clicking "Reset" button shows the following window with current environment details displayed for your reference.

![reset-image-4](media/reset-image-4.png)

In this case, please go to [Power Platform Integration](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Flearn.microsoft.com%2Fen-us%2Fdynamics365%2Ffin-ops-core%2Fdev-itpro%2Fpower-platform%2Fenable-power-platform-integration%23connect-to-existing-dataverse&data=05%7C01%7Cramasri%40microsoft.com%7C2f8fe7106138411f6c0408daa369b317%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C638001971624185428%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C3000%7C%7C%7C&sdata=8xwIg39VdzXXtcBzETMbH1%2F%2BzCBIkSUVyomsPLRbHtE%3D&reserved=0) and choose **Current Dataverse Environment** as the Power Platform Environment ID and Save changes. After completing it, you can re-initiate the reset action.

**Scenario #4:** You are using cloud hosted instance of Finance and Operations applications

Clicking "Reset" button shows the following window with environment details displayed for your reference.

![reset-image-5](media/reset-image-5.png)

The **Current Dataverse Environment** refers to the database associated with dual-write connection. Since there will not be any power platform integration setup, reset functionality will refresh the displayed dual-write connection set as-is. In case you wish to associate the finance and operations environment with a different dataverse organization, then you need to redeploy Finance and Operations environment.

Similar to scenario #1, you should choose "Acknowledge Reset" and "Force Reset" checkboxes and click the Next button. On the "Select legal entities" screen you should select the legal entities to which you wish to reset your dual-write connection followed by Health check and Summary screens. In case one or more table maps are in running state and you forgot to stop them before reset and you also forgot to select "Force Reset" checkbox, then your reset action will fail with a "Failed" message.
