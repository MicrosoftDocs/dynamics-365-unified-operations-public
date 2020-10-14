---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources (October 6, 2020)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Human Resources for October 6, 2020.
author: jcart1106
manager: tfehr
ms.date: 10/06/2020
ms.topic: article
ms.prod:
ms.service: dynamics-365-talent
ms.technology:

# optional metadata

ms.search.form:
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: anbichse
ms.search.scope: Human Resources
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

This topic describes features that are new, changed, or coming soon in Dynamics 365 Human Resources.For more information about our update process and schedule, see [Update process](hr-admin-setup-update-process.md).

For more information about new features and their expected general availability dates, see [Overview of Dynamics 365 Human Resources 2020 release wave 2](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/dynamics365-human-resources/).

## In this release

This release includes the following new features and bug fixes. Changes apply to build number 8.1.3636.

### New features

The following feature is generally available with this release.

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Additional insight into leave calendars | [Saved views - general availability](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/finance-operations/finance-operations-crossapp-capabilities/saved-views--general-availability) | [View team and company calendar](https://docs.microsoft.com/en-us/dynamics365/human-resources/hr-employee-self-service-calendar) |

### Bug fixes

The following bug fixes are included in this release.

>[!NOTE]
>Our goal is to get you this information as soon as possible. We may update this topic to include bug fixes that made it into the build after this topic was initially published.

| Issue number | Issue | Description |
| --- | --- | --- |
| 394249 | Regular translation checkins for supported HCM languages. |  |
| 448806 | **Default Identification Type** exports as **RecID** in HCM Parameters. | This change to the Human Resources Parameters entity adds an additional column that displays the **Default Identification Type**. |
| 492923 | Invalid certificate thumbprint causes Lifecycle Services (LCS) SysTaskRecorder not to work. |  |
| 429950 | Fixed compensation doesn't expire correctly while changing position. | When changing the position of a worker in the **Transfer Worker** form, the end compensation date was set one day before the end of the position. The compensation end date is now the same as the position end date. |
| 467214 | **Salaried analytics** displays only if **Pay rate conversion name** is set to **Annual**. | Salaried pay rates with a name other than **Annual** didn't show in Compensation Analytics. With this update, Compensation Analytics now uses all pay rate conversions. When running the reports by **Hourly** or **Salary**, any pay rate conversion that uses a period other than hourly are included in the **Salary** filter. Only pay rates with a period of **Hourly** are included in the **Hourly** filter. |
| 482464 | The **Details** view doesn't change to grid view after you apply a filter. |  |
| 483184 | Human Resources doesn't generate leave accruals when you select **Tier basis** as the **Adjusted start date** in the **Leave enrollment** record. |  |
| 506949 | **PositionActionDetail** default dimension. |  |
| 507333 | Common Data Service bridge causes a null ref exception on AOS startup. |  |
| 509731 | Leave request for future terminated worker causes issue if they apply for time off after termination date. |  |
| 510716 | Compensation Analytics includes both male and female employees for **Male average hourly pay**. | In Compensation Analytics, the **Male average hourly pay** on the **Compensation Demographic Analysis** included female average pay. Now it only includes males. |
| 511348 | Benefits self-service should only show benefit plans valid from today to end of the benefit period. | Expired benefit plans were displayed to employees in the benefits enrollment page. This fix removes these plans. |
| 512706 | Set the following fields to read only:<br>- **BenefitPlanEmployeeEntity**<br>- **EnrollmentConfirmed**<br>- **EnrollmentConfirmedBy**<br>- **EnrollmentConfirmedDateTime** | The **Add** and **Remove** buttons for dimension details were incorrectly enabled after the action completed. This update to the **Position Action Detail** form makes the fields uneditable once the action has completed. |

## In preview

The following new features are in preview. For more information about turning features on or off, see [Manage features](hr-admin-manage-features.md).

| Feature | Release plan | Documentation |
| --- | --- | --- |
| Human Resources app in Microsoft Teams | [Employee leave and absence experience in Microsoft Teams](https://docs.microsoft.com/dynamics365-release-plan/2020wave1/dynamics365-human-resources/employee-leave-absence-experience-teams) | [Human Resources app in Teams](https://go.microsoft.com/fwlink/?linkid=2127841)<br>[Manage leave requests in Teams](hr-teams-leave-app.md) |
| Enhanced workflow requests and approvals | [Organization and personnel management workflow experience enhancements](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/organization-personnel-management-workflow-experience-enhancements) | [Configuration option to position Work items assigned to me list](https://docs.microsoft.com/dynamics365/human-resources/hr-whats-new-2020-09-03#configuration-option-to-position-work-items-assigned-to-me-list-477004) |
| Virtual entities in Common Data Service for Human Resources | [Expand Dynamics 365 Human Resources core data in Common Data Service](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/expand-dynamics-365-human-resources-core-data-common-data-service) | [Configure Common Data Service virtual entities](https://docs.microsoft.com/en-us/dynamics365/human-resources/hr-admin-integration-common-data-service-virtual-entities) |

## Coming soon

The following new features are scheduled for future releases:

- **Checklist entities included in Common Data Service**: Checklist entities for Onboarding, Offboarding, Transfers, and Business processes will be available soon in Common Data Service.

- **Benefits management reason codes**: Benefits management reason codes will soon be combined with existing reason codes in Human Resources. If you created reason codes in Benefits management that are over 15 characters, you must change the name of the reason code in the Benefits management **Reason codes** form to be 15 characters or less. After you update the name, the reason code will appear under the existing reason code form in Personnel management. This change will be available in the future and won't affect existing functionality.

- **Custom links in Manager self-service**: To support managers, we're expanding capabilities in Manager self-service. We're adding the capability to add custom links on the My team tab. This feature is similar to the custom links feature we provide in the **My information tab** in employee self-service. For more information, see [Custom links in manager self-service](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/human-resources/dynamics365-human-resources/custom-links-manager-self-service).

For a complete list of planned features and their scheduled releases, see [Overview of Dynamics 365 Human Resources 2019 release wave 2](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/dynamics365-human-resources/).

## See also

[What's new or changed in Human Resources](hr-admin-whats-new.md)</br>
[Overview of Dynamics 365 Human Resources 2020 release wave 2](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/dynamics365-human-resources/)</br>
[Update process](hr-admin-setup-update-process.md)</br>
[Manage features](hr-admin-manage-features.md)