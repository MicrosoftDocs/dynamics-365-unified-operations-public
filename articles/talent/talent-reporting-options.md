---
# required metadata

title: Reporting options in Talent
description: This topic explains how to resolve the issue where a customer wants to customize Microsoft Dynamics 365 for Talent reports or create new reports.
author: andreabichsel
manager: AnnBe
ms.date: 11/02/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2018-11-02
ms.dyn365.ops.version: Talent

---

# Reporting options in Talent

[!include [banner](includes/banner.md)]

**Environment details**

This issue applies to all environments.

**Symptom**

The customer wants to customize Microsoft Dynamics 365 for Talent reports or create new reports.

**Issue**

The user can't customize the embedded Microsoft Power BI reports.

**Solution**

- The Core HR data that flows to Common Data Service can be reported on via the PowerApps Common Data Service connector to Power BI Desktop. Note that Common Data Service contains a subset of Core HR data. For more information about Power BI and dashboards, see [Create Power BI reports and dashboards with PowerApps Common Data Service](https://powerapps.microsoft.com/blog/cdsconnectortopowerbi).
- Electronic reporting (ER) is available for some reports in Talent. Customer-driven customizations can be done via the ER configuration options.
- Data can be exported to Microsoft Excel or Microsoft Word by using the various data entities that Talent provides through the Microsoft Office integration.

**Long-term solution**

Additional Power BI options will be available, and more data and entities will be part of Common Data Service.
