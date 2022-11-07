---
# required metadata

title: Configure integration for Dynamics 365 Human Resources 
description: This article explains an architecture for building an integration between Dynamics 365 Human Resources and other systems.
author: twheeloc
ms.date: 11/19/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: CDSIntegrationAdministration
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-10-05
ms.dyn365.ops.version: Human Resources
---

# Security configuration concepts for virtual table-based integrations 

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

## Introduction and background

This article explains an architecture for building an integration between Dynamics 365 Human Resources and a third-party system using [Dataverse virtual tables](/dev-itpro/power-platform/virtual-entites-overview). The article emphasis on security configuration and the authentication and authorization aspects required between the system boundaries in order to build a functional, secure system. 

### Prerequisite reference articles 

The following articles provide additional information about the concepts in this article: 

 - [Virtual entities overview](/dev-itpro/power-platform/virtual-entities-overview) 
 - [Get started with virtual tables (entities)](/developer/data-platform/virtual-entities/get-started-ve) 
 - [Use multi-tenant server-to-server authentication (Microsoft Dataverse)](/developer/data-platform/use-multi-tenant-server-server-authentication) 
 - [Use OAuth authentication with Microsoft dataverse (Dataverse)](/developer/data-platform/authenticate-oauth) 
 - [OAuth 2.0 client credentials flow on the Microsoft identity platform](/azure/active-directory/develop/v2-oauth2-client-creds-grant-flow) 
 - [Authentication and authorization](/dev-itpro/power-platform/authentication-and-authorization) 

### Architecture 

The following diagram represents the major concepts involved in an integration that uses Virtual tables (entities): 

![Virtual tables.](./media/hosts.jpg)

Identify the following diagram elements: 

Microsoft: 
 - Microsoft hosts and operates the various Dynamics 365 products (and related technologies) on behalf of customers. 
 - AAD Tenant ‘C’ – An Azure active directory tenant owned by Microsoft. This is the tenant in which the Dynamics 365 applications are registered. 

Integrating partner: 
- Integrating system – The system being integrated with Dynamics 365. This might be a payroll system or any system that rely on data stored in Dynamics 365. 
- Adapter – The software or service responsible for interacting with both Dynamics 365 and with the integrating system.

>[!NOTE] 
>Adapters that are intended to be used by multiple Dynamics 365 customers are expected to be registered in Azure active directory as multitenant applications.
 
-	Azure active directory tenant ‘A’ – The Azure active directory tenant owned by the integrating partner, and the tenant that the Adapter application ID is registered. 

Mutual customer (Implements Dynamics 365 Human Resources and the integrating partner’s solution): 
 - Dynamics 365 Human Resources – The customer-specific instance of Dynamics 365 Finance or Human Resources that contains the customer data required by the integrating system.
 - Dataverse – The customer-specific Dataverse environment connected to either Dynamics 365 Finance or Human Resources. Dataverse provides a Web API for interacting with Dynamics 365 data. 
 - Azure active directory Tenant ‘B’ – This is the customer’s Azure active directory tenant, and functions as the identity provider (Authorization Server). This issues tokens that authorize callers to call the customer’s Dataverse instance.

### Understanding the basic flow of a request

Let's look at the basic flow of a typical request involved in an integration. Refer to the architectural diagram for reference.

A typical request requires the Adapter to query Dynamics 365 for data and then save and synchronize that data to the integrating system:

1.	The adapter calls the Dataverse Web API to query for relevant data. 

>[!NOTE] 
>Authentication of which token acquisition is a major part and is a prerequisite. This will be describe in the Understanding authentication and authorization section.
 
  a.	This is a call against the Dataverse Web API to query for application data exposed through a virtual table. Refer to 2. Initial sync and 3. Delta sync in the diagram. 
    
2.	Dataverse handles the request by querying the Virtual table through the Virtual entity plugin (Virtual table proxy in the diagram). The Dataverse request is forwarded to the Dynamics 365 Finance or Human Resources Virtual entity service to query for the data that is physically stored in the Dynamics 365 Finance or Dynamics 365 Human Resources databases. 
3.	The Dynamics 365 Finance or Human Resources Virtual entity service translates the request made against the virtual entity into a query against the Finance or Human Resources entity that backs the Dataverse virtual entity. The data is retrieved from the database, translated back into the Dataverse entity representation, and returned to the caller. 
4.	The Adapter perform any necessary mappings and data translations required and makes a call to the integrating system to persist the data into the integrating 
system database. Refer to 4. Save data in the diagram. 

### Understanding Authentication and authorization at system boundaries 

Authentication is the validation that a user or application identity has been proven, confirming that the user or application is who they say they are. 
Authorization grants the user/application the right to access specific application-level permissions. 

