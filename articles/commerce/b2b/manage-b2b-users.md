---
# required metadata

title: Manage business partner users on B2B e-commerce websites
description: This topic describes how administrators can add, edit, and delete business partner users on business-to-business (B2B) e-commerce websites.
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

This topic describes how administrators can add, edit, and delete business partner users on business-to-business (B2B) e-commerce websites.

B2B e-commerce websites require that organizations register to become business partners. After an organization submits registration details to a B2B e-commerce website, it goes through a qualification process. If the organization is successfully qualified, it's onboarded as a business partner.

After an organization is onboarded as a business partner, the organization user who initiated the request to become a business partner is identified as the administrator user and is granted privileges to onboard additional authorized users of the B2B e-commerce website. These authorized users can then place orders on behalf of the business partner.

## Turn on the B2B e-commerce capabilities feature in Commerce headquarters

The B2B e-commerce capabilities feature in Commerce headquarters enables organizations to onboard business partners and define administrator users. This feature also enables administrators to create and manage business partner users and teams, and to assign specific roles to them. Finally, it enables business partner users to create order templates and use existing orders to reorder products.

To turn on the B2B e-commerce capabilities feature in Commerce headquarters, follow these steps.

1. Go to **Workspaces \> Feature Management**.
1. On the **All** tab, filter on the **Module** field by using the term **Retail and commerce**.
1. Find and select the feature that is named **Enable the use of B2B eCommerce capabilities**, and then select **Enable now**.

## Create a number sequence and add it to Commerce shared parameters

Number sequences are used to generate readable, unique identifiers for master data records and transaction records that require identifiers. For more information about number sequences, see [Number sequences overview](../../fin-ops-core/fin-ops/organization-administration/number-sequence-overview.md).

To create a number sequence and add it to Commerce shared parameters in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Headquarters setup \> Number sequences \> Number sequences**, and create a number sequence.
1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**, and add the new number sequence to the **Customer hierarchy ID** reference.

## Set up the administrator user for a new business partner

Potential business partners can initiate the onboarding process to a B2B e-commerce website by submitting an onboarding request via a link on the site. After a potential business partner user selects the link, they can provide the details that are required for onboarding and sign-up. After the request is submitted, a submission confirmation page appears. If the submission is approved, the requestor (that is, the user who initiated the onboarding request) becomes the business partner administrator user.

To approve and set up a business partner administrator user in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce IT \> Distribution schedule**.
1. Run the **P-0001** job to pull all business partner onboarding requests into Commerce headquarters.
1. After the **P-0001** job has successfully run, go to **Retail and Commerce IT \> Customer**, and run the **Synchronize customers and business partners from async mode** job. After this job has successfully run, the onboarding requests are created as prospects records in Commerce headquarters. The **Type ID** field of these records is set to **B2B prospect**.
1. Go to **Customers \> All prospects**, and open the prospects page.
1. Select the prospect record for the new business partner to open the prospect details page.
1. On the **General** tab, select **Convert \> Approve/Reject** to approve or reject the onboarding request. When a confirmation message appears, confirm that you want to continue with the process, and approve the request. An email is then sent to the requestor's email address to confirm that their organization has been approved as a business partner.

    After you approve the request, the **Status** field of the prospect record is set to **Approved**. Additionally, two new customer records are created in the system: a **Type Organization** customer record for the business partner organization and a **Type Person** customer record for the requestor. A customer hierarchy record for the business partner is also created. <!--(Please refer to the Org modeling of B2B customer section in this document for more information)-->

1. Go to **Retail and Commerce IT \> Distribution schedule**, and run the **1010** (**Customers**) job to push the newly created customer and customer hierarchy records to the channel database.

After the request is approved, and the customer and customer hierarchy records are synced to the channel database, the requestor can sign in to the B2B e-commerce website by using the email address that they provided when they submitted the request. Users can use the sign-up flow to define the password for their account. To enable the identity provider (Azure AD B2C) record to be linked to the B2B customer record that was created at sign-up or sign-in, follow the instructions in [Enable automatic linking of identity records to customer accounts](../identity-record-linking.md).

## Notify B2B prospects when they are approved or rejected

When you approve or reject a B2B prospect onboarding request, you can automatically send an email notification to the prospect. 

To set up email notifications in Commerce headquarters for events of the B2B prospect approved or B2B prospect rejected notification type, follow these steps.

