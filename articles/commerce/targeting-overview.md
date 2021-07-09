---
# required metadata

title: Device, market, and geolocation targeting
description: This topic describes how to create, edit, and manage audiences and target variations in Microsoft Dynamics 365 Commerce site builder using device, market, and geolocation information.
author:  sushma-rao 
ms.date: 07/31/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: sushmar
ms.search.validFrom: 2021-07-31
ms.dyn365.ops.version: AX 10.0.21
---

# Device, market, and geolocation targeting

[!include [banner](includes/banner.md)]

This topic describes how to create, edit, and manage audiences and target variations in Microsoft Dynamics 365 Commerce site builder using device, market, and geolocation information. 

Dynamics 365 Commerce enables you to target specific groups of customers with different page content based on their device information, geolocation data, and other dynamically derived attributes from browser requests. Basic segmentation and targeting based on information available in a site user's browser is enabled for e-commerce modules and fragments within a page. This helps personalize content in near real-time for these target groups known as *audiences* and drives increased user engagement and satisfaction.

You can create and manage audiences in Commerce site builder based on customer data such as location, device information, sign-in status, and other information gathered from customer web requests. You can then prepare special variations of your content for members of these audiences. Such variations are called **targets** and are also authored and managed in site builder.

You can begin your targeting journey by first creating either an audience or a target, but both are necessary parts of a successful targeting experience.

> [!NOTE]
> Targeting relies on site user cookie consent. If site users opt out of allowing site cookies, they will not be shown any targeted content. For more information on cookie compliance, see [Cookie compliance](cookie-compliance.md).

## Audiences

An audience is a group of users whose membership is determined by a set of dynamic rules. These rules are simple AND/OR conditions run against basic information or segments available in customer requests. Commerce natively supports segments such as device information (desktop/mobile/tablet, OS, browser), sign-in status, referrer, and query string parameters. Additionally, Commerce also supports connecting to third-party geolocation and segmentation providers. For example, you can purchase a third-party connector from [AppSource](https://appsource.microsoft.com) and then simply follow the setup instructions provided by the publisher. Alternatively, you can use sample test connectors from Commerce to test without needing to configure an external service. For more information on setting up test connectors, see [Configure and enable connectors](e-commerce-extensibility/connectors.md). 

**Disclaimer:** By enabling this feature, your data will be shared with third-party systems that you select. You control what data, if any, that you provide to the third-party. You understand that the data handling and compliance standards of the third-party may not be the same as Microsoft Dynamics 365 Commerce. Your privacy is important to us. To learn more read our [Privacy and Cookies notice](https://privacy.microsoft.com/en-us/privacystatement).

To create an audience in Commerce site builder, follow these steps.

1. Select **Audiences** in the left navigation pane, and then select **New**.
1. Enter a name for the audience. You can also optionally add tags and a description. 
1. Select **Create** and **Add new rule block** on the following page. A rule block is a collection of rules joined together by AND conditions. You can also create multiple rule blocks with OR conditions between them.
1. Select a data source for your segments, followed by the segment name, operator, and value(s). You can create and delete more rules within a rule block or create and delete entire rule blocks. You can also move rule blocks up or down as needed.
    > [!NOTE]
    > - You can have up to 100 values in a list, and each list item can contain up to 50 characters.
    > - Ensure that your use of cookies complies with applicable laws.
1. Once you are satisfied with your audience, select **Finish editing**. You can then also select **Publish** if you want to make the audience available for use in a live target, or you can publish it along with the target.

You can edit an audience by selecting its blue link on the **Audiences** tab and then selecting **Edit** in the audience editor that opens up. You can also select an audience in list view and then select **View Assignments** to view the list of targets and pages that are referencing it. To delete an audience in the audience list view or in the audience editor, unpublish it if it is already published and then select **Delete** in the command bar.

> [!NOTE]
> Audiences are a site-level concept in site builder. You can share the same audience across multiple targets.

## Targets

A target is the user experience that is shown to members of a chosen audience(s). It can include variations of one or more modules within a page or fragment. You can specify a schedule for your target to indicate how long it remains active. Note that this is a separate action from scheduling a publish group that determines when a collection of content will be published. You can also preview your target to see what it will look like to members of selected audiences. Additionally, you can prioritize your targets to indicate which target should be shown in case of a conflict.

### Create a target

To create a target shell for page modules in Commerce site builder, follow these steps.

1. Select **Pages** in the left navigation pane, and then select the blue link for the page that has the module(s) you want to target.
1. Select **Edit** to check out the page for editing.
1. Select **New target** from the **Target** drop-down menu to create a new target shell. You can create multiple targets on a page if needed. 
1. Enter names for your target and description, and then select **Next**.
1. Select **Add** to include or exclude audiences that will see this targeted experience, and then select **Next**. 
    > [!NOTE]
    > Assigning audiences is an optional step for target creation, but you will need to include at least one audience before publishing the target to ensure that the intended groups of users see it.
1. Select the time zone and start/end dates and times to display your target. You can also set the target to show at all times during this window or choose specific days and times. When done, select **Next**. 
    > [!NOTE]
    > The times and time zone you specify are global. If you wish to target different locations at different times or time zones, you will need to create different targets with the desired schedule for each location.
1. Review the details and once everything looks good, select **Create target experience** and **Go to target**. This creates the target shell to which you can now add modules. 
1. Select the module to be targeted, select the ellipsis (...), and then select **Add to current target**. When you target a parent module, all of its children become part of that target. The targeted modules are highlighted with a green color.
1. Make the necessary content updates to the targeted module and add more modules to the target as needed. Select **Save** to save all your changes.
1. Before you publish your target, make sure to select **Preview** in the command bar to review it first. You can then select from one of the following options:
    - **Basic preview** to preview only the selected variation (default page or target) without any associated audiences.
    - **Advanced preview** if you have multiple targets on this page and want to preview them as a user belonging to a selected set of audiences. Select **Next** to choose from the list of relevant audiences or remove the filter to choose from all audiences.
1. When you are satisfied with the target configuration, you will need to publish the page for the target to go live. Select **Publish** to go live immediately or use a publish group to schedule when the page goes live.

You can also target fragments in a similar way from the **Fragments** tab in the left navigation pane.

> [!NOTE]
> To avoid any negative impact to your metrics, you can have either an experiment or targets on a page or fragment, but not both.

### Manage targets

To manage your targets, go to the default page or fragment and follow these steps.

1. Select **Target** from the drop-down menu and then select **Manage targets**.
1. Select a target to edit, duplicate, or delete.
1. If you have multiple targets on the same module or multiple targets with conflicting schedules, select **Prioritize targets** to specify the order in which they should be shown. This button will also appear in the notifications bar when you add more than one target on a page or fragment as a reminder to prioritize if necessary. If no priority is specified, the most recent target will be selected by default.

### Localize targets

Targets in pages and fragments will be included automatically when exporting and importing XLIFF files for localization. If this is not desirable, you can delete the targets for unneeded locales once the localized XLIFF files are imported. 

> [!NOTE]
> Targets are managed per channel and locale. Any changes you make to targets in one channel or locale will not automatically carry forward to other channels or locales.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
