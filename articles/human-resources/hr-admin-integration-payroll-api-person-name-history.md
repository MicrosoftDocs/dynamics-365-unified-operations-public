---
# required metadata

title: Person name history
description: This article provides details and an example query for the Person name history entity in Dynamics 365 Human Resources.
author: avanish2821
ms.date: 03/25/2026
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

Physical name: mserp_dirpersonnamehistoricalentity.

### Description

This entity provides information about the name history for a given person.

> [!IMPORTANT] 
> The **FirstName**, **MiddleName**, **LastName**, **NameValidFrom**, and **NameValidTo** fields are no longer available on the Payroll employee entity. They have been removed to ensure that only one date-effective data source backs this entity.

## Properties

| Property</br>**Physical name**</br>***Type*** | Use | Description |
| --- | --- | --- |
| **First name**</br>mserp_firstname</br>*String* | Read-only | The first name. |
| **Last name prefix**</br>mserp_lastnameprefix</br>*String*) | Read-only | The last name prefix. |
| **Last name**</br>mserp_lastname</br>*String*) | Read-only | The last name. |
| **Middle name**</br>mserp_middlename</br>*String*) | Read-only | The middle name. |
| **Valid to**</br>mserp_validto</br>*String*) | Read-only | The date that the name is valid to. |
| **Party number**</br>mserp_partynumber</br>*String* | Read-only | A user-readable, system-generated unique identifier for the person. |
| **Primary field**</br>mserp_primaryfield</br>*String* | Read-only | The unique identifier of the record. |
| **Person name history entity ID**</br>mserp_dirpersonnamehistoricalentityid</br>*GUID* | System generated | A system-generated globally unique identifier (GUID) value to uniquely identify the record. |

## Relations

| Property value | Related entity | Navigation property | Collection type |
| --- | --- | --- | --- |
| Not applicable | [mserp_payrollemployeeentity](hr-admin-integration-payroll-api-payroll-employee.md) | Not applicable | mserp_FK_PayrollEmployeeEntity_Name |

## Example query for Payroll employee

**Request**

```http
GET [Organizaton URI]/api/data/v9.1/mserp_dirpersonnamehistoricalentities?$filter=mserp_partynumber eq 'HR000001606'
```

**Response**

```json
{
    "mserp_firstname": "Agustina",
    "mserp_lastnameprefix": "",
    "mserp_lastname": "Fierro",
    "mserp_middlename": "middle",
    "mserp_validto": "2021-09-10T21:23:53Z",
    "mserp_partynumber": "HR000001606",
    "mserp_primaryfield": "HR000001606 | ",
    "mserp_dirpersonnamehistoricalentityid": "00000832-0000-0000-c12b-014105000000",
    "mserp_validfrom": null
},
{
    "mserp_firstname": "Agustina",
    "mserp_lastnameprefix": "",
    "mserp_lastname": "Fierro",
    "mserp_middlename": "",
    "mserp_validto": "2154-12-31T23:59:59Z",
    "mserp_partynumber": "HR000001606",
    "mserp_primaryfield": "HR000001606 | 9/10/2021 09:23:54 pm",
    "mserp_dirpersonnamehistoricalentityid": "00000832-0000-0000-d20b-000010000000",
    "mserp_validfrom": "2021-09-10T21:23:54Z"
}
```

## See also

[Payroll integration API introduction](hr-admin-integration-payroll-api-introduction.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
