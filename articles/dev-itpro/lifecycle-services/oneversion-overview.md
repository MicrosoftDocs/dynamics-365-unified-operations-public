---
# required metadata

title: One Version overview
description: This topic gives an overview of the different experiences that encompass ONE Version
author: meeram
manager: AnnBe
ms.date: 03/04/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 267184
ms.assetid: eb056816-ccf4-43a5-aed3-cf72543353de
ms.search.region: Global
# ms.search.industry: 
ms.author: manado
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# ONE Version

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/coming-soon.md)]

The set of topics below are aimed at providing the information related to **service updates for 8.1 and above** for the cloud releases.

- The release cadence and process is detailed  in the [standard and first release](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/get-started/public-preview-releases) topic.
- [Software lifecycle](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/migration-upgrade/versions-update-policy?toc=/fin-and-ops/toc.json) topic enumerates the details the service updates, availability and end of service.
- An [FAQ](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/get-started/one-version) document is available for questions in the process, tools, planning and Retail service updates.

The service update experience is composed of 4 distinct steps: **Onboard, Notice, Execute and Validate**. Each of these and related topics are enumerated below.

**Onboard**

The customer can choose the maintenance window based on business constraints using the settings as shown in the screen shot below. An upcoming calendar is available to help with planning.  New features are opt-in only and enabled by the user. All updates are applied on the user acceptance environment followed by production giving time to the customer to validate as required. The customer can select the environment to update. There is also the ability to pause the update for up-to 3 months.

 [![Queries](./media/UpdateSettings-ConfigureUpdates.JPG)](./media/UpdateSettings-ConfigureUpdates.JPG)

**Notify**

To plan ahead and understand what&#39;s changing the [release notes](https://docs.microsoft.com/en-us/business-applications-release-notes/april19/dynamics365-finance-operations/) will be available to look ahead and review the features up-to 3 months in advance.  The [what&#39;s new](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/get-started/whats-new-changed) will carry specific details about the specific month&#39;s update. An email notification will be sent 5 days in advance and a notification will popup in LCS just prior to an update as shown below.

[![Queries](./media/Notification-bar.JPG)](./media/Notification-bar.JPG)

**Execute**

Post the notification Microsoft will apply the update( **auto update** ) in the designated maintenance window. This operation will be followed by an email notification indicating the status of the update. The ability to **self-update** will also be available through LCS using the standard update experience. \&lt;add link\&gt; Opportunity to update the sandbox and other environments early is available through the **First release program** through [http://experience.dynamics.com](http://experience.dynamics.com).

[![Queries](./media/Self-Update-Execute.jpg)](./media/Self-Update-Execute.jpg)

**Validate**

Once an update is complete on the user acceptance test environment, a basic business process test validation may be completed. To support this effort, a no code automation test tool for business process testing is available\&lt;link\&gt;. Several customers have data integrations that are external and internal. It&#39;s recommended that the Data Task Automation tool\&lt;link\&gt; be used to test these scenarios.

[![Queries](./media/TestAutomation.png)](./media/TestAutomation.png)
