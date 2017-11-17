---
# required metadata

title: Onboarding vendors
description: The process to onboard new vendors and actions required by different roles.
author: mkirknel
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Application User
# ms.devlang: 
# ms.reviewer: bis
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2017-12-31 
ms.dyn365.ops.version: AX 7.3
---

# Onboarding vendors
[!include[banner](../includes/banner.md)]
---

New vendors can be onboarded and registered as vendors in Microsoft Dynamics 365
for Finance and Operations based on information collected from a person
representing the vendor.

The process is described in steps where different roles take actions in the
system.

Step 1  
The initial request is the prospective vendor registration request and it
typically comes from a source such as a customer-hosted website that allows
anonymous access. Vendors can sign up by providing basic information such as: vendor name, justification, organization number, contact person name and email. The requests are imported via the data management interface.

Step 2

Based on the information provided in the prospective vendor registration request, a procurement professional decides whether to onboard the vendor. The procurement professional views the incoming request in the list page **Prospective vendor registration requests** in Microsoft Dynamics 365.

Step 3

Based on the information provided in the prospective vendor registration request, a procurement professional decides whether to onboard the vendor. The procurement professional views the incoming request in the list page Prospective vendor registration requests in Microsoft Dynamics 365.

Step 4  
The vendors contact person logs into Microsoft Dynamics 365 with the new user
account and uses a registration wizard to provide information such as addresses,
business information, procurement categories, and questionnaire responses.

Step 5  
A **vendor request** is created with the registration information and the vendor
request is submitted to workflow and routed for review and approval.

Step 6  
On approval, a vendor record is created, and the user account of the vendor’s
contact person is granted permission to vendor collaboration or is inactivated.

The schema below illustrates the steps and the acting role involved in the
process.

| Role and ”process”       | Step – 1 Data Management Odata - Entities import | Step -2 Prospective vendor registration request List page | Step – 3 User provisioning workflow | Step - 4 Registration wizard | Step – 5 Vendor request: Request submitted to workflow | Step - 6 Creation of Vendor master & User role modification |
|--------------------------|--------------------------------------------------|-----------------------------------------------------------|-------------------------------------|------------------------------|--------------------------------------------------------|-------------------------------------------------------------|
| System                   | Request for new vendor imported                  |                                                           |                                     |                              |                                                        | Vendor is created on acceptance of vendor request           |
| Procurement professional |                                                  | Starts the onboarding process                             |                                     |                              | Reviews and accepts/rejects the vendor                    |                                                             |
| Administrator            |                                                  |                                                           | Creates user in Dynamics 365 and Azure       |                              |                                                        |                                                             |
| Vendor contact person    |                                                  |                                                           | Sends mail to the contact person    | Registers vendor information |                                                        |                                                             |

Importing the prospective vendor registration request
-----------------------------------------------------

The **prospective vendor registration request** is an entity in Microsoft
Dynamics 365. You can set up the system to import data via this entity. *(TODO:
Refer to the Blog post that Gaurav is creating)*

The entity contains the following information for import:

| **Field**                    | **Description**                                                                                                                                                                                                                                                            |
|------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Vendor name                  | Name of the vendor                                                                                                                                                                                                                                                         |
| Business justification       | Reason or reasons for the vendor request.                                                                                                                                                                                                                                  |
| Organization number          | An officially known registration number.                                                                                                                                                                                                                                   |
| Line of business             | The line of business that the vendor is in.                                                                                                                                                                                                                                |
| Contact person’s first name  | The name of the person that will be invited to register vendor information.                                                                                                                                                                                                |
| Contact person’s middle name |                                                                                                                                                                                                                                                                            |
| Contact person’s last name   |                                                                                                                                                                                                                                                                            |
| Contact person’s email       | The email that will be used to create a new user in Microsoft Dynamics 365 and which will be registered in the tenant’s Azure active directory account.                                                                                                                    |
| Submitted date               | The date that the request was created in an external system.                                                                                                                                                                                                               |
| Legal entity                 | The legal entity where the vendor is requesting to become a vendor. This value must be a legal entity code that has been registered in Microsoft Dynamics 365. If no value is received though the import, a value from the Procurement and sourcing parameters is applied. |
| Vendor type                | This can be an organization or a person and will determine how the vendor is finally created.                                                                                                                                                                            |

When the prospective vendor registration request is imported, it will be visible
in the list page **Prospective vendor registration request**. From the list
page, a procurement professional can invite the user. A user request for
provisioning the user is sent to a workflow.

