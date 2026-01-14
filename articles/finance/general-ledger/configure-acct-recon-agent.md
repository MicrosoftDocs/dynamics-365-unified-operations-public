---
title: Set up and configure the Account Reconciliation Agent (production ready preview)
description: Learn how to set up and configure the Account Reconciliation Agent in Microsoft Dynamics 365 Finance.
author: twheeloc
ms.author: bking
ms.topic: overview
ms.date: 01/26/2026
ms.reviewer: twheeloc
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: LedgerConsolidate
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 9d8f55cb-b2cf-4e01-89cf-0e21f5c8ae1f
---

# Set up and configure the Account Reconciliation Agent (production ready preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

This article explains how system administrators can set up and configure the Account Reconciliation Agent in Microsoft Dynamics 365 Finance.

## Prerequisites

Before you can use the Account Reconciliation Agent, your system must meet the following requirements:

- You must be running Dynamics 365 Finance version 10.0.44 or later. To use Dynamics 365 ERP Model Context Protocol capabilities, you must be running Dynamics 365 Finance version 10.0.47 or later.
- The following features must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). If the features aren't shown in your system, select **Check for updates**.

    - (Preview) Immersive Home
    - (Production ready preview) Agent management
    - (Production ready preview) Account reconciliation agent
    - (Preview) Dynamics 365 ERP Model Context Protocol server (Optional)



- You must be running the following packages in the Power Platform admin center:

    - **Copilot for finance and operations apps**, version 1.0.3048.2 or later
    - **Copilot in Microsoft Dynamics 365 Finance**, version 1.0.3049.1 or later
  
 - Normally, the Microsoft Copilot Studio agents needed for the Account reconciliation agent to run are published automatically. But there might be data loss prevention (DLP) policies on your environment that prevent the publishing of these agents.
 - To check if the agents were successfully published, follow these steps:
1. go to Copilot Studio and find your environment.
2. Confirm that the following Microsoft Copilot Studio agents are published in that environment:
 - Account reconciliation agent
 - Account reconciliation amounts
 - Account reconciliation API
If the agents aren't published, see [Troubleshoot data policy enforcement for Copilot Studio](/microsoft-copilot-studio/admin-dlp-troubleshooting). 
Confirm that the agents are shared with the organization. 


Learn more in [Immersive Home overview](../../fin-ops-core/fin-ops/copilot/immersive-home.md).  

## Set up agent identity

> [!TIP]
> For security and ease of maintenance, we recommend that you use a dedicated identity for the agent.

### Set up agent identity users and assign security roles

Create agent identity user accounts in both Dataverse and Finance.

The user accounts must have the following security roles:

- Required Dataverse user roles:

    - Finance and Operations basic user
    - Account reconciliation agent role
    - Environment maker

- Required Finance user roles:

    - Account reconciliation agent
    - System user

### Create the required connections

The Account Reconciliation Agent uses connectors to Dataverse and Microsoft Copilot Studio to do its work. You must set up those connectors before you can use the agent. Additionally, an optional connection Fin & Ops Apps (Dynamics 365) should be created for the use of Dynamics 365 ERP Model Context Protocol.

To set up the connectors, follow these steps:

