---
# required metadata

title: Enable Microsoft Power Platform integration
description: This topic explains how to enable Microsoft Power Platform integration using Lifecycle Services for Finance and Operations apps and Dataverse.
author: jaredha
ms.date: 10/18/2021
ms.topic: article
ms.prod:
ms.technology: 

# optional metadata

# ms.search.form:
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: "intro-internal"
ms.search.region: Global
# ms.search.industry:
ms.author: jaredha
ms.search.validFrom: 2021-10-13
ms.dyn365.ops.version: 10.0.0
---
# Enable Microsoft Power Platform integration

[!include[banner](../includes/banner.md)]

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

The Dynamics 365 Finance and Operations apps integration with Microsoft Power Platform can be enabled when you create a new Finance and Operations apps environment in Microsoft Lifecycle Services (LCS). Alternatively, Microsoft Power Platform can be enabled in an existing Finance and Operations apps environment. For both options, you must complete the prerequisite setup.

## Prerequisites for setting up Microsoft Power Platform integration

The following list provides prerequisite details to set up Microsoft Power Platform integration.

- Make sure that at least one gigabyte (GB) of Microsoft Power Platform database storage capacity space is available for your tenant. If this space isn't available, the setup will fail. View your capacity in the [Power Platform admin center](https://admin.powerplatform.microsoft.com/resources/capacity). 

- Identify your Finance and Operations apps environment administrator. You can find that information in the **Environment details** section.

    ![Environment details tab.](media/EnvironmentDetails.png)

- Validate your Microsoft Power Platform environment governance policy. To validate, you must be a **Global administrator** or **Power Platform administrator**.

    1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com).
    2. Select **Settings** in the upper-right corner of the page to open the **Power Platform settings** pane.

        ![Power Platform settings pane.](media/PowerPlatformSettings.png)

- For organizations that **do not allow everyone** to create Microsoft Power Platform production environments, the Finance and Operations apps environment administrator account for your environment must be added to one of the following Microsoft Power Platform admin roles. To make this change, you must be a **Global Administrator**.

    - Global admins
    - Dynamics 365 admins
    - Microsoft Power Platform admins

    > [!NOTE]
    > The preceding roles might provide more permissions than the Finance and Operations apps administrator account requires. Therefore, a more limited role for this integration will eventually be added to Azure Active Directory (Azure AD). The new role won't require any of the preceding roles. If you want to keep the administrator that has the least privileges, you can temporarily grant one of the preceding roles. Then, after the Microsoft Power Platform integration is set up, remove that role.

- All users who create Microsoft Power Platform environments must be licensed. The Microsoft 365 admin center should be used to apply the **Dynamics 365 Unified Operations Plan**, **AX Enterprise** license, or an application-specific license such as **Dynamics 365 Finance**, to the Finance and Operations apps environment administrator account.

## <a name="enable-during-deploy"></a>Enable during environment deployment

When you set up a new Finance and Operations apps environment in LCS, the deployment wizard includes several sections where you can set values. One of those sections is named **Power Platform Integration**.

![Power Platform Integration section in the deployment wizard.](media/powerplat_integration_step0.png)

Complete the following steps to configure the **Power Platform Integration** section.

1. Set the **Configure Power Platform Environment** option to **Yes**. Several additional settings become available.
2. In the **Power Platform template** field, select one of the following values:

    - **Dynamics 365 Standard**: This basic template is applicable to all Finance and Operations apps environments. Select this value if you don't require a more specific template.
    - **Project Operations**: This template is specific to the Dynamics 365 Project Operations scenario. This value is available only if your tenant has licenses and entitlement for Project Operations.

3. If you're deploying a DevTest or cloud-hosted environment, the **Environment Type** field is available. You can select the type of Dataverse environment that is created and linked. Otherwise, by default, the environment type is set to **Sandbox** for Tier 2 through Tier 5 acceptance test environments and **Production** for production environments.
4. Select **Agree** to agree to the terms and conditions of the integration.

