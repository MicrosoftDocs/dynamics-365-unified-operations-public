---
# required metadata

title: Configure Service Updates through Lifecycle Services
description: This topic provides information for you to configure how and when to get service updates to your environments.
author: manalidongre
manager: AnnBe
ms.date: 06/22/2017
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
ms.custom: 266824
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: manado
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Configure Service Updates through Lifecycle Services (LCS)

[!include [banner](../includes/banner.md)]

You will now be able to configure how and when you get service updates from Microsoft to your Dynamics 365 for Finance and Operations environments directly through Lifecycle Services. The ability to configure updates is only available for implementation projects and to users (customer/partner) that is assigned the **project owner** role in LCS. To modify your update settings, use the following steps:

1. Navigate to the Project Settings page in your implementation project.
2. A new tab called Update settings will be available that has the configuration options.

> [!NOTE]
> This is not available for customers that have signed up for the First release programs at this time. We are working on making this available to them.

> [!NOTE]
> These settings only apply to service updates and have no impact on the operation system level security updates applied monthly to your environments.

On this page you have the following options:

1. **Update environment** : Select an alternate sandbox environment to be updated prior to the production update. By default, the Tier 2 Standard Acceptance Test (Sandbox) environment included in the base offer is updated by Microsoft before applying the update on the Production environment. If you have purchased Tier 2 and above Sandbox add-on environments and would like a different Sandbox to be updated, then you can use this setting to change the default and select an alternate environment.

> [!IMPORTANT]
> The environment selected here will be updated 7 calendar days prior to the update cadence selected for the production environment.

1. **Production environment update cadence** : Select a recurring cadence for your Production environment updates. The Sandbox environment configured above will be updated 7 calendar days prior to the selected cadence. You can select the following:
  1. Select the cadence: You can choose whether to get updates in the first, second, third week of the month.
  2. Select one of the three time-zones: Select whether you want the Production updated in Eastern Time(UTC – 5) or Hong Kong Time(UTC + 8) or the Greenwich Mean Time(UTC + 0).
  3. Select a day of the week: Select a day in the week when you want to get the update.
  4. Select a time slot: Select a time slot when you want to get the update.

> [!NOTE]
> At this time, we only have a few options available under the day of the week and time slot drop downs. We will soon we adding additional options include weekdays for customers.

1. **View update calendar:** Once you have set the update cadence and configured the update environment, to know exactly when environment will be updated we generate an update calendar for the next six months that shows exactly when the configured sandbox and production environments will be updated. This provides you with a level of predictability on when to expect the update. Under the Production update cadence, you will see the View update calendar link.
