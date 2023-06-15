---
# required metadata

title: Plan your organizational hierarchy
description: Before you set up organizations and organization hierarchies, make sure that you understand how to best model your business. 
author: sericks007
ms.date: 02/19/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: OMHierarchyManager, OMLegalEntity, OMOperatingUnit
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.assetid: babde0c6-bb5d-45ae-95ca-2af75a0ea292
ms.search.region: Global
# ms.search.industry: 
ms.author: sericks
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Plan your organizational hierarchy

[!include [banner](../includes/banner.md)]

Before you set up organizations and organization hierarchies, make sure that you plan how your business will be modeled. The organization model has a significant effect on the implementation and business processes.

Organizational hierarchies represent the relationships between the organizations that make up a business. Therefore, the most important consideration when you model organizations is the structure of your business. We recommend that you define organization structures based on feedback from executives and senior managers from functional areas, such as finance and accounting, human resources, operations, purchasing, and sales and marketing.

When you are planning hierarchies, it is also important to consider the relationship between the organizational hierarchy and financial dimensions. You can set up multiple organizational hierarchies to represent different views of your business. By using financial dimensions, you can create reports based on these views. Work with your partner to create hierarchies that address both organizational and statutory reporting needs.

> [!NOTE]
> Although you can use financial dimensions to represent legal entities without creating the legal entities, financial dimensions aren't designed to address the operational or business needs of legal entities. The interunit accounting functionality is designed to address only the accounting entries that are created by each transaction.

> [!IMPORTANT]
> You shouldn't decide how to model organizations based only on the information in this article. This documentation is a guide. You can work with your Partner for additional guidance. Your Partner has gained experience in various industries and across the customer base.

## Decide whether to model internal organizations as legal entities or operating units

You must have at least one legal entity to represent your business. A legal entity can enter legal contracts and is required to prepare financial statements that report on its performance.

Legal entities can be used for transactional business or for consolidation. This means that a legal entity in finance and operations does not necessarily represent a real entity in your business. For example, a company that participates in transactions can own subsidiary legal entities. In this scenario, a legal entity is required for transactions, and a virtual legal entity is required to consolidate the results and balances of the subsidiary legal entities.

Internal organizations in your business, such as regional offices, can be represented as additional legal entities, or as operating units of the main legal entity. An operating unit is not required to be a legally defined organization. Operating units are used to control economic resources and operational processes in the business. For example, departments and cost centers are operating units.

Some functionality works differently depending on whether the organization is a legal entity or an operating unit. Carefully consider the functionality described below as you make your decision.

### Master data

#### If the organization is modeled as a legal entity

Some master data, such as customers, payment terms, tax authorities, and site-specific stock ordering, must be set up for each legal entity. Some master data, such as users, products, and most human resources data, is shared among all legal entities.

#### If the organization is modeled as an operating unit

Master data is shared among operating units.

### Module parameters

#### If the organization is modeled as a legal entity

Parameters for modules, such as Accounts receivable parameters, Accounts payable parameters, and Cash and bank management parameters, must be set per legal entity. Because the module setup for legal entities is separate, each subsidiary can comply with local statutory requirements and business practices. For example, a professional services legal entity and a manufacturing legal entity can have different module parameters even though they report to the same parent company.

#### If the organization is modeled as an operating unit

Module parameters are shared among operating units.

### Data security

#### If the organization is modeled as a legal entity

Most data is automatically secured by company ID. A company ID is a unique identifier for the data that is associated with a legal entity. A company can be associated with only one legal entity, and a legal entity can be associated with only one company. Users can access data only for the companies that they have access to. You do not need to customize to secure data by company ID.

#### If the organization is modeled as an operating unit

Data can be secured per operating unit by creating customized data security policies. Data security policies are used to limit access to data. For example, assume that a user is allowed to create purchase orders only in a particular operating unit. Data security policies can be created to prevent the user from accessing purchase order data from any other operating unit. The volume of transactions and the number of security policies can affect performance. When you design security policies, keep performance in mind.

### Ledgers

#### If the organization is modeled as a legal entity

Each legal entity requires a ledger that provides a chart of accounts, accounting currency, reporting currency, and fiscal calendar. A balance sheet can be created only for a legal entity. Main accounts, dimensions, account structures, charts of accounts, and account rules can be used by more than one legal entity.

