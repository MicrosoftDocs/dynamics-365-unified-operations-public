---
# required metadata

title: Usage profiler 
description: 
author: kfend
manager: AnnBe
ms.date: 2015-12-05 18 - 06 - 51
ms.topic: article
ms.prod: 
ms.service: Lifecycle Services
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: AX 2012
# ms.tgt_pltfrm: 
ms.custom: 18751
ms.assetid: ceeb6463-00d4-41f9-88c3-61791020a9f5
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 
ms.dyn365.ops.version: 2012

---

# Usage profiler (AX 2012)



The Usage profiler provides you with the following information:

-   A detailed summary of usage characteristics modeled for an organization, including system configuration, transaction volumes, and scheduling information.
-   A graphic representation of the organization’s peak load profile. This graph is based on a combination of the predicted schedule of concurrent user load and the batch schedules. From this graph, the peak load point can be established. You can either reschedule tasks in Microsoft Dynamics AX to mitigate peak load, or accommodate peak load in your hardware sizing estimation.

Information from the usage profile is also used in the project summary report that project stakeholders can use to better understand the plans for an implementation. The following table describes the types of usage data that are gathered, and where they are gathered from.

| Summarized Data                         | Gathered from:                                                                                                                                              |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Batch peak lines/hour                   | Value of the highest peak from the load chart added to the estimated hourly load from batch transactions entered in Business process questionnaires         |
| Integration peak lines/hour             | The sum of all integration lines/hour values added to the estimated hourly load from integration transactions entered in Business process questionnaires    |
| Rich Client peak lines/hour             | Sum of Online, Workflow and “None” transactions from Business process questionnaires added to the sum of the miscellaneous peak “lines per hour” questions. |
| Total peak lines/hour                   | Total of the above entries (the value for batch is halved)                                                                                                  |
| Remote peak concurrent users            | Value of the highest peak from the load chart of all remote operating sites                                                                                 |
| Enterprise Portal peak concurrent users | Value of the answer to the Deployment details question                                                                                                      |
| Total peak concurrent users             | Highest among: Peak of total user load chart, question from Deployment details, and sum of the questions from all the Business process questionnaires.      |

## Prerequisites
If you want to import process data from Business process modeler, you must first complete the modeling of the organization. For more information, see [Business process modeler (Lifecycle Services, LCS)](/lifecycle-services/business-process-modeler-lcs.md).

## Import business processes from BPM
We recommend that you start by importing data from Business process modeler, and then add additional data manually.

1.  [Go to Lifecycle Services](https://lcs.dynamics.com).
2.  Configure your organization in Business process modeler.
3.  On the project home page, click the **Usage profiler** tile, and then on the **Usage profiler** page, click **Import from BPM**.The system displays the message **Retrieving BPM data**. When it has finished importing the data, you will be returned to the Usage profiler page.

## Enter data
You can either enter data directly in Usage profiler, or you can download an Excel template, complete it, and then upload it again.

| **Note**                                                                                                                                                                                |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| When you are finished entering data, click the **Mark as complete** tile. The usage profile must be marked as complete to be used by other tools, such as the Infrastructure estimator. |

The following table lists the sections that you can enter data for.

| Section                 | Description                                                                                                                                                                                                                                                                                                                                                       |
|-------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Environment details** | Under **Deployment details**, answer a series of questions about the version, hosting environment, organizational structure, and so on.                                                                                                                                                                                                                           |
| **Business processes**  | Business processes must be defined in **Business Process Modeler**, and then imported. All business processes will be in the **Not started** state until the predicted usage information has been filled in. Many processes require that you estimate the predicted monthly volume and number of users. You may need to enter users and volumes for subprocesses. |
| **Reports**             | Describe reports by whether they are operational, management, or offline, their complexity, frequency, and related business process.                                                                                                                                                                                                                              |
| **Operating sites**     | Operating sites are the locations in which your organization is running Microsoft Dynamics AX. You'll need to provide a name, whether the location is remote or onsite, upload and download bandwidth, and your WAN connection latency. Use the **Work schedule** to enter peak concurrent users per hour.                                                        |
| **ISV products**        | Enter the ISV products in your environment, and the estimated transaction lines per hour.                                                                                                                                                                                                                                                                         |
| **Customizations**      | Describe planned customizations in terms of peak transaction lines per hour, and related business process.                                                                                                                                                                                                                                                        |
| **Integrations**        | Describe planned integrations in terms of peak transaction lines per hour, and related business process.                                                                                                                                                                                                                                                          |
| **Batch processes**     | Describe batch processes in terms of transaction lines and recurrence.                                                                                                                                                                                                                                                                                            |

### 

### Enter data directly in Usage profiler

Click each section, and enter the requested data for your organization. Only modules that were imported from Business Process Modeler will be visible.
| **Note**                                                                                                                               |
|----------------------------------------------------------------------------------------------------------------------------------------|
| The **Usage profiler** page is a panorama page. Scroll to the right by using your mouse wheel or the lower scroll bar in your browser. |

### 

### Enter data by using an Excel template

1.  Click **Download Excel template**.
2.  Enter data in the template, and save it.
3.  Click **Upload completed template**, and select the template with your data.

## View reports
You can view a report of your estimated weekly peak load and the operating sites, or see an estimate of the infrastructure you will need for your implementation.

1.  On the main **Usage profiler** page, click **Summary** to view the **Summary** report.
2.  On the main **Usage profiler** page, click **Infrastructure estimation** to view the **Infrastructure estimation** report.


