---
# required metadata

title: Worker Postal Address entity
description: This article provides details and an example query for the Hcm Worker Postal Address entity in Microsoft Dynamics 365 Human Resources.
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

# Worker Postal Address entity

> [!NOTE]
> The functionality that's noted in this article is available as of Microsoft Dynamics 365 Human Resources version 10.0.40.

This article describes the Hcm Worker Postal Address entity (PayIntV1HcmWorkerPostalAddressEntity) for Dynamics 365 Human Resources.

## Description

This entity provides information about the worker postal address.

## Properties

| Property | Physical name | Type | Use | 
|---|---|---|---|
| Effective | mserp_effective | Date time offset | Read-only |
| Addresslatitude | mserp_addresslatitude | Real | Read-only |
| Attentiontoaddressline | mserp_attentiontoaddressline | String | Read-only |
| Ispostaladdress | mserp_ispostaladdress | Enum | Read-only |
| Addressstreet | mserp_addressstreet | String | Read-only |
| Addresscityinkana | mserp_addresscityinkana | String | Read-only |
| Dunsnumber | mserp_dunsnumber | String | Read-only |
| Addressdistrictname | mserp_addressdistrictname | String | Read-only |
| Formattedaddress | mserp_formattedaddress | String | Read-only |
| Addressstate | mserp_addressstate | String | Read-only |
| Addresscity | mserp_addresscity | String | Read-only |
| Addresslocationroles | mserp_addresslocationroles | String | Read-only |
| Addressdescription | mserp_addressdescription | String | Read-only |
| Personnelnumber | mserp_personnelnumber | String | Read-only |
| Isprivate | mserp_isprivate | Enum | Read-only |
| Addresspostbox | mserp_addresspostbox | String | Read-only |
| Addressbuilding | mserp_addressbuilding | String | Read-only |
| Addresstimezone | mserp_addresstimezone | Enum | Read-only |
| Isroleinvoice | mserp_isroleinvoice | Enum | Read-only |
| Addresszipcode | mserp_addresszipcode | String | Read-only |
| Addresscountyid | mserp_addresscountyid | String | Read-only |
| Isprimarytaxregistration | mserp_isprimarytaxregistration | Enum | Read-only |
| Addresslongitude | mserp_addresslongitude | Real | Read-only |
| Addressapartment | mserp_addressapartment | String | Read-only |
| Isrolehome | mserp_isrolehome | Enum | Read-only |
| Isprimary | mserp_isprimary | Enum | Read-only |
| Addressstreetnumber | mserp_addressstreetnumber | String | Read-only |
| Addresscountryregionisocode | mserp_addresscountryregionisocode | String | Read-only |
| Isroledelivery | mserp_isroledelivery | Enum | Read-only |
| Expiration | mserp_expiration | Date time offset | Read-only |
| Addresslocationid | mserp_addresslocationid | String | Read-only |
| Buildingcompliment | mserp_buildingcompliment | String | Read-only |
| Addressstreetinkana | mserp_addressstreetinkana | String | Read-only |
| Addresscountryregionid | mserp_addresscountryregionid | String | Read-only |
| Islocationowner | mserp_islocationowner | Enum | Read-only |
| Isrolebusiness | mserp_isrolebusiness | Enum | Read-only |
| Isprivatepostaladdress | mserp_isprivatepostaladdress | Enum | Read-only |

## Example query for PayIntV1HcmWorkerPostalAddressEntity

Entity name: mserp_payintv1hcmworkerpostaladdressentities

**Request**

```HTTP
GET [Organization URI]/api/data/v9.1/mserp_payintv1hcmworkerpostaladdressentities
```

**Response**

```JSON
{  
    "mserp_addressdistrictname": "",
    "mserp_buildingcompliment": "",
    "mserp_effective": "2012-09-11T18:48:45Z",
    "mserp_addressstate": "WA",
    "mserp_isroleinvoice": 200000000,
    "mserp_dunsnumber": "",
    "mserp_personnelnumber": "000001",
    "mserp_formattedaddress": "123 Coffee Street\nSuite 300\nRedmond, WA 98052 \nUSA",
    "mserp_addresscity": "Redmond",
    "mserp_islocationowner": 200000000,
    "mserp_addresscityinkana": "",
    "mserp_isrolebusiness": 200000001,
    "mserp_addressdescription": "Contoso Entertainment System USA",
    "mserp_addressstreetinkana": "",
    "mserp_addressstreetnumber": "",
    "mserp_addressbuilding": "",
    "mserp_addresstimezone": null,
    "mserp_ispostaladdress": 200000001,
    "mserp_addressapartment": "",
    "mserp_addressstreet": "123 Coffee Street\nSuite 300",
    "mserp_addresslatitude": 0,
    "mserp_addresslocationroles": "Business",
    "mserp_addresscountryregionisocode": "US",
    "mserp_addresscountryregionid": "USA",
    "mserp_isroledelivery": 200000000,
    "mserp_attentiontoaddressline": "",
    "mserp_isrolehome": 200000000,
    "mserp_addresspostbox": "",
    "mserp_expiration": "2154-12-31T23:59:59Z",
    "mserp_isprimary": 200000000,
    "mserp_addresslongitude": 0,
    "mserp_isprimarytaxregistration": 200000000,
    "mserp_addresslocationid": "000000034",
    "mserp_isprivate": 200000000,
    "mserp_isprivatepostaladdress": 200000000,
    "mserp_addresszipcode": "98052",
    "mserp_addresscountyid": ""
}
```
