---
# required metadata

title: Known issues with the new deployment experience
description: [Full description that appears in the search results. Often the first paragraph of your topic.]
author: sarvanisathish
manager: AnnBe
ms.date: 12/07/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global 
# ms.search.industry: 
ms.author: sarvanis
ms.search.validFrom: 2018-12-31
ms.dyn365.ops.version: 8.1.1

---

# Known issues with the new deployment experience

[!include[banner](../includes/banner.md)]

Features not yet implemented
----------------------------

The following LCS features are not yet implemented in the new deployment
experience. These features have not been deprecated.

| **Feature**             | **Description**                                                                                                                                                                                                                                                                                                              |
|-------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Data movement scenarios | The self-service automation to move database bacpacs/copy databases across environments is not yet implemented. At this time, you will need to log a Support ticket to perform these operations. In the coming weeks, the following self-service feature will be enabled - Golden config bacpac move to Sandbox environment. |
| Monitoring page         | The LCS page that allows you to monitor the Finance and Operations environment is not yet implemented.                                                                                                                                                                                                                       |
| Package deployments     | Applying binary, app, and X++ updates is not yet enabled. Currently, you can only update your environment by deleting and redeploying. Slipstreaming is enabled.                                                                                                                                                             |
| LCS tiles experience    | Not yet enabled.                                                                                                                                                                                                                                                                                                             |

Features not intended to be implemented
---------------------------------------

The following LCS features are deprecated and will not be implemented in the new
deployment experience.

| **Feature**        | **Description**                                                                                                                                                          |
|--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| System diagnostics | System diagnostics has been deprecated. All data and functionality provided by system diagnostics today will be available through other features in the product and LCS. |
| Service requests   | Service requests are being replaced with self-service actions.                                                                                                           |

Known issues in this release
----------------------------

Know issues are bugs that will be addressed in the upcoming release. Every 2
weeks there is a new release of LCS.

-   Logs on failures are not yet available through LCS. Currently, you need to
    log failures as a Support incident.

-   LCS integration from a Dynamics 365 for Finance and Operations environment
    does not work. The features that are not available as a result of this
    include:

    -   Getting started

    -   Online Help enabled through BPM libraries. Online Help to
        docs.microsoft.com is available.

    -   Raising Support tickets from within Finance and Operations.
        Cloud-powered Support from LCS is enabled.

Finance and Operations 
=======================

Features not yet implemented
----------------------------

The following features that have infrastructure dependencies are not yet
implemented in the new deployment experience. These features have not been
deprecated.

| **Feature**                 | **Description**                                           |
|-----------------------------|-----------------------------------------------------------|
| Retail                      | Retail support is not yet enabled.                        |
| Trace Parser                | Perf Tools are not yet supported.                         |
| Reporting – Print to Screen | Only print to PDF is supported at this time.              |
| Export to word              | Export to Word functionality is not enabled at this time. |

Finance and Operations features not intended to be implemented
--------------------------------------------------------------

The following features are deprecated and will not be implemented in the new
deployment experience.

| **Feature**  | **Description**                     |
|--------------|-------------------------------------|
| Custom fonts | Custom fonts will not be supported. |

Known issues in this release
----------------------------

Known issues are listed below. These are bugs that are being worked on actively.
Hotfixes will be provided in future releases.

### Financial reporting

-   **Default reports are not imported by default:** To import the default
    reports, do the following:

    1.  Launch Report designer by going to **General Ledger \> Inquiries and
        reports \> Financial reports.**

    2.  Click **New**.

    3.  Go to **Tools \> Import Default Reports**. 

    4.  Reports will load into the web client after a few minutes.

-   **Print to PDF is printing to XPS instead** (due to a print driver access
    issue).
