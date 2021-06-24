---
# required metadata

title: Configuration for Finance insights - vesrions upto 10.0.19
description: This topic explains the configuration steps that will enable your system to use the capabilities that are available in Finance insights for versions upto 10.0.19.
author: ShivamPandey-msft
ms.date: 06/03/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
ms.custom: 14151
ms.assetid: 3d43ba40-780c-459a-a66f-9a01d556e674
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2020-07-20
ms.dyn365.ops.version: AX 10.0.13

---
# Configuration for Finance insights for private preview (preview) - upto version 10.0.19

[!include [banner](../includes/banner.md)]

[!include [preview banner](../includes/preview-banner.md)]

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

> [!NOTE]
> The following procedures for setting up Finance insights are valid for Microsoft Dynamics 365 Finance versions up to 10.0.19. To set up Finance insights on version 10.0.20 and later, see [Configuration for Finance Insights (preview) - versions 10.0.20 and beyond](configure-for-fin-insites-PubPrvw.md).

Finance insights combines functionality from Microsoft Dynamics 365 Finance with Microsoft Dataverse, Azure, and AI Builder to provide powerful forecasting tools for your organization. This topic explains the configuration steps that will enable your system to use the capabilities that are available in Finance insights.

## Deploy Dynamics 365 Finance

Deploy the environments by following these steps.

1. In Microsoft Dynamics Lifecycle Services (LCS), create or update a Dynamics 365 Finance environment. The environment requires app version 10.0.11/Platform update 35 or later.
2. The environment must be a high-availability (HA) environment in Sandbox. (This type of environment is also known as a Tier-2 environment.) For more information, see [Environment planning](../../fin-ops-core/fin-ops/imp-lifecycle/environment-planning.md).
3. If you are configuring Finance insights in a Sandbox environment, you might need to copy production data to that environment for predictions to work. The prediction model uses multiple years of data to build predictions. The Contoso demo data doesn’t contain enough historical data to train the prediction model adequately. 

## Configure Dataverse

Use the following steps to configure Dataverse for Finance insights.

1. Open the environment page in LCS and verify that the **Power Platform Integration** section is already setup.
    1. If it is already set up, the Dataverse environment name linked to the Dynamics 365 Finance Environment should be listed. Copy the Dataverse environment name.
    2. If it is not set up, follow these steps:
        1. Select the **Setup** button in the Power Platform Integration section. It may take up to an hour for the environment to be set up.
        2. If the Dataverse environment is successfully set up, the Dataverse environment name linked to the Dynamics 365 Finance Environment should be listed. Copy the Dataverse environment name.
> [!NOTE]
> After completing the environment set up, **DO NOT** select the **Link to CDS for Apps** button. This is not needed for Finance Insights and will disable the ability to complete the required Environment Add-ins in LCS.

