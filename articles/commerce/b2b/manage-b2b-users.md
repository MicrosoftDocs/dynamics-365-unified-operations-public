---
title: Manage business partner users on B2B e-commerce websites
description: This article describes how to add, delete, and edit business partner users on Microsoft Dynamics 365 Commerce business-to-business (B2B) e-commerce websites and in Commerce headquarters.
author: BrianShook
ms.date: 11/02/2023
ms.topic: how-to
audience: Application User
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2021-01-31
ms.custom: 
  - bap-template
---

# Manage business partner users on B2B e-commerce websites

[!include [banner](../../includes/banner.md)]

This article describes how to add, delete, and edit business partner users on Microsoft Dynamics 365 Commerce business-to-business (B2B) e-commerce websites and in Commerce headquarters.

> [!NOTE]
> - The [Manage B2B business partners using customer hierarchies](partners-customer-hierarchies.md) article is a prerequisite for this document.
> - Ensure that you initialize the document types entity in Commerce headquarters by opening the **Document types** form at **Organization administration \> Document management \> Document types**.

B2B e-commerce websites require that organizations register to become business partners. After an organization submits registration details to a B2B e-commerce website, the registration request goes through a qualification process. If the organization is successfully qualified, it's onboarded as a business partner.

After an organization is onboarded as a business partner, the organization user who initiated the request to become a business partner is identified as the administrator user and is granted privileges to onboard additional authorized users of the B2B e-commerce website. These authorized users can then place orders on behalf of the business partner.

## Set up the administrator user for a new business partner

Potential business partners can initiate the onboarding process to a B2B e-commerce website by submitting an onboarding request via a link on the B2B website. They can then use the customizable form to provide the details that are required for onboarding and sign-up. After the request is submitted, a submission confirmation page appears. If the submission is approved, the company that the request was submitted for becomes a business partner, and the requestor (the user who initiated the onboarding request) becomes the administrator user for the business partner.

To approve a business partner request in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce IT \> Distribution schedule**.
1. Run the **P-0001** job to pull all business partner onboarding requests into Commerce headquarters.
1. After the **P-0001** job has successfully run, go to **Retail and Commerce IT \> Customer**, and run the **Synchronize customers and channel requests** job. After this job has successfully run, the onboarding requests are created as prospects of the **B2B prospect** type in Commerce headquarters. 
1. Go to **Customers \> All prospects**, and select the new business partner's prospect record to open the prospect details page.
1. On the **General** tab, select **Convert \> Approve/Reject** to approve the onboarding request. When the confirmation message appears, confirm that you want to continue with the process, and then approve the request. The approval changes the **Status** field of the prospect record to **Approved**. An email is then sent to the requestor's email address to confirm that their organization has been approved as a business partner. A customer hierarchy is also created, where the requester is added as an administrator for the business partner.

    > [!NOTE]
    > Currently, the confirmation email is sent immediately on approval. However, future Commerce functionality will let the administrator manually trigger the emails.

1. Go to **Retail and Commerce IT \> Distribution schedule**, and run the **1010 (Customers)** job to push the new customer and customer hierarchy records to the channel database.

> [!NOTE]
> To ensure that the new customer records are sent to the channel database, at least one of the address books that are associated with the customer should be included in the customer address book that is associated with the online store. You can automate this process by configuring the address book on the default customer of the online store so that the system copies the address book value to every new customer.

After the customer hierarchy records are synchronized to the channel database, the requestor can sign in to the B2B e-commerce website by using the email address that they provided when they submitted the onboarding request. Users can use the sign-up flow to define the password for their account. For information about how to enable the Microsoft Entra B2C identity provider record to be linked to the B2B customer record that was created on prospect approval, see [Enable automatic linking](../identity-record-linking.md).

## Notify B2B prospects when they are approved or rejected

When you approve or reject a B2B prospect onboarding request, an email notification can automatically be sent to the prospect.

To set up email notifications in Commerce headquarters for events of the **B2B prospect approved** or **B2B prospect rejected** notification type, follow these steps.

