---
# required metadata

title: Onboard vendors
description: This article describes the process for onboarding new vendors. It explains the actions that are required by various roles during this process.
author: GalynaFedorova
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: VendProspectiveVendorRegistrationRequests, SysUserRequestListPage, VendRequestListPage, VendRequestCompanyProfile
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: gfedorova
ms.search.validFrom: 2017-12-31 
ms.dyn365.ops.version: 7.3
---

# Onboard vendors

[!include [banner](../includes/banner.md)]

---

New vendors can be onboarded and registered as vendors in Microsoft Dynamics 365 Supply Chain Management, based on information that is collected from a person who represents the vendor.

The process consists of the following steps, where various roles perform actions in the system.

1. **Data management OData** – Entity import - The initial request is the prospective vendor registration request. Typically, this request comes from a source such as a customer-hosted website that allows anonymous access. Vendors can sign up by providing basic information, such as the vendor name, justification, organization number, and name and email address of the contact person. The requests are imported via the Data management interface.
2. **Prospective vendor registration request list page** - Based on the information that is provided in the prospective vendor registration request, a procurement professional decides whether the vendor should be onboarded. The procurement professional views the incoming request on the **Prospective vendor registration requests** list page.
3. **User provisioning workflow** - When a procurement professional has verified the information in the incoming request and has decided to continue with the onboarding process, the user request workflow provisions the new user and sends an invitation email to accept the contact person as an authenticated user of Microsoft Dynamics 365.
4. **Vendor registration wizard** - The vendor's contact person signs in by using the new user account. They complete a vendor registration wizard to provide information such as addresses, business information, procurement categories, and questionnaire responses.
5. **Approval workflow** - A vendor request that includes the registration information is created. This vendor request is submitted to a workflow, and is routed for review and approval.
6. **Creation of a vendor master and user role modification** - When the vendor request is approved, a vendor record is created. The user account of the vendor's contact person is either granted permission to vendor collaboration or inactivated.

The following table shows the steps and roles that are involved in the process.

| Role and "process"       | Data management OData – Entity import | Prospective vendor registration request list page | User provisioning workflow | Vendor registration wizard | Approval workflow | Creation of a vendor master and user role modification |
|--------------------------|---|---|---|---|---|---|
| System                   | The request for a new vendor is imported. | | | | | After the vendor request is accepted, the vendor record is created. |
| Procurement professional | | Start the onboarding process. | | | Review and either accept or reject the vendor request. | |
| Administrator            | | | Create a user in Supply Chain Management and Microsoft Azure. | | | |
| Vendor contact person    | | | Send email to the contact person. | Register vendor information. | | |

