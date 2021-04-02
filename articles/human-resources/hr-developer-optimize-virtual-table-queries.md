---
# required metadata

title: Optimize Dataverse virtual table queries
description: Tips to optimize and troubleshoot performance of Dataverse virtual table queries
author: andreabichsel
ms.date: 04/02/2021
ms.topic: article
ms.prod: 
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
ms.author: jaredha
ms.search.validFrom: 2021-04-02
ms.dyn365.ops.version: Human Resources

---

# Optimize Dataverse virtual table queries

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

## Issue

When using Dataverse virtual tables to develop integrations to develop integrations and other data connections with Dynamics 365 Human Resources, you can experience performance issues with the queries against the virtual tables. The slow query execution can occur across various clients or interfaces. For example, you may experience the issue when querying a virtual table through the Dataverse Web API, when creating a Power App against a virtual table, or when building a Power BI report on a virtual table. All these interfaces have the potential to surface the performance issue. 

One of the causes of slow performance with Dataverse virtual tables for Human Resources is the foreign key columns of the virtual table related to the table's [navigation properties](https://docs.microsoft.com/powerapps/developer/data-platform/webapi/web-api-types-operations#navigation-properties). When navigation properties are created for a virtual table, a foreign key column is automatically added to the table to represent the value of the key for the related virtual table's key column. Because of how the values for these foreign key columns are maintained in an entity, fetching the values can have a negative impact on the performance of a query against the virtual table.

An example where you may see the impact of this is in queries against the Worker (`mshr_hcmworkerentity`) or Base worker (`mshr_hcmworkerbaseentity`) entity. You may see the performance issue manifest itself in a few different ways:

- The query against the virtual table may return the expected results, but take longer than expected to complete execution of the query.
- The query may time out and return the following error: "A token was obtained to call Finance and Operations, but Finance and Operations returned an error of type InternalServerError."
- The query may return an error type 400 with the following message: "An unexpected error occurred."
- The query may overuse server resources, and become subject to [throttling](https://docs.microsoft.com/dynamics365/human-resources/hr-admin-integration-throttling-faq). In this case the query returns the following error: "A token was obtained to call Finance and Operations, but Finance and Operations returned an error of type 429."

  ![Error type 429 on HcmWorkerBaseEntity](./media/HcmWorkerBaseEntityErrorType429.png)

## Resolution

### Limit the columns selected in the query

With virtual tables, one of the methods with the greatest potential to improve query performance is to limit the number of columns selected in the query.

### Implement paging

### Filter records



## See also

- [What's new or changed in Human Resources](hr-admin-whats-new.md)
- [Administrator Guide](hr-admin-overview.md)
- [User Guide](hr-hrpro-overview.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
