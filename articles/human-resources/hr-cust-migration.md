---

# required metadata

title: Dynamics 365 Human Resources customer migration to the finance and operations infrastructure 
description: This article describes customer's Dynamics 365 Human Resources migration to the finance and operations infrastructure. 
author: twheeloc
ms.date: 10/25/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-10-13
ms.dyn365.ops.version: Human Resources

---

# Dynamics 365 Human Resources customer migration 

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

Customer migration is a lift and shift migration of customer database using the automated migration tooling to the finance and operations infrastructure; the result is a new Finance and operations environment utilizing the customer’s Human resources database.  

## Prerequisites 

### User Access and Permissions 
 - LCS user should have Organization admin role. 
 - User should be able to create Azure DevOps project or use an existing DevOps project 
 - User should have access to create Azure DevOps Personal Access Security Token or have a token available to use 

### Dataverse environment backup (Sandbox)
 - Refresh existing Human Resources sandbox with copy of HR Production (optional, recommended) 
 - Create a new dataverse environment using Power platform admin center. 
>[!Note]
>When adding database, ensure that Enable Dynamics 365 apps button is selected **Yes** 
 - Copy existing dataverse environment (linked to standalone HR app) to the newly created environment (in previous step) 

### Dataverse capacity 
 - Verify available capacity is sufficient for environment copy in the Dataverse storage using Summary page in the Power Platform admin center.  
 - If available capacity is not sufficient, reduce the overall consumption using free up storage space guidance. Customer may also elect to add additional storage 
 capacity.  

## Customer Migration Process 

### Create HR Migration LCS Project 
The first step is to create a new finance and operations implementation project in Lifecycle Services (LCS). The customer will have an existing Human Resources LCS 
project. The existing Human Resources environment(s) will be migrated to the new finance and operations Implementation project. 

### Steps to create a new project 

1. Log into LCS using global administrator or designated service account user. 
2. On the LCS home page, select the create/new (+) action to open the project creation pane.  
3. Select Finance and Operations product.  
4. Select project purpose as Implementation.  
5. Enter a project Name and Description appropriately. 
6. In the Project custom type drop-down list, select Microsoft Dynamics 365 Human Resources Migration.  
7. Select the check box to agree to Terms and Conditions. 
8. Select Create. 



After you have created a new LCS project, you will need to complete the additional setup and configuration of your LCS project. For example, you will be required to do 
the following:

 - Complete the project onboarding by clicking the hamburger menu and selecting Project onboarding. For more information about this process, see Project onboarding - 
 Finance & Operations | Dynamics 365 | Microsoft Docs.
      - For region selection, choose the same region as your current environment(s); this region selection does not impact migration.  
      - Use ‘other’ for legacy system.  
 - Complete the project settings including optionally configuring the SharePoint Online library, Azure DevOps and Azure connections. For more information, 
 see Lifecycle Services (LCS) user guide - finance and operations | Dynamics 365 | Microsoft Docs. 

>[!Note] 
>Customers may use existing Azure DevOps project and associated Personal Access Security Token; when using existing project, the configurations related to the project 
>are automatically available and can be reviewed for accuracy.  

### Migrating Human Resources environment 

Once you have created a new LCS project and completed the LCS project onboarding process, you are ready to migrate your first environment. We strongly recommend that 
you refresh the Sandbox environment that you want to migrate from your Production environment in the standalone infrastructure before starting this process.  

### Prepare to migrate Human Resources Sandbox environment 

#### Power Platform environment 
>[!Note] 
>This is only applicable to sandbox environment(s) migration. When migrating production, the existing PPAC environment, attached to the Prod will be carried forward.  

 - Create or use an existing power platform environment in the Power platform admin center to be used for sandbox migration.  
 - Copy an environment to refresh the power platform environment to use for mapping.  

#### Steps to Migrate Human Resources Sandbox environment 

