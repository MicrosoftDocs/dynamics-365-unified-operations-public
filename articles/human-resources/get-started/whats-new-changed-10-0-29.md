---
# required metadata

title: What's new or changed in Dynamics 365 Human Resources 10.0.29 (August 2022)
description: This article describes features that are either new or changed in the Microsoft Dynamics 365 Human Resources version 10.0.29 preview release.
author: twheeloc
ms.date: 08/01/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2022-04-22 
ms.dyn365.ops.version: 10.0.29

---

# What's new or changed in Dynamics 365 Human Resources 10.0.29 (September 2022)

[!include [banner](../../includes/preview-banner.md)]

This article lists features that are new or changed for Microsoft Dynamics 365 Human Resources version 10.0.29. This version has a build number of 10.0.xxxx and is 
available on the following schedule:

- **Preview of release:** August 2022
- **General availability of release (self-update):** September 2022
- **General availability of release (auto-update):** October 2022

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that made it into the build after this 
article was initially published.

| Feature name | Overview | Release status |
|----|----|----|
|Specify location owner| This feature allows system administrators to specify the owner of a location (address).|Default |
|Benefits notification| This preview feature provides the ability to send email notifications and reminders to the employees in the new hire enrollment, open enrollment, and qualifying life event scenarios. It allows you to create and set multiple email templates, as needed for specific scenarios, and send the notifications via benefits workspace and the worker benefits form. You can also track the notifications/reminders history.| Preview|

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance).

| Feature name | More information |
|--------------|------------------|

|Task management| Additional entities have been created to support notification options via dataverse.  HCMProcessTaskAssignment contains the assignment type, legal entity, assigned worker name, assigned worker personnel number, and assigned worker primary email address. All business process types are included in the single entity (Onboarding, Offboarding, and Transition).  If the task has been assigned to a group, each member of the group will be a line in the entity. The demo data for the Task Management Calendar has been updated through 2030. |
|Security configuration|The following self-service roles have been added to security configuration, which map to the stand-alone HR self-service roles. 
Self-service manager
Self-service employee
Self-service contractor 
The self-service roles do NOT include time sheet entry or expense, as access to those areas requires Team Member licensing.  The roles listed above should be used for the HR Self Service license. |
|Life events | Multiple deliverables are built to enhance the life event experience within Benefits Management.| 

## Features on by default in this release

The following table lists the features that are turned on by default in 10.0.29. Most features that have been turned on automatically can be turned off in Feature management. In the future, some features that have been turned on automatically might be removed from Feature management and will become mandatory. This is to ensure that customers are using current functionality, so that as enhancements are added they can build on the current functionality. Features will never by automatically enabled in less than one year unless they are determined to be essential. 

| Feature name | Feature added | Feature state | Module |
| :---- | :---- | :---- | :---- |
|Task management|	3/31/2022|	On by default|	Human Resources|
|Future-dated worker transfer with cross-company compensation|	08/31/2019|	On by default|	Human Resources|
|Filter active positions|	01/06/2020|	On by default|	Human Resources|
|Managers can view performance-related information for extended reports	|4/29/2021|	On by default|	Human Resources|
|Human resources user experience enhancements	|03/31/2022|	On by default|	Human Resources|
|Configure multiple compensation levels per job|	03/31/2022|	Mandatory	|Human Resources|
|Print performance reviews|	03/31/2022|	On by default|	Human Resources|