Submitting a prospective vendor user request
--------------------------------------------

The purpose of a prospective user request is to provision the person that has
raised the initial request to be able to log in to Dynamics 365 with the email
account that is provided in the prospective vendor registration request.

The user request is processed by the user request workflow. The workflow
communicates through Azure active directory B2B and creates the user in Dynamics
365 with the appropriate security settings.

A new user will be set up with the following security roles:

-   System external user

-   Vendor prospective (external)

The new user will receive an email generated from the user request workflow to
invite the user to log on to the system.

For information about the configuration of the email and the workflow in
general, see the description of a user request workflow in [Set up and maintain vendor collaboration](set-up-maintain-vendor-collaboration.md).

Vendor registration
-------------------

The prospective vendor user who logs into Microsoft Dynamics 365 will land on
the first page of a wizard where vendor information can be entered.

The wizard reflects the vendor request configuration and the country/region
where the vendor is doing business determines what information is requested in
the wizard and what information is mandatory.

For more information about the vendor request configuration, see [Vendor request configurations](vendor-request-configuration.md).

Below is an overview of the pages in the wizard and their purpose, the
description provides some examples of contents.

| Page                       | Description                                                                                                                                                                                                                                                                                   |
|----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Country/region             | The country/region determines the vendor request configuration that is applied on the remaining wizard pages. This also determines values in the Tax state look up.                                                                                                                           |
| Terms and conditions       | This page will be available depending on the configuration. It may request an acknowledgement from the user to proceed.                                                                                                                                                                       |
| Vendor information         | Contains the vendor name that is defaulted from the original prospective vendor registration request, the organization number, the vendor's phone number, fax, and email, and the vendor's adresses for different purposes.                                                                                                                                                                                         |
| Contact person information | Contains the contact person’s name, defaulted from the original prospect vendor registration request, the contact person’s phone number and email address, and the contact person's adresses for different purposes.                                                                                                                                                                                                                                                                                                            |      
| Business information       | Contains tax registration numbers (for different countries), minority owned, and numbers of employees.                                                                                                                                                                                                                                                                                     |
| Procurement categories     | The procurement categories that the vendor is requesting to be approved for. The procurement category hierarchy is available to select from. The number of levels of the hierarchy that is displayed can be configured in the **Procurement and sourcing parameters / Vendor collaboration.** |
| Questionnaires             | Depending on the configuration, the prospective vendor user may have to respond to a set of questionnaires. The vendor request configuration can be configured to add a questionnaire to the page. Questionnaires can also be configured per procurement category as required in the wizard. So, questionnaires will appear depending on which procurement categories that were selected on the previous pages. You can add a questionnaire in the **Procurement categories** page under the relevant category and set the activity type to **Vendor onboarding**.                                                                                                                                                                                  |

When the prospective vendor user finalizes the wizard, a vendor request is
created.

Submit a vendor request manually or automatically

A vendor request can be created as a draft and manually submitted to workflow or
it can be submitted to workflow automatically when the vendor registration
wizard is finalized. A request can, for example, be submitted manually if a
procurement professional wants to assess if the request should be routed through
an approval process before it is submitted to the workflow.  
Click **Procurement and sourcing parameters/Vendor collaboration** and select
**Auto submit prospective vendor registration to workflow** to configure the
vendor request to be submitted automatically to workflow when the vendor
registration wizard finalizes.

Vendor request
--------------

Vendor requests are available on the **Vendor request** page.

A vendor request contains the information that was provided by the prospective
vendor user in the registration wizard.

The request allows you to review the vendor information and decide whether the
vendor is to become a registered vendor in Microsoft Dynamics 365.

The vendor request should be submitted to workflow, and be routed to the
relevant reviewers and approvers. Basic information about setting up workflows
can be found in [Procurement and sourcing workflows](procurement-sourcing-workflows.md) and [Workflow overview](overview-workflow-system.md)

The vendor request can have the following statuses:

