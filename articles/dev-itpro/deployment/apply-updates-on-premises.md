---
# required metadata

title: Apply updates to an on-premises deployment
description: This topic provides information about how to apply updates to an on-premises deployment for Microsoft Dynamics 365 for Finance and Operations, Enterprise edition.
author: manado
manager: AnnBe
ms.date: 11/06/2017
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
ms.search.scope: Operations, Unified Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sarvanis
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: Platform update 12

---
# Apply updates to an on-premises deployment

[!include[banner](../includes/banner.md)]

This topic provides information about how to apply supported updates to an on-premises environment of Dynamics 365 for Finance and Operations, Enterprise edition. Any updates that are made to an on-premises environment are done through Lifecycle Services (LCS). 


## Update types
There are four kinds of updates that can be applied to an on-premises deployment of Dynamics 365 for Finance and Operations: 
- Customizations 
- Application hotfixes released by Microsoft  
- Platform update  
- Application binary updates  
Currently, only the application of customizations, X++ application hotfixes, and platform updates to on-premises environments are supported. 

> [!IMPORTANT]
> Before you apply any updates, save the configuration settings that were used to deploy an on-premises environment because when you apply updates, you will need to re-enter the configuration settings.

## Apply code customizations
To apply customizations at the same time that you deploy a new on-premises environment, follow the steps in the topic, [Develop and deploy custom models to on-premises environments](develop-deploy-custom-models-on-premises.md). To apply new customizations on an already deployed environment, complete the following steps: 

1. In Lifecycle Services, navigate to the on-premises implementation project.  
2. Under **Environments**, click **Delete** to delete the application. This will clean up and remove any code that is deployed. When you click **Delete**, the on-premises agent, the data, and the infrastructure are not affected. 

![Delete an application](./media/apply-updates-on-prem-env-01.png)

3. After the environment is deleted, click **Configure** to re-deploy with a new application and custom code.  
4. In the **Advanced settings** of the deployment configuration, select the application deployable package to apply, and then click **Done** to continue with the environment deployment process.  

## Find and apply application hotfixes
There are two ways to find available application hotfixes: 
- **Issue Search** in Lifecycle Services - To learn more about issue search, see [Issue search](../lifecycle-services/issue-search-lcs.md).  
- **Application hotfix** tiles - For cloud-hosted environments, the **Environment details** page shows all of the hotfixes that are applicable to that environment based on the version that is currently deployed. The tile functionality is not available for on-premises environments, so if a customer wants to see the list of applicable hotfixes, a cloud-hosted development environment should be maintained on the same version as the on-premises sandbox or production environment. Note that this is only recommended for X++ hotfixes and not for any other kind of updates.

Complete the following steps to apply the hotfix.

1. Download the required hotfix to your development environment, and then follow the steps in the article, Create a deployable package (create-apply-deployable-package.md).  
2. After you have the deployable package, upload the package to the Lifecycle Services Asset library on the **Software deployable packages** tab.  
3. Similar to applying code customizations, you can include the deployable package as an asset when you deploy an environment. Follow the steps in the section in this topic, **Apply code customizations**, to apply this package to new environment or to an already deployed environment. 

## Apply the latest platform update 
There are two ways to apply the latest platform update: 
  - Deploy a new environment and select the latest platform update topology during deployment. Then, follow the regular environment deployment steps. 
  - To update an existing environment wtih the latest update, select **Delete** to delete the application and then select **Configure** to deploy a new version of the platform on the on-premises environment. 