1. Log into LCS as the global administrator or designated service account user.  
Note: It is recommended to use a named user account. The user should be logged in with the security role of ‘Project Owner’ or ‘Environment manager’ in the standalone 
Human Resources LCS project.  
2. Open newly created Human resources migration project in LCS. 
3. Review and complete appropriate phases of the migration methodology and the project onboarding.  
4. In the project dashboard, select the Migrate HR action in the Default: Standard Acceptance Test pane.  
5. In the Select environment to migrate pane, select appropriate Lifecycle Services project and originating Human Resources environment (from your source standalone 
Human Resources application).
6. Enable Map to new Power Platform environment and select appropriate Power Platform environment then click Next.  
7. Complete the Deployment settings (Finance and Operations – Sandbox) wizard to confirm details and Customer sign off before selecting Deploy.  
8. The environment state shows progress status from Loading to Deploying to Deployed.  

Graphical user interface, text, application, email

Description automatically generated 

Graphical user interface, text, application, email

Description automatically generated 

                
>[!NOTE]
>The production pane is grayed out and will not be available until the go-live project readiness checklist is completed.  See Prepare for go-live for more information.  

 
### Considerations/Assumptions:  

A Dynamics 365 Human Resources sandbox environment exists in an LCS project on the tenant for which: 
 - The Human Resources sandbox environment is not linked to an existing merged environment. A Human Resources environment may only have one migration in process at any
 given time. 
 - The number of sandbox environments allowed at a time is based on Human Resources licensing. If sufficient licensing has been purchased for the tenant, additional 
 sandbox environments will be listed in the Environments pane of the project. 
 - Migrations must be done to environments of the same type, meaning sandbox to sandbox and production to production.  

>[!NOTE] 
>Only the environment(s) type for Human Resources are considered when determining production or sandbox status.  If your environments are categorized incorrectly,
>a production environment is marked as sandbox or vice versa, please reach out to Microsoft Support to have your environment(s) types updated. 

 - For any reason when a migration is not successful, a failure error message is displayed on the respective environment. Additionally, a Delete button is available to
 delete failed migration and follow steps to re-migrate the environment. Customer may also elect to create a support ticket for additional assistance.  

Graphical user interface, application, email

Description automatically generated 

 

### Validate Human Resources Migration 

Once the sandbox migration process is successfully completed, you should create a detailed testing plan, where all business processes will be verified and signed off 
(similar to testing/validating through the initial implementation).  

Before you execute detail testing, validate the following: 
 - The migrated environment is accessible with generated URL. 
 - Users can access the migrated sandbox.  
 - Dataverse environment that is associated with migrated sandbox is accessible.  
 - Spot check various data to make sure that the most updated data is available.  
 - Execute your most critical business processes for validation.  
 - Your security policies are applicable.
 - Batch jobs are triggered as expected.  

You will not have remote desktop access to migrated sandbox, but you can operate your Tier 2+ sandbox environments by using self-service capabilities and tools to 
perform the common critical actions that are described here: 

 - Access the Azure SQL database. 
 - Access log files. 
 - Use perfmon tools. 
 - Turn Maintenance mode on/off. 
 - Restart services. 
 - Configure the Regression suite automation tool. 

Please review FAQ for Self-service deployment here.  

### Migrating Human Resources Production environment 

Once you have completed migrating and validation of a sandbox environment, you may follow additional steps to access your production environment.  

#### Pre-requisites to migrate Human Resources Production environment  
 - Subscription estimator should be completed 
 - Go-live readiness assessment should be completed 

#### Steps to migrate Human Resources Production environment 
 1. Log into LCS as the global administrator or designated service account user.  
