---
# required metadata

title: ISV licensing (on-premises)
description: This topic describes the independent software vendor (ISV) licensing feature for on-premises environments.
author: manalidongre
manager: AnnBe
ms.date: 03/08/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 70381
ms.assetid: 90ae4ae6-f19a-4ea5-8bd9-1d45729b0636
ms.search.region: Global
# ms.search.industry: 
ms.author: manado
ms.search.validFrom: 2018-03-07
ms.dyn365.ops.version: AX 7.3.0

---

# ISV licensing (on-premises)

[!include[banner](../includes/banner.md)]

This topic provides information about how to import ISV licenses to an on-premises deployment of Microsoft Dynamics 365 for Finance and Operations, Enterprise edition. 
   
    >[!IMPORTANT]
    > The process documented in this article is only available for customers that have on-premises environments deployed with Platform Update 12 or higher.  

For general information on the benefits of ISV licensing, how to enable licensing for your solution, and other information related to self-signed certificates, see the topic, [ISV licensing](isv-licensing.md). 

## Pre-requisites 
Before you import the ISV license file into your on-premises environment, verify the following pre-requisites:  

- The most recent version of the local agent was used when deploying the environment. 
- The environment is deployed with Platform Update 12 and all hotfixes for Platform Update 12 are applied. This is mandatory because we have released a fix for an ISV licensing scenario. To get the latest set of hotfixes, use the tiles on the **Environment details** page in LCS.  
- The environment must be deployed and the AOS service must be running before your import the ISV license.  
- The ISV solution must be applied to the on-premises environment before you import the ISV license. The ISV package can be applied to an on-premises environment either during the deployment flow or as a post-deployment step using the **Apply Updates** flow in LCS. If the ISV solution is not applied prior to importing the license, the customizations will not be enabled.  

## Import licenses 
The following steps can be used for a sandbox environment or a production environment that is deployed in an on-premises project.  

    >[!NOTE]
    >Because importing an ISV license requires downtime, no business transactions can be performed on the environment during import. When you complete the import, make sure that no one is using the system and that an official downtime notice has been communicated to all the users.  

1. Collect the tenant name and ID for the customer to issue the license to.  

    1. Connect to the Service Fabric Explorer where the environment is hosted 
    2. Navigate to Clusters->Applications->AXSFType->fabric:\AXSF and click on the details tab on the right pane 
    3. In the parameters table, locate the values for the keys License_TenantDomainGuid and Licence_TenantId 

2. Generate a license for the customer (tenant ID and name), and sign the license by using the certificate's private key. You must pass the following parameters to the axutil genlicense command to create the license file. This will generate an xml file.  

  | Parameter name  | Description                                                                                                          |
|-----------------|----------------------------------------------------------------------------------------------------------------------|
| file            | The name of the license file.                                                                                        |
| licensecode     | The name of the license code from Microsoft Visual Studio.                                                           |
| certificatepath | The path of the certificate's private key.                                                                           |
| password        | The password of the certificate's private key.                                                                       |
| customer        | The customer's tenant name.                                                                                          |
| serialnumber    | The customer's tenant ID.                                                                                            |
| expirationdate  | Optional: The license expiration date.                                                                               |
| usercount       | Optional: The number that can be required for the custom validation logic. This can be, but is not limited to users. |

Here is an example: 
C:\AOSService\PackagesLocalDirectory\Bin\axutil genlicense /file:c:\templicense.txt /certificatepath:c:\tempisvcert.pfx /licensecode:ISVLicenseCode /customer:TAEOfficial.ccsctp.net /serialnumber:4dbfcf74-c5a6-4727-b638-d56e51d1f381 /password:********  

3. Copy the generated licenses to a folder in one of the machines that is running fabric:/AXSF and verify that fabric:/AXSF is healthy.
4. Run the following Import-LicensePackage.ps1 script from one of the AOS machines. This script can be found in the latest Deployment scripts folder available in **Shared Asset** library in LCS under the **Model** tab. Below is the list of parameters to pass to the script.

| LicenseFilesPath      | The path to a folder that ocntains the license files that need to be imported. |
|-----------------------|-------------|
| SqlUser               | The same user that is specified in the credentials.json file to run the AOS. |
| SqlPassword           | The password that can be used to connect to SQL. |
| EnvironmentConfigPath | The configuration file for the environment. The file, config.json, is located under the agent share in the folder with the format wp\<environment-name>\StandaloneSetup. |

5. After the command is executed, a log file is generated for each license file that is processed in the format {license_file_name}.output.log and {license_file_name}.error.log. The logs generated during database synchronizer are in a file of format dbsync.output.log and dbsync.error.log. 
6. Once script executes successfully, validate that the config key has been imported and is enabled. In the product, the corresponding configuration key will be available and enabled on the License configuration page. By default, the configuration is enabled. For example, if you have added a configuration key by the name 'ISVConfigurationKey1' it will be visible in this page as shown in the screenshot below. 
7. After the configuration key is enabled, the changes in the ISV solution will be visible in the product.  







