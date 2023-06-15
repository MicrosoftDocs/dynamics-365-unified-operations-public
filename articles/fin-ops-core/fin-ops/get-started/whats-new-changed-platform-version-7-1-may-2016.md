---
title: What's new or changed in Dynamics AX platform update 1 (May 2016)
description: This article describes features that are either new or changed in Microsoft Dynamics AX platform update 1. This version was released in May 2016 and has a build number of 7.0.4127.16103.
author: sericks007
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: sericks
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: Platform update 1
ms.assetid: 259a6844-3675-44bd-a4ea-57a5976628ff
ROBOTS: NOINDEX, NOFOLLOW
---

# What's new or changed in Dynamics AX platform update 1 (May 2016)

[!include [banner](../includes/banner.md)]

This article describes features that are either new or changed in Microsoft Dynamics AX platform update 1. This version was released in May 2016 and has a build number of 7.0.4127.16103.

## Platform compatibility

| What can you do? | Why is this important? |
|------------------|------------------------|
| Upgrade the Dynamics AX platform to a new release without upgrading your application. | The Dynamics AX platform is now compatible with previous versions of the Dynamics AX application, starting with the Dynamics AX 7.0 (February 2016) version. Therefore, you can stay up to date with the latest improvements of the platform without having to upgrade your whole application. In this release, the platform is functionally compatible with the Dynamics AX 7.0 (February 2016) release. However, it's still not fully binary-compatible, so you must still compile your code after you upgrade the platform. The feature for upgrading the platform is available only to applications that don't overlay any of the following models: Application Platform, Application Foundation, Directory, and Test Essentials. |

## Development and customization

<table>
<thead>
<tr>
<th>What can you do?</th>
<th>Why is this important?</th>
</tr>
</thead>
<tbody>
<tr>
<td>Apply the <strong>InternalsVisibleToAttribute</strong> attribute to open internals for consumption from other models.</td>
<td>As we lock models for over-layering, artifacts will become internal to the model to better isolate implementation details from outside calls. However, it might be advantageous to mark other models as "friends" that have access to the internals. This capability is mainly useful for test scenarios. For this purpose, the <strong>InternalsVisibleTo</strong> tag can be applied to the descriptor XML file for the model that contains the internal code.</td>
</tr>
<tr>
<td>Enable modules to disallow over-layering.</td>
<td>You can now lock models for over-layering, in two phases: soft locking and hard locking. Soft locking causes occurrences of over-layering to be treated as warnings. Hard locking causes occurrences of over-layering to be treated as errors, and the build of the model is blocked. When hard locking is used, you can't perform over-layering.</td>
</tr>
<tr>
<td>Document Customization Analysis Best Practice rule violations on the <strong>Customization analysis</strong> report.</td>
<td>A new column on the <strong>Customization analysis</strong> report lets independent software vendors (ISVs) document why a particular rule has been suppressed.</td>
</tr>
<tr>
<td>Use the <strong>InternalUseOnly</strong> attribute to identify artifacts that should marked as internal in the future.</td>
<td>A new <strong>InternalUseOnly</strong> attribute has been added to the X++ language. The X++ compiler diagnoses cases where artifacts that are decorated with this attribute are referenced outside the current model as warnings. This attribute is an alternative to marking the artifact with the <strong>internal</strong> keyword, but it has the advantage that it gives teams time to weed out rogue references while they are still producing a build.</td>
</tr>
<tr>
<td>Choose the Microsoft Visual Studio 2015 Dark theme for X++ code editing.</td>
<td>The visual quality of the code editing experience has been improved for the Dark theme. Select the theme at <strong>Tools</strong> &gt; <strong>Options</strong> &gt; <strong>Environment</strong> &gt; <strong>General</strong> &gt; <strong>Color theme</strong>.</td>
</tr>
<tr>
<td>Customize extended data types (EDTs) through extension.</td>
<td>You can now customize EDTs through extension. However, you can't currently add array elements.</td>
</tr>
<tr>
<td>Customize the <strong>Text</strong> property on controls in form extensions.</td>
<td>Some controls (such as buttons) have a <strong>Text</strong> property instead of a <strong>Label</strong> property. You can now customize these properties through extension.</td>
</tr>
<tr>
<td>Hide an existing menu item or embedded menu through extension.</td>
<td>You can now set the <strong>Visible</strong> property in an extension.</td>
</tr>
<tr>
<td>Extend a query.</td>
<td>You can now extend a query in the following ways:
<ul>
<li>Add ranges to an existing data source.</li>
<li>Add new (embedded) data sources to an existing data source.</li>
<li>Add new fields to an existing data source.</li>
</ul></td>
</tr>
<tr>
<td>Add instance and static state, and instance and static methods, to class extensions.</td>
<td>The extension story has been extended so that instance methods, static methods, instance state, and static state can be added to Dynamics AX artifacts. In this release, the support is limited to augmenting classes.</td>
</tr>
<tr>
<td>Add top-level functions through extensions of the <strong>Global</strong> class.</td>
<td>The new extension model for classes enables static methods to be added. If a static method is added to an extension of the <strong>Global</strong> class, that method becomes available as a function in the X++ language. Therefore, over-layering is no longer required in order to achieve that result.</td>
</tr>
<tr>
<td>Opt out of the company switch warning.</td>
<td>When you switch rows on forms that display cross-company data from DataAreaID-backed tables, a warning about changing companies is displayed. You can opt out of that behavior on a form-by-form basis, either at design-time in the designer or at run-time through an API method.</td>
</tr>
<tr>
<td>Subscribe to an event that performs the final validation.</td>
<td>The new event, FinalDataValidation, calls the FinalDataValidation events in sequence. This event serves as the final validation of the data and the action before it is applied on the database by the AOS.</td>
</tr>
</tbody>
</table>

