---
# required metadata

title: Reporting options
description: This article explains how to resolve the issue where a customer wants to customize Microsoft Dynamics 365 Human Resources reports or create new reports.
author: andreabichsel
manager: AnnBe
ms.date: 02/03/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-human-resources
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Reporting options

**Environment details**

This issue applies to all environments.

**Symptom**

The customer wants to customize Microsoft Dynamics 365 Human Resources reports or create new reports.

**Issue**

The user can't customize the embedded Microsoft Power BI reports.

**Solution**

- The Human Resources data that flows to Common Data Service can be reported on via the Power Apps Common Data Service connector to Power BI Desktop. Note that Common Data Service contains a subset of Human Resources data. For more information about Power BI and dashboards, see [Create Power BI reports and dashboards with Power Apps Common Data Service](https://powerapps.microsoft.com/blog/cdsconnectortopowerbi).
- Electronic reporting (ER) is available for some reports in Human Resources. Customer-driven customizations can be done via the ER configuration options.
- Data can be exported to Microsoft Excel or Microsoft Word by using the various data entities that Human Resources provides through the Microsoft Office integration.

**Long-term solution**

Additional Power BI options will be available, and more data and entities will be part of Common Data Service.
