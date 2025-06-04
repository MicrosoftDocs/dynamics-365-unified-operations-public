---
title: Set up and configure the Supplier Communications Agent (production ready preview)
description: Learn how to set up and configure the Supplier Communications Agent in Microsoft Dynamics 365 Supply Chain Management to streamline vendor communications.
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

Before you can use the Supplier Communications Agent, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.44 or later.

- In Supply Chain Management, the following features must be turned on in the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace. If the features aren't shown for your system, select **Check for updates**.
    - *(Preview) Immersive Home*
    - *(Production ready preview) Agent management*
    - *(Production ready preview) Supplier Communications Agent*

    Learn more about the *Immersive Home* feature in [Immersive Home overview](../../fin-ops-core/fin-ops/copilot/immersive-home.md).

- In the [Power Platform admin center](https://admin.powerplatform.microsoft.com/), make sure you are running the following versions of the following Dynamics 365 Apps in your Supply Chain Management environment. It's important that you install or update them in the following order:
    - First, install (or update to) *Copilot for finance and operations apps* version 1.0.3048.2 or later.
    - Then, install (or update to) *Copilot in Microsoft Dynamics 365 Supply Chain Management* version 1.1.3046.2 or later.

- Optional: If you want the agent to send emails automatically, turn on the *(Preview) Send follow-up emails to vendors with Supplier Communications Agent - automatically sending emails* feature in Feature management. We recommend that you turn off this feature for sandbox environments, where data such as purchase orders might not be up to date, or vendor email addresses might be missing.

## Set up an agent identity

The Supplier Communications Agent interacts with Dataverse and Microsoft Copilot Studio to do its work. You must select the identity that is used for these interactions and create the required connections.

> [!TIP]
> For security and ease of maintenance, we recommend that you use a dedicated identity for the agent.

### Set up agent identity users and assign security roles

Create agent identity user accounts in both Dataverse and Supply Chain Management. Assign the following security roles to them.

- Required Dataverse user roles:

    - *Finance and Operation Basic User*
    - *Supplier Communications Agent*
    - *Environment Maker*

- Required Supply Chain Management user roles:

    - *(Preview) Supplier Communications Agent*
    - *System user*

### Create required connections and activate the triggering flows

1. Sign in to [Power Apps](https://make.powerapps.com) as an environment administrator user.
1. In the left pane, select **Connections**.
1. Select **New connection**.
1. Use the search field in the upper right of the page to find the connection that is named *Microsoft Dataverse*.
1. Select **Create** for the connection, and then follow the on-screen instructions to create the connector. When you're prompted to sign in, sign in as the intended agent identity.
1. You're returned to the **Connections** list. The new connector appears at the bottom of the list. It's named after the agent identity that you signed in as when you created it.
1. Select **New connection**.
1. Find the connection that is named *Microsoft Copilot Studio (preview)*. 
1. Select **Create** for the connection, and then follow the on-screen instructions to create the connector. When you're prompted to sign in, sign in as the intended agent identity.
1. You're returned to the **Connections** list. The new connector appears at the bottom of the list. It's named after the agent identity that you signed in as when you created it.
1. Update the agent's connection references so that they point to the connections that you created. You must also activate the triggering flows. This article includes a [sample PowerShell script](#sample-script) that you can use to complete this step.

## Assign permissions to users who work with the agent

All Supply Chain Management users who work with the Supplier Communications Agent must be created as Dataverse users, if they aren't already Dataverse users. Learn how to create Dataverse users in [Create users](/power-platform/admin/create-users).

In addition, the following roles must be assigned to the users.

### Permissions for users who manage the agent configuration

- Required Dataverse user roles:

    - *Basic User*
    - *Finance and Operations Agent Configuration Manager*
    - *Finance and Operations Basic User*

- Required Supply Chain Management user roles:

    - *System user*
    - *Purchasing manager* and/or *Purchasing agent*

### Permissions for users who review agent results

- Required Dataverse user roles:

    - *Basic User*
    - *Finance and Operations Basic User*

- Required Supply Chain Management user roles:

    - *System user*
    - *Purchasing agent*

## Synchronize mailboxes with Dataverse

To enable the email analysis and delivery features of the Supplier Communications Agent, you must set up targeted mailboxes so that they are synchronized with Dataverse at the server level.

### Private mailbox

> [!IMPORTANT]
> Only the owner of a private mailbox can create an agent configuration and review agent results that are related to it. The owner must have permissions to [manage the agent configuration](./supplier-com-agent-setup.md#permissions-for-users-who-manage-the-agent-configuration) and [review agent results](./supplier-com-agent-setup.md#permissions-for-users-who-review-agent-results).

To set up a private mailbox, follow these steps.

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/) as a user who has a system administrator security role. (Although users who don't have an administrator role can enable synchronization for their own mailboxes, administrator approval might be required.)
1. Select the environment that you want to set up.
1. On the command bar, select **Settings**.
1. On the **Settings** page, under **Email**, select **Mailboxes**.
1. On the **Select a view** dropdown menu at the top of the page, select **Active Mailboxes**.
1. Select the checkbox for each mailbox that you want to use with the Supplier Communications Agent.
1. On the command bar, select **Test & enable mailbox** to enable synchronization for the selected mailboxes.

After a private mailbox is set up, the user who owns it must update the personalization settings to specify that all emails should be tracked.

To enable tracking of all emails for a private mailbox that you own, follow these steps.

1. Go to the URL of your environment.
1. Select the **Settings** button (gear symbol) in the upper right, and then select **Personalization Settings**.
1. In the **Set Personal Options** dialog, on the **Email** tab, in the **Track** field, select *All email messages*.
1. Select **OK**.

### Shared mailbox

If you're using a shared mailbox, create a queue so that all users who work on the shared mailbox can access email contents.

1. Sign in the [Power Platform admin center](https://admin.powerplatform.microsoft.com/) as user who has a system administrator security role.
1. Select the environment that you want to set up.
1. On the command bar, select **Settings**.
1. On the **Settings** page, under **Users + permissions**, select **Teams**.
1. Select **Create team**.
1. In the **New team** dialog, specify a name, business unit, and administrator as required. Set the **Team type** field to *Owner*.
1. Select **Next**.
1. In the **Add team members** dialog, add all the users who should have access to the shared mailbox.

    > [!IMPORTANT]
    > All users who create an agent configuration and review agent results that are related to this mailbox must be added as team members.

1. Select **Next**.
1. In the **Manage security roles** dialog, select **Finance and Operations Basic User** and **Basic User**, and then select **Save**.
1. Return to the **Settings** page for your environment, and then, under **Business** section, select **Queues**.
1. Select **New** to create a **Queue** entity record.
1. Enter a name, set the **Incoming email** field to the email address of the shared mailbox, and set the **Owner** field to the team that you created earlier.
1. Select **Save**.
1. A mailbox should now be created in the **Email settings** section. Select the mailbox name.
1. On the command bar, select **Test & Enable Mailboxes**.

    > [!TIP]
    > If this operation fails, review the **Alerts** section for the mailbox. If it includes an error message that states that approval is required, you must ask your global or Exchange admin to approve the mailbox. Learn more in [Approve email](/power-platform/admin/connect-exchange-online#approve-email).

1. Ensure that no other mailboxes that have the same email address are set up and active. 

    1. Return to the **Settings** page for your environment.
    1. Under **Email**, select **Mailboxes**. 
    1. On the **Select a view** dropdown menu at the top of the page, select **Active Mailboxes**.
    1. If any other mailboxes have the same email address as the shared mailbox email address, deactivate them.

Get detailed instructions in [Set up server-side synchronization of email](/power-platform/admin/set-up-server-side-synchronization-of-email-appointments-contacts-and-tasks).

### Troubleshoot server-side synchronization

Learn how to fix common issues that are related to server-side synchronization in [Troubleshooting and monitoring](/power-platform/admin/troubleshooting-monitoring-server-side-synchronization).

## Refresh data (optional)

After you enable the Supplier Communications Agent in a sandbox environment, we recommend that you do a data refresh. In this way, when you do testing in the sandbox environment, you can use the same data that you will have in the production environment. Learn how to do a database refresh in [Refresh database](/dynamics365/fin-ops-core/dev-itpro/database/database-refresh).

## <a name="own-email"></a>Set your email address as a vendor contact for testing

When you use the [review and apply purchase order changes received in vendor emails](supplier-com-agent-apply-email-changes.md) feature, the agent only reads emails from vendor domains. This means that when you are testing the system (and want to send/forward vendor emails from your own email account), you must add your email address as a vendor contact. To do so, follow these steps.

1. Go to **Procurement and sourcing** \> **Vendors** \> **All vendors**.
1. Create or select a vendor.
1. On the **Contact information** FastTab, add a row with your own email address (the one you will send/forward test messages from).

## <a name="sample-script"></a>Update connection references and enable triggering flows by using a PowerShell script

The following sample PowerShell script finishes [setting up the agent identity](#set-up-an-agent-identity) by updating the connection references for the agent and activating the triggering Power Automate flows.

To use the script, follow these steps.

1. Copy the script, and save it as a .ps1 file. 
1. Set the following parameters at the top of the script:

    - `environmentId` – Specify the ID of your Dataverse environment. You can find the ID in the Power Platform admin center.
    - `dataverseUrl` – Specify the URL of your Dataverse environment. You can find the URL in the Power Platform admin center.
    - `DVConnectionName` – Specify the name of the Dataverse connector to use. The connector is named after the agent identity that you signed in as when you [created](#set-up-an-agent-identity) it. You can find the name on the **Connections** page in Power Apps.
    - `MCSConnectionName` – Specify the name of the Copilot Studio connector to use. The connector is named after the agent identity that you signed in as when you [created](#set-up-an-agent-identity) it. You can find the name on the **Connections** page in Power Apps.

1. Customize the script as required.
1. Run the script from any PowerShell console.
1. When you're prompted to sign in, sign in as an environment administrator.

### Sample PowerShell Script to update connection references and enable triggering flows

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
if (-not (Get-Module -ListAvailable -Name Az.Accounts | Where-Object Version -ge 2.17)) {
    Write-Warning -Message 'Installing required version of module Az.Accounts'
    Install-Module -Name Az.Accounts -AllowClobber -Scope CurrentUser -Force -MinimumVersion 2.17
}

# Import required modules
Import-Module Az.Accounts -MinimumVersion 2.17
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
