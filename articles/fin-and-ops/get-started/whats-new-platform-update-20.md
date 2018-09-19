---
# required metadata

title: What's new or changed in Dynamics 365 for Finance and Operations platform update 20 (September 2018)
description: This topic describes features that are either new or changed in Dynamics 365 for Finance and Operation platform update 20. This version was released in September 2018.
author: tonyafehr
manager: AnnBe
ms.date: 09/19/18
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: tfehr
ms.search.scope:  Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: a765a61c-52a3-45c5-b578-68b9249c592a
ms.search.region: Global
# ms.search.industry: 
ms.author: tfehr
ms.search.validFrom: 2017-09-30 
ms.dyn365.ops.version: Platform update 16, Platform update 17, Platform update 18, Platform update 19, Platform 20

---
# What's new or changed in Dynamics 365 for Finance and Operations platform update 20 (September 2018)

[!include [banner](../includes/banner.md)]

This topic describes features that are either new or changed in Dynamics 365 for Finance and Operations platform update 20. This version was released in September 2018 has a build number of XXXXX.

> [!NOTE]
> This platform release is cumulative. It contains new or changed features from Platform update 16, Platform update 17, Platform update 18, Platform update 19, and Platform update 20, as well as all earlier updates. 

> This update is currently available for targeted customers and will be available to all users in the future. For more information about standard and targeted releases, see the [Standard and targeted platform releases](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/get-started/public-preview-releases) topic.

### Announcing the Dynamics 365 October '18 release notes
Wondering about upcoming and recently released capabilities in any of our business apps or platform? 