| Status                     | Description                                                                                                                                                                                                                                                                                                |
|----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Draft                      | The vendor request is not submitted yet.                                                                                                                                                                                                                                                                   |
| Request submitted          | The request is submitted, and the workflow is processing the first step in the workflow.                                                                                                                                                                                                                   |
| Pending review             | If there are multiple reviewers in a workflow task, a reviewer can **Accept** the task of reviewing and complete the review. If there are only one reviewer, the participant can go ahead and complete the review by clicking **Completed** in the workflow action without having to accept the work item. |
| Request pending approval   | The request is routed to the participants for approval and there is an option to request additional information. This will route the work item back to the submitter. The vendor request can also be approved or rejected at this state.                                                                   |
| Application change request | Additional information has been requested by the approver and the vendor request is routed to the participant who submitted the vendor request, who can add needed information and re-submit. If resubmitted, a vendor request returns to the state Request pending approval                               |
| Request Approved           | This is a final state.                                                                                                                                                                                                                                                                                     |
| Request rejected           | This is a final state.                                                                                                                                                                                                                                                                                     |

### Approving a vendor request

When a vendor request gets approved, a vendor account is created, and the status
**Approved** will be visible on the initial prospective vendor registration
request as well as on the vendor request.

Before you approve a vendor request, in the **New vendor** page, on the
**General** FastTab, click **Vendor group** to select a vendor group.

If the prospective vendor user should have access to Microsoft Dynamics 365 as a
vendor collaboration user representing the vendor, set the vendor collaboration
access permission to **Yes**. To inactivate the user account that was used by
the prospective vendor to register, set the permission to **No**.

When the vendor collaboration access is set to YES, approval of the vendor
request will submit a request to modify the user’s roles so that the user gets
the roles defined in **External roles** for the type=vendor.

When the vendor collaboration access is set to NO, approval of the vendor
request will submit a request to inactivate the user. Inactivating the vendor
account requires that the workflow to inactivate a user request is set up.

Note that to create a vendor account on approval, the number sequence for
creating vendors from vendor requests must be set to auto.

For an overview of the access permissions of a vendor collaboration user, see
https://docs.microsoft.com/en-us/dynamics365/unified-operations/supply-chain/procurement/set-up-maintain-vendor-collaboration.

Rejecting a vendor request
--------------------------

When a vendor request is rejected, it requires a reason for rejection which must
be selected in the vendor request.

Rejection of a vendor request will submit a request for inactivating the user.
Inactivating a user requires that the workflow to inactivate a user request
workflow is set up. For more information, see
<https://docs.microsoft.com/en-us/dynamics365/unified-operations/supply-chain/procurement/set-up-maintain-vendor-collaboration>.

When a vendor request is rejected, the status **Rejected** will be visible on
the initial prospective vendor registration request as well as on the vendor
request.

Deleting a prospective vendor registration request in different statuses
========================================================================

The prospective vendor registration request has different statuses that provide
an overview of how it is progressing.

By using the **Delete** action on the prospective vendor registration request,
you can clean up and remove the chain of records that have been created, and you
can inactivate the user account. The result of using the **Delete** action
varies depending on the status of the prospective vendor registration request.

| Status                       | Status description                                                                                                                                                | Result of using the **Delete** action                                                                                                                                                                                                                               |
|------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **New**                      | No actions have been taken on the request.                                                                                                                        | The prospective vendor registration request will be deleted.                                                                                                                                                                                                        |
| **User requested**           | When you click **Invite user,** the status changes to **User requested**, and a **Prospective user request** is created and submitted to a user request workflow. | Deleting a prospective vendor registration request with this status is not allowed because the user request workflow has not ended. The process can be halted by recalling and deleting the request. (Is state then set back to NEW ?)                              |
| **User invited**             | The user request workflow is approved, and the user is created.                                                                                                   | Creates a request to inactivate the user and deletes the prospective vendor registration request.                                                                                                                                                                   |
| **Registration in progress** | The new user has logged in and started the vendor registration wizard.                                                                                            | Creates a request to inactivate the user, deletes the prospective vendor registration request and deletes the data entered into the registration wizard.                                                                                                            |
| **Vendor request created**   | The vendor registration wizard is finalized.                                                                                                                      | Creates a request to inactivate the user, deletes the prospective vendor registration request and the data in the registration wizard, and deletes the vendor request. Note: Delete is not possible when the vendor request is in a review process in the workflow. |
| **Approved**                 | The vendor request is approved.                                                                                                                                   | Deletes the prospective vendor registration request and the data entered into the registration wizard, and deletes the vendor request.                                                                                                                              |
| **Rejected**                 | The vendor request is rejected.                                                                                                                                   | Deletes the prospective vendor registration request and the data entered into the registration wizard, and deletes the vendor request.                                                                                                                              |
