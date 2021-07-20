---
# required metadata

title: Validate applications for Finance and Operations apps
description: This topic provides information about the requirements that are used to verify that custom code meets Microsoft guidelines.
author: kfend
ms.date: 04/13/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 196913
ms.assetid: 5f9729e3-ff67-4526-b2aa-d7f9f3062a41
ms.search.region: Global
# ms.search.industry: 
ms.author: omarc


---

# Validate applications for Finance and Operations apps

[!include [banner](../includes/banner.md)]

This topic provides information about the requirements that are used to verify that custom code meets Microsoft guidelines, and that a solution package can be successfully bundled and delivered in a Finance and Operations apps environment.

Microsoft requires specific reviews in order to validate the following requirements:

-   A partner's custom code meets Microsoft guidelines.
-   A Microsoft Dynamics Lifecycle Services (LCS) solution package can be successfully bundled and delivered.
-   Core independent software vendor (ISV) business scenarios can be transacted.

Currently, partners must demonstrate that these requirements have been met by doing test deployments and then sharing the results with Microsoft. No code will be deployed on a customer environment that Microsoft hasn't validated. Partners must complete the following curation artifacts and tests:

-   Code analysis report (CAR)
-   Business process modeler (BPM)/test scripts
-   Business database backup
-   Project name and description
-   Data packages 
-   Methodology 
-   Binaries (optional)
-   Deployable packages
-   Models (code and tests)
-   Marketing content

## Curation meeting

The following table describes the steps that must be completed before the validation meeting.

| Phase | Step | Activity                               | Process steps                                                                                                                                        | Success criteria                                                                                                                                                                                                                                                                                                                        |
|-------|------|----------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1     | 1    | Validate code.                          | Run all customer model files by using the CAR tool, and then generate the report.                                                                   | Successfully create a CAR without any localization, accessibility, performance, or security issues.                                                                                                                                                                                                                                     |
| 1     | 2    | Verify user experience (UX) guidelines. | Follow UX guidelines to implement the workspace correctly.                                                                                          | Reference best practice information in the Migrate and Create methodology section of LCS.                                                                                                                                                                                                                                               |
| 2     | 3    | Validate the solution package in LCS.   | Create a solution package in LCS that includes all the required artifacts.                                                                                                            | A solution package that has all the required artifacts has been published in LCS, and a globally unique identifier (GUID) has been created for the solution.                                                                                                                                                                                                                        |
| 2     | 4    | Deploy an environment.                  | Deploy a standard environment that has partner code, based on the package contents (code, binaries, and configuration).      | Successfully deploy at least one Finance and Operations environment without any errors. The environment configuration (including components and the configuration) is the same as the partner's reference environment. A user can successfully sign in to this environment without any errors. |
| 2     | 5    | Configure and deploy data.              | Deploy partner-supplied data in the environment without any errors.                                                                                 | Demonstrate that partner-supplied master and reference data was successfully pushed into the environment without any errors.               |
| 2     | 6    | Do a sanity check.                      | After data has been loaded into the environment, users should be able to complete business transactions (as defined in the scope of the solution).  | Users can sign in to the data-loaded environment without any errors. Business transactions can be completed, as defined in the package scope, without any errors.                                                                                                                                                                                |

### Detailed curation requirements

The following table provides more information about each curation requirement.

| Requirement                  | Description                                                                                                                                                                                                                                                                          |
|------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| CAR                          | All major issues that the CAR highlights should be addressed after you upgrade. The CAR must be submitted to Microsoft before the validation meeting.                                                                                                                                |
| BPM/test scripts             | All task recordings should be completed for the industry vertical that the solution package is designed for and should include end-to-end scenarios.                                                                                                                                 |
| Business database backup     | A business database of your upgraded environment and best practice configurations should be loaded into the Asset library in LCS.                                                                                                                        |
| Project name and description | The project name and description should be incorporated into the beginning of the implementation methodology for the solution package.                                                                                                                                               |
| Data packages                | All data packages should be loaded into LCS before the validation meeting. Create data entities for any additional custom fields or tables for your custom functional features. You should be able to modify the data packages and load them into an empty environment, and then consume the data packages in Data Management Framework. |
| Methodology                  | The methodology should incorporate an overview of the product. A guided experience to Conference Room Pilot 1 (CRP1) and any other implementation methodology that is specifically tailored to your solution are optional. |
| Binaries (optional)          | Incorporate any required binary files.                                                                                                                                                                                                                                               |
| Deployable packages          | Incorporate the deployable packages that are required in order to bring your custom features and functionality into your environment.                                                                                                                                     |
| Models (code and tests)      | Incorporate any model files that are required for your solution.                                                                                                                                                                                                                     |
| Marketing content            | Add your marketing content, such as logos, descriptions, and screen shots of your solution package. The solution logo should be app-specific and should not include your company name. The description should be aligned with your custom business processes.                            |


## Update and maintenance requirements
If you have a curated solution that is published on AppSource, you must keep the solution up to date. After each major Spring and Fall release, you will have eight weeks to upgrade your code. You must update and test the following artifacts:

-   CAR
-   Models (code and tests)
-   Deployable packages
-   BPM/test scripts
-   Data packages
-   Business database backup

### Maintenance process steps

| Phase | Number | Activity                                       | Process steps                                                                | Success criteria                                                                                                                                                                                                                                                                                     |
|-------|--------|------------------------------------------------|------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1     | 1      | Validate customer code. | Run all customer model files by using the CAR tool, and generate the report. | Successfully create a CAR without any localization, accessibility, performance, or security issues. All major issues that the CAR highlights should be addressed after you've upgraded to the latest major release. The CAR must be submitted to Microsoft within eight weeks after each major Spring and Fall release. |


## Additional resources

[Requirements for publishing apps on AppSource](lcs-solutions-app-source.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]