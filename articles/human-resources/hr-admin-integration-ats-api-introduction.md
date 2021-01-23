---
# required metadata

title: Applicant Tracking System integration API introduction
description: This topic describes the Dynamics 365 Human Resources Applicant Tracking System (ATS) integration API.
author: andreabichsel
manager: tfehr
ms.date: 01/25/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-human-resources
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jaredha
ms.search.validFrom: 2021-01-25
ms.dyn365.ops.version: Platform update 36
---

# Applicant Tracking System integration API introduction

This topic describes the Dynamics 365 Human Resources Applicant Tracking System (ATS) integration API. The intent of the API is to enable streamlined integrations between Dynamics 365 Human Resources and partnering ATSs.

![add image]

The integrated experience begins in Human Resources when a hiring manager creates a recruiting request. When the request is activated, the ATS pulls the detail for the request to create a recruiting project. Then it follows the recruiting pipeline to select and hire a candidate for the position(s). Finally, the ATS completes the round-trip integration by sending the selected candidate’s record into Human Resources. The candidate record can then go through more onboarding validations and workflows to create the employee record.

To enable the integration, Human Resources has added the following components:

1.	Functionality to create a recruiting request.
2.	An expanded candidate profile and related workflows.
3.	An integration API opening up the new functionality to integrating applications.

For more information about setting up and using the recruiting request and candidate functionality, see [Recruit job candidates](hr-personnel-recruit.md).

## Microsoft Dataverse

This API is built on Microsoft Dataverse (formerly Common Data Service). All RESTful interaction with this API is done via the Microsoft Dataverse Web API, which uses OData. This API is a subset of the Dataverse Web API. The Dataverse Web API defines characteristics such as authentication, SLAs, batch, concurrency control, and error handling.

For more information about the Microsoft Dataverse Web API, see:

- [What is Microsoft Dataverse?](https://docs.microsoft.com/powerapps/maker/data-platform/data-platform-intro)
- [Use the Microsoft Dataverse Web API](https://docs.microsoft.com/powerapps/developer/data-platform/webapi/overview)

## Data model

The data model is centered around two main entities:

- **RecruitingRequest** represents a request to an ATS to recruit for one or more open positions. For data model details about **RecruitingRequest** and related entities, see [Recruiting request and related entities](hr-admin-integration-ats-api-recruiting-entities.md).
- **CandidateToHire** represents details of a candidate who has accepted an offer for a position. **Person** represents the individual who is the candidate. A person can have multiple roles in the company, such as candidate, worker, employee, or contractor. For data model details about **CandidateToHire**, **Person**, and related entities, see [Candidate to hire and related entities](hr-admin-integration-ats-api-candidate-entities.md).

The following diagram illustrates relationships within the API. Several types have foreign keys to other, pre-existing entities in Human Resources that aren't illustrated here. This document provides information on entities that are specific to recruiting integration scenarios. However, there are many other entities in the Dataverse Web API for Dynamics 365 Human Resources that may also be relevant to your integration. For example, you may also need detail for workers, jobs, positions, or other entities not defined here. Many of these entities are referenced in foreign key relationships or navigation properties.

![ATS integration flow](media/hr-admin-integration-ats-api-introduction-flow.png)

## Option sets

The model also includes option sets that provide enumerated values associated with entity properties. For detail on working with option sets in the Dataverse Web API, see [Create and update option sets using the Web API](https://docs.microsoft.com/powerapps/developer/data-platform/webapi/create-update-optionsets). Option sets are defined for each Dataverse environment.

## See also

[Recruit job candidates](hr-personnel-recruit.md)<br>
[What is Microsoft Dataverse?](https://docs.microsoft.com/powerapps/maker/data-platform/data-platform-intro)<br>
[Use the Microsoft Dataverse Web API](https://docs.microsoft.com/powerapps/developer/data-platform/webapi/overview)<br>
[Create and update option sets using the Web API](https://docs.microsoft.com/powerapps/developer/data-platform/webapi/create-update-optionsets)<br>
[Recruiting request and related entities](hr-admin-integration-ats-api-recruiting-entities.md)<br>
[Candidate to hire and related entities](hr-admin-integration-ats-api-candidate-entities.md)

## See also

[Recruiting request and related entities](hr-admin-integration-ats-api-recruiting-entities.md)<br>
[Candidate to hire and related entities](hr-admin-integration-ats-api-candidate-entities.md)