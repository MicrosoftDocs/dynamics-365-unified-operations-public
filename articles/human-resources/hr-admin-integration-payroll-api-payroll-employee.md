---
# required metadata

title: Payroll employee
description: This topic provides details and an example query for the Payroll employee entity in Dynamics 365 Human Resources.
author: jcart
manager: tfehr
ms.date: 04/07/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jcart
ms.search.validFrom: 2021-04-07
ms.dyn365.ops.version: Human Resources
---

# Payroll employee

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic provides details and an example query for the Payroll employee entity in Dynamics 365 Human Resources.

## Properties

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| **Personnel number**<br>mshr_personnelnumber<br>*String* | Read-only<br>Required | The employee's unique personnel number. |
| **Primary field**<br>mshr_primaryfield<br>*String* | Required<br>System generated |  |
| **Last name**<br>mshr_lastname<br>*String* | Read only<br>Required | Employee last name. |
| **Legal entity ID**<br>mshr_legalentityID<br>*String* | Read-only<br>Required | Specifies the legal entity (company). |
| **Valid from**<br>mshr_namevalidfrom<br>*Date Time Offset* | Read-only <br>Required | Date the employee information is valid from.  |
| **Gender**<br>mshr_gender<br>*Int32* | Read-only<br>Required | The employee's gender. |
| **Payroll employee entity ID**<br>mshr_payrollemployeeentityid<br>*GUID* | Required<br>System generated | A system-generated GUID value to uniquely identify the employee. |
| **Employment start date**<br>mshr_employmentstartdate<br>*Date time offset* | Read-only<br>Required | The start date of the employee's employment. |
| **Identification type ID**<br>mshr_identificationtypeid<br>*String* |Read-only<br>Required | The identification type defined for the employee. |
| **Employment end date**<br>mshr_employmentenddate<br>*Date time offset* | Read-only<br>Required |The end of the employee's employment.  |
| **Data area ID**<br>mshr_dataareaid_id<br>*GUID* | Required <br>System generated | System-generated GUID value identifying the legal entity (company). |
| **Valid to**<br>mshr_namevalidto<br>*Date Time Offset* |  Read-only<br>Required | Date the employee information is valid to. |
| **Birth date**<br>mshr_birthdate<br>*Date Time Offset* | Read-only <br>Required | The employee's birth date |
| **Identification number to**<br>mshr_identificationnumber<br>*String* | Read-only <br>Required |The identification number defined for the employee.  |
| **First name**<br>mshr_firstname<br>*String* | Read-only<br>Required | Employee first name. |
| **Middle name**<br>mshr_middlename<br>*String* | Read-only<br>Required |Employee middle name.  |

## Example query for Payroll employee

**Request**

```http
GET [Organizaton URI]/api/data/v9.1/mshr_payrollemployeeentities?$filter=mshr_personnelnumber eq @personnelnumber and mshr_identificationtypeid eq @idtype and mshr_namevalidfrom le @asofdate and mshr_namevalidto ge @asofdate&@personnelnumber='000041'&@idtype='SSN'&@asofdate=2021-04-01
```

**Response**

```json
{
	     "mshr_legalentityid": "USMF",
            "mshr_personnelnumber": "000041",
            "mshr_employmentstartdate": "2011-04-05T07:00:00Z",
            "mshr_employmentenddate": "2154-12-31T23:59:59Z",
            "mshr_firstname": "Cassie",
            "mshr_middlename": "Lassie",
            "mshr_lastname": "Hicks",
            "mshr_namevalidfrom": "2021-03-12T20:34:25Z",
            "mshr_namevalidto": "2154-12-31T23:59:59Z",
            "mshr_birthdate": "1987-09-12T00:00:00Z",
            "mshr_gender": 200000002,
            "mshr_identificationtypeid": "SSN",
            "mshr_identificationnumber": "888-99-9342",
            "mshr_dataareaid": "USMF",
            "mshr_primaryfield": "000041 | USMF | 4/5/2011 07:00:00 am",
            "_mshr_fk_worker_id_value": "000000ad-0000-0000-d5ff-004105000000",
            "_mshr_fk_employment_id_value": "00000d0d-0000-0000-0600-014105000000",
            "_mshr_fk_fixedcompplan_id_value": "0000029f-0000-0000-d5ff-004105000000",
            "mshr_payrollemployeeentityid": "00000d3c-0000-0000-d5ff-004105000000",
            "_mshr_dataareaid_id_value": null
}
```
