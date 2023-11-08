---
# required metadata

title: Configurationm instructions for Copilot for generative help and guidance
description: This article provides instructins for administrators on how to enable Copilot for generative help and guidance in the finance and operations platform
author: cabeln
ms.date: 11/07/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: EventCreateRule
# ROBOTS:
audience: Application user
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom:
ms.search.region: Global
# ms.search.industry:
ms.author: richdi
ms.search.validFrom: 2023-11-15
ms.dyn365.ops.version: Platform update 62
---

# Enable *Microsoft Copilot for generative help and guidance* on your Dynamics 365 finance and operations environment 

The **Copilot for generative help and guidance** helps users by providing in-app help guidance with the help of the power of generative AI.

> [!IMPORTANT]
> The Microsoft Copilot functionality in this article is available as part of a preview release. For more information about preview releases, see [One version service updates FAQ](/dynamics365/unified-operations/fin-and-ops/get-started/one-version).
>
> To learn about the capabilities and limitations of AI-powered and Copilot features see [Responsible AI FAQs for Dynamics 365 finance and operations platform](../../dev-itpro/responsible-ai/responsible-ai-overview.md).

> [!NOTE]
> During the preview phase, the Copilot application can only be installed for environments on tenants that are hosted in the US.

## Enable the feature for your system

This section describes the steps that you must complete to enable the **Copilot for generative help and guidance**.

### Prerequisites: Your Supply Chain Management environment and connection to Data Verse 
To install the preview build must be running Supply Chain Management 10.0.37 or later and have enabled the Power Platform integration in LCS. (It is not required to enambe Dual-Write for this feature.)


### Step 1: Upgrade Supply Chain Management to the required build

This feature is available in public preview in build 10.0.38. You can install the preview build on an environment Supply Chain Management 10.0.37 or later and add the latest PEAP preview build for build 10.0.38.

in LCS navigate to the Project Level asset library. Click *Import* and select the build 10.0.38 from the list in the shared asset library. This will import the 10.0.38 PEAP build into your Project Asset library. 
Once available you can deploy it using *Apply update* on your environment. 

Find more information about availability and using [early access build](dynamics365/get-started/release-schedule#early-access---frequently-asked-questions).


### <a name="enable-sql-key"></a>Step 2: Enable the SQL row version change tracking license key

Follow these steps to check the status of the **Sql row version change tracking (Preview)** license key and enable it if necessary. If the key isn't enabled, you'll get an error when you try to install the Copilot application in the Power Platform admin center.

1. Go to **System administration \> Setup \> License configuration**.
1. On the **Configuration keys** tab, scroll down the **Sql row version change tracking (Preview)** key. If the key is already enabled, then skip the rest of this procedure. If it isn't enabled, then continue to the next step.
1. Put your system into maintenance mode, as described in [Maintenance mode](../sysadmin/maintenance-mode.md).
1. Return to the **License configuration** and enable the **Sql row version change tracking (Preview)** key.
1. Turn off maintenance mode, as described in [Maintenance mode](../sysadmin/maintenance-mode.md).

### Step 3: Enable Supply Chain Management to access your Dataverse environment

Follow these steps to enable Supply Chain Management to access your Dataverse environment.

1. Go to [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
1. Select the Dataverse environment that's connected to your Supply Chain Management environment, and open the detail view.
1. Select the **Settings** menu on the menu bar.
1. Go to **Product \> Features**.
1. Set the **Finance and Operations in Dataverse** option to *On*.

### Step 4: Install the Copilot application in Supply Chain Management

> [!NOTE]
> During the preview phase, the Copilot application can only be installed for environments on tenants that are hosted in the US.

Follow these steps to install the Copilot application in your Supply Chain Management environment.

1. Go to the [Copilot in Microsoft Dynamics 365 Supply Chain Management](https://appsource.microsoft.com/product/dynamics-365/mscrm.dynamicsscmai-preview?flightCodes=f42a7338c806438f8fca820c4ed82b7c&tab=Overview) page in the Microsoft commercial marketplace.
1. Select **Get it now**.
1. The deployment process opens [Power Platform admin center](https://admin.powerplatform.microsoft.com/). Select the Dataverse environment that's connected to your Supply Chain Management environment to install the Copilot application.

    > [!IMPORTANT]
    > **Troubleshooting:** You may see the following error message while installing the Copilot application in the Power Platform admin center: "Unable to complete updates to the Track changes option for table: 'EcoResProductTranslationAIEntity'. Exception details: This functionality requires enabling sql row version change tracking feature. Please enable SQL Row version configuration key." If you see this error, follow the instructions given in [Step 3: Enable the SQL row version change tracking license key](#enable-sql-key).

1. You can follow the status of the installation by opening the detail view of the environment. In the **Resources** field, select **Dynamics 365 apps**. The status of the Copilot application is **Installing**. After the installation is complete, the status changes to **Installed**. If an error occurs, the status changes to **Failed** and you can find details about the error in the **Notifications** field.

### Step 5: Enable the required security roles

Users who should have access to the functionality must be assigned the *AIB Roles* and *Finance and Operations AI* security roles in Dataverse.

In the detail view of the environment, in the **Access** field, select **Users** or **Teams**. Select the users or teams that should have access, and assign the *AIB Roles* and *Finance and Operations AI* security roles to them.


### Step 6: Enable the workspace feature in Feature management

In the [**Feature management**](../../fin-ops/get-started/feature-management/feature-management-overview.md) workspace, turn on the feature that's named *(Preview) User experience for Copilot in Finance and Operations*. As of Supply Chain Management version 10.0.36, this feature is turned on by default.

