---
# required metadata

title: Regulatory Configuration Services (RCS): Globalization feature
description: This topic explains how to use Microsoft Regulatory Configuration Services (RCS) and the Global repository to create and use Globalization features.
author: JaneA07
manager: AnnBe
ms.date: 05/20/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: RCS, RCSWorkspace, e-Invoicing service
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 97423
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: janeaug
ms.search.validFrom: 2020-05-01
ms.dyn365.ops.version: AX 10.0.11

---

# Regulatory Configuration Services (RCS): Globalization feature

[!include [banner](../includes/banner.md)]

You can use Microsoft Regulatory Configuration Services (RCS) to create a Globalization feature for use in Globalization services. Feature allows user to:
-	Define related feature components (Electronic reporting (ER) configurations and setup parameters) 
-	Manage feature lifecycle (through feature status)
-	Enable feature for Globalization features for defined F&O environments 
-	Sharing of feature with other organization

The following steps explain how a user in RCS can add a feature with related components, update its status and enable it for use in a Globalization service, like e-Invoicing service for an F&O environment. 
To complete these steps, you must first complete the steps related to:
-	Access to an RCS instance
-	Creation of a configuration provider that is active, see [Create configuration providers and mark them as active](../../fin-ops-core/dev-itpro/analytics/tasks/er-configuration-provider-mark-it-active-2016-11.md)

From Dynamics F&O you can take the following actions:
- Go to **Organization administration > Workspaces > Electronic reporting**.
- If you have no RCS environment provisioned to your company, you can click  **Regulatory services – Configuration** external link and follow the instructions to provision an RCS environment for your organization.

Note: If RCS environment has been already provisioned to your company, use the page URL to access it by selecting the sign in option.

## Requires Feature enablement:
-	Go to your instance of RCS and click on ** Feature management** tile
-	From the list select **Globalization features**
-	Click **Enable now** button

![Feature management Global feature](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/janeaug_rcs_Global-feature/articles/finance/localizations/media/RCS_GlobalF_1%20Feature%20mgmt.JPG)

> Note: Feature management text: This feature provides a new Globalization features workspace, a new form for creating, importing, and setting up available Globalization features for Globalization services use, such as e-Invoicing and tax services.

## Globalization feature
To use a Globalization feature user needs to import them from RCS/Global repository and create their own version of the feature to use it. There are two ways to utilize Globalization feature, user can either:
-	Add a new feature, based on an existing feature that has been published or shared with them by add/derive, or
-	Add a new feature from scratch

## Accessing Globalization features
-	Enable feature in **Feature management**
-	Go to New **Globalization feature workspace**
-	Click **e-Invoicing** feature tile

![Feature management Global feature](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/janeaug_rcs_Global-feature/articles/finance/localizations/media/RCS_GlobalF_2%20Feature%20wrkspace.JPG)

- Which opens the **Globalization features** form:

![Feature management Global feature](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/janeaug_rcs_Global-feature/articles/finance/localizations/media/RCS_GlobalF_3%20Feature%20form.JPG)

## Add feature by deriving from existing Globalization feature 
-	Import feature from Global repository
  -	Click **import** from **Action pane**
  
![Feature management Global feature](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/janeaug_rcs_Global-feature/articles/finance/localizations/media/RCS_GlobalF_4%20Feature%20import%20form%20GR.JPG)
 
  - Click **Synchronize** to get latest features 
    - Message: Global repo list updated
    - Note features that you see in the list are features that are available to you either:
    - Published by Microsoft, or 
    - Shared with you by another configuration provider
  
![Feature management Global feature](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/janeaug_rcs_Global-feature/articles/finance/localizations/media/RCS_GlobalF_5%20Feature%20GR%20sync.JPG)
 
  - Select feature(s) to import from feature list and click **import**
    - Message: Feature has been successfully imported

![Feature management Global feature](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/janeaug_rcs_Global-feature/articles/finance/localizations/media/RCS_GlobalF_6%20Feature%20GR%20import%20success.JPG)  

-	Add Feature by deriving:
  - Click **Add**
  - Select **Based on existing version**
  - Fill in Feature name and description
  - Select base version of the feature to derive from the list of available features 
  - Click **Create feature** 

![Feature management Global feature](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/janeaug_rcs_Global-feature/articles/finance/localizations/media/RCS_GlobalF_7%20Feature%20create%20derived.JPG) 

