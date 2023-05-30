---
title: Regulatory Configuration Services (RCS) - Globalization features
description: This article explains how to use Microsoft Regulatory Configuration Services (RCS) and the Global repository to create and use Globalization features.
author: kfend
ms.date: 06/04/2020
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2020-05-01
ms.dyn365.ops.version: AX 10.0.11
ms.assetid: 
ms.search.form: RCS, RCSWorkspace, e-Invoicing service
---

# Regulatory Configuration Services (RCS) - Globalization features

[!include [banner](../includes/banner.md)]

You can use Microsoft Regulatory Configuration Services (RCS) to create a Globalization feature that can be used in Globalization services, such as an e-invoicing service. RCS lets you perform these tasks:

- Define related components of a feature.
- Manage the feature lifecycle through a feature's status.
- Make a feature available for defined environments.
- Share a feature with other organizations.

The following procedures explain how a user in RCS can add a Globalization feature and related components, update the feature's status, and make the feature available so that it can be used in Globalization services.

Before you complete the procedures, you must complete the steps that are related to the following tasks:

- Accessing an RCS instance.
- Creating and activating a configuration provider. For more information, see [Create configuration providers and mark them as active](../../fin-ops-core/dev-itpro/analytics/tasks/er-configuration-provider-mark-it-active-2016-11.md).

In your finance and operations apps instance, follow these steps.

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**.
2. If no RCS environment is provisioned for your company, select **Regulatory services – Configuration**, and follow the instructions to provision one.

> [!NOTE]
> If an RCS environment has already been provisioned for your company, use the page URL to access the environment by selecting the sign-in option.

## Turn on the Globalization features

1. In your RCS instance, select the **Feature management** tile.
2. In the **Feature management** workspace, select **Globalization features** in the list, and then select **Enable now**.

    ![Globalization features in Feature management.](./media/RCS_GlobalF_1%20Feature%20mgmt.JPG)

## Globalization features

To use a Globalization feature, you must first import it from the the Global repository and create your own version of it. There are two ways to add Globalization features:

- Add a derived feature that is based on an existing feature that has been published or shared.
- Add a new feature that you've created from scratch.

## Access Globalization features

1. Make sure that the **Globalization features** feature is turned on in Feature management, as described earlier in this article.
2. Open the new **Globalization Features** workspace, and then, under **Features**, select the **e-Invoicing** tile.

    ![Global Features workspace.](./media/RCS_GlobalF_2%20Feature%20wrkspace.JPG)

    The **e-Invoicing Features** page is opened.

    ![e-Invoicing Features page.](./media/RCS_GlobalF_3%20Feature%20form.JPG)

## Add a derived Globalization feature

You can add a new Globalization feature by deriving it from an existing feature that has been published or shared.

1. Select **Import** to open the **Import feature from Global repository** page.

    ![Import feature from Global repository page.](./media/RCS_GlobalF_4%20Feature%20import%20form%20GR.JPG)

2. Select **Synchronize** to get the latest features.

    The synced list includes features that are available to you either because they were published by Microsoft or because they were shared with you by another configuration provider.

    ![Synced list of features.](./media/RCS_GlobalF_5%20Feature%20GR%20sync.JPG)

3. In the list, select the features to import, and then select **Import**. You receive a message when the selected features have been successfully imported.

    ![Successful import message.](./media/RCS_GlobalF_6%20Feature%20GR%20import%20success.JPG)

4. Select **Add**, and then, in the drop-down dialog box, select the **Based on existing version** option.
5. Enter a name and description for the feature.
6. In the list of available features, select the base version of the feature, and then select **Create feature**.

    ![Adding a derived feature.](./media/RCS_GlobalF_7%20Feature%20create%20derived.JPG)

    The feature that you added is created and has a status of **Draft**.

    ![Derived feature that has Draft status.](./media/RCS_GlobalF_8%20Feature%20draft%20create.JPG)

7. Review the feature components to determine whether updates are required:

    - Review the configurations, in case you need to customize the Electronic reporting (ER) formats and their binding with format mappings for the feature version.
    - Review the setup, in case you need to customize the **Actions** tab, **Applicability rules** tab, or **Variables** tab for the feature version.

8. On the **Versions** tab, select an **Effective from** date, and enter a description if the **Description** field is blank.
9. Select **Change status** to complete the feature. Completed features can be made available for a specific environment so that they can be used in Globalization services, or they can be published to the Global repository.

> [!NOTE]
> Features that have a **Feature version status** value of **Published** can be shared with external organizations.

## Add a new Globalization feature

You can add a new Globalization feature by creating it from scratch.

1. On the **Import feature from Global repository** page, select **Add**, and then, in the drop-down dialog box, select the **New feature** option.
2. Enter a name and description for the feature.
3. Select **Create feature**.

    ![Adding a new feature.](./media/RCS_GlobalF_9%20Feature%20create%20new.JPG)

4. On the **Versions** tab, select an **Effective from** date, and then select **Change status** to complete the feature. Completed features can be made available for a specific environment so that they can be used in Globalization services, or they can be published to the Global repository.

> [!NOTE]
> Features that have a **Feature version status** value of **Published** can be shared with external organizations.

## Feature component overview

Globalization features have several components:

- **Version** – This component supports feature lifecycle management and lets users manage the status for different versions of the feature.
- **Configurations** – This component lets users manage, view, and edit related ER formats and format mappings.
- **Setups** – This component lets users of Globalization services, such as an e-invoicing service, manage the setup of the related feature version. Therefore, it supports the flexible construction of communication and responses rules.
- **Environment** – This component lets users of Globalization services, such as an e-invoicing service, manage the environment where the feature version setup is used and grant authorization to the users who will have access to it.
- **Organizations** – This component lets users to share the feature with external organizations.

## Configuring feature components

### Version and status

The version is used to manage the Globalization feature lifecycle.

The status can be changed in the **Status** field on the **Version** tab. The following statuses are available:

- **Draft** – The feature can be edited only when it's in this status.
- **Complete** – The feature and all related components have been finalized (completed) and can't be edited.
- **Published** – The feature and all related components have been published to the Global repository.
- **Shared** – The feature and all related components have been shared with external organizations.
- **Enabled** – The feature and all related components have been enabled for use in a Globalization service, such as an e-invoicing service.

> [!NOTE]
> Features must move sequentially through some of these statuses. Therefore, not every status might be available at every lifecycle stage.

### Configurations

The following actions are available for configurations:

- **View** – View the underlying feature configurations that don't require any update.
- **Edit** – Create a draft version of a selected configuration so that you can edit the format or format mapping in the Format designer.
- **Delete** – Delete a selected configuration from the feature.
- **Rebase** – Rebase the feature. For more information, see the [Rebase derived Globalization features](#rebase) section later in this article.

### Setups

The following actions are available for feature setups:

- **Add** – Create a new feature setup. This feature setup can be derived from an existing feature setup or created from scratch.
- **Delete** – Delete a selected feature setup.
- **View** – View an underlying feature setup that doesn't require any changes.
- **Edit** – Create, delete, or modify the attributes of the three main components of a feature setup:

    - Actions and their parameters
    - Applicability rules
    - Variables

![Feature version setup page.](./media/RCS_GlobalF_10%20Feature%20set%20up.JPG)

### Environments

The following actions are available for environments:

- **Enable** – For a selected feature version, select a published environment, and select an **Effective from** date when it should be available. For more information, see the [Configure environments for enablement](#configureenvironment) section later in this article.
- **Cancel** – Remove an environment for a feature setup.

### Organizations

Follow these steps to share a Globalization feature with an external organization.

1. On the **e-Invoicing features** page, select the feature and the feature version to share.
2. On the **Organizations** tab, select **Share with**, and then, in the drop-down dialog box, enter the organization's domain name.
3. Select **Share**.

    ![Sharing a feature with an organization.](./media/RCS_GlobalF_20%20Feature%20orgn_share%20with.JPG)

The feature is shared with the selected organization and is available for that organization in the Global repository. From there, the feature can be imported into the organization's instance of RCS or Dynamics 365 Finance so that it can be used.

## <a name="rebase"></a>Rebase derived Globalization features

You can rebase a derived Globalization feature to the new or updated base feature version. In this way, changes that have occurred in the base version can be automatically updated. The updated base feature version is created by the originating configuration provider, and it's then published or shared.

![Updated base feature version.](./media/RCS_GlobalF_12%20Feature%20new%20version.JPG)

For example, if you want to rebase the derived version of a feature that you created, you first get the latest version of the feature by importing it from the Global repository.

1. On the **e-Invoicing features** page, select **Import**.
2. Select **Synchronize** to get the latest features.
3. In the list of features, select the features to import, and then select **Import**.

    ![Importing the latest version of a feature.](./media/RCS_GlobalF_13%20Feature%20new%20version%20import.JPG)

4. In the list of features, select the feature to rebase.
5. On the **Version** tab, select **New** to create a draft version.

    ![New draft version created.](./media/RCS_GlobalF_14%20Feature%20new%20base%20version.JPG)

6. Select **Rebase**.
7. In the **Rebase** dialog box, select the latest version of the feature to rebase to.

    ![Rebase dialog box.](./media/RCS_GlobalF_15%20Feature%20rebase%20version.JPG)

8. Select **OK**.
9. Review the feature components, and make any changes that are required.
10. Select **Change status** to complete the rebased feature. When the rebase is completed, you can perform additional actions. For example, you can publish the feature and make it available for use in Globalization services.

    ![Feature status updated to Completed.](./media/RCS_GlobalF_16%20Feature%20rebase%20version%20complete.JPG)

## <a name="configureenvironment"></a>Configure environments for Globalization features

Users of Globalization services can manage the environment to set up a Globalization feature and grant authorization to other users who will have access to it.

1. In the **Globalization Features** workspace, under **Environments**, select the **e-Invoicing** tile.

    ![Globalization Features workspace.](./media/RCS_GlobalF_17%20Feature%20environment.JPG)

2. Select **Key Vault parameters**, and then select **New** to create an Azure Key Vault secret.
3. Enter a name and description for the key vault, and then, in the **Key Vault URI** field, enter the URL that identifies the Key Vault resource in Azure.
4. On the **Certificates** FastTab, select **Add** to add the certificate, and enter a name and description for each certificate.

    ![Certificate added.](./media/RCS_GlobalF_18%20Feature%20envn%20key%20vault%20parameter.JPG)

5. Select **New** to create a new environment.
6. Enter a name, a description, and the shared access signature token secret required for the storage.
7. On the **Users** FastTab, select **New** to add a user who will have permission to access this environment.
8. Enter the user's user ID and email address.
9. Repeat steps 7 and 8 to add more users.
10. Select **Publish** to publish the environment.

    ![Published environment.](./media/RCS_GlobalF_19%20Feature%20envn%20publishing.JPG)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
