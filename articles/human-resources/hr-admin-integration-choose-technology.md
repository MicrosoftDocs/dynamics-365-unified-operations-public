---
# required metadata

title: Choose a data integration technology
description: This article provides information about integrating with data managed by Human Resources. It describes different integration technologies to help you decide which technologies best fit your needs.
author: andreabichsel
manager: AnnBe
ms.date: 02/28/2020
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

This article provides information for integrating with data managed by Dynamics 365 Human Resources. It describes different integration technologies to help you decide which technologies best fit your needs.

## Data integration background

Business data is a key asset that makes your company unique. Your business's data is highly valuable. You can use the relationships between data gathered throughout your business to improve business processes and business intelligence across your organization. We strive to provide easy, secure, and stable access to your business data whatever system it comes from.

Historically, integrating data between multiple systems has been difficult.
Microsoft is taking steps to make data integration easier, and a large step
toward that goal is realized through [Common Data Service](https://docs.microsoft.com/powerapps/maker/common-data-service/data-platform-intro).

Human Resources is making Common Data Service the preferred
public interface for Human Resources data. Over time, we expect that all the most important data managed by Human Resources will be exposed in Common Data Service. We recommend Common Data Service as the technology of choice for most integrating applications.

We realize Common Data Service might not yet contain all the data your application requires. We also realize your project timeline might require an alternative technology. Be sure to let us know when Common Data Service doesn't meet your integration needs.

## Integration technologies

The following sections describe the different data integration technologies
available for use with Human Resources.

### Common Data Service entities

Common Data Service is the preferred public data interface for Human Resources. It grew out of the Dynamics 365 XRM platform, which is used by [Dynamics 365 Customer Engagement](https://docs.microsoft.com/dynamics365/#pivot=business-apps&panel=customer-engagement) solutions.

Common Data Service provides a platform and API for data entities. When you deploy Human Resources, it connects to a Common Data Service instance. The entities for Human Resources data deploy into that Common Data Service instance. The entities and their data are available to any application that can connect to the Common Data Service instance. Human Resources synchronizes data to and from the Common Data Service entities.

When the data entities required by your integrating apps are in Common Data Service, you can fully use [Common Data Service and the APIs it supports](https://docs.microsoft.com/powerapps/#pivot=home&panel=developer). Among the supported APIs is the [Dynamics 365 Web API](https://docs.microsoft.com/dynamics365/customer-engagement/developer/use-microsoft-dynamics-365-web-api), which provides an OData implementation for accessing Common Data Service data.

Common Data Service entities and their associated APIs are the best option for accessing Human Resources data from web applications, web services/APIs, and from any other application that connects to OData feeds.

> [!NOTE]
> With the decision to make Common Data Service the preferred data interface for
Human Resources being relatively recent, you may find that the Human Resources data entities you need for your integration are not yet available in Common Data Service.
> </br>
> For a list of Human Resources entities available in Common Data Service, see [Human Resources and Common Data Service](https://docs.microsoft.com/dynamics365/unified-operations/talent/corehrentities).
> </br>
> If the Human Resources entities required for your integration aren't yet available, you'll either need to wait for the data entities to be made available or use one of the other integration technologies described below.
> </br>
> By default, Common Data Service  integration is turned off in new environments that don't include the provided demo data. It's turned on in new environments that include demo data, and the environments start to sync data when they are provisioned. After your environment is ready to sync data, you can turn on integration.

### DMF/DIXF entities

Human Resources, built primarily on the same platform as Finance and Operations applications, provides a [Data Management Framework (DMF)](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/data-entities/data-entities-data-packages?toc=/fin-and-ops/toc.json). DMF is also known as the Data Import Export Framework (DIXF). Human Resources provides a set of data entities you can use for importing and exporting Human Resources data. While Common Data Service entities are the preferred data integration interface for Human Resources, DMF entities are still useful in some circumstances, such as:

- Common Data Service entities aren't yet available.

- The integration requires high-performance bulk data import/export capabilities.

The DMF entities currently provide the most complete data coverage for Human Resources data.

DMF isn't appropriate for real-time integrations, such as when you need immediate user feedback in a user interface. Package operations are scheduled batch jobs, and often have a minimum of a 1-2 minute latency before the batch service picks up the job for execution, plus whatever time is required to complete the import/export operation.

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

DMF additionally provides a powerful feature (known as [Bring Your Own
Database](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/analytics/export-entities-to-your-own-database),
or BYOD) that allows Human Resources to export data to your own Microsoft Azure SQL
database. This capability provides tremendous flexibility. When the data is present in your own SQL database, you can make use of any applications or middleware
that can connect to a SQL datastore.

BYOD is mainly a read-only solution. While you can manipulate and store whatever data you want in the Azure SQL database (such as for data mashups), data stored in the Azure SQL database isn't synchronized to Human Resources.

BYOD is appropriate for reporting solutions, data integrations, data mashups, as
a data source for an [Azure Data
Factory](https://docs.microsoft.com/azure/data-factory/) pipeline.

> [!NOTE]
> BYOD is not available for Attract and Onboard.

### OData-enabled entities

Most DMF entities are also enabled for access through the Human Resources data service (OData). The documentation provided for the [Finance and Operations OData
service](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/data-entities/odata) applies to Human Resources, except for creating your own OData-exposed entities.

While Common Data Service and the OData implementation provided by Common Data Service (through the [Dynamics 365 Web
API](https://docs.microsoft.com/previous-versions/dynamicscrm-2016/developers-guide/mt593051(v=crm.8))) is preferred over the Human Resources data service, the Human Resources data service currently has more complete entity coverage for the Human Resources data.

### Excel Add-in

The [Excel Add-in](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/office-integration/use-excel-add-in?toc=/dynamics365/unified-operations/talent/toc.json) makes use of OData-enabled entities beneath the surface. It provides a convenient way for an end user to retrieve and modify Human Resources data through the familiar Excel UI.

The Excel Add-in is appropriate for ad-hoc data imports/exports by business
domain experts. For a recurring data integration that requires programmatic
automation, another integration technology will be more appropriate.

### Data Integrator

You can use the [Data Integrator
service](https://docs.microsoft.com/powerapps/administrator/data-integrator) to integrate data to and from Common Data Service. Data Integrator lets you define integration projects, often based on pre-defined templates that application developers have tailored for specific integrations. You can schedule integration projects to run automatically on a recurring schedule or run them manually.

Data Integrator projects are appropriate for Common Data Service batch integrations. They're a great choice for integrations between the Dynamics 365 family of applications. For example, Microsoft provides a Data Integrator template for integrating data from Human Resources into Dynamics 365 Finance. You can learn more about the template in  [Integration from Dynamics 365 Human Resources to Dynamics 365 Finance](hr-admin-integration-finance.md).

### Power Query

Data Integrator supports [Power Query](https://docs.microsoft.com/power-query/power-query-what-is-power-query) through its [Advanced Query feature](https://docs.microsoft.com/powerapps/administrator/data-integrator#advanced-data-transformation-and-filtering). Power Query provides powerful, flexible data filtering and transformation, including the rich M formula language. Power Query will likely be familiar if you've developed Power BI reports.

## Deciding on an integration technology

With so many different integration technologies available, deciding on which
integration approach to use can sometimes be overwhelming. As the data coverage in Common Data Service matures, the decision will become easier, with Common Data Service being the preferred data interface in most cases. But until then, you may find that Common Data Service doesn't yet meet your needs. The following table summarizes some of the key characteristics of the integration technology options.

| Technology/Tool/API    | Recurring integrations                   | Synchronous/Asynchronous                    | Programmatic access through an API        | Appropriate data volumes                                   | Data coverage                       |
|------------------------|------------------------------------------|---------------------------------------------|-------------------------------------------|------------------------------------------------------------|-------------------------------------|
| Common Data Service entities           | Yes, using Data Integrator or middleware | Sync Async, Batch (through Data Integrator) | Yes, through Dynamics 365 Web API (OData) | Varies with use case (supports paging for interactive use) | Improving<sup>2</sup>                       |
| DMF entities           | Yes, scheduled through middleware        | Async, Batch                                | Yes, through DMF Package REST API         | High (hundreds of thousands of records)                    | High                                |
| DMF Package REST API   | Yes, scheduled through middleware        | Async, Batch                                | Yes                                       | High (hundreds of thousands of records)                    | API supports all DMF entities       |
| BYOD                   | Yes, scheduled by Admin in Human Resources        | Async, Batch                                | No<sup>3</sup>                                    | High (hundreds of thousands of records)                    | Supports all DMF entities           |
| OData-enabled entities | Yes, using middleware                    | Sync                                        | Yes, through Human Resources Data Service (OData)  | Varies with use case (supports paging for interactive use) | High                                |
| Excel Add-in           | No                                       | Sync                                        | No                                        | Medium (tens of thousands of records)                      | Supports all OData-enabled entities |
| Data Integrator        | Yes, scheduled in Data Integrator        | Async, Batch                                | No                                        | Varies with use case                                       | Supports all Common Data Service entities           |

<sup>2</sup>Microsoft is investing heavily in increasing data coverage for Common Data Service entities. We recommend using Common Data Service when coverage is available. Currently, Common Data Service data coverage is low, compared to DMF and OData-enabled entities.

<sup>3</sup>SQL database can be accessed programmatically.
