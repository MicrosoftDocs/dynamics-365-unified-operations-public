---
# required metadata

title: Extending Talent using Powerapp/Flow - Example Scenarios
description: 
author: Neelima Gudavalli
manager: Annbe
ms.date: 03/04/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: Dynamics 365 for Talent
               PowerApps
               Flow
               CDS

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Talent, Core, Experience Apps
# ms.tgt_pltfrm: 
ms.custom:
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: Neelima Gudavalli
ms.search.validFrom: 2019-03-04
ms.dyn365.ops.version: Talent October 2018 update

---
This topic covers couple of example scenarios on Talent Extensibility using Powerapp and Flow. You can import solution package associated with each of the example into your Powerapp environment. These packages can be used as guidance or as a starting point for implementing customer specific scenarios

## Prerequisites

User with "Environment Maker" permission can import Packages

A user must have a PowerApps Plan 2 or PowerApps Plan 2 trial license in order to export or import any app.

## Flow- Form Connect
This template can be used to read data from Microsoft Forms and store it in a CDS entity.

It can be extended to cover scenarios like Capturing candidate assessments, Capture course Questionnaire results, Interview questions library for HR administrators, Candidate Evaluating the interview process.

In Attract, Forms can be exposed to the Candidate Portal and Candidate can fill details. Forms can also be embedded as activities in a job template.

When a Candidate submits form, Flow captures the form submission, reads data and stores it in the CDS entity.
## Initiate and Extract Parameters Passed to Powerapps
This template can be used as a starting point for any PowerApps scenario specific to Attract. It comes with all default parameters passed by Attract like Job Application, Candidate ID, JobID

This example template demonstrates how to retrieve a Candidate Assessment form for a Hiring manager to see the Assessment filled by a candidate.

The PowerApps can be embedded into job template in Attract
## Integration with Office 365
This PowerApps covers the scenarios of extracting team information of logged in users from office 365 and references the worker within Dynamics 365 for Talent to extract clock in and clock out details and exception recordings. Clock in and Clout out details are stored in CDS custom entities and assumed to be populated from third party systems via integration.

This app can be extended to cover scenarios like Display Team vacation, Calendar events, any Team specific events and can be used by HR, Employees and Managers
## Flow – Email Notification
This template can be used for email notification scenarios.

This template covers the scenario that trigger email notification to Candidate when Hiring team rejects the candidate in any stage of recruiting process.This template can be extended further to track candidate stage change through recruiting process and send notifications to Hiring team/Candidate

In general, Flows can be set up to send notifications for event happening in Core HR, Attract or Onboard for entities stored in CDS
## Flow – SQL Connect and execute
This Flow template connects to SQL Server and allows execution of SQL Queries.

The flow is designed to read and update SQL table but can be extended to include scenarios like: Populating a staging table in CDS with records from SQL and keeping it synchronized on periodic basis using incremental push from SQL
## Flow – Share Point Integration
This template can be used to read data from share point lists, compare the list with any CDS entity field values and can send result of comparison as a email notification. 

Organizations may have a set of urgently required Skills. These Skills can be stored in SharePoint as a SharePoint list.  When candidate applies to any job with the listed skill sets above, an email notification will be sent if there is a significant match with the skills stored in SharePoint. This way the urgently required positions are filled faster as the notifications help recruiters to reach out and cross hire Candidates across organization

This flow covers this scenario and can be extended to cover any scenarios that involves SharePoint integration.

Note: If you want to use above Apps/Flow as it is, please test it to make sure to covers all scenarios specific to your implemenation.

##Additional Resources

Power Platform: https://docs.microsoft.com/en-us/power-platform/admin/admin-documentation

