---
# required metadata

title: Known issues with self-service deployment
description: This topic lists known issues that you might experience when using self-service deployment.
author: rashmansur
manager: AnnBe
ms.date: 05/26/2020
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
ms.author: rashmim
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

## Finance and Operations apps 

### Features not yet implemented

The following features that have infrastructure dependencies are not yet implemented in the modern deployment experience. These features have not been deprecated.

| **Feature**                 | **Description**                                           |
|-----------------------------|-----------------------------------------------------------|
| Commerce                      | Commerce support is now enabled with the 10.0.10 release. Please see [Create payment packaging for Application Explorer for self-service deployment](../../../commerce/dev-itpro/payment-connector-package.md) for more details.          |

### Features not intended to be implemented
The following features are deprecated and will not be implemented in the modern deployment experience.

| **Feature**  | **Description**                     |
|--------------|-------------------------------------|
| Custom fonts | Custom fonts are not supported. Please see [Document Reporting Service in Dynamics 365 applications](../analytics/reporting-experience-iias-environments.md) for more details.
| List of all deprecated features us here  | [Removed or deprecated features on Self-Service](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/migration-upgrade/deprecated-features)|

