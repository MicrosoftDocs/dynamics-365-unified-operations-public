
This release includes the following bug fixes. Changes apply to build number 8.1.4591.

### Bug fixes

The following bug fixes are included in this release.

> [!NOTE]
> Our goal is to get you this information as soon as possible. We might update this topic to include bug fixes that made it into the build after this topic was initially published.

| Issue number | Issue | Description |
|---|---|---|
| 632573 | No Validation error when saving Course | Create course with only changing minimum participants number to greater than 0 still allow being saved even when maximum is still 0. |
| 632040 | Benefits container is still visible in ESS, even though it is empty. | |
| 615955 | Error "Field 'Purpose' must be filled in" when creating new recruiting request location. | When creating an address for a new recruiting request location, you get the error: "Field 'Purpose' must be filled in." However, the "Purpose" field is not available on the page. |
| 620797 | Blank gender field is misleading | When gender is not entered for a personal contact the report shows ‘Click or tap here to enter text’ – That is misleading as nothing can be entered for that. |
| 620798 | Benefit statement removing decimal places. | Benefit statement was removing last decimal place if it's zero. |
| 620800 | Benefits statement link is hidden. | Benefit statement statement is not viewable by default in ESS. |
| 626699 | Worker name appears incorrectly. | In the checklist group setup, the worker name appears incorrectly after removing a position. |
| 629778 | Performance issue with CDS integration. | Auth related request caused performance issue. |

## In preview

The following new features are in preview. For more information about how to turn features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
|---|---|---|
| Benefits management workspace | [Benefits management workspace (Preview)](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/benefits-management-workspace) | [Benefits management workspace](hr-benefits-management-workspace.md) |
| Custom fields in Eligibility |[Custom fields support in eligibility processing](/dynamics365-release-plan/2021wave1/human-resources/dynamics365-human-resources/custom-field-support-benefits-management) | [Using custom fields in eligibility processing](/dynamics365/human-resources/hr-benefits-setup-eligibility-rules#using-custom-fields-in-eligibility-rules) |

## Coming soon
For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2021 release wave 2](/dynamics365-release-plan/2021wave2/human-resources/dynamics365-human-resources/).

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2021 release wave 2](/dynamics365-release-plan/2021wave2/human-resources/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
