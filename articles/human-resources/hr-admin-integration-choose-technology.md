---
# required metadata

title: Choose a data integration technology
description: This topic provides information about integrating with data managed by Human Resources. 
author: twheeloc
ms.date: 08/19/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
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


[!INCLUDE [PEAP](../includes/peap-2.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]



This topic provides information for integrating with data managed by Dynamics 365 Human Resources. It describes different integration technologies to help you decide which technologies best fit your needs.

## Data integration background

Business data is a key asset that makes your company unique. Your business's data is highly valuable. You can use the relationships between data gathered throughout your business to improve business processes and business intelligence across your organization. We strive to provide easy, secure, and stable access to your business data whatever system it comes from.

Historically, integrating data between multiple systems has been difficult. Microsoft is taking steps to make data integration easier, and a large step
toward that goal is realized through [Dataverse](/powerapps/maker/common-data-service/data-platform-intro).

Human Resources is making Dataverse the preferred public interface for Human Resources data. Over time, we expect that all the most important data managed by Human Resources will be exposed in Dataverse. We recommend Dataverse as the technology of choice for most integrating applications.

We realize Dataverse might not yet contain all the data your application requires. We also realize your project timeline might require an alternative technology. Be sure to let us know when Dataverse doesn't meet your integration needs.

## Integration technologies

The following sections describe the different data integration technologies available for use with Human Resources.

### Dataverse tables

Dataverse is the preferred public data interface for Human Resources. It grew out of the Dynamics 365 XRM platform, which is used by [Dynamics 365 Customer Engagement](/dynamics365/?panel=customer-engagement#pivot=business-apps) solutions.

Dataverse provides a platform and API for data tables. When you deploy Human Resources, it connects to a Dataverse instance. The entities for Human Resources data deploy into that Dataverse instance. The tables and their data are available to any application that can connect to the Dataverse instance. Human Resources synchronizes data to and from the Dataverse tables.

> [!NOTE]
> Human Resources entities correspond to Dataverse tables. For more information about Dataverse (formerly Common Data Service) and terminology updates, see [What is Microsoft Dataverse?](/powerapps/maker/data-platform/data-platform-intro)

When the data tables required by your integrating apps are in Dataverse, you can fully use [Dataverse and the APIs it supports](/powerapps/?panel=developer#pivot=home). Among the supported APIs is the [Dynamics 365 Web API](/dynamics365/customer-engagement/developer/use-microsoft-dynamics-365-web-api), which provides an OData implementation for accessing Dataverse data.

Dataverse tables and their associated APIs are the best option for accessing Human Resources data from web applications, web services/APIs, and from any other application that connects to OData feeds.

> [!NOTE]
> With the decision to make Dataverse the preferred data interface for Human Resources being relatively recent, you may find that the Human Resources data entities you need for your integration are not yet available in Dataverse.
> </br>
> For a list of Human Resources entities available in Dataverse, see [Human Resources and Dataverse](/dynamics365/unified-operations/talent/corehrentities).
> </br>
> If the Human Resources entities required for your integration aren't yet available, you'll either need to wait for the data entities to be made available or use one of the other integration technologies described below.
> </br>
> By default, Dataverse  integration is turned off in new environments that don't include the provided demo data. It's turned on in new environments that include demo data, and the environments start to sync data when they are provisioned. After your environment is ready to sync data, you can turn on integration.

### DMF/DIXF entities

Human Resources, built primarily on the same platform as Finance and Operations applications, provides a [Data Management Framework (DMF)](/dynamics365/unified-operations/dev-itpro/data-entities/data-entities-data-packages?toc=%2ffin-and-ops%2ftoc.json). DMF is also known as the Data Import Export Framework (DIXF). Human Resources provides a set of data entities you can use for importing and exporting Human Resources data. While Dataverse tables are the preferred data integration interface for Human Resources, DMF entities are still useful in some circumstances, such as:

- Dataverse tables aren't yet available.

- The integration requires high-performance bulk data import/export capabilities.

> [!NOTE]
> Human Resources entities correspond to Dataverse tables. For more information about Dataverse (formerly Common Data Service) and terminology updates, see [What is Microsoft Dataverse?](/powerapps/maker/data-platform/data-platform-intro)

DMF entities currently provide the most complete data coverage for Human Resources data.

DMF isn't appropriate for real-time integrations, such as when you need immediate user feedback in a user interface. Package operations are scheduled batch jobs, and often have a minimum of a 1-2 minute latency before the batch service picks up the job for execution, plus whatever time is required to complete the import/export operation.

DMF may be the best option when high throughput is required (such as a nightly scheduled import/export of many thousands of records).

> [!NOTE]
> DMF is not available for Attract and Onboard.

### DMF package REST API

The DMF provides a [REST API](/dynamics365/unified-operations/dev-itpro/data-entities/data-management-api)
for manipulating data packages. This API can be used to programmatically interact with the DMF, allowing actions such as:

- Importing a data package.

- Exporting a data package.

- Checking the status of an import/export operation.

The DMF Package REST API is fully supported in Human Resources.

### Azure SQL DB (BYOD)

DMF additionally provides a powerful feature (known as [Bring Your Own Database](/dynamics365/unified-operations/dev-itpro/analytics/export-entities-to-your-own-database), or BYOD) that allows Human Resources to export data to your own Microsoft Azure SQL database. This capability provides tremendous flexibility. When the data is present in your own SQL database, you can make use of any applications or middleware that can connect to a SQL datastore.

BYOD is mainly a read-only solution. While you can manipulate and store whatever data you want in the Azure SQL database (such as for data mashups), data stored in the Azure SQL database isn't synchronized to Human Resources.

BYOD is appropriate for reporting solutions, data integrations, data mashups, as a data source for an [Azure Data Factory](/azure/data-factory/) pipeline.

> [!NOTE]
> BYOD is not available for Attract and Onboard.

### OData-enabled entities

Most DMF entities are also enabled for access through the Human Resources data service (OData). The documentation provided for the [Finance and Operations OData service](/dynamics365/unified-operations/dev-itpro/data-entities/odata) applies to Human Resources, except for creating your own OData-exposed entities.

While Dataverse and the OData implementation provided by Dataverse (through the [Dynamics 365 Web API](/previous-versions/dynamicscrm-2016/developers-guide/mt593051(v=crm.8))) is preferred over the Human Resources data service, the Human Resources data service currently has more complete entity coverage for the Human Resources data.

### Excel Add-in

The [Excel Add-in](/dynamics365/unified-operations/dev-itpro/office-integration/use-excel-add-in?toc=%2fdynamics365%2funified-operations%2ftalent%2ftoc.json) makes use of OData-enabled entities beneath the surface. It provides a convenient way for an end user to retrieve and modify Human Resources data through the familiar Excel UI.

The Excel Add-in is appropriate for ad-hoc data imports/exports by business domain experts. For a recurring data integration that requires programmatic automation, another integration technology will be more appropriate.

### Data Integrator

You can use the [Data Integrator service](/powerapps/administrator/data-integrator) to integrate data to and from Dataverse. Data Integrator lets you define integration projects, often based on pre-defined templates that application developers have tailored for specific integrations. You can schedule integration projects to run automatically on a recurring schedule or run them manually.

Data Integrator projects are appropriate for Dataverse batch integrations. They're a great choice for integrations between the Dynamics 365 family of applications. For example, Microsoft provides a Data Integrator template for integrating data from Human Resources into Dynamics 365 Finance. You can learn more about the template in  [Integration from Dynamics 365 Human Resources to Dynamics 365 Finance](hr-admin-integration-finance.md).

### Power Query

Data Integrator supports [Power Query](/power-query/power-query-what-is-power-query) through its [Advanced Query feature](/powerapps/administrator/data-integrator#advanced-data-transformation-and-filtering). Power Query provides powerful, flexible data filtering and transformation, including the rich M formula language. Power Query will likely be familiar if you've developed Power BI reports.

## Deciding on an integration technology

With so many different integration technologies available, deciding on which integration approach to use can sometimes be overwhelming. As the data coverage in Dataverse matures, the decision will become easier, with Dataverse being the preferred data interface in most cases. But until then, you may find that Dataverse doesn't yet meet your needs. The following table summarizes some of the key characteristics of the integration technology options.

| Technology/Tool/API    | Recurring integrations                   | Synchronous/Asynchronous                    | Programmatic access through an API        | Appropriate data volumes                                   | Data coverage                       |
|------------------------|------------------------------------------|---------------------------------------------|-------------------------------------------|------------------------------------------------------------|-------------------------------------|
| Dataverse tables           | Yes, using Data Integrator or middleware | Sync Async, Batch (through Data Integrator) | Yes, through Dynamics 365 Web API (OData) | Varies with use case (supports paging for interactive use) | Improving<sup>2</sup>                       |
| DMF entities           | Yes, scheduled through middleware        | Async, Batch                                | Yes, through DMF Package REST API         | High (hundreds of thousands of records)                    | High                                |
| DMF Package REST API   | Yes, scheduled through middleware        | Async, Batch                                | Yes                                       | High (hundreds of thousands of records)                    | API supports all DMF entities       |
| BYOD                   | Yes, scheduled by Admin in Human Resources        | Async, Batch                                | No<sup>3</sup>                                    | High (hundreds of thousands of records)                    | Supports all DMF entities           |
| OData-enabled entities | Yes, using middleware                    | Sync                                        | Yes, through Human Resources Data Service (OData)  | Varies with use case (supports paging for interactive use) | High                                |
| Excel Add-in           | No                                       | Sync                                        | No                                        | Medium (tens of thousands of records)                      | Supports all OData-enabled entities |
| Data Integrator        | Yes, scheduled in Data Integrator        | Async, Batch                                | No                                        | Varies with use case                                       | Supports all Dataverse tables           |

<sup>2</sup>Microsoft is investing heavily in increasing data coverage for Dataverse tables. We recommend using Dataverse when coverage is available. Currently, Dataverse data coverage is low, compared to DMF and OData-enabled entities.

<sup>3</sup>SQL database can be accessed programmatically.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
