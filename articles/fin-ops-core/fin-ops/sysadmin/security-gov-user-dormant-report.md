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

The **User log and dormant user report V2** feature gives Finance and Operations administrators an accurate view of **user activities in the system** for the purpose of **auditing and historical review**.

The feature provides two complementary views:

- **User log** &mdash; an audit trail of individual user sign-in activity in the system, showing each user, the date and time of each sign-in, and the related account information. This to confirm or investigate a user's past activity.
- **Dormant user report** &mdash; a derived view that uses the same activity history to surface **inactive users**. Administrators define how many days of inactivity qualify as "dormant," and the report returns the accounts that meet that criteria, including users who have never signed in at all.

This article covers:

- What the feature offers
- Prerequisites and how to turn it on
- Where to find the form and how to read it
- An important note for customers who already use the older dormant user report
- Frequently asked questions

## Prerequisites

Before you turn on the feature, confirm the following:

- The signed-in user has the **System administrator** role.
- The **User security governance** feature is already turned on. User Log V2 requires it as a dependency &mdash; you cannot enable User Log V2 without it. If it is off, the feature management page shows the message *"The User Security Governance feature must be enabled before enabling this feature."*
- **Platform Update 73 (PU73)** and above.
- **Finance and Operations application version 10.0.49** or later.

## Turn on the feature

1. In the Finance and Operations app, go to **Workspaces** &gt; **Feature management**.
2. Select **All** and search for **User log**.
3. Select **(Preview) User log and dormant user report V2 feature** and choose **Enable now**.

> [!NOTE]
> This feature is in **public preview**. It can be turned off again at any time from the same page.

After the feature is enabled, the new menu item is available at:
**System administration** &gt; **Security** &gt; **Security governance** &gt; **User Log V2**.

## Use the User Log V2 form

Open the form from **System administration** &gt; **Security** &gt; **Security governance** &gt; **User Log V2**. It has two tabs.

### User audit report tab

This tab shows individual sign-in events, sorted with the most recent sign-in at the top. Each row represents a verified authentication for a user, including their user ID, email, and the date and time of sign-in.

Use this tab to investigate specific sign-in activity &mdash; for example, *"Did this user sign in last Tuesday?"*. The grid is read-only, but standard filtering, grouping, and **Export to Excel** all work as usual.

### Dormant user report tab

This tab generates a list of users on demand based on the filters you choose. Set the filters at the top of the tab and select **Show** to view the report.

Filters:

| Filter | Values | Meaning |
|---|---|---|
| **Days inactive** | Number (`0` = all users) | Returns users whose last sign-in is at least this many days ago. `0` returns every user, including users who have never signed in. |
| **Account status** | **All**, **Enabled**, **Disabled** | Includes only accounts in the selected state. |
| **Authentication type** | **All**, **Claims user**, **Active Directory user** | Filters by how the user authenticates. |

Result columns: **User ID**, **User name**, **Alias**, **Company**, **Enabled**, **Last login**, **Days since last login**, **Account type**.

> [!NOTE]
> Users who have **never** signed in are returned with **Last login** blank and **Days since last login** = `-1`. Treat `-1` as an indicator of "no recorded sign-in," not as a real day count.

## Important &mdash; this is a new feature, not an extension of the older report

> [!IMPORTANT]
> The User log V2 form **does not contain any historical data**. Sign-in information is captured fresh, starting from the moment you enable the feature. Data from before that point is not migrated or back-filled into the new form.
>
> If you need to review user activity from **before** the feature was enabled, continue to use the **older dormant user report** for that historical view. The two reports are independent and can be used side-by-side &mdash; the older report remains available for past data, and User log V2 becomes the source of truth for everything captured going forward.

## Frequently asked questions

**Q. The form opens but both tabs are empty. What did I miss?**
The feature is on, but no sign-in data has been captured yet. Have at least one user sign in, then refresh the form &mdash; rows will start to appear in the **User audit report** tab.

**Q. Can I run V2 alongside the older report?**
Yes. The two are independent. You can compare them side-by-side while you build confidence in V2.

**Q. Is the report exportable?**
Yes &mdash; both tabs are standard Finance and Operations grids, so **Open in Microsoft Office** &gt; **Export to Excel** works as usual.

**Q. Are Active Directory users supported?**
Yes. Both **Claims user** and **Active Directory user** sign-ins are captured, and the **Authentication type** filter on the **Dormant user report** tab lets you narrow the report to one type.
