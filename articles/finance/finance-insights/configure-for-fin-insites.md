---
# required metadata

title: Configuration for Finance Insights (preview)
description: This topic walks through the configuration steps that will enable your system to use the capability that's available in Finance Insights. 
author: ShivamPandey-msft
manager: AnnBe
ms.date: 07/20/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 14151
ms.assetid: 3d43ba40-780c-459a-a66f-9a01d556e674
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2020-07-20
ms.dyn365.ops.version: AX 10.0.13

---
# Configuration for Finance Insights (preview)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

Finance Insights combines functionality from Microsoft Dynamics 365 Finance, with the Microsoft Common Data Service (CDS), Microsoft Azure, and Microsoft AI Builder to provide powerful forecasting tools for your organizations. This topic walks through the configuration steps that will enable your system to use the capability that's available in Finance Insights. 

## Deploy Dynamics 365 Finance

Deploy the environments by completing the following steps.

1. Create or update a Dynamics 365 Finance environment in Lifecycle Services (LCS). The environment needs App Version 10.0.11/Platform Update 35 or later.
  
2. The environment must be a high availability (HA) environment in Sandbox (also known as a Tier-2 environment). For more information, see [Environment planning](../../fin-ops-core/fin-ops/imp-lifecycle/environment-planning.md).

3. If you are using Contoso demo data you'll need additional sample data to use Customer payment predictions, Cashflow forecasts, and Budget forecasts. See [Set up demo data for Payment predictions](set-up-demo-data.md) for information about setting up demo data specifically for Customer payment predictions.

  
## Configure the Common Data Service 

You can complete the steps as listed or use the attached PowerShell script to speed up the configuration. 


# [Configuration steps](#tab/configuration-steps)

1. Create a new Common data services environment in the same Active Directory Tenant. To do this, open the Environments page on the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
   
      [![Power Platform Admin Center](./media/power-pltfrm-admin-center.png)](./media/power-pltfrm-admin-center.png)
   
   - Click **+New environment**.
   - Select a Sandbox for the environment Type.
   - Set **Create Database** to **Yes**. 
   - Click **Next**.
   - Select the language and currency for your organization.
   - Accept the default values for the other options.
   - Click **Save**.
   - Navigate to the environment page, and then refresh the environments page. When the **State** shows **Ready**, complete the following steps. 
     - Record the CDS Organization ID.
     - Select the environment and click **Settings**.
     - Click **Resources > All Legacy Settings**.
     - Click **Settings** on the top bar and select **Customizations**.
     - Click **Developer Resources**.
     - Record the Instance Reference Information ID as the CDS Organization ID.
     - From the address bar in the browser, record the CDS Organization URL, such as &lt;https:/org42b2b3d3.crm.dynamics.com&gt;
