---
# required metadata

title: Enable the Microsoft Power Platform integration
description: This topic explains how to enable the Microsoft Power Platform integration by using Microsoft Dynamics Lifecycle Services (LCS) for Finance and Operations apps and Dataverse.
author: jaredha
ms.date: 10/25/2021
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
# Enable the Microsoft Power Platform integration

[!include[banner](../includes/banner.md)]

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

The integration of Finance and Operations apps with Microsoft Power Platform can be enabled when you create a new Finance and Operations apps environment in Microsoft Dynamics Lifecycle Services (LCS). Alternatively, Microsoft Power Platform can be enabled in an existing Finance and Operations apps environment. For both options, you must complete the setup prerequisites.

## Prerequisites for setting up the Microsoft Power Platform integration

The following list describes the prerequisites for setting up the Microsoft Power Platform integration.

- Make sure that at least one gigabyte (GB) of Microsoft Power Platform database storage capacity space is available for your tenant. If this space isn't available, the setup will fail. View your capacity in the [Power Platform admin center](https://admin.powerplatform.microsoft.com/resources/capacity). 

- Identify your Finance and Operations apps environment administrator. You can find that information in the **Environment details** section.

    ![Environment administrator information in the Environment details section.](media/EnvironmentDetails.png)

- Validate the governance policy of your Microsoft Power Platform environment. To do this validation, you must have either the **Global administrator** role or the **Power Platform administrator** role.

    1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com).
    2. Select **Settings** in the upper-right corner of the page to open the **Power Platform settings** pane.

        ![Power Platform settings pane.](media/PowerPlatformSettings.png)

- For organizations that **don't allow everyone** to create Microsoft Power Platform production environments, the Finance and Operations apps environment administrator account for your environment must be added to one of the following Microsoft Power Platform admin roles. To make this change, you must have the **Global administrator** role.

    - Global admins
    - Dynamics 365 admins
    - Microsoft Power Platform admins

    > [!NOTE]
    > The preceding roles might provide more permissions than the Finance and Operations apps environment administrator account requires. Therefore, a more limited role for this integration will eventually be added to Azure Active Directory (Azure AD). The new role won't require any of the preceding roles. If you want to keep the administrator that has the least privileges, you can temporarily grant one of the preceding roles. Then, after the Microsoft Power Platform integration is set up, remove that role.

- All users who create Microsoft Power Platform environments must be licensed. The Microsoft 365 admin center should be used to apply the **Dynamics 365 Unified Operations Plan** license, the **AX Enterprise** license, or an application-specific license such as **Dynamics 365 Finance** to the Finance and Operations apps environment administrator account.

## <a name="enable-during-deploy"></a>Enable integration during environment deployment

When you set up a new Finance and Operations apps environment in LCS, the deployment wizard includes several sections where you can set values. One of those sections is named **Power Platform Integration**.

![Power Platform Integration section in the deployment wizard.](media/powerplat_integration_step0.png)

Follow these steps to configure the **Power Platform Integration** section.

1. Set the **Configure Power Platform Environment** option to **Yes**. Several additional settings become available.
2. In the **Power Platform template** field, select one of the following values:

    - **Dynamics 365 Standard** – This basic template is applicable to all Finance and Operations apps environments. Select this value if you don't require a more specific template.
    - **Project Operations** – This template is specific to the Dynamics 365 Project Operations scenario. This value is available only if your tenant has licenses and entitlement for Project Operations.

3. If you're deploying a DevTest or cloud-hosted environment, the **Environment Type** field is available. There, you can select the type of Dataverse environment that is created and linked. Otherwise, by default, the environment type is set to **Sandbox** for Tier 2 through Tier 5 acceptance test environments and **Production** for production environments.
4. Select **Agree** to agree to the terms and conditions of the integration.

