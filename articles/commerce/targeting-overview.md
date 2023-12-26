---
title: Device, market, and geolocation targeting
description: This article describes how to create, edit, and manage audiences and targets in Microsoft Dynamics 365 Commerce site builder by using device, market, and geolocation information.
author: sushma-rao
ms.date: 03/03/2023
ms.topic: overview
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: v-chgriffin
ms.search.region: global
ms.author: sushmar
ms.search.validFrom: 2021-07-31
ms.dyn365.ops.version: AX 10.0.21
ms.custom: 
ms.assetid: 
ms.search.industry: Retail
---

# Device, market, and geolocation targeting

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This article describes how to create, edit, and manage audiences and targets in Microsoft Dynamics 365 Commerce site builder by using device, market, and geolocation information.

Dynamics 365 Commerce lets you personalize variations of your page content (known as *targets*) for specific groups of customers (known as *audiences*) to help increase user engagement and satisfaction. You can create either an audience or a target first. However, a successful targeting experience requires both these components.

You create and manage audiences in Commerce site builder, based on customer data such as location, device information, sign-in status, and other dynamically derived information from customer web requests. You also create and manage targets on e-commerce modules and fragments in Commerce site builder.

**Disclaimer:** You're responsible for using this feature in compliance with all applicable laws and regulations, including those that are related to targeting and profiling. 

## Audiences

An audience is a group of users, and membership in the group is determined by a set of dynamic rules. These rules are simple logic tests that are run against information that is available in customer requests or other available segments. You can combine multiple rules by using AND/OR operators.

Commerce natively supports basic segments such as device information, sign-in status, referrer, and query string parameters. It also supports extensible segments through connections to third-party providers.

### Basic segments

By default, the following segments are available and can be included in audience definitions:

- **Signed-in status** – Test whether a user is authenticated.
- **Device platform** – Test for the following device types:

    - Mobile
    - Desktop
    - Tablet
    - Other

- **Device OS** – Test for the following operating systems:

    - Windows
    - Linux
    - iOS
    - Android, Other

- **Query string parameters** – Test for the existence of a key-value pair in a query string parameter of a request URL. For example, for the URL `www.fabrikam.com/en-us/request?promo=true`, a rule can be written to test that the **promo** parameter has the value **true**.
- **Cookie** – Test for a cookie value that is set for the domain in the request URL. For example, a Fabrikam.com request might include a cookie that has the name **CustomLayout** and the value **1**. The cookie test checks for the existence of a cookie but doesn't explicitly create one. In the previous example, JavaScript must have previously set the **CustomLayout** cookie from another module or some other business process.

    > [!NOTE]
    > Make sure that your use of cookies complies with applicable laws.

- **Referrer** – If a user follows a link to request the page, the referrer is the URL of the page that hosted the link.

### Extensible segments

Commerce lets you expand the list of available segments by connecting to third-party segmentation providers. A segmentation provider will describe the types of segments that are available. For more information about how to connect to a geolocation or segmentation provider, see [Configure and enable connectors](e-commerce-extensibility/connectors.md).

If an external provider is enabled, it might connect to a service that has unpredictable performance. To help ensure a better user experience, requests for targeted pages with external provider lookups aren't resolved on the initial page request. The default version of the page is shown on the first request and the targeted version only on subsequent requests. To override this default behavior for external geolocation providers, file a support ticket with [Microsoft Support](https://support.microsoft.com/). 

> [!NOTE]
> To avoid unpredictable site performance, thoroughly test the performance of the external geolocation provider and ensure that there are no significant page load time delays before contacting Microsoft.

To view targeted pages that reference external segments, a user must consent to allow cookies. The user's browser then requests all segments from relevant providers, and the results are put into a cookie that is returned to the user. Subsequent requests to the page will use this information to serve targeted content to the user. For more information about cookie compliance, see [Cookie compliance](cookie-compliance.md).