## Monitoring and telemetry

| What can you do? | Why is this important? |
|------------------|------------------------|
| Get insights into the most expensive queries that are run on the system. | The **SQL Insights** view on the **Environment monitoring** page shows historical data for the most expensive queries, based on duration, logical input/output (I/O), CPU time, and execution count. There is an option to download the execution plan, so that you can do additional analysis and query tuning. |
| Quickly troubleshoot issues by using predefined queries. | The **View Raw Logs** view on the **Environment monitoring page** has new queries that you can use to troubleshoot specific issues, such as system failures, deadlocks, errors, batch throttling issues, and issues in the **Management reporting** module. |
| Get information about system failures that have occurred in your environment. | The **Monitoring** section in LCS now has a **View suggested fixes** link that shows a list of system failures that have occurred in your environment, together with the number of occurrences and an option to download a hotfix to fix the issue. |

## Web client

<table>
<thead>
<tr>
<th>What can you do?</th>
<th>Why is this important?</th>
</tr>
</thead>
<tbody>
<tr>
<td>See a helpful description for a field or button on a page by hovering the mouse pointer over the field's or button's label.</td>
<td>This feature makes it easier for users to learn and understand important business information that is related to a page field. Therefore, they can now be more productive when they use Dynamics AX.</td>
</tr>
<tr>
<td>Customize and add your own field descriptions.</td>
<td>You can add field descriptions that are specific to your solution, or add information relating to your company policies.</td>
</tr>
<tr>
<td>Perform &quot;heads-down&quot; data entry by using an enhanced grid.</td>
<td>The Dynamics AX grid control now has a <strong>fastEdit</strong> property, which is available at run time. When this property is enabled, the grid and the surrounding page are focused only on accepting and validating user input. Therefore, this property can be used to create an optimized "heads-down" data entry experience. When the application code sets the <strong>fastEdit</strong> property at run time (for example, <strong>MyGridInstance.fastEdit(true)</strong>), typically in the grid <strong>init()</strong> method, the client-side grid devotes its processing to accepting user input. Validation is queued and is only performed whenever the user offers an interactive pause. In this mode, <strong>gotFocus()</strong>, <strong>lostFocus()</strong>, <strong>enter()</strong>, <strong>leave()</strong>, and so on, aren't called, and lookup controls aren't available to the end user. The <strong>fastEdit</strong> property should be used only with grids that don't offer specialized, application-defined entry of default values or multiple-dependent field validation.</td>
</tr>
<tr>
<td>Create a workspace through personalization.</td>
<td>From a dashboard, you can now right-click and select <strong>Personalization</strong> &gt; <strong>Add a workspace</strong>. A workspace tile is added to your dashboard. You can personalize this tile by entering a name for the workspace. Then click the tile to open a new, blank workspace that you can personalize the content of, just as you can personalize the content of any other workspace.</td>
</tr>
<tr>
<td>Add a link to a workspace from a details page.</td>
<td>Previously, you could save a filtered list or a tile from a list page to a workspace. You can now also save the list as a link on the workspace.</td>
</tr>
<tr>
<td>View page information and control information.</td>
<td>You can view technical details about an element via a shortcut menu. The shortcut menu now offers a <strong>Form information</strong> menu item that, in turn, has <strong>Form name</strong> and <strong>Control name</strong> menu items. Click <strong>Form name</strong> to open a dialog box that provides information about the current control and current page. If a developer clicks <strong>Control name</strong>, Microsoft Visual Studio starts and opens the meta definition of the current page and control.</td>
</tr>
<tr>
<td>See improved responsiveness of page elements across devices and browser viewports.</td>
<td>Because Dynamics AX is run in viewports of varying size, it's important that page content be laid out correctly for the available space. The following changes have been made:
<ul>
<li>Overflow buttons are now available on toolbars and on the navigation bar for actions that don't fit the available width of the viewport.</li>
<li>Message box content is now resized, based on the available width.</li>
<li>The various panes (navigation pane, filter pane, navigation list, FactBox pane, and aside pane) now collapse automatically, based on the available width.</li>
</ul></td>
</tr>
</tbody>
</table>

