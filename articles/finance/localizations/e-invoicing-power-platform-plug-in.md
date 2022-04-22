---

# required metadata

title: Microsoft Power Platform plug-in admin reference
description: This topic provides information about how to set up and configure the Electronic invoicing solution in Microsoft Dataverse.
author: germansh
ms.date: 02/10/2022
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

# Microsoft Power Platform plug-in admin reference

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This topic provides information about how to set up and configure the Electronic invoicing solution in Microsoft Dataverse.

## Prerequisites

The following requirements must be met before you configure the Dataverse solution for Electronic invoicing:

- [Platform updates for version 10.0.23 of Finance and Operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-23.md) must be installed.
- Microsoft Power Platform integration with Finance and Operations must be configured. For more information, see [Enable the Microsoft Power Platform integration](../../fin-ops-core/dev-itpro/power-platform/enable-power-platform-integration.md).
- Electronic invoicing for Finance and Operations apps must be configured. For more information, see [Get started with Electronic invoicing service administration](e-invoicing-get-started-service-administration.md).
- The business events catalog must be synced, and the periodic processing batch job must be running. For more information, see [Business events overview](../../fin-ops-core/dev-itpro/business-events/home-page.md).

## Getting the solution

The [Dataverse solution for Electronic invoicing (Microsoft Dynamics 365 Electronic Invoicing connector for Microsoft Dataverse)](https://appsource.microsoft.com/product/dynamics-crm/mscrm.electronic-invoicing) must be installed from AppSource. After the installation process is complete, make sure that the **msdyn_MicrosoftDynamicsElectronicInvoicing** solution appeared in the solutions list in Dataverse. This solution adds a list of Electronic invoicing entities that contain audit and log information for electronic invoicing submissions. The solution also adds a business logic plug-in that implements communication with the Electronic invoicing solution.

## Authentication and authorization

After the solution is imported into the Dataverse environment, the Finance and Operations apps environment and the Dataverse environment must be set up to connect to each other. Dataverse will call Finance and Operations apps by using Service-to-Service (S2S) authentication, based on an Azure Active Directory (Azure AD) application. The security role for Finance and Operations apps must be manually added by the system administrator. Different security roles can be assigned to users in your Finance and Operations apps. The roles that are assigned to a user (for example, the Accounts payable clerk) depend on the functions that the user requires to perform their duties. These assigned roles must have the privileges to run the corresponding virtual entities and business events.

Follow these steps to assign security roles.

1. In your Finance and Operations apps, go to **System administration** \> **Users**.
2. In the list, find and select the user that you want to assign security roles to, and then select **Assign roles**.
3. Select the roles to assign.
4. Save your changes.

Follow these steps to set up the integration between environments.

1. In Regulatory Configuration Services (RCS), go to **Globalization features** \> **Environments** \> **Service environments**, and select the target service environment.
2. In the **Dataverse endpoint URI** field, enter `https://<Dataverse organization URL>/api/data/v9.1/`.
3. In your Finance and Operations apps, go to **System Administration** \> **Setup** \> **Azure Active Directory applications** to register Dataverse.
4. Add a row.
5. In the **Client ID** field, enter **ecd93392-c922-4f48-9ddf-10741e4a9b65**.
6. In the **Name** field, enter **Microsoft Dataverse Integration**.
7. In the **User ID** field, select the user that you assigned security roles to in the previous procedure.
8. Go to **Organization Administration** \> **Setup** \> **Electronic document parameters** \> **Dataverse integration**.
9. Register a new app. For more information, see [Register the app in the Azure portal](../../fin-ops-core/dev-itpro/power-platform/admin-reference.md#register-the-app-in-the-azure-portal).
10. Set up the Azure key vault, and put the app secret there. For more information, see [Set up the Azure Key Vault client](setting-up-azure-key-vault-client.md).
11. On the **Dataverse integration** page, on the **Dataverse integration** tab, enter the app ID and secret.
12. Create an application user in Dataverse, and associate it with the app ID. For more information, see [Create an application user](/power-platform/admin/manage-application-users#create-an-application-user). This user should be assigned a security role that has privileges to read and write the following Dataverse entities:

    - Electronic Invoice Submission
    - Electronic Invoice Submission Document

13. Create another application user in Dataverse, and associate it with the app ID **ecd93392-c922-4f48-9ddf-10741e4a9b65**. This user should be assigned the **Finance and Operations Basic User** security role and a role that has privileges to read and write the following Dataverse entities:

    - Electronic Invoice Action
    - Electronic Invoice Execution
    - Electronic Invoice Submission
    - Electronic Invoice Submission Document

## Enabling virtual entities

The Dataverse solution for Electronic invoicing for Indonesia depends on a set of virtual entities that must be enabled before you run the Electronic invoicing scenario. Because so many entities that are enabled for Open Data Protocol (OData) are available in Finance and Operations apps, the entities aren't available as virtual entities in Dataverse by default.

For more general information about how to enable virtual entities in Dataverse, see [Enable Microsoft Dataverse virtual entities](../../fin-ops-core/dev-itpro/power-platform/enable-virtual-entities.md).

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