>[!NOTE]
>It is recommended to use a named user account. The user should be logged in with the security role of ‘Project Owner’ or ‘Environment manager’ in the LCS project.  
2. Open newly created Human resources migration project in LCS. 
3. Review and complete appropriate phases of the migration methodology and the project onboarding.  
4. In the project dashboard, select the Migrate HR action in the Production pane.  
5. In the Select environment to migrate pane, select appropriate Lifecycle Services project and Originating Human Resources environment (from your source standalone 
Human Resources application) then click Next.
6. Complete the Deployment settings (Finance and Operations – Sandbox) wizard to confirm details and Customer sign off before selecting Deploy.  
7. The environment state shows progress status from Loading to Deploying to Deployed.  

#### Post migration considerations:  

 - Apply the latest quality updates on your environment(s) 
 - If using Virtual Tables, re-configure endpoints.  
 
Graphical user interface, text, application, email
Description automatically generated 

 - Re-configure Dual-write integration – Evaluate which entities are necessary to be enabled. 
 - Additional re-consideration for integration would be to utilize virtual tables to replace Dual-write.  

#### Dual-write integration 
#### Set up Power Platform Dual-write integration 

1. Go to Power Platform admin center and the Environments tab.  
2. Select the previously copied/refreshed environment and confirm the state is Ready.  
3. Go to LCS and confirm the migration project status is Deployed. 
4. Select Full details under the migrated environment, to review additional details and Setup Dual-write application.  
5. In the Dual-write application configuration pane, Select checkbox to agree mapping and synchronizing data between databases and select Configure.  
6. A pop-up message of successful trigger for the Dual-write configuration is received, click OK. 
7. Progress status can be monitored for the configuration in the details.  
8. Once the status for the configuration is complete, select Link to Power Platform environment to synchronize available data entities.  
9. Once the status reflects successful completion of environment linking, go to Power Platform admin center to review and select appropriate data entities.  
10. In the left hamburger pane, select Dynamics 365 apps under Resources menu.  
11. Find Dual-write Dynamics 365 Human Resources app to confirm the status is Enabled.  
12. Select the Dual-write Dynamics 365 Human Resources app and click Install.  
13. In the Install Dual-write Dynamics 365 Human Resources app pane, select the appropriate environment to install the package.  
14. Select checkbox to agree to terms of service and select Install.  
15. In the Environment Dynamics 365 apps, the status will reflect Installing while it is in progress and will update to Installed, once completed.  

#### Review and apply Dual-write solution 

1. In newly the created finance and operations environment, go to Data management workspace > Dual-write. 
2. Click on Apply solution.  
3. In the pane, select Dynamics installed solutions, Dual-write applications core entity maps and Dynamics 365 Human Resources maps and click Apply.  
4. An info message is displayed to confirm solution is being applied.  
5. Once solution is applied successfully, all the available Table maps are displayed.   
6. Review available Table maps to appropriately select and run integration using Dual-write. 
7. When running Dual-write integration, if there was an existing integration from the source Human resources environment, customers do not need to select Initial sync
checkbox when running the integration for table map(s). You may only run Initial sync checkbox when running the integration for the first time for that table map.  

Graphical user interface, text, application

Description automatically generated 

#### Recommended practices 

The following section outlines recommendations for performing the migration from the standalone infrastructure to the finance and operations app infrastructure. 

 - We highly recommend working with your Microsoft Dynamics partner to help aid with your Human Resources environment migration.   
 - Plan appropriate time to conduct a full user acceptance test (UAT) on the Sandbox migrated environment. 
 - Plan and document the detailed steps to migrate your integrations to the migrated environment. 
 - Create a detailed checklist to outline the cutover process for your migration. 
 - Plan an appropriate amount of downtime for your business while you perform the migration. 
 - Additionally, FastTrack qualified customers are also highly encouraged to work with your FastTrack Solution Architect to help oversee the migration process.  
 - We highly recommend that you refresh your Sandbox environment in the standalone infrastructure before you perform the first migration. This includes refreshing your 
 Dataverse environment connected to the Sandbox you plan to migrate to.  
 - We strongly recommend that you use a service account when you deploy, migrate, and create your LCS project.  
 - Plan to upgrade Sandbox for UAT validation on the latest GA release (see considerations)  
