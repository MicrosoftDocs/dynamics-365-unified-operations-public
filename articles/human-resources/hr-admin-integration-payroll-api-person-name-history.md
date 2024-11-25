---
# required metadata

title: Person name history
description: This article provides details and an example query for the Person name history entity in Dynamics 365 Human Resources.
author: twheeloc
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
ms.search.validFrom: 2021-09-01
ms.dyn365.ops.version: Human Resources
---

# Person name history



[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes the Person name history entity in Dynamics 365 Human Resources.

Physical name: mshr_dirpersonnamehistoricalentity.

### Description

This entity provides information about the name history for a given person.

> [!IMPORTANT] 
> The **FirstName**, **MiddleName**, **LastName**, **NameValidFrom**, and **NameValidTo** fields are no longer available on the Payroll employee entity. They have been removed to ensure that only one date-effective data source backs this entity.

## Properties

| Property</br>**Physical name**</br>***Type*** | Use | Description |
| --- | --- | --- |
| **First name**</br>mshr_firstname</br>*String* | Read-only | The first name. |
| **Last name prefix**</br>mshr_lastnameprefix</br>*String*) | Read-only | The last name prefix. |
| **Last name**</br>mshr_lastname</br>*String*) | Read-only | The last name. |
| **Middle name**</br>mshr_middlename</br>*String*) | Read-only | The middle name. |
| **Valid to**</br>mshr_validto</br>*String*) | Read-only | The date that the name is valid to. |
| **Party number**</br>mshr_partynumber</br>*String* | Read-only | A user-readable, system-generated unique identifier for the person. |
| **Primary field**</br>mshr_primaryfield</br>*String* | Read-only | The unique identifier of the record. |
| **Person name history entity ID**</br>mshr_dirpersonnamehistoricalentityid</br>*GUID* | System generated | A system-generated globally unique identifier (GUID) value to uniquely identify the record. |

## Relations

| Property value | Related entity | Navigation property | Collection type |
| --- | --- | --- | --- |
| Not applicable | [mshr_payrollemployeeentity](hr-admin-integration-payroll-api-payroll-employee.md) | Not applicable | mshr_FK_PayrollEmployeeEntity_Name |

## Example query for Payroll employee

**Request**

```http
GET [Organizaton URI]/api/data/v9.1/mshr_dirpersonnamehistoricalentities?$filter=mshr_partynumber eq 'HR000001606'
```

**Response**

```json
{
    "mshr_firstname": "Agustina",
    "mshr_lastnameprefix": "",
    "mshr_lastname": "Fierro",
    "mshr_middlename": "middle",
    "mshr_validto": "2021-09-10T21:23:53Z",
    "mshr_partynumber": "HR000001606",
    "mshr_primaryfield": "HR000001606 | ",
    "mshr_dirpersonnamehistoricalentityid": "00000832-0000-0000-c12b-014105000000",
    "mshr_validfrom": null
},
{
    "mshr_firstname": "Agustina",
    "mshr_lastnameprefix": "",
    "mshr_lastname": "Fierro",
    "mshr_middlename": "",
    "mshr_validto": "2154-12-31T23:59:59Z",
    "mshr_partynumber": "HR000001606",
    "mshr_primaryfield": "HR000001606 | 9/10/2021 09:23:54 pm",
    "mshr_dirpersonnamehistoricalentityid": "00000832-0000-0000-d20b-000010000000",
    "mshr_validfrom": "2021-09-10T21:23:54Z"
}
```

## See also

[Payroll integration API introduction](hr-admin-integration-payroll-api-introduction.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
