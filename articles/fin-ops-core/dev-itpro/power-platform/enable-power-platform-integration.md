---
# required metadata

title: Enable the Microsoft Power Platform integration
description: This topic explains how to enable the Microsoft Power Platform integration by using Microsoft Dynamics Lifecycle Services (LCS) for Finance and Operations apps and Dataverse.
author: jaredha
ms.date: 05/16/2022
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

The integration of Finance and Operations apps with Microsoft Power Platform can be enabled when you create a new Finance and Operations apps environment in Microsoft Dynamics Lifecycle Services (LCS). Alternatively, Microsoft Power Platform can be enabled in an existing Finance and Operations apps environment. For both options, you must complete the setup prerequisites.

Power Platform integration lets you complete the following tasks:

* Create apps and flows by using the new Power Platform environment that is automatically created for you.
* Integrate Finance and Operations apps data with the Dataverse platform by using virtual tables, business events, and dual-write features.
* Install and connect other Dynamics 365 applications with your Finance and Operations apps.
* Install add-ins, and connect them with your Finance and Operations apps.

## Initial Power Platform environment

By default, all Finance and Operations apps environments (sandbox and production) that are managed by LCS will receive an initial Power Platform environment **without** Dataverse. This environment is linked to your Finance and Operations environment, as shown in the following illustration. The relationship is one to one. Over time, your Finance and Operations apps will be migrated to this location in Power Platform admin center. You can determine whether an environment in Power Platform admin center is linked to an environment from LCS by looking at the Finance and Operations apps URL on the environment details page in Power Platform admin center.

:::image type="content" source="media/LinkedPowerPlatformEnvironment.png" alt-text="Linked Power Platform environment.":::

The Power Platform environment that is connected to your environment in LCS enables Finance and Operations apps customers to take advantage of Microsoft Power Platform. This Power Platform environment can't be deleted or reset, and a Dataverse database can't be manually added to it in Power Platform admin center. To add Dataverse and fully enable Microsoft Power Platform integration capabilities, follow the instructions in the [Enable integration with an existing Power Platform environment](#connect-to-existing-dataverse) section of this topic.

Alternatively, your organization might already have a Power Platform environment with Dataverse that you want to connect to your Finance and Operations environment. To reuse an existing Dataverse instance, follow the instructions in [Connect to an existing Power Platform environment](). In this case, the initial Power Platform environment that was created when your Finance and Operations environment was created is disconnected and will no longer show the Finance and Operations apps URL. At that point, the initial environment can be deleted or used for another purpose.

## Licensing and capacity considerations

When you purchase a license for any Finance and Operations app, such as Dynamics 365 Finance or Dynamics 365 Supply Chain Management, your tenant is entitled to an additional 10 gigabytes (GB) of Dataverse database capacity. In addition, for each user license that you purchased, you receive an incremental amount of database capacity, as shown in the following illustration from Power Portal admin center.

:::image type="content" source="media/PPI-Capacity.png" alt-text="Capacity view in Power Platform admin center.":::

The same purchase of licenses entitles you to one self-service sandbox environment and production environment in LCS. Because of this, an initial Power Platform environment can automatically be created for every Finance and Operations apps environment. Every initial environment in Power Platform admin center is without Dataverse. Therefore, it uses only 1 GB of database capacity to provision apps that are created by using Power Apps and flows that are created by using Power Automate. When you set up Power Platform integration, a Dataverse database is added to the same environment. This database often consumes 3 GB or more.

Additional add-on sandbox environments that customers purchase to use in LCS do **not** entitle them to additional Dataverse database capacity. Customers who will require Power Platform integration capabilities should purchase add-on Dataverse database storage. For more information about how to manage capacity in Power Platform admin center, see [Free up storage space](/power-platform/admin/free-storage-space).

## Provisioning templates

In several of the scenarios that are described in this topic, you will create a brand-new Power Platform environment with Dataverse. To help you quickly add all the applications that are required for your new instance, we have prepared several provisioning templates that bundle them together. The following table provides details about these templates.

| Template name | Description | Apps included |
|---------------|-------------|---------------|
| Dynamics 365 Standard | This basic template prepares all the platform components for business events, virtual tables, dual-write functionality, and add-in support. Dual-write isn't enabled and won't automatically sync data when this template is selected. Select this template if you don't require a more specific template. | MicrosoftOperationsVEAnchor, DualWriteCoreAnchor, MsDynCE_CRMHub, MsDyn_FnOIntegrationMDLApp_Anchor |
| Dynamics 365 Standard with dual-write | This template is the same as **Dynamics 365 Standard**, but it includes all the applications that are required for dual-write, so that you can quickly enable that feature after environment deployment. | MicrosoftOperationsVEAnchor, DualWriteCoreAnchor, MsDynCE_CRMHub, MsDyn_FnOIntegrationMDLApp_Anchor, MsDyn_DualWriteAppCoreAnchor |
| Project Operations | This template is specific to the Dynamics 365 Project Operations scenario. It's available only if your tenant has licenses and entitlement for Project Operations. | MicrosoftOperationsVEAnchor, Dynamics365FinanceAndOperationsAnchor, ProjectOperations_Anchor |

## Prerequisites for setting up the Microsoft Power Platform integration

The following list describes the prerequisites for setting up the Microsoft Power Platform integration.

- Make sure that at least 1 GB of Microsoft Power Platform database storage capacity space is available for your tenant. If this space isn't available, the setup will fail. View your capacity in the [Power Platform admin center](https://admin.powerplatform.microsoft.com/resources/capacity). 

- Identify your Finance and Operations apps environment administrator. You can find that information in the **Environment details** section.

    ![Environment administrator information in the Environment details section.](media/EnvironmentDetails.png)

- Validate the governance policy of your Microsoft Power Platform environment. To do this validation, you must have either the **Global administrator** role or the **Power Platform administrator** role.

    1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com).
    2. Select **Settings** in the upper-right corner of the page to open the **Power Platform settings** pane.

        ![Power Platform settings pane.](media/PowerPlatformSettings.png)