1. Create email templates for emails that will be sent to prospects when either the **B2B prospect approved** or **B2B prospect rejected** notification type is triggered. For information about the placeholders that these notification types support, see [Notification types](../email-templates-transactions.md#notification-types). For information about how to create email templates, see [Create an email template](../email-templates-transactions.md#create-an-email-template).
1. Add the **B2B prospect approved** and **B2B prospect rejected** notification types to your email notification profile, and then map them to the email templates that you created. For more information about notification profiles, see [Set up an email notification profile](../email-notification-profiles.md).

## Onboard additional business partner users

The business partner administrator user can onboard additional business partner users to the B2B e-commerce website as required.

To onboard additional business partner users to a B2B e-commerce website, follow these steps.

1. Sign in to the B2B e-commerce website as an administrator.
1. Go to **My Account \> Organization users \> View details**, and select **Add a user**.
1. Enter the required information, and then select **Save**. The status of the new user is set to **Pending**.

After the **P-0001** and **Synchronize customers and channel requests** jobs have been run, a customer record of the **Person** type is created for the new user in Commerce headquarters. This customer record is also associated with the relevant business partner's customer hierarchy record. Additionally, an email is sent to the new user's email address to notify them that they have been added as a user of the business partner organization and can now sign in to the B2B e-commerce website.

Next, run the **1010 (Customers)** job to synchronize the new business partner user to the channel database.

After the customer record is synchronized, the status of the user on the B2B e-commerce website is set to **Active**, and the new user can sign in to the B2B e-commerce website by using their email address. Users can use the sign-up flow to define the password for their account. For information about how to enable the Microsoft Entra B2C identity provider record to be linked to the B2B customer record that was created in Commerce headquarters, see [Enable automatic linking](/dynamics365/commerce/identity-record-linking).

## Edit business partner user details

To edit the details of business partner users, follow these steps.

1. Sign in to the B2B e-commerce website as an administrator.
1. Go to **My Account \> Organization users \> View details**, select the **Edit** button (pencil symbol), make the required changes, and then select **Save**. The changes take effect only after the **P-0001**, **Synchronize customers and channel requests**, and **1010 (Customers)** jobs have been run.

## Remove a business partner user

As required, an administrator can remove existing users of a business partner organization from the list of users who can access the B2B e-commerce website.
To remove a business partner user, follow these steps.
- Sign in to the B2B e-commerce website as an administrator.
- Go to **My Account > Organization users \> View details**, and select the **Remove** button ("X" symbol). When a confirmation message appears, confirm that you want to remove the user. The change takes effect only after the **P-0001**, **Synchronize customers and channel requests**, and **1010 (Customers)** jobs have been run.

> [!NOTE]
> When you remove a user from the list of users who can access the B2B e-commerce website, the corresponding customer record is removed from the business partner's customer hierarchy record. However, the customer record itself isn't deleted from Commerce headquarters, and the customer can still sign in to the B2B site.

## Onboard existing customers as business partners on the B2B e-commerce website

Administrators can onboard business partners and users directly in Commerce headquarters. This capability is useful for onboarding your existing business partners on the B2B e-commerce website.

To onboard business partners and users in Commerce headquarters, follow these steps.

1. Create or select a customer of the **Organization** type to add as a business partner.
1. Create or select a customer of the **Person** type to add as an administrator or user for the business partner. Ensure that primary email addresses are associated with the customers. These email addresses are used to sign in to the website. 

    > [!NOTE]
    > The system must be able to find a unique customer record for users who should be able to sign in to the website. If the system finds more than one customer that has the same primary email address in the legal entity, the user won't be able to sign in to the website.

1. Create a customer hierarchy ID.
1. In the **Name** field, enter a name.
1. In the **Organization** field, enter the business partner organization customer.
1. On the **Hierarchy** FastTab, select **Add**.
1. In the **Name** field, select a customer of the **Person** type.
1. Select the **Admin** role for the customer that should be designated as the administrator.
1. Repeat this process to add more customers to the hierarchy.

## Additional information

- All the jobs that are mentioned in this article can be configured to run on a schedule in a batch format. The expectation is that business partners will configure batch jobs as required.
- Currently, only one user/customer record can be designated as an administrator user, and that role can be changed only in Commerce headquarters. There is no support for self-service capabilities that let business partners to designate multiple administrators or change administrators from B2B e-commerce websites.
- Although spending limits can be defined for users, enforcement of spending limits during the order entry process hasn't yet been implemented.
- All business logic and validation for a user's experience on a B2B e-commerce website are based on the configuration of the customer record that is mapped to the user in Commerce headquarters.

## Additional resources

[Set up a B2B e-commerce site](set-up-b2b-site.md)

[Manage B2B business partners using customer hierarchies](partners-customer-hierarchies.md)

[Configure the customer account payment method for B2B e-commerce sites](payment-method.md)

[Set product quantity limits for B2B e-commerce sites](quantity-limits.md)

[Number sequences overview](../../fin-ops-core/fin-ops/organization-administration/number-sequence-overview.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