**Disclaimer:** If you enable this feature, your data will be shared with third-party systems that you select. You control what data, if any, you provide to the third party. You understand that the data handling and compliance standards of the third party might differ from the standards of Microsoft Dynamics 365 Commerce. Your privacy is important to Microsoft. To learn more, read our [Privacy and Cookies notice](https://privacy.microsoft.com/privacystatement).

### Create an audience in site builder

To create an audience in Commerce site builder, follow these steps.

1. In the left navigation pane, select **Audiences**.
1. Select **New**.
1. Enter a name for the audience. You can also optionally add tags and a description.
1. Select **Create** and then **Add new rule block**. A rule block is a collection of rules that are joined by AND conditions. You can also create multiple rule blocks that have OR conditions between them.
1. Select a data source for your segments, and then specify the segment name, operator, and values. You can create and delete more rules in a rule block, or you can create and delete entire rule blocks. You can also move rule blocks up or down as you require.

    > [!NOTE]
    > You can have up to 100 values in a list, and each list item can contain up to 50 characters.

1. When you're satisfied with the audience configuration, select **Finish editing**. You can then select **Publish** to make the audience available for use in a live target. Alternatively, you can publish the audience together with the target. 

To edit an audience, select the hyperlink for it on the **Audiences** tab, and then select **Edit** in the audience editor that appears. To view the list of targets and pages that reference an audience, select the audience in the audience list view, and then select **View Assignments**. To delete an audience in the audience list view or the audience editor, unpublish it if it has already been published, and then select **Delete** on the command bar.

> [!NOTE]
> Audiences are a site-level concept in Commerce site builder. You can share the same audience across multiple targets.

### Rename an audience in site builder

To rename an existing audience in Commerce site builder, follow these steps.

1. In the left navigation pane, select **Audiences**.
1. Select the name of the audience segment that you want to rename.
1. Select **Edit** to start editing the audience.
1. In the audience properties pane, select the pen symbol next to the audience name.
1. Edit the audience name as needed.
1. Select the check mark to confirm the name change.
1. Select **Finish editing**.

## Targets

A target is the user experience that is shown to members of one or more selected audiences. It can include variations of one or more modules on a page or in a fragment. 

You can define a schedule for your targets to specify how long they should remain active. Note that this action is separate from the action of scheduling a publish group that determines when a collection of content will be published. You can also preview your targets to see what they'll look like to members of selected audiences. Additionally, you can prioritize your targets to specify which target should be shown in the event of a conflict.

### Create a target

To create a target shell for page modules in Commerce site builder, follow these steps.

1. In the left navigation pane, select **Pages**. Then select the hyperlink for the page that has the modules that you want to target.
1. Select **Edit** to check out the page for editing.
1. On the **Target** menu, select **New target** to create a new target shell. You can create multiple targets on a page as you require.
1. Enter a name and description for your target, and then select **Next**.
1. Select **Add** to include the audiences that will see the targeted content, or to exclude audiences. Then select **Next**.

    > [!NOTE]
    > Audience assignment is an optional step during target creation. However, before you publish the target, you must include at least one audience to ensure that the intended groups of users will see the targeted content.

1. Define the time window for the display of your target by selecting the time zone, and the start and end dates and times. You can set the target so that it's shown at all times during the window, or you can select specific days and times. When you've finished, select **Next**.

    > [!NOTE]
    > The times and time zone that you specify are global. If you want to target different locations at different times or in different time zones, you must create different targets and define the desired schedule for each location.

1. Review the details, and when everything looks correct, select **Create target experience** and then **Go to target**. The target shell is created. You can now add modules to it.
1. Select the module to target, select the ellipsis (**...**), and then select **Add to current target**. When you target a parent module, all its children become part of that target. The targeted modules are highlighted in green.
1. Make the necessary content updates to the targeted module, and add more modules to the target as you require. Then select **Save** to save all your changes.
1. Before you publish your target, be sure to select **Preview** on the command bar to review it. You can then select one of the following options:

    - **Basic preview** – Select this option to preview only the selected variation (default page or target), without any associated audiences.
    - **Advanced preview** – Select this option if you have multiple targets on a page and want to preview them as a user who belongs to a selected set of audiences, or on a specific date/time. Select **Next** to select from a list of relevant audiences. You can also remove the filter to select among all audiences.

1. When you're satisfied with the target configuration, you must publish the page to make the target go live. Select **Publish** to make the target go live immediately. Alternatively, you can use a publish group to schedule when the page goes live. For information about publish groups, see [Work with publish groups](publish-groups.md).

You can also target fragments. The procedure is similar. However, in step 1, you select **Fragments** instead of **Pages** in the left navigation pane.

> [!NOTE]
> To avoid any negative impact on your metrics, you can have either an experiment or targets on a page or in a fragment. You can't have both an experiment and targets.

### Manage targets

To edit, duplicate, or delete targets, go to the default page or fragment, and follow these steps.

1. On the drop-down menu, select **Target**, and then select **Manage targets**.
1. Select a target to edit, duplicate, or delete.
1. If you have multiple targets in the same module, or if multiple targets have conflicting schedules, select **Prioritize targets** to specify the order that they should be shown in. If you add more than one target on a page or in a fragment, the **Prioritize targets** button also appears in the notification bar to remind you to prioritize the targets. If no priority is specified, the most recent target is selected by default.

### Localize targets

Targets on pages and in fragments are automatically included when XLIFF files are exported and imported for localization purposes. However, if any locales aren't required, you can delete the targets for them after the localized XLIFF files are imported.

> [!NOTE]
> Targets are managed per channel and locale. Changes that you make to targets in one channel or locale aren't automatically carried forward to other channels or locales.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
