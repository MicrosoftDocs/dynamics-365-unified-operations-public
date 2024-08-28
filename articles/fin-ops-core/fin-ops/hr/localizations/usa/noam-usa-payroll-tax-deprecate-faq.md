---
# required metadata
title: Deprecation of US payroll tax updates FAQ
description: This article describes the deprecation of tax updates for US payroll and summarizes questions that are frequently asked.
author: aolson
ms.date: 08/28/2024
ms.topic: article 
# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.reviewer: twheeloc
ms.search.validFrom: 2021-02-05
ms.dyn365.ops.version: Human Resources
---

# Deprecation of US payroll tax updates FAQ

[!include [banner](../../../../../finance/includes/banner.md)]

This article discusses the retired tax updates for the US payroll feature in Microsoft Dynamics 365 Human Resources and the impacted payroll functionality. 

## Overview
On August 1, 2019, Microsoft made the following announcement: Microsoft strives to bring best in class Dynamics 365 offerings to its entire customer base. To that end, Microsoft continues to evaluate its portfolio
of offerings. As Microsoft evaluates the impact of certain features and enhances functionality offered via ISV solutions, tax updates for the U.S. Payroll feature will no longer be supported.
 - Tax update support ends effective October 1, 2021 for online and on-premises customers of the following solutions: Dynamics 365 for Finance (aka Unified Operations | Finance and Operations)
     - Dynamics 365 Finance (online and on-premises)
     - Dynamics 365 Finance, Enterprise edition (online and on-premises)
     - Dynamics AX 2012 R3 

To ensure our customers have ample time to provide for the safety of their employees, protect the health and well-being of their communities, and react to the changes needed due to COVID-19, we will extend the 
support date for the US Payroll tax updates to July 31, 2024 for Dynamics 365 Finance. 

>[!NOTE]
> Payroll is now part of Dynamics 365 Human Resources, so all future communications will state Human Resources.

As part of Dynamics 365 Human Resources version 10.0.40 and 10.0.41, the tax engine code was removed as part of the US Payroll tax update deprecation. While removing the tax engine classes, changes were made to 
other parts of the code as a result. These changes caused some previous payroll functionality to not work as expected.

### Customer impact 
As the support for tax updates are retired, the tax engine has been removed from the application. To understand the changes as a result of the removal, see
[Deprecation of US payroll tax updates](noam-usa-deprecate-payroll-tax.md). Customers can continue to use the payroll module without any future functionality enhancements from Microsoft. The U.S. payroll module 
will continue to exist in the solutions after the tax updates retirement. This enables both customers and partners that have built additional functionality on top of the existing U.S. payroll to continue to use
those features, but you may need to make updates based on the removed artifacts. Support for the existing U.S. payroll module will be addressed via the existing standard extensibility review process. 


### Frequently asked questions (FAQs) 

### What are the impacts of removing the tax engine that was used for US Payroll? 
For more information about the impact of removing the code, see [Deprecation of US payroll tax updates](noam-usa-deprecate-payroll-tax.md).

### What does it mean when functionality is marked with status “Limited”?
A. When functionality is marked as Limited, it indicates that either a portion of, or the entire, functionality relied on the removed tax engine code, and as a result, may not work as it did before. 
 
### Why weren’t these changes shared earlier?
The payroll activities were initially independent of the tax engine. However, after the code was removed and related artifacts were adjusted, customers reported being unable to complete some payroll activities 
as they could before the update. This situation has provided us with a better understanding of how customers have extended the payroll functionality.

### Will data be removed from the tables?
No. Although tables that were used by the tax engine may still be present and no longer used, we won't delete data from any customer environment.

### How do I update the data in the remaining tables?
If a page or artifact was removed that was responsible for updating the data in the remaining tables, it may require a customization to continue to update them.

### Is there a plan to deprecate the payroll module in Dynamics 365 Human Resources?
Currently, there are no plans to deprecate or remove the payroll module from Dynamics 365 Human Resources. If this happens in the future, the formal deprecation guidelines would be followed. For more information,
see [One Version service updates FAQ](../../../../dev-itpro/get-started/one-version.md). 

### Will Microsoft continue to provide support for the Payroll module?  
No. Microsoft won't make additional enhancements to our U.S. Payroll feature or other payroll functionality, but customers can still report any issues with the existing functionality and we will address those on 
a case-by-case basis. Log a support case with Microsoft Support for any new issues.



