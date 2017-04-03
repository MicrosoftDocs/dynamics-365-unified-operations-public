---
# required metadata

title: View and export field descriptions
description: This article describes how to view field descriptions and how to use the Field descriptions page to export descriptions.
author: YuyuScheller
manager: AnnBe
ms.date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: FieldDescriptions
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 2084
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 11534
ms.assetid: e2795f51-a8a7-4c74-bdb9-b1be93bdd358
ms.search.region: Global
# ms.search.industry: 
ms.author: yuyus
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# View and export field descriptions

This article describes how to view field descriptions and how to use the Field descriptions page to export descriptions.

Microsoft Dynamics 365 for Operations has descriptions for some of the more complex fields. These descriptions appear when you hover over a field. You can also view and export descriptions on the **Field descriptions** page. 

Not all pages have field descriptions. We want to provide descriptions only for the more complex fields, not where the use of the field is obvious. Therefore, some pages don't have any field descriptions, some pages have a few descriptions, and some of the more complex pages, such as many of the parameters pages, have many descriptions. 

If you have access to the Dynamics 365 for Operations development environment, you can add new field descriptions and customize existing descriptions. For example, you can add company-specific information to a field description. For more information, see [Customize field help](/dynamics365/operations/dev-itpro/user-interface/customize-field-help).

## See field descriptions in the user interface
You can view field descriptions by hovering over a field. If no description is available, you see the field name when you hover over the field. (Note: In version 7.0.0, field descriptions can be viewed only on the **Field descriptions** page.) The following illustration shows the field description that appears when you hover over the **Lock items during count** field. 

[![Example of a field description](./media/field-description.png)](./media/field-description.png)

## Use the Field descriptions page to view and export field help
The **Field descriptions** page lets you view and export field descriptions. You can see the descriptions that are available for one page at a time.

### View the descriptions for a page

To view the descriptions for a page, follow this step.

-   In the **Select a page** field, type the name of the page. Alternatively, click the arrow to open a list of all the pages, and then browse or filter the list.

You can use either the name of the page that is shown in the user interface (UI) (for example, **Customers**) or the code name (AOT name) that's available when you right-click a page (for example, **CustTable**). 

For information about the various ways to filter the list of pages, see the "Searching for a page" section later in this article. 

If you set the **Include fields without a description** option to **Yes**, all the fields on the page are shown, even if they don't have a field description.

### Export the descriptions for a page

To export the descriptions for a page, follow these steps.

1.  In the **Select a page** field, select a page.
2.  Click the **Open in Microsoft Office** button in the upper-right corner, and then click **FieldDescriptionTmp**.

### Searching for a page

There are several ways to search for a page in the **Select a page** field. In many cases, you must click the arrow in the **Select a page** field to open the drop-down list, and then select from a filtered list of pages.

-   Type part of the name, and then open the drop-down list to select from a filtered list of pages.
-   Open the drop-down list, and then click either the **Page name** heading at the top of the list or the **Page AOT name** heading. A dialog box appears, where you can use advanced filtering options, such as **Page name begins with**.
-   Type the full name of the page. When you use this option, it's best to open the drop-down list and see what else is in the list, even if field descriptions are shown.
    -   If there is a single exact match to the name, the field descriptions for that page are shown.
    -   If there is more than one exact match, no descriptions are shown. You must open the drop-down list and select the page that you want.
    -   If the name that you typed is part of the name of another page, you see the descriptions for your page. However, if you open the drop-down list, you see additional pages that contain that name.

For example, no descriptions are shown when you type **Counting** in the ****Select a page**** field. You open the drop-down list, and see that there are two pages that have the name **Counting** and several pages that contain the word "Counting" in the name. If you select the page that has the AOT name **InventJournalCount**, the field descriptions are shown for that page. However, if you open the drop-down list again, you will see that the list now contains all pages that have "InventJournalCount" as part of their AOT name.

## Troubleshooting
This section provides information to help you troubleshoot issues that you might encounter when you use field descriptions.

### I can't find a field description

We’re in the process of adding descriptions for the more complex fields. If you require help for a particular field, let us know by adding a comment for this wiki article.

### The field description isn't helpful

Let us know by adding a comment for this wiki article. If you can, describe the additional information that you require.

### I can't find a field on the Field descriptions page

To show all the fields on a page, set the **Include fields without a description** option to **Yes**. Click the **Select a page** field to verify that you've selected the correct page. If the name that you typed is part of another field name, you might have selected the page that has the longer name.

### I can't find a page on the Field descriptions page

For information about the various way to find pages, see the "Searching for pages" section earlier in this article. If you've typed the exact name of the page, the field descriptions might not be shown if more than one page has the same name. Click the arrow in the **Select a page** field to open a filtered list of the pages that are available.

See also
--------

[Customize field help](https:/docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/user-interface/customize-field-help.md)

