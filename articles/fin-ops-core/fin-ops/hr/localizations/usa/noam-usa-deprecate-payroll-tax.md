---
# required metadata

title: Deprecation of US payroll tax updates
description: This article describes the deprecation of tax updates for US payroll.
author: jaredha
ms.date: 08/08/2024
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

This article describes the deprecation of tax updates for US payroll.

As of the 10.0.40 release of Microsoft Dynamics 365 Finance, tax updates are retired for the US payroll feature. Customers can now choose among different third-party solutions that are available on AppSource and other integrations with Dynamics 365 Human Resources.

## What was done?

The tax engine code was removed, and significant code modifications were made to accommodate this change. All the `ste.taxengine` classes that were directly used in the codebase were eliminated. Other parts of the code that referenced `ste.taxengine` were adjusted so that they return default values or null. Because of these changes, some payroll functionality that previously depended on the tax engine might not work as expected.

### Summary of the functionality code changes

The following table provides a detailed overview of functionality that still works and functionality that is affected by the removal of the tax engine. The table doesn't cover all functionality. If any functionality in the **Payroll** module doesn't work as expected, a dependency on the now-removed tax engine might be the cause.

| Area | Functionality | Status |
|------|---------------|--------|
| Payroll setup | Pay cycles and pay periods | Working. Pay cycles and pay periods can be set up independently. |
| Payroll setup | Payroll calculation frequencies | Working. Pay cycle and pay cycle frequency can be set up. |
| Earning codes  |	Earning codes and earning groups |	Working. |
| Tax codes | Taxes, tax regions, tax codes, and tax groups | *Limited. |
| Payroll processing tasks – earning statement processing | Generate and release earning statements for workers | Working. Earning statements can be generated and released for a specific period. |
| Payroll processing tasks – pay statements | All pay statements, issued pay statements, and submitted pay statements | *Limited. |
| Payroll processing tasks – pay statement processing | Generate, submit, and post payroll statements | *Limited. |
| Tax processing | Tax transaction history, tax register report | *Limited. All previous records still exist, but new reports can't be created. |
| Payroll positive pay | Positive pay configuration and positive payroll setup | Positive pay configuration and positive payroll setup are working. However, because a pay statement has to be generated and it won't work as expected. |
|Benefits	|Benefits including garnishments and tax levies| *Limited. |

*Functionality is limited. For more details, see [Issue search in Lifecycle services](../../../../dev-itpro/lifecycle-services/issue-search-lcs.md). If you can't find the information you need, contact support.

> [!NOTE]
> Pay statement generation doesn't work as it worked in earlier versions.

### Additional information

- On the **Human Resources shared parameters** page, the **Payroll** tab has disabled tabs, and tax can't be updated.
- Previously generated pay statements and processed payroll still exist. However, new ones can't be processed or generated.
- Customers should integrate with third-party payroll providers by using the developed entities. For more information, see the following articles:

    - [Payroll integration API introduction](/dynamics365/human-resources/hr-admin-integration-payroll-api-introduction)
    - [Payroll entities](/dynamics365/human-resources/hr-admin-integration-payroll-api-payroll-employee)
