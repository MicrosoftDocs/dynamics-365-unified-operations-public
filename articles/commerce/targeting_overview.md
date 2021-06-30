---
# required metadata

title: E-commerce Segmentation and Targeting
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

# Customer segmentation and targeting in Dynamics 365 Commerce
Dynamics 365 Commerce enables you to target specific groups of customers with different page content based on their device information, geolocation, and other dynamically derived attributes from their browser request. This will help personalize content in near real-time for these target groups known as **audiences** and drive increased user engagement and satisfaction.

You can create and manage audiences in site builder based on customer data such as location, device information, sign-in status, referrer, or query string parameters, gathered from the customer's web request. These audiences can then be targeted with module or fragment variations called **targets**, also authored and managed in site builder.

## Audiences
An audience is a group of users whose membership is determined by a set of dynamic rules. These rules are simple AND or OR conditions against basic information or segments available in the customer's request. Commerce natively supports segments such as device info (desktop/mobile/tablet, OS, browser), sign-in status, referrer and query string parameters. Additionally, Commerce also supports connecting to third-party geolocation and segmentation providers. For more information on setting up a geolocation connector, see [GeoLookup connector](e-commerce-extensibility/connectors.md#geolookup-connector).

To create an audience in Commerce site builder, follow these steps.
1. Select **Audiences** in the left navigation pane, and then select **New**.
2. Give your audience a name and optionally add tags and a description. 
3. Click on **Create** and **Add new rule block** on the the following page. A rule block is a collection of rules joined together by AND conditions. You can also create multiple rule blocks with OR conditions between them.
4. Select a data source for your segments, followed by the segment name, operator and value(s). You can create and delete more rules within a rule block or create and delete entire rule blocks. You can also move rule blocks up or down as needed.
    > [!NOTE]
    > You can have up to 100 values in a list with up to 50 characters in each item.
6. Once you are satisfied with your audience, select **Finish editing**. You can also select **Publish** if you want to make the audience available for use in a live target or publish it along with the target.

You can edit an audience by clicking on it's blue link in the **Audiences** tab and the **Edit** button in the audience editor that opens up. You can also select an audience in the list view and select **View Assignments** to view the list of targets, experiments and pages that are referencing it. To delete an audience in the audience list view or in the audience editor, select **Delete** in the top command bar.

## Targets
A target is the user experience that will be shown to members of the chosen audience. You can target modules in the **Pages** tab or fragments in the **Fragments** tab.

### Create a target
To target page modules in Commerce site builder, follow these steps.
1. Select **Pages** in the left navigation pane, and then select the blue link for the page that has the module(s) you want to target.
2. Click **Edit** to check out the page for editing.
3. Click the **Default** drop-down and then **New target** to create a new target shell.
4. Give your target a name and description and click **Next**.
5. Click **Add** to include or exclude audiences that will see this targeted experience and click **Next**. 
    > [!NOTE]
    > Assigning audiences is an optional step for target creation but you will need to assign audiences before publishing the target to ensure the right groups of users see it.
6. Select time zone, start and end dates/times to display your target. You can also set the target to show at all times during this window or choose specific days and times and click **Next**.
7. Review the details and once everything looks good, click **Create target experience** and **Go to target**. This creates the target shell to which you can now add modules. 
8. Select the module to be targeted, select the ellipsis (...), and then select **Add to current target**. The targeted module will be highlighted with a green color.
9. Make the necessary updates to the targeted module and add more modules if required. Click **Save** to save all your changes.
10. To preview the target as a member of an audience and on a particular day, click on **Preview** in the command bar, select **Advanced preview** and click **Next**. You can either choose from the list of relevent audiences shown here or remove the filter to choose from all audiences. 
11. Once everything looks good, click on **Publish** to publish your target immediately or include within a publish group to schedule when it goes live.

You can also target fragments in a similar way from the **Fragments** tab in the left navigation pane.

> [!NOTE]
> You can currently either have an experiment or target on a page but not both.

### Manage targets
To manage your targets, go to the default page or fragment and follow these steps.
1. Open the targets dropdown and click on **Manage targets**.
2. Click on a target to edit, duplicate or delete it.
3. If you have more than one target on the same module, click on **Prioritize targets** to specify the order in which they should be shown.

### Localize targets
Targets in pages and fragments will be automatically included when exporting and importing XLIFFs for localization. If this is not desirable, delete the targets before the localization progress. If you need to create different schedules per locale, you will need to create different targets per each locale.

<<Open - C1 needs explicit cookie consent from C2; need to include info on that module>>

[!INCLUDE[footer-include](../includes/footer-banner.md)]
