---
# required metadata

title: Device, market, and GEO IP targeting
description: This topic describes how to create, edit and manage audiences and target variations in site builder. Basic segmentation and targeting based on information available in the user's browser such as device type or location is enabled for e-commerce modules and fragments within a page.
author:  sushma-rao 
ms.date: 7/31/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: sushmar
ms.search.validFrom: 2021-07-31
ms.dyn365.ops.version: AX 10.0.21
---

# Device, market, and Geo IP targeting
Dynamics 365 Commerce enables you to target specific groups of customers with different page content based on their device information, geolocation, and other dynamically derived attributes from their browser request. This will help you personalize content in near real-time for these target groups known as **audiences** and drive increased user engagement and satisfaction.

You can create and manage audiences in site builder based on customer data such as location, device information, sign-in status, and other information gathered from the customer's web request. You can prepare special variations of your content for members of these audiences. These variations called **targets** are also authored and managed in site builder.

## Audiences
An audience is a group of users whose membership is determined by a set of dynamic rules. These rules are simple AND or OR conditions against basic information or segments available in the customer's request. Commerce natively supports segments such as device info (desktop/mobile/tablet, OS, browser), sign-in status, referrer and query string parameters. Additionally, Commerce also supports connecting to third-party geolocation and segmentation providers. You can purchase a third-party connector from [AppSource](https://appsource.microsoft.com) and follow the setup instructions provided by the publisher. You can alternatively use sample test connectors from Commerce to test without needing to configure an external service. For more information on setting up test connectors, see [Configure and enable connectors](e-commerce-extensibility/connectors.md). 

**Disclaimer:** By enabling this feature, your data will be shared with third-party systems that you select. You control what data, if any, that you provide to the third-party. You understand that the data handling and compliance standards of the third-party may not be the same as Microsoft Dynamics 365 Commerce. Your privacy is important to us. To learn more read our [Privacy and Cookies notice](https://privacy.microsoft.com/en-us/privacystatement).

To create an audience in Commerce site builder, follow these steps.
1. Select **Audiences** in the left navigation pane, and then select **New**.
2. Give your audience a name and optionally add tags and a description. 
3. Click on **Create** and **Add new rule block** on the the following page. A rule block is a collection of rules joined together by AND conditions. You can also create multiple rule blocks with OR conditions between them.
4. Select a data source for your segments, followed by the segment name, operator and value(s). You can create and delete more rules within a rule block or create and delete entire rule blocks. You can also move rule blocks up or down as needed.
    > [!NOTE]
    > You can have up to 100 values in a list with up to 50 characters in each item.
    > Please ensure that your use of cookies complies with applicable laws.
6. Once you are satisfied with your audience, select **Finish editing**. You can also select **Publish** if you want to make the audience available for use in a live target or publish it along with the target.

You can edit an audience by clicking on it's blue link in the **Audiences** tab and the **Edit** button in the audience editor that opens up. You can also select an audience in the list view and select **View Assignments** to view the list of targets and pages that are referencing it. To delete an audience in the audience list view or in the audience editor, unpublish it if it is already published and then select **Delete** in the top command bar.

> [!NOTE]
> Audiences are a site-level concept in site builder.

## Targets
A target is the user experience that will be shown to members of the chosen audience. It can either include variations of one or more modules within a page or a fragment. You can begin your targeting journey by creating an audience or a target but both are necessary parts to a successful targeting experience.

### Create a target
To target page modules in Commerce site builder, follow these steps.
1. Select **Pages** in the left navigation pane, and then select the blue link for the page that has the module(s) you want to target.
2. Click **Edit** to check out the page for editing.
3. Click the **Target** drop-down and then **New target** to create a new target shell. <TODO: check with Jane on command bar entry point>
4. Give your target a name and description and click **Next**.
5. Click **Add** to include or exclude audiences that will see this targeted experience and click **Next**. 
    > [!NOTE]
    > Assigning audiences is an optional step for target creation but you will need to include at least one audience before publishing the target to ensure the right groups of users see it.
6. Select the time zone, start and end dates/times to display your target. You can also set the target to show at all times during this window or choose specific days and times and click **Next**. 
    > [!NOTE]
    > The times and timezone you specify are global. If you wish to target different locations at different times/zones, you will need to create different targets with the desired schedule for each location.
    > Scheduling a target dictates for how long it remains active. This is separate from scheduling a publish group that determines when a collection of content will go live.
8. Review the details and once everything looks good, click **Create target experience** and **Go to target**. This creates the target shell to which you can now add modules. 
9. Select the module to be targeted, select the ellipsis (...), and then select **Add to current target**. When you target a parent module, all its children become part of that target. The targeted modules are highlighted with a green color.
10. Make the necessary updates to the targeted module and add more modules if required. Click **Save** to save all your changes.
11. Before you publish your target, make sure to click on **Preview** in the command bar to review it first. You can then select from one of the following options:
    - **Basic preview** to preview only the selected variation (default page or target) without any associated audiences.
    - **Advanced preview** if you have multiple targets on this page and want to preview them as a user belonging to a selected set of audiences. Click **Next** to choose from the list of relevent audiences or remove the filter to choose from all audiences.
12. Once everything looks good, you will need to publish the page for the target to go live. Click on **Publish** to go live immediately or use a publish group to schedule when it goes live.

You can also target fragments in a similar way from the **Fragments** tab in the left navigation pane.

> [!NOTE]
> You can currently either have an experiment or target on a page but not both.

### Manage targets
To manage your targets, go to the default page or fragment and follow these steps.
1. Open the targets dropdown and click on **Manage targets**.
2. Click on a target to **edit**, **duplicate** or **delete** it.
3. If you have more than one target on the same module, click on **Prioritize targets** to specify the order in which they should be shown. You will also see this button show up in the notifications bar whenever there is an unresolved conflict. If no priority is specified, the newest target will be picked by default.

### Localize targets
Targets in pages and fragments will be automatically included when exporting and importing XLIFFs for localization. If this is not desirable, you can delete the targets for locales that you don't need once the localized XLIFFs are imported. Targets are managed per channel and locale so any changes you make to targets in one channel/locale will not be automatically applied to the rest.

<<TODO - C1 needs to get explicit cookie consent from C2 for targeting; need to include info on that module>>
<<Analytics??>>

[!INCLUDE[footer-include](../includes/footer-banner.md)]
