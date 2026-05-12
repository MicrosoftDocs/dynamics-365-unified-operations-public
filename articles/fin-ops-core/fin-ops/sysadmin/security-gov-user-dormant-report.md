---
title: User log and dormant user report V2 for Finance and Operations (preview)
description: Learn how the new User log V2 form gives Finance and Operations administrators an accurate view of user sign-ins and dormant accounts.
author: anshularora  
ms.author: anshularora
ms.topic: concept-article
ms.date: 05/12/2026
ms.custom: 
ms.reviewer: 
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2026-05-12
ms.search.form: UserSecGovSysUserLogV2, UserSecGovMain
ms.dyn365.ops.version: Version 10.0.47
---

# User log and dormant user report V2 for Finance and Operations (preview)

The **User log and dormant user report V2** feature helps Finance and Operations administrators audit user activity and review past sign-ins.

The feature has two views:

- **User log** &mdash; Lists each user sign-in in the system. Each row shows the user, the date and time, and account details. Use this view to confirm or investigate a user's past activity.
- **Dormant user report** &mdash; Lists inactive users. You set how many days of inactivity count as "dormant." The report then shows users who haven't signed in within that period, plus users who have never signed in.

This article covers:

- What the feature offers
- Prerequisites and how to turn it on
- Where to find the form and how to read it
- An important note for customers who already use the older dormant user report
- Frequently asked questions

## Prerequisites

Before you turn on the feature, check the following items:

- You're signed in as a **System administrator**.
- The **User security governance** feature is on. User Log V2 depends on it.
- Your environment runs **Platform Update 73 (PU73)** or later.
- Your environment runs **Finance and Operations** version **10.0.49** or later.

## Turn on the feature

1. In the Finance and Operations app, go to **Workspaces** &gt; **Feature management**.
2. Select **All** and search for **User log**.
3. Select **(Preview) User log and dormant user report V2 feature** and choose **Enable now**.

> [!NOTE]
> This feature is in **public preview**. You can turn it off at any time from the same page.

After you turn on the feature, find the new menu item at:
**System administration** &gt; **Security** &gt; **Security governance** &gt; **User Log V2**.

## Use the User Log V2 form

Open the form from **System administration** &gt; **Security** &gt; **Security governance** &gt; **User Log V2**. It has two tabs.

### User audit report tab

This tab lists sign-in events, with the most recent at the top. Each row shows one verified sign-in. It includes the user ID, email, date, and time.

Use this tab to investigate a user's sign-in activity. For example: *"Did this user sign in last Tuesday?"* The grid is read-only. You can still filter, group, and **Export to Excel** as usual.

### Dormant user report tab

This tab builds the report on demand. Set the filters at the top of the tab. Then select **Show** to view the results.

Filters:

| Filter | Values | Meaning |
|---|---|---|
| **Days inactive** | Number (`0` = all users) | Shows users whose last sign-in was at least this many days ago. Enter `0` to show every user, including users who never signed in. |
| **Account status** | **All**, **Enabled**, **Disabled** | Shows only accounts in the state you pick. |
| **Authentication type** | **All**, **Claims user**, **Active Directory user** | Filters by how the user signs in. |

Result columns: **User ID**, **User name**, **Alias**, **Company**, **Enabled**, **Last login**, **Days since last login**, **Account type**.

> [!NOTE]
> For users who have **never** signed in, **Last login** is blank, and **Days since last login** is `-1`. Treat `-1` as a flag for "no sign-in on record," not as a real day count.

## Important &mdash; this is a new feature, not an extension of the older report

> [!IMPORTANT]
> The User log V2 form **doesn't show any historical data**. The system starts to collect sign-in data only after you turn on the feature. Data from before that point isn't moved into the new form.
>
> To review user activity from **before** you turned on the feature, use the **older dormant user report**. The two reports are independent, and you can use them side by side. The older report still holds your past data. User log V2 covers every sign-in from this point forward.

## Frequently asked questions

**Q. The form opens, but both tabs are empty. What did I miss?**
The feature is on, but the system hasn't captured any sign-ins yet. Ask a user to sign in, and then refresh the form. New rows then appear on the **User audit report** tab.

**Q. Can I run V2 alongside the older report?**
Yes. The two reports are independent. You can compare them side by side while you build confidence in V2.

**Q. Can I export the report?**
Yes. Both tabs are standard Finance and Operations grids. Use **Open in Microsoft Office** &gt; **Export to Excel** as you would for any other grid.

**Q. Do you support Active Directory users?**
Yes. The system captures both **Claims user** and **Active Directory user** sign-ins. To narrow the report to one type, use the **Authentication type** filter on the **Dormant user report** tab.