>[!NOTE] 
>See Authentication vs. authorization for more information. 

Most cross-system calls (with the exception of the call from Dataverse to Dynamics 365 Finance or Human Resources through the Virtual Table Proxy) in the diagram involve the Adapter. The Adapter needs to authenticate itself to: 
 - Make the call to Dataverse 
 - Make calls to the integrating system  

Looking at the system boundaries in the diagram, understand that every web request between systems must be authenticated and that application-level authorization checks
will be performed before data will be returned to the caller. For a request against a Dynamics 365 Virtual Table backed byDynamics 365 Finance or Human Resources, the relevant system boundaries where authentication and authorization checks are enforced are: 

  1.	The call between the Adapter and the Dataverse Web API (Odata) endpoint 
  2.	The call between the Dataverse Virtual Entity plugin and the Dynamics 365 Dynamics 365 Finance or Human Resources Virtual entity service 

In both cases, authentication checks are performed first, followed by application-level authorization checks to ensure the authenticated user or application has the proper application-level privileges to retrieve the requested data. 

Authentication to call Dataverse is handled through a Bearer token that must be included as an HTTP header in the web request to Dataverse. The Adapter must get a token
from the Tenant ‘B’ Azure Active Directory instance (the call designated as “1. Get Token” in the diagram). AAD acts as the Identity Provider in the authentication flow.

The Adapter authenticates by providing its application identity (non-secret, as registered in AAD Tenant ‘A’) and an application secret or certificate possessed only by
the Adapter application. 

Once authenticated to make calls to Dataverse, the Dataverse-level authorization checks are performed against each request, ensuring the caller (the Adapter 
application’s identity designated as \<Guid A>\) has the appropriate application permissions. Application-level authorization is managed in Dataverse through an 
Application User that represents the Adapter application ID. Application-level permissions are managed by granting access to specific Dataverse-defined application 
roles. The roles, in turn, provide the granular privileges to the application. 

For more detailed guidance, see [Use multi-tenant server-to-server authentication](/power-apps/developer/data-platform/use-multi-tenant-server-server-authentication). 
  
Assuming Dataverse-level application permission checks pass, the Virtual entity plugin next makes a call to the Virtual entity service endpoint on the Dynamics 365 Finance or Human Resources environment. This call is made using Server-to-Server (S2S) authentication using the identity and secret configured in the finance and operations Virtual data source configuration record: 

![Sandbox.](./media/sandbox.jpg)


Refer to Configure Dataverse virtual entities - Finance & Operations | Dynamics 365 | Microsoft Learn for specifics. 

The call from the Dataverse virtual entity plugin to Dynamics 365 Finance or Human Resources includes the Adapter identity of the original call from the “Adapter” (the identity designated as \<Guid A>\ in the diagram) to Dataverse. Assuming the Virtual entity data source is configured correctly and the S2S Authentication checks pass, the Virtual entity service in Dynamics 365 Finance or Human Resources will run the query in the context of the original caller (the Adapter, aka identity \<Guid A>\). Dynamics 365 Finance or Human Resources level application permission checks (Authorization) will be done to ensure that the Adapter has the privileges required to access the data entities requested through the query. 


Finance/HR security is managed by: 
1. Mapping the Adapter identity (\<Guid A>\) to a specific Dynamics 365 Finance or Human Resources user. This is done on the **Azure Active Directory applications** page. For more information, see [Register your external application](/dev-itpro/data-entities/services-home-page.md#register-your-external-application). 
2. Granting the Dynamics 365 Finance or Human Resources user from (1) the appropriate application-level roles/duties/privileges. For more information, see [Role-based security](/dev-itpro/sysadmin/role-based-security). 
   
    
Assuming the Adapter application (\<Guid A>\) has been granted the privileges required:
 - to access the requested data  
 - the query is executed 
 - the data is translated back into its Dataverse entity page 
 - the data is returned to the Adapter

>[!NOTE]
>It is possible during development to run the Adapter using a Dynamics 365 Finance or Human Resources user that is in the Administrator role. In a production environment, the Adapter should never be run with Administrator privileges. 

### Key takeaways 
    
Important implications of the Virtual table or entity architecture are: 
 - Security configuration for Virtual tables that are backed by Dynamics 365 Human Resources is managed in Human Resources. 
 - The customer (Mutual customer in the diagram) has full control over what privileges are granted to the integrating Adapter identity (\<Guid A>\). 
 - The customer is responsible for proper security configuration of their Dynamics 365 Human Resources environment. The Integrating partner who creates the Adapter needs to provide guidance as to what privileges the Adapter requires. 
 