## Data management and integration

| What can you do? | Why is this important? |
|------------------|------------------------|
| Configure cross-company data sharing by replicating reference and group data between multiple companies in the same Dynamics AX deployment. | This feature can make the setup process for multiple companies much easier. For example, if all your companies use the same payment day options, you can configure that group setting in one company and then replicate it to other companies in the deployment. |
| Choose to truncate data in the entity before data is imported via files or data packages. | For import data scenarios, administrators can now choose to truncate data in the entity before data is imported via files or data packages. This feature makes it easy for customers to reset the configuration data to the original dataset in any environment. |

## Analytics

<table>
<thead>
<tr>
<th>What can you do?</th>
<th>Why is this important?</th>
</tr>
</thead>
<tbody>
<tr>
<td>Author Microsoft Power BI reports over large volumes of data by using Power BI Desktop.</td>
<td>In the Dynamics AX 7.0 (February 2016) release, you can author Power BI reports by using OData end points that are exposed via data entities. Although this approach is still supported, power users can now also create Power BI DirectQuery reports by using Dynamics AX data that is staged in Entity store. Entity store, introduced in Dynamics AX platform update 1, is an extensible operational data warehouse that is optimized for advanced analytics. Power BI Desktop is a rich authoring tool that is intended for power users. Power BI Desktop lets you author reports and data models by connecting to Entity store.</td>
</tr>
<tr>
<td>Migrate Power BI reports between Dynamics AX environments.</td>
<td>In most cases, reports are created in developer or test environments where data volume is low. Additionally, test environments might not contain actual customer names or other very personal data. After a report is developed, it must be migrated to production environments. Administrators can now upload the .pbix files for reports to LCS. They can then migrate to a different Dynamics AX environment without having to manually update connection strings and so on.</td>
</tr>
<tr>
<td>Schedule an update of Entity store.</td>
<td>Entity store must be updated with data from the Dynamics AX production environment on a defined schedule. As an administrator, you can create schedules by using the Dynamics AX batch framework.</td>
</tr>
<tr>
<td>Personalize your workspaces by adding Power BI tiles.</td>
<td>In the previous release, Power BI visuals can be added only to a few workspaces that are created by developers. The current release adds personalization capability, so that any user can now either create new workspaces or add Power BI tiles to any existing workspace.</td>
</tr>
<tr>
<td>Personalize your workspaces by adding full-page, interactive Power BI reports</td>
<td>Power BI full-page reports let users interactively explore data. They can either use and tweak the reports that have been created by power users, or create rich reports for themselves. Users can also add the reports to workspaces of their choice as a personalization.</td>
</tr>
<tr>
<td>Release Power BI reports as components of a Dynamics AX solution.</td>
<td>With the Dynamics AX 7.0 (February 2016) release, partners and ISVs can publish Dynamics AX Power BI content packs by using the Power BI marketplace. Those content packs appear as services on PowerBI.com. Although you can still publish content via Power BI marketplace, partners and ISVs can now also release Power BI reports (.pbix files) together with a Dynamics AX solution in LCS. This approach also lets partners release Power BI report packs and updates to their customers in a regular cadence, either on a one-on-one basis or as an update to the solution.</td>
</tr>
<tr>
<td>Take advantage of near-real-time Power BI reporting and the integration of Microsoft Cortana Intelligence Suite (CIS) with Entity store.</td>
<td>Entity store is an extensible and rich operational data warehouse that is optimized for advanced analytic scenarios. Entity store is now deployed with every instance of Dynamics AX. An administrator or a power user can stage Dynamics AX aggregate measurements into an Entity store and configure the update schedule. Data in the Entity store can be reported on by using Power BI DirectQuery models. Therefore, near-real-time Power BI reports can be generated. Entity store is also used for integration with CIS. Dynamics AX data is sent to Microsoft Azure Machine Learning for advanced predictions. The results are then shown in the client user interface.</td>
</tr>
<tr>
<td>Take advantage of framework improvements with SQL Server Reporting Services integration.</td>
<td>Some of these improvements include:
<ul>
<li>Performance improvements when querying large data sets.</li>
<li>Performance improvements when rendering reports to a file.</li>
<li>Better instrumentation and error handling.</li>
</ul>
</td>
</tr>
<tr>
<td>Add your domain as a verified AAD domain to the tenant in which Dynamics AX is deployed.</td>
<td>Using Azure AD portal, you can now add your domain as a verified AAD domain to the tenant in which Dynamics AX is deployed. Doing so will not only allow you to log in and use your domain email accounts to log into Dynamics AX, but you will also be able to use those same accounts to pin Power BI tiles and Power BI reports within the Dynamics AX client.</td>
</tr>
</tbody>
</table>

