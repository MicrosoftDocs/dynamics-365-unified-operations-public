---
title: Microsoft Dynamics 365 Finance business performance planning requirements
description: Learn about the system and version requirements for installing Microsoft Dynamics 365 Finance business performance planning.
author: ShielaSogge
ms.author: twheeloc
ms.topic: article
ms.date: 06/04/2026
ms.reviewer: twheeloc 
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2023-12-03
ms.search.form: 
ms.dyn365.ops.version: 
---

# Microsoft Dynamics 365 Finance business performance planning requirements

[!INCLUDE [lcs-freeze-banner](../../includes/lcs-freeze-banner.md)]

This article describes the requirements for installing Microsoft Dynamics 365 Finance business performance planning.

## System requirements

Installation of business performance planning requires a Tier-2 environment (multibox). For more information about environments, see [Environment planning](../../fin-ops-core/fin-ops/imp-lifecycle/environment-planning.md).

Business performance planning currently supports the following geographies: Australia, Brazil, UK, USA, Europe, Canada, France, Germany, India, Norway, Switzerland, UAE, South America, South Africa, and Japan. Confirm that the environment where you plan to install business performance planning is in one of these geographies.

## Version requirements

Although Dynamics 365 Finance version 10.0.37 and Platform update (PU) 61 aren't required, they provide extra options for getting general ledger information into a balance format through process automations.

## Prerequisites

Before you can install business performance planning, create the Microsoft Power Platform environment.

Before you can use the functionality of business performance planning, purchase a Finance premium license and make it available on the tenant.

> [!IMPORTANT]
> If you don't purchase a Finance license, business performance planning doesn't appear in Power Platform admin center as a Dynamics 365 app that you can install. To perform any planning operations, you must have a Finance premium license.

For more information about Finance licensing, see [Finance pricing](https://dynamics.microsoft.com/finance/pricing/).

## Installation

To install business performance planning, install two main components.

1. Install the business performance planning app from Power Platform admin center. For more information, see [Install the business performance planning app](bpp-App-install.md).
1. Install the Power BI visuals from Marketplace. For more information, see [Install business performance planning visuals](powerbi-visual-install.md).
