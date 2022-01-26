---
# required metadata

title: Complete, publish, and delpoy a Globalization feature
description: This topic provides information about the lifecycle process of Globalization features.
author: dkalyuzh
ms.date: 12/15/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.custom: 
ms.author: dkalyuzh
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Complete, publish, and delpoy a Globalization feature

[!include [banner](../includes/banner.md)]


## Electronic invoicing feature version
The electronic invoicing features are versioned. When a new version is created, the version number is automatically incremented. 

Electronic invoicing feature versions follow a lifecycle that has up to three statuses:

- **Draft** - You can edit the configuration attributes and artifacts of this feature version. For example, file format configurations.
- **Complete** - The feature version has been completed for editing and no more updates will be made to this version. You can no longer edit the feature version or any of the components.
- **Published** – The feature version has been published to the Global repository that's associated with your organization. You can no longer edit the feature version or any of the components. 

The **Effective from** date can be defined for the new version of the electronic invoicing feature as a default version that can be used or can be overwritten when the feature is deployed to the service environment.

Complete the follwoing steps to changes the status of a specific electronic invoicing feature version.

 1. On the **Versions** tab, select the version.
 2. Select **Change status** > **Complete**, if the current status is **Draft**, or **Publish** if the current status is **Completed**.
 3. Select **Yes** to confirm the request in the dialog box.

Changing the status from **Complete** to **Publish** is optional, because electronic invoicing feature version will be transformed to this status automatically when the feature version is deployed to the service environment.

You can track the status in the **Feature version status** column.

## Deploy feature versions

In RCS, use the **Deploy** command to publish an electronic invoicing feature version to the target service environment or connected application. 

1. On the **Versions** tab, select the version of the electronic invoicing feature with a status of **Completed** or **Published** that you want to deploy to the service environment or connected application.
2. Select **Deploy**, and then select one of the following options to define the target of the deployment. Ypu can select one or both targets.

   - **Connected application** – When the target of the deployment is the connected application, the configuration that's provided by the application setup is written in the Dynamics 365 Finance or Dynamics 365 Supply Chain Management instance that was previously associated with it.
   - **Service environment** – When the target of the deployment is the service environment, the electronic invoicing feature version is deployed to the service environment. Electronic invoicing is then ready to receive and process electronic documents that the Finance or Supply Chain Management applications send.

> [!NOTE]
> You will usually make changes in the parameters of the Electronic reporting feature that must be deployed to Service environment. Changes to the Connected application are rare. Deploy new versions to the Connected application only when you make changes in the corresponding parameters of your application.

To see if a specific version of the electronic invoicing feature is deployed to a particular environment, look on the **Environments** tab.

## Remove feature versions
In RCS, select **Cancel** to remove a specific electronic invoicing feature version from a service environment, if it was deployed there. 

> [!IMPORTANT]
> **Cancel** only works in service environments. It doesn't remove anything from the connected application for the current electronic invoicing feature.


## Rebase electronic invoicing features
When one electronic invoicing feature is derived from another, selecting **Rebase** updates the derived feature with the changes that have been introduced in the original (parent) feature. To rebase the derived version of a feature that you created, complete the following steps. 

 1. Get the latest version of the feature by importing it from the Global repository. For more information, see [Import feature from Global repository](e-invoicing-import-feature-global-repository.md).
 2. In the list of features, select the feature to rebase.
 3. On the **Version** tab, select **New** to create a draft version.
 4. Select **Rebase**, and in the **Rebase** dialog box, select the version of the feature to rebase to.
 5. Select **OK**.
 6. Review the feature components, and make any necessary changes.
 7. Select **Change status** to complete the rebased feature. When the rebase is complete, you can perform additional actions.
	

## Get specific versions of electronic invoicing features
When you create a new version of an electronic invoicing feature, the system creates a copy of the latest feature version. To take one of the earlier versions of the feature as a base for the new version, select the version, and then select **Get this version command**. A new draft version of the feature will be the copy of the selected version.