#### If the organization is modeled as an operating unit

An operating unit can't have its own ledger information. If your internal organizations do not require unique ledgers, you can model them as operating units. Ledger information will be set up for the parent legal entity in the hierarchy. Income statements can be created for operating units within a legal entity or for the parent legal entity.

### Fiscal calendars

#### If the organization is modeled as a legal entity

Each legal entity has its own fiscal calendar. If your internal organizations use different fiscal years and fiscal calendars, you must model the organizations as legal entities.

#### If the organization is modeled as an operating unit

Operating units must share a fiscal calendar. If your internal organizations can use the same fiscal years and fiscal calendars, you can model the organizations as operating units.

### Consolidation

#### If the organization is modeled as a legal entity

You must consolidate the financial results for regional offices into a single, consolidated company in order to prepare financial statements.

#### If the organization is modeled as an operating unit

Consolidation is not required, because data is already shared among operating units.

### Centralized payments

#### If the organization is modeled as a legal entity

Centralized payments must be set up so that invoices for all child legal entities can be paid to or from a single parent legal entity.

#### If the organization is modeled as an operating unit

Centralized payments are not required because all invoices are recorded in a single legal entity.

### Intercompany transactions

#### If the organization is modeled as a legal entity

Intercompany sales orders, purchase orders, payments, or receipts can be applied to one another. You are not required to use journal vouchers. You can view intercompany transactions at the sub-ledger level (Accounts receivable, Accounts payable). The following examples illustrate how intercompany transactions are handled.

##### Example 1: Headquarters provides services to regional offices and must charge the costs of those services to the regional offices

If you model the regional office as a legal entity, you have the following options:

- Headquarters creates a journal entry to cross-charge the regional office for the expense. The transactions cannot be aged.
- Headquarters sends a purchase order for the services to the regional office. A sales order is automatically created in the legal entity for the regional office, with intercompany sub-ledger transactions.

##### Example 2: Headquarters procures and pays for service that is delivered to a regional office

If you model the regional office as a legal entity, you have the following options:

- The invoice and payment follow the regulatory requirements of headquarters. Headquarters can create a journal entry to cross-charge the regional office for the expense. The transactions cannot be aged.
- The invoice and payment follow the regulatory requirements of headquarters. Headquarters can create an intercompany sub-ledger transaction.

#### If the organization is modeled as an operating unit

Intercompany transactions among operating units are supported only through journal vouchers. An operating unit cannot issue or receive a purchase order, sales order, or invoice from another operating unit in the same legal entity. You cannot view intercompany transactions at the sub-ledger level (Accounts receivable, Accounts payable). The following examples illustrate how intercompany transactions are handled.

##### Example 1: Headquarters provides services to regional offices and must charge the costs of those services to the regional offices

If you model the regional office as an operating unit, headquarters enters an expense transaction and codes it to the regional office.

##### Example 2: Headquarters procures and pays for service that is delivered to a regional office

If you model the regional office as an operating unit, the invoice and payment follow the regulatory requirements of headquarters. The invoice can be coded to the regional office. On the income statement, use a balancing financial dimension to report costs for the regional office.

### Local tax requirements

#### If the organization is modeled as a legal entity

A legal entity is subject to the tax laws of the tax authority in the country/region where the legal entity is registered. For example, a legal entity that is registered in Denmark is subject to Danish tax laws and regulations. A legal entity can belong to only one country/region. The country/region that you select for the primary address of the legal entity controls the country/region-specific features that are available to that legal entity. For example, if the primary address of the legal entity is in Denmark, features that are related to Danish tax laws and regulations become available. Therefore, if your organizations are in different countries/regions and require different local tax options, you must set up the organizations as separate legal entities.

#### If the organization is modeled as an operating unit

Operating units use the country context of the parent legal entity. Operating units in the same legal entity cannot have different country/region-specific requirements. If your organizations are in the same country/region and use the same tax options, you can set them up as operating units.

### Statutory reporting for a country/region

#### If the organization is modeled as a legal entity

For countries/regions that are supported, most statutory reports can be created. 

