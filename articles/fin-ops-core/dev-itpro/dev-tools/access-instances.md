---
title: Deploy and access development environments
description: Learn how to access development instances, configure local development VMs, and find configuration settings for developers and administrators.
author: laneswenka
ms.author: laswenka
ms.topic: install-set-up-deploy
ms.date: 03/10/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.assetid: 4be8b7a1-9632-4368-af41-6811cd100a37
ms.custom:
  - sfi-image-nochange
  - sfi-ropc-nochange
---

# Deploy and access development environments

[!include [banner](../includes/banner.md)]

This article describes how to access development instances, configure local development virtual machines (VMs), and find important configuration settings for developers and administrators.

> [!NOTE]
>
> - Microsoft Support might provide limited troubleshooting for Tier 1 development environments.
> - In certain circumstances, Microsoft Support might request a fresh deployment of a Tier 1 environment to resolve an issue.
> - Development environments shouldn't contain business-critical data and are considered disposable.
> - These environments aren't intended for performance testing.
> - Depending on your workload, you might need to choose or adjust the Azure SKU for the selected VM.
> - Each tenant supports only 120 environments. Limit the number of cloud-hosted environments under a specific tenant to allow enough capacity to deploy sandbox and production environments.
> - For cloud-hosted environments older than six months, review the supported software list on the [Microsoft Dynamics 365 Finance + Operations supported software](../deployment/onprem-compatibility.md) page.

## Definitions

| Term      | Definition                             |
|-----------|----------------------------------------|
| End user  | A user who accesses an instance through the web client. The end user must have Microsoft Microsoft Entra credentials to access an instance and must be provisioned or added as a user of that instance. |
| Developer | A user who develops code through the Microsoft Visual Studio environment. A developer requires Remote Desktop access to development environment (VM). The developer account must be an administrator on the VM. |

## Deploy cloud development environments

To deploy a cloud development environment in your Lifecycle Services project:

1. Create a connection between a Lifecycle Services project and your Azure subscription. You need your Azure subscription ID and must authorize the use of the subscription.
1. Select **+** under **Environments** to deploy.

    :::image type="content" source="media/access-instances-5.jpeg" alt-text="Screenshot of the Lifecycle Services Onboard methodology.":::

1. Select an application and platform version.
1. Select an environment topology. For more information, see [Sign up for preview subscriptions](sign-up-preview-subscription.md).
1. If you chose a cloud-hosted environment, select which Azure connector you want to use. Then select **Deploy**.

    :::image type="content" source="media/access-instances-3.jpeg" alt-text="Screenshot of the Deploy environment page.":::

:::image type="content" source="media/CloudHostedPicture.jpg" alt-text="Screenshot of cloud-hosted instances.":::

## Cloud environment that is provisioned through Lifecycle Services

> [!NOTE]
> [Copilot and AI agents](../copilot/enable-copilot.md) aren't supported in [developer environments that you deployed through Lifecycle Services](../dev-tools/access-instances.md#cloud-environment-that-is-provisioned-through-lifecycle-services).

When you provision a cloud environment through Lifecycle Services:

- The user who requests the cloud environment is the administrator in that environment.
- You create user accounts on the development VM to allow access to the environment by using Remote Desktop. You can access these credentials on the environment page in Lifecycle Services.

### Access an instance through a URL

End users can access the system. The administrator can add users to this system by using the **Users** page in the instance. These users don't need to be users in Lifecycle Services. You get the base URL for the cloud environment from your Lifecycle Services project site.

1. Go to your Lifecycle Services project navigation menu, and select **Cloud-hosted environments**.
1. In the environment list section, select the deployed environment.
1. When the environment page opens, you can access the application by selecting **Login** &gt; **Log on to finance and operations** in the upper-right corner.
1. Use valid end user credentials to sign in to the application. If the current Lifecycle Services user is the user who originally deployed the environment, that user is probably a valid end user and the administrator of the application.
1. In your browser, make a note of the base URL after you sign in. For example, the base URL might be `https://dynamicsAx7aosContoso.cloud.dynamics.com`.

### Access the cloud instance through Remote Desktop

You can access cloud environments both as an end user and as a developer. The developer gets access to the system through Remote Desktop credentials. You get the Remote Desktop credentials from the environment page on the Lifecycle Services project site (see the illustration earlier in this article).