-	Newly added feature is created with a status of **Draft**

![Feature management Global feature](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/janeaug_rcs_Global-feature/articles/finance/localizations/media/RCS_GlobalF_8%20Feature%20draft%20create.JPG) 

-	Review the feature components to see if updates are needed:
  - Review Configurations in case it becomes necessary to customize the Electronic Reporting (ER) formats and its binding with format mappings for the feature version
  - Review Setup in case it becomes necessary to customize the Actions set, Applicability rules or Variables for the feature version
-	Go to **Versions** tab:
  - Select an **Effective from** date and complete description if not prefilled
  - Click **Change status** to complete 
-	Completed features can be:
  -	**Enable for** for a specific environment so the feature can be use in Globalization services
  -	**Published** to Global repository
  - Note: Features with ‘Feature version status’ of Published can be shared with external organization

## Add new Globalization feature 
-	Add Feature by creating a new feature from scratch:
  -	Click **Add**
  -	Select **New feature**
  -	Fill in Feature name and description
  -	Click **Create feature** 

![Global feature create](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/janeaug_rcs_Global-feature/articles/finance/localizations/media/RCS_GlobalF_9%20Feature%20create%20new.JPG) 

-	Newly added feature is created with a status of **draft**
-	Add required feature components – see below
-	Go to **Versions** tab:
  -	Select an **Effective from** date and
  -	Click **Change status** to complete 
-	Completed features can be:
  -	**Enable for** for a specific environment so the feature can be use in Globalization services
  -	**Published** to Global repository
  - Note: Features with ‘Feature version status’ of Published can be shared with external organization

## Feature components overview

Globalization feature has several components parts that cover: 
-	**Version**
  - Supports feature lifecycle management and allows user to manage status for different versions of the feature
-	**Configurations**
  -	Allows user to manage, view and edit related Electronic Reporting (ER) formats and format mappings
-	**Setups**
  -	Allows users of Globalization services, for example e-invoicing service, to manage the related Feature version set-up, supporting the flexible construction of communication and responses rules
-	**Environment**
  -	Allows users of Globalization services, for example e-invoicing service, to manage the environment where they want to use feature setup version, as well granting authorization for the users that will have access to it
-	**Organizations to share with**
  -	Allows user to share feature with external organization
  
## Configuring feature components:

-	**Version**
  -	Version manages Globalization feature lifecycle. Status can be changed through version tab ‘status change’. Permissible statuses are:
  -	Draft – feature can be edited only as draft
  -	Complete – feature and all related components are finalized and cannot be edited 
  -	Published – feature and all related components are published to Global repo
  -	Shared – feature and all related components are shared with external organizations
  -	Enabled – feature and all related components are enabled for use in a Globalization service, for example e-Invoicing
    Note: Some statuses are required to be moved through sequentially, so every status may not be available at every lifecycle stage.

-	**Configurations**
  -	View – Clicking view will allow the user to view the underlying feature configuration that don’t require any editing/updating
  -	Edit – Click editing will create a draft version of the selected configuration and allow user to make edits to the format or format mapping through the Format designer
  -	Delete – Allows user to delete selected configuration from the feature
  -	Rebase – Allows user to rebase the feature – for details see **Rebase section** below

-	**Setups**
  -	Add – Allows user to create a new feature setup, which can be either derived from an existing feature setup, or created from the scratch
  -	Delete – Allows user to delete selected feature setup
  -	View – Allows user to view the underlying feature setup that do not require any editing/updating
  -	Edit – Allows user to Create, Delete or Modify the attributes of the three main components of a feature setup:
  -	Actions and their parameters
  -	Applicability rules
  -	Variables
  
  Note: for more details, consult article: <TBD>
    
![Feature set up](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/janeaug_rcs_Global-feature/articles/finance/localizations/media/RCS_GlobalF_10%20Feature%20set%20up.JPG) 

-	**Environments**
 -	Enable – For a selected Feature version, it allows the user to choose a published environment and enable it with an ‘Effective from’ date onwards – for details see **Configuring Environments for enablement section** below
 -	Cancel – Allows user to remove an environment for a Feature setup

