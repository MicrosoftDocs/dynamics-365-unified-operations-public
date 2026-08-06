---
title: Leave and absence integration with Project operations
description: Leave and absence integration with Project operations automatically syncs approved leave from Dynamics 365 Human Resources into time entry.
author: twheeloc
ms.author: twheeloc
ms.reviewer: twheeloc
ms.date: 07/30/2026
ms.topic: article
---

# Leave and absence integration with Project operations time entry overview

Leave and absence integration with Project operations time entry is a Dynamics 365 Human Resources capability that automatically synchronizes approved leave information from Dynamics 365 Human Resources into Project operations time entry. It uses Microsoft Dataverse and Dual-write synchronization technologies to create a corresponding approved time-off entry within the time entry experience whenever a leave request is approved.

Organizations depend on accurate employee availability information to effectively manage project staffing, resource allocation, and time reporting. Traditionally, approved leave requests in Dynamics 365 Human Resources and time reporting in Project operations have resided in separate experiences, creating manual effort and potential inconsistencies. This integration bridges that gap and provides a unified experience for employees, project managers, and resource managers.

Leave and absence remains the system of record for employee leave, while Project operations consumes approved leave information to support accurate time reporting and resource planning.

## Business challenge

Before this integration existed, organizations encountered several gaps between human resources and project management processes:

- Approved leave requests weren't automatically reflected in Project operations time entry.
- Project resources needed to manually track approved absences while reporting time.
- Project managers had limited visibility into planned employee absences when planning project work.
- Organizations faced risks of inaccurate resource planning, scheduling conflicts, and time reporting discrepancies.

## Key capabilities

The integration delivers automated synchronization, in-context visibility, and improved planning data across both solutions.

### Automatic leave synchronization

When an employee's leave request is approved:

- The system automatically synchronizes leave information to Project operations.
- Approved leave appears directly within the time entry experience.
- The system generates corresponding time-off records without manual intervention.
- Resource calendars automatically update to reflect employee availability.

### Visibility during time reporting

Employees can:

- View approved leave directly within time entry.
- Understand available working hours before submitting time.
- Avoid manual reconciliation between leave requests and project time reporting.

### Enhanced resource planning

Project managers and resource managers gain:

- Better visibility into upcoming employee absences.
- Improved resource allocation decisions.
- More accurate project scheduling and forecasting.
- Reduced risk of assigning work to unavailable resources.

### Automatic handling of leave changes

If leave is modified or cancelled, the integration automatically updates or removes the corresponding time-off entries to ensure consistency between systems.

## User experience

The integration preserves existing workflows in both applications while removing duplicate effort.

### Employee experience

Employees continue to submit leave requests through Dynamics 365 Human Resources using existing leave approval workflows. Once approved, leave information automatically appears in Project operations time entry.

Employees get a more streamlined experience because approved leave already shows when they enter project time, reducing duplicate effort and improving reporting accuracy.

### Project manager experience

Project managers benefit from:

- Improved visibility into employee availability.
- Better planning for project assignments.
- More informed approval decisions.
- Reduced scheduling conflicts caused by overlooked absences.

### Business benefits

The synchronized view across solutions produces measurable operational value.

- **Increased accuracy**: Eliminates discrepancies between leave records and project time reporting by maintaining a synchronized view across solutions.
- **Reduced administrative effort**: Removes manual updates and duplicate data entry across Human Resources and Project operations systems.
- **Improved resource utilization**: Provides project managers with accurate availability information, enabling more effective staffing decisions.
- **Better employee experience**: Employees no longer need to manually reconcile approved leave with project time reporting activities.
- **Operational efficiency**: Automated synchronization reduces errors, improves compliance with approved leave schedules, and supports more reliable project delivery.

### Process flow

The end-to-end flow of leave information between the two systems follows this sequence:

1. Employee submits a leave request in Dynamics 365 Human Resources.
1. Manager approves the leave request.
1. Approved leave information synchronizes to Project operations.
1. Time-off entries are automatically created and reflected in employee resource calendars.
1. Employees and managers can view approved leave within the time entry experience.
1. Any future leave updates or cancellations are automatically synchronized across systems.
