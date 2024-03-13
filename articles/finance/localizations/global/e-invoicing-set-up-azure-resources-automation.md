---
title: Create Azure resources using Azure PowerShell or ARM templates
description: This article explains how to create Microsoft Azure resources required for Electronic invoicing using Azure PowerShell or ARM templates.
author: amkedi
ms.date: 03/11/2024
ms.topic: article
ms.prod: 
ms.technology: 
audience: 
ms.reviewer: johnmichalak
ms.search.region: 
ms.author: amkedi
ms.search.validFrom: 
ms.dyn365.ops.version: 
ms.custom: 
ms.assetid: 
ms.search.form: 
---

# A step-by-step guide to automate the creation of Azure resources for e-invoicing.

[!include [banner](../../includes/banner.md)]

# Introduction
To enable e-invoicing in Dynamics 365 Finance, you need to create and configure several Azure resources, such as Azure Key Vault, Azure storage account, Azure container etc. This process can be time-consuming and error-prone if done manually. To simplify and automate this process, you can use a PowerShell script or an [ARM template](https://learn.microsoft.com/en-us/azure/azure-resource-manager/templates/overview) that creates and configures all the required Azure resources for you.

# Using Azure PowerShell
## Prerequisites
Before you run the PowerShell script, you need to have the following prerequisites:
- An Azure subscription with sufficient permissions to create and manage resources.
- You have installed the [Azure PowerShell](https://learn.microsoft.com/en-us/powershell/azure/install-azure-powershell) module (A supported version of [PowerShell version 7 or higher](https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell-on-windows) is the recommended version of PowerShell for use with the Az PowerShell module)
- The PowerShell script file.

## PowerShell script
```
param (
    [Parameter(Mandatory=$true)]
    [string]$subscriptionId,

    [Parameter(Mandatory=$true)]
    [string]$resourceGroup,

    [Parameter(Mandatory=$true)]
    [string]$location,

    [Parameter(Mandatory=$true)]
    [string]$storageAccountName,

    [Parameter(Mandatory=$true)]
    [string]$keyVaultName,

    [Parameter(Mandatory=$true)]
    [string]$containerName,

    [Parameter(Mandatory=$true)]
    [string]$storageAccountKeyVaultSecretName
)

if (!(Get-Module -ListAvailable -Name Az)) {
    throw "Az PowerShell module is required to run this script. Please install from https://learn.microsoft.com/en-us/powershell/azure/install-azure-powershell."
} 

function Write-ErrorMessage {
    param (
        [string]$errorMessage
    )
    Write-Host "Error: $errorMessage" -ForegroundColor Red
    exit 1
}

function Write-VerboseMessage {
    param (
        [string]$message
    )
    Write-Host "Verbose: $message" -ForegroundColor DarkYellow
}

function Confirm-ResourceExists {
    param (
        [string]$resourceType,
        [string]$resourceName,
        [string]$resourceGroup = ''
    )

    try {
        switch ($resourceType) {
            'ResourceGroup' {
                Get-AzResourceGroup -Name $resourceName -ErrorAction Stop | Out-Null
            }
            'StorageAccount' {
                Get-AzStorageAccount -ResourceGroupName $resourceGroup -Name $resourceName -ErrorAction Stop | Out-Null
            }
            'StorageContainer' {
                Get-AzStorageContainer -Name $resourceName -ErrorAction Stop | Out-Null
            }
            'KeyVault' {
                $kv = Get-AzKeyVault -ResourceGroupName $resourceGroup -VaultName $resourceName

                if ($null -eq $kv)
                {
                    return $false
                }
            }
        }
        return $true
    } catch {
        return $false
    }
}

# Connect to Azure account and set the subscription context
try {
    Write-VerboseMessage "Connecting to Azure account..."
    Connect-AzAccount -Subscription $subscriptionId -ErrorAction Stop -Verbose
} catch {
    Write-Host $_.Exception.Message
    Write-ErrorMessage "Failed to connect to the Azure account or set subscription context."
}

try {
    Write-VerboseMessage "Checking if the e-invoice service principal exists."
    $objectId = (Get-AzADServicePrincipal -ApplicationId "ecd93392-c922-4f48-9ddf-10741e4a9b65" -ErrorAction SilentlyContinue -Verbose).Id 

    if ($null -eq $objectId)
    {
        Write-VerboseMessage "The e-invoice service principal does not exist. Trying to create now."
        New-AzADServicePrincipal -AppId "ecd93392-c922-4f48-9ddf-10741e4a9b65" -ErrorAction Stop -Verbose
    }
    else {
        Write-VerboseMessage "The e-invoice service principal already exists. No action required."
    }
}
catch {
    Write-Host $_.Exception.Message
    Write-ErrorMessage "Adding e-Invoicing Service to your tenant as a service principal failed."
}

# Check if the resource group exists
if (-not (Confirm-ResourceExists -resourceType 'ResourceGroup' -resourceName $resourceGroup)) {
    try {
        Write-VerboseMessage "Creating Azure resource group..."
        New-AzResourceGroup -Name $resourceGroup -Location $location -ErrorAction Stop -Verbose
        $msg = "Resource group {0} created successfully in at location: {1}." -f $resourceGroup, $location
        Write-VerboseMessage $msg
    } catch {
        Write-Host $_.Exception.Message
        Write-ErrorMessage "Failed to create Azure resource group."
    }
} else {
    Write-VerboseMessage "Resource group '$resourceGroup' already exists."
}

# Check if the Azure Key Vault exists
if (-not (Confirm-ResourceExists -resourceType 'KeyVault' -resourceName $keyVaultName -resourceGroup $resourceGroup)) {
    try {
        Write-VerboseMessage "Creating Azure Key Vault..."
        New-AzKeyVault -Name $keyVaultName -ResourceGroupName $resourceGroup -Location $location -ErrorAction Stop -Verbose
        $msg = "Key vault {0} created successfully in resource group: {1} at location: {2}." -f $keyVaultName, $resourceGroup, $location
        Write-VerboseMessage $msg
    } catch {
        Write-Host $_.Exception.Message
        Write-ErrorMessage "Failed to create Azure Key Vault."
    }
} else {
    Write-VerboseMessage "Azure Key Vault '$keyVaultName' already exists."
}

# Check if the storage account exists
if (-not (Confirm-ResourceExists -resourceType 'StorageAccount' -resourceName $storageAccountName -resourceGroup $resourceGroup)) {
    try {
        Write-VerboseMessage "Creating Azure Storage Account..."
        New-AzStorageAccount -ResourceGroupName $resourceGroup `
          -Name $storageAccountName `
          -Location $location `
          -SkuName Standard_LRS `
          -Kind StorageV2 `
          -AllowBlobPublicAccess $true -ErrorAction Stop -Verbose

          $msg = "Storage account {0} created successfully in resource group: {1} at location: {2}." -f $storageAccountName, $resourceGroup, $location
          Write-VerboseMessage $msg
    } catch {
        Write-Host $_.Exception.Message
        Write-ErrorMessage "Failed to create Azure Storage Account."
    }
} else {
    Write-VerboseMessage "Storage account '$storageAccountName' already exists."
}