1. Create email templates for emails that will be sent to prospects when the B2B prospect approved or B2B prospect rejected notification type is triggered.

    For information about the placeholders that the B2B prospect approved and B2B prospect rejected notification types support, see [Notification types](../email-templates-transactions.md#notification-types). For information about how to create email templates, see [Create an email template](../email-templates-transactions.md#create-an-email-template). 

1. Add the B2B prospect approved and B2B prospect rejected notification types to your email notification profile, and map them to the email templates that you created. For more information about notification profiles, see [Set up an email notification profile](../email-notification-profiles.md). 

## Onboard additional business partner users

The business partner administrator user can onboard additional business partner users to the B2B e-commerce website as required.

To onboard additional business partner users to a B2B e-commerce website, follow these steps.

1. Sign in to the B2B e-commerce website as an administrator.
1. Go to **My Account \> Organization users \> View details**, and select **Add a user**.
1. Enter the required information, and then select **Save**. The status of the new user is set to **Pending**.

    After the **P-0001** and **Synchronize customers and business partners from async mode** jobs are run, a **Type Person** customer record for the new user is created in Commerce headquarters. This customer record is also associated with the relevant business partner's customer hierarchy record. Additionally, an email is sent to the new user's email address to notify them that they have been added as a user of the business partner organization and can now sign in to the B2B e-commerce website.

1. Run the **1010** (**Customers**) job to sync the new business partner user to the channel database.

After the customer record is synced, the status of the user on the B2B e-commerce website is set to **Active**, and the new user can sign in to the B2B e-commerce website by using their email address. Users can use the sign-up flow to define the password for their account. To enable the identity provider (Azure AD B2C) record to be linked to the B2B customer record that was created at sign-up or sign-in, follow the instructions in [Enable automatic linking of identity records to customer accounts](../identity-record-linking.md).

## Edit business partner user details

To edit the details of business partner users, follow these steps.

1. Sign in to the B2B e-commerce website as an administrator.
1. Go to **My Account \> Organization users \> View details**, select the **Edit** button (pencil symbol), make the required changes, and then select **Save**. The changes take effect only after the **P-0001**, **Synchronize customers and business partners from async mode**, and **1010** (**Customers**) jobs have been run.

## Remove a business partner user

As required, an administrator can remove existing users of a business partner organization from the list of users who can access the B2B e-commerce website.

To remove a business partner user, follow these steps.

1. Sign in to the B2B e-commerce website as an administrator.
1. Go to **My Account \> Organization users \> View details**, and select the **Remove** button ("X" symbol). When a confirmation message appears, confirm that you want to remove the user. The change takes effect only after the **P-0001**, **Synchronize customers and business partners from async mode**, and **1010** (**Customers**) jobs have been run.

> [!NOTE]
> When you remove a user from the list of users who can access the B2B e-commerce website, the corresponding customer record is removed from the business partner's customer hierarchy record. However, the customer record itself isn't deleted from Commerce headquarters.

## Onboard business partner and users in Commerce headquarters

Administrators can onboard business partners and users directly in Commerce headquarters.

To onboard business partners and users in Commerce headquarters, follow these steps.

1. Create a **Type Organization** customer record for the business partner organization.
1. Create **Type Person** customer records for business partner users. Make sure that a primary email address is specified for every customer.
1. For each **Type Person** customer record that must be designated as an administrator user of the business partner organization, on the **Retail** FastTab, set the **B2B administrator** option to **Yes**.
1. Create a customer hierarchy ID. In the **Name** field, enter a name.
1. In the **Organization** field, enter the business partner organization customer.
1. Select **Add**, and then select a customer in the **Name** field.
1. Repeat this process to add additional customers to the hierarchy.

## Additional information

- All the jobs that are mentioned in this topic can be configured to run on a schedule in a batch format. The expectation is that business partners will configure batch jobs as required.
- Currently, only one user/customer record can be designated as an administrator user, and that role can be changed only in Commerce headquarters. There is no support for self-service capabilities that let business partners to designate multiple administrators or change administrators from B2B e-commerce websites.
<!--- The modules and labels of the different fields referenced in the screenshots for e-commerce are only for illustration purposes. Customers have complete control on the placement of the B2B related modules and the labels.-->
- Although spending limits can be defined for users, enforcement of spending limits during the order entry process hasn't yet been implemented.
- All business logic and validation for a user's experience on a B2B e-commerce website are based on the configuration of the customer record that is mapped to the user in Commerce headquarters.

## Additional resources

[Set up a B2B e-commerce site](set-up-b2b-site.md)

[Create org modeling hierarchies for B2B organizations](org-model.md)

[Configure the customer account payment method for B2B e-commerce sites](payment-method.md)

[Set product quantity limits for B2B e-commerce sites](quantity-limits.md)

[Number sequences overview](../../fin-ops-core/fin-ops/organization-administration/number-sequence-overview.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
