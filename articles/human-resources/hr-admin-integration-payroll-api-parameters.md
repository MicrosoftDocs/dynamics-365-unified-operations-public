---
# required metadata

title: Payroll integration parameters
description: This topic describes the Dynamics 365 Human Resources Payroll integration parameters.
author: marcelbf
ms.date: 06/17/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: marcelbf
ms.search.validFrom: 2021-06-17
ms.dyn365.ops.version: Human Resources
---

# Payroll integration parameters


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

Before using the Dynamics 365 Human Resources Payroll integration, you must set up the parameters described in this topic.

## Enable payroll address

To be able to use the payroll address, you must enable it from the [shared parameters form](hr-setup-shared-parameters.md) on the Payroll integration tab.

## Define the identification type

To expose the identification type ID in the [payroll employee entity](hr-admin-integration-payroll-api-payroll-employee.md), you must [configure human resources parameters](hr-setup-shared-parameters.md) for each company.

1. In the **Compensation management** workspace, under links, select **Human Resources Parameters**. 
2. On the **Payroll integration** tab, specify the value of the following fields.

| Field | Description |
| --- | --- |
| Use identification types in payroll processing | When this option is selected, the selected type ID will be exposed in the payroll employee entity. |
| Identification type | The identification type to be exposed in the field **mshr_payrollemployeeentityid** of the [payroll employee entity](hr-admin-integration-payroll-api-payroll-employee.md). |

## See also

[Payroll integration API introduction](hr-admin-integration-payroll-api-introduction.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
