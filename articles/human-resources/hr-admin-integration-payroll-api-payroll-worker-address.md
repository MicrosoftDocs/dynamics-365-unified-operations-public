---
# required metadata

title: Payroll worker address API
description: This topic provides details and an example query for the Payroll worker address entity in Dynamics 365 Human Resources.
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

# Payroll worker address API

This topic provides details and an example query for the Payroll worker address entity in Dynamics 365 Human Resources.

## Properties

| Property<br>**Physical name**<br>***Type*** | Use | Description |
| --- | --- | --- |
| **City**<br>mshr_city<br>*GUID* | String<br>Required |  |
| **Personnel number**<br>mshr_personnelnumber<br>*GUID* | String<br>Required |  |
| **Country region**<br>mshr_countryregionid<br>*GUID* | String<br>Required |  |
| **Valid from**<br>mshr_postaladdressvalidfrom<br>*GUID* | Date Time Offset <br>Required |  |
| **Worked in address**<br>mshr_isworkedinaddressbr>*GUID* | Int32<br>Required | Denotes if the address is where the employee works. |
| **County**<br>mshr_county<br>*GUID* | Guid<br>Required |  |
| **Payroll worker address ID**<br>mshr_payrollworkeraddressentityid<br>*GUID* | GUID<brRequired |  |
| **Primary field**<br>mshr_primaryfield<br>*GUID* | String<br>Required |  |
| **Street**<br>mshr_street<br>*GUID* | String<br>Required |  |
| **Valid to**<br>mshr_postaladdressvalidto<br>*GUID* | Date Time Offset <br>Required |  |
| **Location ID**<br>mshr_locationidbr>*GUID* | String <br>Required |  |
| **Postal code**<br>mshr_zipcode<br>*GUID* | String <br>Required |The identifcation number defined for the employee.  |
| **Lived in address**<br>mshr_islivedinaddressbr>*GUID* | String<br>Required | Denotes if the address is where the employee lives. |
| **Middle state**<br>mshr_state<br>*GUID* | String<br>Required |  |

## Example query 

identificationtypeid

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

**Query**

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
            "mshr_street": "6543 Spruce Ave",
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
