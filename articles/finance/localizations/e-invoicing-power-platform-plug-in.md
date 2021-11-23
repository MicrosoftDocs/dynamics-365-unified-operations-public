---

# required metadata

title: Power Platform plug-in admin reference
description: This topic provides step-by-step instructions about how to set up and configure Electronic invoicing solution in Microsoft Dataverse
author: germansh
ms.date: 11/17/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: Power Platform, Electronic invoicing, Dataverse
# ROBOTS: 
audience: Administration User
# ms.devlang: 
ms.reviewer: 
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: germansh
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Power Platform plug-in admin reference

[!include [banner](../includes/banner.md)]
This topic provides step-by-step instructions about how to set up and configure
Electronic invoicing solution in Microsoft Dataverse.

# Prerequisites

The Microsoft Dataverse solution for Electronic invoicing requires the following
conditions to be met before starting with the solution configuration:

-   [Platform updates for version 10.0.23 of Finance and Operations
    apps](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-23)

-   Electronic invoicing for Microsoft Dynamics 365 Finance and Operations needs
    to be configured: [Get started with Electronic invoicing service
    administration](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/e-invoicing-get-started-service-administration?toc=/dynamics365/finance/toc.json)

-   Business events catalog is synchronized and the periodic processing batch
    job is running: [Business events overview](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/business-events/home-page)

# Getting the solution

The Microsoft Dataverse solution for Electronic invoicing must be installed from
Microsoft AppSource. For more information, see (AppSource link).

Ensure the following solution is installed in Microsoft Dataverse.

-   **msdyn_MicrosoftDynamicsElectronicInvoicing** - This adds a list of
    Electronic Invoicing entities which will contain audit and logs information
    for electronic invoicing submissions as well as a business logic plugin
    implementing communication with the Electronic Invoicing.

# Authentication and authorization

After the solutions are imported in the Microsoft Dataverse environment, both
environments, Finance and Operations and Microsoft Dataverse, must be set up to
connect to each other. Microsoft Dataverse will call Dynamics 365 products
Finance and Operations applications using Service-to-Service (S2S)
authentication, based on an Azure Active Directory (AAD) application. The
security role for Finance and Operations must be added manually by the system
administrator. Different security roles can be assigned to the user in Finance
and Operations. This is based on the functions that the user needs to perform
his/her duties, eg Accounts payable clerk, etc. This assigned role needs to have
the privilege to run the corresponding Virtual Entities and Business events.

The next steps walk through this process in Finance and Operations apps.

To assign a security role:

1.  Launch Finance and Operations

2.  Navigate to System Administration

3.  Select and Click the Users option

4.  Find the user you want to assign a security role

5.  Click the + Assign roles button

6.  Select the role(s) you want to assign.

To set up integration

-   In Finance and Operations go to System Administration \> Setup \> Azure Active Directory applications
    to register Microsoft Dataverse.

    -   Add a new row.

    -   Client ID - The Application (client) ID -
        **ecd93392-c922-4f48-9ddf-10741e4a9b65**

    -   Name - Enter Microsoft Dataverse Integration (or a different name).

    -   User ID - The user ID with the sufficient security roles configured
        above.

-   In Finance and Operations go to Organization Administration \> Setup \> Electronic document parameters \> Dataverse integration
    to set up the app used for integration with Dataverse.
    
    -   Register a new app: [Register the app in the Azure portal](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/power-platform/admin-reference#register-the-app-in-the-azure-portal)
       
    -   Set up the Azure Key Vault and put the app secret there: [Set up the Azure Key Vault client](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/setting-up-azure-key-vault-client)

    -   Set up the App ID and Secret on the Dataverse integration tab.

    -   Create an Application User in Microsoft Dataverse, associated with the App ID: [Create an application user](https://docs.microsoft.com/en-us/power-platform/admin/manage-application-users#create-an-application-user). The user should be assigned a security role and having privileges to read/write the following Dataverse entities:

        -   Electronic Invoice Submission

        -   Electronic Invoice Submission Document

-   Create an Application User in Microsoft Dataverse, associated with the App
    ID - **ecd93392-c922-4f48-9ddf-10741e4a9b65:** [Create an application user](https://docs.microsoft.com/en-us/power-platform/admin/manage-application-users#create-an-application-user).

    The user should be assigned the 'Finance and Operations Basic User' security role and a role having privileges to read/write the
    following Dataverse entities:

    -   Electronic Invoice Action

    -   Electronic Invoice Execution

    -   Electronic Invoice Submission

    -   Electronic Invoice Submission Document

# Enabling virtual entities

The Microsoft Dataverse solution for Electronic invoicing for Indonesia depends
on a set of virtual entities which need to be enabled prior to running the
electronic invoicing scenario. Due to the large number of OData enabled entities
available in Finance and Operations, by default, the entities are not available
as virtual entities in Microsoft Dataverse.

General information on how to enable virtual entities in Microsoft Dataverse can
be referenced here: [Enable Microsoft Microsoft Dataverse virtual
entities](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/power-platform/enable-virtual-entities).

For the Indonesia scenario the following virtual entities are required to be
enabled in Microsoft Dataverse:

-   BusinessDocumentBatchSubmissionItemEntity

-   BusinessDocumentSalesInvoiceBaseEntity

-   BusinessDocumentSalesInvoiceLineItemEntity

-   BusinessDocumentProjectInvoiceBaseEntity

-   BusinessDocumentProjInvoiceCostLineEntity

-   BusinessDocumentProjInvoiceEmplLineEntity

-   BusinessDocumentProjInvoiceItemLineEntity

-   BusinessDocumentProjInvoiceOnAccLineEntity

-   BusinessDocumentProjInvoiceRevenueLineEntity

-   BusinessDocumentCustTransEntity

-   BusinessDocumentCustVendCreditInvoicingJourEntity

-   BusinessDocumentTaxGroupHeadingEntity

-   BusinessDocumentTaxTableEntity

-   BusinessDocumentTaxTransactionEntity

-   BusinessDocumentParametersEntity