1. Sign in to [Power Apps](https://make.powerapps.com) using the newly created agent identity user.
1. In the left pane, select **Connections**.
1. At the top of the page, select **New connection**.
1. In the **Search** field, enter **Microsoft Dataverse**.
1. In the search results, find the **Microsoft Dataverse** connection, select **Create** for it, and follow the on-screen instructions to create the connector.
1. When you're prompted to sign in, sign in as the intended agent identity.

    You're returned to the **Connections** page. The new connector appears at the bottom of the list and is named after the agent identity that you signed in as when you created it.

1. At the top of the page, select **New connection**.
1. Search for the **Microsoft Copilot Studio (preview)** connection, select **Create** for it, and follow the on-screen instructions to create the connector. When you're prompted to sign in, sign in as the intended agent identity.

    You're returned to the **Connections** page. The new connector appears at the bottom of the list and is named after the agent identity that you signed in as when you created it.


1. At the top of the page, select **New connection**.
1. Search for the Fin & Ops Apps (Dynamics 365) connection.
1. Select **Create**, and follow the on-screen instructions to create the connector. When you're prompted to sign in, sign in as the intended agent identity.
You're returned to the Connections page. The new connector appears at the bottom of the list and is named after the agent identity that you signed in as when you created it.


### Update connection references and activate the triggering flows

To finish setting up agent identity, you must update the agent's connection references so that they point to the connections that you created. You must also activate the triggering Power Automate flows. This section provides a sample PowerShell script that you can use to complete both tasks.

To use the sample PowerShell script, follow these steps:

1. Copy the script, and save it as a .ps1 file.
1. Before you run the script, set the following four parameters at the top:

    - `environmentId` – Specify the ID of your Dataverse environment. You can find this ID in the Power Platform admin center.
    - `dataverseUrl` – Specify the URL of your Dataverse environment. You can find this URL in the Power Platform admin center.
    - `DVConnectionName` – Specify the name of the Dataverse connector to use. The connector is named after the agent identity that you signed in as when you [created it](#create-the-required-connections). You can find the name on the **Connections** page in Power Apps.
    - `MCSConnectionName` – Specify the name of the Copilot Studio connector to use. The connector is named after the agent identity that you signed in as when you [created it](#create-the-required-connections). You can find the name on the **Connections** page in Power Apps.
    - DynamicsAXConnectionName  – Specify the name of the Fin & Ops Apps connector to use. The connector is named after the agent identity that you signed in as when you created it. You can find the name on the **Connections** page in Power Apps.

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
    [Parameter(Mandatory=$false, HelpMessage="Dynamics 365 Finance and Operations connection name")]
    [string]$DynamicsAXConnectionName = ""
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
if ($DynamicsAXConnectionName)
{
    Set-ConnectionReferenceConnection -userProvidedConnectionName $DynamicsAXConnectionName -providerName "/providers/Microsoft.PowerApps/apis/shared_dynamicsax" -connectionReferenceLogicalName "msdyn_accountReconciliationApi.shared_dynamicsax.d2dc587e63f84ef68793f11e1a7b9ba3" -accessToken $accessToken
}

Write-Host
Write-Host 'Activating flows...'
Write-Host

Enable-TriggerFlow -flowId '3d0aef2d-ca97-ef11-a72d-000d3a36041c' -accessToken $accessToken # Account reconciliation - Acknowledge receipt of reconciliation event
Enable-TriggerFlow -flowId '5cd7d9b8-37a1-ef11-a72d-000d3a5a293d' -accessToken $accessToken # Account reconciliation - Agent execution request added
Enable-TriggerFlow -flowId '0274b722-b1a4-ef11-a72d-6045bd075f60' -accessToken $accessToken # Account reconciliation - Analyze exception data for amount mismatch rules
Enable-TriggerFlow -flowId '570a7d17-ac0a-f011-bae1-6045bd0139fb' -accessToken $accessToken # Account reconciliation - Complete agent activity request
Enable-TriggerFlow -flowId '75c311f8-1880-ef11-ac21-000d3a5aa6e6' -accessToken $accessToken # Account reconciliation - Determine work to be done
Enable-TriggerFlow -flowId '2b7f9cf7-0996-ef11-a72c-000d3a327b96' -accessToken $accessToken # Account reconciliation - Evaluate current exception against amount mismatch rules
Enable-TriggerFlow -flowId '9726ee57-f604-f011-bae1-6045bd0139fb' -accessToken $accessToken # Account reconciliation - Evaluate ledger not in subledger exception record
Enable-TriggerFlow -flowId 'e645e143-f804-f011-bae1-0022480b9145' -accessToken $accessToken # Account reconciliation - Evaluate subledger not in ledger exception record
Enable-TriggerFlow -flowId '782ddc43-cd97-ef11-a72d-000d3a36041c' -accessToken $accessToken # Account reconciliation - Get Voucher Summary Record
Enable-TriggerFlow -flowId '79284164-5a9c-ef11-a72d-000d3a5a293d' -accessToken $accessToken # Account reconciliation - Identify missing accounting
Enable-TriggerFlow -flowId 'fe418c1d-5b9c-ef11-a72d-000d3a5a293d' -accessToken $accessToken # Account reconciliation - Identify pending transfers
Enable-TriggerFlow -flowId '64fd40b7-d197-ef11-a72d-000d3a36041c' -accessToken $accessToken # Account reconciliation - Log recommended action"
Enable-TriggerFlow -flowId 'f8a02f0e-d097-ef11-a72d-000d3a36041c' -accessToken $accessToken # Account reconciliation - Mark reconciliation trigger complete
Enable-TriggerFlow -flowId '96e55129-0798-ef11-a72c-000d3a36041c' -accessToken $accessToken # Account reconciliation - Trigger reconciliation for individual exceptions
Enable-TriggerFlow -flowId 'e681a39e-1298-ef11-a72c-000d3a36041c' -accessToken $accessToken # Account reconciliation - Trigger subledger/ledger processing
Enable-TriggerFlow -flowId 'c2ad4a0d-228f-ef11-96d2-002248047a14' -accessToken $accessToken # Account reconciliation - When an individual exception event is added

Write-Host
Write-Host 'Account reconciliation agents are ready for use' -ForegroundColor Green
```
