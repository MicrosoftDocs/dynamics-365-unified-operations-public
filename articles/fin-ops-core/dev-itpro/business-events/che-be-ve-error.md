---
# required metadata

title: Cloud Hosted Environments are unable to use Business Events or Virtual Entities and Receive a 400 error
description: This article provides information about troubleshooting business events.
author: ramasri
ms.date: 06/26/2023
ms.topic: article
ms.prod: 
ms.technology: 


audience: IT Pro
# ms.devlang: 
ms.reviewer: johnmichalak
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global for most topics. Set Country/Region name for localizations
# ms.search.industry: 
ms.author: ramasri
---

# Cloud Hosted Environments are unable to use Business Events or Virtual Entities and Receive a 400 error

While setting up business events or virtual entities on a cloud hosted environment, it is common to receive the following error message:

    Response Status code does not indicate success : 400 ({“error”:”invalid_client”,”error_description”;”Expected aud https://securityservice.operations365.dynamics.com  but found.”})

The reason is, the cloud hosted environments and on-premise (aka LBD) environments don't use Security Service. Please follow these manual steps to get this setup.

1. Create a new app registration in AAD. Save the Application client Id value.
2. Under that new app registration create a new Secret. Save the Secret value.
3. Go to Power Platform Admin Center > Environments > Settings > Users + Permissions > Application users > New App User. Create an app user for the Application Client ID from step 1 and give them appropriate role.
4. Add App ID from step 1 in Dynamics 365 Finance and Operations System Administration > Azure Active Directory Application.
5. Run the following PowerShell script in Admin PowerShell console to refresh the integration of Dataverse via PowerShell in remote desktop on the Cloud Hosted Environment or LBD environment.

```console

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
