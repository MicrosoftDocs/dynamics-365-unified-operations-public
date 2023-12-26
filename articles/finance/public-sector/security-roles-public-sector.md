---
# required metadata

title: Security roles in the public sector
description: This article provides information about public sector security roles including the Project manager and Purchasing agent roles.
author: v-kiarnd
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: UserRequestListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.assetid: e26a6d93-851e-46be-8543-de2798909350
ms.search.region: Global
ms.search.industry: Public sector
ms.author: twheeloc
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Security roles in the public sector

[!include [banner](../includes/banner.md)]

This article describes the functionality for public sector security roles. This functionality includes the Project manager and Purchasing agent roles for the public sector.

All users must be assigned to at least one security role to have access to Dynamics 365 Finance. Security roles determine which duties users can perform and which parts of the user interface they can view.

## What are the prerequisites for assigning security roles in the public sector?
Users must exist in Finance before you can assign them to roles. Even if you use automatic role assignment, users themselves aren't automatically added.

## Which roles do I have to assign?
After users are in the system, there are two roles that you might have to set up for public sector organizations:

-   Project manager
-   Purchasing agent

### What is the Project manager - Public sector role?

The **Project manager - Public Sector** security role supports the public sector extensions for Project management. Assign this role in addition to the **Project manager** role to give project managers access to project management functionality. By default, this security role is assigned the following duties.

| Duty name                                                         | Duty AOT name                           | Duty description                                                                |
|-------------------------------------------------------------------|-----------------------------------------|---------------------------------------------------------------------------------|
| Inquire into purchase order to invoice progress for public sector | PurchOrderToInvoiceProgressInquire\_PSN | Respond to inquiries about the status of the purchase order–to–invoice process. |

### What is the Purchasing agent - Public sector role?

The **Purchasing agent - Public Sector** security role supports the public sector extensions for Project management. Assign this role in addition to the **Purchasing agent** role to give purchasing agents access to purchasing functionality. By default, this security role is assigned the following duties.

| Duty name                                                       | Duty AOT name                            | Duty description                                                                                        |
|-----------------------------------------------------------------|------------------------------------------|---------------------------------------------------------------------------------------------------------|
| Maintain purchase agreement master                              | AgreementPurchaseAgreementMasterMaintain | Maintain the details of purchase agreements.                                                            |
| Configure AIF synchronization                                   | AifSyncConfigure                         | Specify filters on ports.                                                                               |
| Inquire into purchasing case progress                           | CasePurchasingCaseProgressInquire        | Respond to inquiries about the status of purchasing cases.                                              |
| Maintain catalogs                                               | CatProcurementCatalogMasterMaintain      | Maintain all types of catalogs.                                                                         |
| Maintain all category hierarchy details                         | EcoResCategoryMasterMaintain             | Maintain categories.                                                                                    |
| Inquire into products definition master                         | EcoResProductDefinitionMasterInquire     | Respond to inquiries about master data for product definitions.                                         |
| Inquire into product builder configuration data                 | PBAProductBuilderConfigStatusInquire     | Open and review product builder configurations.                                                         |
| Maintain product builder configuration                          | PBAProductBuilderConfigurationMaintain   | Edit and update product builder configurations.                                                         |
| Maintain product configuration                                  | PCProductConfigConfigurationMaintain     | Maintain a constraint-based configuration for product configuration models.                             |
| Inquire into product configuration                              | PCProductConfigConfigurationStatInquir   | Respond to inquiries about configuration master data for constraint-based product configuration models. |
| Maintain purchase setup print management settings               | PrintMgmtPurchaseSettingsMaintain        | Maintain print management settings for purchase setups.                                                 |
| Maintain purchase document print management settings            | PrintMgmtPurchDocumentSettingsMaintain   | Maintain print management settings for purchase documents.                                              |
| Inquire into purchasing policies                                | ProcPurchasingProcessInquire             | Respond to inquiries about policies that govern the purchasing process.                                 |
| Inquire into purchasing policies for public sector              | ProcPurchasingProcessInquire\_PSN        | Respond to inquiries about public sector policies that govern the purchasing process.                   |
| Approve purchase agreement                                      | PurchaseAgreementWFMaintain              | Review and approve purchase agreements in a workflow.                                                   |
| Maintain purchase orders                                        | PurchOrderMaintain                       | Document and record purchase orders.                                                                    |
| Maintain purchase requisition consolidation                     | PurchReqConsolidationMaintain            | Maintain the purchase requisition consolidation process.                                                |
| Maintain creation of purchase orders from purchase requisitions | PurchReqOrderFromRequisitionMaintain     | Release purchase orders from purchase requisitions.                                                     |
| Approve purchase requisitions                                   | PurchReqPurchaseRequisitionApprove       | Approve and authorize purchase requisitions.                                                            |
| Maintain all purchase requisitions                              | PurchReqPurchaseRequisitionMaintainAll   | Edit and update purchase requisitions.                                                                  |
| View purchase requisitions on hold                              | PurchReqTableView                        | Open and review purchase requisitions that are on hold.                                                 |
| Maintain request for quotation questionnaire                    | PurchRFQQuestionnaireMaintain            | Edit and update request for quotation (RFQ) questionnaires.                                             |
| Maintain request for quotation                                  | PurchRFQRequestForQuoteMaintain          | Edit and update RFQs.                                                                                   |
| Maintain request for quotation replies                          | PurchRFQRequestForQuoteReplyMaintain     | Edit and update RFQ replies.                                                                            |
| Maintain sealed bids                                            | PurchRFQSealedBids                       | Edit and update sealed bids.                                                                            |
| Inquire about payment status for vendor invoices                | VendInvoice4paymentStatusInquire\_RU     | Respond to inquiries about the payment status for vendor invoices.                                      |
| Maintain vendor invoices for payment                            | VendInvoice4PaymMaintain\_RU             | Edit and update vendor invoices for payment.                                                            |
| Maintain prospective vendor master                              | VendProspectiveVendorMasterMaintain      | Edit and update the prospective vendor master.                                                          |
| Maintain employee-initiated vendor requests                     | VendRequestEmployeeVendorRequestMaintain | Document and record employee-initiated vendor requests.                                                 |
| Inquire into vendor-initiated request status                    | VendRequestVendorInitiateRequestInquire  | Respond to inquiries about the status on vendor-initiated requests.                                     |
| Inquire into unsolicited vendor master                          | VendUnsolicitedVendorMasterInquire       | Respond to inquiries about unsolicited vendor master data.                                              |
| Maintain vendor user requests                                   | VendUserRequestMaintain                  | Maintain and submit vendor user requests.                                                               |
| Maintain vendor master                                          | VendVendorMasterMaintain                 | Edit and update the vendor master.                                                                      |
| Maintain vendor questionnaires                                  | VendVendorQuestionnaireMaintain          | Create and update vendor questionnaire information.                                                     |
| Inquire into workflow performance                               | WorkflowViewWorkflowPerf                 | View reports about the performance of workflows.                                                        |

## What do I do next?
After the users are created, you assign them to roles on the **Assign users to roles** page.

## Additional resources

[Role-based security](../../fin-ops-core/dev-itpro/sysadmin/role-based-security.md)





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
