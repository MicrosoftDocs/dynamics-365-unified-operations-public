---
title: Configure job-based filtering for performance goals
description: Job-based filtering in Dynamics 365 Human Resources links goal templates and groups to specific jobs, so managers see only relevant workers. 
ms.date: 10/23/2026
ms.topic: concept-article
author: twheeloc
ms.author: twheeloc
---

# Configure job-based filtering for performance goals

Use job-based filtering to associate goal templates and goal groups with one or more jobs. When a manager or HR user assigns goals, the selected template or group narrows the worker list to people whose active job matches the configured jobs.

The **Job based filtering** feature is available in Dynamics 365 Finance version 10.0.50.

## Why use job-based filtering?

Organizations often define different performance goals for different job roles. Without multi-job filtering, administrators might duplicate goal templates or managers might see workers who aren't relevant to the goal content.

By using this feature, you can:

- Associate zero, one, or many jobs with a goal template.
- Associate zero, one, or many jobs with a goal group independently of its templates.
- Reduce the worker list during assignment to workers with a matching active job.
- Continue to use bulk assignment for the workers in the filtered list.

> [!NOTE]
> Job-based filtering isn't a security feature and doesn't assign goals automatically. It only narrows a list that the user is already authorized to view. The user must still select the workers and complete the existing assignment process.

### Where the feature appears

| Area | What's introduced | Who uses it |
| ---- | ---- | ---- |
| Feature management workspace | The **Job based filter (Multiselect)** feature entry. | System administrator |
| Goal templates | A multiselect **Job** control for associating a template with multiple jobs. | HR administrator |
| Goal groups | The existing single-job criterion is presented as a multiselect **Job** control. | HR administrator |
| Add from template | The worker list is filtered by the jobs configured on the selected goal template. | Line manager or other authorized assigning user |
| Add from group | The worker list is filtered by the jobs configured on the selected goal group. | Line manager or other authorized assigning user |

### Prerequisites

- Your environment must be on Dynamics 365 Finance version 10.0.50 or later.
- A system administrator must enable the feature.
- The person who configures job criteria must already have permission to maintain goal templates or goal groups.
- Workers who should match a filtered source must have a valid active job on the date when the worker list is generated.

#### Enable the feature

When you enable the **Job based filter** feature, new configuration controls become available. This feature doesn't create mappings, change existing employee goals or reviews, or grant any additional access.

1. Open the **Feature management** workspace.
1. On the **All** tab, search for **Job based filter (Multiselect)**.
1. Select the feature, and then select **Enable now**. Alternatively, use the standard Feature management scheduling options to enable it later.
1. Refresh the browser session if the new controls don't appear immediately.

### Configure jobs on a goal template

When you configure jobs on a goal template, you can select zero, one, or many jobs. If you clear the final job, the template becomes unfiltered and is available for all otherwise eligible workers.

1. Open the page where your organization maintains goal templates.
1. Open an existing goal template, or create a template.
1. In the **Job** control, select one or more valid jobs.
1. Save the goal template.

#### Configure jobs on a goal group

Job criteria on a goal group are independent of the criteria on the goal templates that belong to the group. The group doesn't inherit jobs from its templates, and templates don't inherit jobs from the group.

1. Open the page where your organization maintains goal groups.
1. Open an existing goal group, or create a group.
1. In the **Job** control, select one or more valid jobs.
1. Save the goal group.

### Add templates to a goal group

When you add a goal template to a goal group, the system compares the job criteria on both records:

- A template with no configured jobs aligns with every goal group.
- A template aligns when at least one template job matches at least one group job.
- If the criteria don't align, the system displays a non-blocking warning. You can still add the template if the combination is intentional.

The system never removes templates from a goal group automatically when job criteria change.

## Assign goals by using a filtered worker list

### Add from template

1. Start the existing **Add from template** process.
1. Select a goal template.
1. The worker list refreshes and includes authorized workers whose active job matches at least one job on the template.
1. Select one or more workers and complete the existing assignment process.

### Add from group

1. Start the existing **Add from group** process.
1. Select a goal group.
1. The worker list refreshes and includes authorized workers whose active job matches at least one job on the group.
1. Select one or more workers and complete the existing assignment process.

Multiple jobs use **OR** logic. For example, if Jobs A, B, and C are selected, the list includes otherwise eligible workers whose active job is A, B, or C. The order of the jobs doesn't create a priority.

#### Understand filtering behavior

| Situation | Result |
| ---- | ---- |
| No job is configured on the selected template or group | No job filter is applied. The existing authorized worker list is shown. |
| One or more jobs are configured | The authorized worker list is narrowed to workers whose valid active job matches any configured job. |
| A worker has no valid active job | The worker doesn't appear for a filtered source but remains available for an unfiltered source. |
| A worker changes jobs | Future worker lists use the new active job. Existing assigned goals and reviews aren't changed. |
| A configured job expires or becomes invalid | The invalid job doesn't contributes matches. Other valid job mappings continue to work. |
| No authorized worker matches | The existing empty-list experience is shown. No assignment occurs. |

#### Security and access

Existing security is evaluated before the job filter. This evaluation includes roles, duties, privileges, legal-entity scope, manager hierarchy, employment status, workflow state, and record status.

- A job match never makes an unauthorized worker visible.
- Feature enablement doesn't grant goal template, goal group, or worker access.
- You can select only jobs that you are authorized to see as new configuration.
- The feature introduces no new security role, duty, or privilege.

#### Upgrade and integration considerations

Goal groups previously supported a single job value. During upgrade, the existing value is copied to the new multiselect representation. The previous single-select field is retained for compatibility.

If you have reports, integrations, workflows, or validations that use the previous goal group job field, assess them and move to the new multiselect representation. Supported data entities expose the multiselect configuration for goal templates and goal groups.

Don't interpret an empty multiselect job configuration as “no workers.” It means that no job filter is applied.

### Limitations

- Job criteria are available only on goal templates and goal groups.
- Job criteria aren't added to goal categories, review types, review templates, performance periods, measurements, skills, certificates, tests, degrees, education disciplines, or other competency setup records.
- The criteria is **Job**, not position and not a security role.
- Existing goals aren't reassigned or deleted when a worker's job changes.
- Goals aren't automatically assigned to matching workers.

#### Troubleshooting

| Symptom | What to check |
| ---- | ---- |
| The Job control isn't visible. | Confirm that **Job based filter (Multiselect)** is enabled and that you have existing maintenance access to the record. |
| An expected worker isn't listed. | Confirm the worker is already in your authorized scope and has a valid active job that matches one of the configured jobs. |
| The worker list is empty. | Confirm that at least one authorized worker has a matching active job. An empty list is a valid result. |
| A job can't be saved. | The job might have expired, been retired, deleted, or become unavailable to your user. Remove or replace it and save again. |
| A warning appears when adding a template to a group. | The template and group job criteria don't overlap. Review the combination, and continue only if it's intentional. |

#### Related content

- [Performance management overview](hr-develop-performance-management-overview.md)
- [Create goals](hr-develop-create-goal.md)
