---
# required metadata

title: Create ER configurations in RCS and upload them to the Global repository
description: This topic explains how to create an Electronic reporting (ER) configuration in Microsoft Regulatory Configuration Services (RCS) and upload it to the Global repository.
author: JaneA07
manager: AnnBe
ms.date: 09/21/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: ERSolutionTable, ERWorkspace, RCS
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 97423
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: janeaug
ms.search.validFrom: 2020-02-01
ms.dyn365.ops.version: AX 10.0.9

---

# Create ER configurations in Regulatory Configuration Services (RCS) and upload them to the Global repository

[!include [banner](../includes/banner.md)]

You can use Microsoft Regulatory Configuration Services (RCS) to design Electronic reporting (ER) configurations and publish them so that they can be used in your organization.

The following procedures explain how a user in the System Administrator or Electronic Reporting Developer role can create a derived version of an ER configuration that has been configured in an RCS instance, and then upload the derived configuration to the Global repository. 

Before you can complete those procedures, you must complete the following prerequisites:

- Access an RCS instance.
- Create an active configuration provider. For more information, see [Create configuration providers and mark them as active](../../fin-ops-core/dev-itpro/analytics/tasks/er-configuration-provider-mark-it-active-2016-11.md).

You must also make sure that an RCS environment is provisioned for your company.

1. In a Finance and Operations app, go to **Organization administration** \> **Workspaces** \> **Electronic reporting**.
2. If no RCS environment is provisioned for your company, select **Regulatory services – Configuration external**, and then follow the instructions to provision one.

If an RCS environment has been already provisioned for your company, use the page URL to access it by selecting the sign-in option.

## Create a derived version of a configuration in RCS

1. In the **Electronic reporting** workspace, verify that you have an active configuration provider for your organization. 
2. Select **Reporting configurations**.
3. Select the configuration that you want to derive a new version from. You can use the filter field above the tree to narrow your search.
4. Select **Create configuration** \> **Derive from Name**.
5. Enter a name and description, and then select **Create configuration** to create a new derived version.
6. Select the newly derived configuration, add a description of the version, and then select **OK**. The status of the configuration to is changed to **Completed**.

![New configuration version in RCS](media/RCS_CompleteConfig.JPG)

> [!NOTE]
> When the configuration status is changed, you might receive a validation error message that is related to the connected applications. To turn off the validation, on the Action Pane on the **Configurations** tab, select **User parameters**, and then set the **Skip validation at configuration's status change and rebase** option to **Yes** 

## Upload a configuration to the Global repository

To share a new or derived configuration with your organization, you can upload it to the Global repository.

1. Select the completed version of the configuration, and then select **Upload into repository**.
2. Select the **Global (Microsoft)** option, and then select **Upload**.

    ![Upload into repository options](media/RCS_Upload_to_GlobalRepo_options.JPG)

3. In the confirmation message box, select **Yes**. 
4. Update the description of the version as required, and then select **OK**. 

The status of the configuration is updated to **Share**, and the configuration is uploaded to the Global repository. From there, you can work with it in the following ways:

- Import it into your Dynamics 365 instance. For more information, see [(ER) Import configurations from RCS](../../fin-ops-core/dev-itpro/analytics/tasks/import-configuration-rcs.md).
- Share it with a third party or an external organization, see [RCS Share Electronic reporting (ER) configurations with external organizations](rcs-global-repo-share-configuration.md)

    ![Derived Intrastat Contoso configuration version in the Global repository](media/RCS_Config_upload_GlobalRepo.JPG)

## Delete a configuration from the Global repository
Complete the following steps to delete a configuration that your organization has created.

1. In the **Electronic reporting** workspace, verify that your configuration provider is **Active**. For more information, see [Create configuration providers and mark them as active](../../fin-ops-core/dev-itpro/analytics/tasks/er-configuration-provider-mark-it-active-2016-11.md).
2. On your active configuration provider, select **repository**.
3. Select the repository type **Global**, and select **Open**.
4. On the **Filter** FastTab, find the configuration that you want to delete by using the **Filter** functionality.
5. On the **Version** FastTab, select the version of the configuration that you want to delete, and then select **Delete**:

    ![Delete configuration from global repository](media/RCS_Delete_from_GlobalRepo.JPG)

6. In the confirmation message box, select **Yes**.

    ![Delete configuration version confirmation message](media/RCS_Delete_from_GlobalRepo_Msg.JPG)
 
The configuration version is deleted, and confirmation message is shown. 

> [!NOTE]
> Configurations can only be deleted by the Configuration provider that created them. If the configuration has been shared with another organization, the configuration will need to be unshared before you delete it.
 
