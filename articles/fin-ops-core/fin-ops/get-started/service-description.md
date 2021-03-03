---
# required metadata

title: Service description for Dynamics 365 Finance and Dynamics 365 Supply Chain Management apps
description: This topic provides the service description for Dynamics 365 Finance and Dynamics 365 Supply Chain Management.
author: shellybakke
manager: AnnBe
ms.date: 03/04/2021
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: NotInTOC
ms.search.region: Global
# ms.search.industry:
ms.author: sericks
ms.search.validFrom: 2021-03-31
ms.dyn365.ops.version: 10.0.18
---

# Service description for Dynamics 365 Finance and Dynamics 365 Supply Chain Management apps

[!include[banner](../includes/banner.md)]

## Overview

Microsoft Dynamics 365 Finance and Supply Chain Management is a cloud Enterprise Resource 
Planning (ERP) service for enterprises, built on and for Microsoft Azure. It provides organizations with ERP functionality that supports their unique requirements and helps them adjust to constantly changing business environments, without the hassle of managing infrastructure. Finance and Supply Chain Management brings together a set of ERP, business intelligence, infrastructure, compute, and database services in a single offering that enables organizations to run industry-specific and operational business processes that are extendable with specific solutions from Independent Software Vendors (ISV) (see Microsoft AppSource). Organizations can match their business growth by easily adding users and business processes with a simple, transparent subscription model.  

