---
# required metadata

title: Onboard business partners 
description: This topic describes how to add, edit, and delete partner users from B2B e-commerce sites.
author: josaw1
manager: AnnBe
ms.date: 01/12/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 
# optional metadata
ms.search.form:  RetailOperations
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: josaw
#ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: retail
ms.author: josaw
ms.search.validFrom: 2021-01-31
ms.dyn365.ops.version: 10.0.14

---



# Onboard business partners 

[!include [banner](../../includes/banner.md)]

B2B e-commerce websites require that an Organization need to register to
become a business partner. Once they submit their registration details
on the e-commerce site, they go through a qualification process to
become a Business partner and only on successful qualification are they
on-boarded as a Business partner. 

Once the Organization is on-boarded as a Business partner, the user who
initiates the request to become a Business partner is identified as an
Admin user and he/she is provided with the privileges to onboard
additional users as authorized users of the B2B e-commerce portal. These
authorized users can place orders on behalf of the Business
partner. The users of the Business partner should be able to see the
Order details & history of the orders that they have created. The Admin
user of the Business partner should be able to see the Order details &
history of the orders across the Business partners users. The same is
true for functions like request of documents like account
statements, aged debtors listing report etc.

The below section covers details on how Business partners are on-boarded
to the D365 Commerce B2B website and how the Business partner
organization is represented in Commerce HQ.

## Details

### Enable the feature

1.  Navigate to **Workspaces &gt; Feature Management**

2.  Select the **All** tab

3.  Filter on the Module field by **Retail and commerce**

4.  Enable the feature **Enable the use of B2B eCommerce capabilities**

### Setup

1.  Create a Number sequence from the following path **Headquarters
    setup &gt; Number sequences &gt; Number sequences**

2.  Attach the above created number sequence to **Customer hierarchy
    ID** from the following path **Headquarters setup &gt;
    Parameters &gt; Commerce shared parameters**

### Self-serve based on-boarding of business partner & setting up Admin user

1.  Potential business partners can initiate the on-boarding process to
    the B2B e-commerce website by submitting an on-boarding request
    through the site. This can be done by clicking the link for
    on-boarding on the site. On clicking the link, the business partner
    can provide the details required for the on-boarding and clicking
    Sign-up. Refer screenshot below

2.  On submitting the request, the user should see a confirmation
    screen. Refer screen shot below:

3.  Execute the **P-0001** job from the path **Retail and Commerce
    IT &gt; Distribution Schedule** to pull all the business partner
    on-boarding request to HQ

4.  After the P-0001 job successfully brings the on-boarding request
    into HQ, execute the job **Synchronize customers and business
    partners from async mode** from the path **Retail and Commerce
    IT &gt; Customer.** On successful execution of this job, the
    on-boarding requests will be created as Prospects record in Commerce
    HQ and the **Type ID** of such prospect records will be set to **B2B
    prospect**

5.  Open the prospects form from the path **Customers &gt; All
    prospects**

6.  Click on the prospect record that needs to be actioned to open the
    prospect details form

7.  Approve or Reject the on-boarding request by clicking on the tab
 **General &gt; Convert &gt; Approve / Reject**

8.  On clicking **Approve / Reject**, a confirmation dialog will pop-up
    that will allow a user to continue with the process or discontinue
    the process

9.  If the request is approved, the **Status** on the prospect record
    will be set to **Approved** and 2 new customer records are created
    in the system, one customer of the **Type Organization** for the
    Business partner organization and second customer of the **Type
    Person** for the requestor. A customer hierarchy record for the
    business partner is also created (Please refer to the Org modeling
    of B2B customer section in this document for more information)

10. Execute the **1010 Customers** job from the path **Retail and
    Commerce IT &gt; Distribution Schedule** to push the newly created
    customers & customer hierarchy record to the Channel DB.

11. An email will be triggered to the requestor's email address
    confirming that they have been approved or rejected to be a business
    partner

