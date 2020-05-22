---
# required metadata

title: Regulatory Configuration Services (RCS) - Globalization feature
description: This topic explains how to use Microsoft Regulatory Configuration Services (RCS) and the Global repository to create and use Globalization features. 
author: JaneA07
manager: AnnBe
ms.date: 05/22/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: RCS, RCSWorkspace, e-Invoicing service
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 97423
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: leguo
ms.search.validFrom: 2020-05-01
ms.dyn365.ops.version: AX 10.0.11

---

# Regulatory Configuration Services (RCS) - Globalization feature

[!include [banner](../includes/banner.md)]

You can use Microsoft Regulatory Configuration Services (RCS) to create a Globalization feature to use in Globalization services. RCS allows you to:
-	Define related feature components 
-	Manage the feature lifecycle through a feature's status
-	Enable a Globalization feature for a defined environments 
-	Share a feature with other organizations

The following steps explain how a user in RCS can add a feature with related components, update it's status, and enable it for use in a Globalization service, like an e-Invoicing service. 
To complete these steps, you must first complete the steps related to:
-	Accessing an RCS instance
-	Creating a configuration provider that is active. For more information, see [Create configuration providers and mark them as active](../../fin-ops-core/dev-itpro/analytics/tasks/er-configuration-provider-mark-it-active-2016-11.md).

In your Dynamics 365 Finance or Operations app instance, you can take the following actions:
1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
2. If you have no RCS environment provisioned to your company, select **Regulatory services – Configuration** and follow the instructions to provision an RCS environment for your organization.

> [!NOTE]
> If an RCS environment has been provisioned to your company, use the page URL to access it by selecting the sign in option.

## Enable the Globalization features
1. Go to your instance of RCS and select the **Feature management** tile.
2. From the list, select **Globalization features** and then select **Enable now**.

![Feature management Global feature](./media/RCS_GlobalF_1%20Feature%20mgmt.JPG)

## Globalization feature
To use a Globalization feature, you need to import the feature from the RCS/Global repository and create your own version of the feature to use it. There are two ways to utilize Globalization feature, user can either:
- Add a new feature based on an existing feature that has been published or shared
- Add a new feature that you have created from scratch

## Access Globalization features
1. Navigate to **Feature management** to enable the feature.
2. Go to the new **Globalization feature workspace** and then select the **e-Invoicing** tile.

  ![Global feature workspace](./media/RCS_GlobalF_2%20Feature%20wrkspace.JPG)

The **Globalization features** page will open.

  ![Global feature form](./media/RCS_GlobalF_3%20Feature%20form.JPG)

## Add a derived feature 
1. On the **Import feature from Global repository** page.
    
 ![Global feature import](./media/RCS_GlobalF_4%20Feature%20import%20form%20GR.JPG)
 
2. Select **Synchronize** to get the latest features. 

The features that you see in the synchronized list are features that are available to you because they were published by Microsoft or because they were shared with you by another configuration provider.
  
  ![Global feature sync](./media/RCS_GlobalF_5%20Feature%20GR%20sync.JPG)
 
3. Select the features from the list that you want to import, and then select **Import**.

  ![Global feature import msg](./media/RCS_GlobalF_6%20Feature%20GR%20import%20success.JPG)  

4. Select **Add**, and then select **Based on existing version**.
5. Enter the feature name and description.
6. Select the base version of the feature from the list of available features, and then select **Create feature**.

![Global feature derived](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/janeaug_rcs_Global-feature/articles/finance/localizations/media/RCS_GlobalF_7%20Feature%20create%20derived.JPG) 

The feature you added is created with a status of **Draft**.

![Global feature create draft](./media/RCS_GlobalF_8%20Feature%20draft%20create.JPG) 

7. Review the feature components to see if updates are needed.
  - Review the configurations in case you have to customize the Electronic Reporting (ER) formats and their binding with format mappings for the feature version.
  - Review the setup in case you have to customize the **Actions set**, **Applicability rules**, or **Variables** for the feature version.

8. On the **Versions** tab, select an **Effective from** date, and if the **Description** field is empty, enter a description.
9. Select **Change status** to complete the feature. Completed features can be enabled for a specific environment so the feature can be use in Globalization services, or published to the Global repository.

> [!NOTE]
> Features with a **Feature version status** of **Published** can be shared with external organizations.

## Add a new Globalization feature 
You can add a new Globalization feature by creating the new feature from scratch.

1. On the **Import feature from Global repository** page, select **Add** > **New feature**.
2. Enter a name and description for the feature.
3. Select **Create feature**.

![Global feature create new](./media/RCS_GlobalF_9%20Feature%20create%20new.JPG) 

4. On the **Versions** tab, select an **Effective from** date and then select **Change status** to complete the feature.	Completed features can be enabled for a specific environment so the feature can be use in Globalization services, or published to the Global repository.

> [!NOTE]
> Features with a **Feature version status** of **Published** can be shared with external organizations.

## Feature components overview

Globalization feature has several components parts that cover: 
-	**Version** - Supports feature lifecycle management and allows user to manage status for different versions of the feature
-	**Configurations** - Allows user to manage, view and edit related Electronic Reporting (ER) formats and format mappings
-	**Setups** - Allows users of Globalization services, for example e-invoicing service, to manage the related Feature version set-up, supporting the flexible construction of communication and responses rules
-	**Environment** - Allows users of Globalization services, for example e-invoicing service, to manage the environment where they want to use feature setup version, as well granting authorization for the users that will have access to it
-	**Organizations** - Allows user to share feature with external organization

