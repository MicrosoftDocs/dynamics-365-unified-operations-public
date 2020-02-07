---
# required metadata

title: Choose a data integration technology
description: This article provides guidance on various options for integrating with data managed by Human Resources, describing the characteristics of different integration technologies so that integrators can make informed decisions regarding which technologies best fit their needs.
author: andreabichsel
manager: AnnBe
ms.date: 02/03/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-human-resources
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Choose a data integration technology

Dynamics 365 Human Resources manages business data that is useful in a variety of business processes. This article provides guidance on various options for
integrating with data managed by Human Resources, describing the characteristics of different integration technologies so that integrators can
make informed decisions regarding which technologies best fit their needs.

## Data integration vision

Microsoft sees business data as a key asset that makes your company unique. Your
business's data is highly valuable. Data gathered and maintained by one part of
the business relates to data gathered by another part of the business, and these
relations can be used to improve business processes and business intelligence
across your organization. Providing easy, secure, stable access to your business
data, regardless of which system “owns” the data is a key tenet to the vision we
have for data integration with Human Resources.

Historically, integrating data between multiple systems has been difficult.
Microsoft is taking steps to make data integration easier, and a large step
toward that goal is realized through [Common Data Service](https://docs.microsoft.com/powerapps/maker/common-data-service/data-platform-intro).

Going forward, Human Resources is making Common Data Service the preferred
public interface for Human Resources data. Over time, we expect that all the most important data managed by Human Resources will be exposed in Common Data Service. We recommend Common Data Service as the technology of choice for most integrating applications. While we realize that not all data your application may require is currently present in Common Data Service, and that your project timelines may require an alternative technology, please let us know when Common Data Service does not meet your integration needs.

## Integration technologies

The following sections describe the different data integration technologies
available for use with Human Resources.

### Common Data Service entities

Common Data Service is the preferred public data interface for Human Resources. Common Data Service is built on a mature platform, having grown out of the Dynamics 365 “XRM” platform, upon which the [Dynamics 365 Customer
Engagement](https://docs.microsoft.com/dynamics365/#pivot=business-apps&panel=customer-engagement) solutions are built.

Common Data Service provides a platform for data entities and an API for accessing those entities. When Human Resources is deployed in your organization, Human Resources is connected to a Common Data Service instance and the entities that maintain Human Resources data are deployed into that Common Data Service instance, making the entities and their data available to any application that can connect to the Common Data Service instance. Depending on which Human Resources apps you are using, Human Resources either performs data operations directly against the Common Data Service entities (this is the case for Attract and Onboard) or synchronizes data to/from the Common Data Service entities.

Once the data entities that expose the data your integrating apps require are
present in Common Data Service, you can make full use of [Common Data Service and the APIs it supports](https://docs.microsoft.com/powerapps/#pivot=home&panel=developer). Among the supported APIs is the [Dynamics 365 Web
API](https://docs.microsoft.com/dynamics365/customer-engagement/developer/use-microsoft-dynamics-365-web-api), which provides an OData implementation for accessing Common Data Service data.

The Common Data Service entities and the associated APIs are the best option for accessing Human Resources data from web applications, web services/APIs, and from any other
application that connects to OData feeds.

> [!NOTE]
> With the decision to make Common Data Service the preferred data interface for
Human Resources being relatively recent, you may find that the Human Resources data entities you need for your integration are not yet available in Common Data Service<sup>1</sup>. If the Human Resources entities required for your integration are not yet available, you will need to wait for the data entities to be made available or you will need to use one of the other integration technologies described below.
> 
> By default, Common Data Service integration is turned off in new environments that don't include the provided demo data. It's turned on in new environments that include demo data, and the environments start to sync data when they are provisioned. After your environment is ready to sync data, you can turn on integration.

<sup>1</sup>For a list of Human Resources entities available in Common Data Service, see [Human Resources and Common Data Service](https://docs.microsoft.com/dynamics365/unified-operations/talent/corehrentities). For Attract and Onboard, all entities are available in Common Data Service.

### DMF/DIXF entities

Human Resources, built primarily on the same platform as Finance and Operations applications, provides a [Data Management Framework(DMF)](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/data-entities/data-entities-data-packages?toc=/fin-and-ops/toc.json), sometimes also known as the Data Import Export Framework or DIXF, and a set of data entities that can be used for importing/exporting data into/from Human Resources. While Common Data Service entities are the preferred data integration interface for Human Resources, the DMF entities will still be useful in some circumstances, such as:

- Common Data Service entities aren't yet available.

- The integration requires high performance bulk data import/export capabilities.

The DMF entities currently provide the most complete data coverage for Human Resources data.

DMF is not appropriate for real-time integrations (such as when immediate user
feedback in a user interface is required), because package operations are
scheduled batch jobs, and will often have a minimum of a 1-2 minute latency
before the batch service picks up the job for execution, plus whatever time is
required to complete the import/export operation.

DMF may be the best option when high throughput is required (such as a nightly
scheduled import/export of many thousands of records).

> [!NOTE]
> DMF is not available for Attract and Onboard.

### DMF package REST API

The DMF provides a [REST
API](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/data-entities/data-management-api)
for manipulating data packages. This API can be used to programmatically
interact with the DMF, allowing actions such as:

- Importing a data package.

- Exporting a data package.

- Checking the status of an import/export operation.

The DMF Package REST API is fully supported in Human Resources: Core
HR.

### Azure SQL DB (BYOD)

DMF additionally provides a powerful feature (generally known as [Bring Your Own
Database](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/analytics/export-entities-to-your-own-database),
or BYOD) that allows Human Resources to export data to your own Microsoft Azure SQL
database. This provides tremendous flexibility, because when the data is present
in your own SQL database, you can make use of any applications or middleware
that can connect to a SQL datastore.

BYOD should generally be considered a read-only solution. While you are able to
manipulate and store whatever data you want in the Azure SQL database (such as for
data mashups), data stored in the Azure SQL database will not be synchronized
back to Human Resources.

BYOD is appropriate for reporting solutions, data integrations, data mashups, as
a data source for an [Azure Data
Factory](https://docs.microsoft.com/azure/data-factory/) pipeline.

> [!NOTE]
> BYOD is not available for Attract and Onboard.

### OData-enabled entities

Most DMF entities are also enabled for access through the Human Resources data service (OData). The documentation provided for the [Finance and Operations OData
service](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/data-entities/odata) generally also applies to Human Resources, although documentation about creating your own OData-exposed entities will not apply.

While Common Data Service and the OData implementation provided by Common Data Service (through the [Dynamics 365 Web
API](https://docs.microsoft.com/previous-versions/dynamicscrm-2016/developers-guide/mt593051(v=crm.8))) is preferred over the Human Resources data service, the Human Resources data service currently has more complete entity coverage for the Human Resources data.

### Excel Add-in

The [Excel Add-in](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/office-integration/use-excel-add-in?toc=/dynamics365/unified-operations/talent/toc.json) makes use of OData-enabled entities beneath the surface. It provides a convenient way for an end user to retrieve and modify Human Resources data through the familiar Excel UI.

The Excel Add-in is appropriate for ad-hoc data imports/exports by business
domain experts. For a recurring data integration that requires programmatic
automation, another integration technology will be more appropriate.

### Data Integrator

The Common Data Service administrator experience provides a [Data Integrator
service](https://docs.microsoft.com/powerapps/administrator/data-integrator)
that can be used for data integrations to/from Common Data Service. Data Integrator can be used to define integration projects (often based on pre-defined templates that application developers have tailored for specific integrations). The integration projects can be scheduled to run automatically on a recurring schedule or be run manually.

Data Integrator projects are appropriate for Common Data Service batch integrations and make a great choice for integrations between the Dynamics 365 family of applications. As an example, Microsoft provides an out-of-the-box Data
Integrator template that can be used for integrating data from Human Resources into Dynamics 365 Finance. For more information, see [Integration from Dynamics 365 Human Resources to Dynamics 365 Finance](hr-admin-integration-finance.md).

### Power Query

Data Integrator also supports [Power Query](https://docs.microsoft.com/power-query/power-query-what-is-power-query) (through its [Advanced Query
feature](https://docs.microsoft.com/powerapps/administrator/data-integrator#advanced-data-transformation-and-filtering)).
Power Query provides powerful, flexible data filtering and transformation,
including the rich M formula language, and will likely be familiar to those who
have experience developing Power BI reports.

## Deciding on an integration technology

With so many different integration technologies available, deciding on which
integration approach to use can sometimes be overwhelming. Over time,
and particularly as the data coverage in Common Data Service matures, the decision will become easier, with Common Data Service being the preferred data interface in most cases. But until then, you may find that Common Data Service does not yet meet your needs. The following table helps summarize some of the key characteristics of the various integration technology options.

| Technology/Tool/API    | Recurring integrations                   | Synchronous/Asynchronous                    | Programmatic access through an API        | Appropriate data volumes                                   | Data coverage                       |
|------------------------|------------------------------------------|---------------------------------------------|-------------------------------------------|------------------------------------------------------------|-------------------------------------|
| Common Data Service entities           | Yes, using Data Integrator or middleware | Sync Async, Batch (through Data Integrator) | Yes, through Dynamics 365 Web API (OData) | Varies with use case (supports paging for interactive use) | Improving<sup>2</sup>                       |
| DMF entities           | Yes, scheduled through middleware        | Async, Batch                                | Yes, through DMF Package REST API         | High (hundreds of thousands of records)                    | High                                |
| DMF Package REST API   | Yes, scheduled through middleware        | Async, Batch                                | Yes                                       | High (hundreds of thousands of records)                    | API supports all DMF entities       |
| BYOD                   | Yes, scheduled by Admin in Human Resources        | Async, Batch                                | No<sup>3</sup>                                    | High (hundreds of thousands of records)                    | Supports all DMF entities           |
| OData-enabled entities | Yes, using middleware                    | Sync                                        | Yes, through Human Resources Data Service (OData)  | Varies with use case (supports paging for interactive use) | High                                |
| Excel Add-in           | No                                       | Sync                                        | No                                        | Medium (tens of thousands of records)                      | Supports all OData-enabled entities |
| Data Integrator        | Yes, scheduled in Data Integrator        | Async, Batch                                | No                                        | Varies with use case                                       | Supports all Common Data Service entities           |

<sup>2</sup>Microsoft is investing heavily in increasing data coverage for Common Data Service entities, and recommends Common Data Service as the preferred data interface when coverage is available. Currently, Common Data Service data coverage is low relative to DMF and OData-enabled entities.

<sup>3</sup>SQL database can be accessed programmatically.

## Summary

Your business data is a valuable asset, but its value can be greatly diminished
if it is hard to use the data for your specific purposes (such as reporting, data
mashups, or custom applications). Dynamics 365 Human Resources provides several
technologies for working with your data outside of the Human Resources application's user interface (UI), allowing integrating applications access to the data. This topic has described the available integration technologies and some of their key characteristics. This information should help you make better decisions on which approaches to leverage for your integration projects.