> [!NOTE]
> A posting layer in the general ledger allows you to make adjusting entries to a parent company that uses a different accounting standard than the child company. For example, for a company that uses generally accepted accounting practices in the United Kingdom (UK GAAP), you can make adjusting entries in the posting layer. These entries can be consolidated into a parent company that uses generally accepted accounting principles (GAAP) in the United States. The adjusting entries do not affect UK GAAP reporting.

#### If the organization is modeled as an operating unit

Statutory reports must be created by using another application. You must ensure that data is captured in finance and operations apps to support the requirements of each operating unit, where they differ from the requirements of headquarters.

### Currency

#### If the organization is modeled as a legal entity

If your organizations must use different functional currencies, you must model the organizations as legal entities. Functional currencies are set up per legal entity. However, you can enter transactions in multiple currencies.

#### If the organization is modeled as an operating unit

If your organizations can use a single functional currency, you can model the organizations as operating units. Operating units must share a functional currency. However, you can enter transactions and create reports in multiple currencies.

### Year-end closing

#### If the organization is modeled as a legal entity

If laws and accounting practices differ among the countries/regions where your organizations are located, you may require different year-end procedures per organization. This means that you must model the organizations as legal entities. Each legal entity has its own year-end procedures.

#### If the organization is modeled as an operating unit

If laws and accounting practices are the same among the countries/regions where your organizations are located, you may use a single set of year-end procedures. This means that you can model the organizations as operating units. All operating units must use the same year-end closing procedure.

### Number sequences

#### If the organization is modeled as a legal entity

Number sequences for some references can be set up per legal entity. Some number sequences can be shared.

#### If the organization is modeled as an operating unit

Number sequences for some references can be set up per operating unit. Some number sequences can be shared.

### Products

#### If the organization is modeled as a legal entity

Product definitions are shared, and they must be released to individual legal entities before they can be included in transactions. Each legal entity has its own set of released products that can be included in transaction documents. If your internal organizations must use different sets of products, you must model the organizations as legal entities.

> [!NOTE]
> Even though product definitions are shared, in each legal entity where a product has been released, you can specify different sales, purchase, and stocking parameters for the item at each inventory site.

#### If the organization is modeled as an operating unit

All operating units share the same set of products. If your internal organizations can share the same set of products, you can model the organizations as operating units.

### Inquiry and reporting

#### If the organization is modeled as a legal entity

You must manually change companies to enter transactions and perform inquiries in multiple legal entities. Because of data security boundaries, consolidated inquiry and reporting can be resource intensive and time-consuming.

#### If the organization is modeled as an operating unit

You do not need to change companies to access data from multiple operating units. Consolidated inquiry and reporting and individual regional inquiry is easier and faster.

## Best practices for modeling organizations and hierarchies

Consider the following best practices when you implement an organization hierarchy:

- Create a department to model the intersection between a legal entity and a business unit. You can then roll up data from a department to a legal entity for statutory reporting, and from a department to a business unit for internal reporting. Departments can serve as profit centers. If you use departments, you do not have to use legal entities and business units as dimensions in the account structure. You can use just departments as a dimension. However, you must use both cost centers and departments as dimensions in the account structure if cost centers are used only as cost accumulators, and departments are used for revenue recognition.
- Model multiple hierarchies for operating units if you have complex requirements for reporting profit and loss.
- In a single legal entity, do not model multiple hierarchies for the same hierarchy purpose.
- Do not create a hierarchy for every purpose. Usually, you can use one hierarchy for multiple purposes. For example, one hierarchy of operating units can be assigned to all policy-related purposes.
- Create balanced hierarchies. In a hierarchy, all nodes that are the same distance from the root node are defined as a level. In a balanced hierarchy, only one type of operating unit can occur at each level, and the distance from the root node to each level is consistent. If there are intermediate levels between a department and a legal entity or a business unit, placeholder organizations may be required to create a balanced hierarchy.
- Do not model a separate hierarchy of operating units if the structure for legal entities is also your operating structure. A mixed hierarchy of legal entities and operating units may serve both purposes.
- Before you model major restructuring scenarios, use the hierarchy's effective dates to perform an impact analysis and a validation test.
- Use draft mode to change a hierarchy before you publish a new version in a production environment.
- Limit the number of people who have permissions to add or remove organizations from a hierarchy in a production environment. A smaller number reduces the chance that costly mistakes can occur and corrections must be made.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

