---

# required metadata

title: Microsoft Power Platform plug-in admin reference
description: This topic provides information about how to set up and configure the Electronic invoicing solution in Microsoft Dataverse.
author: germansh
ms.date: 11/30/2021
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

This topic provides information about how to set up and configure the Electronic invoicing solution in Microsoft Dataverse.

## Prerequisites

The following conditions must met before you configure the Dataverse solution for Electronic invoicing:

- [Platform updates for version 10.0.23 of Finance and Operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-23.md)
- Microsoft Power Platform integration with Finance and Operations needs to be configured: [Enable the Microsoft Power Platform integration](../../fin-ops-core/dev-itpro/power-platform/enable-power-platform-integration.md)
- Electronic invoicing for Microsoft Dynamics 365 Finance and Operations apps needs to be configured. For more information, see [Get started with Electronic invoicing service administration](e-invoicing-get-started-service-administration.md).
- The business events catalog must be synchronized and the periodic processing batch job must be running. For more information, see [Business events overview](../../fin-ops-core/dev-itpro/business-events/home-page.md).

## Getting the solution

The Dataverse solution for Electronic invoicing must be installed from Microsoft AppSource: [Connector for Electronic Invoicing and Dataverse](https://appsource.microsoft.com/en-us/product/dynamics-crm/mscrm.electronic-invoicing). Make sure that the following solution is installed in Dataverse.

- **msdyn_MicrosoftDynamicsElectronicInvoicing**: This solution adds a list of Electronic invoicing entities that contain audit and log information for electronic invoicing submissions and a business logic plug-in that implements communication with the Electronic invoicing solution.

## Authentication and authorization

After the solutions are imported in the Dataverse environment, both environments, Finance and Operations apps and Dataverse, must be set up to connect to each other. Dataverse will call Finance and Operations apps using Service-to-Service (S2S) authentication, based on an Azure Active Directory (AAD) application. The security role for Finance and Operations apps must be added manually by the system administrator. Different security roles can be assigned to the user in your Finance and Operations apps. This is based on the functions that the user needs to perform their duties. For example, the Accounts payable clerk. This assigned role must have the privilege to run the corresponding Virtual Entities and Business events.

Complete the following steps to assign a security role.

1. In your Finance and Operations apps, go to **System administration** > **Users**.
2. In the list, locate and select the user you want to assign a security role to, and select **+ Assign roles**. 
3. Select the roles you want to assign.
4. Save your changes.

Complete the following steps to set up the integration between environments. 

1. In Regulatory Configuration Services (RCS), go to **Globalization features** > **Environments** > **Service environments** and  select the target service environment. 
2. In the **Dataverse endpoint URI** field, enter **https://{Dataverse organization URL}/api/data/v9.1/**.
3. In your Finance and Operations apps, go to **System Administration** > **Setup** > **Azure Active Directory applications** to register Microsoft Dataverse.
4. Add a new row and in the **Client ID** field, enter **ecd93392-c922-4f48-9ddf-10741e4a9b65**.
5. In the **Name** field, enter **Microsoft Dataverse Integration** and in the **User ID** field, select the the user that you assigned the security roles to.
6. Go to **Organization Administration** > **Setup** > **Electronic document parameters** > **Dataverse integration**.
7. Register a new app. For more information, see [Register the app in the Azure portal](../../fin-ops-core/dev-itpro/power-platform/admin-reference.md#register-the-app-in-the-azure-portal).
8. Set up the Azure Key Vault and put the app secret there. For more information, see [Set up the Azure Key Vault client](setting-up-azure-key-vault-client.md).
9. On the **Dataverse integration** page, on the **Dataverse integration** tab, enter the App ID and secret.
10. Create an application user in Dataverse, and associate the user with the App ID. For more information, see [Create an application user](/power-platform/admin/manage-application-users#create-an-application-user). The user should be assigned a security role with privileges to read and write the following Dataverse entities:

     -  Electronic Invoice Submission
     - Electronic Invoice Submission Document

10. Create another application user in Dataverse, and associate them with the App ID, **ecd93392-c922-4f48-9ddf-10741e4a9b65**. For more information, see [Create an application user](/power-platform/admin/manage-application-users#create-an-application-user).

    The user should be assigned the **Finance and Operations Basic User** security role and role with privileges to read and write the following Dataverse entities:

    - Electronic Invoice Action
    - Electronic Invoice Execution
    - Electronic Invoice Submission
    - Electronic Invoice Submission Document

## Enabling virtual entities

The Dataverse solution for Electronic invoicing for Indonesia depends on a set of virtual entities which need to be enabled before you run the Electronic invoicing scenario. Because of the large number of OData enabled entities available in Finance and Operations apps, the entities are not available as virtual entities by default in Dataverse.

For more general information on how to enable virtual entities in Dataverse, see [Enable Microsoft Microsoft Dataverse virtual entities](../../fin-ops-core/dev-itpro/power-platform/enable-virtual-entities.md).

For Indonesia, the following virtual entities must be enabled in Dataverse:

- BusinessDocumentBatchSubmissionItemEntity
- BusinessDocumentSalesInvoiceBaseEntity
- BusinessDocumentSalesInvoiceLineItemEntity
- BusinessDocumentProjectInvoiceBaseEntity
- BusinessDocumentProjInvoiceCostLineEntity
- BusinessDocumentProjInvoiceEmplLineEntity
- BusinessDocumentProjInvoiceItemLineEntity
- BusinessDocumentProjInvoiceOnAccLineEntity
- BusinessDocumentProjInvoiceRevenueLineEntity
- BusinessDocumentCustTransEntity
- BusinessDocumentCustVendCreditInvoicingJourEntity
- BusinessDocumentTaxGroupHeadingEntity
- BusinessDocumentTaxTableEntity
- BusinessDocumentTaxTransactionEntity
- BusinessDocumentParametersEntity



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