[Check out the October '18 release notes](https://go.microsoft.com/fwlink/?linkid=870424). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning. 

### Platform update 20 bug fixes
For information about the bug fixes included in Platform update 20, log in to Lifecycle Services (LCS) and view this [KB article](https://go.microsoft.com/fwlink/?linkid=875608).

## Adding and removing columns in a grid is easier
Some of the most typical changes that a user makes to a grid are adding, removing, resizing, and reordering
columns. In this update, we’ve made adding and removing columns easier by promoting the **Add columns** and **Hide this column** actions directly into the grid column header context menus. 

## Chain of Command on nested types 
In this release, we’ve enabled Chain of Command on nested types within forms including data sources and controls. This allows Chain of Command to be used for a much wider range of extension scenarios involving forms. For more information, see [Nested class methods in forms can be wrapped in Platform update 16 or later](../../dev-itpro/extensibility/method-wrapping-coc.md#nested-class-methods-in-forms-can-be-wrapped-in-platform-update-16-or-later).

## Change form patterns to custom using form extensions
With this update, you can change a form's pattern to custom by using a form extension. This allows for more
flexibility in the structure of the form that you are extending. However, the basic structure should remain the same so
that form updates in the future don't conflict with your customizations.

## Client internet connection
Client internet connectivity options allow an administrator to manually turn off
the external connections that the client makes even when internet connectivity
is available. These can be used for troubleshooting issues or to see what the
client will look like when internet connectivity is not available. For more
information, see [Client internet connectivity
options](#chain-of-command-on-nested-types).

## Data management updates
Platform update 20 fixes an issue related to data being truncated during export when using text qualifiers. Using a
text qualifier means that the system pads the data value with the text qualifier character, which increases the total
length of the data value. The issue was that the logic was not handling the increased length correctly, resulting in
truncation.

This update also fixes an issue when exporting empty composite entities in non-batch mode.
To improve the performance of loading the data management workspace, a non-unique index made up of a
**partitionID** and **DefinitionGroup** has been added.

Previously, when a file was used to import data and there was a column with the same name as a column in the
staging table and the columns were not mapped, the import would fail if the column in the staging table was
configured to default a value in the mapping details for the data project. This has been fixed.

When an entity’s child artifact had the configuration key disabled, the entire entity was not available in the OData
flow which affected the Excel-add in use cases. The logic has been fixed to honor the configuration keys in a manner
consistent with DIXF.

After updating to Platform update 15, some environments never completed an entity list refresh, which made certain
entities unusable. Now the logic for all entities is available by default, which means that an entity is no longer
enabled if the config key checks fail.

Under certain circumstances, data jobs used to fail if they were executed when the entity list refresh was still in
progress. This occurred if there were mapping errors resulting from the entity refresh. This has been addressed by
adding validations to check for mapping errors in the flow and providing appropriate messages to the user. For
batch and integration jobs, the messages are now logged to help investigate failures.

Previously, when taking API out of the queue, in cases when there was no file uploaded to the blob, the API still
returned a URL in its response. This has been fixed so that the URL returned will be NULL along with the reason why
it is NULL.

OData flows also used to excessively check for user security privileges. This has been fixed so that the number of
times the check is made during an OData call processing is optimized.

## Data task automation
Data task automation in Microsoft Dynamics 365 for Finance and Operations lets
you easily repeat many types of data tasks and validate the outcome of each
task. Data task automation is very useful for projects that are in the
implementation phase. For example, you can automate the creation and
configuration of data projects. You can also configure and trigger the execution
of import/export operations, such as the setup of demo data and golden
configuration data, and other tasks that are related to data migration. You can
also create automated testing of data entities by using task outcome validation.
For more information, see [Data task automation](#data-task-automation).

## Extensibility enhancements
Platform update 20 includes the following extensibility enhancements:
-  Enable changing a form to use a custom pattern that includes a form extension. This allows ISVs to add tabs
and other form parts that don’t fit the original pattern. Developers now have actions to **Set pattern to
custom** and **Restore original pattern**.
-  Allow an extension to change **TableField.AssetClassification** so that General Data Protection Regulation
(GDPR) data classification information can be provided.
-  Enable form extension methods to call methods and controls that are added by using other extensions. For
example, now when a form has a button and methods added by extension, future extensions to that form
will be able to call the new button and methods.
-  Add query object support for set-based update statements by using an update_recordset method.
-  Allow a query extension to add a root data source to a union query.
-  Enable the addition of ranges into a view using an extension.
-  Enable setting **SupportsSetBasedSqlOperations** on data entity view extensions. **Yes** can only be set if all
extensions have are set to **Yes**, including the base element. If any extension or the base element has the
value set to **No**, then the runtime result will be **No**.
-  Allow a form extension to add workflow to a form by editing **WorkflowEnabled**, **WorkflowDataSource**,
and **WorkflowType**.
-  Enable Chain of Command for form methods. This allows an extension to add workflow to a form by
overriding the **canSubmitToWorkflow** method. Note that if the targeted form method is a kernel method
without an X++ override, then you will need to recompile the target form.
-  Enable Chain of Command for data entities.
-  Enable Chain of Command on nested types within forms, including data sources and controls.

For more information about all the extensibility capabilities, see the [Extensibility home page](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/extensibility/extensibility-home-page).

## Incremental refresh option for entity store models
Incremental refresh is an option for
updating entity store models in response to changes in objects referenced by the
model. These are changes to root attributes within a model that are detected by
the delta processing engine during an entity store refresh. This includes entity
store model collections that can be uniquely identified using a field reference.
System administrators can use the entity store management tooling provided with
Finance and Operations to identify entity store models supported by the
incremental delta detection logic.

## Performance improvement in the Visual Studio development environment
This update includes fixes that improve your experience while using the X++ code editor and metadata properties
window. This includes:
-  When hovering the mouse pointer over a label ID in the X++ code editor, Visual Studio used to “freeze” in
some cases. This bug has been resolved.
-  Opening the X++ code editor is faster, especially when working with large files. We have optimized the
process of loading referenced assemblies.
-  Opening the EDT property lookup from the properties window is significantly faster. In some cases, time was
reduced from 8 seconds to 0.03 seconds.

## Performance improvements in the web client that may affect test automation code
With this update, data that is bound to controls that are not visible to the end user will not be sent over from the
server until the control becomes visible. If you use test automation that uses form adaptors or the SysTest framework,
you may need to make changes to your test code. For more details, refer to the [Performance improvements that may
affect test automation code](https://community.dynamics.com/365/financeandoperations/b/newdynamicsax/archive/2018/05/08/performance-improvements-that-may-break-automated-test-code) blog post.

## Personalization tools
On the **Personalization** toolbar, you can now hide required fields and sections that contain required fields. This allows you to create a simplified experience where required fields that are defaulted by business logic are not shown. Hidden required fields are also temporarily made visible if they are empty when a save is attempted.

If the **Personalization** toolbar is open, the page is still read-only but is now much more interactive. Specifically, you can expand or collapse the FactBox pane, switch tabs, and expand or collapse sections while the **Personalization** toolbar is open in the same manner as you typically would on the page. To apply a personalization change to a collapsible section or tab (such as to hide a FastTab), you will trigger the button that appears beside the collapsible section or tab when it gains keyboard focus or when you hover over it.

For more information about personalization, see [Personalize the user experience](personalize-user-experience.md).

## Updates to the Performance software development kit
As of Platform update 20, you don’t need to create certificates or sign in to your test environment using Remote
Desktop to configure the Performance software development kit (Perf SDK). The new Perf SDK uses the Azure Active
Directory (AAD) application to authenticate test users.
