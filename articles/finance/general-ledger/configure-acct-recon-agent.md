---
title: Set up and configure the Account reconciliation agent (production ready preview)
description: Learn how to set up and configure the Account reconciliation agent in Microsoft Dynamics 365 Finance.
author: twheeloc
ms.author: bking
ms.topic: overview
ms.date: 08/03/2026
ms.reviewer: twheeloc
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: LedgerConsolidate
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 9d8f55cb-b2cf-4e01-89cf-0e21f5c8ae1f
---

# Set up and configure the Account reconciliation agent (production ready preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

> [!NOTE]
> Microsoft is enhancing the Account Reconciliation Agent to give customers more configuration flexibility and predictable credit consumption. Until these improvements are released, the Microsoft team must activate this agent. To request activation and be guided through the process, complete this [form](https://forms.office.com/r/wCREkgRH6D).

This article explains how system administrators can set up and configure the Account reconciliation agent in Microsoft Dynamics 365 Finance.
Customers can use Power Platform admin center to set up and configure the Account reconciliation agent. For more information, see [Deploy Dynamics 365 agents by using the agent deployment wizard](../../fin-ops-core/dev-itpro/copilot/agent-deployment.md).

>[!NOTE]
>To improve performance and response quality, Microsoft might automatically update the AI model that the service uses. As a result, the model that generates responses might differ from the one displayed in the user interface.

## Prerequisites

Before you use the Account reconciliation agent, make sure your system meets the following requirements:

- You're running Dynamics 365 Finance version 10.0.46 or later.
- You turn on the following features in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). If the features don't appear in your system, select **Check for updates**.
  - Immersive Home
  - Agent management
  - (Production ready preview) Account reconciliation agent

- You're running the following packages in the Power Platform admin center:

  - **Copilot for finance and operations apps**, version 1.0.3048.2 or later
  - **Copilot in Microsoft Dynamics 365 Finance**, version 1.0.3049.1 or later
  
The Microsoft Copilot Studio agents needed for the Account reconciliation agent to run are published automatically. But there might be data loss prevention (DLP) policies on your environment that prevent the publishing of these agents. To check if the agents are successfully published, follow these steps:

1. Go to Copilot Studio and find your environment.
1. Confirm that the following Microsoft Copilot Studio agents are published in that environment:

- Account reconciliation agent

If the agents aren't published, see [Troubleshoot data policy enforcement for Copilot Studio](/microsoft-copilot-studio/admin-dlp-troubleshooting).
Confirm that the agents are shared with the organization.

Learn more in [Immersive Home overview](../../fin-ops-core/fin-ops/copilot/immersive-home.md).  

### Set up agent identity
>
> [!TIP]
> For security and ease of maintenance, use a dedicated identity for the agent.

### Set up agent identity users and assign security roles

Create agent identity user accounts in both Dataverse and Finance.

Assign the following security roles to the user accounts:

- Required Dataverse user roles:

  - Finance and Operations basic user
  - Account reconciliation agent role
  - Environment maker

- Required Finance user roles:

  - Account reconciliation agent
  - System user