For a quick demonstration of the vendor onboarding process, watch this short YouTube video about [How to onboard a new vendor in finance and operations](https://www.youtube.com/watch?v=0KUc3AGaTKk).

## Importing the prospective vendor registration request

The prospective vendor registration request is an entity in Supply Chain Management. You can set up the system to import data via this entity. 

The following table shows the information that this entity contains, and that can be imported.

| Field                        | Description |
|------------------------------|-------------|
| Vendor name                  | The name of the vendor. |
| Business justification       | The reason or reasons for the vendor request. |
| Organization number          | An officially known registration number. |
| Line of business             | The line of business that the vendor is in. |
| Contact person's first name  | The first name of the person who will be invited to register vendor information. |
| Contact person's middle name | The middle name of the person who will be invited to register vendor information. |
| Contact person's last name   | The last name of the person who will be invited to register vendor information. |
| Contact person's email       | The email address that will be used to create a new user in Supply Chain Management, and that will be registered in the tenant's Azure Active Directory (Azure AD) account. |
| Submitted date               | The date when the request was created in an external system. |
| Legal entity                 | The legal entity where the vendor is requesting to become a vendor. This value must be a legal entity code that has been registered in Supply Chain Management. If no value is received though the import process, a value from the Procurement and sourcing parameters is applied. |
| Vendor type                  | The vendor can be either an organization or a person. The vendor type determines how the vendor is finally created. |

After the prospective vendor registration request is imported, it appears on the **Prospective vendor registration request** list page. From this list page, a procurement professional can invite the user. A user request for provisioning the user is sent to a workflow.

## Submitting a prospective vendor user request

The purpose of a prospective vendor user request is to provision the person who submitted the initial request, so that they can sign in to Supply Chain Management by using the email account that is provided in the prospective vendor registration request.

The prospective vendor user request is processed by the user request workflow. This workflow communicates through Azure AD B2B collaboration. It creates a user in Supply Chain Management that has the appropriate security settings.

New users that are set up have the following security roles:

- System external user
- Vendor prospective (external)

The new user will receive an email that is generated by the user request workflow. This email invites the user to sign in to the system.

For information about the configuration of the email and the workflow in general, see the description of a user request workflow in [Set up and maintain vendor collaboration](set-up-maintain-vendor-collaboration.md).

## Vendor registration

A prospective vendor user who signs in to Supply Chain Management will see the first page of a vendor registration wizard, where they can enter vendor information.

The wizard reflects the configuration of the vendor request. The country or region where the vendor does business determines what information is requested in the wizard and what information is mandatory.

For more information about the vendor request configuration, see [Set up and maintain vendor collaboration](set-up-maintain-vendor-collaboration.md). The following table gives an overview of the pages in the wizard and the purpose of each page.

| Page                       | Description |
|----------------------------|-------------|
| Country/region             | The country or region determines the vendor request configuration that is applied on the remaining wizard pages. It also determines values in the **Tax state** lookup. |
| Terms and conditions       | This page might be available, depending on the vendor request configuration. If it's available, the user must acknowledge the terms and conditions to continue. |
| Vendor information         | This page contains the vendor name, which is automatically entered from the original prospective vendor registration request. It also contains the organization number, the vendor's telephone number, fax number, and email address, and the vendor's addresses for various purposes. |
| Contact person information | This page contains the contact person's name, which is automatically entered from the original prospect vendor registration request. It also contains the contact person's telephone number and email address, and the contact person's addresses for various purposes. |
| Business information       | This page contains tax registration numbers (for various countries or regions) and the numbers of employees. It also indicates whether the business is minority owned. |
| Procurement categories     | This page contains the procurement categories that the vendor is requesting approval for. The user can select categories in the procurement category hierarchy. You can configure the number of levels that are shown in the hierarchy at **Procurement and sourcing parameters** &gt; **Vendor collaboration**, under **Procurement and sourcing** &gt; **Setup**. |
| Questionnaires             | The wizard might include a set of questionnaires for the vendor. Questionnaires that appear in the wizard are configured either on the vendor request or per procurement category. If questionnaires are configured per procurement category, the procurement categories that the vendor requests approval for determine the questionnaires that appear in the wizard. On the **Procurement categories** page, you can add a questionnaire under the relevant category and set the activity type to **Vendor onboarding**. |

When the prospective vendor user completes the vendor registration wizard, a vendor request is created.

## Manually or automatically submit a vendor request

A vendor request can be created as a draft and manually submitted to a workflow. Alternatively, the vendor request can be automatically submitted to a workflow when the vendor registration wizard is completed. A request can be submitted manually if, for example, a procurement professional wants to assess whether the request should be routed through an approval process before it's submitted to the workflow.

- Select **Procurement and sourcing parameters** &gt; **Vendor collaboration**, and then select **Auto submit prospective vendor registration to workflow** to configure the vendor request so that it's submitted automatically to a workflow when the vendor registration wizard is completed.

## Vendor requests

Vendor requests are available on the **Vendor collaboration user requests** page.

A vendor request contains the information that the prospective vendor user entered in the vendor registration wizard.

The request lets you review the vendor information and decide whether the vendor should become a registered vendor.

The vendor request should be submitted to a workflow, and it should be routed to the relevant reviewers and approvers. For basic information about how to set up workflows, see [Procurement and sourcing workflows](procurement-sourcing-workflows.md).

The following table shows the statuses that vendor requests can have.

| Status                     | Description |
|----------------------------|-------------|
| Draft                      | The vendor request hasn't yet been submitted. |
| Request submitted          | The vendor request has been submitted, and the first step in the workflow is being processed. |
| Pending review             | If there are multiple reviewers in a workflow task, a reviewer can accept the task of reviewing the vendor request and then complete the review. If there is only one reviewer, that participant can complete the review by selecting **Completed** in the workflow action. They don't have to accept the work item first. |
| Request pending approval   | The vendor request has been routed to the participants for approval, and there is an option to request additional information. A request for additional information cause the work item to be routed back to the submitter. The vendor request can also be approved or rejected while it's in this status. |
| Application change request | Additional information has been requested by the approver, and the vendor request has been routed to the person who submitted the vendor request. The submitter can add required information and then resubmit the vendor request. If a vendor request is resubmitted, the status is changed back to **Request pending approval** status. |
| Request approved           | This status is a final state. |
| Request rejected           | This status is a final state. |

## Approving a vendor request

When a vendor request is approved, a vendor account is created, and the status **Approved** appears on both the initial prospective vendor registration request and the vendor request.

Before you approve a vendor request, on the **New vendor** page, on the **General** FastTab, select **Vendor group** to select a vendor group.

If the prospective vendor user should have access to Supply Chain Management as a vendor collaboration user who represents the vendor, set the vendor collaboration access permission to **Yes**. To inactivate the user account that the prospective vendor used to register, set this permission to **No**.

If the vendor collaboration access permission is set to **Yes**, when the vendor request is approved, a request is submitted to modify the user's roles so that the user has the roles that are defined for the **Vendor** type in **External roles**. If this permission is set to **No**, when the vendor request is approved, a request is submitted to inactivate the user. In this case, the workflow to inactivate a user request must be set up.

For a vendor account to be created when the vendor request is approved, the number sequence for creating vendors from vendor requests must be set to **Auto**.

For an overview of the access permissions of a vendor collaboration user, see [Set up and maintain vendor collaboration](set-up-maintain-vendor-collaboration.md).

## Rejecting a vendor request

If a vendor request is rejected, a reason for rejection must be selected in the vendor request.

When a vendor request is rejected, a request is submitted to inactivate the user. In this case, the workflow to inactivate a user request must be set up. For more information, see [Set up and maintain vendor collaboration](set-up-maintain-vendor-collaboration.md).

When a vendor request is rejected, the status **Rejected** appears on both the initial prospective vendor registration request and the vendor request.

## Deleting a prospective vendor registration request in various statuses

The various statuses of a prospective vendor registration request give an overview of the request's progress.

By using the **Delete** action on the prospective vendor registration request, you can clean up and remove the chain of records that has been created, and you can inactivate the user account. The result of the **Delete** action varies, depending on the status of the prospective vendor registration request, as shown in the following table.


|          Status          |                                                                                     Status description                                                                                      |                                                                                                                                                            Result of the Delete action                                                                                                                                                             |
|--------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           New            |                                                                         No actions have been taken on the request.                                                                          |                                                                                                                                              The prospective vendor registration request is deleted.                                                                                                                                               |
|      User requested      | When you select <strong>Invite user</strong>, the status is changed to <strong>User requested</strong>, and a prospective user request is created and submitted to a user request workflow. |                                                                                                          You can't delete a prospective vendor registration request that has this status, because the user request workflow hasn't ended.                                                                                                          |
|       User invited       |                                                               The user request workflow is approved, and the user is created.                                                               |                                                                                                                      A request to inactivate the user is created, and the prospective vendor registration request is deleted.                                                                                                                      |
| Registration in progress |                                                         The new user has signed in and has started the vendor registration wizard.                                                          |                                                                                     A request to inactivate the user is created, and the prospective vendor registration request and the data that was entered in the vendor registration wizard are deleted.                                                                                      |
|  Vendor request created  |                                                                     The vendor registration wizard has been completed.                                                                      | A request to inactivate the user is created, and the prospective vendor registration request, the data that was entered in the vendor registration wizard, and the vendor request are deleted. **NOTE:** <br>You can't use the **Delete** action when the vendor request is in a review process in the workflow. |
|         Approved         |                                                                               The vendor request is approved.                                                                               |                                                                                                   The prospective vendor registration request, the data that was entered in the vendor registration wizard, and the vendor request are deleted.                                                                                                    |
|         Rejected         |                                                                               The vendor request is rejected.                                                                               |                                                                                                   The prospective vendor registration request, the data that was entered in the vendor registration wizard, and the vendor request are deleted.                                                                                                    |



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