2. Open the [Power Platform admin center](https://admin.powerplatform.microsoft.com/), and follow these steps to create a new Dataverse environment in the same Active Directory tenant:

    1. Open the **Environments** page.

        [![Environments page](./media/power-pltfrm-admin-center.png)](./media/power-pltfrm-admin-center.png)

    2. Select the Dataverse environment created above and then select **Settings**.
    3. Select **Resources \> All Legacy Settings**.
    4. On the top navigation bar, select **Settings**, and then select **Customizations**.
    5. Select **Developer Resources**.
    6. Copy the **Dataverse organization ID** value.
    7. In the browser's address bar, make a note of the URL for the Dataverse organization. For example, the URL might be `https://org42b2b3d3.crm.dynamics.com`.

3. If you plan to use the Cash flow forecasts or Budget forecasts feature, follow these steps to update the annotation limit for your organization to at least 50 megabytes (MB):

    1. Open the [Power Apps portal](https://make.powerapps.com).
    2. Select the environment that you just created, and then select **Advanced settings**.
    3. Select **Settings \> Email Configuration**.
    4. Change the value of the **Maximum file size** field to **51,200**. (The value is expressed in kilobytes \[KB\].)
    5. Select **OK** to save your changes.

## Configure the Azure setup

### Enter the Dataverse directory ID and the user's Azure AD object ID

1. Enter the Dataverse directory ID:

    1. Open the [Azure portal](https://portal.azure.com).
    2. Sign in by using the user ID that was used to create the Dataverse environment.
    3. Go to **Azure Active Directory**.
    4. Copy the **Tenant ID** value.

2. Enter the user's Azure Active Directory (Azure AD) object ID:

    1. In the [Azure portal](https://portal.azure.com), go to **Users**, and search for the user by email address.
    2. Select the user's name.
    3. Copy the **Object ID** value.

### Use Azure Cloud Shell to set up Finance insights Data Lake resources

# [Use a Windows PowerShell script](#tab/use-a-powershell-script)

A Windows PowerShell script has been provided, so that you can easily set up the Azure resources that are described in [Configure export to Azure Data Lake](../../fin-ops-core/dev-itpro/data-entities/configure-export-data-lake.md). If you prefer to do manual setup, skip this procedure, and continue with the procedure in the [Manual setup](#manual-setup) section.

> [!NOTE]
> Follow the steps below to run the PowerShell script. The Azure CLI "Try it" option, or running the script on your PC may not work.

Follow these steps to configure Azure by using the Windows PowerShell script. You must have rights to create an Azure resource group, Azure resources, and an Azure AD application. For information about the required permissions, see [Check Azure AD permissions](/azure/active-directory/develop/howto-create-service-principal-portal#permissions-required-for-registering-an-app).

1. In the [Azure portal](https://portal.azure.com), go to your target Azure subscription. Select the **Cloud Shell** button to the right of the **Search** field.
2. Select **PowerShell**.
3. Create storage if you're prompted to do so.
4. Go to the **Azure CLI** tab and select **Copy**.  
5. Open Notepad and paste the PowerShell script. Save the file as ConfigureDataLake.ps1.
6. Upload the Windows PowerShell script to the session using the menu option for upload in Cloud Shell.
7. Run the script .\ConfigureDataLake.ps1.
8. Follow the prompts to run the script.
9. Use the information from the script output to install the **Export to Data Lake** add-in in LCS.
10. Use the information from the script output to enable the entity store on the **Data connections** page in Finance (**System administration \> System parameters \> Data connections**).

### Manual setup

#### Add applications to the Azure AD tenant

1. In the [Azure portal](https://portal.azure.com), go to **Azure Active Directory**.
2. Select **Manage \> Enterprise applications**.
3. Search for the following applications by app ID.

    | Application                              | App ID                               |
    |------------------------------------------|--------------------------------------|
    | Microsoft Dynamics ERP Microservices     | 0cdb527f-a8d1-4bf8-9436-b352c68682b2 |
    | Microsoft Dynamics ERP Microservices CDS | 703e2651-d3fc-48f5-942c-74274233dba8 |
    | AI Builder Authorization Service         | ad40333e-9910-4b61-b281-e3aeeb8c3ef3 |

If you can't find any of the preceding applications, try the following steps.

1. On your local machine, select the **Start** menu, and search for **powershell**.
2. Select and hold (or right-click) **Windows PowerShell**, and then select **Run as administrator**.
3. Run the following command to install the **AzureAD** module.

    `Install-Module -Name AzureAD`

4. If a NuGet provider is required to continue, select **Y** to install it.
5. If an "Untrusted repository" message appears, select **Y** to continue.
6. For each application that must be added, run the following commands to add the application to Azure AD. When you're prompted, sign in as the Azure AD administrator.

    `Connect-AzureAD`

    `New-AzureADServicePrincipal –AppId <AppId>`

#### Create Azure resources

> [!NOTE]
> Make sure that you create the following resources in the same Azure AD instance as the Dataverse environment. You can't use resources from a different Azure AD instance.

1. Create a new storage account:

    1. In the [Azure portal](https://portal.azure.com), create a storage account.
    2. In the **Create storage account** dialog box, set the following fields:

        - **Location** – Select the data center where your environment is located.
        - **Performance** – We recommend that you select **Standard**.
        - **Account kind** – You must select **StorageV2**.

    3. In the **Advanced options** dialog box, for the **Data Lake storage Gen2** option, select **Enable** under the **Hierarchical namespaces** feature. If you disable this feature, you can't consume data that Finance and Operations apps write by using services such as Power BI data flows.
    4. Select **Review and create**. When the deployment is completed, the new resource will be shown in the Azure portal.
    5. Go to the storage account that you created.
    6. On the left menu, select **Access keys**.
    7. Copy and save the connection string for either **Key1** or **Key2**.
    8. Copy and save the storage account name.

2. Create a new key vault:

    1. In the [Azure portal](https://portal.azure.com), create a key vault.
    2. In the **Create key vault** dialog box, in the **Location** field, select the data center where your environment is located.
    3. After key vault is created, select it in the list, and then select **Secrets**.
    4. Select **Generate/Import**.
    5. In the **Create a secret** dialog box, in the **Upload options** field, select **Manual**.
    6. Enter a name for the secret. Make a note of the name, because you will have to provide it later.
    7. In the **Value** field, enter the connection string that you obtained from the storage account in the previous procedure.
    8. Select **Enabled**, and then select **Create**. The secret is created and added to Key Vault.
    9. Go to the **Key Vault Overview**, and make a note of the DNS name.

3. Create and register an Azure AD application:

    1. In the [Azure portal](https://portal.azure.com), go to **Azure Active Directory**, and then select **App registrations**.
    2. Select **New application registration**, and set the following fields:

        - **Name** – Enter the name of the app.
        - **Application type** – Select **Web API**.
        - **Redirect URI setup** – Enter the URL for your Dynamics 365 instance, such as, `https://yourdynamicsinstance.dynamics.com/auth`.

    3. Go to the app that you just created, and copy and save its **Application (client) ID** value. You will have to provide this value later, when you set up the key vault.
    4. Go to **API permissions**, and follow these steps:

        1. Select **Add a permission**.
        2. Select **Azure Key vault**.
        3. After you select delegated permissions, select **user\_impersonation**.
        4. Select **Add permissions**.

    5. On the menu for the app, select **Certificates \& secrets**, and then follow these steps to create Key Vault secrets:

        1. Select **New client secret**.
        2. In the **Key Description** field, enter a name.
        3. Select a duration, and then select **Add**. A secret is generated in the **Value** field.
        4. Copy and save the secret value.

4. Create Key Vault secrets:

    1. Go to the key vault that you created earlier, and select **Secrets**.
    2. For each secret name in the following table, follow these steps:

        1. Select **Generate/Import**.
        2. In the **Create a secret** dialog box, in the **Upload options** field, select **Manual**.
        3. Create the secret name and value from the following table.
        4. Select **Enabled**, and then select **Create**. The secret is created and added to Key Vault.

        | Secret name                       | Secret value                                                                                |
        |-----------------------------------|---------------------------------------------------------------------------------------------|
        | app-id                            | The app ID of the application that you created earlier                                      |
        | app-secret                        | The client secret that you saved earlier                                                    |
        | storage-account-name              | The name of the storage account that you created earlier, such as **storageaccount1**       |
        | storage-account-connection-string | The connection string that you copied from the **Access keys** page for the storage account |

5. Authorize the application to access the key vault:

    1. In the [Azure portal](https://portal.azure.com), open the key vault that you created earlier.
    2. Select the access policies.
    3. For each application in the following table, follow these steps:

        1. Select **Add Access Policy** to create an access policy.
        2. In the **Secret permissions** field, select the permissions from the following table.
        3. In the **Select principal** field, search for the application display name from the following table.
        4. Select **Select**.
        5. Select **Add**.
        6. Select **Save**.

        | Application                                              | Permissions |
        |----------------------------------------------------------|-------------|
        | The display name of the new application that you created | Get, List   |
        | **Microsoft Dynamics ERP Microservices**                 | Get, List   |

6. Assign roles to access the storage account:

    1. In the [Azure portal](https://portal.azure.com), open the storage account that you created earlier.
    2. Select **Access Control (IAM)**, and then select **Role Assignments**.
    3. Select **Add, Add Role Assignment**.
    4. For each application in the following table, follow these steps:

        1. Select the role from the following table.
        2. Leave the **Assign access to** field set to **Azure AD user, group, or service principal**.
        3. In the **Select** field, enter the application from the following table.
        4. Select **Save**.

        | Application                                              | Role                        |
        |----------------------------------------------------------|-----------------------------|
        | The display name of the new application that you created | Owner                       |
        | The display name of the new application that you created | Contributor                 |
        | The display name of the new application that you created | Storage Account Contributor |
        | The display name of the new application that you created | Storage Blob Data Owner     |
        | **AI Builder Authorization Service**                     | Storage Blob Data Reader    |

# [Azure CLI](#tab/azure-azure-cli)

```
function New-FinanceDataLakeAzureResources {
    Assert-ScriptSetup

    $ClientAppName = 'Finance Data Lake Application'
    $DefaultSecretExpiryInYear = 1
    $MicrosoftDynamicsERPMicroservicesAppId = '0cdb527f-a8d1-4bf8-9436-b352c68682b2'
    $MicrosoftDynamicsERPMicroservicesCDSAppId = '703e2651-d3fc-48f5-942c-74274233dba8'
    $AIBuilderAuthorizationServiceAppId = 'ad40333e-9910-4b61-b281-e3aeeb8c3ef3'
    $KeyVaultServicePrincipalAppId = 'cfa8b339-82a2-471a-a3c9-0fc0be7a4093'
    $GraphServicePrincipalAppId = '00000003-0000-0000-c000-000000000000'

    Import-Module AzureAD.Standard.Preview
    $connectAzureADParameters = @{ 'Identity' = $true; 'TenantId' = $env:ACC_TID }
    $azContext = AzureAD.Standard.Preview\Connect-AzureAD @connectAzureADParameters
    $userContext = ConvertFrom-Json ((az ad signed-in-user show) -join '')
    $user = Get-AzureADUser -Filter ("UserPrincipalName eq '" + $userContext.UserPrincipalName + "'")

    Set-AzureSubscription
    
    $resourceGroup = $null
    $ResourceGroupName = 'D365FinanceInsightsDataLake'
    $ResourceGroupNameSuffix = ''
    $FullResourceGroupName = ''
    Write-Output ("The default Azure Resource Group name is '{0}'" -f $ResourceGroupName)
    while (-not ($resourceGroup)) {
        $ResourceGroupNameSuffix = (Read-Host -Prompt "Enter optional Azure Resource Group name suffix: (leave blank for no suffix)")
        if ([string]::IsNullOrWhitespace($ResourceGroupNameSuffix))
        {
            $FullResourceGroupName = $ResourceGroupName
        }
        else
        {
            if ($ResourceGroupNameSuffix -notmatch "^[A-Za-z0-9]+$") {
                Write-Warning "The Azure Resource Group name suffix can only include alphanumeric characters."
                continue
            }

            if ($ResourceGroupNameSuffix.Length -gt 60) {
                Write-Warning "The Azure Resource Group name suffix cannot be longer than 60 characters."
                continue
            }

            $FullResourceGroupName = $ResourceGroupName + $ResourceGroupNameSuffix
        }
        
        $resourceGroup = Get-AzResourceGroup -Name $FullResourceGroupName -ErrorAction SilentlyContinue

        if (-not ($resourceGroup)) {
            Write-Output ("Your new Azure Resource Group name is '{0}'" -f $FullResourceGroupName)
            $resourceLocation = ''
            $azResourceLocations = (Get-AzLocation | Select-Object Location).Location
            while ([string]::IsNullOrWhitespace($resourceLocation) -or (-not ($resourceLocation -in $azResourceLocations))) {
                $resourceLocation = (Read-Host -Prompt "Enter the location in which to create the Azure Resource Group: ('help' to see values)")
                if ($resourceLocation -eq 'help') {
                    Write-Output ("List of available regions is '{0}'" -f ($azResourceLocations -join ','))
                }
                elseif ([string]::IsNullOrWhitespace($resourceLocation) -or (-not ($resourceLocation -in $azResourceLocations)))
                {
                    Write-Warning ("The provided location is not available for resource group. List of available regions is '{0}'" -f ($azResourceLocations -join ','))
                }
            }
            $resourceGroup = New-AzResourceGroup -Name $FullResourceGroupName -Location $resourceLocation
            Write-Output ("Created Azure Resource Group '{0}'" -f $resourceGroup.ResourceGroupName)
        }
        else {
            Write-Output ("Found Azure Resource Group '{0}'" -f ($resourceGroup.ResourceGroupName))
        }
    }

    Write-Output '================================================================================='
    $MicrosoftDynamicsERPMicroservicesAppObjectId = Create-ADServicePrincipal -AppId $MicrosoftDynamicsERPMicroservicesAppId
    Create-ADServicePrincipal -AppId $MicrosoftDynamicsERPMicroservicesCDSAppId | Out-Null
    $aibuilderAuthorizationServiceObjectId = Create-ADServicePrincipal -AppId $AIBuilderAuthorizationServiceAppId
    Write-Output ('=================================================================================')

    $clientAppSPN = Get-AzureADServicePrincipal -Filter ("DisplayName eq '" + $ClientAppName + "'")
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

        $clientApp = New-AzureADApplication -DisplayName $ClientAppName -RequiredResourceAccess @($keyVaultAccess, $graphAccess)
        $clientAppSPN = New-AzureADServicePrincipal -AppId $clientApp.AppId -Tags @($ClientAppName)
        $clientAppId = $clientApp.AppId
        Write-Output ('Created App Registration "' + $ClientAppName + '" with Application Id: ' + $clientAppId)
    }
    else {
        $clientApp = Get-AzureADApplication -Filter ("DisplayName eq '" + $ClientAppName + "'")
        $clientAppId = $clientApp.AppId
        Write-Output ('Found App Registration "' + $ClientAppName + '" with Application Id: ' + $clientAppId)
    }
            
    $clientAppSecretCredential = New-AzureADApplicationPasswordCredential -ObjectId $clientApp.ObjectId -CustomKeyIdentifier "ClientAppAccessKey" -EndDate (get-date).AddYears($DefaultSecretExpiryInYear)
    $ClientAppSecret = $clientAppSecretCredential.Value
    $clientAppSpId = $clientAppSPN.ObjectId

    Write-Output ('Generated application secret: ' + $ClientAppSecret)
    Write-Output '================================================================================='

    $templateObject = ConvertFrom-Json $azureTemplate -AsHashtable
    $templateObject.{$schema} = "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#"
    Write-Output 'Provisioning Azure resources. This may take a few minutes.'
    try {
        $deployment = New-AzResourceGroupDeployment -ResourceGroupName $FullResourceGroupName -TemplateObject $templateObject -aibuilderAppObjectId $aibuilderAuthorizationServiceObjectId -clientAppId $clientAppId -clientAppSecret $ClientAppSecret -clientAppSpObjectId  $clientAppSpId -microserviceSpObjectId $MicrosoftDynamicsERPMicroservicesAppObjectId -userSpObjectId $user.ObjectId -Force -ErrorAction Stop
    }
    catch {
        $ErrorMessage = $_.Exception.Message
        if ($ErrorMessage.Contains("not allowed to be updated"))
        {
            Write-Error ($ErrorMessage)
            Write-Warning "Some items in the existing resource group $FullResourceGroupName could not be updated. To resolve the issue, remove the existing resource group $FullResourceGroupName and run the script again."
        }
        else {
            throw
        }

    }
    if ($deployment.ProvisioningState -eq 'Succeeded') {
        Write-Output "Successfully deployed the following resources to Azure:"
        Write-Output ("  Key Vault:                         " + $deployment.Outputs.keyVaultName.Value)
        Write-Output ("  Storage Account:                   " + $deployment.Outputs.storageAccountName.Value)
        
        $keyVault = Get-AzKeyVault -VaultName $deployment.Outputs.keyVaultName.Value
        $tenantId = (Get-AzContext).Tenant.Id

        Write-Output "Values for LCS Data Lake Add-In:"
        Write-Output ("  Tenant ID:                         " + $tenantId)
        Write-Output ("  DNS Name:                          " + $keyVault.VaultUri)
        Write-Output "  Storage account secret name:       storage-account-name"
        Write-Output "  Application ID secret name:        app-id"
        Write-Output "  Application Secret secret name:    app-secret"
        Write-Warning "Copy this information for the LCS Add-in for easy access. Azure Cloud Shell will eventually time out and close."

        Write-Output '================================================================================='
        Write-Output "Values for System parameters > Data connections:"
        Write-Output ("  Application ID:                    " + $clientAppId)
        Write-Output ("  Application Secret:                " + $ClientAppSecret)
        Write-Output ("  DNS name:                          " + $keyVault.VaultUri)
        Write-Output "  Secret name:                       storage-account-connection-string"
        Write-Warning "Copy this information for the System parameters for easy access. Azure Cloud Shell will eventually time out and close."
    }
    else {
        Write-Output ("Provisioning Azure resources failed with the following state: " + $deployment.ProvisioningState)
        Write-Output ("Some of the resources may have been created in resource group: " + $FullResourceGroupName)
    }
}

function Assert-ScriptSetup {
    if ($PSVersionTable.PSEdition -ne 'Core' -or -not $env:ACC_TID) { 
        throw "This script needs to be uploaded and run from Azure Cloud Shell (PowerShell)." 
    }
    
    if ((Get-AzContext) -eq $null -and (Connect-AzAccount) -eq $null) {
        throw 'Unable to connect to Azure account.'
    }
}

function Set-AzureSubscription {
    $azSubscription = $null
    while (-not ($azSubscription)) {
        $subscriptionId = (Read-Host -Prompt "Enter the Azure Subscription ID: (leave blank for default)")
        if ([string]::IsNullOrWhitespace($subscriptionId)){
            break
        }
        elseif (-not [guid]::TryParse($subscriptionId, $([ref][guid]::Empty))) {
                Write-Warning "Azure Subscription ID must be a valid GUID."
                continue
        }

        $azSubscription = Select-AzSubscription -SubscriptionId $subscriptionId
    }
}

function Create-ADServicePrincipal {
    param (
        [string] $AppId
    )

    $service = Get-AzureADServicePrincipal -Filter ("AppId eq '" + $AppId + "'")
    if (-not $service) {
        New-AzureADServicePrincipal -AppId $AppId | Out-Null
        $service = Get-AzureADServicePrincipal -Filter ("AppId eq '" + $AppId + "'")
        Write-Host ("Added AAD Enterprise Application {0} with Application ID {1}" -f $service.DisplayName,$AppId)
    }
    else {
        Write-Host ("Found AAD Enterprise Application {0} with Application ID {1}" -f $service.DisplayName,$AppId)
    }

    return $service.ObjectId
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
  Start-Transcript -path (Join-Path $HOME Provision-FinInsights-Azure.log)
  New-FinanceDataLakeAzureResources
}
catch {
  Write-Error $_.Exception.Message

  if ($PSItem.Exception.StackTrace -ne $null)
  {
      Write-Warning $_.Exception.StackTrace
  }

  $inner = $_.Exception.InnerException
  while ($null -ne $inner) {
    Write-Output 'Inner Exception:'
    Write-Error $_.Exception.Message
    Write-Warning $_.Exception.StackTrace
    $inner = $inner.InnerException
  }
}
finally {
  Stop-Transcript
}

```
---



## Configure the data lake

Follow these steps to use LCS to add the Azure Data Lake add-in to the environment.

1. Sign in to LCS, and then, under the environment name on the right side of the page, select **Full Details**.
2. In the **Environment add-ins** section, select **Install a new add-in**.
3. Select the **Export to Data Lake** add-in.
4. Enter the following values.

    | Value                                                              | Description |
    |--------------------------------------------------------------------|-------------|
    | Tenant ID of the Azure Subscription where the Key Vault is located | The tenant ID where the storage account, apps, and key vaults are located. To find this value, open the [Azure portal](https://portal.azure.com), go to **Azure Active Directory**, and copy the **Tenant ID** value. |
    | Provide the DNS name of your Key Vault                             | The DNS name of the key vault, such as `https://customkeyvault.vault.azure.net/`. (This value matches the DNS name that is used in the entity store.) |
    | Provide the secret that contains the name of the storage account   | **storage-account-name** |
    | Secret Name for App ID to be used for accessing Data Lake          | **app-id** |
    | Secret name to be used with App ID                                 | **app-secret** |

5. Agree to the terms, and select **Install**.

The add-in will be installed within a few minutes.

## Configure AI Builder

1. Sign in to LCS, and open the **Environment details** page.
2. Scroll to the **Environment add-ins** section. You should see the add-ins that are already installed in this environment. If the **Export to Data Lake** add-in isn't among them, configure this add-in.
3. Select the **Get insights** add-in.
4. On the **Get insights** add-in details page, enter the following values.

    | Value                                                    | Description |
    |----------------------------------------------------------|-------------|
    | CDS Organization URL                                     | The Dataverse organization URL copied from above. |
    | CDS Org ID                                               | The Dataverse organization ID copied from above. |
5. Enable **Is this the default environment for you Tenant**.

The add-in might take serveral minutes to install.
    
## Configure the entity store

Follow these steps to set up the entity store in your Finance environment.

1. Go to **System administration \> Setup \> System parameters \> Data connections**.
2. Set the following key vault fields:

    - **Application (client) ID** – Enter the application client ID that you created earlier.
    - **Application Secret** – Enter the secret that you saved for the application that you created earlier.
    - **DNS name** – You can find the Domain Name System (DNS) name on the application details page for the application that you created earlier.
    - **Secret name** – Enter **storage-account-connection-string**.
3. Enable **Enable Data Lake integration**.
4. Select **Test Azure Key Vault** and verify there are no errors.
5. Select **Test Azure storage** and verify there are no errors.

## Feedback and support

Please send an email to [Customer payment insights (Preview)](mailto:fiap@microsoft.com) if you are interested in providing feedback or need support.

## Privacy notice

Previews (1) might use less privacy and fewer security measures than the Dynamics 365 Finance and Operations service, (2) aren't included in the service level agreement (SLA) for this service, (3) should not be used to process personal data or other data that is subject to legal or regulatory compliance requirements, and (4) have limited support.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