> [!NOTE]
> The system agent security role is exempt from Dynamics 365 finance and operations user license requirements. For more information, see [Use Model Context Protocol for finance and operations apps](../../fin-ops-core/dev-itpro/copilot/copilot-mcp.md#agent-licenses).

### Deploy the agent
>
> [!NOTE]
> You can deploy the agent in two ways. The first way is to use the new Agent Deployment Wizard experience. The second way is to manually create the required connections and activate the flows by using a PowerShell script. The following sections describe the two ways.

### Deployment via the Agent deployment wizard

The Agent deployment wizard simplifies the process of setting up required connections for the agent and activates the necessary flows.  

### Access the Deployment wizard

To access the Deployment wizard, follow these steps:

1. Open Copilot Hub in Power Platform admin center and select Dynamics 365.
1. If you don't see Copilot Hub in Power Platform Admin Center, check if the feature flag ShowDynamics365ERPInCopilotHub is enabled.
1. Select the target environment.
1. Choose the Accounts reconciliation agent.
1. Select **Add** to launch the Agent deployment wizard.

### Deploy the Agent using the Wizard

Prerequisites - The wizard checks if the target environment meets all required prerequisites for the Accounts reconciliation agent. It also includes an optional action to refresh the virtual entities for the Accounts reconciliation agent. While this step is optional, it's recommended that you refresh the virtual entities for the proper activation of the Accounts reconciliation agent.  

### Select the Agent identity

Each agent runs under a dedicated agent user identity. In this step, you select the previously created user as part of the Set up Agent identity step.

### Connecting the Agent

In this step, the wizard asks you to select the connection reference for Microsoft Dataverse and Copilot Studio. If the connection reference doesn't exist, you can create it. To create the connection reference, select the **Plus** icon next to the connection reference dropdown. Create connection references by using the agent identity you set up previously, as mentioned on the UI.

After you select or create a connection reference for each of the resources or applications, select **Connect the Agent** to set up the connection references for the agent.  

Next, activate all Power Automate flows used by the agent, as part of the second step on this page.

### Enabling the agent

The final step makes the agent available for use.
To enable the agent, follow these steps:

1. Publish the agent bot in Copilot Studio.
1. Verify that the agent is enabled and available in the target environment.
1. When you enable the agent, it becomes active and ready for use.

For more information about Agent Deployment wizard, see [Deploy Dynamics 365 agents by using the agent deployment wizard](../../fin-ops-core/dev-itpro/copilot/agent-deployment.md).

### Manual deployment of the agent

#### Create the required connections

The Account reconciliation agent uses connectors to Dataverse and Microsoft Copilot Studio to do its work. Set up those connectors before you use the agent.

To set up the connectors, follow these steps:

1. Sign in to [Power Apps](https://make.powerapps.com) by using the newly created agent identity user.
1. In the left pane, select **Connections**.
1. At the top of the page, select **New connection**.
1. In the **Search** field, enter **Microsoft Dataverse**.
1. In the search results, find the **Microsoft Dataverse** connection, select **Create** for it, and follow the on-screen instructions to create the connector.
1. When you're prompted to sign in, sign in as the intended agent identity.

    You're returned to the **Connections** page. The new connector appears at the bottom of the list and is named after the agent identity that you signed in as when you created it.

1. At the top of the page, select **New connection**.
1. Search for the **Microsoft Copilot Studio (preview)** connection, select **Create** for it, and follow the on-screen instructions to create the connector. When you're prompted to sign in, sign in as the intended agent identity.

    You're returned to the **Connections** page. The new connector appears at the bottom of the list and is named after the agent identity that you signed in as when you created it.

#### Update connection references and activate the triggering flows

To finish setting up agent identity, update the agent's connection references so that they point to the connections that you created. You must also activate the triggering Power Automate flows. This section provides a sample PowerShell script that you can use to complete both tasks.

To use the sample PowerShell script, follow these steps:

1. Copy the script, and save it as a .ps1 file.
1. Before you run the script, set the following four parameters at the top:

    - `environmentId` – Specify the ID of your Dataverse environment. You can find this ID in the Power Platform admin center.
    - `dataverseUrl` – Specify the URL of your Dataverse environment. You can find this URL in the Power Platform admin center.
    - `DVConnectionName` – Specify the name of the Dataverse connector to use. The connector is named after the agent identity that you signed in as when you [created it](#create-the-required-connections). You can find the name on the **Connections** page in Power Apps.
    - `MCSConnectionName` – Specify the name of the Copilot Studio connector to use. The connector is named after the agent identity that you signed in as when you [created it](#create-the-required-connections). You can find the name on the **Connections** page in Power Apps.

1. Customize the script as you require.
1. Run the script from any PowerShell console. When you're prompted to sign in, sign in as an environment administrator.

#### Sample script to update connection references and enable triggering flows

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
    try {
    # Retrieve the access token for the Dataverse environment
    $accessToken = Get-AzAccessToken -ResourceUrl "$dataverseUrl" -AsSecureString
    $token = $accessToken.Token
    $userId = $accessToken.UserId

    Write-Host "Access token for $userId retrieved successfully." -ForegroundColor Green
    } catch {
        Write-Host "Failed to retrieve access token. Error: $($_.Exception.Message)" -ForegroundColor Red
    }
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
    -connectionReferenceLogicalName "msdyn_sharedcommondataserviceforapps_f9321" `
    -accessToken $accessToken
Set-ConnectionReferenceConnection `
    -userProvidedConnectionName $MCSConnectionName `
    -providerName "/providers/Microsoft.PowerApps/apis/shared_microsoftcopilotstudio" `
    -connectionReferenceLogicalName "msdyn_sharedmicrosoftcopilotstudio_462f2" `
    -accessToken $accessToken

Write-Host
Write-Host 'Activating flows...'
Write-Host

Enable-TriggerFlow -flowId '570a7d17-ac0a-f011-bae1-6045bd0139fb' -accessToken $accessToken # Account reconciliation - Complete agent activity request
Enable-TriggerFlow -flowId '75c311f8-1880-ef11-ac21-000d3a5aa6e6' -accessToken $accessToken # Account reconciliation - Determine work to be done
Enable-TriggerFlow -flowId '13dd7af5-f73b-f111-bec6-0022480882fa' -accessToken $accessToken # Account reconciliation - Generate and log recommended action
Enable-TriggerFlow -flowId 'd3314698-792b-f111-88b5-00224808ca0b' -accessToken $accessToken # Account reconciliation - Agent execution is triggered

Write-Host
Write-Host 'Account reconciliation agents are ready for use' -ForegroundColor Green
 ```