:::image type="content" source="media/restricted-admin.png" alt-text="Screenshot of restricted admin access.":::

For environments deployed **before Platform update 12**:

1. Select the VM name.
1. Use the local administrator user name and password that appear to connect to the cloud VM through Remote Desktop. You can reveal the password by selecting the show password icon.

For any environments deployed **on or after Platform update 12**, there are distinct accounts, a developer account, and an admin account.

After you sign in to the environment through Remote Desktop, if you want to access the local application from the browser, use the same base URL that you use to access the application from a remote computer. The previous section explains how to obtain this base URL from Lifecycle Services.

### Delete cloud-hosted developer environments

When you're done with the developer environment, or if troubleshooting an infrastructure issue is too time consuming, you can delete the environment from Lifecycle Services and create a new one later. To delete a cloud-hosted environment from Lifecycle Services, use the following steps:

1. Go to your Lifecycle Services project navigation menu, and select **Cloud-hosted environments**.
1. Highlight the environment that you want to remove and select **Deallocate**. This action powers down the machine in your Azure subscription.
1. After the deallocation is successful, the environment is in a *Deallocated* state. You can now use the **Delete** button to start the deletion process.

You can't delete a cloud-hosted environment if the virtual network that you created with it's also being used by other cloud-hosted environments. This scenario isn't common, but in some cases customers want all their developer environments to reuse an existing virtual network so that they can share files more easily between them. If you implemented this scenario, you must delete the other environments before you delete the base environment that created the original virtual network, or move the shared virtual network outside of the resource group of the environment you're trying to delete.

If the delete operation fails, check to see if one of the following issues occurred:

- The Azure connector management certificate expired or the Azure connector isn't working as expected. Review [Complete the Azure Resource Manager onboarding process](../deployment/arm-onboarding.md) to make sure you correctly set up all the steps regarding the authorization and access control.
- You moved the Azure subscription to a different tenant than where you originally created it.
- You disabled or deleted the Azure subscription.
- There are Azure policies in your subscription that prevent you from deleting one or more resources in your environment's resource group.
- There are one or more [resource locks](/azure/azure-resource-manager/management/lock-resources) on resources in the environment's resource group. Remove the locks and try the operation again. This situation can also occur if a feature such as a backup vault prevents deletion of a resource.

If Lifecycle Services can't successfully complete the delete operation, the operation is marked as *Incomplete*. Use the **Delete Lifecycle Services metadata** button to clean up this environment's metadata from the Lifecycle Services backend systems.

> [!NOTE]
> This operation doesn't try to delete the resources in the Azure subscription. You need to manually remove the environment's resource group if it still exists.

You can easily identify the environment’s resource group in the Azure subscription, as it has the same name as the environment in Lifecycle Services.

## VM that is running locally

You can download a virtual hard disk (VHD) from Lifecycle Services and set it up on a local machine. This system is a preconfigured one-box development environment of finance and operations apps that a developer can access. You can find the VHD in the Shared Asset library of Lifecycle Services under the asset type **Downloadable VHD**.