- For organizations that **don't allow everyone** to create Microsoft Power Platform environments, the Finance and Operations apps environment administrator account for your environment must be added to one of the following roles in Azure Active Directory (Azure AD). To make this change, you must be assigned to the **Global administrator** role.

    - Dynamics 365 Service Admin
    - Power Platform Admin

    > [!NOTE]
    > The preceding roles might provide more permissions than the Finance and Operations apps environment administrator account requires. Therefore, a more limited role for this integration will eventually be added to Azure AD. The new role won't require any of the preceding roles. If you want to keep the administrator that has the least privileges, you can temporarily grant one of the preceding roles. Then, after the Microsoft Power Platform integration is set up, remove that role.

- All users who create Microsoft Power Platform environments must be licensed. The Microsoft 365 admin center should be used to apply the **Dynamics 365 Unified Operations Plan** license, the **AX Enterprise** license, or an application-specific license such as **Dynamics 365 Finance** to the Finance and Operations apps environment administrator account.

## <a name="enable-during-deploy"></a>Enable integration during environment deployment

> [!IMPORTANT]
> When you enable Power Platform integration, a new Dataverse database is added to the initial Power Platform environment that was described earlier. If your organization already has a Dataverse instance that you want to connect to the Finance and Operations environment, **do not enable** Power Platform integration during environment creation in LCS. After deployment of the Finance and Operations environment is completed, you will be able to connect to an existing Power Platform environment by using the **Setup** button.
>
> Power Platform integration is **irreversible**, and the link can't be changed or removed. As part of the setup, you connect your Finance and Operations environment to a Power Platform environment. Runtime features such as virtual entities, business events, and dual-write all depend on this connection. Therefore, it can't be removed until you delete the Finance and Operations environment. This behavior resembles the behavior when you apply a service update from Microsoft. The only way to redo this action is to redeploy the environment.

When you set up a new Finance and Operations apps environment in LCS, the deployment wizard includes several sections where you can set values. One of those sections is named **Power Platform Integration**.

![Power Platform Integration section in the deployment wizard.](media/powerplat_integration_step0.png)

Follow these steps to configure the **Power Platform Integration** section.