12. If the request is approved and after the customer & customer
    hierarchy records are synchronized to the Channel DB, the requestor
    will be able to sign-in to the B2B e-commerce website using the
    email address that was provided at the time of submitting the
    request. During the first log-in, the requestor will be prompted to
    set a password for themselves.

### On-boarding business partner users

The Admin user of the business partner organization can on-board
additional users from the organization to the B2B e-commerce website by
following the steps below:

1.  Sign into the B2B e-commerce website

2.  Navigate to **My Account &gt; Organization users &gt; View details**

3.  Click on **Add a user**

4.  Fill in the required information and click **Save**

5.  The status of the newly added user will be set to **Pending**

6.  After the **P-0001** job and the **Synchronize customers and
    business partners from async mode** jobs are executed**,** the newly
    added user is also created as a customer of the Type Person in
    Commerce HQ and the customer record is also associated to the
    relevant Business partners customer hierarchy record.

7.  An email is triggered to the users email address notifying that they
    have been added as a user of the Business partner organization and
    can now log-in to the B2B e-commerce website

8.  The **1010 Customer** job will sync the newly created customer to
    the Channel DB

9.  When the customer for the newly added user is synchronized to the
    Channel DB, the status of the user on the B2B e-commerce website is
    set to Active

10. When the status of the newly created user is set to Active, the user
    will be able to log-in to the B2B e-commerce website using their
    email address. They will be prompted to set up their password on
    their first log-in



### Editing user details

The details of a business partner user can be edited by the Admin user
as per the below steps:

1.  Sign into the B2B e-commerce website

2.  Navigate to **My Account &gt; Organization users &gt; View details**

3.  Click on the **Edit** (pencil) button and make the required changes
    and click **Save**

4.  After the **P-0001** job, **Synchronize customers and business
    partners from async mode** job and **the 1010 Customer job** is
    executed, the changes will be reflected

### Removing a user

An existing user of a business partner organization can be removed by
the Admin user from the list of users who can access the B2B e-commerce
website by following the steps below:

1.  Sign into the B2B e-commerce website

2.  Navigate to **My Account &gt; Organization users &gt; View details**

3.  Click on the **Remove** ( X )button and in the pop-up window,
    confirm the same

4.  After the **P-0001** job, **Synchronize customers and business
    partners from async mode** job and **the 1010 Customer job** is
    executed, the changes will be reflected

5.  Removing the user from the website will remove the corresponding
    customer record from the business partners customer hierarchy
    record. The customer itself will not be deleted from Commerce HQ.

### On-boarding business partner & users from Commerce HQ

Users can choose to on-board business partner & users directly from
Commerce HQ by following the steps below:

1.  Create a customer record of the **Type Organization** for the
    business partner organization

2.  Create customer records of the **Type Person** for business partner
    users. Ensure that all customers have a primary email address
    defined for them

3.  For the customer of the **Type Person** who needs to be designated
    as the **Admin** user of the business partner organization, set the
    field **B2B administrator** to Yes under the **Retail** fast tab of
    the customer record

4.  Create a Customer hierarchy id and

    1.  Specify a **Name**

    2.  Associate the business partner organization customer to the
 **Organization** field

    3.  Click on **Add** and in the **Name** field, select a customer
        using the drop down. Repeat the process to add additional
        customers to the hierarchy.


## Call outs

1.  All jobs that are referenced in the document above can be configured
    to run on a schedule in a batch format and it is expected that
    customers configure them accordingly.

2.  In this release, only one user / customer can be designated as an
    Admin user and the role can be changed only in HQ. Self-serve
    capability for the business partner to designate multiple admins or
    change admins from the B2B e-commerce website is not supported.

3.  The modules & labels of the different fields referenced in the
    screenshots for e-commerce are only for illustration purposes.
    Customers have complete control on the placement of the B2B related
    modules and the labels.

4.  While **Spending limits** can be defined for users, the enforcement
    of the same during the order entry process has not been implemented
    in this release.

5.  All business logics & validations for a user's experience on the B2B
    e-commerce website is based on the configuration for the
    corresponding customer record that is mapped to the user in Commerce
    HQ.

