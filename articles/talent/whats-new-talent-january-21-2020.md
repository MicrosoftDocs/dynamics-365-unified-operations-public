---
# required metadata

title: What's new or changed in Dynamics 365 Talent (January 21, 2020)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent.
author: Darinkramer
manager: AnnBe
ms.date: 1/21/2020
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
ms.search.validFrom: 2020-01-21
ms.dyn365.ops.version: Talent

---
# "What's new or changed in Dynamics 365 Talent (January 21, 2020)"

[!include [banner](includes/banner.md)]

This topic describes features that are either new or changed in Dynamics 365 Talent.

## Changes in Attract
This release includes minor bug fixes for Dynamics 365 Talent: Attract. Additional functionality is being added within Attract as a result of the announcement posted [here](https://dynamics.microsoft.com/en-us/talent-to-human-resources/).

### Download environment data

Administrators can download their environment’s data. The data is exported in standard JSON format with all the jobs, candidates and configuration exported in a zip file. More information is available [here](https://docs.microsoft.com/en-us/dynamics365/talent/attract-onboard-export-data).

### Restricting access to environments for non-admin users

In this release, administrators can also choose to restrict access to the environment for non-admin users. Please note that this is a one-way action.

## Changes in Onboard
This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

### Exporting onboarding guides

Users can now export all of their onboarding guides and onboarding templates in Word document format.

## Changes in Core HR
Changes described in this section apply to build number 8.1.2726.

### Most recent annual compensation field in Verify employment form is not consistent  - (392092)

This release includes a change that will consistently display the latest currency based on the company selector on the verify employment form.

### Known as field has been to be added to the Feedback recipient lookup. - (407789)

The lookup for workers, when providing performance feedback, does not provide enough information to determine if feedback is going to the correct person. The "known as" column has been added to help identify the unique name of the employee.
 
### HcmWorkerPayrollInfo record is created without an association to a worker - (394526)

With this release, a change has been made to not write HCMWorkerPayrollInfo records without reference to an employee.

### Able to access edit department when navigating from position hierarchy - (341001)

When security has been set up to deny access to editing departments, the edit will be disabled when navigating to the departments form in all scenarios.

## Coming soon

A new Common Data Service solution will be available soon with the following changes:

| Description | Change |
| --- | --- |
| **Job/Position** entity changes | <ul><li>**Compensation region** added</li><li>**Financial dimensions** added</li></ul> |
| **Worker** entity changes | <ul><li>**Name sequence** added</li><li>**Works from home** added</li><li>**Language** added</li><li>**Seniority date** added</li><li>**Anniversary date** added</li><li>**Original hire date** added</li></ul> |
| **Employment** entity changes | <ul><li>**Financial dimensions** added</li><li>**Termination reason** added</li><li>**Termination date** renamed from **Transition date**</li><li>**Probation date** added</li></ul> |
| **Worker address** entity changes | <ul><li>**Street address** added</li><li>**Address line 1**, **Address line 2**, and **Address line 3** marked for deprecation</li></ul> |
| New variable compensation setup entities | <ul><li>**Compensation variable plan type**</li><li>**Compensation variable plan**</li><li>**Vesting rules**</li><li>**Compensation variable plan level**</li></ul> |
| New **Worker calender employment** entity | <ul><li>**Work calendar entity** added</li></ul> |