# Check if the storage container exists
$ctx = (Get-AzStorageAccount -ResourceGroupName $resourceGroup -Name $storageAccountName).Context
Set-AzCurrentStorageAccount -Context $ctx
if (-not (Confirm-ResourceExists -resourceType 'StorageContainer' -resourceName $containerName -resourceGroup $resourceGroup)) {
    try {
        Write-VerboseMessage "Creating storage container..."
        New-AzStorageContainer -Name $containerName -Context $ctx -ErrorAction Stop -Verbose
        $msg = "Storage container {0} created successfully in storage account: {1}." -f $containerName, $storageAccountName
        Write-VerboseMessage $msg
    } catch {
        Write-Host $_.Exception.Message
        Write-ErrorMessage "Failed to create storage container."
    }
} else {
    Write-VerboseMessage "Storage container '$containerName' already exists."
}

# Set the start and end time for the SAS token
$StartTime = Get-Date
$EndTime = $StartTime.AddYears(3)

# Generate SAS token for the container
try {
    Write-VerboseMessage "Generating SAS token for the container..."
    $sasToken = New-AzStorageContainerSASToken -Name $containerName -Permission racwdli -Protocol HttpsOnly -StartTime $StartTime -ExpiryTime $EndTime -Context $ctx -ErrorAction Stop -Verbose
    $msg = "SAS token for container {0} generated successfully with full permissions. The token would expire on {1}." -f $containerName, $EndTime
    Write-VerboseMessage $msg
} catch {
    Write-Host $_.Exception.Message
    Write-ErrorMessage "Failed to generate SAS token for the container."
}

