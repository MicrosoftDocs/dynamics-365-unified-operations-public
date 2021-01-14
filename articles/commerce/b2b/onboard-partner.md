---
# required metadata

title: Manage business partner users on B2B e-commerce sites
description: This topic describes how administrators can add, edit, and delete business partner users from B2B e-commerce sites.
author: josaw1
manager: AnnBe
ms.date: 01/14/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 
# optional metadata
ms.search.form:  RetailOperations
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: v-chgri
#ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: retail
ms.author: josaw
ms.search.validFrom: 2021-01-31
ms.dyn365.ops.version: 10.0.14

---

# Manage business partner users on B2B e-commerce sites 

[!include [banner](../../includes/banner.md)]

This topic describes how administrators can add, edit, and delete business partner users from B2B e-commerce sites.

Business-to-business (B2B) e-commerce websites require that organizations register to become business partners. Once an organization submits registration details to a B2B e-commerce site, it goes through a qualification process. Upon successful qualification, the organization is onboarded as a business partner. 

Once an organization is onboarded as a business partner, the organization user who initiates the request to become a business partner is identified as an administrator user who is provided with the privileges to onboard additional authorized users of the B2B e-commerce portal. These authorized users can then place orders on behalf of the business partner. Business partner users are able to see order details and history of orders that they have created. The business partner administrator is able to see the order details and history of all orders business partner users have created. The same is true for functions such as the request of documents like account statements and aged debtors listing reports.

<!--The below section covers details on how Business partners are on-boarded to the D365 Commerce B2B website and how the Business partner organization is represented in Commerce headquarters.-->

## Enable the B2B capabilities feature in Commerce headquarters

The **Enable the use of B2B eCommerce capabilities** feature in Commerce headquarters allows organizations to onboard business partners and define administrator users. This feature also allows administrators to create and manage business partner users and teams and assign specific roles to them, and allows business partner users to create order templates and use existing orders to reorder products.

To enable the B2B capabilities feature in Commerce headquarters, follow these steps.

1. Go to **Workspaces \> Feature Management**.
1. Select the **All** tab.
1. Filter on the **Module field** using the term "Retail and commerce".
1. Find and enable the feature named **Enable the use of B2B eCommerce capabilities**.

## Create a number sequence and add it to Commerce shared parameters

