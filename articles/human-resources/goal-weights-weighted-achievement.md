---
title: Manage goal weights and weighted achievement
description: Use goal weights to express the relative importance of goals and calculate how much each goal contributes to a worker's overall achievement.
author: twheeloc
ms.author: twheeloc
ms.reviewer: twheeloc
ms.date: 10/13/2026
ms.topic: concept-article
---

# Manage goal weights and weighted achievement

This article describes how to use goal weights to express the relative importance of goals and calculate how much each goal contributes to a worker's overall achievement.

This feature is available in Dynamics 365 Finance version 10.0.50 and is enabled in Feature management.

## Why use goal weights?

Not every goal contributes equally to performance. Without weighting, a simple average can give a low-priority goal the same influence as a business-critical goal.

Use the **Goal weights management** feature to:

- Define a default weight and optional minimum and maximum boundaries on a goal template.

- Copy that configuration to new employee goals created from the template.

- Let employees propose weights in draft and managers confirm or adjust them within the configured boundaries.

- Require the applicable goal weights in a weighted review to total less than or equal to 100% before the review moves to In progress.

- Show each goal's weighted contribution and an overall weighted achievement value.

> [!NOTE]
> Weighted achievement is an additional performance indicator. It doesn't automatically determine ratings, compensation, payroll, promotion, succession, or any other employment outcome.

### Where the feature appears

| Area | What's introduced | Who uses it |
| ---- | ---- | ---- |
| Feature management workspace | The **Goal weights management** feature. | System administrator |
| Goal templates | **Default goal weight**, **Minimum goal weight**, and **Maximum goal weight**. | HR administrator |
| Employee goal | **Actual goal weight**, copied from the template default when available and editable while the lifecycle permits. | Employee, line manager, or authorized HR administrator |
| Goal setup | A read-only, live **Total goal weight** indicator and a warning when the total isn't 100%. | Employee, line manager, or authorized HR administrator |
| Performance review | Goal completion, actual weight, weighted goal percentage, total goal weight, and overall weighted goal achievement. | Employee, line manager, or authorized HR administrator |

#### Prerequisites

- Your environment must be on Dynamics 365 Finance version 10.0.50 or later.

- A system administrator must enable the feature.

- The person who configures template values must have permission to maintain goal templates.

- Managers and employees must have access to the goals and reviews where they enter or view weights.

#### Enable the feature

To enable the **Goal weights management** feature, follow these steps:

1. Open the **Feature management** workspace.

1. On the **All** tab, search for **Goal weights management**.

1. Select the feature, and then select **Enable now**. Alternatively, use the standard Feature management scheduling options to enable it later.

1. Refresh the browser session if the new controls don't appear immediately.

Enabling the feature doesn't assign weights to existing employee goals and doesn't recalculate existing reviews. If no weights are configured, existing behavior and calculations continue.

#### Configure goal weight defaults and boundaries

1. Open the page where your organization maintains goal templates.

1. Open an existing goal template, or create a template.

1. Optionally enter a **Default goal weight**.

1. Optionally enter a **Minimum goal weight** and a **Maximum goal weight**.

1. Save the goal template.

### Field behavior

| **Field** | Purpose | Rules |
| ---- | ---- | ---- |
| **Default goal weight** | Initial value copied to a new employee goal's **Actual goal weight**. | Optional. If you configure minimum or maximum values, the default must be within that inclusive range. |
| **Minimum goal weight** | Lowest **Actual goal weight** that a user can enter for a goal created from the template. | Optional. If omitted, the effective minimum is 0% for range validation. |
| **Maximum goal weight** | Highest **Actual goal weight** that a user can enter for a goal created from the template. | Optional. If omitted, the effective maximum is 100% for range validation. |
| **Actual goal weight** | The employee goal's authoritative weight. Calculations use this value. | Must be within the goal's boundaries. In a weighted review, it must be greater than 0%. |

All weight values are percentages from 0 through 100 and support up to two decimal places. Extra decimal places are rounded by the standard Finance and Operations numeric-field behavior.

For example, if a template has a default of 40%, a minimum of 30%, and a maximum of 50%, a new employee goal starts with an **Actual goal weight** of 40%. A user can change the value to any value from 30% through 50%, inclusive.

#### How values are copied to employee goals

When you create an employee goal from a goal template, the template's default, minimum, and maximum values are copied to the goal. The copy happens once, when you create the goal.

- The **Actual goal weight** starts at the template's default, if you configure a default.

- The copied minimum and maximum become the employee goal's boundaries.

- Changing the template later affects only goals created after the change.

- Existing employee goals, in-progress reviews, completed reviews, and archived reviews aren't updated or recalculated.

#### Set and approve actual goal weights

The **Actual goal weight** is the only weight used in validation and calculation. There's no separate review-level weight.

| **Review state** | Employee | Line manager | Authorized HR administrator |
| ---- | ---- | ---- | ---- |
| **Not started / draft** | Can edit weights on own goals | Can edit | Can edit |
| **In progress, before manager approval** | Read-only | Can edit and approve | Can edit where authorized |
| **In progress, after manager approval** | Read-only | Read-only | Read-only |
| **Completed** | Read-only | Read-only | Read-only |
| **Returned to draft** | Can edit weights on own goals | Can edit | Can edit |

The employee can propose values while the review is in draft. Submission to the manager ends the employee's editing window. The manager can then confirm or adjust the weights before approving them. Manager approval is the final lock for all roles while the review remains in that state.

