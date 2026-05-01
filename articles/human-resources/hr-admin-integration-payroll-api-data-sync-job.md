---
# required metadata

title: Schedule Payroll Data Sync Job
description: This article describes the batch job required to sync data for payroll entities.
author: avanish2821
ms.date: 03/25/2026
ms.topic: concept-article
# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2021-02-03
ms.dyn365.ops.version: Human Resources
---

# Schedule Payroll Data sync job

## Overview
This document describes the steps to schedule a **Payroll data sync batch job** in **Dynamics 365 Human Resources**, including how to configure recurrence and verify the batch job execution.


## Steps
1. In Microsoft Dynamics 365 Human Resources, click **Modules**.
2. Select the **Payroll** module.
3. Click **Schedule payroll data sync**.
4. Select the **Entity Name** from the dropdown.
- To identify the correct entity name, refer to the table in the [Entity Names](#entity-names-to-schedule-data-sync-batch-job) section below.
5. Enable **Run in the background**.
6. Expand the section and configure the following:
  - **Batch processing**: Yes
  - **Task description**: Payroll data synchronization
  - **Batch group**: (select as applicable)
  - **Private**: No
  - **Critical job**: No
  - **Monitoring category**: Undefined
7. Define the recurrence for the data sync job.
- Example configuration:
  - **Recurrence pattern**: Hours
  - **Repeat every**: 8 hours
  - **Start date/time**: As required
  - **End by**: Set an appropriate end date
8. Click **OK** to schedule the batch job for payroll data synchronization.


### Verify the batch job
To verify the batch job, follow these steps:
1. Go to **System administration** > **Inquiries** > **Batch jobs**.
2. Filter the batch jobs based on **Job description**.
3. Use the contains filter and provide 'payroll' text.
4. Verify that the payroll data sync job appears in the list.


## Entity names to schedule data sync batch job

| Entity name for batch job | Corresponding PayIntV1 change tracking table |
|-------------------------------|------------------------------------------|
| HcmWorkerEntity | PayIntV1Worker |
| HcmWorkerContactEntity | PayIntV1WorkerContact |
| HcmEmploymentDetailEntity | PayIntV2EmploymentDetail |
| HcmPositionEntity | PayIntV1HcmPosition |
| PayrollEmployeeV2Entity | PayIntV1PayrollEmployee |
| PayrollBankAccountDisbursementEntity | PayIntV1BankAccountDisbursement |
| PayrollWorkerAddressCurrentEntity | PayIntV1PayrollWorkerCurrentAddress |
| HcmPositionUnionAgreementEntity | PayIntV1PositionUnionAgreement |
| OMLegalEntity | PayIntV1OMLegal |
| HcmPositionWorkerAssignmentEntity | PayIntV1HcmPositionWorkerAssignment |
| HcmIdentificationTypeEntity | PayIntV1HcmIdentificationType |
| HcmPersonIdentificationNumberEntity | PayIntV1HcmPersonIdentificationNumber |
| PayrollPositionDetailsEntity | PayIntV1PayrollPositionDetails |
| HcmCompFixedEmplEntity | PayIntV1HcmCompFixedEmpl |
| HcmEmploymentEmployeeEntity | PayIntV1HcmEmploymentEmployee |
| HcmJobEntity | PayIntV1HcmJob |
| HcmPositionDefaultDimensionEntity | PayIntV1HcmPositionDefaultDimension |
| HcmWorkerBaseEntity | PayIntV2HcmWorkerBase |
| PayrollPositionJobEntity | PayIntV1PayrollPositionJob |
| HcmEmploymentV2Entity | PayIntV1HcmEmploymentV2 |
| HcmEmployeeV2Entity | PayIntV2HcmEmployeeV2 |
| HcmWorkerBankAccountEntity | PayIntV1WorkerBankAccount |
| HcmVariableCompensationEnrollmentV2Entity | PayIntV1HcmVariableCompensationEnrollment |
| HcmVariableCompensationAwardEntity | PayIntV1HcmVariableCompensationAward |
| HcmWorkerPostalAddressEntity | PayIntV1HcmWorkerPostalAddress |
| HcmEmploymentTermEntity | PayIntV1HcmEmploymentTerm |
| HcmPositionTimelineEntity | PayIntV1HcmPositionTimeline |
| HcmVariableCompensationEnrollmentPositionEntity |PayIntV2HcmVariableCompensationEnrollmentPosition |


#### Legal Entity specific payroll integration entities

The following entities contain legal entity specific data. Since batch jobs execute within a specific legal entity context, a separate batch job must be scheduled for each legal entity.

- PayIntV1HcmCompFixedEmplEntity  
- PayIntV1HcmPositionDefaultDimensionEntity  
- PayIntV1HcmVariableCompensationAwardEntity  
- PayIntV1HcmVariableCompensationEnrollmentEntity  
- PayIntV1PayrollEmployeeEntity  
- PayIntV2HcmVariableCompensationEnrollmentPositionEntity  

