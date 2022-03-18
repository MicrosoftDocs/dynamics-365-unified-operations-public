---
# required metadata

title: Compensation pay frequency
description: This topic provides details and an example query for the Compensation pay frequency entity in Dynamics 365 Human Resources.
author: marcelbf
ms.date: 09/01/2021
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
ms.search.validFrom: 2021-09-01
ms.dyn365.ops.version: Human Resources
---

# Compensation pay frequency


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic describes the Compensation pay frequency entity in Dynamics 365 Human Resources.

Physical name: mshr_hcmpayrateconversionentity.

### Description

This entity provides information about the pay rate conversion for a given compensation pay frequency.

## Properties

| Property</br>**Physical name**</br>***Type*** | Use | Description |
| --- | --- | --- |
| **Annual pay rate conversion**</br>mshr_annualconversionfactor</br>*Decimal* | Read-only | The annual conversion factor for the payment frequency. |
| **Description**</br>mshr_description</br>*String* | Read-only | The description of the conversion rate. |
| **Hourly pay rate conversion**</br>mshr_hourlyconversionfactor</br>*Decimal* | Read-only | The hourly conversion factor for the payment frequency. |
| **Monthly pay rate conversion**</br>mshr_monthlyconversionfactor</br>*Decimal* | Read-only | The monthly conversion factor for the payment frequency. |
| **Pay rate conversion**</br>mshr_payrateconversion</br>*String* | Read-only | A unique string to identify the conversion rate. |
| **Period**</br>mshr_period</br>*period option set* | Read-only | The main period for the given pay rate conversion. |
| **Weekly pay rate conversion**</br>mshr_weeklyconversionfactor</br>*Decimal* | Read-only | The weekly conversion factor for the payment frequency. |
| **Data area id**</br>mshr_dataareaid</br>*String* | Read-only | The legal entity (company). |
| **Compensation pay frequency entity ID**</br>mshr_dirpersonnamehistoricalentityid</br>*GUID* | System generated | A system-generated globally unique identifier (GUID) value to uniquely identify the record. |

## Example query for Payroll employee

**Request**

```http
GET [Organizaton URI]/api/data/v9.1/mshr_hcmpayrateconversionentities?$filter=mshr_payrateconversion eq 'Annual' and mshr_dataareaid eq 'usmf'
```

**Response**

```json
{
    "mshr_annualconversionfactor": 1,
    "mshr_description": "Annual",
    "mshr_hourlyconversionfactor": 0.0004807692,
    "mshr_monthlyconversionfactor": 0.0833333333,
    "mshr_payrateconversion": "Annual",
    "mshr_period": 200000000,
    "mshr_weeklyconversionfactor": 0.0192307692,
    "mshr_dataareaid": "usmf",
    "mshr_hcmpayrateconversionentityid": "0000056e-0000-0000-b027-fef003000000",
    "_mshr_dataareaid_id_value": null
}
```

## See also

[Payroll integration API introduction](hr-admin-integration-payroll-api-introduction.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