-	**Share with**
  -	To share a Globalization feature with an external organization user needs to take the following steps
   -	Select the feature that you want to share
   -	Go to **Share with** tab
   -	Click **+Organization**
   -	Enter Organization domain name and click **Share**
    
   scrnshot
   
   ![Global feature - Share with](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/janeaug_rcs_Global-feature/articles/finance/localizations/media/RCS_GlobalF_11%20Feature%20share%20with.JPG) 

  -	Feature is **Shared with** the organization and is available for them in the Global repository where it can be imported for use either into their RCS or F&O instance


## Rebasing a derived Globalization features:
User can leverage the ability to rebase a derived feature to the new/updated base feature version. This will allow changes that have occurred in the base version to be automatically updated: 
- Updated base version feature is created (by originating Configuration provider) and published or shared with user, for example: 
 
 scrnshot
 
 ![Feature management Global feature](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/janeaug_rcs_Global-feature/articles/finance/localizations/media/RCS_GlobalF_9%20Feature%20create%20new.JPG) 
 
 - User wants to rebase the derived version of the feature that they created
  -	Get the latest version of the feature by importing from Global repository
    -	Click **import** from **action pane**
    -	Click **Synchronize** to get latest features 
     -	Message: Global repo list updated
    -	Select features to import from feature list and click **import**
     -	Message: Feature has been successfully imported

scrnshot

![Feature management Global feature](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/janeaug_rcs_Global-feature/articles/finance/localizations/media/RCS_GlobalF_9%20Feature%20create%20new.JPG) 
 
  -	User goes to **Feature list** and selects feature that they want to be rebased:
    -	Go to **Version** tab and click **New** to create draft version. 
    -	Note: On **Version** tab – **Rebase** option is active

scrnshot

![Feature management Global feature](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/janeaug_rcs_Global-feature/articles/finance/localizations/media/RCS_GlobalF_9%20Feature%20create%20new.JPG) 

  - Click **Rebase** side window appears on right
  - Click the **drop down** and select the latest version of the feature to rebase to:

scrnshot

![Feature management Global feature](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/janeaug_rcs_Global-feature/articles/finance/localizations/media/RCS_GlobalF_9%20Feature%20create%20new.JPG) 

  -	Click **Ok**
  -	Message: A feature version rebase operation completed successfully
    
-	Note: Feature version components have been updated to the latest version
-	User can review feature components to make any changes required
-	Then click **Change status** to complete the rebased feature to be able to take subsequent actions like publishing and/or enabling for Globalization service use

scrnshot

![Feature management Global feature](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/janeaug_rcs_Global-feature/articles/finance/localizations/media/RCS_GlobalF_9%20Feature%20create%20new.JPG) 

## Configuring Environments for enablement: 
Allows users of Globalization services, for example e-invoicing service, to manage the environment where they want to use feature setup version, as well granting authorization for the users that will have access to it
-	Click on tile **e-invoicing** under **Environments**

scrnshot

![Feature management Global feature](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/janeaug_rcs_Global-feature/articles/finance/localizations/media/RCS_GlobalF_9%20Feature%20create%20new.JPG) 

-	Click **Key Vault parameters** to enter the details for the digital certificate
 -	Click **New** to create a Key Vault secret: 
      -	**Name** - name of the key vault
      -	**Description** - description of the key vault
      -	**Key Vault URI** - link that identifies the key vault resource in Azure
  -	Click **Add** to aggregate certificate names: 
      -	**Name** - name of certificate
      -	**Description** - description of the certificate

scrnshot

![Feature management Global feature](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/janeaug_rcs_Global-feature/articles/finance/localizations/media/RCS_GlobalF_9%20Feature%20create%20new.JPG) 

-	Click **New** to create a new environment: 
  -	**Name** - environment name
  -	**Description** - environment description
  -	**Storage SAS token secret** - name of stored certificate in key vault
  -	**Publish** - status of the environment:
   -	Not published: environment is created
   -	Changed: some of the environment attributes are changed, but not published yet
   -	Published: environment is published
  -	Click **New** to add the users that will have permission to access this environment:
   -	**User ID** – create User ID
   -	**Email** - users email address 
-	Click **Publish** to publish the environment

scrnshot

![Feature management Global feature](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/janeaug_rcs_Global-feature/articles/finance/localizations/media/RCS_GlobalF_9%20Feature%20create%20new.JPG) 