> [!IMPORTANT]
> The **language** and **currency** values of the Dataverse environment that's created and linked to your Finance and Operations apps environment are automatically determined, based on the physical address of your Azure AD tenant. For example, if the address is in Redmond, Washington, USA, the language will be English by default, and the currency will be US dollars (USD).
>
> If you require values that differ from the default values, contact Microsoft support. We can help link an existing Dataverse environment that you manually provision to the Finance and Operations apps environment. Eventually, fields for the language and currency will be added as setup options, so that you can manually set them or accept the default values.

## <a name="enable-after-deploy"></a>Enable after environment deployment

If the Power Platform integration isn't enabled during the deployment of the Finance and Operations apps environment, you can enable the integration in LCS after deployment. To set up after the Finance and Operations apps environment has been deployed, complete the following steps.

1. After the Finance and Operationsapps environment has been deployed through LCS, open the **Environment details** page in LCS.
2. In the **Power Platform integration** section, select **Setup**.

    ![Setup button in the Power Platform Integration section.](media/powerplat_integration_step1.png) 

3. In the **Power Platform environment setup** dialog box, agree to the terms and conditions, and then select **Setup** at the bottom of the dialog box.

    > [!NOTE]
    > A Microsoft Dataverse-based environment will now be provisioned in the Power Platform admin center. The environment typically requires 1GB of database storage capacity and will have the same name as your Finance and Operations apps environment. Dual-write platform-level components will be installed, but dual-write application components will not be set up or enabled. That is a separate action.

4. When you receive a message that states that the Microsoft Power Platform environment is being provisioned, select **OK**.

    The **Power Platform integration** section of the **Environment details** page now shows a message that states that the Microsoft Power Platform environment is being provisioned.

5. After a few minutes, refresh the **Environment details** page.
6. In the **Power Platform integration** section, notice that the value of the **Status** field is **Environment setup is in progress**.

    Typically, the setup takes between 60 and 90 minutes.

    After the Dataverse environment is provisioned, the **Install a new add-in** and the **Dual-write application** buttons become available in the **Power Platform integration** section.

    ![Install a new add-in button.](media/InstallANewAddIn.png)

    ![Dual-write application button.](media/powerplat_integration_dwApp_button.png)

> [!IMPORTANT]
> The **language** and **currency** values of the Dataverse environment that is created and linked to your Finance and Operations apps environment are automatically determined, based on the physical address of your Azure AD tenant. For example, if that address is in Redmond, Washington, USA, the language will be English by default, and the currency will be US dollars (USD).
>
> If you require values that differ from the default values, contact Microsoft support. We can help link an existing Dataverse environment that you manually provision to the Finance and Operations apps environment. Eventually, fields for the language and currency will be added as setup options, so that you can manually set them or accept the default values.

## Enable integration with an existing Microsoft Power Platform environment

When you enable Microsoft Power Platform integration for a Finance and Operations apps environment in LCS, either during or after deployment, the process creates a new Dataverse-enabled Microsoft Power Platform environment, and links the Finance and Operations apps environment to the new Microsoft Power Platform environment. However, you may want to enable the integration by linking your Finance and Operations apps environment to an existing Microsoft Power Platform environment. The option to enable the integration with an existing Microsoft Power Platform environment isn't currently available in LCS. Work with the Microsoft engineering team to enable the integration with an existing Power Platform environment.

There are two scenarios for enabling ntegration with an existing Microsoft Power Platform environment

- A known, connected Microsoft Power Platform environemnt is already defined by dual-write configurations.
- No existing connected Microsoft Power Platform environment is identified.

### Enabling the integration for already-connected environments

If the Finance and Operations apps environment has configured dual-write to connect the environment to a single Microsoft Power Platform environment, these environments are identified as a one-to-one linking. For these environments, when Finance and Operations apps version 10.0.21 is generally available, identified one-to-one linked environments will be automatically updated to enable the full Microsoft Power Platform integration for the Finance and Operations apps environment. 

## Troubleshooting the setup

Setup can fail at various stages of the deployment of the Dataverse-based environment. 

![Dual-write setup failure.](media/Error.png)

- Anytime the setup fails, an error message is displayed. Based on the error message, you may need to address licensing or capacity issues. After these have been resolved, you can then select **Resume** in the **Power Platform integration** section of the **Environment details** page in LCS to finish the setup.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
