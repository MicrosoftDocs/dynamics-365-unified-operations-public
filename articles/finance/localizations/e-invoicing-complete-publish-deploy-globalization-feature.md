---
# required metadata

title: Complete, publish and delpoy Globalization feature
description: This topic provides description of the process of lifecycle of Globalization features
author: dkalyuzh
ms.date: 12/15/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
---

# Complete, publish and delpoy Globalization feature

[!include [banner](../includes/banner.md)]


## Electronic invoicing feature version
The electronic invoicing features are versioned. When a new version is created, the version number is automatically incremented. 

Electronic invoicing feature versions follow a lifecycle that has up to three statuses:
- Draft – If a feature version is in this status, you can edit its configuration attributes and any of its artifacts (for example, file format configurations).
- Complete – If a feature version is in this status, it has been completed for editing that means that you are not going to change this version anymore. You can no longer edit the feature version or any of the components.
- Published – If a feature version is in this status, it has been published to the Global repository that is associated with your organization. You can no longer edit the feature version or any of the components. 

**Effective from** date can be defined for the new version of the electronic invoicing feature as a default versions that can be used or be overwritten during deploying the feature to service environment.

To changes the status of the particular electronic invoicing feature version:
 1. Select the version in **Versions** tab.
 2. Select **Change status** > **Complete** (if the current status is Draft), or **Publish** (if the current status is Completed).
 3. Confirm the request in the popup dialog with selecting **Yes**.

Changing the status from Complete to Publish is optional, as electronic invoicing feature version will be transformed to this status during Deploying the feature version to the service environment automatically.

You can track the status in the **Feature version status** column.

## Deploy feature versions
In RCS, you use the **Deploy** command to publish an electronic invoicing feature version to the target service environment or connected application. 
 1. In **Versions** tab select the version of electronic invoicing feature in status Completed or Published that you want to deploy to the service environment and/or connected application.
 2. Select **Deploy**, and then select one of the following options to define the target of the deployment (one target or both at once):
  - **Connected application** – When the target of the deployment is the connected application, the configuration that is provided by the application setup is written in the Finance and Supply Chain Management instance that was previously associated with it.
  - **Service environment** – When the target of the deployment is the service environment, the electronic invoicing feature version is deployed to the service environment. Electronic invoicing is then ready to receive and process electronic documents that Finance and Supply Chain Management applications send.

> [!NOTE]
> Usually, you will do changes in the parameters of Electronic reporting feature that must be deployed to Service environment, and changes of the Connected application are rare. You should deploy new versions to Connected application only when you do changes in the corresponding parameters of your application.

To check if particular version of the electronic invoicing feature is deployed to particular environment, you can review Environments tab.
![complete-2](https://user-images.githubusercontent.com/78973132/146524914-2c088417-28ba-4bc5-9593-e1c96cd77960.jpg)


## Remove feature versions
In RCS, you use the **Cancel** command to remove a specific electronic invoicing feature version from a service environment, if it was deployed there. 

> [!IMPORTANT]
> The Cancel command works only in service environments. It doesn't remove and setup from the connected application for the current electronic invoicing feature.


## Rebase electronic invoicing features
When one electronic invoicing feature is derived from another, the **Rebase** command updates the derived feature with the changes that have been introduced in the original (parent) feature.
If you want to rebase the derived version of a feature that you created, follow the steps:
 1. You first get the latest version of the feature by importing it from the Global repository ([Import feature from Global repo](e-inv_tut-setup-electronic-invoicing_global-feature_import.md)).
 2. In the list of features, select the feature to rebase.
 3. On the **Version** tab, select **New** to create a draft version.
 4. Select **Rebase** for this Draft version.
 5. In the **Rebase** dialog box, select the version of the feature to rebase to.
 6. Select **OK**.
 7. Review the feature components, and make any changes that are required.
 8. Select **Change status** to complete the rebased feature. When the rebase is completed, you can perform additional actions described above.
	

## Get particular version of electronic invoicing features
When you create a new version of the electronic invoicing feature, the system creates a copy of the latest version of the feature version. If you need to take one of the earlier versions of the feature as a base for the new version, you should select this version, and select **Get this version command**. New draft version of the feature will be the copy of the selected version.