# Construct the SAS URL
$sasURL = "https://$($storageAccountName).blob.core.windows.net/$($containerName)?$($sastoken)"

# Set access policy for the application to get and list secrets
try {
    Write-VerboseMessage "Setting access policy for Azure Key Vault..."
    Set-AzKeyVaultAccessPolicy -VaultName $keyVaultName -ObjectId $objectId -PermissionsToSecrets get,list -ErrorAction Stop -Verbose
    $msg = "Get and list access policies set successfully on key vault {0} for the e-invoicing application {1}." -f $keyVaultName, $objectId
    Write-VerboseMessage $msg
} catch {
    Write-Host $_.Exception.Message
    Write-ErrorMessage "Failed to set access policy for Azure Key Vault."
}

# Convert SAS URL to secure string
$secretvalue = ConvertTo-SecureString $sasURL -AsPlainText -Force

# Create a new secret in Azure Key Vault
try {
    Write-VerboseMessage "Creating secret in Azure Key Vault..."
    Set-AzKeyVaultSecret -VaultName $keyVaultName -Name $storageAccountKeyVaultSecretName -SecretValue $secretvalue -Expires $EndTime -ContentType "" -ErrorAction Stop -Verbose
    $msg = "Secret {0} created successfully in {1} and will expire on {2}." -f $storageAccountKeyVaultSecretName, $keyVaultName, $EndTime
    Write-VerboseMessage $msg
} catch {
    Write-Host $_.Exception.Message
    Write-ErrorMessage "Failed to create secret in Azure Key Vault."
}