1. Set the **Configure Power Platform Environment** option to **Yes**. Several additional settings become available.
2. In the **Power Platform template** field, select a template. For more information, see the [Provisioning templates](#provisioning-templates) section of this topic.
3. If you're deploying a DevTest or cloud-hosted environment, the **Environment Type** field is available. There, you can select the type of Dataverse instance that is created and linked. Otherwise, by default, the environment type is set to **Sandbox** for Tier 2 through Tier 5 acceptance test environments and **Production** for production environments.
4. Select **Agree** to agree to the terms and conditions of the integration.

> [!IMPORTANT]
> The **language** and **currency** values of the Dataverse instance that is created and linked to your Finance and Operations apps environment are automatically determined, based on the physical address of your Azure AD tenant. For example, if the address is in Redmond, Washington, USA, the language will be English by default, and the currency will be US dollars (USD).
>
> If you require values that differ from the default values, contact Microsoft support. We can help link an existing Dataverse instance that you manually provision to the Finance and Operations apps environment. Eventually, fields for the language and currency will be added as setup options, so that you can manually set them or accept the default values.

## <a name="enable-after-deploy"></a>Enable integration after environment deployment

In many cases, you might want to enable the Power Platform integration after you've already deployed Finance and Operations apps. For example, you went live with Finance and Operations apps first and now want a new Dataverse instance to go with it, or you chose to connect to an existing Dataverse instance as described in the next section.

> [!IMPORTANT]
> Power Platform integration is **irreversible**, and the link can't be changed or removed. As part of the setup, you connect your Finance and Operations environment to a Power Platform environment. Runtime features such as virtual entities, business events, and dual-write all depend on this connection. Therefore, it can't be removed until you delete the Finance and Operations environment. This behavior resembles the behavior when you apply a service update from Microsoft. The only way to redo this action is to redeploy the environment.

1. After the Finance and Operations apps environment has been deployed through LCS, open the **Environment details** page in LCS.
2. In the **Power Platform integration** section, select **Setup**. *If you want to connect to an existing Dataverse organization, see the next section of this topic.*

    ![Setup button in the Power Platform Integration section.](media/powerplat_integration_step1.png) 

3. In the **Power Platform environment setup** dialog box, agree to the terms and conditions, and then select **Setup**.

    > [!NOTE]
    > A Dataverse-based environment will now be provisioned in Power Platform admin center. The environment typically requires 1 GB of database storage capacity and will have the same name as your Finance and Operations apps environment. Dual-write platform-level components will be installed, but dual-write application components won't be set up or enabled. Those actions are separate.

4. When you receive a message that states that the Microsoft Power Platform environment is being provisioned, select **OK**.

    The **Power Platform integration** section of the **Environment details** page now shows a message that states that the Microsoft Power Platform environment is being provisioned.

5. After a few minutes, refresh the **Environment details** page.
6. In the **Power Platform integration** section, notice that the value of the **Status** field is **Environment setup is in progress**.

    Typically, the setup takes between 60 and 90 minutes.

    After the Dataverse instance is provisioned, the **Install a new add-in** and **Dual-write application** buttons become available in the **Power Platform integration** section.

    ![Install a new add-in button.](media/InstallANewAddIn.png)

    ![Dual-write application button.](media/powerplat_integration_dwApp_button.png)

> [!IMPORTANT]
> The **language** and **currency** values of the Dataverse instance that is created and linked to your Finance and Operations apps environment are automatically determined, based on the physical address of your Azure AD tenant. For example, if the address is in Redmond, Washington, USA, the language will be English by default, and the currency will be USD.
>
> If you require values that differ from the default values, manually create a new Power Platform environment that meets your specifications. You can then follow the instructions in the next section to connect your existing Dataverse instance via LCS.

After you complete the setup, the only way to reverse the action is to delete the environment in LCS. Relinking or linking to another environment isn't supported.

### <a name="connect-to-existing-dataverse"></a>Enable integration with an existing Power Platform environment

If you already have a Dataverse instance that you want to connect to a Finance and Operations environment, you can connect it during the setup of Power Platform integration from a previously deployed Finance and Operations environment. However, note that this option isn't available when you deploy a new Finance and Operations environment.

:::image type="content" source="media/PPI-ConnectToExisting.png" alt-text="Connecting to an existing Power Platform environment.":::

To get the Power Platform environment ID, you can copy it from the address bar of your browser when you visit the environment in Power Platform admin center.

:::image type="content" source="media/PPI-ExistingEnvironmentID.png" alt-text="Retrieving the environment ID from the browser's address bar.":::

During the integration process, Microsoft will apply the packages for the **Dynamics 365 standard** provisioning template. If you require packages from the other templates, you must manually install. For more information, see the [Provisioning templates](#provisioning-templates) section of this topic.

Customers who are already live with Power Platform environments or other Dynamics 365 apps, and who want to add Finance and Operations apps to that ecosystem, will find it most useful to bring their existing Dataverse instance. For the integration, you use the same setup process that is described earlier for a new Dataverse database in the initial environment. After you complete the integration setup, the only way to reverse the action is to delete the environment in LCS. Relinking or linking to another environment is not supported.

#### Validations for bringing your existing Power Platform environment

If you connect an existing Power Platform environment, the following validations must pass. Otherwise, the request won't proceed.

1. The **Enable D365 apps** option must be enabled when Dataverse is deployed in the Power Platform environment. This type of Dataverse deployment is the only type that supports Dynamics 365 apps, including connections to Finance and Operations apps.
2. The Power Platform environment must be in the same geography as Finance and Operations apps. For example, in LCS, you might see an Azure Region such as **West US 2**. In Microsoft Power Platform, the environment should be deployed in **United States**. This requirement is in place for performance and data residency reasons.
3. The user in LCS who is doing the Power Platform integration setup must be an administrator of the environment in Dataverse, and must have an applicable Finance, Supply Chain Management, or Commerce license assigned.

### Environments that already use dual-write, virtual tables, business events, or add-ins before Power Platform integration is enabled

For customers who enabled dual-write, virtual tables, or business events before the Power Platform integration feature existed, we are in the process of automatically creating Dataverse where it's missing in LCS.

You can verify that the Microsoft Power Platform integration was automatically enabled by viewing the **Power Platform Integration** section of the **Environment details** page for the Finance and Operations apps environment in LCS. If the integration was successfully enabled, the **Environment name** field will show the name of the integrated Microsoft Power Platform environment, and the **Status** field will be set to **Setup completed successfully**.

> [!NOTE]
> The Microsoft Power Platform integration will automatically be enabled for Finance and Operations apps environments that are already connected to a single Microsoft Power Platform environment and that already use business events functionality. However, these environments won't be able to use the new business events and data events functionality starting in release 10.0.22. The business events endpoints that are already used in these environments will be migrated to the Dataverse platform in version 10.0.23. At that point, the new business events and data events functionality will become available in the environments. Until then, business events will continue to work as they are currently configured in the environment.
> 
> For more information about the new business events and data events functionality that will be delayed for these environments until the migration is completed, see [Finance and Operations business events in Dataverse](/dynamics365-release-plan/2021wave2/finance-operations/finance-operations-crossapp-capabilities/new-scenarios-enabled-power-platform-convergence#finance-and-operations-business-events-in-dataverse) and [Finance and Operations CUD events in Dataverse](/dynamics365-release-plan/2021wave2/finance-operations/finance-operations-crossapp-capabilities/new-scenarios-enabled-power-platform-convergence#finance-and-operations-cud-events-in-dataverse) in the 2021 release wave 2 plan. 


## Troubleshooting the setup

Setup can fail at various stages of the deployment of the Dataverse-based environment.

Any time that the setup fails, an error message is shown. The following illustration shows an example of the error message for a dual-write setup failure.

![Error message for a dual-write setup failure.](media/Error.png)

Based on the error message, you might have to address licensing or capacity issues. After these issues have been fixed, you can select **Resume** in the **Power Platform integration** section of the **Environment details** page in LCS to finish the setup.

## Enable the integration for cloud-hosted development environments

You can manually enable the Microsoft Power Platform integration for cloud-hosted development environments by completing the procedures in this section. For information about how to deploy cloud development environments, see [Deploy and access development environments](../dev-tools/access-instances.md).

### Register an application in the Azure portal

> [!IMPORTANT]
> The Azure AD application must be created on the same tenant as the Finance and Operations app.

1. Open the [Azure portal](https://portal.azure.com).
2. Go to **Azure Active Directory \> App registrations**.
3. Select **New registration**, and enter the following information:

    - **Name** – Enter a unique name.
    - **Account type** – Select **Accounts in any organizational directory (Any Azure AD directory - Multitenant)**.
    - **Redirect URI** – Leave this field blank.

4. Select **Register**.
5. Make a note of the **Application (client) ID** value. You will need this value later.
6. Create a symmetric key for the application.

    1. Select **Certificates & secrets** in the left navigation pane for the new app registration.
    2. Select **New client secret**.
    3. Enter a description and an expiration date.
    4. Select **Save**.
    5. Copy the key in the **Value** field that is created. You will need this key value later.
 
### Add the Azure AD application as a Microsoft Power Platform user

After the Azure AD application has been created in the Azure portal, it must be added as a Microsoft Power Platform application user. 

1. In the Power Platform admin center, create the application user by following the steps in [Create an application user](/power-platform/admin/manage-application-users#create-an-application-user).
2. In the step where you select security roles to add for the application user, select **Finance and Operations Integration User**.

### Grant app permissions in Finance and Operations apps

Dataverse will use the Azure AD application that you created to call Finance and Operations apps. Therefore, the application must be trusted by Finance and Operations apps and associated with a user account that has the appropriate rights.

1. In Finance and Operations apps, go to **System administration \> Setup \> Azure Active Directory applications**.
2. Select **New** to add a row to the grid, and enter the following information:

    - **Client ID** – Enter the **Application (client) ID** value of the Azure AD application that you created earlier.
    - **Name** – Enter **Dataverse Integration** (or another name that you will recognize for the integration).
    - **User ID** – Select **PowerPlatformApp**.

> [!NOTE]
> The **PowerPlatformApp** user that is available has the appropriate permissions for Dataverse integrations with Finance and Operations apps. However, if this user doesn't exist, or if you want to use a different application user account, you can create or use any other user that has the following roles: **Business events security role**, **Dataverse Virtual entity application**, **Dataverse Virtual entity anonymous user**, and **Dataverse Virtual entity authenticated user**.

### Configure Finance and Operations apps to use the Azure AD application to connect to Dataverse 

1. Sign in to the Finance and Operations environment through Remote Desktop Protocol (RDP).
2. Copy the following Windows PowerShell script, and save it to the virtual machine (VM) for the Finance and Operations environment as a .ps1 file.

    ```powershell
    param(
        [Parameter(Mandatory = $false)]
        [switch]$Relaunched
    )

    $isRelaunched = $false
    if ($PSBoundParameters.ContainsKey("Relaunched"))
    {
        $isRelaunched = $Relaunched.IsPresent
    }

    if (-not ([Security.Principal.WindowsPrincipal] [Security.Principal.WindowsIdentity]::GetCurrent()).IsInRole([Security.Principal.WindowsBuiltInRole]::Administrator))
    {
        # Relaunch as an elevated process:
        Start-Process powershell.exe "-File", ('"{0}"' -f $MyInvocation.MyCommand.Path), "-Relaunched" -Verb RunAs
        exit
    }

    $aosWebsiteName = "AOSService"

    function Get-AosWebSitePhysicalPath()
    {
        if (Get-Service W3SVC | Where-Object status -ne 'Running')
        {
            #IIS service is not running, starting IIS Service.
            Start-Service W3SVC
        }

        $webSitePhysicalPath = (Get-Website | Where-Object { $_.Name -eq $aosWebsiteName }).PhysicalPath

        return $webSitePhysicalPath
    }

    function Get-WebConfigValue($Key)
    {
        $webroot = Get-AosWebSitePhysicalPath
        $webConfigPath = Join-Path $webroot "web.config"
        if (-not (Test-Path $webConfigPath))
        {
            Throw "Unable to find web.config file at '$($webConfigPath)'..."
        }

        [xml]$webConfigDocument = Get-Content $webConfigPath -ErrorAction stop
        $appSettingNode = $webConfigDocument.SelectSingleNode("/configuration/appSettings/add[@key='$($Key)']")
        if ($appSettingNode)
        {
            return $appSettingNode.Value
        }

        return $null
    }

    function Set-WebConfigValue($Key, [string]$Value)
    {
        $webroot = Get-AosWebSitePhysicalPath
        $webConfigPath = Join-Path $webroot "web.config"
        if (-not (Test-Path $webConfigPath))
        {
            Throw "Unable to find web.config file at '$($webConfigPath)'..."
        }

        [xml]$webConfigDocument = Get-Content $webConfigPath -ErrorAction stop
        $appSettingNode = $webConfigDocument.SelectSingleNode("/configuration/appSettings/add[@key='$($Key)']")
        if ($null -ne $appSettingNode)
        {
            Write-Host "Updating key '$($Key)' to value '$($Value)'..."
            $appSettingNode.Value = [string]$Value
        }
        else
        {
            Write-Host "Inserting new key '$($Key)' with value '$($Value)'..."
            $ns = New-Object System.Xml.XmlNamespaceManager($webConfigDocument.NameTable)
            $ns.AddNamespace("ns", $webConfigDocument.DocumentElement.NamespaceURI)
            $addElement = $webConfigDocument.CreateElement("add")
            $addElement.SetAttribute("key", $Key)
            $addElement.SetAttribute("value", $Value)
            $appSettings = $webConfigDocument.SelectSingleNode("//ns:appSettings", $ns)
            $appSettings.AppendChild($addElement) | Out-Null
        }

        $webConfigDocument.Save($webConfigPath)
        Write-Host
    }

    function Confirm-ValueOfType($Value, $Type)
    {
        if ($Type -eq "Uri")
        {
            try
            {
                New-Object System.Uri $Value | Out-Null
            }
            catch
            {
                Throw "Cannot parse '$($Value)' as a URL: $($_)"
            }
        }
        elseif ($Type -eq "Guid")
        {
            try
            {
                [Guid]::Parse($Value) | Out-Null
            }
            catch
            {
                Throw "Cannot parse '$($Value)' as a guid: $($_)"
            }
        }
        elseif ($Type -eq "String")
        {
            if ([string]::IsNullOrEmpty($Value))
            {
                Throw "String value cannot be empty."
            }
        }
    }

    function Update-WebConfigValueFromHost($Key, $Prompt, $Type)
    {
        $shouldUpdate = $true
        $currentValue = Get-WebConfigValue -Key $Key
        if ($currentValue)
        {
            if ($Type -eq "Secret")
            {
                $currentValue = "<redacted>"
            }

            while ($true)
            {
                $yesNoResponse = Read-Host -Prompt "Value for '$($Prompt)' is already set to '$($currentValue)'. Do you want to overwrite it? (y/n)"
                if ($yesNoResponse -eq "y" -or $yesNoResponse -eq "yes")
                {
                    $shouldUpdate = $true
                    break
                }
                elseif ($yesNoResponse -eq "n" -or $yesNoResponse -eq "no")
                {
                    $shouldUpdate = $false
                    break
                }
                else
                {
                    Write-Host "Did not recognize input value '$($yesNoResponse)' - please try again."
                }
            }
        }

        if ($shouldUpdate)
        {
            $value = Read-Host -Prompt "Enter $($Prompt)"
            Confirm-ValueOfType -Value $value -Type $Type
            if ($Type -eq "Secret")
            {
                # If value is blank, assume we are trying to clear it
                $secretValue = ""
                if (-not [string]::IsNullOrEmpty($value))
                {
                    $webroot = Get-AosWebSitePhysicalPath -ErrorAction stop
                    $webrootBinPath = Join-Path $webroot "bin"
                    $b2bInvitationHelperDllPath = Join-Path $webrootBinPath "Microsoft.Dynamics.AX.Security.B2BInvitationHelper.dll"
                    Add-Type -Path $b2bInvitationHelperDllPath

                    $encryptionEngine = [Microsoft.Dynamics.AX.Security.B2BInvitationHelper.Cryptor]::GetEncryptionEngine()
                    $secretValue = [System.Convert]::ToBase64String($encryptionEngine.Encrypt($value))
                }

                $value = $secretValue
            }

            Set-WebConfigValue -Key $Key -Value $value
        }
    }

    function Enable-Flight($FlightName)
    {
        Write-Verbose "Enabling flight '$($FlightName)'..."
        $webroot = Get-AosWebSitePhysicalPath -ErrorAction stop
        $webrootBinPath = Join-Path $webroot "bin"
        $environmentDllPath = Join-Path $webrootBinPath 'Microsoft.Dynamics.ApplicationPlatform.Environment.dll'
        Add-Type -Path $environmentDllPath

        $config = [Microsoft.Dynamics.ApplicationPlatform.Environment.EnvironmentFactory]::GetApplicationEnvironment()

        $ServerName = $config.DataAccess.DbServer
        $DatabaseName = $config.DataAccess.Database
        $UserId = $config.DataAccess.SqlUser
        $Password = $config.DataAccess.SqlPwd
        $EnableFlightQuery = "DECLARE @flightName NVARCHAR(100) = '$($FlightName)';
        IF NOT EXISTS (SELECT TOP 1 1 FROM SysFlighting WHERE flightName = @flightName)
            INSERT INTO SYSFLIGHTING(FLIGHTNAME,ENABLED, FLIGHTSERVICEID, PARTITION)
            SELECT @flightName, 1, 12719367, RECID FROM DBO.[PARTITIONS];
        ELSE
            UPDATE SysFlighting SET enabled = 1, flightServiceId = 12719367 WHERE flightName = @flightName;"

        Invoke-Sqlcmd -ServerInstance $ServerName -Database $DatabaseName -Username $UserId -Password $Password -Query $EnableFlightQuery
        Write-Verbose "Flight '$($FlightName)' has been enabled."
    }

    function Test-Settings()
    {
        $cdsApiPath = "sdkmessages";
        Write-Host "Testing setup by calling API '$($cdsApiPath)'..."
        $webroot = Get-AosWebSitePhysicalPath -ErrorAction stop
        $webrootBinPath = Join-Path $webroot "bin"
        $httpCommunicationDllPath = Join-Path $webrootBinPath "Microsoft.Dynamics.HttpCommunication.dll"
        Add-Type -Path $httpCommunicationDllPath

        try
        {
            $assembly = [System.Reflection.Assembly]::LoadFile($httpCommunicationDllPath)
            $loggerType = $assembly.GetType("Microsoft.Dynamics.HttpCommunication.Logging.InMemoryLogger")
            $bindingFlags = [System.Reflection.BindingFlags]::Instance -bor [System.Reflection.BindingFlags]::Public
            $loggerConstructor = $loggerType.GetConstructor($bindingFlags, $null, [System.Type]::EmptyTypes, $null)
            $logger = $loggerConstructor.Invoke($null)

            $cdsWebApiClient = New-Object Microsoft.Dynamics.HttpCommunication.Cds.CdsWebApiClient $logger;
            $bindingFlags = [System.Reflection.BindingFlags]::Instance -bor [System.Reflection.BindingFlags]::NonPublic
            $method = [Microsoft.Dynamics.HttpCommunication.Cds.CdsWebApiClient].GetMethod("GetWithStringResponse", $bindingFlags, $null, @([string]), $null)
            $task = $method.Invoke($cdsWebApiClient, @($cdsApiPath))
            $response = $task.GetAwaiter().GetResult()

            Write-Host $logger.LogContent.ToString()
            Write-Host "Received response with length: $($response.Length)" 
            Write-Host "Test complete."
        }
        catch
        {
            Write-Verbose $logger.LogContent.ToString()
            Throw "Failed while testing the new settings: $($_)"
        }
    }

    try
    {
        Update-WebConfigValueFromHost -Key "Infrastructure.CdsOrganizationUrl" -Prompt "Dataverse Organization URL" -Type "Uri"
        Update-WebConfigValueFromHost -Key "Infrastructure.CdsOrganizationId" -Prompt "Dataverse Organization id" -Type "Guid"
        Update-WebConfigValueFromHost -Key "Infrastructure.DataverseCommunicationAadTenantId" -Prompt "Dataverse AAD Tenant domain (e.g. Contoso.OnMicrosoft.com)" -Type "String"
        Update-WebConfigValueFromHost -Key "Infrastructure.DataverseCommunicationAppId" -Prompt "Dataverse AAD App id" -Type "Guid"
        Update-WebConfigValueFromHost -Key "Infrastructure.DataverseCommunicationAppSecretEncrypted" -Prompt "Dataverse AAD App secret" -Type "Secret"

        Enable-Flight -FlightName "BusinessEventsCDSIntegration"

        Write-Host "Restarting AOS..."
        Stop-Website -Name $aosWebSiteName
        Start-Website -Name $aosWebSiteName
        Write-Host "AOS has been restarted."

        Test-Settings
    }
    catch
    {
        Write-Error $_
    }

    if ($isRelaunched)
    {
        Write-Host "Press any key to continue..."
        [System.Console]::ReadKey() | Out-Null
    }

    ```

3. Run the script in Windows PowerShell, and follow the instructions. You will enter the following information:

    - **Dataverse Organization URL** – Enter the URL that is used to access Dataverse. For example, enter `https://contoso.crm.dynamics.com`. You can find this URL in the **Environment URL** field in the **Details** section of the environment details in the Power Platform admin center.
    - **Dataverse Organization ID** – You can find this ID in the **Organization ID** field in the **Details** section of the environment details in the Power Platform admin center.
    - **Dataverse AAD Tenant domain** – Enter the primary domain of the Azure AD tenant that is used by Dataverse. You can find this domain in the **Domain** field for the directory on the **Portal settings** page in the [Azure portal](https://portal.azure.com). Typically, it's also the domain segment of the administrator's email address. For example, if the email address is `admin@contoso.onmicrosoft.com`, the domain is `contoso.onmicrosoft.com`.
    - **Dataverse AAD app ID** – Enter the **Application (client) ID** value of the Azure AD application that you created earlier.
    - **Dataverse AAD app secret** – Enter the secret key value that was created earlier for the Azure AD apps.

## Verifying Power Platform integration status

The ```RetrieveFinanceAndOperationsIntegrationDetails``` API is available to validate the status of the Power Platform integration for the Power Platform environment. If the Power Platform environment is linked to a Finance and Operations apps environment through the Power Platform integration, the API will return the AAD tenant and environment details of the Finance and Operations apps environment.

The API can be used in troubleshooting to verify that the Power Platform integration is enabled for an environment. It is also recommended that the API be used in coding plug-ins, client forms, or other applications that must be aware of the Finance and Operations apps environment linked to the Power Platform environment.

**Request**
```http
GET [Organization URI]/api/data/v9.1/RetrieveFinanceAndOperationsIntegrationDetails
```

**Response**
```json
{
    "Url": "https://contoso.operations.dynamics.com",
    "TenantId": "72ad15fq-3m88-4e15-be25-8751c9bd0764",
    "Id": "b2106f5c-e218-4aac-841a-a59da4738eb4"
}
```

**Properties**

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| Environment URL<br>**Url**<br>***String*** | Read-only<br>Required | The URL of the Finance and Operations apps environment linked to the Power Platform environment through the Power Platform integration. |
| Tenant ID<br>**TenantId**<br>***GUID*** | Read-only<br>Required | The ID of the Azure AD tenant on which both the Finance and Operations apps environment and Power Platform environment are located. |
| Environment ID<br>**Id**<br>***GUID*** | Read-only<br>Required | The ID of the Finance and Operations apps environment linked to the Power Platform environment through the Power Platform integration. |

If the environment is not linked to a Finance and Operations apps environment through the Power Platform integration, the following error is returned in the API response:

| Error code | Message |
| --- | --- |
| 0x80048d0b | Dataverse instance is not integrated with Finance and Operations. |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
