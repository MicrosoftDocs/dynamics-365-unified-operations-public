---
# required metadata

title: Infrastructure estimator (AX 2012)
description: The Microsoft Dynamics Lifecycle Services Infrastructure estimator provides an automated rough first estimate of the hardware needs of an environment. Estimates can be provided for environments that are on your premises or in the cloud. The estimate is intended to be used as a basis for more in-depth, manual sizing estimates, not to replace them.
author: josaw1
manager: AnnBe
ms.date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Lifecycle Services
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: josaw1
ms.search.scope: AX 2012
# ms.tgt_pltfrm: 
ms.custom: 19081
ms.assetid: ce126e17-5dc6-42fd-a9aa-4932e3db3830
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 
ms.dyn365.ops.version: 2012

---

# Infrastructure estimator (AX 2012)

The Microsoft Dynamics Lifecycle Services Infrastructure estimator provides an automated rough first estimate of the hardware needs of an environment. Estimates can be provided for environments that are on your premises or in the cloud. The estimate is intended to be used as a basis for more in-depth, manual sizing estimates, not to replace them.

An infrastructure sizing estimate is created by:
1.  Gathering usage and role requirements in a usage profile.
2.  Matching the requirements with a set of servers of predefined size.

| **Important**                                                                                                                                                                                                                 |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Because few data points are used to create an estimate, the estimate will be rough, and sizing limits are relatively low. Therefore, the Infrastructure estimator can’t currently address the needs of large implementations. |

## Environments
Infrastructure estimates are available for the following types of environments, either on premises or in the cloud.
-   DevelopmentCreate an estimate for an environment that supports developers and a version control system. The estimate for a development environment is not designed to support a heavy transaction load. The estimate assumes three computers.
-   ProductionCreate an estimate for a live environment. The estimate for a production environment is based on information that you entered in the Usage profiler. The estimate provided for this environment will support a high volume of business transactions and many users.
-   TestCreate an estimate for an environment that supports functional or performance testing. The estimate can include up to four computers.
-   TrainingCreate an estimate for an environment that supports training users on Microsoft Dynamics AX. The estimate provided for a training environment is not designed to support a heavy transaction load. The estimate can include up to four computers.

## Server roles
Server roles represent the major components of the Microsoft Dynamics AX environment. Each server can be used to meet multiple role requirements (for example, by putting Analysis Services and Reporting Services on the same computer). For the purposes of the Infrastructure estimator, each server role requires a predefined amount of processing power. The Infrastructure estimator selects the smallest server that meets the CPU and RAM requirements for each role in the environment. The following server roles may be required, depending on your environment.

| Role                          | Condition                                                                                 |
|-------------------------------|-------------------------------------------------------------------------------------------|
| AOS                           | Always required                                                                           |
| SQL Server                    | Always required                                                                           |
| Terminal Services             | Required if there is a remote operating site                                              |
| Enterprise Portal             | Required if it is specified in the Deployment details questionnaire of the Usage profiler |
| AOS for Enterprise Portal     | Required if Enterprise Portal is needed                                                   |
| SQL Server Reporting Services | Required if it is specified in the Deployment details questionnaire of the Usage profiler |
| SQL Server Analysis Services  | Required if it is specified in the Deployment details questionnaire of the Usage profiler |
| Help server                   | Required if it is specified in the Deployment details questionnaire of the Usage profiler |

## Prerequisites
If you want to create an infrastructure estimate for a production environment, you must first complete a usage profile. For more information, see [Usage profiler (Lifecycle Services, LCS)](usage-profiler-lcs.md). Estimates for development, test, and training environments do not require a completed usage profile.

## Create an infrastructure estimate
1.  [Go to Lifecycle Services](https://lcs.dynamics.com).
2.  On the project home page, click the Infrastructure estimator tile.
3.  If you need an estimate for a production environment and you haven’t yet completed a usage profile, click the Usage profiler button. For more information, see [Usage profiler (Lifecycle Services, LCS)](usage-profiler-lcs.md).
4.  Click New estimate.
5.  Select the type of environment that you are creating an estimate for.
6.  Enter a name for the estimate, and select whether the environment will be hosted on premises or in the cloud.
7.  Enter other information as needed. The following table describes the additional information that you may need to provide, depending on the type of environment that you selected.

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Environment</th>
    <th>Parameters</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Development</td>
    <td><ul>
    <li>Number of developers</li>
    <li>Version control system</li>
    </ul></td>
    </tr>
    <tr class="even">
    <td>Production</td>
    <td>None</td>
    </tr>
    <tr class="odd">
    <td>Test</td>
    <td><ul>
    <li>Type of testing</li>
    <li>Number of computers</li>
    </ul></td>
    </tr>
    <tr class="even">
    <td>Training</td>
    <td>Number of computers</td>
    </tr>
    </tbody>
    </table>

8.  Click Create.

## View infrastructure estimates
On the main Infrastructure estimator page, select an estimate to view the details.



