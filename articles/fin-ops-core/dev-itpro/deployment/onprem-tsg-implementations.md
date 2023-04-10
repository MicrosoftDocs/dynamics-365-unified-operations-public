---
title: Scripts for resolving issues in on-premises environments
description: This article will serve as a central repository for scripts that you can use to fix issues in on-premises environments.
author: faix
ms.date: 01/02/2023
ms.topic: article
ms.prod: dynamics-365 
ms.service:
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this article to]
audience: Developer
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: osfaixat
ms.search.validFrom: 2019-11-30
ms.dyn365.ops.version: Platform update 30
search.app:
  - financeandoperationsonprem-docs
---

# Scripts for resolving issues in on-premises environments
[!include [banner](../includes/banner.md)]

This article will serve as a central repository for scripts that you can use to fix issues in on-premises environments. These scripts must usually be run as pre-deployment or post-deployment scripts.

For more information about how to resolve issues in on-premises environments, see [Troubleshoot on-premises deployments](troubleshoot-on-prem.md).

## Prepare your environment for script execution

1. Configure the execution of pre-deployment and post-deployment scripts. For more information, see [Local agent pre-deployment and post-deployment scripts](../lifecycle-services/pre-post-scripts.md).
2. Add the following code to your Predeployment.ps1 script.

    ```powershell
    # This has to be filled out
    # $agentShare = '<Agent-share path>' # E.g '\\LBDContosoShare\agent''

    $agentShare = '\\servername\D365FFOAgent'
    Write-Output "AgentShare is set to $agentShare"

    # The scripts make the assumption that the wp folder only contains one folder for the environment name.
    # If you have multiple folders in there from older deployments, then please remove those.
    # It is not recommended to use the same agent share for multiple environments.

    #& $agentShare\scripts\TSG_UpdateFRDeployerConfig.ps1 -agentShare $agentShare

    #& $agentShare\scripts\TSG_WindowsAzureStorage.ps1 -agentShare $agentShare

    #& $agentShare\scripts\TSG_SysClassRunner.ps1 -agentShare $agentShare
    
    #& $agentShare\scripts\TSG_RemoveFilesFromZip.ps1 -agentShare $agentShare -filesToRemove 'Packages\TaxEngine\bin\Microsoft.Dynamics365.ElectronicReportingMapping.dll','Packages\TaxEngine\bin\Microsoft.Dynamics365.ElectronicReportingMapping.pdb','Packages\TaxEngine\bin\Microsoft.Dynamics365.ElectronicReportingServiceContracts.dll','Packages\TaxEngine\bin\Microsoft.Dynamics365.ElectronicReportingServiceContracts.pdb','Packages\TaxEngine\bin\Microsoft.Dynamics.ElectronicReporting.Instrumentation.dll','Packages\TaxEngine\bin\Microsoft.Dynamics.ElectronicReporting.Instrumentation.pdb','Packages\TaxEngine\bin\Microsoft.Dynamics365.LocalizationFrameworkCore.dll','Packages\TaxEngine\bin\Microsoft.Dynamics365.LocalizationFrameworkCore.pdb','Packages\TaxEngine\bin\Microsoft.Dynamics365.LocalizationFrameworkForAx.dll','Packages\TaxEngine\bin\Microsoft.Dynamics365.LocalizationFrameworkForAx.pdb'

    #& $agentShare\scripts\TSG_EnableGMSAForAOS.ps1 -agentShare $agentShare -gmsaAccount contoso\svc-AXSF$
    #& $agentShare\scripts\TSG_EnableDixfService.ps1 -agentShare $agentShare -gmsaAccount contoso\svc-Dixf$ -DMFShare "\\servername\dixf-share"
    ```

3. From the relevant section of this article, copy the code that you require to fix your issue, and paste it into a new file. Save this file in the same folder where your Predeployment.ps1 script is stored. The file name must match the title of the section that you copied the code from. Repeat this step for other issues that you must fix.
4. In the Predeployment.ps1 script, in the code that you added earlier, uncomment the lines that invoke the scripts that you want to use.

## <a name="sysclassrunner"></a>TSG\_SysClassRunner.ps1