Number sequences are used to generate readable, unique identifiers for master data records and transaction records that require identifiers. For more information on number sequences, see [Number sequences overview](https://docs.microsoft.com/dynamics365/fin-ops-core/fin-ops/organization-administration/number-sequence-overview).

To create a number sequence and add it to Commerce shared parameters in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Headquarters setup \> Number sequences \> Number sequences** and create a new number sequence.
1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters** and add the new number sequence to the **Customer hierarchy ID** reference.

## Set up the administrator user for a new business partner 

Potential business partners can initiate the onboarding process to a B2B e-commerce website by submitting an onboarding request via a link on the B2B site. After selecting the link, the business partner can provide the details required for the onboarding and sign up. After submitting the request, the user will see a submission confirmation screen. If the submission is approved, the organization user who initiated the onboarding request will become the business partner administrator user.

To approve and set up a business partner administrator in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce IT \> Distribution Schedule**.
1. Execute the **P-0001** job to pull all business partner onboarding requests into headquarters.
1. After the P-0001 job runs successfully, go to **Retail and Commerce IT \> Customer** and execute the **Synchronize customers and business partners from async mode** job. After this job runs successfully, the onboarding requests will be created as prospects records in Commerce headquarters and the **Type ID** of the prospect records will be set to **B2B prospect**.
1. Go to **Customers \> All prospects** and open the prospects form. 
1. Select the prospect record for the new business partner to open the prospect details form.
1. Select the **General \> Convert \> Approve / Reject**  tab to approve or reject the onboarding request. When a confirmation dialog box appears that asks if you want to continue with the process, continue the process and approve the request. An email will be sent to the requestor's email address confirming that they have been to be a business partner.
1. Once you approve the request, the **Status** on the prospect record is set to **Approved**. Also, two new customer records are created in the system: one **Type Organization** customer record for the business partner organization and a **Type Person** customer record for the requestor. A customer hierarchy record for the business partner is also created. <!--(Please refer to the Org modeling of B2B customer section in this document for more information)-->
1. Go to **Retail and Commerce IT \> Distribution Schedule** and execute the **1010 Customers** job to push the newly created customers and customer hierarchy records to the channel database (channel DB). Once the request is approved and the customer and customer hierarchy records are synchronized to the channel DB, the requestor will be able to sign in to the B2B e-commerce website using the email address that was provided at the time of submitting the request. During the first sign-in session, the requestor will be prompted to set a password for the requestor administrator account.

## Onboard additional business partner users

The business partner administrator user can onboard additional business partner users to the B2B e-commerce website as needed.

To onboard additional business partner users to the B2B e-commerce site, follow these steps.

1. Sign in to the B2B e-commerce site as an administrator.
1. Go to **My Account \> Organization users \> View details** and select **Add a user**.
1. Fill in the required information and then select **Save**. The status of the newly-added user will be set to **Pending**. After the **P-0001** job and the **Synchronize customers and business partners from async mode** jobs have been run, a **Type Person** customer record is created for the new user in Commerce headquarters. This customer record is also associated with the relevant business partner's customer hierarchy record. An email is also sent to the new user's email address notifying them that they have been added as a user of the business partner organization and can now sign in to the B2B e-commerce site.
1. Run the **1010 Customer** job to synchronize the new business partner user to the channel DB. Once the customer record is synchronized, the status of the user on the B2B e-commerce website is set to **Active** and the new user will be able to sign in to the B2B e-commerce site using their email address. During the first sign-in session, the new user will be prompted to set a password.

## Edit user details

To edit business partner user details, follow these steps.

1. Sign in to the B2B e-commerce site as an administrator.
1. Go to **My Account \> Organization users \> View details**, select **Edit** (pencil symbol), make the required changes, and then select **Save**. The changes will take effect once the **P-0001**, **Synchronize customers and business partners from async mode**, and **1010 Customer** jobs have been run.

## Remove a user

An administrator can remove existing users of a business partner organization from the list of users who can access the B2B e-commerce site as needed. 

To remove a business partner user, follow these steps.

1. Sign in to the B2B e-commerce site as an administrator.
1. Go to **My Account \> Organization users \> View details** and select **Remove** ("X" symbol ). When a confirmation dialog box appears, confirm the user removal. The changes will take effect once the **P-0001**, **Synchronize customers and business partners from async mode**, and **1010 Customer** jobs have been run.

> [!NOTE]
> Removing the user from the list of users who can access the B2B e-commerce site will remove the corresponding customer record from the business partners customer hierarchy record. However, the customer record itself will not be deleted from Commerce headquarters.

## Onboard business partner and users from Commerce headquarters

Administrators can choose to onboard business partners and users directly from Commerce headquarters.

To onboard business partners and users in Commerce headquarters, follow these steps.

1. Create a **Type Organization** customer record for the business partner organization.
1. Create **Type Person** customer records for business partner users. Ensure that all customers have a primary email address specified.
1. For **Type Person** customer records that need to be designated as administrator users of the business partner organization, under the **Retail** fast tab of the customer record, select **Yes** for **B2B administrator**.
1. Create a customer hierarchy ID. For **Name**, enter a name.
1. For **Organization**, enter the business partner organization customer.
1. Select **Add**, and then select a customer from the **Name** drop-down menu. 
1. Repeat the process to add additional customers to the hierarchy.

## Call outs

1. All jobs referenced in this topic can be configured to run on a schedule in a batch format. It is expected that customers configure them accordingly.
1. Currently only one user/customer record can be designated as an administrator user and the role can only be changed in Commerce headquarters. Self-serve capabilities for business partners to designate multiple administrators or change administrators from B2B e-commerce sites is not supported.
<!--1. The modules and labels of the different fields referenced in the screenshots for e-commerce are only for illustration purposes. Customers have complete control on the placement of the B2B related modules and the labels.-->
1. While spending limits can be defined for users, the enforcement of spending limits during the order entry process has not yet been implemented.
1. All business logics and validations for a user's experience on a B2B e-commerce site is based on the configuration of the corresponding customer record mapped to the user in Commerce headquarters.

## Additional resources

[Number sequences overview](https://docs.microsoft.com/dynamics365/fin-ops-core/fin-ops/organization-administration/number-sequence-overview)