2. If you plan to use Cash flow forecasts, or Budget forecasts, also update the annotation limit for your organization to at least 50 MB. To do so, complete the following steps. 
   - Go to the [Power Apps](https://make.powerapps.com) portal. Select the environment you created above and click **Advanced settings**.
   - Click **Settings > Email Configuration**.
   - Change the **Maximum file size** (in kilobytes) to 51,200.
   - Click **OK** to save the changes.

# [PowerShell configuration script](#tab/powershell-configuration-script)

    Write-Output 'The following modules need to be present for execution of this script:'
    Write-Output '  Microsoft.PowerApps.Administration.PowerShell'
    Write-Output '  Microsoft.PowerApps.PowerShell'
    Write-Output '  Microsoft.Xrm.Tooling.CrmConnector.PowerShell'

    try {
        $moduleConsent = Read-Host 'Is it ok to install or update these modules as needed? (yes/no)'
        if ($moduleConsent -ne 'yes' -and $moduleConsent -ne 'y') {
            Write-Warning 'User declined to install required modules.'
            return
        }

    $module = 'Microsoft.PowerApps.Administration.PowerShell'
    if (-not (Get-InstalledModule -Name $module -MinimumVersion '2.0.61' -ErrorAction SilentlyContinue)) {
        Install-Module -Name $module -MinimumVersion '2.0.61' -Force
        Write-Output ('Installed {0} module.' -f $module)
    }
    else {
        Write-Output ('{0} module found.' -f $module)
    }

    $module = 'Microsoft.PowerApps.PowerShell'
    if (-not (Get-InstalledModule -Name $module -MinimumVersion '1.0.9' -ErrorAction SilentlyContinue)) {
        Install-Module -Name $module -MinimumVersion '1.0.9' -AllowClobber -Force
        Write-Output ('Installed {0} module.' -f $module)
    }
    else {
        Write-Output ('{0} module found.' -f $module)
    }

    $module = 'Microsoft.Xrm.Tooling.CrmConnector.PowerShell'
    if (-not (Get-InstalledModule -Name $module -MinimumVersion '3.3.0.892' -ErrorAction SilentlyContinue)) {
        Install-Module -Name $module -MinimumVersion '3.3.0.892' -Force
        Write-Output ('Installed {0} module.' -f $module)
    }
    else {
        Write-Output ('{0} module found.' -f $module)
    }

    Write-Output '================================================================================='

    $useMfa = $false
    $useMfaPrompt = Read-Host "Does your organization require the use of multi-factor authentication? (yes/no)"
    if ($useMfaPrompt -eq 'yes' -or $useMfaPrompt -eq 'y') {
        $useMfa = $true
    }
    if(-not $useMfa) {
        $credential = Get-Credential -Message 'Power Apps Credential'
    }

    $orgFriendlyName = Read-Host "Enter the name of the CDS Organization to use or create: (blank for 'FinanceInsightsOrg')"
    if ($orgFriendlyName.Trim() -eq '') {
        $orgFriendlyName = 'FinanceInsightsOrg'
    }

    $isDefaultOrgPrompt = Read-Host ("Is '" + $orgFriendlyName + "' the default organization for your tenant? (yes/no)")
    if ($isDefaultOrgPrompt -eq 'yes' -or $isDefaultOrgPrompt -eq 'y') {
        $isDefaultOrg = $true
    }

    if ($credential) {
        Add-PowerAppsAccount -Username $credential.UserName -Password $credential.Password
    }
    else {
        Add-PowerAppsAccount
    }

    if ($isDefaultOrg) {
        $orgMatch = ('(default)')
        $environment = (Get-AdminPowerAppEnvironment | Where-Object { $_.IsDefault -eq $true })
    }
    else {
        $orgMatch = ('{0} (*)' -f $orgFriendlyName)
        $environment = (Get-AdminPowerAppEnvironment | Where-Object { ($_.IsDefault -eq $false -and ($_.DisplayName -eq $orgFriendlyName -or $_.DisplayName -like $orgMatch)) })
    }

    $getCrmOrgParams = @{ 'OnlineType' = 'Office365' }
    if ($credential) {
        $getCrmOrgParams.Credential = $credential
    }

    if ($null -eq $environment) {
        Write-Output '================================================================================='
        Write-Output 'PowerApps environment not found. A new one will be provisioned.'

        $invalid = 'invalid'

        $location = $invalid
        $cdsLocations = (Get-AdminPowerAppEnvironmentLocations | Select-Object LocationName).LocationName
        while (-not ($location -in $cdsLocations)) {
            $location = (Read-Host -Prompt "Enter the location in which to create the new PowerApps environment: ('help' to see values)")
            if ($location -eq 'help') {
                $cdsLocations
            }
        }

        $currency = $invalid
        $cdsCurrencies = (Get-AdminPowerAppCdsDatabaseCurrencies -Location $location | Select-Object CurrencyName).CurrencyName
        while ($currency -ne '' -and -not ($currency -in $cdsCurrencies)) {
            $currency = (Read-Host -Prompt "Enter the currency to use for the new PowerApps environment: ('help' to see values, blank for default)")
            if ($currency -eq 'help') {
                $cdsCurrencies
            }
        }

        $language = $invalid
        $cdsLanguages = (Get-AdminPowerAppCdsDatabaseLanguages -Location $location | Select-Object LanguageName, LanguageDisplayName)
        while ($language -ne '' -and -not ($language -in $cdsLanguages.LanguageName)) {
            $language = (Read-Host -Prompt "Enter the language name to use for the new PowerApps environment: ('help' to see values, blank for default)")
            if ($language -eq 'help') {
                $cdsLanguages | Format-Table -Property LanguageName, LanguageDisplayName
            }
        }

        Write-Output 'Provisioning PowerApps environment. This may take several minutes.'

        $sleep = 15

        $envParams = @{ 'DisplayName' = $orgFriendlyName; 'EnvironmentSku' = 'Sandbox'; 'ProvisionDatabase' = $true; 'Location' = $location; 'WaitUntilFinished' = $true }
        if ($language.Trim() -ne '') {
            $envParams.LanguageName = $language
        }
        if ($currency.Trim() -ne '') {
            $envParams.CurrencyName = $currency
        }
        $newEnvResult = New-AdminPowerAppEnvironment @envParams
        if (($null -eq $newEnvResult) -or ($newEnvResult.CommonDataServiceDatabaseProvisioningState -ne 'Succeeded')) {
            Write-Warning 'Failed to create to PowerApps environment'
            if ($null -ne $newEnvResult) {
                $newEnvResult
            }
        }
        else {
            $environment = $null
            $retryCount = 0
            while (($null -eq $environment) -and ($retryCount -lt 5)) {
                Start-Sleep -Seconds $sleep
                $environment = (Get-AdminPowerAppEnvironment | Where-Object { ($_.DisplayName -like $orgMatch) })
            }
            Write-Output ("Provisioned PowerApps environment with name: '" + $environment.DisplayName + "'")
        }

        Write-Output 'Waiting for CDS organization provisioning. This may take several minutes.'
        if (-not $credential) {
            $sleep = 120
            Write-Output 'You may be prompted for credentials multiple times while checking the status of the provisioning.'
        }

        while ($null -eq $crmOrg) {
            Start-Sleep -Seconds $sleep
            $crmOrg = (Get-CrmOrganizations @getCrmOrgParams) | Where-Object { $_.FriendlyName -eq $orgFriendlyName }
        }
    }
    else {
        $crmOrgs = Get-CrmOrganizations @getCrmOrgParams
        if ($UseDefaultOrganization -eq $true) {
            $crmOrg = $crmOrgs | Where-Object { $_.FriendlyName -match $orgMatch }
        }
        else {
            $crmOrg = $crmOrgs | Where-Object { $_.FriendlyName -eq $orgFriendlyName }
        }
    }

      Write-Output '================================================================================='
      Write-Output 'Values for PowerAI LCS Add-In:'
      Write-Output ("  CDS orgainization url:             " + $crmOrg.WebApplicationUrl)
      Write-Output ("  CDS orgainization ID:              " + $crmOrg.OrganizationId)
    }
    catch {
        Write-Error $_.Exception.Message
        Write-Warning $_.Exception.StackTrace
        $inner = $_.Exception.InnerException
        while ($null -ne $inner) {
          Write-Output 'Inner Exception:'
          Write-Error $_.Exception.Message
          Write-Warning $_.Exception.StackTrace
          $inner = $inner.InnerException
        }
      }
---

## Configuring Azure setup

### Record the CDS Directory ID and user's Azure Active Directory object ID

1. Record CDS Directory ID.
   - Go to the [Azure portal](https://portal.azure.com).
   - Log in using the user ID that was used to create the CDS environment.
   - Go to Azure Active Directory.
   - Copy the Tenant ID and record it as the CDS Directory ID.
2. Record the user's Azure Active Directory object ID.
   - Go to the [Azure portal](https://portal.azure.com).
   - Go to Users and search for the user by email.
   - Click the user's name.
   - Copy the Object ID as the CDS Initial User Object ID. 

### Using Azure Cloud Shell for setting up Finance Insights Data Lake Resources

# [Configuration steps for Azure setup](#tab/configuration-steps-for-azure-setup)

A PowerShell script is available that can be used to create the Azure resources. If you prefer manual setup, skip the following section and continue with procedure in the Manual setup section below. 

A PowerShell script has been provided to easily set up the Azure resources described in [Configure export to Azure Data Lake](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/data-entities/configure-export-data-lake). The steps for configuring Azure using the script are as follows. You will need rights to create an Azure resource group, Azure resources, and an AAD application. See [Check Azure AD permissions](https://docs.microsoft.com/azure/active-directory/develop/howto-create-service-principal-portal#permissions-required-for-registering-an-app) for details on required permissions.

1. Navigate to your target Azure subscription from the [Azure Portal](https://portal.azure.com). Just to the right of the **Search box**, click the **Cloud Shell** button.

2. Select **PowerShell** in the new window that opens.

3. Create storage if prompted. Upload the PowerShell script to the session. 

4. Run the script. 

6. Click the device login link and enter the login information.

7. Follow prompts to execute the script.

8. Use the information from the script output to install the **Export to Data Lake** add-in in Lifecycle Services (LCS).

9. Use information from the script output to enable the entity store in Dynamics 365 for Finance (**System Administration > System parameters > Data connections**).

# [PowerShell configuration script for Azure CLI](#tab/powershell-configuration-script-for-azure-cli azurecli-interactive)
```azurecli-interactive
```
    function New-FinanceDataLakeAzureResources {
       $defaultSecretExpiryInYear = 1

    $MicrosoftDynamicsERPMicroservicesAppId = '0cdb527f-a8d1-4bf8-9436-b352c68682b2'
    $MicrosoftDynamicsERPMicroservicesCDSAppId = '703e2651-d3fc-48f5-942c-74274233dba8'
    $AIBuilderAuthorizationServiceAppId = 'ad40333e-9910-4b61-b281-e3aeeb8c3ef3'
    $KeyVaultServicePrincipalAppId = 'cfa8b339-82a2-471a-a3c9-0fc0be7a4093'
    $GraphServicePrincipalAppId = '00000003-0000-0000-c000-000000000000'

    $subscriptionContext = Connect-AzAccount
    if ($null -eq $subscriptionContext) {
        throw 'Unable to connect to Azure account.'
    }

    Import-Module AzureAD.Standard.Preview
    $connectAzureADParameters = @{ 'Identity' = $true; 'TenantId' = $env:ACC_TID }
    $azContext = AzureAD.Standard.Preview\Connect-AzureAD @connectAzureADParameters
    $userContext = ConvertFrom-Json ((az ad signed-in-user show) -join '')
    $user = Get-AzureADUser -Filter ("UserPrincipalName eq '" + $userContext.UserPrincipalName + "'")

    $subscriptionId = (Read-Host -Prompt "Enter the Azure Subscription ID: (blank for default)")
    if ($subscriptionId.Trim() -ne '') {
        $azSubscription = Select-AzSubscription -SubscriptionId $subscriptionId
    }

    $resourceGroupName = (Read-Host -Prompt "Enter the Azure Resource Group name: (blank for 'FinanceDataLake')")
    if ($null -eq $resourceGroupName -or $resourceGroupName.Trim() -eq '') {
        $resourceGroupName = 'FinanceDataLake'
    }
    $resourceGroup = Get-AzResourceGroup -Name $resourceGroupName -ErrorAction SilentlyContinue

    if (-not ($resourceGroup)) {
        $resourceLocation = ''
        $azResourceLocations = (Get-AzLocation | Select-Object Location).Location
        while ($resourceLocation.Trim() -eq '' -or (-not ($resourceLocation -in $azResourceLocations))) {
            $resourceLocation = (Read-Host -Prompt "Enter the location in which to create the Azure Resource Group: ('help' to see values)")
            if ($resourceLocation -eq 'help') {
                $azResourceLocations
                $resourceLocation = ''
            }
        }
        $resourceGroup = New-AzResourceGroup -Name $resourceGroupName -Location $resourceLocation
    }
    else {
        $resourceLocation = $resourceGroup.Location
    }

    $clientAppName = (Read-Host -Prompt "Enter the name of the application registration: (blank for 'Finance Data Lake Application')")
    if ($clientAppName.Trim() -eq '') {
        $clientAppName = 'Finance Data Lake Application'
    }

    Write-Output '================================================================================='

    $service = Get-AzureADServicePrincipal -Filter ("AppId eq '" + $MicrosoftDynamicsERPMicroservicesAppId + "'")
    if (-not $service) {
        New-AzureADServicePrincipal -AppId $MicrosoftDynamicsERPMicroservicesAppId | Format-Table -AutoSize
        $service = Get-AzureADServicePrincipal -Filter ("AppId eq '" + $MicrosoftDynamicsERPMicroservicesAppId + "'")
        Write-Output ("Added AAD Enterprise Application 'Microsoft Dynamics ERP Microservices' with Application ID {0}" -f $MicrosoftDynamicsERPMicroservicesAppId)
    }
    else {
        Write-Output ("Found AAD Enterprise Application 'Microsoft Dynamics ERP Microservices' with Application ID {0}" -f $MicrosoftDynamicsERPMicroservicesAppId)
    }
    $MicrosoftDynamicsERPMicroservicesAppObjectId = $service.ObjectId

    $service = Get-AzureADServicePrincipal -Filter ("AppId eq '" + $MicrosoftDynamicsERPMicroservicesCDSAppId + "'")
    if (-not $service) {
        New-AzureADServicePrincipal -AppId $MicrosoftDynamicsERPMicroservicesCDSAppId | Format-Table -AutoSize
        Write-Output ("Added AAD Enterprise Application 'Microsoft Dynamics ERP Microservices CDS' with Application ID {0}" -f $MicrosoftDynamicsERPMicroservicesCDSAppId)
    }
    else {
        Write-Output ("Found AAD Enterprise Application 'Microsoft Dynamics ERP Microservices CDS' with Application ID {0}" -f $MicrosoftDynamicsERPMicroservicesCDSAppId)
    }

    $service = Get-AzureADServicePrincipal -Filter ("AppId eq '" + $AIBuilderAuthorizationServiceAppId + "'")
    if (-not $service) {
        New-AzureADServicePrincipal -AppId $AIBuilderAuthorizationServiceAppId | Format-Table -AutoSize
        $service = Get-AzureADServicePrincipal -Filter ("AppId eq '" + $AIBuilderAuthorizationServiceAppId + "'")
        Write-Output ("Added AAD Enterprise Application 'AI Builder Authorization Service' with Application ID {0}" -f $AIBuilderAuthorizationServiceAppId)
    }
    else {
        Write-Output ("Found AAD Enterprise Application 'AI Builder Authorization Service' with Application ID {0}" -f $AIBuilderAuthorizationServiceAppId)
    }
    $aibuilderAuthorizationServiceObjectId = $service.ObjectId

    Write-Output '================================================================================='

    $clientAppSPN = Get-AzureADServicePrincipal -Filter ("DisplayName eq '" + $clientAppName + "'")
    if (-not ($clientAppSPN)) {
        $keyVaultPrincipal = Get-AzureADServicePrincipal -Filter ("AppId eq '" + $KeyVaultServicePrincipalAppId + "'")
        if (-not $keyVaultPrincipal)
        {
            New-AzureADServicePrincipal -AppId $KeyVaultServicePrincipalAppId | Format-Table -AutoSize
            Write-Output "Added Key Vault principal to AAD"
            $keyVaultPrincipal = Get-AzureADServicePrincipal -Filter ("AppId eq '" + $KeyVaultServicePrincipalAppId + "'")
        }
        $keyVaultAccess = New-Object -TypeName "Microsoft.Open.AzureAD.Model.RequiredResourceAccess"
        $keyVaultAccess.ResourceAppId = $keyVaultPrincipal.AppId
        $keyVaultAccess.ResourceAccess = (New-Object -TypeName "microsoft.open.azuread.model.resourceAccess" -ArgumentList $keyVaultPrincipal.Oauth2Permissions.Id, "Scope")

        $graphPrincipal = Get-AzureADServicePrincipal -Filter ("AppId eq '" + $GraphServicePrincipalAppId + "'")
        if (-not $graphPrincipal)
        {
            New-AzureADServicePrincipal -AppId $GraphServicePrincipalAppId | Format-Table -AutoSize
            Write-Output "Added Graph principal to AAD"
            $graphPrincipal = Get-AzureADServicePrincipal -Filter ("AppId eq '" + $GraphServicePrincipalAppId + "'")
        }
        $userRead = $graphPrincipal.Oauth2Permissions | Where-Object { $_.Type -eq "User" -and $_.Value -eq "User.Read" }
        $graphAccess = New-Object -TypeName "Microsoft.Open.AzureAD.Model.RequiredResourceAccess"
        $graphAccess.ResourceAppId = $graphPrincipal.AppId
        $graphAccess.ResourceAccess = (New-Object -TypeName "microsoft.open.azuread.model.resourceAccess" -ArgumentList $userRead.Id, "Scope")

        $clientApp = New-AzureADApplication -DisplayName $clientAppName -RequiredResourceAccess @($keyVaultAccess, $graphAccess)
        $clientAppSPN = New-AzureADServicePrincipal -AppId $clientApp.AppId -Tags @($clientAppName)
        $clientAppId = $clientApp.AppId
        Write-Output ('Created App Registration "' + $clientAppName + '" with Application Id: ' + $clientAppId)
    }
    else {
        $clientApp = Get-AzureADApplication -Filter ("DisplayName eq '" + $clientAppName + "'")
        $clientAppId = $clientApp.AppId
        Write-Output ('Found App Registration "' + $clientAppName + '" with Application Id: ' + $clientAppId)
    }
            
    $clientAppSecretCredential = New-AzureADApplicationPasswordCredential -ObjectId $clientApp.ObjectId -CustomKeyIdentifier "ClientAppAccessKey" -EndDate (get-date).AddYears($defaultSecretExpiryInYear)
    $ClientAppSecret = $clientAppSecretCredential.Value
    $clientAppSpId = $clientAppSPN.ObjectId

    Write-Output ('Generated application secret: ' + $ClientAppSecret)
    Write-Output '================================================================================='

    $templateObject = ConvertFrom-Json $azureTemplate -AsHashtable
    $templateObject.{$schema} = "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#"
    Write-Output 'Provisioning Azure resources. This may take a few minutes.'
    $deployment = New-AzResourceGroupDeployment -ResourceGroupName $resourceGroupName -TemplateObject $templateObject -aibuilderAppObjectId $aibuilderAuthorizationServiceObjectId -clientAppId $clientAppId -clientAppSecret $ClientAppSecret -clientAppSpObjectId  $clientAppSpId -microserviceSpObjectId $MicrosoftDynamicsERPMicroservicesAppObjectId -userSpObjectId $user.ObjectId

    if ($deployment.ProvisioningState -eq 'Succeeded') {
        Write-Output "Successfully deployed the following resources to Azure:"
        Write-Output ("  Key Vault:                         " + $deployment.Outputs.keyVaultName.Value)
        Write-Output ("  Storage Account:                   " + $deployment.Outputs.storageAccountName.Value)
    }
    else {
        Write-Output ("Provisioning Azure resources failed with the following state: " + $deployment.ProvisioningState)
        Write-Output ("Some of the resources may have been created in resource group: " + $resourceGroupName)
    }

    Write-Output '================================================================================='

    $keyVault = Get-AzKeyVault -VaultName $deployment.Outputs.keyVaultName.Value
    Write-Output "Values for LCS Data Lake Add-In:"
    Write-Output ("  Tenant ID:                         " + $subscriptionContext.Context.Subscription.TenantId)
    Write-Output ("  DNS Name:                          " + $keyVault.VaultUri)
    Write-Output "  Storage account secret name:       storage-account-name"
    Write-Output "  Application ID secret name:        app-id"
    Write-Output "  Application Secret secret name:    app-secret"
    Write-Warning "Copy this information for the LCS Add-in as it is not saved. Azure Cloud Shell will eventually time out and close."

    Write-Output '================================================================================='
    Write-Output "Values for System parameters > Data connections:"
    Write-Output ("  Application ID:                    " + $clientAppId)
    Write-Output ("  Application Secret:                " + $ClientAppSecret)
    Write-Output ("  DNS name:                          " + $keyVault.VaultUri)
    Write-Output "  Secret name:                       storage-account-connection-string"
    Write-Warning "Copy this information for the System parameters as it is not saved. Azure Cloud Shell will eventually time out and close."
    }

    $azureTemplate = @"
    {
        "contentVersion": "1.0.0.0",
        "parameters": {
          "aibuilderAppObjectId": {
            "type": "string",
            "metadata": {
              "description": "Specifies the object ID of the AI Builder application."
            }
          },
          "clientAppId": {
            "type": "string",
            "metadata": {
              "description": "Specifies the application ID of client application."
            }
          },
          "clientAppSecret": {
            "type": "String",
            "metadata": {
              "description": "Specifies the Azure App ID client secret to in azure key vault."
            }
          },
          "clientAppSpObjectId": {
            "type": "string",
            "metadata": {
              "description": "Specifies the object ID of a client application service principal."
            }
          },
          "userSpObjectId": {
            "type": "string",
            "metadata": {
              "description": "Specifies the object ID of tenant admin service principal."
            }
          },
          "microserviceSpObjectId": {
            "type": "string",
            "metadata": {
              "description": "Specifies the object ID of Microsoft Dynamics ERP Microservices service principal."
            }
          },
          "storageAccountType": {
            "type": "string",
            "defaultValue": "Standard_LRS",
            "allowedValues": [
              "Standard_LRS",
              "Standard_GRS",
              "Standard_ZRS",
              "Premium_LRS"
            ],
            "metadata": {
              "description": "Storage Account type"
            }
          }
        },
        "variables": {
          "storageAccountApiVersion": "2019-06-01",
          "keyVaultApiVersion": "2018-02-14",
          "secretsPermissions": [
            "list",
            "get"
          ],
            "location": "[resourceGroup().location]",
            "storageAccountName": "[concat('store', uniquestring(resourceGroup().id))]",
            "keyVaultName": "[concat('keyvault', uniquestring(resourceGroup().id))]",
            "owner": "[concat('/subscriptions/', subscription().subscriptionId, '/providers/Microsoft.Authorization/roleDefinitions/', '8e3af657-a8ff-443c-a75c-2fe8c4bcb635')]",
            "contributor": "[concat('/subscriptions/', subscription().subscriptionId, '/providers/Microsoft.Authorization/roleDefinitions/', 'b24988ac-6180-42a0-ab88-20f7382dd24c')]",
            "storageAccountContributor": "[concat('/subscriptions/', subscription().subscriptionId, '/providers/Microsoft.Authorization/roleDefinitions/', '17d1049b-9a84-46fb-8f53-869881c3d3ab')]",
            "storageBlobDataOwner": "[concat('/subscriptions/', subscription().subscriptionId, '/providers/Microsoft.Authorization/roleDefinitions/', 'b7e6dc6d-f1e8-4753-8033-0f276bb0955b')]",
            "storageBlobDataReader": "[concat('/subscriptions/', subscription().subscriptionId, '/providers/Microsoft.Authorization/roleDefinitions/', '2a2b9908-6ea1-4ae2-8e65-a410df84e7d1')]"
          },
          "resources": [
            {
              "type": "Microsoft.Storage/storageAccounts",
            "apiVersion": "[variables('storageAccountApiVersion')]",
            "name": "[variables('storageAccountName')]",
            "location": "[variables('location')]",
            "sku": {
              "name": "[parameters('storageAccountType')]"
            },
            "kind": "StorageV2",
            "properties": {
              "accessTier": "Hot",
              "supportsHttpsTrafficOnly": true,
              "isHnsEnabled": true
            },
            "resources": [
              {
                "type": "Microsoft.Storage/storageAccounts/providers/roleAssignments",
                "apiVersion": "2018-09-01-preview",
                "name": "[concat(variables('storageAccountName'), '/Microsoft.Authorization/', guid(uniqueString(variables('storageAccountName'),'1')))]",
                "dependsOn": [
                  "[variables('storageAccountName')]"
                ],
                "properties": {
                  "roleDefinitionId": "[variables('owner')]",
                  "principalId": "[parameters('clientAppSpObjectId')]"
                }
              },
              {
                "type": "Microsoft.Storage/storageAccounts/providers/roleAssignments",
                "apiVersion": "2018-09-01-preview",
                "name": "[concat(variables('storageAccountName'), '/Microsoft.Authorization/', guid(uniqueString(variables('storageAccountName'),'2')))]",
                "dependsOn": [
                  "[variables('storageAccountName')]"
                ],
                "properties": {
                  "roleDefinitionId": "[variables('contributor')]",
                  "principalId": "[parameters('clientAppSpObjectId')]"
                }
              },
              {
                "type": "Microsoft.Storage/storageAccounts/providers/roleAssignments",
                "apiVersion": "2018-09-01-preview",
                "name": "[concat(variables('storageAccountName'), '/Microsoft.Authorization/', guid(uniqueString(variables('storageAccountName'),'3')))]",
                "dependsOn": [
                  "[variables('storageAccountName')]"
                ],
                "properties": {
                  "roleDefinitionId": "[variables('storageAccountContributor')]",
                  "principalId": "[parameters('clientAppSpObjectId')]"
                }
              },
              {
                "type": "Microsoft.Storage/storageAccounts/providers/roleAssignments",
                "apiVersion": "2018-09-01-preview",
                "name": "[concat(variables('storageAccountName'), '/Microsoft.Authorization/', guid(uniqueString(variables('storageAccountName'),'4')))]",
                "dependsOn": [
                  "[variables('storageAccountName')]"
                ],
                "properties": {
                  "roleDefinitionId": "[variables('storageBlobDataOwner')]",
                  "principalId": "[parameters('clientAppSpObjectId')]"
                }
              },
              {
                "type": "Microsoft.Storage/storageAccounts/providers/roleAssignments",
                "apiVersion": "2018-09-01-preview",
                "name": "[concat(variables('storageAccountName'), '/Microsoft.Authorization/', guid(uniqueString(variables('storageAccountName'),'5')))]",
                "dependsOn": [
                  "[variables('storageAccountName')]"
                ],
                "properties": {
                  "roleDefinitionId": "[variables('storageBlobDataReader')]",
                  "principalId": "[parameters('aibuilderAppObjectId')]"
                }
              }
            ]
          },
          {
            "type": "Microsoft.KeyVault/vaults",
            "apiVersion": "[variables('keyVaultApiVersion')]",
            "name": "[variables('keyVaultName')]",
            "location": "[variables('location')]",
            "dependsOn": [
              "[resourceId('Microsoft.Storage/storageAccounts', variables('storageAccountName'))]"
            ],
            "tags": {
            },
            "properties": {
              "enabledForDeployment": false,
              "enabledForTemplateDeployment": false,
              "enabledForDiskEncryption": false,
              "enableRbacAuthorization": false,
              "accessPolicies": [
                {
                  "objectId": "[parameters('clientAppSpObjectId')]",
                  "tenantId": "[subscription().tenantId]",
                  "permissions": {
                    "secrets": "[variables('secretsPermissions')]"
                  }
                },
                {
                  "objectId": "[parameters('microserviceSpObjectId')]",
                  "tenantId": "[subscription().tenantId]",
                  "permissions": {
                    "secrets": "[variables('secretsPermissions')]"
                  }
                },
                {
                  "objectId": "[parameters('userSpObjectId')]",
                  "tenantId": "[subscription().tenantId]",
                  "permissions": {
                    "secrets": "[variables('secretsPermissions')]"
                  }
                }
              ],
              "tenantId": "[subscription().tenantId]",
              "sku": {
                "name": "Standard",
                "family": "A"
              },
              "enableSoftDelete": false,
              "networkAcls": {
                "defaultAction": "Allow",
                "bypass": "AzureServices"
              }
            }
          },
          {
            "type": "Microsoft.KeyVault/vaults/secrets",
            "name": "[concat(variables('keyVaultName'), '/', 'app-id')]",
            "apiVersion": "[variables('keyVaultApiVersion')]",
            "location": "[variables('location')]",
            "dependsOn": [
              "[resourceId('Microsoft.KeyVault/vaults', variables('keyVaultName'))]"
            ],
            "properties": {
              "value": "[parameters('clientAppId')]"
            }
          },
          {
            "type": "Microsoft.KeyVault/vaults/secrets",
            "name": "[concat(variables('keyVaultName'), '/', 'app-secret')]",
            "apiVersion": "[variables('keyVaultApiVersion')]",
            "location": "[variables('location')]",
            "dependsOn": [
              "[resourceId('Microsoft.KeyVault/vaults', variables('keyVaultName'))]"
            ],
            "properties": {
              "value": "[parameters('clientAppSecret')]"
            }
          },
          {
            "type": "Microsoft.KeyVault/vaults/secrets",
            "name": "[concat(variables('keyVaultName'), '/', 'storage-account-name')]",
            "apiVersion": "[variables('keyVaultApiVersion')]",
            "location": "[variables('location')]",
            "dependsOn": [
              "[resourceId('Microsoft.KeyVault/vaults', variables('keyVaultName'))]"
            ],
            "properties": {
              "value": "[variables('storageAccountName')]"
            }
          },
          {
            "type": "Microsoft.KeyVault/vaults/secrets",
            "name": "[concat(variables('keyVaultName'), '/', 'storage-account-connection-string')]",
            "apiVersion": "[variables('keyVaultApiVersion')]",
            "location": "[variables('location')]",
            "dependsOn": [
              "[resourceId('Microsoft.KeyVault/vaults', variables('keyVaultName'))]"
            ],
            "properties": {
              "value": "[concat('DefaultEndpointsProtocol=https;AccountName=', variables('storageAccountName'), ';AccountKey=', listKeys(resourceId('Microsoft.Storage/storageAccounts', variables('storageAccountName')), variables('storageAccountApiVersion')).keys[0].value, ';EndpointSuffix=core.windows.net')]"
            }
          }
        ],
        "outputs": {
          "storageAccountName": {
            "type": "string",
            "value": "[variables('storageAccountName')]"
          },
          "keyVaultName": {
            "type": "string",
            "value": "[variables('keyVaultName')]"
          }
        }
      }
    "@

    try {
      New-FinanceDataLakeAzureResources
    }
    catch {
      Write-Error $_.Exception.Message
      Write-Warning $_.Exception.StackTrace
      $inner = $_.Exception.InnerException
      while ($null -ne $inner) {
        Write-Output 'Inner Exception:'
        Write-Error $_.Exception.Message
        Write-Warning $_.Exception.StackTrace
        $inner = $inner.InnerException
      }
    }
---

  ### Manual setup

  #### Add Applications to the Azure Active Directory Tenant
  1. Go to Azure Active Directory
  2. Go to **Manage > Enterprise Applications**.
  3. Search for the following applications, using App ID (see steps below if you cannot find those applications).

  | Application                                 | App ID                                  |
  |---------------------------------------------|-----------------------------------------|
  | Microsoft Dynamics ERP Microservices        | 0cdb527f-a8d1-4bf8-9436-b352c68682b2    |
  | Microsoft Dynamics ERP Microservices CDS    | 703e2651-d3fc-48f5-942c-74274233dba8    |
  | AI Builder Authorization Service            | ad40333e-9910-4b61-b281-e3aeeb8c3ef3    |

If you are unable to find any of the preceding applications, try the following in Enterprise Applications:
1. On your local machine: Click on the **Start** menu and search for "powershell".
2. Right-click **Windows PowerShell** and choose **Run as administrator**.
3. Run the following command to install “AzureAD” module.
   - Install-Module -Name AzureAD
   - If NuGet provider is required to continue, select “Y” to install it.
   - If the **Untrusted repository** message appears, select “Y” to continue.
   - For each application that must be added, run the following commands to add the application to the Azure Active Directory. 
     - Login as the Azure Active Directory administrator when prompted
     - Connect-AzureAD 
     - New-AzureADServicePrincipal –AppId <AppId>

#### Create an Azure resources.
   > [!NOTE]
   > Be sure you are creating the following resources in the same Azure Active Directory as the CDS environment. It's not possible to use resources from another Azure Active Directory.  

1. Create a new Storage Account using the following instructions:
   - In the Azure portal, create a new storage account.
   - In the **Create storage account** dialog box, provide values for the following parameter fields:
     - **Location**: Select the data center where your environment is located.
     - **Performance**: We recommend that you select **Standard**.
     - **Account kind**: You must select **StorageV2**.
     - In the **Advanced options** dialog box, you will see the **Data Lake storage Gen2** option. Select **Enable** under the Hierarchical namespaces feature. If you disable this option, you can't consume data written by Finance and Operations apps with services, such as Power BI data flows.
     - Select **Review and create**. When the deployment is completed, the new resource will be shown in the Azure portal.
   - Go to the storage account that you created.
     - Go to **Access keys** from the menu on the left.
     - Copy and save the connection string for either Key1 or key2.
     - Copy and save the storage account name.

2. Create a new **Key Vault** using the following instructions:
   - In the Azure portal, create a new Key Vault.
   - In the **Create key vault** dialog box, in the **Location** field, select the data center where your environment is located.
   - After Key Vault is created, select it in the list, and then select **Secrets**.
   - Select **Generate/Import**.
   - In the **Create a secret** dialog box, in the **Upload options** field, select **Manual**.
   - Enter a name for the secret. Make a note of the name, because you'll have to provide it later.
   - In the value field, enter the connection string that you obtained from the storage account in the previous procedure.
   - Select **Enabled**, and then select **Create**. The secret is created and added to Key Vault.
   - Go to the Key Vault Overview and note the DNS Name.
   
 3. Create and register an Azure Active directory application using the following instructions: 
    - In the Azure portal, select Azure Active Directory, and then select App registrations.
    - Select New application registration, and enter the following information:
      - **Name**: Enter the name of the app.
      - **Application type**: Select Web API.
      - **Redirect URI setup**: Provide the URL for your Dynamics instance, such as, &lt;https://yourdynamicsinstance.dynamics.com/auth&gt;. 
      - Go to the app just created, and save its **Application (client) ID**. You will have to provide this key when setting up the key vault later.
    - Go to **API permissions**.
      - Select **+ Add a permission**.
      - Select **Azure Key vault**.
      - After you select delegated permissions, select **user_impersonation**.
      - Click **Add permissions**.  
    - Select **Certificates & secrets** on the menu for the app. Create Key Vault Secrets by completing the following steps.
      - Select **New client secret**.
      - In the Key Description field, enter a name.
      - Select a duration, and then select **Add**.
      - A secret is generated in the **Value** field.
      - Copy and save the secrete value.

4. Create Key Vault Secrets using the following instructions:
    - Go to the Key Vault created previously and select **Secrets**.
    - For each secrete name in the table below repeat the following steps:
      - Select **Generate/Import**.
      - In the **Create a secret** dialog box, select **Manual** in the **Upload options** field.
      - Create the secret name and value from the following table.
      - Select **Enabled**, and then select **Create**. The secret is created and added to Key Vault.

    |     Secret   Name                        |     Secret   value                                                                 |
    |------------------------------------------|------------------------------------------------------------------------------------|
    |     app-id                               |     The ID   of the application just created                                       |
    |     app-secret                           |     The   client secret saved previously                                           |
    |     storage-account-name                 |     The   name of the storage account created previously, such as, storageaccount1 |
    |     storage-account-connection-string    |     The   connection string copied from Access Keys of the storage account         |

3. Authorize the application to access the key vault using the following instructions:
    - In the Azure portal, open the **Key Vault** that you created previously. 
    - Select the access policies. 
    - To access the list of applications in the table below complete the following steps.
      - Click **+ Add Access Policy** to create a new access policy.
      - In the **Secret permissions** field, select the permissions from the following table.
      - In the **Select principal** field, search for the application display name from the following table. 
      - Click **Select**.
      - Click **Add**.
      - Click **Save**.
  
    |     Application                                                      |     Permissions    |
    |----------------------------------------------------------------------|--------------------|
    |     Display name of the new application you created                  |     Get, List      |
    |     Microsoft Dynamics ERP Microservices                             |     Get, List      |

4. Assign roles to access the storage account using the following instructions:
    - In the Azure portal, open the storage account that you created previously. Select **Access Control (IAM)** and select **Role Assignments**. 
    - Click **+ Add, Add Role Assignment**.
      - Select the role from the following table.
      - Keep **Assign access to** as **Azure AD user, group, or service principal**.
      - In the **Select** field, enter the application from the following table.
      - Click **Save**.
   
    |     Application                                         |     Role                             |
    |---------------------------------------------------------|--------------------------------------|
    |     Display name of the new application you created     |     Owner                            |
    |     Display name of the new application you created     |     Contributor                      |
    |     Display name of the new application you created     |     Storage Account   Contributor    |
    |     Display name of the new application you created     |     Storage Blob Data   Owner        |
    |     AI Builder Authorization Service                    |     Storage Blob Data   Reader       | 
 
  
  ## Configure entity store
  
  Set up the entity store in your Dynamics 365 Finance environment. 
  
 1. Go to **System administration > Setup > System parameters > Data connections**.
 
 2. Set **Enable Data Lake integration** to **Yes**. 
 
 3. Set the following Azure key vault values. 
 
    - Application (client) ID: This is the Application client ID that you create above. 
    - Application Secrete: The secret you saved for the application created above.
    - DNS name: You can find the DNS name on the application details page for the application you created above.
    - Secrete name: storage-account-connection-string.
   
## Configure the Data Lake

Add Azure Data Lake add-in to the environment using LCS. 

1. Log in to the LCS and click **Full Details** under the environment name, which is on the right side of the page. 

2. Click the **Environment add-ins** section and select **+ Install a new add-in**.

3. Select **Export to Data Lake** add-in. 

4. Enter the following values. 

  |     Value                                                                                |     Description                                    |
  |------------------------------------------------------------------------------------------|----------------------------------------------------|
  |     Tenant   ID of the Azure Subscription where the Key Vault is located.                |     This   is the tenant Id where the storage account, apps and Key Vaults are located.           Go   to: **Azure portal > Azure Active Directory > Tenant ID**          |
  |     Provide   the DNS name of your Key Vault                                             |     The   DNS name of the Key Vault (same as what is used in Entity store). For example, &lt;https://customkeyvault.vault.azure.net/&gt;                                               |
  |     Provide   the secret that contains the name of the storage account                   |     storage-account-name                                      |
  |     Secret   Name for App ID to be used for accessing Data Lake                          |     app-id                                                    |
  |     Secret   name to be used with App ID                                                 |     app-secret                                                |

5. Agree to the terms and click **Install**.

6. The add-in will be installed within a few minutes. 

## Configure AI Builder

1. Login to LCS and go to the **Environment details** page. 
2. Scroll to the **Environment add-ins** section. You should see the add-ins that are already installed in this environment. 
3. You should see the **Export to Data Lake** add-in installed. If you do not see **Export to Data Lake** add-in installed, configure **Export to Data Lake** as a first step.
4. Select the **Get insights** add-in. 

   - The **Get insights** add-in details page will open. Enter the values listed in the following table. 

   |     Value                                                         |     Description                                                 |
   |-------------------------------------------------------------------|-----------------------------------------------------------------|
   |     CDS   Organization URL                                        |     The   CDS Organization URL of the CDS instance. Make.powerapps.com  Click the **Settings** icon (right upper corner)  Advance  Setting  Copy the URL (ending with dynamics.com)    |
   |     CDS   Org ID                                                  |     The Environment ID of the CDS instance. Make.powerapps.com **Settings   > Customizations > Developer resources > Instance Reference Information > ID**                                    |
   |     CDS   Tenant ID (Directory ID  from AAD)                      |     The Tenant ID of the CDS instance.  Go to: **Azure portal > Azure Active Directory > Tenant ID**       |
   |     Provide   user object ID who has system administrator role    |     The AAD User Object ID of the user in CDS. This user must be a System Administrator of the CDS instance  **Azure Active directory > Users > select your user > Identity > Object ID**      |
   |     Is this the default CDS environment for the tenant?         |     If the CDS instance was the first production instance created, Select the check box. If the CDS instance was created manually, clear the check box.                                                  |

#### Privacy notice
Previews (1) might use less privacy and fewer security measures than the Dynamics 365 Finance and Operations service, (2) aren't included in the service level agreement (SLA) for this service, (3) should not be used to process personal data or other data that is subject to legal or regulatory compliance requirements, and (4) have limited support.
