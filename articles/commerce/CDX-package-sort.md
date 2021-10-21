---
# required metadata

title: Sort Commerce Data Exchange packages by primary index
description: This topic provides an overview of the Dynamics 365 Commerce feature to sort Commerce Data Exchange (CDX) packages by a primary index per package.
author: jashanno
ms.date: 08/24/2021
ms.topic: article
audience: IT Pro
ms.reviewer: sericks
ms.search.region: global
ms.author: jashanno
ms.search.validFrom: 2021-08-24

---

# Sort Commerce Data Exchange packages by primary index

[!include [banner](../includes/banner.md)]

This topic provides an overview of the Dynamics 365 Commerce feature to sort Commerce Data Exchange (CDX) packages by a primary index per package. The **Sort CDX packages by primary index** feature optimizes the data preprocessing performance of data transformation. It is important to note that this feature does not alter any data application logic for a Commerce Scale Unit (CSU) or a Modern POS offline database, nor does it improve performance for either of those components.

## Prerequisites

The **Sort CDX packages by primary index** feature must be turned on in the **Feature management** workspace. For more information, see [Feature management overview](../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Feature value

This feature provides additional performance when using Micrsoft Dataverse with Digital Commerce, Headless Commerce, or Dynamics 365 Commerce (when Dataverse is used).

## Using this feature

This feature, after it is turned on in **Feature management**, will function without visibility to the end user.
