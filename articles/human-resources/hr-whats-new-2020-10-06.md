---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources (October 6, 2020)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for October 6, 2020.
author: jcart1106
ms.date: 10/06/2020
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

ms.search.form:
# ROBOTS:
audience: Application User
# ms.devlang:
# ms.tgt_pltfrm:
ms.custom:
ms.assetid:
ms.search.region: Global
# ms.search.industry:
ms.author: jcart
ms.search.validFrom: 2020-10-06
ms.dyn365.ops.version: Human Resources

---

# What's new or changed in Dynamics 365 Human Resources (October 6, 2020)

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]



This topic describes features that are new, changed, or coming soon in Dynamics 365 Human Resources. For more information about our update process and schedule, see [Update process](hr-admin-setup-update-process.md).

For more information about new features and their expected general availability dates, see [Overview of Dynamics 365 Human Resources 2020 release wave 2](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/).

## In this release

This release includes the following new features and bug fixes. Changes apply to build number 8.1.3636.

### New features

The following feature is generally available with this release.

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Additional insight into leave calendars | [Provide additional insight into leave calendar views](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/provide-additional-insight-leave-calendar-views) | [View team and company calendar](hr-employee-self-service-calendar.md) |

### Bug fixes

The following bug fixes are included in this release.

>[!NOTE]
> Our goal is to get this information to you as soon as possible. There may be updates to this topic to include bug fixes that made it into the build after this topic was initially published.

| Issue number | Issue | Description |
| --- | --- | --- |
| 448806 | **Default Identification Type** exports as **RecID** in HCM parameters | This change to the Human Resources parameters entity adds an additional column that displays the **Default Identification Type**. |
| 492923 | Task recordings aren't saving in Lifecycle Services (LCS) | Task recordings can now be saved in LCS. |
| 429950 | Fixed compensation doesn't expire correctly while changing position | When changing the position of a worker on the **Transfer Worker** page, the end compensation date was set one day before the end of the position. The compensation end date is now the same as the position end date. |
| 467214 | **Salaried analytics** displays only if **Pay rate conversion name** is set to **Annual** | Salaried pay rates with a name other than **Annual** didn't show in Compensation Analytics. With this update, Compensation Analytics now uses all pay rate conversions. When running the reports by **Hourly** or **Salary**, any pay rate conversion that uses a period other than hourly are included in the **Salary** filter. Only pay rates with a period of **Hourly** are included in the **Hourly** filter. |
| 482464 | When viewing **Reviews**, the **Details** view doesn't change to grid view after you apply a filter | After applying a filter, the reviews grid displays as expected. |
| 483184 | Human Resources doesn't generate leave accruals when you select **Tier basis** as the **Adjusted start date** in the **Leave enrollment** record |The **Adjusted start date** is populated and used when generating leave accruals.  |
| 509731 | Time off request for future terminated worker causes issue if they apply for time off after termination date | Time off requests can now be submitted for employees with a future termination date as long as the request is before the termination date. |
| 510716 | Compensation Analytics includes both male and female employees for **Male average hourly pay** | In Compensation Analytics, the **Male average hourly pay** on the **Compensation Demographic Analysis** included female average pay. Now it only includes males. |
| 511348 | Benefits self-service should only show benefit plans valid from today to end of the benefit period | Expired benefit plans were displayed to employees on the **Benefits enrollment** page. This fix removes these plans. |
| 512706 | Set the following fields to read only:<ul><li>BenefitPlanEmployeeEntity</li><li>EnrollmentConfirmed</li><li>EnrollmentConfirmedBy</li><li>EnrollmentConfirmedDateTime | The **Add** and **Remove** buttons for dimension details were incorrectly enabled after the action completed. This update to the **Position Action Detail** page makes the fields uneditable after the action has completed. |

## In preview

The following new features are in preview. For more information about turning features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Human Resources app in Microsoft Teams | [Employee leave and absence experience in Microsoft Teams](/dynamics365-release-plan/2020wave1/dynamics365-human-resources/employee-leave-absence-experience-teams) | [Human Resources app in Teams](./hr-admin-teams-leave-app.md)<br>[Manage leave requests in Teams](hr-teams-leave-app.md) |
| Enhanced workflow requests and approvals | [Organization and personnel management workflow experience enhancements](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/organization-personnel-management-workflow-experience-enhancements) | [Configuration option to position Work items assigned to me list](./hr-whats-new-2020-09-03.md#configuration-option-to-position-work-items-assigned-to-me-list-477004) |
| Virtual entities in Dataverse for Human Resources | [Expand Dynamics 365 Human Resources core data in Dataverse](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/expand-dynamics-365-human-resources-core-data-common-data-service) | [Configure Dataverse virtual entities](hr-admin-integration-common-data-service-virtual-entities.md) |

## Coming soon

The following new features are scheduled for future releases:

- **Checklist entities included in Dataverse**: Checklist entities for Onboarding, Offboarding, Transfers, and Business processes will be available soon in Dataverse.

- **Benefits management reason codes**: Benefits management reason codes will soon be combined with existing reason codes in Human Resources. If you created reason codes in Benefits management that are over 15 characters, you must change the name of the reason code in the Benefits management **Reason codes** form to be 15 characters or less. After you update the name, the reason code will appear under the existing reason code form in Personnel management. This change will be available in the future and won't affect existing functionality.

- **Custom links in Manager self-service**: To support managers, we're expanding capabilities in Manager self-service. We're adding the capability to add custom links on the **My team** tab. This feature is similar to the custom links feature on the **My information tab** in employee self-service. For more information, see [Custom links in manager self-service](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/custom-links-manager-self-service).

For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2019 release wave 2](/dynamics365-release-plan/2019wave2/dynamics365-human-resources/).

## Additional resources

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2020 release wave 2](/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]