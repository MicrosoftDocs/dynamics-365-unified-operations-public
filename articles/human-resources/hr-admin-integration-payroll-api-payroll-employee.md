---
# required metadata

title: Payroll employee
description: This article provides details and an example query for the Payroll employee entity in Dynamics 365 Human Resources.
author: jcart
ms.date: 07/09/2024
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
ms.author: ajitchandran
ms.search.validFrom: 2021-04-07
ms.dyn365.ops.version: Human Resources
---

# Payroll employee



[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes the Payroll employee entity for Dynamics 365 Human Resources.

Physical name: mshr_payrollemployeeentity.

### Description

This entity provides information about the employee. You must set the [payroll integration parameters](hr-admin-integration-payroll-api-parameters.md) before using this entity.

>[!IMPORTANT] 
>**FirstName**, **MiddleName**, **LastName**, **NameValidFrom**, and **NameValidTo** fields are no longer available on this entity. This ensures that there is only one date effective datasource that backs this entity.
>These fields will be available on the **DirPersonNameHistoricalEntity**, which was released in Platform update 43. There is an OData relationship from **PayrollEmployeeEntity** to **DirPersonNameHistoricalEntity**. 

## Properties

| Property</br>**Physical name**</br>***Type*** | Use | Description |
| --- | --- | --- |
| **Legal entity ID**</br>mshr_legalentityid</br>*String* | Read-only | Specifies the legal entity (company). |
| **Personnel number**</br>mshr_personnelnumber</br>*String* | Read-only | The employee's unique personnel number. |
| **Employment start date**</br>mshr_employmentstartdate</br>*Date time offset* | Read-only | The start date of the employee's employment. |
| **Employment end date**</br>mshr_employmentenddate</br>*Date time offset* | Read-only |The end of the employee's employment.  |
| **Birth date**</br>mshr_birthdate</br>*Date Time Offset* | Read-only | The employee's birth date. |
| **Gender**</br>mshr_gender</br>[mshr_hcmpersongender option set](hr-admin-integration-payroll-api-gender.md) | Read-only | The employee's gender. |
| **Employment type**</br>mshr_employmenttype</br>[mshr_hcmemploymenttype option set](hr-admin-integration-payroll-api-hcmemploymenttype.md) | Read-only | The employment type. |
| **Identification type ID**</br>mshr_identificationtypeid</br>*String* |Read-only | The identification type defined for the employee. |
| **Identification number to**</br>mshr_identificationnumber</br>*String* | Read-only |The identification number defined for the employee. |
| **Ready to pay**</br>mshr_readytopay</br>[mshr_noyes option set](hr-admin-integration-payroll-api-no-yes.md) | Read-only | Indicates if the employee is marked as ready to pay. |
| **Payroll employee entity ID**</br>mshr_payrollemployeeentityid</br>*GUID* | System generated | A system-generated globally unique identifier (GUID) value to uniquely identify the employee. |

## Relations

|Property value | Related entity | Navigation property | Collection type |
| --- | --- | --- | --- |
| _mshr_fk_employment_id_value | mshr_hcmemploymentdetailentity | mshr_FK_Employment_id | mshr_FK_HcmEmploymentDetailEntity_PayrollEmployee |
| _mshr_fk_fixedcompplan_id_value | [mshr_payrollfixedcompensationplanentity](hr-admin-integration-payroll-api-payroll-fixed-compensation-plan.md) | mshr_FK_FixedCompPlan_id | mshr_FK_PayrollFixedCompensationPlanEntity_Employee |
| _mshr_fk_name_id_value | mshr_dirpersonnamehistoricalentity | mshr_FK_Name_id | - |
| _mshr_fk_worker_id_value | mshr_hcmworkerbaseentity | mshr_FK_Worker_id | mshr_FK_HcmWorkerBaseEntity_PayrollEmployee |
| _mshr_fk_workerbankaccount_id_value | mshr_hcmworkerbankaccountentity | mshr_FK_WorkerBankAccount_id | mshr_FK_HcmWorkerBankAccountEntity_PayrollEmployee |
| _mshr_fk_variablecompaward_id_value | [mshr_payrollvariablecompensationawardentity](hr-admin-integration-payroll-api-payroll-variable-compensation-plan.md) | mshr_FK_VariableCompAward_id | mshr_FK_PayrollVariableCompensationAwardEntity_Employee |
| _mshr_fk_address_id_value | [mshr_payrollworkeraddressentity](hr-admin-integration-payroll-api-payroll-worker-address.md) | mshr_FK_Address_id | mshr_FK_PayrollWorkerAddressEntity_Worker |

## Example query for Payroll employee

**Request**

```http
GET [Organizaton URI]/api/data/v9.1/mshr_payrollemployeeentities?$filter=mshr_personnelnumber eq '000041'
```

**Response**

```json
{
    "mshr_legalentityid": "USMF",
    "mshr_personnelnumber": "000041",
    "mshr_employmentstartdate": "2011-04-05T07:00:00Z",
    "mshr_employmentenddate": "2154-12-31T23:59:59Z",
    "mshr_birthdate": "1987-09-12T00:00:00Z",
    "mshr_gender": 200000002,
    "mshr_employmenttype": 200000000,
    "mshr_identificationtypeid": "SSN",
    "mshr_identificationnumber": "888-99-9342",
    "mshr_readytopay": 200000000,
    "mshr_dataareaid": "USMF",
    "mshr_primaryfield": "000041 | USMF | 4/5/2011 07:00:00 am",
    "_mshr_fk_employment_id_value": "00000d4e-0000-0000-0600-014105000000",
    "_mshr_fk_fixedcompplan_id_value": "00000598-0000-0000-4cd0-fda002000000",
    "_mshr_fk_name_id_value": "00000832-0000-0000-d700-014105000000",
    "_mshr_fk_worker_id_value": "000000af-0000-0000-d5ff-004105000000",
    "_mshr_fk_workerbankaccount_id_value": "000006f2-0000-0000-b7ff-004105000000",
    "mshr_payrollemployeeentityid": "00000666-0000-0000-d5ff-004105000000",
    "_mshr_fk_address_id_value": null,
    "_mshr_fk_variablecompaward_id_value": null,
    "_mshr_dataareaid_id_value": null
}
```

## See also

[Payroll integration API introduction](hr-admin-integration-payroll-api-introduction.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
