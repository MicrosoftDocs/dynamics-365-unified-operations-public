---
# required metadata

title: What's new or changed in Dynamics 365 for Talent (July 16, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 for Talent.
author: Darinkramer
manager: AnnBe
ms.date: 7/16/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
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
# "What's new or changed in Dynamics 365 for Talent (July 16, 2019)"

[!include [banner](includes/banner.md)]

This topic describes features that are either new or changed in Dynamics 365 for Talent.

## Changes in Attract
This release includes minor bug fixes for Dynamics 365 Talent: Attract.

## Changes in Onboard
This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Changes in Core HR
Changes described in this section apply to build number 8.1.2390.

### CDS Entities now supporting custom fields

| Entity                                     | Entity                           | 
| -----------------------------------------  | -------------------------------- |
|  BusinessProcessCalendar		               |  HcmJobFunction		            	|
|  BusinessProcessGroupAssignment            |  HcmJobType		                	|
|  BusinessProcessStage			                 |	HcmLanguageCode		            	|
|  BusinessProcessTemplateHeader             |  HcmPayrollCalculationFrequency	|
|  BusinessProcessTemplateTask               |  HcmPosition			                |
|  HcmBenefitOption			                     |  HcmPositionType		            	|
|  HcmBenefitType			                       |  HcmSkillType		              	|
|  HcmCompensationGrid			                 |	HcmVeteranStatus		            |
|  HcmCompensationLevel			                 |  HcmWorkCalendarHoliday	      	|
|  HcmCompensationPayFrequency		           |  HcmWorkCalendarHolidayLine    	|
|  HcmCompensationReferencePointSetup	       |  HcmWorker			                  |
|  HcmCompensationReferencePointSetupLine    |  HcmWorkerPersonalDetail		      |
|  HcmCompensationRegion		                 |  LeaveType		                  	|
|  HcmCompFixedPlanTable		                 |  OMDepartment		              	|
|  HcmEmployment			                       |  OMLegalEntity		              	|
|  HcmEthnicOrigin			                     |  PayCycle		                  	|
|  HcmFixedCompensationEvent		             |  PayPeriod	                  		|
|  HcmJob      				                       |  PayrollBenefitCalculationRate 	|
|  PayrollBenefitCalculationRateDetail       |  PayrollEarningCode		          |

### Unable to see goals and reviews in manager self-service ???????? 

This weeks changes now allow displaying and editing of goals and reviews for skip level managers in manager self-service.

### Goal form cannot be closed once user edits any goal field

This weeks release corrects an issue where the goal form does not close when selecting the close box.

### Creating new goals and saving displays error

This weeks release corrects an issue when saving goals in employee and manager self-service.

### Can't filter on in review status on the work items assigned to me page

### Missing key field in Worker bank account CDS mirror entity???

### Unable to add a field to Position Details 

With this release, custom fields are now supported on position details.
 
### Unable to set up expiring date on the earning code through data management

This weeks release includes a change to allow setting expire dates on earning codes in data management.

### New custom fields don't sync quick enough

Performance of custom field sync to CDS has been improved with this weeks release.

## In preview

### Preview features are enabled only in sandbox instances

When you provision a new instance of Talent, you can specify whether the instance type is **Production** or **Sandbox**. Instances of the **Sandbox** type allow for early testing of new features. All existing Talent instances will be updated to the **Production** instance type. If you want one of your existing instances to be updated to the **Sandbox** instance type, contact [Support](https://docs.microsoft.com/dynamics365/unified-operations/talent/talent-support) to initiate the change request.

For more information about how changes are published, see [Provision Talent](https://docs.microsoft.com/dynamics365/unified-operations/talent/provisioning-talent).

### Restrict leave types in time-off requests

Organizations can offer many different types of leave to employees. However, it might not be appropriate for employees to submit time-off requests for some leave types. Those leave types might be managed by HR instead. In this release, you can configure which leave types employees can submit time-off requests for. 

### View extended information for performance in manager self-service

A new option will let managers view the performance of both their direct reports and their extended reports. Currently, line managers can assign and update performance goals and issue new reviews, which their employees co-manage. In addition, direct managers and their employees can maintain and update performance journals to help ensure that the performance review process goes smoothly. When this change is implemented, managers will be able to view and maintain performance-related information for their extended reports in addition to their direct reports. 