- [Microsoft AppSource](https://appsource.microsoft.com/partners)
- [Licensing Guide](https://dynamics.microsoft.com/finance-and-operations-to-finance-and-scm/)

The Finance and Supply Chain Management cloud service is comprised of the components illustrated below.

![Illustration showing devices in the Finance and Supply Chain Managemnt environments](media/Devices.png)

## Operating model

The operating model of Finance and Supply Chain Management distinguishes specific roles and responsibilities for Customer, Implementation Partner, and Microsoft throughout the lifecycle of the service. 

Microsoft maintains the Finance and Supply Chain Management service by deploying, actively monitoring, and servicing the Customer’s production tenants.  This includes allocating the required system infrastructure to run the service and proactive communication to Customers about the service’s health. 

![Implementation roles and responsibilities](media/implementation-roles-responsibilities.png)

With the support of their Implementation Partner, Customers determine the configuration of the business application logic in Finance and Supply Chain Management to match their unique business processes. Customers can extend Finance and Supply Chain Management with ISV solutions of their choice, unique customizations, or a combination of these. Customers typically choose one of the following configuration scenarios: 

-	**Solution 1:** Standard Finance and Supply Chain Management configuration (no extension) 
-	**Solution 2:** Finance and Supply Chain Management configuration with Customer-specific extensions 
-	**Solution 3:** Finance and Supply Chain Management configuration with one or more ISV solutions and Customer-specific extensions 

For any of these scenarios, the Customer defines, develops, and tests any modifications using Microsoft Dynamics Lifecycle Services (LCS) and tools. 

![Common configuration scenarios](media/common-configuration-scenarios.png)

## System configuration

Finance and Operations scales with transaction volume and User load. Each Customer implementation of Finance and Operations produces a unique solution due to the following variables: 

-	**Data composition:** A unique set of parameters that control behavior, layout of the organization, structure of master data (such as financial and inventory dimensions), and granularity of transaction tracking. 
-	**Extension and configuration:** Extension mechanisms of Finance and Supply Chain Management with code extensions, ISV solutions, and unique configurations including workflows, integrations, and report configurations. 
-	**Usage patterns:** A unique combination of online and batch usage combined with the ability to integrate with upstream and downstream systems for unified data flow and the ability to differentiate based on the information views used by Customers in their business processes. 

Microsoft configures production tenants sized to handle the transaction volumes and user concurrency. Microsoft is responsible for: 

-	Proper allocation of resources of production tenants, based on the Customer’s profiling information in the LCS Subscription Estimator; 
-	Continually monitoring and diagnosing service availability of production tenants; and 
-	Analyzing and troubleshooting system performance issues with Finance and Operations. 

To ensure that an implementation is configured for high performance, Customers must:

-	Provide accurate usage information for the Finance and Supply Chain Management implementation through the LCS Subscription Estimator; 
- Build and test extensions for performance and scale; and 
-	Test data configurations appropriately for performance. 

## Service operations

Service operations reflect various aspects of provisioning and use of Finance and Supply Chain Management, from onboarding and implementation to updates and monitoring. For each successful implementation of Finance and Supply Chain Management, Microsoft, the Customer, and Implementation Partners or ISVs (when applicable) have specific roles and responsibilities. 

![Service operations](media/service-operations.png)

### Onboarding and implementation

Typical onboarding and implementation events and the expected responsibilities for each party are provided in the following table.

|Request |	Expected Microsoft action |	Expected Customer/ Implementation Partner action |
|--------|-----------------------------|--------------------------------------------------|
|Initial offer purchase |	LCS project is created after the purchase of the offer.  |	Go through EA or CSP onboarding process. Partner creates tenant for Customer, if applicable. |
|Add-On purchase |	Grant Customer access to Add-On selected during the implementation. |	Not applicable. |
|Implementation planning and analysis |	Provide relevant tools in LCS, such as Business Process Modeler and interoperability with Visual Studio Online.| 	Project planning, Visual Studio Team Services, System onboarding and admin account setup. |

For more information, see [Onboard an implementation project](../imp-lifecycle/onboard.md)
  
### Tenant and data management 

Typical tenant and data management events for the Service and the responsibilities for each party are described in Table 2.1 for Production Instances and Table 2.2 for Non-Production Instances.   

|Customer's request |	Customer's responsibility |	Microsoft's responsibility |	Microsoft's lead time |	Microsoft's estimated maintenance downtime |
|-------------------|----------------------------|---------------------------|--------------------------|------------------------------------------|
|Deploy a new Production Instance |	Request submitted through service request in LCS and available through LCS for self-service deployments.<br><br>- Accurately complete the sizing questionnaire in the LCS Subscription Estimator before requesting a Production Instance.<br><br>- Complete all implementation tasks specified in the LCS checklists. |- Complete Go live health check from Microsoft Fasttrack Services.<br><br>- Deploy a Production Instance only after Customer has completed all LCS checklists and notify Customer of the provisioned environment through email.|	2 business days* | N/A |
|Copy a Non-Production Instance database to a Production Instance before go-live.<br><br>(Note: This request is not available if Customer already is live in production) |	Request submitted through service request in LCS and available through LCS for self-service deployments.<br><br>Validation and sign-off. 	|Copy a Non-Production Instance (e.g., Sandbox Tier 2 Add-on) database to a Production Instance as part of the go-live process. |	5 hours*| 	1-4 hours |
|Maintenance mode 	| - Put AOS in maintenance mode through LCS.<br><br>- Complete necessary maintenance.<br><br>- Request to put the AOS back into active mode. |	N/A |	N/A 	|2 hours| 

Microsoft will provide point in time restoration of Customer’s Non-Production Instance databases as described in Table 2.2.

|Customer's request |	Customer's responsibility |	Microsoft's responsibility |	Microsoft's lead time |	Microsoft's estimated maintenance downtime |
|-------------------|-----------------------------|------------------------------|-----------------------|----------------------------------------|
|New sandbox instance |	Request submitted through service request in LCS and available through LCS for selfservice deployments.<br><br>- Ensure all the instances needed, have been planned and Add-On offers purchased.<br><br>- Complete all implementation tasks specified in the LCS checklists. 	|- Ensure instance request is against a base subscription or an AddOn offer.<br><br>- Deploy the instance and notify the Customer and Implementation Partner.<br><br>- A sandbox instance is a Tier-1 development or build environment or a Tier-2 (or higher). Tier-2 (or higher) environments are multibox environments closer in topology to a production environment. |	2 business days* |	N/A |
|Copy golden configuration database from Dev/Test to Sandbox before go-live |	- Validation and sign-off.<br><br>- Prepare and export the database from a development environment 
(Tier 1).<br><br>- Trigger the import operation through LCS and update the database to a sandbox environment (Tier 2 or higher). |	N/A |	N/A 	|1-4 hours |
|Copy a Production Instance database to a Non-Production Instance |	Trigger the copy operation through LCS.<br><br>- Post-copy: Delete or obfuscate sensitive data, adjust environment specific application configuration (such as integration endpoints) and enable or add users.<br><br>- Customer should make these changes by applying a data package. |	N/A |	N/A 	|1-4 hours |
|Non-Production Instance database point in time restore 	|Accept that process cannot be undone.<br><br>Trigger the point in time restore operation through Lifecycle Services.  |	N/A |	N/A 	|1-8 hours |
|Copy Tier 2 Sandbox database to a Tier 1 Sandbox for troubleshooting and debugging |	Trigger database export operation through LCS on the sandbox environment.<br><br>Import and update the database in Tier 1 environment.| 	N/A |	N/A |	1-4 hours |

### Data back-up and retention 

Databases are protected by automatic back-ups. Automatic back-ups are Databases are protected retained for 30 days unless Microsoft performs a rollback. Rollbacks may by automatic back-ups as be performed in the event a failure occurs during any planned maintenance update specified in Table 4. For more information, see [Automated backups - Azure SQL Database & SQL Managed Instance](https://docs.microsoft.com/azure/azure-sql/database/automated-backups-overview?tabs=single-database).

### Service activity responsibilities

Table 3 describes some typical scenarios and activities for the Service along with the responsibilities of Microsoft, Customer, or both concerning such activities.

Activity 	Microsoft 	Customer 
Provisioning initial tenants 	
Size projected load in LCS using the Subscription Estimator tool and request specific environment(s) to be provisioned 	 	⚫ 
Provision all Production Instances and Non-Production Instances  	⚫ 	 
Validate the deployed Production Instances and Non-Production Instances 	 	⚫ 
Service updates 	
Microsoft applies service updates to a designated Non-Production and 
Production Instances 	⚫ 	⚫ 
Download update from LCS and define, develop, and test the update, and provide code update package back to LCS 	 	⚫ 
Request extension updates to be applied to the Production Instance 	 	⚫ 
Create code and data backup for Production Instance before applying any updates 	⚫ 	 
In case of any failure, roll back Production instance to code and data backup 	⚫ 	 
Data management (Backup, restore, and update) 	
Backup database  	⚫ 	 
Determine HA and disaster recovery plan 	⚫ 	 
Monitor Production Instance database performance 	⚫ 	⚫ 
Tuning the Production Instance database for performance  	⚫ 	⚫ 
Initiate copy of Production Instance database to Non-Production Instance 	 	⚫ 
 

Activity 	Microsoft 	Customer 
Update infrastructure 	
Schedule regular infrastructure updates 	⚫ 	 
Scale up and down (Users, storage, instances) 	
Purchase additional users and Non-Production add-ons 	 	⚫ 
Changes in usage must be updated in the LCS’ Subscription Estimator tool 	 	⚫ 
Report any significant performance issues impacting usage of the Service 	 	⚫ 
Proactively manage the resources needed for the Service applicable Service 	⚫ 	 
Investigate and troubleshoot Incidents 	⚫ 	⚫ 
Security (User access) 	
Provide user access to the Service 	 	⚫ 
Provide LCS project access for managing and operating instances deployed through LCS 	 	⚫ 
Monitor Production Instance 	
Monitor Production Instances 24x7 	⚫ 	⚫ 
Notify Customer proactively of incidents with the Production Instance 	⚫ 	 
Manage and Monitor Non-Production Instances 	
Manage Non-Production Instances with LCS  	 	⚫ 
Monitor Non-Production Instances 	 	⚫ 




