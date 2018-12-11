---
# required metadata

title: Entity store is a data lake
description: This topic provides information about data management in Microsoft Dynamics 365 for Finance and Operations.
author: MilindaV2
manager: AnnBe
ms.date: 12/11/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations

# ms.tgt_pltfrm: 
ms.custom: 96283
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: milindav
ms.search.validFrom: 2018-12-03
ms.dyn365.ops.version: Platform Update 23

---

# Entity store is a data lake

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/private-preview-banner.md)]

This is a restricted scenario enabled via flighting. This scenario is being delivered via multiple platform updates. 
Automated Entity store refresh – available in PU23 
Entity store data in Azure Data Lake (full push) – available in PU23. Restricted.  
DataFlows for Entity store schemas in PowerBI.com – available in a future PU  
Entity store data in Azure Data Lake (trickle feed) – available in a future PU 
Analytical workspaces extensible with PowerBI.com - available in a future PU 

## Automated Entity store refresh  
When you launch System Administration > Set up > Entity store UI, you will see a message indicating that you can switch to the Automated Entity store refresh option.  
With this option Entity store refresh is managed by the system – administrator does not need to schedule and monitor Entity store refresh. 
This is a non-reversible option. Once chosen, you can’t re-enable the legacy UI. 
 
 
Choose Switch now 
 
 
Select Yes to continue. You will see the new experience as follows. 
 
 
Once the new experience is enabled, you will be able to define the desired refresh for each of the aggregate measurements.  
Following refresh options are available to choose. Additional options including options for real-time refresh will be added in future platform updates.  
Every hour 
Twice a day 
Once a day 
Once a week 
In addition to these options, administrator can refresh any aggregate measurement on demand by selecting the Refresh now button. 
 
## Entity store data in Azure Data Lake 
This is a restricted feature enabled via flighting. Following experience applies if your environment is included in the flight. 
With this option, Entity store data is populated in an Azure Data Lake (storage gen2) account in your own subscription – instead of the relational Entity store in Microsoft subscription. 
You can use full capabilities of PowerBI.com and other Azure tools to work with Entity store. 
Before you start, you need to perform these steps in Azure portal 
You need to provision a storage account via Azure portal in the same data center that your Dynamics 365 for Finance and Operations is provisioned. You must have the connection string to storage account ready for the next step. See appendix for step by step instructions  
You need to provision a Key Vault in your own subscription using Azure portal. Note down the DNS name of the KeyVault entry you created. 
You need to add a secret to the Key Vault with the value of the connection string. Note down the name of the secret that you added to Key Vault. You need to provide this information to the system later.  
Create an Azure Active Directory Application and grant API access to Azure Key vault. Keep the Application ID (not Application name) and its Application Key /secret handy. You need to provide these ‘Application ID’ and ‘Application Secret’ to the system later. 
Open the key vault you created earlier. Using Access policies option, grant the application you created above with get and list permissions. This grants the Azure application with access to the secrets in the on the Key Vault.  
Launch System Administration > Set up > System parameters UI, you will see a new tab Data connections included with system parameters form as follows 
 
 
Provide the information you noted earlier in the Data connections tab in the system parameters form 
Provide the Azure Active Direction Application ID you registered above in the Application ID field.  
Provide the Application key/ secret in the Azure Active Directory application in the Application Secret field. 
Provide the DNS name of the Key Vault in the DNS Name field 
Provide the name of the secret you added to the key vault with connection string information in the secret name field 
Next select Test Azure Key Vault and Test Azure storage links to validate whether the configuration information you provided is accessible to the system 
Next, select Enable data connection check box 
With this configuration, Entity store data should be populated into the storage location you provided instead of the Relational Entity store database. 
Aggregate measurements and refresh options you choose in Entity store UI should now apply to data copied to Data lake. 
 
  
## Create Storage accounts 
Go to Azure portal and create a new storage account. Provide following specific values in the parameters shown in the Create storage account dialog 
Location: choose the data center where your Dyn365F&O is located. If you choose a data center which is in a different Azure region, you will incur additional data movement costs. If your PowerBI and/or data warehouse is in a different region. You can choose replication as a strategy to move storage between regions. 
Performance: Standard is recommended 
Account Kind: you must choose StorageV2 
 
In the advanced options dialog, disable Data Lake storage Gen2 (preview) option.  
We will enable this mode in a later PU. Until then, you will not be able to consume data using ADLS APIs 
You may not see this option if you are not part of the preview program for ADLS Gen2 
Select review and create.  
When the deployment is complete, the newly created resource will be shown in the Azure portal 
Select the resource and select settings > access keys.  
Copy the connection string parameter value – you will need this in the next step 
 
## Create a key vault and a secret 
Go to Azure portal and create a new Key vault. Provide following specific values in the parameters shown in the Create key vault dialog 
Location: choose the data center where your Dyn365F&O is located. 
When the key vault is created. Choose the Key vault you created, select Secrets.  
Select Generate/Import.  
Create a secret dialog will be displayed. In the upload options field, choose manual. 
Provide a name for the secret. Note this name, you need to provide this name to the system later 
Enter the connection string you obtained from the storage account in previous step in the value field 
Select enabled and select the Create button 
Your secret will be created and added to the key vault 
 
## Register the App 
Launch Azure portal and choose Azure Active Directory. Launch App registrations option 
Select new Application registration. Provide following values and create the Application. 
Name: provide a name for your app 
Application type: Web API 
Sign-on URL: copy paste the root URL of Dynamics 365 F&O 
Once the application is created, choose the application and choose settings icon.  
Select required permissions option.  
In the required permissions dialog, select Add option. 
Select Add API option. In the list of APIs shown, select Azure Key Vault 
Select Delegated permissions check box. Select to grant permissions. Choose Done to save changes  
Next select Keys in the application menu of the newly created application 
Provide a name in the Key Description field. Choose a Duration. Select the Save button 
A secret will be generated in the value field. Copy this secret to clipboard– it will disappear in a minute or so. You will need to provide this key to the application later. 
 
## Add service principal to Key vault 
Launch Azure portal and open Key Vault you created above 
Select Access policies. Select Add icon to create a new access policy 
In the select principal field, choose the name of the application you registered above. 
In the Key permissions field, choose Get and List permissions as shown below 
In the Secret permissions field, choose Get and List permissions as shown below 
Select Save 
 
 
 
 
