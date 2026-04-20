---
# required metadata

title: Worker Bank Account entity
description: This article provides details and an example query for the Worker Bank Account entity in Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.date: 02/20/2026
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
ms.author: twheeloc
ms.search.validFrom: 2021-04-07
ms.dyn365.ops.version: Human Resources
---

# Worker Bank Account entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.39.

This article describes the Worker Bank Account entity (PayIntV1WorkerBankAccountEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about bank account of worker.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Accountidentification | mserp_accountidentification | String | Read-only |
| Internetaddress | mserp_internetaddress | String | Read-only |
| Addressstreet | mserp_addressstreet | String | Read-only |
| Swiftno | mserp_swiftno | String | Read-only |
| Mobilephone | mserp_mobilephone | String | Read-only |
| Addresslocationid | mserp_addresslocationid | String | Read-only |
| Bankiban | mserp_bankiban | String | Read-only |
| Bankaccounttype | mserp_bankaccounttype | Enum | Read-only |
| Personnelnumber | mserp_personnelnumber | String | Read-only |
| Addressdistrictname | mserp_addressdistrictname | String | Read-only |
| Branchnumber | mserp_branchnumber | String | Read-only |
| Extension | mserp_extension | String | Read-only |
| Addressdescription | mserp_addressdescription | String | Read-only |
| Addresscounty | mserp_addresscounty | String | Read-only |
| Fax | mserp_fax | String | Read-only |
| Addressstate | mserp_addressstate | String | Read-only |
| Telexnumber | mserp_telexnumber | String | Read-only |
| Routingnumbertype | mserp_routingnumbertype | Enum | Read-only |
| Routingnumber | mserp_routingnumber | String | Read-only |
| Addressstreetnumber | mserp_addressstreetnumber | String | Read-only |
| Addressvalidfrom | mserp_addressvalidfrom | Date time offset | Read-only |
| Nameofperson | mserp_nameofperson | String | Read-only |
| Addresspostbox | mserp_addresspostbox | String | Read-only |
| Name | mserp_name | String | Read-only |
| Addressbuildingcompliment | mserp_addressbuildingcompliment | String | Read-only |
| Branchname | mserp_branchname | String | Read-only |
| Email | mserp_email | String | Read-only |
| Addresscountryregionid | mserp_addresscountryregionid | String | Read-only |
| Addresscity | mserp_addresscity | String | Read-only |
| Banklocationcode | mserp_banklocationcode | String | Read-only |
| Telephone | mserp_telephone | String | Read-only |
| Addresszipcode | mserp_addresszipcode | String | Read-only |
| Accountholder | mserp_accountholder | String | Read-only |
| Bankaccountnumber | mserp_bankaccountnumber | String | Read-only |
| Addresscountryregionisocode | mserp_addresscountryregionisocode | String | Read-only |
| Addressvalidto | mserp_addressvalidto | Date time offset | Read-only |

## Example query for PayIntV1WorkerBankAccountEntity

Entity name: mserp_payintv1workerbankaccountentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1workerbankaccountentities
```

**Response**

```JSON
{  
    "mserp_accountidentification": "Checking1",
    "mserp_internetaddress": "",
    "mserp_addressstreet": "",
    "mserp_swiftno": "",
    "mserp_mobilephone": "",
    "mserp_addresslocationid": "",
    "mserp_bankiban": "",
    "mserp_bankaccounttype": 200000000,
    "mserp_personnelnumber": "000028",
    "mserp_addressdistrictname": "",
    "mserp_branchnumber": "",
    "mserp_extension": "",
    "mserp_addressdescription": "",
    "mserp_addresscounty": "",
    "mserp_fax": "",
    "mserp_addressstate": "",
    "mserp_telexnumber": "",
    "mserp_routingnumbertype": 200000000,
    "mserp_routingnumber": "876543291",
    "mserp_addressstreetnumber": "",
    "mserp_addressvalidfrom": "2024-01-01T00:00:00Z",
    "mserp_nameofperson": "",
    "mserp_addresspostbox": "",
    "mserp_name": "Checking 1",
    "mserp_addressbuildingcompliment": "",
    "mserp_branchname": "",
    "mserp_email": "",
    "mserp_addresscountryregionid": "",
    "mserp_addresscity": "",
    "mserp_banklocationcode": "",
    "mserp_telephone": "",
    "mserp_addresszipcode": "",
    "mserp_accountholder": "",
    "mserp_bankaccountnumber": "999999",
    "mserp_addresscountryregionisocode": "",
    "mserp_addressvalidto": "2024-01-01T00:00:00Z"
}
```
