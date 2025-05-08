---
title: Set up and configure the Supplier Communications Agent (production ready preview)
description: Learn how to set up and configure the Supplier Communications Agent in Dynamics 365 Supply Chain Management to streamline vendor communication.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 04/24/2025
ms.custom:
  - bap-template
  - ai-gen-docs-bap
  - ai-gen-description
  - ai-seo-date:04/24/2025
---

# Set up and configure the Supplier Communications Agent (production ready preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

This article explains how system administrators can set up and configure the Supplier Communications Agent.

## Prerequisites

To use the Supplier Communications Agent, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.44 or later.
- The following features must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). Select **Check for updates** if the features aren't shown on your system.
    - *(Preview) Immersive Home*
    - *(Production ready preview) Agent management*
    - *(Production ready preview) Supplier Communications Agent*

- You must be running the following packages in the Power Platform admin center:
    - *Copilot for finance and operations apps* version 1.0.3048.2 or later
    - *Copilot in Microsoft Dynamics 365 Supply Chain Management* version 1.1.3046.2 or later

- Optionally, you can also use feature management to turn on the following feature if you'd like to automatically send emails. We recommend that you turn it off for sandbox environments where data such as purchase orders might not be up to date or vendor emails could be missing.
    - *(Preview) Send follow-up emails to vendors with Supplier Communications Agent - automatically sending emails*

To learn more about the *Immersive Home* feature, go to [Immersive Home overview](../../fin-ops-core/fin-ops/copilot/immersive-home.md).

## Synchronize mailboxes with Dataverse

To enable email analysis and delivery features of the Supplier Communications Agent, you must set up targeted mailboxes to be synchronized with Microsoft Dataverse at the server level.

### Private mailbox

To set up a private mailbox, follow these steps:

1. Sign in the [Power Platform admin center](https://admin.powerplatform.microsoft.com/) as a user with a system administrator security role. (Users without an administrator role can enable synchronization on their own mailboxes, but this might still require administrator approval.)
1. Select the environment you want to set up.
1. On the command bar, select **Settings.**
1. On the **Settings** page, expand the **Email** section and select **Mailboxes**.
1. Open the **Select a view** drop-down list in the heading of the page and select *Active Mailboxes*.
1. Select the check box for each of the mailboxes that you want to use with the supplier communication agent.
1. On the command bar, select **Test & enable mailbox** to enable synchronization for the selected mailboxes.
1. Now you must assign security roles to enable the user who owns the mailbox to configure the agent. Go back to the **Settings** page, expand the **Users + permissions** section, and select **Users**.
1. Find and select the user that owns the private mailbox.
1. On the command bar, select **Manage security roles**.
1. In the **Manage security roles** dialog, select the *Finance and Operations Agent Configuration Manager* and *Basic User* roles.
1. Select **Save**.

After the private mailbox is set up, the user who owns the mailbox must update personalization settings to track all the emails. The owner of the mailbox must follow these steps:

1. Go to your environment URL.
1. Select the gear button on the top right and select **Personalization settings**.
1. Open the **Email** tab and set **Track** to *All email messages*.
1. Select **OK**.

### Shared mailbox

If you're using a shared mailbox, then create a queue to allow all users working on the shared mailbox to access email contents.

1. Sign in the [Power Platform admin center](https://admin.powerplatform.microsoft.com/) as user with a system administrator security role.
1. Select the environment you want to set up.
1. On the command bar, select **Settings**.
1. On the **Settings** page, expand the **Users + permissions** section and select **Teams**.
1. Select **Create team** at the top.
1. Fill out a name, business unit, and administrator as needed and set the **Team type** to *Owner*. Then select **Next**.
1. On the next page, add all the members that should have access to the shared mailbox. This allows the selected users to access email contents from the Supplier Communications Agent incoming email workspace in Supply Chain Management.
1. On the **Manage security roles** page, select *Finance and Operations Basic User* and *Basic User* and then select **Save**.
1. Go back to the **Settings** page, expand the **Business** section, and select **Queues**.
1. Select the **New** button on top to create a new **Queue** entity record.
1. Enter a **Name**, set **Incoming email** to the email address of the shared mailbox, and assign the **Owner** as the team that was created earlier. Then select **Save**.  
1. A new mailbox should now be created under **Email settings**. Select the mailbox name.
1. On the top command bar, select **Test & enable mailboxes**.  

    > [!TIP]
    > If this operation fails, check the **Alerts** section for the mailbox. If you see an error message that says approval is needed, you must ask your global or Exchange admin to approve the mailbox. Learn more in [Approve email](/power-platform/admin/connect-exchange-online#approve-email).  

1. Make sure that no other mailboxes with the same email address are set up and active. To check this, go back to the **Settings** page for your environment in the Power Platform Admin Center. Expand the **Email** section and select **Mailboxes**. Then, select *All Mailboxes* from the drop-down list at the top. Make sure that there's only one mailbox with the same shared mailbox email address. If more than one exists, deactivate all the others.
1. Now you must assign the required security role to the user who will configure the agent from the **Agents** page in Supply Chain Management. Go back to the **Settings** page, expand the **Users + permissions** section, and select **Users**.
1. Find and select the user responsible for configuring the agent.
1. On the command bar, select **Manage security roles**.
1. In the **Manage security roles** dialog, select the *Finance and Operations Agent Configuration Manager* role.
1. Select **Save**.

For detailed instructions, go to [Set up server-side synchronization of email](/power-platform/admin/set-up-server-side-synchronization-of-email-appointments-contacts-and-tasks).

### Troubleshoot server-side synchronization

To learn how to solve common issues related to server-side synchronization, go to [Troubleshooting and monitoring](/power-platform/admin/troubleshooting-monitoring-server-side-synchronization).

## Set up agent identity

> [!TIP]
> For reasons of security and ease of maintenance, we recommend that you use a dedicated identity for the agent.

### Set up agent identity users and assign security roles

Create agent identity user accounts in both Dataverse and Dynamics 365 Supply Chain Management. Assign them the security roles shown in the following lists.

- Required Dataverse user roles:
    - *Finance and Operation Basic User*
    - *Supplier Communications Agent*
    - *Environment Maker*

- Required Dynamics 365 Supply Chain Management user roles:
    - *(Preview) Supplier Communications Agent*
    - *System user*

### Create required connections and activate the triggering flows

The Supplier Communications Agent uses connectors to Dataverse and Microsoft Copilot Studio to perform its work. You must set them up before you can use the agent.

1. Open the [Power Apps Maker portal](https://make.powerapps.com) and sign in as an environment administrator user.
1. In the left navigator, select **Connections**.
1. At the top of the page, select **New connection**.
1. Use the **Search** field at the top-right of the page to find the connection with a **Name** of *Microsoft Dataverse*. Select the **Create** button for that row and follow the instructions on your screen. Sign in as the intended agent identity when prompted.
1. You return to the **Connections** list. Your new connector is now shown at the bottom of the list and is named after the agent identity you signed in with when creating it.
1. At the top of the page, select **New connection**.
1. Find the connection with a **Name** of *Microsoft Copilot Studio (preview)*. Select the **Create** button for that row and follow the instructions on your screen. Sign in as the intended agent identity when prompted.
1. You return to the **Connections** list. Your new connector is now shown at the bottom of the list and is named after the agent identity you signed in with when creating it.

Now, you must update the agent's connection references to point to the connections that you created. You must also activate the triggering flows. You can accomplish these tasks using the [sample PowerShell script](#sample-script) provided at the bottom of this article.

## Refresh data

After you enable the supplier communication agent on a sandbox environment, we recommend that you do a data refresh, which will let you test in the sandbox environment with the same data that you would have on your production environment. To learn how to do a database refresh, go to [Refresh database](/dynamics365/fin-ops-core/dev-itpro/database/database-refresh)

## Users for both Dataverse and Supply Chain Management

Existing Dynamics 365 Supply Chain Management users that should be able to read the agent emails and summaries must also be created as Dataverse users (if the aren't already). To learn how, go to [Create users](/power-platform/admin/create-users).

## <a name="sample-script"></a>Sample script to update connection references and enable triggering flows

This sample PowerShell script finishes [setting up the agent identity](#set-up-agent-identity) by updating the connection references for the agent and activating the triggering Power Automate flows. You must set the following parameters before running the script:

- `environmentId` - Your Dataverse environment ID. You can find it in the Power Platform admin center.
- `dataverseUrl` - Your Dataverse environment URL. You can find it in Power Platform admin center.
- `DVConnectionName` - The name of the Dataverse connector to use. The connector is named after the agent identity you signed in with when [creating](#set-up-agent-identity) it. You can find it on the **Connections** page of the Power Apps Maker portal.
- `MCSConnectionName` - The name of the Microsoft Copilot Studio connector to use. The connector is named after the agent identity you signed in with when [creating](#set-up-agent-identity) it. You can find it on the **Connections** page of the Power Apps Maker portal.

Copy the following script and save it as a `.ps1` file. Enter the parameter values at the top, customize it if needed, and run it from any PowerShell console. When you run the script, sign in as an environment administrator when prompted.

```powershell
Param(
   [Parameter(Mandatory=$true, HelpMessage="Dataverse environment id")]
   [string]$environmentId = "", 

   [Parameter(Mandatory=$true, HelpMessage="Dataverse environment URL")]
   [string]$dataverseUrl = "",

   [Parameter(Mandatory=$true, HelpMessage="Microsoft Dataverse connection name")]
   [string]$DVConnectionName = "",

   [Parameter(Mandatory=$true, HelpMessage="Microsoft Copilot Studio connection name")]
   [string]$MCSConnectionName = ""
)

# Check PS version
if ($PSVersionTable.PSVersion.Major -lt 7) {
    Write-Error 'This script requires at least PowerShell version 7' -ErrorAction Stop
}

# Install the required modules if not already installed
if (-not (Get-Module -ListAvailable -Name Microsoft.PowerApps.PowerShell)) {
    Write-Warning -Message 'Installing module Microsoft.PowerApps.PowerShell'
    Install-Module -Name Microsoft.PowerApps.PowerShell -AllowClobber -Scope CurrentUser
}

# Install the required modules if not already installed
if (-not (Get-Module -ListAvailable -Name Az.Accounts)) {
    Write-Warning -Message 'Installing module Az.Accounts'
    Install-Module -Name Az.Accounts -AllowClobber -Scope CurrentUser
}

# Import required modules
Import-Module Az.Accounts
Import-Module Microsoft.PowerApps.PowerShell

function Get-AccessToken {
    # Retrieve the access token for the Dataverse environment
    $accessToken = Get-AzAccessToken -ResourceUrl "$dataverseUrl" -AsSecureString
    $token = $accessToken.Token
    $userId = $accessToken.UserId
    Write-Host "Access token for $userId retrieved successfully." -ForegroundColor Green

    return $token
}

function Get-ConnectionId {
    param (
        [string]$userProvidedName,
        [string]$providerName
    )

    $matchedConnectionId = $null

    $connections = Get-PowerAppConnection -EnvironmentName $environmentId -ConnectorNameFilter $providerName
    foreach ($con in $connections) {
        if (($con.ConnectionName -eq $userProvidedName) -or ($con.DisplayName -eq $userProvidedName))
        {
            $matchedConnectionId = $con.ConnectionName
            break
        }
    }

    if ($null -eq $matchedConnectionId)
    {
        Write-Error -Message "Unable to find connection $userProvidedName ($providerName)" -ErrorAction Stop
    }

    Write-Host "Found connection id $matchedConnectionId for connection $userProvidedName"

    return $matchedConnectionId
}

function Get-ConnectionReferenceId {
    param(
        [string]$connectionReferenceLogicalName,
        [securestring]$accessToken
    )

    $uri = "$dataverseUrl/api/data/v9.2/connectionreferences?`$filter=connectionreferencelogicalname eq '$connectionReferenceLogicalName'"
    $response = Invoke-RestMethod -Method Get `
        -Uri $uri `
        -Authentication Bearer -Token $accessToken `
        -ContentType 'application/json'
        
    
    if ($null -eq $response) {
        Write-Error -Message "Connection reference not found for logical name $connectionReferenceLogicalName" -ErrorAction Stop
    }

    $connectionReferenceDisplayName = $response.value[0].connectionreferencedisplayname
    $connectionReferenceId = $response.value[0].connectionreferenceid

    Write-Host "Found connection reference id $connectionReferenceId for $connectionReferenceDisplayName ($connectionReferenceLogicalName)"

    return $connectionReferenceId
}

function Set-ConnectionReferenceConnection {
    param (
        [string]$connectionReferenceLogicalName,
        [string]$userProvidedConnectionName,
        [string]$providerName,
        [securestring]$accessToken
    )

    Write-Host "Updating connection reference ${connectionReferenceLogicalName}..."

    $connectionReferenceId = Get-ConnectionReferenceId -connectionReferenceLogicalName $connectionReferenceLogicalName -accessToken $accessToken
    $connectionId = Get-ConnectionId -userProvidedName $userProvidedConnectionName -providerName $providerName

    $body = @{
        "connectionid" = "$connectionId"
    } | ConvertTo-Json -Depth 1

    $uri = "$dataverseUrl/api/data/v9.2/connectionreferences($connectionReferenceId)"
    Write-Host "Updating connection reference URI: $uri with connection id $connectionId"

    Invoke-RestMethod -Method Patch `
        -Uri $uri `
        -Authentication Bearer -Token $accessToken `
        -ContentType 'application/json' `
        -Body $body
   
    Write-Host "Connection reference updated successfully." -ForegroundColor Green
    Write-Host
}

function ValidateUserEnvironment {
    param (
        [string]$environmentId
    )

    $env = Get-PowerAppEnvironment -EnvironmentName $environmentId
    if ($null -eq $env) {
        Write-Error -Message "Environment $environmentId was not found" -ErrorAction Stop
    }

    $displayName = $env.DisplayName
    Write-Host "Connected to environment: $displayName ($environmentId)"
}

function Enable-TriggerFlow {
    param (
        [string]$flowId,
        [securestring]$accessToken
    )

    $flowUri = "$dataverseUrl/api/data/v9.2/workflows($flowId)"
    $flow = $null

    Write-Host "Enabling flow $flowId with uri $flowUri"

    try {
        $flow = Invoke-RestMethod -Method Get `
            -Uri $flowUri `
            -Authentication Bearer -Token $accessToken `
            -ContentType 'application/json'
    }
    catch {
        Write-Error -Message $_.Exception -ErrorAction Stop
    }

    $displayName = $flow.name
    Write-Host "Activating flow $displayName for id $flowId"

    $body = @{
        "statecode" = 1  # Activated
        "statuscode" = 2 # Activated
    } | ConvertTo-Json -Depth 1 -Compress
    
    try {
        Invoke-RestMethod -Method Patch `
            -Uri $flowUri `
            -Authentication Bearer -Token $accessToken `
            -ContentType 'application/json' `
            -Body $body
    }
    catch {
        Write-Error -Message $_.Exception -ErrorAction Stop
    }

    Write-Host "Activated flow $displayName" -ForegroundColor Green
    Write-Host
}

# Actual script body

Write-Host
Write-Host "Authenticating interactively..."
Write-Host

Connect-AzAccount -UseDeviceAuthentication
$accessToken = Get-AccessToken
ValidateUserEnvironment -environmentId $environmentId

Write-Host
Write-Host 'Setting up connection references...'
Write-Host

Set-ConnectionReferenceConnection `
    -userProvidedConnectionName $DVConnectionName `
    -providerName "/providers/Microsoft.PowerApps/apis/shared_commondataserviceforapps" `
    -connectionReferenceLogicalName "new_sharedcommondataserviceforapps_6ae5d" `
    -accessToken $accessToken

Set-ConnectionReferenceConnection `
    -userProvidedConnectionName $MCSConnectionName `
    -providerName "/providers/Microsoft.PowerApps/apis/shared_microsoftcopilotstudio" `
    -connectionReferenceLogicalName "msdyn_sharedmicrosoftcopilotstudio_0be09" `
    -accessToken $accessToken

Write-Host
Write-Host 'Activating flows...'
Write-Host

Enable-TriggerFlow -flowId 'c1061034-ff20-f011-9989-002248095ade' -accessToken $accessToken # (Self Heal) Speed up updates in purchase orders with Supplier Communications Agent
Enable-TriggerFlow -flowId '1db577aa-83fe-ef11-bae1-000d3a34a571' -accessToken $accessToken # Speed up updates in purchase orders with Supplier Communications Agent
Enable-TriggerFlow -flowId 'acd7bb36-07a1-ef11-a72d-6045bd0390ae' -accessToken $accessToken # Send follow-up emails to vendors with Supplier Communications Agent

Write-Host
Write-Host 'Supplier communications agent is ready for use' -ForegroundColor Green
```