1. Go to the Lifecycle Services main page and select **Shared asset library** or go to [Shared Asset Library](https://lcs.dynamics.com/V2/SharedAssetLibrary).
1. Select the asset type **Downloadable VHD**.
1. Find the VHD you want based on the finance and operations version you need. The VHD is divided into multiple file parts that you need to download. For example, the asset files that start with "VHD - 10.0.5" are the different files you need to install version 10.0.5.
1. Download all files (parts) associated with the VHD you want to a local folder.
1. After the download finishes, run the executable file that you downloaded, accept the software license agreement, and choose a file path to extract the VHD to. These steps create a local VHD file that you can use to run a local virtual machine.

### Configure the VHD for Commerce

Follow the steps in this section if you're also configuring for Commerce.

To use the downloadable VHD for POS customizations, complete the following step.

- On the host computer, enable Nested VM support. For more information, see [Run Hyper-V in a Virtual Machine with Nested Virtualization](/virtualization/hyper-v-on-windows/user-guide/nested-virtualization).

### Running the virtual machine locally

Follow these steps to run the VM from Hyper-V Manager.

1. Select **Start** to start the VM.
1. Select **Connect** to open the VM in a window.
1. Select the **Ctrl+Alt+Delete** button on the toolbar. The VM receives most keyboard commands, but Ctrl+Alt+Delete isn't one of them. Therefore, you must use the button or a menu command.
1. Sign in to the VM by using the following credentials:

    - User name: **localadmin**
    - Password: **pass@word1**

    > [!TIP]
    > You can resize the VM window by changing the screen resolution. Right-click the desktop on the VM, and then select **Screen resolution**. Select a resolution that works well for your display.

1. Provision the administrator user. For more information, see the next section.
1. Start the Batch Manager Service. This step is required if you're running batch jobs or workflows.

    1. Open a **Command Prompt** window as an administrator.
    1. Type **net start DynamicsAxBatch**, and then press Enter.

   You can also start the service from the **Services** window.

1. [Apply updates](../migration-upgrade/upgrade-latest-platform-update.md#apply-a-platform-update-to-environments-that-are-not-connected-to-lcs) as needed.

#### Commerce configuration

For POS customizations, you must also follow these steps on the guest VM.

1. Download and install [Microsoft Emulator for Windows 10 Mobile Anniversary Update](/windows/uwp/debug-test-perf/test-with-the-emulator).
1. Start the Hyper-V host service. For more information, see [Hyper-V: The Hyper-V Virtual Machine Management service must be running](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee956894(v=ws.10)). If errors occur during startup, you can also try to uninstall and reinstall the Hyper-V role on the guest VM.

### Provision the administrator user

For developer access, you must be an administrator on the instance. For environments that Lifecycle Services provisions, deploy with the correct user. For more information, see [Frequently asked questions](access-instances.md#frequently-asked-questions). To provision your own credentials as an administrator on a local VM, run the Admin user provisioning tool. On the local VM, a link is provided on the desktop.

1. Run the admin user provisioning tool as an administrator (right-click the icon, and then select **Run as administrator**).
1. Enter your email address, and then select **Submit**.

> [!NOTE]
> The Admin user provisioning tool isn't supported in environments that Lifecycle Services provisions. Use it only on local VMs.

> [!NOTE]
> For local VMs that use the virtual hard drive (VHD) that was released for versions 10.0.24 and later, use the instructions in [Set up the downloadable VHD for first use](vhd-setup.md).

### Commerce configuration

Follow the steps in this section if you're also configuring for Commerce.

### Base URL of the local application

After you provision the user as an administrator, the user can access the instance on the computer by navigating to the following base URL: `https://usnconeboxax1aos.cloud.onebox.dynamics.com`. If you're using version control and plan to connect multiple development VMs to the same Azure DevOps project, rename your local VM. For instructions, see [Rename a local development (VHD) environment](../migration-upgrade/vso-machine-renaming.md).

#### Commerce configuration

The URL of the POS app is `https://usnconeboxax1pos.cloud.onebox.dynamics.com/`.

The URL of the Cloud POS app is `https://usnconeboxax1pos.cloud.onebox.dynamics.com`. After you complete the configuration steps, you provision this VM with your Microsoft Entra tenant. Your Microsoft Entra admin account maps to a cashier worker account in demo data. You can use this cashier account to easily activate a POS device in this environment.

- Cashier user ID: **000160**
- Cashier password: **123**
- Cashier LE: **USRT**
- Cashier store: **Houston**

## Location of packages, source code, and other AOS configurations

On a VM, you can find most of the application configuration by opening the web.config file of AOSWebApplication.

1. Start IIS.
1. Go to **Sites** &gt; **AOSWebApplication**.
1. Right-click, and then select **Explore** to open File Explorer.
1. Open the web.config file in Notepad or another text editor. The following keys are of interest to many developers and administrators:

    - **Aos.MetadataDirectory** – This key points to the location of the packages folder that contains platform and application binaries, and also source code. (Source code is available only in development environments.) Typical values are: `c:\packages`, `c:\AosServicePackagesLocalDirectory`, and `J:AosServicePackagesLocalDirectory`.
    - **DataAccess.Database** – This key holds the name of the database.
    - **Aos.AppRoot** – This key points to the root folder of the Application Object Server (AOS) web application.

### Commerce configuration

The software development kit (SDK) is available at `C:\RetailSDK`. For more information about how to use and customize applications, see the following articles:

- [Retail software development kit (SDK) architecture](../../../commerce/dev-itpro/retail-sdk/retail-sdk-overview.md)
- [Point of sale (POS) device activation](../../../commerce/dev-itpro/retail-device-activation.md)

#### Remove preexisting encrypted data from headquarters

If you see the following `NoCertificateFoundException` error in Event Viewer while configuring the shared hardware station on a VHD image, you might need to manually remove the merchant properties from the deployed environment.

`No certificate found for id <id value presented>...`

In AOS of your VHD environment, clear preloaded values in the **SECUREMERCHANTPROPERTIES** or **CONNECTIONSTRING** attributes from the following tables:

```SQL
SELECT SECUREMERCHANTPROPERTIES FROM dbo.RETAILHARDWAREPROFILE -- hardware profile form
```

```SQL
SELECT SECUREMERCHANTPROPERTIES FROM dbo.RETAILCHANNELPAYMENTCONNECTORLINE -- online stores form
```

```SQL
SELECT SECUREMERCHANTPROPERTIES FROM dbo.CREDITCARDACCOUNTSETUP -- payment service form 
```

```SQL
SELECT CONNECTIONSTRING FROM dbo.RETAILCONNDATABASEPROFILE -- payment service connection string for CDX
```

If you find preloaded values, set the attribute values to empty by using scripts similar to the following examples.

> [!WARNING]
> The example `UPDATE` scripts provided below are illustrative for newly provisioned environments experiencing the certificate issue described earlier. Only update values for the intended table or rows to avoid disruptive or destructive data updates. You might need more selectors if you're updating specific rows for the tables being updated.

```SQL
UPDATE dbo.RETAILHARDWAREPROFILE SET SECUREMERCHANTPROPERTIES=";)
```

```SQL
UPDATE dbo.RETAILCHANNELPAYMENTCONNECTORLINE SET SECUREMERCHANTPROPERTIES=";)
```

```SQL
UPDATE dbo.CREDITCARDACCOUNTSETUP SET SECUREMERCHANTPROPERTIES=";)
```

```SQL
UPDATE dbo.RETAILCONNDATABASEPROFILE SET CONNECTIONSTRING=";
```

Once you clear these values, use the forms in headquarters to set up your payment gateway merchant details in the hardware profile, online store channel, or the payments service forms appropriate for the environment. For the setup instructions required for your payment options, see the appropriate article:

- [Set up Dynamics 365 Payment Connector for Adyen](../../../commerce/dev-itpro/adyen-connector-setup.md)
- [Dynamics 365 Payment Connector for PayPal](../../../commerce/paypal.md)

## Redeploy or restart the runtime on the VM

To restart the local runtime and redeploy all the packages, follow these steps:

1. Open File Explorer, and go to `C:\CustomerServiceUnit`.
2. Right-click **AOSDeploy.cmd**, and then select **Run as administrator**.

This process might take a while. The process completes when the `cmd.exe` window closes. If you want to just restart AOS (without redeploying the runtime), run **iisreset** from an administrator **Command Prompt** window, or restart **AOSWebApplication** from IIS.

## Frequently asked questions

### Can I join cloud-hosted environments to my Microsoft Entra domain as it is currently deployed in a workgroup?

These environments are self-contained. Microsoft hasn't tested or supported joining these environments to a Microsoft Entra domain when you deploy them through Azure.  

### Is there a way to hide the local account passwords in Lifecycle Services?

You can hide local account passwords by lowering a user's security role in the project to *Project team member*. You can't hide local account passwords for the *Environment manager* or *Project owner* roles.

### Are cloud-hosted environments supported with Azure Bastion?

Microsoft hasn't tested or supported these environments with Azure Bastion.  

### Environment is in a failed state with the error message, "Updated Microsoft Entra ID Tenant is missing reply URL configuration." How do I resolve this issue?

This message indicates that a Tier 1/customer-managed environment is configured with a Microsoft Entra ID tenant different from the one used at the time of deployment. To resolve this issue, use one of the following options:

1. (Recommended) Delete the environment and redeploy it by using the tenant in which you want to use the environment.
1. Revert the settings to the tenant configuration that you used at the time of deployment.
1. Follow the instructions in [How can I fix my existing environment when my environment is in a failed state or if I'm getting sign-in errors?](access-instances.md#how-can-i-fix-my-existing-environment-when-my-environment-is-in-a-failed-state-or-i-am-getting-sign-in-errors) to update the reply URL in the target tenant.  

### As a partner/ISV, how can I facilitate cloud-hosted deployments for customers that I work with?

Deploy a Tier 1/customer-managed environment under the customer's Microsoft Entra tenant. This approach ensures that the configuration and integrations are correctly provisioned for any given environment. The tenant and environment association is based on the user who deployed the environment.

To facilitate cloud-hosted deployments, create customer-specific cloud-hosted environments by following these steps. This approach ensures that the deployment is registered under the correct tenant.

- Deploy the environment by using a user from the tenant that you want to use with the environment. Don't use the Admin user provisioning tool to change the tenant for a Tier 1/customer-managed/cloud-hosted environment.

> [!NOTE]
> The Microsoft Entra tenant that you associate with the Azure subscription doesn't play any role in environment configuration. The Azure subscription and the corresponding connector configuration are used only to deploy Azure resources.

### I ran the Admin user provisioning tool on my development environment, and now I receive the following sign-in error: "Error: Microsoft EntraSTS50011: The reply URL specified in the request doesn't match the reply URLs configured for the application."

As stated earlier, it's important to deploy finance and operations environments under the correct Microsoft Entra tenant. For Tier 1/customer-managed environments that you deploy through LCS, you can't change the Microsoft Entra tenant settings after deployment.

### How can I fix my existing environment when my environment is in a failed state or I am getting sign-in errors?

If you have environments where you previously used the Admin user provisioning tool to update the tenant settings, delete those environments and then redeploy them under the correct Microsoft Entra tenant.

If you can't delete and redeploy an existing environment, add its URL to the configured Microsoft Entra tenant. The tenant admin can run the following commands.

> [!NOTE]
> Since you're manually adding these URLs, you also need to manually clean up these URLs when you delete the environment.

1. If you don't already have it on your machine, install the Microsoft. Graph PowerShell module.

    ```powershell
    Install-Module Microsoft.Graph
    ```

1. Retrieve the following values from the web.config file.

    ```powershell
    $Microsoft EntraTenant = <Value of Aad.TenantDomainGUID from web.config>
    $EnvironmentUrl = <Value of Infrastructure.HostUrl from web.config>

    # For example, if value is spn:fd663e81-110e-4c18-8995-ddf534bcf5e1 then take only fd663e81-110e-4c18-8995-ddf534bcf5e1
    $Microsoft EntraRealm = <Value of Aad.Realm from web.config without spn: prefix. >
    ```

1. Run the following commands **by using the tenant admin account for the Microsoft Entra tenant in the web.config file**.

    ```powershell
    # Using tenant admin account under this tenant login via Microsoft Graph PowerShell cmdlet.
    Connect-MgGraph -TenantId $Microsoft EntraTenant -Scopes "Application.ReadWrite.All"

    # Get Service Principal details
    $SP = Get-MgServicePrincipal -Filter "AppId eq '$Microsoft EntraRealm'"
    
    # Add Reply URLs
    [System.Collections.ArrayList]$ReplyUrls = $SP.ReplyUrls
    $ReplyUrls.Add("$EnvironmentUrl")
    $ReplyUrls.Add("$EnvironmentUrl/oauth")

    #Set/Update Reply URL
    Update-MgServicePrincipal -ServicePrincipalId $SP.Id -ReplyUrls $ReplyUrls
    
    # Log out
    Disconnect-MgGraph
    ```

### I fixed my environment, but it's still in a failed state. How do I resolve this issue?

Restart your environment from Lifecycle Services by first performing **Stop** and then **Start** operations against your environment. If the environment configuration is correct, the environment URL is restored automatically **within 2 hours** of the **Start** operation.

### When I run the Admin user provisioning tool on my local development environment, I get the error "The value's length for key 'password' exceeds its limit of '128'."

If you're using the virtual hard drive (VHD) that Microsoft released for versions 10.0.24 and later, you need to run the Generate Self-Signed Certificates tool before the Admin user provisioning tool. For more information, see [Set up the downloadable VHD for first use](vhd-setup.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
