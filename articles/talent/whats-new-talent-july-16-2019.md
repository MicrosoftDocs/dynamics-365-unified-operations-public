---
# required metadata

title: What's new or changed in Dynamics 365 for Talent (July 16, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 for Talent.
author: Darinkramer
manager: AnnBe
ms.date: 07/16/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: andreabichsel
ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2019-07-16
ms.dyn365.ops.version: Talent

---
# What's new or changed in Dynamics 365 for Talent (July 16, 2019)

[!include [banner](includes/banner.md)]

This topic describes features that are either new or changed in Microsoft Dynamics 365 for Talent.

## Changes in Attract
This release includes minor bug fixes for Dynamics 365 Talent: Attract.

## Changes in Onboard
This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Changes in Core HR
Changes described in this section apply to build number 8.1.2390.

### Common Data Service entities that now support custom fields

- BusinessProcessCalendar		              
- BusinessProcessGroupAssignment         
- BusinessProcessStage			                
- BusinessProcessTemplateHeader          
- BusinessProcessTemplateTask            
- HcmBenefitOption			                    
- HcmBenefitType			                      
- HcmCompensationGrid			                 
- HcmCompensationLevel			                
- HcmCompensationPayFrequency		          
- HcmCompensationReferencePointSetup	    
- HcmCompensationReferencePointSetupLine 
- HcmCompensationRegion		                
- HcmCompFixedPlanTable		                
- HcmEmployment			                       
- HcmEthnicOrigin			                     
- HcmFixedCompensationEvent		            
- HcmJob      				                       
- HcmJobFunction
- HcmJobType
- HcmLanguageCode
- HcmPayrollCalculationFrequency
- HcmPosition
- HcmPositionType
- HcmSkillType
- HcmVeteranStatus
- HcmWorkCalendarHoliday
- HcmWorkCalendarHolidayLine
- HcmWorker
- HcmWorkerPersonalDetail
- LeaveType
- OMDepartment
- OMLegalEntity
- PayCycle
- PayPeriod
- PayrollBenefitCalculationRatePayrollBenefitCalculationRateDetail
- PayrollEarningCode

### Unable to see goals and reviews in manager self-service

This week's changes now allow displaying and editing of goals and reviews for skip-level managers in manager self-service.

### Goal form cannot be closed after a user edits any goal field

This release corrects an issue where the goal form does not close when selecting **Close**.

### Creating new goals and saving displays error

This release corrects an issue when saving goals in employee and manager self-service.

### Unable to add a field to position details 

With this release, custom fields are now supported on position details.
 
### Unable to set up expiring date on the earning code through data management

Changes now allow you to set expiration dates on earning codes in data management.

### New custom fields don't sync quickly enough

Performance of custom field sync to Common Data Service has been improved with this week's release.

## In preview

### Preview features are enabled only in sandbox instances

When you provision a new instance of Talent, you can specify whether the instance type is **Production** or **Sandbox**. Instances of the **Sandbox** type allow for early testing of new features. All existing Talent instances will be updated to the **Production** instance type. If you want one of your existing instances to be updated to the **Sandbox** instance type, contact [Support](https://docs.microsoft.com/dynamics365/unified-operations/talent/talent-support) to initiate the change request.

For more information about how changes are published, see [Provision Talent](https://docs.microsoft.com/dynamics365/unified-operations/talent/provisioning-talent).

### Restrict leave types in time-off requests

Organizations can offer many different types of leave to employees. However, it might not be appropriate for employees to submit time-off requests for some leave types. Those leave types might be managed by HR instead. In this release, you can configure which leave types employees can submit time-off requests for. 

### View performance information for direct and extended reports in manager self-service

A new option will let managers view the performance of both their direct reports and their extended reports. Currently, line managers can assign and update performance goals and issue new reviews. In addition, direct managers and their employees can maintain and update performance journals to help ensure that the performance review process goes smoothly. When this change is implemented, managers will be able to view and maintain performance-related information for their extended reports in addition to their direct reports.
