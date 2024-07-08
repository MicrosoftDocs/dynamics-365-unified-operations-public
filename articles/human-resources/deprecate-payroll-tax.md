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

As announced earlier, the Tax updates are retired for the US payroll feature in Microsoft Dynamics 365 Finance from 10.0.40 release. Customers can choose from different third-party solutions available on AppSource and other integrations with Dynamics 365 Human Resources.
What was done? 
The tax engine code was removed from the system, and significant code modifications were made to accommodate this change. Specifically, all instances of the ste.taxengine classes that were directly used in the codebase were eliminated, and other parts of the code that referenced ste.taxengine were adjusted to return default values or null. Due to these changes, some of the payroll functionalities may not work as expected due to their previous dependency on the tax engine.
The table below provides a detailed overview of what functionalities still work and which ones are affected by the removal of the tax engine. However, please note that not all functionalities are covered in the table. If any functionality in the payroll module does not work as expected, it could be due to its dependency on the now-removed tax engine.
Summary of the functionality code changes,

Area	Topic	Status
Payroll Setup	Pay cycle and pay periods	Working. We can set up pay cycle and pay periods independently.
Payroll Setup	Payroll Calculation frequencies	Working. We can set up pay cycle and pay cycle frequency.
Codes and Taxes	Earning codes and earning groups	Working as expected.
Codes and Taxes	Taxes, tax regions, tax codes, and tax groups	Not working
Payroll Processing tasks – Earning Statement processing	Generate & release earning statement for workers	Working. We can generate and release earning statements for a particular period
Payroll processing tasks – Pay Statements	All pay statements, Issued & Submitted pay statements 	Not working. 
Payroll Processing tasks – Pay statement processing	Generate, submit & post payroll statements	Not working.
Tax processing 	Tax transaction history, Tax register report	Not working. All previous records would exist as is, however there would be no new reports created.
Payroll positive pay	Positive pay configuration and positive payroll setup	Positive pay configuration and positive payroll setup are working. However, since a pay statement has to be generated and it would not work as expected.

Note: All functionality related to pay statement generation would not work as it did before. 

Note : In the Human Resources shared parameters, the Payroll tab will have values disabled and you would no longer be able to update tax. 

Note : Some of the generated pay statements or processed payroll in the past will still exist in the system. However, new ones cannot be processed or generated. 

In summary, the US Payroll module would be of limited use since it lacks functionality for payroll processing tasks, payment processing and pay statement generation. We recommend that customers instead integrate with third-party payroll providers using the entities developed for the same. You can view the details of the list of entities here - Introduction and List of entities
Additional Information:
When a functionality that no longer works, is triggered, an error message would pop saying:
“This functionality is no longer supported due to one or more dependencies on the deprecated tax updates for the U.S. payroll feature. For further details, please refer to the following documentation: https://aka.ms/uspayrolltaxupdates.”
In-app banner: There is also an in-app banner informing users that from 10.0.40, the tax updates have been deprecated.
