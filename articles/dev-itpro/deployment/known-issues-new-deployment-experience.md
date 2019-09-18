---
# required metadata

title: Known issues with self-service deployment
description: This topic lists known issues that you might experience when using self-service deployment.
author: sarvanisathish
manager: AnnBe
ms.date: 09/18/2019
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

# Known issues with self-service deployment

[!include[banner](../includes/banner.md)]
[!include [banner](../includes/limited-availability.md)]

This topic describes the known issues with [self-service deployment](infrastructure-stack.md).

## Lifecycle Services (LCS)

### Features not intended to be implemented
The following LCS features are deprecated and will not be implemented in self-service deployment.

| **Feature**        | **Description**   |
|--------------------|--------|
| System diagnostics | System diagnostics has been deprecated. All data and functionality provided by system diagnostics today will be available through other features in the product and LCS. |
| Service requests   | Service requests are being replaced with self-service actions. |

### Known issues in this release
Know issues are bugs that will be addressed in upcoming releases. Every 2 weeks there is a new release of LCS.

-   Log files listing deployment failures are not yet available through LCS. Currently, you can open a support ticket if you need the log files.

-   LCS integration from the application environment does not work. The features that are not available as a result of this include:

    -   Getting started

    -   Online Help enabled through BPM libraries. Online Help from docs.microsoft.com is available.

    -   Raising support tickets from within the application. Cloud-powered support from LCS is enabled.

## Finance and Operations apps 

### Features not yet implemented

The following features that have infrastructure dependencies are not yet implemented in the modern deployment experience. These features have not been deprecated.

| **Feature**                 | **Description**                                           |
|-----------------------------|-----------------------------------------------------------|
| Retail                      | Retail support is not yet enabled.                        |
| Trace Parser                | Perf tools are not yet supported.                         |
| Reporting – Print to Screen | Only print to PDF is supported at this time.              |
| Export to Word              | Export to Word functionality is not enabled at this time. |

### Features not intended to be implemented
The following features are deprecated and will not be implemented in the modern deployment experience.

| **Feature**  | **Description**                     |
|--------------|-------------------------------------|
| Custom fonts | Custom fonts will not be supported. |

### Known issues in this release
Known issues are listed below. These are bugs that are being worked on actively. Hotfixes will be provided in future releases.

#### Financial reporting

-   **Default reports are not imported by default:** To import the default reports, do the following:

    1.  Launch Report designer by going to **General Ledger \> Inquiries and reports \> Financial reports.**
    2.  Click **New**.
    3.  Go to **Tools \> Import Default Reports**. 
    4.  Reports will load into the web client after a few minutes.

-   **Print to PDF is printing to XPS instead** (due to a print driver access issue).