## Office integration

| What can you do? | Why is this important? |
|------------------|------------------------|
| Add a Yammer or Twitter conversation feed to a page by using the new Feed control. | As an administrator, you can configure a Yammer feed to a workspace, so that users can view and participate in a relevant conversation. For example, a Yammer feed control can be added to the **Sales processing** workspace by a developer and then configured to point to a "Sales Discussion" Yammer group. |
| Configure mail so that it's sent via the new Microsoft Exchange Mail Provider. | As an administrator, you can configure mail so that it's sent via the new Exchange Mail Provider. When a Microsoft 365 license is associated with the tenant (domain), the Exchange Mail Provider is a great option for several reasons. For example, it sends email as the current user instead of using a single saved account. Additionally, unlike the Simple Mail Transfer Protocol (SMTP) provider, the Exchange Mail Provider saves email in the Sent folder. Finally, it doesn't require any configuration except turning it on. |
| See the Skype for Business presence indicator next to email fields that use the **SysEmailAddress** or **EmailBase** EDT. (This feature applies only to non-grid fields that aren't in edit mode.) | Users can quickly see whether a contact is online and available to answer a question via Skype for Business. |
| Add unbound text into Word templates as labels using the Word add-in. | As a template designer, you can use labels for unbound text so that the text is translated appropriately depending on what language is currently being used when a document is generated. |
| Sign into the Office add-ins even when your company uses ADFS. | The Office add-ins now leverage a new API from the Office team that allows an ADFS (Active Directory Federation Services) sign in to take place inside of a special dialog that enables the add-in to avoid some permission issues. To take advantage of this support, your installation of Office should be as up-to-date as possible. |

## Task guides

| What can you do? | Why is this important? |
|------------------|------------------------|
| Access new or updated task guides | Task guides provide a guided, interactive experience that leads you through the steps of a task or business process. You can download and customize the task guides that Microsoft provides. To see a list of new or updated task guides, see [New or updated task guides (May 2016)](new-updated-task-guides-available-may-2016.md). |

## Additional resources

[What's new or changed in finance and operations home page](whats-new-changed.md)

[New or updated task guides (May 2016)](new-updated-task-guides-available-may-2016.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
