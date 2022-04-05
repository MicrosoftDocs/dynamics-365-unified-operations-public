---
# required metadata

title: Reporting options
description: This topic explains how to customize Microsoft Dynamics 365 Human Resources reports or create new reports.
author: twheeloc
ms.date: 08/19/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: HcmPersonnelManagementWorkspace, LeaveAbsenceWorkspace, HcmTalentBenefitWorkspace, HcmCompensationWorkspace, HcmEmployeeDevelopmentWorkspace, HcmLearningWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Reporting options


[!INCLUDE [PEAP](../includes/peap-2.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]



**Environment details**

This issue applies to all environments.

**Symptom**

The customer wants to customize Microsoft Dynamics 365 Human Resources reports or create new reports.

**Issue**

The user can't customize the embedded Microsoft Power BI reports.

**Solution**

- The Human Resources data that flows to Dataverse can be reported on via the Power Apps Dataverse connector to Power BI Desktop. Note that Dataverse contains a subset of Human Resources data. For more information about Power BI and dashboards, see [Create Power BI reports and dashboards with Power Apps Common Data Service](https://powerapps.microsoft.com/blog/cdsconnectortopowerbi).
- Electronic reporting (ER) is available for some reports in Human Resources. Customer-driven customizations can be done via the ER configuration options.
- Data can be exported to Microsoft Excel or Microsoft Word by using the various data entities that Human Resources provides through the Microsoft Office integration.

**Long-term solution**

Additional Power BI options will be available, and more data and entities will be part of Dataverse.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
