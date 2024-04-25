---

title: Business performance analytics business field mappings
description: This article provides information about field mappings in business performance analytics.
author: carylhenry
ms.author: carylhenry
ms.reviewer: twheeloc 
ms.date: 4/24/2024
ms.topic: article 

ms.custom:
ms.search.form: business-performance-analytics
audience: Application User
ms.application-unique-name: msdyn_BusinessPerformanceAnalytics
---

# Business performance analytics field mappings

> [!NOTE]
> The functionality that's described in this article is available as part of a preview release. The functionality and the content of this article are subject to change. For more information about how to participate in the public preview for Business performance analytics, contact <bpaquestions@service.microsoft.com>.

| Dimension                        | Business performance analytics table field     | Finance and operations field           | Power BI data name                            |
| -------------------------------- | ---------------------------------------------- | -------------------------------------- | --------------------------------------------- |
| dmo_sellingpartypostaladdressdim | dmo_sellingpartypostaladdress                  | LogisticsPostalAddress.Address         | Dim - Selling party.Columns.Postal address    |
| dmo_sellingpartypostaladdressdim | dmo_sellingpartypostaladdresscity              | LogisticsPostalAddress.City            | Dim - Selling party.Columns.City              |
| dmo_sellingpartypostaladdressdim | dmo_sellingpartypostaladdresscountryregion     | LogisticsPostalAddress.CountryRegionId | Dim - Selling party.Columns.Country or region |
| dmo_sellingpartypostaladdressdim | dmo_sellingpartypostaladdresscounty            | LogisticsPostalAddress.Country         | Dim - Selling party.Columns.County            |
| dmo_sellingpartypostaladdressdim | dmo_sellingpartypostaladdresskey               | LogisticsPostalAddress.RecId           | Dim - Selling party.Keys.Key                  |
| dmo_sellingpartypostaladdressdim | dmo \_sellingpartypostaladdresspartition       | LogisticsLocation.LocationId           | Dim - Selling party.Keys.Partition ID         |
| dmo_sellingpartypostaladdressdim | dmo_sellingpartypostaladdresspostalcodezipcode | LogisticsPostalAddress.ZipCode         | Dim - Selling party.Columns.Postal code       |
| dmo_sellingpartypostaladdressdim | dmo_sellingpartypostaladdressstateprovince     | LogisticsPostalAddress.State           | Dim - Selling party.Columns.State or province |
| dmo_sellingpartypostaladdressdim | dmo_sellingpartypostaladdressstreet            | LogisticsPostalAddress.Street          | Dim - Selling party.Columns.Street            |
