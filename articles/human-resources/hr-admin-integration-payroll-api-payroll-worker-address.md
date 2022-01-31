---
# required metadata

title: Payroll worker address
description: This topic provides details and an example query for the Payroll worker address entity in Dynamics 365 Human Resources.
author: jcart
ms.date: 04/07/2021
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
ms.author: jcart
ms.search.validFrom: 2021-04-07
ms.dyn365.ops.version: Human Resources
---

# Payroll worker address


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic describes the Payroll worker address entity for Dynamics 365 Human Resources.

Physical name: mshr_payrollworkeraddressentity.

### Description

This entity provides the payroll residency location and payroll work location for a given employee.

## Properties

| Property</br>**Physical name**</br>***Type*** | Use | Description |
| --- | --- | --- |
| **Personnel number**</br>mshr_personnelnumber</br>*String* | Read-only | The employee's unique personnel number. |
| **Location ID**</br>mshr_locationidbr>*String* | Read-only | The ID for the address. |
| **Lived in address**</br>mshr_islivedinaddressbr </br> *[mshr_NoYes option set](hr-admin-integration-payroll-api-no-yes.md)* | Read-only | A value that indicates whether the address is where the employee lives. |
| **Worked in address** </br> mshr_isworkedinaddressbr </br>*[mshr_NoYes option set](hr-admin-integration-payroll-api-no-yes.md)* | Read-only | A value that indicates whether the address is where the employee works. |
| **Country region**</br>mshr_countryregionid</br>*String* | Read-only</br>Required | The country or region that is defined for the address. |
| **Postal code**</br>mshr_zipcode<br>*String* | Read-only | The identification number that is defined for the employee. |
| **Street**</br>mshr_street</br>*String* | Read-only | The street that is defined for the address. |
| **City**</br>mshr_city</br>*String* | Read-only | The city that is defined for the address. |
| **State**</br>mshr_state</br>*String* | Read-only | The state or province that is defined for the address. |
| **County**</br>mshr_county</br>*String* | Read-only | The county that is defined for the address. |
| **Valid from**</br>mshr_postaladdressvalidfrom</br>*Date Time Offset* | Read-only | The date that the address is valid from. |
| **Valid to**</br>mshr_postaladdressvalidto</br>*Date Time Offset* | Read-only | The date that the address is valid to. |
| **Primary field**</br>mshr_primaryfield</br>*String* | Read-only | The primary field. |
| **Payroll worker address ID**</br>mshr_payrollworkeraddressentityid</br>*GUID* | System generated | A system-generated globally unique identifier (GUID) value to uniquely identify the address. |

## Relations

| Property value | Related entity | Navigation property | Collection type |
| --- | --- | --- | --- |
| _mshr_fk_worker_id_value | [mshr_payrollemployeeentity](hr-admin-integration-payroll-api-payroll-employee.md) | mshr_FK_Worker_id | mshr_FK_PayrollEmployeeEntity_Address |

## Example query

**Request**

```http
GET [Organizaton URI]/api/data/v9.1/mshr_payrollworkeraddressentities?$filter=mshr_personnelnumber eq @personnelnumber and mshr_postaladdressvalidfrom le @asofdate and mshr_postaladdressvalidto ge @asofdate&@personnelnumber='000041'&@asofdate=2021-04-01
```

**Response**

```json
{
    "mshr_personnelnumber": "000041",
    "mshr_locationid": "000000538",
    "mshr_islivedinaddress": 200000001,
    "mshr_isworkedinaddress": 200000000,
    "mshr_countryregionid": "USA",
    "mshr_zipcode": "99025",
    "mshr_street": "6543 Cypress Ave",
    "mshr_city": "Tacoma",
    "mshr_state": "WA",
    "mshr_county": "KING",
    "mshr_postaladdressvalidfrom": "2012-09-20T20:14:27Z",
    "mshr_postaladdressvalidto": "2154-12-31T23:59:59Z",
    "mshr_primaryfield": "000041 | 000000538 | 9/20/2012 08:14:27 pm",
    "_mshr_fk_worker_id_value": "00000d3c-0000-0000-d5ff-004105000000",
    "mshr_payrollworkeraddressentityid": "000006f0-0000-0000-f90f-014105000000"

}
```

## See also

[Payroll integration API introduction](hr-admin-integration-payroll-api-introduction.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