#### Balance the total goal weight

The **Total goal weight** is the sum of the **Actual goal weights** for all applicable weighted goals in the review.

- The total is read-only and updates as weights change.

- While the review remains in **Not started** or **Draft**, a total other than 100% shows a warning but doesn't block editing.

- The transition from **Not started** to **In progress** is blocked unless the total is exactly 100%.

- Values such as 99.99% and 100.01% don't satisfy the rule.

- The system doesn't normalize, redistribute, or automatically change any weight.

- A review with no weighted goals continues to use the existing unweighted behavior.

> [!IMPORTANT]
> In a weighted review, every applicable goal must have a weight greater than 0%, and the weights must total exactly 100%. A mixture of weighted and unweighted goals is blocked when the review moves to In progress.

#### Understand weighted achievement

The system calculates each goal's contribution by scaling its completion percentage by its **Actual goal weight**.

**Weighted goal percentage** = Goal completion percentage × **Actual goal weight** ÷ 100

The overall result is the sum of the individual contributions. The contributions aren't averaged again.

Overall weighted goal achievement = Sum of all applicable weighted goal percentages

#### Example

| Goal | **Actual goal weight** | Completion | **Weighted goal percentage** |
| ---- | ---- | ---- | ---- |
| Goal 1 | 40% | 80% | 32% |
| Goal 2 | 30% | 100% | 30% |
| Goal 3 | 20% | 60% | 12% |
| Goal 4 | 10% | 100% | 10% |
| **Total** | **100%** | | **84%** |

The same completion values produce 85% as a simple unweighted average. The weighted result is 84% because the least-complete goal has the greatest weight.

### Overachievement

Completion and calculated achievement can exceed 100%. The system doesn't cap weighted contributions or overall weighted achievement.

| Goal    | Weight | Completion | Contribution |
|-------------|------------|----------------|------------------|
| Goal A      | 20%        | 100%           | 20%              |
| Goal B      | 80%        | 200%           | 160%             |
| **Overall** | **100%**   |                | **180%**         |

#### Calculation and display behavior

| Feature and data state | Calculation used |
| ---- | ---- |
| Feature enabled and weights configured on the goals | Weighted calculation |
| Feature enabled and no weights configured | Existing unweighted calculation |
| Feature disabled | Existing unweighted calculation, even if stored weights exist |

**Weighted goal percentage** and **Overall weighted goal achievement** recalculate automatically after a successful change to completion or **Actual goal weight**. There's no manual recalculate action.

The performance review shows these five values together so users can reproduce the calculation:

- Goal completion percentage
- Actual goal weight
- Weighted goal percentage for each applicable goal
- Total goal weight
- Overall weighted goal achievement

#### Security and access

- The feature uses the existing permissions on goal templates, employee goals, and reviews.
- No new security role, duty, privilege, or field-level security is introduced.
- Employees can act only on their own goals during the permitted lifecycle state.
- Managers can act only on workers within their existing record scope.
- Calculated values are read-only for every role.
- If a user can't see every goal in the applicable set, the system withholds the total instead of showing a partial value and that user can't advance the review.

#### Existing data and feature disablement

- Enabling the feature doesn't assign a zero weight or any other weight to an existing goal.
- An undefined weight means “unweighted.” It isn't the same as an explicit 0% weight.
- In-progress, completed, and archived reviews aren't migrated or recalculated.
- Disabling the feature restores the existing unweighted calculation. Stored weight configuration is retained but remains dormant.
- Re-enabling the feature restores weighted behavior from retained values where applicable.

#### Reporting and integration considerations

Supported interfaces expose the following values where applicable:

- Default, minimum, maximum, and Actual goal weight
- Weighted goal percentage and Overall weighted goal achievement
- Source goal template and source version

Calculated values are read-only. Imports are subject to the same range, boundary, lifecycle, and total validation as the interactive experience. Completed-review reporting uses the values recorded on the completed review, not the current goal template configuration.

#### Limitations

- Template values don't have to total 100%. The 100% rule applies only to a worker's applicable goals.
- The system doesn't automatically normalize or redistribute weights.
- Weighted achievement doesn't drive ratings or downstream employment decisions.
- Changing a goal template doesn't update goals or reviews that already exist.
- There is no manual recalculation action.

#### Troubleshooting

| Issue | What to check |
| ---- | ---- |
| Weight controls aren't visible. | Confirm that the **Goal weights management** feature is enabled and that at least one weight value is configured where required. If the organization doesn't configure any weights, the employee and manager experience remains unchanged. |
| A weight can't be saved. | Confirm that the value is numeric, from 0% through 100%, within the goal's copied minimum and maximum, and editable in the current review state. |
| The review can't move to In progress. | Confirm that every applicable goal has a weight greater than 0% and that the Total Goal Weight is exactly 100%. |
| A template change isn't shown on an existing goal. | This change is expected. Template changes apply only to goals created after the change. |
| The displayed result is above 100%. | This result can be valid when one or more goals exceed 100% completion. Derived achievement values aren't capped. |
| The total isn't shown. | The user might not have access to every goal in the applicable set. A partial total is withheld to prevent misleading results or unintended disclosure. |

## Related content

- [Performance management overview](hr-develop-performance-management-overview.md)
- [Create goals](hr-develop-create-goal.md)
- [Create performance reviews](hr-develop-create-performance-review.md)
