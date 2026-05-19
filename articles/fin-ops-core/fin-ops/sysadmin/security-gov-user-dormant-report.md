---
title: User log and dormant user report V2 for finance and operations (preview)
description: Learn how the new User log V2 form gives finance and operations administrators an accurate view of user sign-ins and dormant accounts.
author: anshularora  
ms.author: anshularora
ms.topic: concept-article
ms.date: 05/19/2026
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2026-05-19
ms.search.form: UserSecGovSysUserLogV2, UserSecGovMain
ms.dyn365.ops.version: Version 10.0.48
---

# User log and dormant user report V2 for finance and operations (preview)

[!include [banner](../../../finance/includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

The **User log and dormant user report V2** feature helps finance and operations administrators audit user activity and review past sign-ins.

The feature has two views:

- **User log**: Lists each user sign-in in the system. Each row shows the user, the date and time, and account details. Use this view to confirm or investigate a user's past activity.
- **Dormant user report**: Lists inactive users. You set how many days of inactivity count as "dormant." The report then shows users who didn't sign in within that period, plus users who never signed in.

## Prerequisites

Before you turn on the feature, you must meet the following prerequisites:

- You're signed in as a **System administrator**.
- The **User security governance** feature is on. User Log V2 depends on it.
- Your environment is on **Platform update 72 (PU72)** with build number **7.0.7996.40 or higher**, or any later platform update.
- Your environment is on **Finance and operations version 10.0.48** or later.

## Enable the user log feature

To enable the user log feature, follow these steps:

1. In finance and operations, go to **Workspaces** > **Feature management**.
1. Select **All** and search for **User log**.
1. Select **(Preview) User log and dormant user report V2 feature** and choose **Enable now**.

> [!NOTE]
> This feature is in **public preview**. You can turn it off at any time from the same page.

After you enable the user log feature, find the new menu item at:
**System administration** > **Security** > **Security governance** > **User Log V2**.

## Use the User Log V2 form

Open the form from **System administration** > **Security** > **Security governance** > **User Log V2**. It has two tabs.

### User audit report tab

This tab lists sign-in events, with the most recent at the top. Each row shows one verified sign-in. It includes the user ID, email, date, and time.

Use this tab to investigate a user's sign-in activity. For example: *"Did this user sign in last Tuesday?"* The grid is read-only. You can still filter, group, and **Export to Excel** as usual.

### Dormant user report tab

The dormant user report tab builds the report on demand. Set the filters at the top of the tab. Then select **Show** to view the results.

The following table shows the available filters:

| Filter | Values | Meaning |
| ------ | ------ | ------- |
| **Days inactive** | Number (`0` = all users) | Shows users whose last sign-in was at least this many days ago. Enter `0` to show every user, including users who never signed in. |
| **Account status** | **All**, **Enabled**, **Disabled** | Shows only accounts in the state you pick. |
| **Authentication type** | **All**, **Claims user**, **Active Directory user** | Filters by how the user signs in. |

Result columns: **User ID**, **User name**, **Alias**, **Company**, **Enabled**, **Last login**, **Days since last login**, **Account type**.

> [!NOTE]
> For users who **never** signed in, **Last login** is blank, and **Days since last login** is `-1`. Treat `-1` as a flag for "no sign-in on record," not as a real day count.

> [!IMPORTANT]
>
> This is a new feature, and not an extension of the older report.
>
> The User log V2 form doesn't show any historical data. The system starts to collect sign-in data only after you turn on the feature. Data from before that point isn't moved into the new form.
>
> To review user activity from before you turned on the feature, use the **older dormant user report**. The two reports are independent, and you can use them side by side. The older report still holds your past data. User log V2 covers every sign-in from this point forward.

## Frequently asked questions

### The form opens, but both tabs are empty. What did I miss?

The feature is on, but the system didn't capture any sign-ins yet. Ask a user to sign in, and then refresh the form. New rows appear on the **User audit report** tab.

### Can I run V2 alongside the older report?

Yes. The two reports are independent. You can compare them side by side while you build confidence in V2.

### Can I export the report?

Yes. Both tabs are standard Finance and Operations grids. Use **Open in Microsoft Office** &gt; **Export to Excel** as you would for any other grid.

### Do you support Active Directory users?

Yes. The system captures both **Claims user** and **Active Directory user** sign-ins. To narrow the report to one type, use the **Authentication type** filter on the **Dormant user report** tab.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
