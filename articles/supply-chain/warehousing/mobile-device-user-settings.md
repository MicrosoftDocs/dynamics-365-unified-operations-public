---
# required metadata

title: Mobile device user settings
description: 
author: MarkusFogelberg
manager: tfehr
ms.date: 02/09/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WHSMobileAppDeviceBrand,WHSMobileAppUserDisplaySettings
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
# ms.search.industry: 
ms.author: mafoge
ms.search.validFrom: 2021-02-09
ms.dyn365.ops.version: 10.0.17

---

<!-- Metadata (above this):
- Add a very short **description** of this topic. Ideally 50 - 160 characters.
- **ms.search.form**: Add form IDs for each page where this help topic should be available as context help. (I did this already here, but you can add more if needed)
 -->

# Mobile device user settings

<!-- Add intro text. Start with the big picture of what the feature does and why the reader might want to use it. How does this benefit users and their businesses? Don't describe the UI. Answer the question: Why should I read the rest of this?  -->

> [!IMPORTANT]
> <!-- Mention that this topic only applies to the new Warehouse Management mobile app.  -->

## Turn on the XXXXX feature

<!-- Always include this section if needed (it is here). Replace XXXXX with actual values, exactly as seen in the UI. -->

Before you can use this feature, it must be turned on in your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *XXXXX*
- **Feature name:** *XXXXX*

## Create and manage user settings

<!-- Add a full intro to this section. This time with more of a feature focus (what am I about to do, and why). Mention the concept of "most specific" setting and how that let's us set up an "All" profile, specific device profiles, and specific device/user profiles. -->

To create and manage user settings for your mobile devices:
<!-- I like numbered procedures. They don't always fit, but often fit more often than you might think. Talk directly to the reader (second person) or name the role (such as "worker") for tasks likely done by somebody not the reader, or "the system" if something will happen automatically (avoid passive voice). -->

1. Go to **XXX \> XXX \> XXX**.
1. Select a user setting from the list pane or select **New** from the Action Pane to create a new one. <!-- Maybe note briefly how the records in the list pane are labelled and what that says about their specificity (though we may have covered enough of this in the intro). -->
1. Make the following settings in the header section of the new or selected record:
    - **Device brand name** - <!-- Describe how to use this. Mention where these values come from (see also next section). Mention why the user might leave this blank. Same goes for the other settings here. -->
    - **Device model ID** - 
    - **User ID** - 
1. Make the following settings on the **General** FastTab:
    - **Button position** - 
    - **Display orientation** -
    - **Scan with camera** - <!-- Describe the effect of both Yes and No options. It's often less obvious than you might think. -->
    - **Show product photo** - <!-- This Yes/No option is obvious though, so you can say something like "Choose whether or not to show product photos ..." and then mention where the photos may appear and maybe where they come from. -->
    - **Display color theme** - <!-- Often we might add a sub-bullet list to describe each option here, but in this case I don't think we need to. -->
    - **Sound level** - <!-- Mention the range of valid values. -->
    - **Vibration level** - 
    - **Text scale percentage** - <!-- Mention the range of valid values. Percentage of what? -->
    - **Button scale percentage** - 

## Create and manage mobile device brands

<!-- Add a full intro to this section. Same basic strategy as the previous. Mention why the user would want to set these up. Mention that these might typically be generated automatically. -->

To create and manage your mobile device brands:

1. Go to **XXX \> XXX \> XXX**.
1. Select a mobile device brand from the list pane or select **New** from the Action Pane to create a new one.
1. Make the following settings in the header section of the new or selected device:
    - **Device brand name** - 
    - **Description** - 
1. Use the **Mobile device models** FastTab to <!-- Explain the general purpose of the items here. -->. Use the toolbar on this FastTab to add or remove rows in the grid. Make the following settings for each row:
    - **Device model ID** - 
    - **Description** - 