# Display the secret
Write-Host "Secret created successfully."
```
## Running the PowerShell script
To run the PowerShell script, follow these steps:
1. Open PowerShell and navigate to the folder where the PowerShell script file and the configuration file are located.
2. Run the following command to execute the PowerShell script using your own parameters:
```
.\Create-AzureResourcesForEInvoice.ps1 -subscriptionId <azure_subscription_id> -resourceGroup <resource_group_name> -location <resource_group_location> -storageAccountName <storage_account_name> -containerName <container_name> -storageAccountKeyVaultSecretName <SAS_token_keyvault_secret_name>
```
3. The script will prompt you to sign in to your Azure account. Enter your credentials and click Sign in.
4. The script will first check if the e-invoice service principal already exists and create if it doesn’t.
5. The script will create and configure the following Azure resources: Azure resource group, Azure key vault, Azure storage account, Azure storage account container.
6. It will check if the Azure resources already exist. If any resource already exists, it will skip creating it and proceed to the next one.
7. It also generates a SAS token for the storage account container and add it as a key vault secret in the Azure key vault.
8. Finally, the script also sets the access policy on the key vault to provide get and list permission to the e-Invoicing application.
9. The script will output the details of the created Azure resources, such as the names, URLs, etc.
10. Note: You can execute the same script in case you need to renew a SAS token that has expired. It will skip creation of the resources but generate a new SAS token and update it in the key vault.

# Using ARM template
## ARM template
```
{
    "$schema": "https://schema.management.azure.com/schemas/2015-01-01/deploymentTemplate.json#",
    "contentVersion": "1.0.0.0",
    "parameters": {
        "keyVaultName": {
            "type": "string",
            "metadata": {
                "description": "Name of KeyVault to Store secrets/certificates/SaS Token"
            }
        },
        "tenantID": {
            "type": "string",
            "metadata": {
                "description": "Azure AD Tenant ID"
            }
        },
        "keyVaultAccessObjectID": {
            "type": "string",
            "metadata": {
                "description": "ID of user or App to grant access to KV"
            },
			"defaultValue": "ecd93392-c922-4f48-9ddf-10741e4a9b65"
        },
        "StorageAccountName": {
            "type": "string",
            "metadata": {
                "description": "Name of Storage Account to Create"
            }
        },
		 "ContainerName": {
            "type": "string",
            "metadata": {
                "description": "Name of container for einvoice upload"
            }
        },
        "accountSasProperties": {
            "type": "object",
            "defaultValue": {
                "signedServices": "bf",
                "signedPermission": "rwacld",
                "signedExpiry": "2024-12-01T00:00:00Z",
                "signedResourceTypes": "o"
            }
        }
    },
    "variables": {},
    "resources": [
        {
			"name": "[parameters('StorageAccountName')]",
            "type": "Microsoft.Storage/storageAccounts",
            "apiVersion": "2018-07-01",  
            "location": "[resourceGroup().location]",
            "tags": {
                "displayName": "[parameters('StorageAccountName')]"
            },
            "sku": {
                "name": "Standard_LRS"
            },
            "kind": "StorageV2",
			"properties": {
				"allowBlobPublicAccess": true
			},
			"resources":[
				{
            "type": "blobServices/containers",
            "apiVersion": "2018-03-01-preview",
            "name": "[concat('default/', parameters('ContainerName'))]",
            "dependsOn": [
                "[parameters('StorageAccountName')]"
            ],
            "properties": {
                "publicAccess": "None"
            }
        }
			]
        },
        {
            "type": "Microsoft.KeyVault/vaults",
            "apiVersion": "2018-02-14",
            "name": "[parameters('keyVaultName')]",
            "location": "[resourceGroup().location]",
            "tags": {
                "displayName": "[parameters('keyVaultName')]"
            },
            "properties": {
                "enabledForDeployment": true,
                "enabledForTemplateDeployment": true,
                "enabledForDiskEncryption": true,
                "tenantId": "[parameters('tenantID')]",
                "accessPolicies": [
                    {
                        "tenantId": "[parameters('tenantID')]",
                        "objectId": "[parameters('keyVaultAccessObjectID')]",
                        "permissions": {
                            "keys": [
                                "get"
                            ],
                            "secrets": [
                                "list",
                                "get"
                            ]
                        }
                    }
                ],
                "sku": {
                    "name": "standard",
                    "family": "A"
                }
            }
        },
        {
            "apiVersion": "2018-02-14",
            "type": "Microsoft.KeyVault/vaults/secrets",
            "dependsOn": [
                "[concat('Microsoft.KeyVault/vaults/', parameters('keyVaultName'))]"
            ],
            "name": "[concat(parameters('keyVaultName'), '/', 'StorageSaSToken')]",
            "properties": {
                "value": "[concat('https://', parameters('StorageAccountName'), '.blob.core.windows.net/', parameters('ContainerName'), '?', listAccountSas(parameters('StorageAccountName'), '2018-07-01', parameters('accountSasProperties')).accountSasToken)]"
            }
        }
    ],
    "outputs": {}
}
```
## Deploying the ARM template
1. Go to the [Azure portal](https://portal.azure.com/) and search for "Deploy a custom template".
2. Click on 'Build your own template in the editor'
3. Copy the ARM template provided above in the editor and click on Save.
4. Provide the required parameters.
5. Click on "Review + Create".
6. Review the details and click on "Create".

# Verifying the Azure resources
To verify that the Azure resources are created and configured correctly, you can do the following:
- Log in to the Azure portal and navigate to the resource group that contains the Azure resources. You should see the resources with the names specified in the PowerShell script/ARM template parameters.
- Open the Azure Key Vault resource and check if the SAS token for the Azure storage account is created and has the correct value.