The following script is used to fix an issue that occurs when SysClassRunner is run in some versions of the platform. For more information about this issue, see [SysClassRunner doesn't run successfully](troubleshoot-on-prem.md#SysClassRunner).

```powershell
param (
    [Parameter(Mandatory=$true)]
    [string]
    $agentShare = ''
)

$delete = @("Microsoft.Diagnostics.Tracing.TraceEvent.dll", "Microsoft.AI.Agent.Intercept.dll", "Microsoft.AI.DependencyCollector.dll", "Microsoft.AI.DependencyCollector.xml", "Microsoft.AI.PerfCounterCollector.dll", "Microsoft.AI.ServerTelemetryChannel.dll", "Microsoft.AI.ServerTelemetryChannel.xml", "Microsoft.AI.Web.dll", "Microsoft.AI.Web.xml", "Microsoft.AI.WindowsServer.dll","Microsoft.AI.WindowsServer.xml", "Microsoft.ApplicationInsights.dll", "Microsoft.ApplicationInsights.xml")

$ErrorActionPreference = "Stop"

$basePath = Get-ChildItem $agentShare\wp\*\StandaloneSetup-*\Apps |
    Select-Object -First 1 -Expand FullName

#Some customers experience an unexpected behavior with the previous command.
if($basePath -notmatch "\AOS")
{
    $basePath = Join-Path $basePath -ChildPath "\AOS" 
}

$basePath = Join-Path $basePath -ChildPath "AXServiceApp\AXSF\Code" 

if(!(Test-Path $basePath))
{
    Write-Error "Basepath: $basePath , not found" -Exception InvalidOperation
}

foreach( $file in $delete)
{
    if(Test-Path -Path "$basePath\$file")
    {
        Remove-Item -Path "$basePath\$file"
    }
}

$axConfig = Join-Path $basePath -ChildPath "AXService.exe.config"

if(!(Test-Path $axConfig))
{
    Write-Error "Unable to find AxService.exe.config in path: $axConfig" -Exception InvalidOperation
}

Write-Output "Found config: $axConfig"

[xml]$xml = get-content $axConfig
$xml.SelectNodes("//*[@name = 'Microsoft.AI.Agent.Intercept']/..") | ForEach-Object {
    $_.bindingRedirect.oldVersion = "0.0.0.0-2.4.0.0"
    $_.bindingRedirect.newVersion = "2.4.0.0"
}

if($xml.SelectNodes("//*[@name = 'Microsoft.ApplicationInsights']").Count -eq 0)
{
    [xml]$newNode = @"
    <dependentAssembly xmlns="urn:schemas-microsoft-com:asm.v1">
        <assemblyIdentity name="Microsoft.ApplicationInsights" publicKeyToken="31bf3856ad364e35" culture="neutral" />
        <bindingRedirect oldVersion="0.0.0.0-2.9.0.0" newVersion="2.9.0.0" />
    </dependentAssembly>
"@
    $xml.configuration.runtime.assemblyBinding.AppendChild($xml.ImportNode($newNode.dependentAssembly, $true))
    
}

$xml.save($axConfig)

Write-Output "TSG SysClassRunner script succeeded"
```

## <a name="frdeployer"></a>TSG\_UpdateFRDeployerConfig.ps1

The following script is used to fix an issue that occurs when Financial Reporting is deployed in some versions of the platform. For more information about this issue, see [Could not load file or assembly EntityFramework](troubleshoot-on-prem.md#FREntityFramework).

```powershell
param (
    [Parameter(Mandatory=$true)]
    [string]
    $agentShare = ''
)

$frConfig = Get-ChildItem $agentShare\wp\*\StandaloneSetup-*\Apps\FR\Deployment\FinancialReportingDeployer.exe.config |
    Select-Object -First 1 -Expand FullName

if( -not $frConfig)
{
    Write-Output "Unable to find FinancialReportingDeployer.exe.Config"
    return
}

Write-Output "Found config: $frConfig"

[xml]$xml = get-content $frConfig

$nodeList = $xml.GetElementsByTagName("loadFromRemoteSources")

if($nodeList.Count -eq 0)
{
    # Create the node 
    $newNode = $xml.CreateNode("element","loadFromRemoteSources","")
    $newNode.SetAttribute("enabled","true")
    # Find the parent
    $nodeList = $xml.GetElementsByTagName("runtime")
    $runtimeNode = $nodeList[0]
    $runtimeNode.AppendChild($newNode)
    # Save doc
    $xml.save($frConfig)
    Write-Output "Inserted new node: "$newNode.Name
}
else
{
    $node = $nodeList[0]

    $attribute = $node.Attributes.GetNamedItem("enabled")

    if($attribute.Value -eq "true")
    {
        Write-Output "Node already exists: "$node.Name
    }

    else
    {
        Write-Output "Node already exists but attribute is incorrect: " $attribute.Name "is" $attribute.Value
    }
}
```

## <a name="azurestorage"></a>TSG\_WindowsAzureStorage.ps1

The following script is used to fix an issue where files can't be downloaded or exported in some versions of the platform.

```powershell
param (
    [Parameter(Mandatory=$true)]
    [string]
    $agentShare = ''
)
$ErrorActionPreference = "Stop"

$delete = @("Microsoft.WindowsAzure.Storage.dll", "Microsoft.WindowsAzure.Storage.xml")

$basePath = Get-ChildItem $agentShare\wp\*\StandaloneSetup-*\Apps |
    Select-Object -First 1 -Expand FullName

#Some customers experience an unexpected behavior with the previous command.
if($basePath -notmatch "\AOS")
{
    $basePath = Join-Path $basePath -ChildPath "\AOS" 
}

$basePath = Join-Path $basePath -ChildPath "AXServiceApp\AXSF\Code" 

if(!(Test-Path $basePath))
{
    Write-Error "Basepath: $basePath , not found" -Exception InvalidOperation
}

foreach( $file in $delete)
{
    if(Test-Path -Path "$basePath\$file")
    {
        Remove-Item -Path "$basePath\$file"
    }
}

Write-Output "TSG WindowsAzureStorage script succeeded"
```


## <a name="taxengine"></a>TSG\_RemoveFilesFromZip.ps1

The following script is used to fix an issue that occurs for some customers who were previously on versions 10.0.5 through 10.0.9. Due to how the prepare process works, there are some older versions of DLLs that remain in the TaxEngine folder, which in newer releases have been moved to different module folders. This script ensures that these DLLs are removed from the downloaded asset, before being deployed to the AOS nodes.

```powershell
[CmdletBinding()]
param
(
    [Parameter(Mandatory)]
    [ValidateNotNullOrEmpty()]
    [ValidateScript({ Test-Path -Path $_ })]
    [string] $agentShare,

    [ValidateNotNullOrEmpty()]
    [string[]]$filesToRemove
)

#requires -Version 5
$ErrorActionPreference = 'Stop'
$InformationPreference = 'Continue'
$files = @()

[Reflection.Assembly]::LoadWithPartialName('System.IO.Compression')

if(! (Test-Path $AgentShare))
{
    throw "The path provided for the agentshare is not valid/accessible."
}

ForEach($file in $FilesToRemove)
{
    if(!$file.StartsWith('Packages'))
    {
        throw "The path of $file does not start with Packages."
    }
    $files += $file.Replace('\', '/')
} 

$basePath = Get-ChildItem $AgentShare\wp\*\StandaloneSetup-*\Apps | Select-Object -First 1 -Expand FullName

#Some customers experience an unexpected behavior with the previous command.
if($basePath -notmatch "\AOS")
{
    $basePath = Join-Path $basePath -ChildPath "\AOS" 
}

$basePath = Join-Path $basePath -ChildPath "AXServiceApp\AXSF\Code"
$zipfile = Join-Path $basePath -ChildPath "Packages.zip"

try
{
    $stream = New-Object IO.FileStream($zipfile, [IO.FileMode]::Open)
    $mode   = [IO.Compression.ZipArchiveMode]::Update
    $zip    = New-Object IO.Compression.ZipArchive($stream, $mode)

    ($zip.Entries | ? { $files -contains $_.FullName }) | % { $_.Delete() } | Write-Host
}
catch
{
    throw 'An Error Occurred'
}
finally
{
    $zip.Dispose()
    $stream.Close()
    $stream.Dispose() 
}

```

## <a name="useGMSA"></a>TSG\_EnableGMSAForAOS.ps1

The following script is used to change the account the AOS runs under from an Active Directory (AD) user to a group Managed Service Account (gMSA).

> [!NOTE]
> This script can only be used starting with version 10.0.17.
> You will need to reinstall the printers on each AOS node as they are not available to the gMSA account. For more information, see [Install network printer devices in on-premises environments](../analytics/install-network-printer-onprem.md).
> This script has been updated to work with Application version 10.0.32, but also works with older Application versions.

```powershell
param (
    [Parameter(Mandatory)]
    [ValidateNotNullOrEmpty()]
    [ValidateScript({ Test-Path -Path $_ })]
    [string] $agentShare,

    [Parameter(Mandatory=$true)]
    [string]
    $gmsaAccount
)

$ErrorActionPreference = "Stop"

$basePath = Get-ChildItem $agentShare\wp\*\StandaloneSetup-*\ |
    Select-Object -First 1 -Expand FullName

if(!(Test-Path $basePath))
{
    Write-Error "Basepath: $basePath , not found" -Exception InvalidOperation
}

$configJsonPath = "$basePath\config.json"

$configJson = Get-Content $configJsonPath | ConvertFrom-Json

$updatedComponents = @()
foreach ($component in $configJson.components)
{
    if($component.name -eq "AOS")
    {
        $component.parameters.infrastructure.principalUserAccountType.value = "ManagedServiceAccount"
        $component.parameters.infrastructure.principalUserAccountName.value = $gmsaAccount
    }

    if($component.name -eq "Bootstrap" -and $component.parameters.infrastructure)
    {
        $component.parameters.infrastructure.principalUserAccountType.value = "ManagedServiceAccount"
        $component.parameters.infrastructure.principalUserAccountName.value = $gmsaAccount
    }

    if($component.name -eq "ReportingServices")
    {
        $component.parameters.accountListToAccessReports.value = $gmsaAccount
    }

    $updatedComponents += $component
}

$configJson.components = $updatedComponents

$configJson | ConvertTo-Json -Depth 100 | Out-File $configJsonPath

Write-Host "Successfully updated the configuration for AOS gMSA execution."
```

## <a name="enableDixf"></a>TSG\_EnableDixfService.ps1

The following script is used to enable the Data Management Framework service for your environment.

>[!NOTE]
> This script can only be used starting with version 10.0.32.
> Additionally, at least version 2.18.0 of the infrastructure scripts is required.

```powershell
param (
    [Parameter(Mandatory)]
    [string]
    $AgentShare,
	[Parameter(Mandatory)]
    [string]
    $DMFShare,
	[Parameter(Mandatory)]
    [string]
    $GmsaAccount
)

$ErrorActionPreference = "Stop"

$basePath = Get-ChildItem $AgentShare\wp\*\StandaloneSetup-*\ |
    Select-Object -First 1 -Expand FullName

if(!(Test-Path $basePath))
{
    Write-Error "Basepath: $basePath , not found" -Exception InvalidOperation
}

$configJsonPath = "$basePath\config.json"

$configJson = Get-Content $configJsonPath | ConvertFrom-Json

$updatedComponents = @()
foreach ($component in $configJson.components)
{
    if($component.name -eq "AOS")
    {
        $component.parameters.services.dmfServiceFabricService.value = "True"
        $component.parameters.services.dmfFileShare.value = $DMFShare

        $gatewayComponent = $configJson.components | Where-Object { $_.name -eq "Gateway" }
        $dmfUrl = "https://$($component.parameters.infrastructure.hostName.value):$($gatewayComponent.parameters.internalServiceEndpointPort.value)/DixfApplication/DixfService/DMFService/DMFServiceHelper.svc"

        $component.parameters.services.dmfServiceUrl.value = $dmfUrl
    }
    elseif($component.name -eq "Dixf")
    {
        $component.isEnabled = "True"
        $component.parameters.infrastructure.principalUserAccountType.value = "ManagedServiceAccount"
        $component.parameters.infrastructure.principalUserAccountName.value = $GmsaAccount
    }

    $updatedComponents += $component
}

$configJson.components = $updatedComponents

$configJson | ConvertTo-Json -Depth 100 | Out-File $configJsonPath

Write-Host "Successfully updated the configuration and enabled DixfService."
```


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
