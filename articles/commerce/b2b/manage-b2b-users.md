---
# required metadata

title: Manage business partner users on B2B e-commerce websites
description: This topic describes how the users of the business partner can be added, edited, and deleted from the business-to-business (B2B) e-commerce website and from the Commerce headquarters.
author: josaw1
ms.date: 10/26/2021
ms.topic: article
ms.prod: 
ms.technology:

# optional metadata

ms.search.form:
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: v-chgri
#ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: retail
ms.author: brshoo
ms.search.validFrom: 2021-01-31
ms.dyn365.ops.version: 10.0.14

---

# Manage business partner users on B2B e-commerce websites

[!include [banner](../../includes/banner.md)]

This topic describes how the users of the business partner can be added, edited, and deleted from the business-to-business (B2B) e-commerce website and from the Commerce headquarters.

> [!NOTE]
> The article on customer hierarchies is a prerequisite for this document. You can find the link for customer hierarchies document here: [Customer hierarchy for B2B sites](https://docs.microsoft.com/en-us/dynamics365/commerce/b2b/org-model)


B2B e-commerce websites require that organizations register to become business partners. After an organization submits registration details to a B2B e-commerce website, it goes through a qualification process. If the organization is successfully qualified, it's onboarded as a business partner.
After an organization is onboarded as a business partner, the organization user who initiated the request to become a business partner is identified as the administrator user and is granted privileges to onboard additional authorized users of the B2B e-commerce website. These authorized users can then place orders on behalf of the business partner.

## Set up the administrator user for a new business partner
Potential business partners can initiate the onboarding process to a B2B e-commerce website by submitting an onboarding request via a link on the website. Using the customizable form, the potential business partners can provide the details that are required for onboarding and sign-up. After the request is submitted, a submission confirmation page appears. If the submission is approved, the company for which the request was raised becomes a business partner and the requestor (that is, the user who initiated the onboarding request) becomes the administrator user for the business partner.
To approve the business partner request in Commerce headquarters, follow these steps.
- Go to **Retail and Commerce IT** > **Distribution schedule**.
- Run the **P-0001** job to pull all business partner onboarding requests into Commerce headquarters.
- After the **P-0001** job has successfully run, go to **Retail and Commerce IT** > **Customer**, and run the **Synchronize customers and channel requests** job. After this job has successfully run, the onboarding requests are created as prospects of type B2B prospect in Commerce headquarters. 
- Go to **Customers** > **All prospects**, and open the prospects page.
- Select the prospect record for the new business partner to open the prospect details page.
- On the General tab, select **Convert** > **Approve/Reject** to approve or reject the onboarding request. When a confirmation message appears, confirm that you want to continue with the process, and approve the request. The approval changes the Status field of the prospect record to Approved. An email is then sent to the requestor's email address to confirm that their organization has been approved as a business partner.

    > [!NOTE]
    > Currently, the email is sent immediately on approval, but we are working on allowing the admin to trigger the emails manually as well.

- As mentioned in the article [Customer hierarchy for B2B site](https://docs.microsoft.com/en-us/dynamics365/commerce/b2b/org-model) on prospect approval, a customer hierarchy get created where the requester is added as an admin for the business partner.
- Go to Retail and Commerce IT > Distribution schedule, and run the 1010 (Customers) job to push the newly created customers and the customer hierarchy records to the channel database.

After the customer hierarchy records are synced to the channel database, the requestor can sign in to the B2B e-commerce website by using the email address that they provided when they submitted the onboarding request. Users can use the sign-up flow to define the password for their account. To enable the identity provider (Azure AD B2C) record to be linked to the B2B customer record that was created on prospect approval, follow the instructions in [Enable automatic linking](https://docs.microsoft.com/en-us/dynamics365/commerce/identity-record-linking).

## Notify B2B prospects when they are approved or rejected
When you approve or reject a B2B prospect onboarding request, you can automatically send an email notification to the prospect.
To set up email notifications in Commerce headquarters for events of the B2B prospect approved or B2B prospect rejected notification type, follow these steps.
- Create email templates for emails that will be sent to prospects when the B2B prospect approved or B2B prospect rejected notification type is triggered. For information about the placeholders that the B2B prospect approved and B2B prospect rejected notification types support, refer this doc [Notification types](https://docs.microsoft.com/en-us/dynamics365/commerce/email-templates-transactions#notification-types). For information about how to create email templates, refer this doc [Create an email template](https://docs.microsoft.com/en-us/dynamics365/commerce/email-templates-transactions#create-an-email-template).
- Add the B2B prospect approved and B2B prospect rejected notification types to your email notification profile, and map them to the email templates that you created. For more information about notification profiles, see [Setup an email notification profile](https://docs.microsoft.com/en-us/dynamics365/commerce/email-notification-profiles).

## Onboard additional business partner users
The business partner administrator user can onboard additional business partner users to the B2B e-commerce website as required.
To onboard additional business partner users to a B2B e-commerce website, follow these steps.
- Sign in to the B2B e-commerce website as an administrator.
- Go to **My Account** > **Organization users** > **View details**, and select Add a user.
- Enter the required information, and then select Save. The status of the new user is set to Pending.

After the **P-0001** and **Synchronize customers and channel requests** jobs are run, a type Person customer record for the new user is created in Commerce headquarters. This customer record is also associated with the relevant business partner's customer hierarchy record. Additionally, an email is sent to the new user's email address to notify them that they have been added as a user of the business partner organization and can now sign in to the B2B e-commerce website.
- Run the **1010 (Customers) job** to sync the new business partner user to the channel database.
After the customer record is synced, the status of the user on the B2B e-commerce website is set to Active, and the new user can sign in to the B2B e-commerce website by using their email address. Users can use the sign-up flow to define the password for their account. To enable the identity provider (Azure AD B2C) record to be linked to the B2B customer record that was created in commerce headquarters, follow the instructions in [Enable automatic linking](https://docs.microsoft.com/en-us/dynamics365/commerce/identity-record-linking).

## Edit business partner user details
To edit the details of business partner users, follow these steps.
- Sign in to the B2B e-commerce website as an administrator.
- Go to **My Account** > **Organization users** > **View details**, select the Edit button (pencil symbol), make the required changes, and then select Save. The changes take effect only after the **P-0001**, **Synchronize customers and channel requests**, and **1010 (Customers)** jobs have been run.

## Remove a business partner user
As required, an administrator can remove existing users of a business partner organization from the list of users who can access the B2B e-commerce website.
To remove a business partner user, follow these steps.
- Sign in to the B2B e-commerce website as an administrator.
- Go to **My Account** > **Organization users** > **View details**, and select the **Remove button** ("X" symbol). When a confirmation message appears, confirm that you want to remove the user. The change takes effect only after the **P-0001**, **Synchronize customers and channel requests**, and **1010 (Customers)** jobs have been run.

> [!NOTE]
> When you remove a user from the list of users who can access the B2B e-commerce website, the corresponding customer record is removed from the business partner's customer hierarchy record. However, the customer record itself isn't deleted from Commerce headquarters.

## Onboard existing customers as business partners on the B2B ecommerce websites
Administrators can onboard business partners and users directly in Commerce headquarters. This is useful for onboarding your existing business partners on the B2B ecommerce website
To onboard business partners and users in Commerce headquarters, follow these steps.
- Create or select a customer of type Organization that you want to add as a business partner.
- Create or select a customer of type Person that you want to add as an admin or a user for the  business partner. Ensure that these customers have a primary email address associated to them. This email is used for logging on the website. 
    > [!Note]
    > If the system finds more than one customer with the same primary email in the legal entity, then the user will not be able to log in on the website, as the system will not be able to find a unique customer record who should be able to sign in on the website.
	
- Create a customer hierarchy ID. In the Name field, enter a name.
- In the Organization field, enter the business partner organization customer.
- On the **"Hierarchy"** fast tab, select Add, and then select a customer of type person in the Name field. Choose the role as Admin for the customer that should be designated as Admin.
- Repeat this process to add additional customers to the hierarchy.

## Additional information
- All the jobs that are mentioned in this topic can be configured to run on a schedule in a batch format. The expectation is that business partners will configure batch jobs as required.
- Currently, only one user/customer record can be designated as an administrator user, and that role can be changed only in Commerce headquarters. There is no support for self-service capabilities that let business partners to designate multiple administrators or change administrators from B2B e-commerce websites.
- Although spending limits can be defined for users, enforcement of spending limits during the order entry process hasn't yet been implemented.
- All business logic and validation for a user's experience on a B2B e-commerce website are based on the configuration of the customer record that is mapped to the user in Commerce headquarters.

## Additional resources

[Set up a B2B e-commerce site](set-up-b2b-site.md)

[Create org modeling hierarchies for B2B organizations](org-model.md)

[Configure the customer account payment method for B2B e-commerce sites](payment-method.md)

[Set product quantity limits for B2B e-commerce sites](quantity-limits.md)

[Number sequences overview](../../fin-ops-core/fin-ops/organization-administration/number-sequence-overview.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
