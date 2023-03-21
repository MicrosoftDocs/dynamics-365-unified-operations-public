---
# required metadata

title: Comparison of cloud and on-premises features
description: The article shows which features are supported in Cloud and on-premises.
author: sericks007
ms.date: 01/14/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 89563
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sericks
ms.search.validFrom: 2017-11-29
ms.dyn365.ops.version: Platform update 9
---

# Comparison of cloud and on-premises features

[!include [banner](../includes/banner.md)]

This article shows a comparison of features available in cloud vs. on-premises for the following applications:

- [Dynamics 365 Finance](cloud-prem-comparison.md#dynamics-365-finance)
- [Dynamics 365 Supply Chain Management](cloud-prem-comparison.md#dynamics-365-supply-chain-management)
- [Dynamics 365 Commerce](cloud-prem-comparison.md#dynamics-365-commerce)
- [Dynamics 365 Human Resources](cloud-prem-comparison.md#dynamics-365-human-resources)

Information about the [development and administration features](cloud-prem-comparison.md#development-and-administration-features) is included, as well.

The following tables list the application areas. Cloud and on-premises support is listed for the feature as a whole. Where specific features differ from the area overall, the features are listed on a separate line in the Feature column.

## Dynamics 365 Finance

| **Area**             | **Feature**                | **Cloud** | **On-premises** |
|---------------------|-----------------------------|-----------|-----------------|
| Compliance and certifications        |                                                                                           | Yes       | Yes             |
|                                      | SOC 1 Type 1 certification                                                                | Yes       | No              |
| Data management and integration      |                                                                                           | Yes       | Yes             |
|                                      | Export data to your own data warehouse                                                    | Yes       | Yes             |
|                                      | Enable the export of incremental updates to a data entity                                 | Yes       | Yes             |
|                                      | Data integrations                                                                         | Yes       | Yes             |
| Document management                  |                                                                                           | Yes       | Yes             |
| Financial management                 |                                                                                           | Yes       | Yes             |
| Help                                 |                                                                                           | Yes       | No              |
| Human resources                      |                                                                                           | Yes       | Yes             |
| Intelligence                         |                                                                                           | Yes       | Yes             |
|                                      | Electronic reporting (ER)                                                                 | Yes       | Yes             |
|                                      | ER: Integration with LCS                                                                  | Yes       | No              |
|                                      | ER: Integration with SharePoint                                                           | Yes       | No              |
|                                      | ER: Integration with Regulatory Configuration Services (RCS)                              | Yes       | No              |
|                                      | ER: Uses local file system as storage of ER configurations accessible via ER repositories | No        | Yes             |
|                                      | Integration with PowerBI.com                                                              | Yes       | No              |
|                                      | Integration with PowerBI Desktop                                                          | No        | Yes             |
|                                      | Analytical workspaces                                                                     | Yes       | No              |
|                                      | Intelligent business process: Recommendations                                             | Yes       | No              |
|                                      | Authoring Power BI reports with OData using Power BI desktop or Excel PowerQuery tools    | Yes       | No              |
|                                      | SQL Server Reporting Services (SSRS) supports scaling out                                 | Yes       | Yes             |
|                                      | Telemetry is transferred into the cloud                                                   | Yes       | No              |
| Lifecycle services                   |                                                                                           | Yes       | Yes             |
|                                      | Configurable business processes                                                           | Yes       | No              |
| Localizations                        |                                                                                           | Yes       | Yes             |
| Mobile app, workspaces, and platform |                                                                                           | Yes       | Yes             |
| Office integration                   |                                                                                           | Yes       | Yes             |
| Organization administration          |                                                                                           | Yes       | Yes             |
| Payroll                              |                                                                                           | Yes       | Yes             |
|                                      | Direct deposit                                                                            | Yes       | No              |
| Project management and accounting    |                                                                                           | Yes       | Yes             |
| Security                             |                                                                                           | Yes       | Yes             |
| Service management                   |                                                                                           | Yes       | Yes             |
| Web client                           |                                                                                           | Yes       | Yes             |
|                                      | Task recorder - Save or load task recordings from the BPM library                         | Yes       | No              |
| Support                              |                                                                                           | Yes       | Yes             |
|                                      | Access to Support via the Help & Support menu                                             | Yes       | No              |
|                                      | Business events                                                                           | Yes       | Yes (either internet connectivity is required or custom endpoints must be implemented to send/receive business events within intranet)              |

## Dynamics 365 Supply Chain Management 

| **Area**                | **Feature**             | **Cloud** | **On-premises** |
|-------------------------|-------------------|-----------|-----------------|
| Asset management                     |                                                                                           | Yes       | Yes             |
| Compliance and certifications        |                                                                                           | Yes       | Yes             |
|                                      | SOC 1 Type 1 certification                                                                | Yes       | No              |
| Cost accounting                      |                                                                                           | Yes       | Yes             |
|                                      | Cost accounting content pack for Power BI                                                 | Yes       | No              |
|                                      | Cost accounting workspace for mobile app                                                  | Yes       | No              |
| Cost management                      |                                                                                           | Yes       | Yes             |
|                                      | Cost management content pack for Power BI                                                 | Yes       | No              |
| Data management and integration      |                                                                                           | Yes       | Yes             |
|                                      | Configuration-driven extension                                                            | Yes       | No              |
|                                      | Export data to your own data warehouse                                                    | Yes       | Yes             |
|                                      | Enable the export of incremental updates to a data entity                                 | Yes       | Yes             |
|                                      | Data integrations                                                                         | Yes       | Yes             |
| Document management                  |                                                                                           | Yes       | Yes             |
| Help                                 |                                                                                           | Yes       | No              |
| Intelligence                         |                                                                                           | Yes       | Yes             |
|                                      | Electronic reporting (ER)                                                                 | Yes       | Yes             |
|                                      | ER: Integration with LCS                                                                  | Yes       | No              |
|                                      | ER: Integration with SharePoint                                                           | Yes       | No              |
|                                      | ER: Integration with Regulatory Configuration Services (RCS)                              | Yes       | No              |
|                                      | ER: Uses local file system as storage of ER configurations accessible via ER repositories | No        | Yes             |
|                                      | Integration with PowerBI.com                                                              | Yes       | No              |
|                                      | Integration with PowerBI Desktop                                                          | No        | Yes             |
|                                      | Analytical workspaces                                                                     | Yes       | No              |
|                                      | Intelligent business process: Recommendations                                             | Yes       | No              |
|                                      | Authoring Power BI reports with OData using Power BI desktop or Excel PowerQuery tools    | Yes       | No              |
|                                      | SQL Server Reporting Services (SSRS) supports scaling out                                 | Yes       | Yes             |
|                                      | Telemetry is transferred into the cloud                                                   | Yes       | No              |
| Inventory management                 |                                                                                           | Yes       | Yes             |
| Lifecycle services                   |                                                                                           | Yes       | Yes             |
|                                      | Configurable business processes                                                           | Yes       | No              |
| Localizations                        |                                                                                           | Yes       | Yes             |
| Manufacturing                        |                                                                                           | Yes       | Yes             |
| Master planning and forecasting      |                                                                                           | Yes       | Yes             |
|                                      | Planning optimization                                                                     | Yes       | No              |
|                                      | Demand forecasting                                                                        | Yes       | No              |
| Mobile app, workspaces, and platform |                                                                                           | Yes       | Yes             |
| Office integration                   |                                                                                           | Yes       | Yes             |
| Organization administration          |                                                                                           | Yes       | Yes             |
| Procurement and sourcing             |                                                                                           | Yes       | Yes             |
|                                      | Punch-out to external catalog from purchase requisition                                   | Yes       | No              |
|                                      | Purchase spend analysis Power BI reports                                                  | Yes       | No              |
| Product information management       |                                                                                           | Yes       | Yes             |
| Product master data                  |                                                                                           | Yes       | Yes             |
| Production                           |                                                                                           | Yes       | Yes             |
|                                      | Production performance Power BI reports                                                   | Yes       | No              |
| Project management and accounting    |                                                                                           | Yes       | Yes             |
| Sales                                |                                                                                           | Yes       | Yes             |
|                                      | Sales and profitability performance Power BI reports                                      | Yes       | No              |
| Security                             |                                                                                           | Yes       | Yes             |
| Service management                   |                                                                                           | Yes       | Yes             |
| Supply chain management              |                                                                                           | Yes       | Yes             |
| Transportation management            |                                                                                           | Yes       | Yes             |
| Vendor collaboration                 |                                                                                           | Yes       | No              |
| Warehouse management                 |                                                                                           | Yes       | Yes             |
|                                      | Mobile warehouse app                                                                      | Yes       | Yes             |
|                                      | Warehousing Power BI reports                                                              | Yes       | No              |
| Web client                           |                                                                                           | Yes       | Yes             |
|                                      | Task recorder - Save or load task recordings from the BPM library                         | Yes       | No              |
| Support                              |                                                                                           | Yes       | Yes             |
|                                      | Access to Support via the Help & Support menu                                             | Yes       | No              |

## Dynamics 365 Commerce 

To see a list of capabilities that are available in on-premises deployments, see [Commerce capabilities that are available in on-premises deployments](../../../commerce/retail-onprem.md).

## Dynamics 365 Human Resources

This table applies to the Human Resources stand-alone version.

| **Area**         | **Feature**         | **Cloud** | **On-premises** |
|------------------|---------------------|-----------|-----------------|
| All Human Resources areas | All Human Resources features | Yes       | No              |

>[!NOTE]
>For the comparison of cloud vs. on-premise of a migrated Human resources environment on the merged infrastructure, see [Dynamics 365 Finance](cloud-prem-comparison.md#dynamics-365-finance). 

## Development and administration features

| **Area**                   | **Feature**                               | **Cloud** | **On-premises** |
|----------------------------|-------------------------------------------|-----------|-----------------|
| Build and test             |                                           | Yes       | Yes             |
| Extensibility              |                                           | Yes       | Yes             |
| Monitoring and telemetry   |                                           | Yes       | Yes             |
| Platform compatibility     |                                           | Yes       | Yes             |
| Servicing                  |                                           | Yes       | Yes             |
|                            | Servicing environments                    | Yes       | No              |
| Trace Parser               |                                           | Yes       | Yes             |
| PerfTimer                  |                                           | Yes       | Yes\*           |
| Upgrade                    |                                           | Yes       | Yes             |
|                            | Upgrade                                   | Yes       | No              |
|                            | Upgrade and support for previous versions | Yes       | No              |
| Visual Studio development  |                                           | Yes       | Yes             |

\* In on-premises environments, PerfTimer only shows results for the client.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
