---
# required metadata

title: One Version service updates overview
description: This article gives an overview of the various steps that make up the experience for managing service updates initiated by Microsoft as part of One Version.
author: angelmarshall
ms.date: 03/02/2023
ms.topic: overview
ms.prod: 
ms.technology: 
ms.custom: bap-template
# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 

ms.search.region: Global
# ms.search.industry: 
ms.author: tsmarsha
ms.search.validFrom: 2019-3-31 
ms.dyn365.ops.version: Platform update 24 

---

# One Version service updates overview

[!include [banner](../includes/banner.md)]

The following set of topics provide information that is related to service updates for Microsoft Dynamics 365 for Finance and Operations version 8.1 (October 2018) and later. This is applicable for cloud releases only.

- [Service update availability](../../fin-ops/get-started/public-preview-releases.md) – This article provides information about the release cadence and release process.
- [Software lifecycle policy and cloud releases](../migration-upgrade/versions-update-policy.md) – This article provides information about the service updates, availability, and end of service.
- [One Version service updates FAQ](../../fin-ops/get-started/one-version.md) – This article answers questions about the update process, tools, planning, and Retail service updates.

The experience for service updates consists of four distinct steps: 

1. Configure
2. Notice
3. Update
4. Validate

The rest of this article describes each step and provides links to related topics.

## Configure

Customers can select a maintenance window, based on their business constraints. In Microsoft Dynamics Lifecycle Services (LCS), use the fields in the **Production environment update cadence** section on the **Update settings** tab of the **Project settings** page, as shown in the following image. A calendar of upcoming updates is available to help you plan ahead.

[![Update settings tab on the Project settings page.](./media/UpdateSettings-ConfigureUpdates.JPG)](./media/UpdateSettings-ConfigureUpdates.JPG)

Users must opt in to new features and turn them on. All updates are applied first to the user acceptance testing (UAT) environment and then to the production environment. Therefore, customers have time to do any validation that is required. Customers can select the environment that is updated. They can also pause an update for up to three months.

## Notice

[Release plans](/business-applications-release-notes/april19/dynamics365-finance-operations/) will be available to help you plan ahead and understand what is changing. You can learn about upcoming features up to three months in advance. The [What's new](../../fin-ops/get-started/whats-new-changed.md) topics provide details about the updates for specific months.

Additionally, a notification email will be sent five days in advance, and a notification will appear in LCS just before an update, as shown in the following illustration.

[![Upcoming updates notification in LCS.](./media/Notification-bar.png)](./media/Notification-bar.png)

## Update

After notifications have been sent, Microsoft will apply the update (**auto update**) during the designated maintenance window. After this operation is completed, a notification email will be sent to indicate the status of the update. Customers will also be able to **self-update** by using the standard update experience in LCS. For more information, see [Apply updates to cloud environments](../deployment/apply-deployable-package-system.md). 

Customers who participate in the First release program will have an opportunity to update their sandbox environment and other environments before general availability. To sign up for the First release program, go to [https://aka.ms/FirstReleaseFnO](https://aka.ms/FirstReleaseFnO).

Customers will also be able to **self-update** by using the standard update experience in LCS, as shown in the following illustration.

[![Apply updates command on the Maintain menu in LCS.](./media/Self-Update-Execute.jpg)](./media/Self-Update-Execute.jpg)

## Validate

After an update is completed in the UAT environment, a basic business process test can be executed to validate the environment. To support this effort, a no-code automation test tool for business process testing is available, as shown in the following illustration. For more information, see [Create and automate user acceptance tests](using-task-guides-and-bpm-to-create-user-acceptance-tests.md). 

[![Regression Suite Automation Tool.](./media/TestAutomation.png)](./media/TestAutomation.png)

Some customers have both external data integrations and internal data integrations. We recommend that these customers use the [Data task automation tool](../data-entities/data-task-automation.md) for testing.




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