> [!IMPORTANT]
> The **language** and **currency** values of the Dataverse environment that is created and linked to your Finance and Operations apps environment are automatically determined, based on the physical address of your Azure AD tenant. For example, if the address is in Redmond, Washington, USA, the language will be English by default, and the currency will be US dollars (USD).
>
> If you require values that differ from the default values, contact Microsoft support. We can help link an existing Dataverse environment that you manually provision to the Finance and Operations apps environment. Eventually, fields for the language and currency will be added as setup options, so that you can manually set them or accept the default values.

## <a name="enable-after-deploy"></a>Enable integration after environment deployment

If the Microsoft Power Platform integration isn't enabled during deployment of the Finance and Operations apps environment, you can enable it in LCS after deployment. To do the setup after the Finance and Operations apps environment has been deployed, follow these steps.

1. After the Finance and Operations apps environment has been deployed through LCS, open the **Environment details** page in LCS.
2. In the **Power Platform integration** section, select **Setup**.

    ![Setup button in the Power Platform Integration section.](media/powerplat_integration_step1.png) 

3. In the **Power Platform environment setup** dialog box, agree to the terms and conditions, and then select **Setup**.

    > [!NOTE]
    > A Dataverse-based environment will now be provisioned in the Power Platform admin center. The environment typically requires 1 GB of database storage capacity and will have the same name as your Finance and Operations apps environment. Dual-write platform-level components will be installed, but dual-write application components won't be set up or enabled. Those actions are separate.

4. When you receive a message that states that the Microsoft Power Platform environment is being provisioned, select **OK**.

    The **Power Platform integration** section of the **Environment details** page now shows a message that states that the Microsoft Power Platform environment is being provisioned.

5. After a few minutes, refresh the **Environment details** page.
6. In the **Power Platform integration** section, notice that the value of the **Status** field is **Environment setup is in progress**.

    Typically, the setup takes between 60 and 90 minutes.

    After the Dataverse environment is provisioned, the **Install a new add-in** and **Dual-write application** buttons become available in the **Power Platform integration** section.

    ![Install a new add-in button.](media/InstallANewAddIn.png)

    ![Dual-write application button.](media/powerplat_integration_dwApp_button.png)

> [!IMPORTANT]
> The **language** and **currency** values of the Dataverse environment that is created and linked to your Finance and Operations apps environment are automatically determined, based on the physical address of your Azure AD tenant. For example, if that address is in Redmond, Washington, USA, the language will be English by default, and the currency will be US dollars (USD).
>
> If you require values that differ from the default values, contact Microsoft support. We can help link an existing Dataverse environment that you manually provision to the Finance and Operations apps environment. Eventually, fields for the language and currency will be added as setup options, so that you can manually set them or accept the default values.

## Enable integration with an existing, selected Microsoft Power Platform environment

When you enable the Microsoft Power Platform integration for a Finance and Operations apps environment in LCS, either during or after deployment, the process creates a new Dataverse-enabled Microsoft Power Platform environment and links the Finance and Operations apps environment to the new Microsoft Power Platform environment. However, you might want to enable integration by linking your Finance and Operations apps environment to an existing Microsoft Power Platform environment other than the environment created automatically during deployment. The option to select the Power Platform environment with which to enable the Power Platform integration isn't currently available in LCS.

How the Power Platform integration is enabled for existing environments depends on the number of Power Platform environments that are linked to the Finance and Operations apps environment. Prior to enabling the Power Platform integration, there are multiple ways in which a Finance and Operations apps environment can be considered linked to a Power Platform environment:
1. **Deployment link**: During the deployment of a new Finance and Operations environment, even when the option to enable the Power Platform integration is not selected, a new Power Platform environment is created and linked to the Finance and Operations environment. You can see this link in the **Finance and Operations URL** field of the environment details for the new Power Platform environment in the Power Platform admin center.
2. **Dual-write**: The option is available in the Dual-write configuration to create a link to a Dataverse environment in any Power Platform environment on the tenant.
3. **Virtual entities**: The virtual entity configuration in the Power Platform environment allows you to select the Finance and Operations environment.

These three configurations won't necessarily link the Finance and Operations apps environment to the same Power Platform environment. There are two scenarios for enabling the Power Platform integration with an existing Microsoft Power Platform environment:

- **Single Power Platform environment**: In this scenario, the Finance and Operations apps environment has matched links to a single Power Platform environment. If Dual-write and/or virtual entities have been configured for the Finance and Operations apps environment, they are configured to link to the same Power Platform environment created during deployment of the Finance and Operations apps environment. 
- **Multiple Power Platform environments**: There is a linking mismatch among existing links between the Finance and Operations apps environment and more than one Power Platform environment.

### Finance and Operations apps connected to a single Microsoft Power Platform environment

If the Finance and Operations apps environment is configured with links to a single Microsoft Power Platform environment, these environments are identified as a one-to-one linking. For these environments, when Finance and Operations apps version 10.0.22 (Platform update 46) is generally available, identified one-to-one linked environments will automatically be updated to enable the full Microsoft Power Platform integration for the Finance and Operations apps environment. 

After general availability date of that version, you can verify that the Microsoft Power Platform integration was automatically enabled by viewing the **Power Platform Integration** section of the **Environment details** page for the Finance and Operations apps environment in LCS. If the integration was successfully enabled, the **Environment name** field will show the name of the integrated Microsoft Power Platform environment, and the **Status** field is set to **Setup completed successfully**.

> [!NOTE]
> The Microsoft Power Platform integration will automatically be enabled for Finance and Operations apps environments that are already connected to a single Microsoft Power Platform environment and that already use business events functionality. However, these environments won't be able to use the new business events and data events functionality when the 10.0.22 (PU46) release becomes generally available. The business events endpoints that are already used in these environments will be migrated to the Dataverse platform when the 10.0.23 (PU47) release becomes generally available. At that point, the new business events and data events functionality will become available in the environments. Until then, business events will continue to work as they are currently configured in the environment.
> 
> For more information about the new business events and data events functionality that will be delayed for these environments until the migration is completed, see [Finance and Operations business events in Dataverse](/dynamics365-release-plan/2021wave2/finance-operations/finance-operations-crossapp-capabilities/new-scenarios-enabled-power-platform-convergence#finance-and-operations-business-events-in-dataverse) and [Finance and Operations CUD events in Dataverse](/dynamics365-release-plan/2021wave2/finance-operations/finance-operations-crossapp-capabilities/new-scenarios-enabled-power-platform-convergence#finance-and-operations-cud-events-in-dataverse) in the 2021 release wave 2 plan. 

### Finance and Operations apps connected to multiple Microsoft Power Platform environments

If a Finance and Operations apps environment has been manually linked to multiple Microsoft Power Platform environments, the process of enabling the Microsoft Power Platform integration for the environment can't be automated. The system can't automatically determine to which Power Platform environment the Finance and Operations apps environment should be linked for the Power Platform integration.

There are two options to enable the Power Platform integration for a Finance and Operations environment that has links to multiple Power Platform environments:
- Reconfigure your Dual-write and/or virtual entity solutions to link the Finance and Operations apps environment to the Power Platform environment created at deployment. Once all links are configured for the single Power Platform environment, you can enable the Power Platform integration in LCS following the steps outlined in the [Enable integration after environment deployment](enable-power-platform-integration#enable-after-deploy) section above. This is the preferred solution because it can be managed without Microsoft support.
- To enable the Power Platform integration with a linked Power Platform environment other than the Power Platform environment created during deployment of the Finance and Operations environment, either work with your FastTrack solution architect or contact Microsoft Support to enable the Power Platform integration with a selected environment.

See [Linking mismatch](../data-entities/dual-write/lcs-setup#linking-mismatch) in the Dual-write documentation for more information on related Dual-write configuration options.

## Troubleshooting the setup

Setup can fail at various stages of the deployment of the Dataverse-based environment.

Any time that the setup fails, an error message is shown. The following illustration shows an example of the error message for a dual-write setup failure.

![Error message for a dual-write setup failure.](media/Error.png)

Based on the error message, you might have to address licensing or capacity issues. After these issues have been fixed, you can select **Resume** in the **Power Platform integration** section of the **Environment details** page in LCS to finish the setup.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
