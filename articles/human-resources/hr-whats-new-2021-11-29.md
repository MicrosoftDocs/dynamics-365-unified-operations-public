---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources November 19, 2021
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for November 19, 2021.
author: marcelbf
ms.date: 12/03/2021
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

ms.search.form:
# ROBOTS:
audience: Application User
# ms.devlang:
ms.search.scope: Human Resources
# ms.tgt_pltfrm:
ms.custom:
ms.assetid:
ms.search.region: Global
# ms.search.industry:
ms.author: marcelbf
ms.search.validFrom: 2021-12-03
ms.dyn365.ops.version: Human Resources

---

This release includes the following bug fixes. Changes apply to build number 8.1.4591.

### Bug fixes

The following bug fixes are included in this release.

> [!NOTE]
> Our goal is to get you this information as soon as possible. We might update this topic to include bug fixes that made it into the build after this topic was initially published.

| Issue number | Issue | Description |
|---|---|---|
| 626178 | Navigation missing from worker tiles in MSS |Fixed navigation to be able to see details of reports in MSS. |
| 632573 | No Validation error when saving Course | Create course with only changing minimum participants number to greater than 0 still allow being saved even when maximum is still 0. |
| 615955 | Error "Field 'Purpose' must be filled in" when creating new recruiting request location. | When creating an address for a new recruiting request location, you get the error: "Field 'Purpose' must be filled in." However, the "Purpose" field is not available on the page. |
| 620797 | Blank gender field is misleading | When gender is not entered for a personal contact the report shows ‘Click or tap here to enter text’ – That is misleading as nothing can be entered for that. |
| 620800 | Benefits statement link is hidden. | Benefit statement statement is not viewable by default in ESS.  Link added to the right side of ESS under 'Links' section |
| 629778 | Performance issue with CDS integration. | Auth related request caused performance issue. |

## In preview

The following new features are in preview. For more information about how to turn features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
|---|---|---|
| Benefits management workspace | [Benefits management workspace (Preview)](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/benefits-management-workspace) | [Benefits management workspace](hr-benefits-management-workspace.md) |


## Coming soon
For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2021 release wave 2](/dynamics365-release-plan/2021wave2/human-resources/dynamics365-human-resources/).

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2021 release wave 2](/dynamics365-release-plan/2021wave2/human-resources/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
