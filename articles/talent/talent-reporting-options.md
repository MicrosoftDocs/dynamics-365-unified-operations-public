---
# required metadata

title: Reporting options in Talent
description: The customer wants to customize Talent reports or create new reports.
author: Darinkramer
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
ms.reviewer: josaw
ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2018-11-02
ms.dyn365.ops.version: Talent

---

# Reporting options in Talent

[!include [banner](includes/banner.md)]


**Environment details:** 

All environments.

**Symptom:** 

The customer wants to customize Talent reports or create new reports. 

**Problem:** 

The user is not able to customize the embedded PowerBI reports.


**Solution:** 

-   The Core HR data that flows to CDS (Common Data Service) can be reported on via the PowerApps
    CDS connector to PowerBI desktop. Note that CDS
    contains a subset of Core HR data. Learn more about Power BI and Dashboards
    by reading [Create Power BI reports and dashboards with PowerApps Common Data Service](https://powerapps.microsoft.com/en-us/blog/cdsconnectortopowerbi).

-   Global electronic reporting (GER) is available for certain reports in
    Talent, and allows for customer-driven customizations via the GER
    configuration options. 

-   Data can be exported to Excel and/or Word using the various data entities
    provided by Talent with office integration.


**Long-term solution:** 

Additional PowerBI options will be available and more date/entities will be part of the CDS.
