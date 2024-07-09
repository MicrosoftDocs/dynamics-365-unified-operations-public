---
# required metadata

title: Deprecation of US payroll tax updates 
description: This article describes the deprecation of tax updates for US payroll.
author: jaredha
ms.date: 07/08/2024
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
ms.author: anisagrawal
ms.reviewer: twheeloc
ms.search.validFrom: 2021-02-05
ms.dyn365.ops.version: Human Resources
---

# Deprecation of US payroll tax updates 

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes the deprecation of tax updates for US payroll.

Beginning in Microsoft Dynamics 365 Finance from 10.0.40 release, tax updates are retired for the US payroll feature. Customers can choose from different third-party solutions available on AppSource and other integrations with Dynamics 365 Human Resources.

## What was done? 
The tax engine code was removed, and significant code modifications were made to accommodate this change. All of the ste.taxengine classes that were directly used in the codebase were eliminated, and other parts of the code that referenced ste.taxengine were adjusted to return default values or null. Due to these changes, some of the payroll functionalities may not work as expected due to their previous dependency on the tax engine.

The table below provides a detailed overview of what functionalities still work and which ones are affected by the removal of the tax engine. Not all functionalities are covered in the table. If any functionality in the payroll module doesn't work as expected, it could be due to its dependency on the now-removed tax engine.

Summary of the functionality code changes:

|Area |	Topic|	Status|
|--------|------------|-------------|
|Payroll setup|	Pay cycle and pay periods	|  Working - pay cycles and pay periods can be set up independently.|
|Payroll setup|	Payroll Calculation frequencies|	Working - pay cycle and pay cycle frequency can be set up.|
|Codes and taxes|	Earning codes and earning groups|	Working|
|Codes and taxes|	Taxes, tax regions, tax codes, and tax groups| Functionality deprecated |
|Payroll processing tasks – earning statement processing	|Generate and release earning statement for workers.|	Working - earning statements can be generated and released for a particular period.|
|Payroll processing tasks – pay statements	|All pay statements, issued, and submitted pay statements |	Functionality deprecated  |
|Payroll processing tasks – pay statement processing	|Generate, submit, and post payroll statements	|Functionality deprecated |
|Tax processing |	Tax transaction history, Tax register report	|Deprecated functionaliy. All previous records still exist, new reports can't be created.|
|Payroll positive pay|	Positive pay configuration and positive payroll setup	|Positive pay configuration and positive payroll setup doesn't work as expected.|

>[!Note]
> Pay statement generation won't work as it did in earlier versions. 


### Additional information
 - On the **Human Resources shared parameters** page, the **Payroll** tab have disabled tabs and tax can't be updated.
 - Previously generated pay statements and processed payroll still exist, new ones can't be processed or generated.
 - Customers should integrate with third-party payroll providers using the developed entities.
For more information, see:
 - [Payroll integration API introduction](hr-admin-integration-payroll-api-introduction)
 - [Payroll entities](hr-admin-integration-payroll-api-payroll-employee)


