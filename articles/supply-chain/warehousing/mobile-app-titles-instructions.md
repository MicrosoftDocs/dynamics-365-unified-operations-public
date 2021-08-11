---
title: Step instructions and titles for the Warehouse Management mobile app
description: This topic describes how to create and display custom instructions for each step of each task flow that you set up for the Warehouse Management mobile app.
author: MarkusFogelberg
ms.date: 08/11/2021
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: mafoge
ms.search.validFrom: 2021-08-11
ms.dyn365.ops.version: 10.0.21
---

# Customize step titles and instructions for the Warehouse Management mobile app

> [!IMPORTANT]
> The features described in this topic only apply for the new Warehouse Management mobile app. They do affect the old warehouse app (which is now deprecated).

This topic describes how to create and display custom instructions for each step of each task flow that you set up for the Warehouse Management mobile app. When provided with well-written instructions, your warehouse workers will be able to start using new flows right away, with no prior training. With this feature, you can:

- **Ramp up workers faster by letting them follow simple instructions for each task step** – Each step of a flow provides instructions that allow front-line workers to understand the task.
- **Provide instructions that match your own processes** – Write your own instructions to match your own business and warehouse processes. You can make the terminology fit your physical space, local abbreviations, and so on.

## Turn on the Warehouse app step instructions feature

Before you can use this feature, it must be turned on in your system. Admins can use the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Warehouse management*
- **Feature name:** *Warehouse app step instructions*

## Step titles and step instructions in the app

Each step in a task flow on the Warehouse Management mobile app is identified by a step ID, and for each step there is a step title, icon, and instruction (see also [Assign step icons and titles for the Warehouse Management mobile app](step-icons-titles.md)).

### Step titles

A *step title* is a short description of what a worker should do during a step. It is shown in large text at the top the screen, as shown in the following illustration.

![Step titles in the Warehouse Management mobile app](media/wma-step-title.png "Step titles in the Warehouse Management mobile app")

> [!TIP]
> Because of the large text size, you should try to keep your titles as short as possible—otherwise the text may be cut off. However, for long titles, workers will still be able to open a dialog with the full text by doing a long-press on the title.

### Step instructions

A *step instruction* is a longer description that provides more information about what a worker should do during a step. It is shown as a pop-up dialog and can be dismissed by tapping anywhere outside of the dialog box. The step instructions appear automatically when a step opens, but include a **Don't show again** check box, which workers can select to prevent the instructions from opening the next time they run the same task.

![Step instructions in the Warehouse Management mobile app](media/wma-step-instructions.png "Step instructions in the Warehouse Management mobile app")

## Load the default setup

When you first turn on the *Warehouse app step instructions* feature, your system won't contain any customizable step titles or instructions, so the first thing you should do is load the defaults. Each default provides text for all available step IDs in each supported language. To load the defaults:

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device steps**.
1. On the Action Pane, select **Create default setup**. This will populate the page with the standard steps.

## Customize step titles and instructions

To customize the title and/or instructions for a step in any number of languages:

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device steps**.
1. The **Mobile device steps** page opens. It lists each step that is available for your system. Each step ID might be shared between any number of mobile device menu items, in which case the same titles and descriptions will be shown for each menu. However, you can create overrides if you want to customize the title and description for specific menu items (as described in the next section). The grid shows the following columns:
    - **Menu item name** – Rows where this field is blank contain the default step titles and descriptions, which apply for all mobile device menu items unless an override is defined. Columns where a menu item is shown here contain overrides that apply to the specified menu item only.
    - **Step ID** – Shows the unique ID for a step.
    - **Title for input** – Shows the title displayed when the app is requesting new information. The page will typically contain blank input fields and no preset values.
    - **Title for confirmation** – Shows the title displayed when the app is requesting confirmation of a value already stored in the system. The fields on the page will typically include preset values.

1. Find the combination of **Step ID** and **Menu item name** that you want to edit and select the value in the **Step ID** column. This opens a page with a grid that lists all the available translations for the titles and descriptions of your selected step.
1. There are two methods to customize the text for any language. Each method allows you to edit texts for existing languages, but only the **Add** method enables you to add texts for new languages, while only the **View translations** method enables you to view and edit texts for all existing menu overrides of the selected language. Do one of the following:
    - Select **Add** on the toolbar to open a dialog where you can add or edit texts for any supported language. Set the **Reference language** to view values in that language in the left column. Set **Language of the translations** to the language you want to add or customize. In the right column, edit the values for **Title for input**, **Instruction for input**, **Title for confirmation**, and **Instruction for confirmation** as needed. Then select **OK**.
    - In the grid, find and select the row that shows the **Language** you want to edit. Select **View *&lt;language&gt;* translations of this step** on the toolbar to open a dialog where you can edit texts for all available overrides for the language you selected. The dialog includes a grid with rows for both the standard texts (where **Menu item name** is blank), and for each available override text (where **Menu item name** shows the menu item the override applies to). Edit the values for **Title for input**, **Instruction for input**, **Title for confirmation**, and **Instruction for confirmation** as needed. Then select **OK**.

1. Continue working until you have defined each of the required titles and instructions for each required language.

## Add menu-specific overrides

As mentioned in the previous section, you can create any number of menu-specific overrides for each step ID. You might use this capability to edit and change the instruction to better fit your local business process for a specific menu item—for example, for sales pick you could provide a hint to start by scanning a work ID if your company normally provides those on a printed document for the worker.

Each override applies to a specific mobile device menu item and can contain any number of translations. All menu items for which no override exists will use the standard texts. For languages where no override translation is defined, the system likewise reverts to the standard texts, even for menu items where an override is otherwise defined for other languages.

To create and configure an override:

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device steps**.
1. In the grid, find and select the row you want to create an override for.
1. On the Action Pane, select **Add step configuration**.
1. The **Add step configuration** drop-down dialog box opens. Set **Menu item** to the name of the mobile device menu item for which your override will apply. Then select **OK**.
1. A page opens showing all the texts available for your new override. Initially, just one language is created. All other languages will continue to use the standard texts unless you add those languages here. Edit the texts and add new languages as needed, as described in the previous section.
