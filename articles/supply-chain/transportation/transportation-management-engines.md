---
# required metadata

title: Transportation management engines
description: Transportation management engines define the logic that is used to generate and process transportation rates in Transportation management. 
author: Weijiesa
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: TMSFreightBillType, TMSGenericEngine, TMSMileageEngine, TMSRateEngine, TMSTransitTimeEngine, TMSZoneEngine, TMSFreightBillTypeAssignment, TMSZoneMaster, TMSEngineParameters
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: b878478c-0e04-4a1e-a037-6fdbb345a9a3
ms.search.region: Global
# ms.search.industry: 
ms.author: weijiesa
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Transportation management engines

[!include [banner](../includes/banner.md)]

Transportation management engines define the logic that is used to generate and process transportation rates in Transportation management. 

A transportation management engine calculates tasks, such as the carrier’s transportation rate. The engine system lets you change calculation strategies at runtime, based on data in Supply Chain Management. A transportation management engine resembles a plug-in that is related to a particular carrier contract.

## What engines are available?
The following table shows the transportation management engines that are available.

| Transportation management engine | Description                                                                                                                                                                                                                                                                                                                 |
|----------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Rate engine**                  | Calculates rates.                                                                                                                                                                                                                                                                                                           |
| **Generic engine**               | Simple auxiliary engines that are used by other engines that do not require data from Supply Chain Management, for example, an apportionment engine. Apportionment engines are used to reduce the final costs of transportation to specific orders and lines, based on dimensions, such as volume and weight. |
| **Mileage engine**               | Calculates the transportation distance.                                                                                                                                                                                                                                                                                     |
| **Transit time engine**          | Calculates the time that is required to travel from the start to the end destination.                                                                                                                                                                                                                                       |
| **Zone engine**                  | Calculates the zone based on the current address and calculates the number of zones that must be crossed in order to travel from address A to address B.                                                                                                                                                                    |
| **Freight bill type**            | Standardizes the freight invoice and the freight bill lines and is used for automatic freight bill matching.                                                                                                                                                                                                                |


## What engines must be configured to rate a shipment?

To rate a shipment using a specific carrier, you must configure multiple transportation management engines. The **Rate engine** is required, but other transportation management engines may be required to support the **Rate engine**. For example, the **Rate engine** can be used to retrieve data from the **Mileage engine** to calculate the rate based on mileage between the source and the destination.

## What’s required to initialize a transportation management engine?
A transportation management engine requires that you set up initialization data in order to function in a specific way. The setup can include the following types of data:
-   References to other transportation management engines. For details, see the configuration example in this section.
-   References to .NET types that are used by the transportation management engine.
-   Simple configuration data.

In most cases, you can click the **Parameters** button in the transportation management engine’s setup forms to configure the initialization data. **Example of the configuration of a rate engine that references a mileage engine** The following example shows the setup that is required for a rate engine that is based on the .NET engine type Microsoft.Dynamics.Ax.Tms.Bll.MileageRateEngine and references a mileage engine.

|          Parameter           |                                                                                  Description                                                                                  |
|------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <em>RateBaseAssigner</em>   | The .NET type that interprets the rate base assignment data for a particular schema. The syntax of the parameter value consists of two segments delimited by a vertical bar ( |
|  <em>MileageEngineCode</em>  |                       Mileage engine code that identifies the mileage engine record in the database.                        |
| <em>ApportionmentEngine</em> |                        Generic engine code that identifies the apportionment engine in the database.                        |

## How is metadata used in transportation management engines?

Transportation management engines that rely on data that is defined in Supply Chain Management can use different data schemas. The transportation management system enables different transportation management engines to use the same generic physical database tables. To make sure that run-time interpretation of engine data is correct, you can define metadata for the database tables. This reduces the cost of building new transportation management engines because additional table and form structures are not required in Operations.

## What can be used as search data in rate calculations?
The data that you use when you calculate rates is controlled by the metadata configuration. For example, if you want to search for rates based on postal codes you must set up metadata based on the lookup type of a postal code.

## Do all engine configurations require metadata?
No, transportation management engines that are used to retrieve the data that is required for rate calculation from external systems don’t need metadata. The rate data for these engines can be retrieved from external transportation carrier systems, usually through a web service. For example, can use a mileage engine that retrieves data directly from Bing maps so that you don’t need a metadata for this engine.

| **Note**                                                                                                                                                                                                                                                                                                                                                                     |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| The transportation management engines that are delivered with Supply Chain Management rely on data that is retrieved from the application. Engines that connect to external systems are not included with Operations. However, the engine-based extensibility model lets you build extensions using Visual Studio Tools. |

## How do I configure metadata for a transportation management engine?
Metadata for transportation management engines is configured differently for the different types of engines.

| Transportation management engine               | Metadata configuration                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Rate engine**                                | Requires a **Rate base type**. The rate base type contains metadata for the rate base data and the rate base assignment data. The structure of rate base metadata is determined by the type of rate engine. The structure of the rate base assignment metadata is determined by the type of rate base assigner that is associated with that rate engine. You set up the rate base type of a rate engine on the **Rate engine** page and on the **Rate master** page. |
| **Zone engine**                                | Requires metadata to be set up directly on the zone master.                                                                                                                                                                                                                                                                                                                                                                                                          |
| **Transit time engine** and **Mileage engine** | Retrieves the metadata directly from the mileage engine’s configuration setup form.                                                                                                                                                                                                                                                                                                                                                                                  |

  **Example of metadata for a rate engine** The transportation management engine requires identification of the origin address, the destination state and country/region, and the start and end point of the shipment. By using these requirements, the metadata would look like the data in the following table. The table also includes information about what type of input data is required.
-   Define this information in **Transportation management** &gt; **Setup** on the **Rate base type** page.

| Sequence | Name                          | Field type | Data type | Lookup type    | Mandatory |
|----------|-------------------------------|------------|-----------|----------------|-----------|
| 1        | Origin postal code            | Assignment | String    | Postal Code    | Selected  |
| 2        | Destination state             | Assignment | String    | State          |           |
| 3        | Destination start postal code | Assignment | String    | Postal Code    | Selected  |
| 4        | Destination end postal code   | Assignment | String    | Postal Code    | Selected  |
| 5        | Destination country           | Assignment | String    | Country/region |           |

### Whitepaper

For more information, download the following white paper (written to support AX2012, but still applies for Dynamics 365 Supply Chain Management)

- [Transportation management engines](https://download.microsoft.com/download/e/0/9/e0957665-c12f-43c7-94c0-611cc49d7d61/TransportationManagementEnginesInAX.pdf)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]