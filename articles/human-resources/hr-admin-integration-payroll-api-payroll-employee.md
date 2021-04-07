---
# required metadata

title: Payroll employee API
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

# Payroll employee API

## Properties

| Property<br>**Physical name**<br>***Type*** | Use | Description |S
| --- | --- | --- |
| **Personnel number**<br>mshr_personnelnumber<br>*GUID* | String<br>Required |  |
| **Primary field**<br>mshr_primaryfield<br>*GUID* | String<br>Required |  |
| **Last name**<br>mshr_lastname<br>*GUID* | String<br>Required |  |
| **Legal entity ID**<br>mshr_legalentityID<br>*GUID* | String<br>Required |  |
| **Valid from**<br>mshr_namevalidfrom<br>*GUID* | Date Time Offset <br>Required |  |
| **Gender*<br>mshr_gender<br>*GUID* | Int32<br>Required |  |
| **Payroll employee entity ID**<br>mshr_payrollemployeeentityid<br>*GUID* | Guid<br>Required |  |
| **Employment start date**<br>mshr_employmentstartdate<br>*GUID* | Date time offset<br>Required |  |
| **Identification type ID**<br>mshr_identificationtypeid<br>*GUID* |String<br>Required | The identification type defined for the employee. |
| **Employment end date*<br>mshr_employmentenddate<br>*GUID* | Date time offset<br>Required |  |
| **Data area ID*<br>mshr_dataareaid_id<br>*GUID* | Guid<br>Required |  |
| **Valid to**<br>mshr_namevalidto<br>*GUID* | Date Time Offset <br>Required |  |
| **Birthdate**<br>mshr_birthdate<br>*GUID* | Date Time Offset <br>Required |  |
| **Identification number to**<br>mshr_identificationnumber<br>*GUID* | String <br>Required |The identification number defined for the employee.  |
| **First name**<br>mshr_firstname<br>*GUID* | String<br>Required |  |
| **Middle name**<br>mshr_middlename<br>*GUID* | String<br>Required |  |

## Example query for Payroll employee

identificationtypeid
[!include [Applies to Human Resources](../includes/applies-to-hr.md)]
W
**Query**

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