## Configuring feature components

### Version and status
Version manages the Globalization feature lifecycle. The status can be changed in the **Status** field on the **Version** tab. 
- The status types include:
  -	**Draft**: The feature can be edited only in this status.
  -	**Complete**: The feature and all related components are finalized and can't be edited.
  -	**Published**: The feature and all related components are published to the Global repository.
  -	**Shared**: The feature and all related components are shared with external organizations.
  -	**Enabled**: The feature and all related components are enabled for use in a Globalization service, for example e-Invoicing.
  
  > [!NOTE]
  > Some statuses are required to be moved through sequentially, so every status may not be available at every lifecycle stage.

### Configurations
  -	**View**: View the underlying feature configurations that don’t require any updating.
  -	**Edit**: Create a draft version of the selected configuration to edit the format or format mapping through the **Format designer**.
  -	**Delete**: Delete a selected configuration from the feature
  -	**Rebase**: Rebase the feature. For more information, see the [Rebasing a derived globalization feature](#rebase) section later in the topic.

### Setups
  -	**Add**: Create a new feature setup, which can be  derived from an existing feature setup or created from the scratch.
  -	**Delete**: Delete a selected feature setup.
  -	**View**: View the underlying feature setup that does not require any modifying.
  -	**Edit**: Create, delete, or modify the attributes of the three main components of a feature setup:
      - Actions and their parameters
      - Applicability rules
      - Variables
  
For more information about feature setup, see [Configuring feature set-up for e-Invoicing](../../fin-ops-core/dev-itpro/analytics/tasks/configuration-feature-set-for-einvoicing.md).
    
  ![Global feature set up](./media/RCS_GlobalF_10%20Feature%20set%20up.JPG) 
  
### Environments
 - **Enable**: For a selected feature version, choose a published environment and enable it with an **Effective from** date. For more information, see the [Configuring Environments for enablement section](#configureenvironment) later in this topic.
 -	**Cancel**: Remove an environment for a feature setup.

### Organizations
Complete the following steps to share a Globalization feature with an external organization.

1. Select the feature that you want to share and on the **Organizations** tab, select **+Share with**.
2. Enter the organization domain name, and then select **Share**.
     
   ![Global feature - Share with](./media/RCS_GlobalF_20%20Feature%20orgn_share%20with.JPG) 

The feature is shared with the selected organization and is available for them in the Global repository where it can be imported for use  into their RCS or Finance instance.


## <a name="rebase"></a>Rebasing a derived Globalization features
You can rebase a derived feature to the new or updated base feature version. This allows changes that have occurred in the base version to be automatically updated. The updated base version feature is created by the originating configuration provider, and published or shared.
 
 ![Global feature new version](./media/RCS_GlobalF_12%20Feature%20new%20version.JPG) 
 
For example, if you want to rebase the derived version of a feature you created, you want to start by getting the latest version of the feature by importing it from the Global repository.

1. On the Action Pane, select **Import**.
2. Select **Synchronize** to get latest features.
3. Select features to import from feature list, and select **Import**.

  ![Global feature new version import](./media/RCS_GlobalF_13%20Feature%20new%20version%20import.JPG) 
 
4. From the feature list, select the feature to be rebased.
5. On the **Version** tab, select **New** to create draft version.  

  ![Global feature rebase](./media/RCS_GlobalF_14%20Feature%20new%20base%20version.JPG) 

6. Select **Rebase**. 
7. In the **Rebase** dialog, select the latest version of the feature to rebase to.

  ![Global feature version](./media/RCS_GlobalF_15%20Feature%20rebase%20version.JPG) 

8. Select **OK**.
9. Review the feature components and make any changes.
10. Select **Change status** to complete the rebased feature. When the rebase is complete, you will be able to take additional actions including publishing and enabling the feature for use in the Globalization service.

  ![Global feature complete status](./media/RCS_GlobalF_16%20Feature%20rebase%20version%20complete.JPG) 

## <a name="configureenvironment"></a>Configuring environments for enablement
Users of the Globalization services can manage the environment to set up the feature and provide authorization to other users that will have access the feature.

1. Under **Environments**, select the **e-invoicing** tile.

  ![Global feature environment](./media/RCS_GlobalF_17%20Feature%20environment.JPG) 

2. Select **Key Vault parameters**, and then select **New** to create a Key vault secret. 
3. Enter a name and description for the Key vault and in the **Key Vault URI** field, enter the link that identifies the key vault resource in Azure.
4. Select **Add** to add certificate names, and provide a name and description for each certificate. 

  ![Global feature key vault](./media/RCS_GlobalF_18%20Feature%20envn%20key%20vault%20parameter.JPG) 

5. Select **New** to create a new environment and provide a name, description and the storage SAS token secret. 
6. Select **New** to add users that will have permission to access this environment.
7. Provide the user ID and email for each user that you add. 
8. Select **Publish** to publish the environment.

  ![Global feature environment publishing](./media/RCS_GlobalF_19%20Feature%20envn%20publishing.JPG) 

