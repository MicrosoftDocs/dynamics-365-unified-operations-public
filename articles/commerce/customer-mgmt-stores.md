---
title: Customer management in stores
description: Learn how retailers can manage customers and contacts at the point of sale (POS) in Microsoft Dynamics 365 Commerce.
ms.topic: how-to
ms.date: 01/21/2026
author: gvrmohanreddy
ms.author: shajain
ms.reviewer: mirao
ms.search.region: Global
ms.search.validFrom: 2021-01-31
ms.search.form: RetailOperations
ms.custom: 
  - bap-template
---

# Customer management in stores

[!INCLUDE [banner](includes/banner.md)]

This article explains how retailers can enable customer management capabilities at the point of sale (POS) in Microsoft Dynamics 365 Commerce.

Store associates need to create and edit customer records at the POS. When store associates use this approach, they can capture any updates to customer information such as the email address, phone number, and address. This information is helpful in downstream systems such as marketing, because the effectiveness of those systems depends on the accuracy of their customer data.

Sales associates can start the customer creation workflow from two POS entry points. They can select a button that is mapped to the **Customer add** operation, or they can select **Create customer** on the app bar on the search results page. In both cases, the **New customer** dialog box appears, where sales associates can enter required customer details, such as the customer's name, email address, phone number, address, and any extra information that's relevant to the business. You can capture that extra information by using the customer attributes that are associated with the customer. For more information about customer attributes, see [Customer attributes](dev-itpro/customer-attributes.md).

Sales associates can also capture secondary email addresses and phone numbers. Additionally, they can capture the customer's preference about receiving marketing information via any of those secondary email addresses or phone numbers. To enable this capability, retailers must turn on the **Capture multiple emails and phone numbers and consent for marketing on these contacts** feature in the **Feature management** workspace in Commerce headquarters (**Systems administration** > **Workspaces** > **Feature management**).

## Default customer properties

Retailers can use the **All stores** page in Commerce headquarters (**Retail and Commerce** > **Channels** > **Stores**) to associate a default customer with each store. Commerce then copies the properties that are defined for the default customer to all new customer records that are created. For example, the **Create customer** dialog box shows properties that are inherited from the default customer that is associated with the store. Those properties include the **customer type**, **customer group**, **receipt option**, **receipt email**, **currency**, and **language**. Any **affiliations** (groupings of customers) are also inherited from the default customer. However, **financial dimensions** come from the customer group that is associated with the default customer, not from the default customer itself.

> [!NOTE]
> The **receipt email** value comes from the default customer only if the receipt email ID isn't provided for the newly created customers. This condition means that if the receipt email ID is present on the default customer, then all the customers created from the e-commerce site get the same receipt email ID as there's no user interface to capture the receipt email ID from the customer. To avoid confusion, leave the **receipt email** field blank for the default customer of the store and use it only if you have a business process that depends on a receipt email address being present. 

Sales associates can capture multiple addresses for a customer. The customer's name and phone number come from the contact information associated with each address. The **Addresses** FastTab of a customer record includes a **Purpose** field that sales associates can edit. If the customer type is **Person**, the default value is **Home**. If the customer type is **Organization**, the default value is **Business**. Other values that this field supports include **Home**, **Office**, and **Post box**. The value of the **Country/region** field for an address comes from the primary address that is specified on the **Operating unit** page in Commerce headquarters at **Organization administration** > **Organizations** > **Operating units**.

> [!NOTE]
> As the number of addresses associated with a customer grows, the performance of the system is adversely impacted. Microsoft recommends avoiding customizations that result in thousands of addresses for any customer.

## Manage customer contacts in Store Commerce

When a person shops on behalf of an organization, store associates need to record both the customer account and the person they're serving. Customer contacts in Microsoft Dynamics 365 Commerce let associates select a contact for a POS transaction and maintain contact details without leaving Store Commerce.

### Set up customer contacts

An administrator must enable the feature in Commerce headquarters, configure the functionality profile used by the store, and update the POS screen layout. Configure contact-management permissions for associates who need to create or update contacts.

#### Enable the feature

1. In Commerce headquarters, go to **System administration** > **Workspaces** > **Feature management**.
1. Enable the **Enable customer contacts in Store Commerce** feature. This feature depends on the **Enable modernized customer details page** feature. To view or manage contacts from the customer details page, you need to first enable this feature.
1. Open the POS functionality profile assigned to the store.
1. In the **Customer contact** section, set **Enable customer contacts in POS** to **Yes**.
1. Save the profile.

> [!NOTE]
> Customer contacts are turned off by default in the functionality profile. Enabling the feature in **Feature management** makes the setting available, but you must also enable it in the profile used by each participating store. If multiple stores use the same profile, the profile change applies to those stores.

#### Show contacts on the transaction screen

1. Open the screen layout used by the store, register, or associate.
1. Open the screen layout designer for the required layout size.
1. Select the customer panel.
1. Turn on **Show contacts**.
1. Save the layout.

Repeat these steps for each applicable layout size. Synchronize the updated configuration to the stores before associates use the feature.

#### Configure contact-management permissions

Use the **Manage customer contacts** permission to control who can create contacts, edit contact details, or change a contact's status. Configure the appropriate POS permission groups and synchronize the updated permissions to the stores.

Associates who don't have permission are prompted for manager authorization when they save a new or updated contact. Selecting an existing contact for a transaction doesn't require the **Manage customer contacts** permission.

#### Check connectivity

Creating contacts, editing contact details, and changing contact status require Store Commerce to be online and able to communicate with Commerce headquarters.

### View an organization's contacts

1. In Store Commerce, find the organization's customer account.
1. Open the customer details page.
1. Select the **Contacts** tab.

The tab lists the customer's contacts, including active and inactive contacts. Each contact shows a name and status, together with the role, phone number, and email address when those details are available. Use the paging controls to view more contacts.

### Create a contact

1. On the customer's **Contacts** tab, select **Create contact**.
1. Enter the contact's **First name**.
1. Enter any other contact details.
1. Select **Save**.
1. Complete manager authorization if prompted.

It has the following fields:

| Field | Description |
| ----- | ----------- |
| **First name** | The contact's first name (required). |
| **Last name** | The contact's last name (optional). |
| **Phone** | The contact's phone number. |
| **Email** | The contact's email address. If you enter an address, it must have a valid email format. |
| **Role** | The contact's role at the organization. Select a value from the available list. The headquarters (also known as finance and operations) application maintains this list against the **Function** field of the contact and defines it on the form ID `mi=smmFunctionGroup`. |
| **Job title** | The contact's job title. Select a value from the available list. The headquarters (also known as finance and operations) application maintains this list against the **Job title** field of the contact. |
| **Status** | **Active** or **Inactive**. You can only add active contacts to a transaction. |

After you save, the contact appears in the organization's contact list. Creating a contact from the **Contacts** tab doesn't automatically add that contact to the current transaction.

### Edit a contact

1. On the customer's **Contacts** tab, find the contact.
1. Select **Edit contact**.
1. Update the contact details.
1. Select **Save**.
1. Complete manager authorization if prompted.

If manager authorization is canceled or the save fails, the dialog reopens with the entered values so that you can retry.

#### Deactivate or reactivate a contact

When a person should no longer be selected for new transactions, change their status instead of removing the contact.

1. On the customer's **Contacts** tab, select **Edit contact** for the contact.
1. Set **Status** to **Inactive**.
1. Select **Save**.
1. Complete manager authorization if prompted.

The contact remains visible on the **Contacts** tab, but isn't offered when an associate selects a contact for a transaction. Deactivation doesn't delete the contact or remove their association with previous transactions.

To make the contact available again, edit the contact and set **Status** to **Active**.

### Add a contact to a transaction

Select the organization first, and then select the person you're serving.

1. Add the organization's customer account to the transaction.
1. In the customer card, select **Add contact**.
1. Find the contact in the **Add contact to transaction** dialog.
1. Select **Add to sale** for that contact.

The dialog closes, and the customer card shows the selected contact. The organization remains the customer account for the transaction.

> [!NOTE]
> Selecting a contact is optional. You can only select active contacts associated with the selected customer. Follow your store's identity-verification procedures before selecting a contact.

#### Create a contact while serving a customer

If the person isn't listed, you can create the contact and add them to the transaction in the same workflow.

1. In the contact selection dialog, select **Create contact**.
1. Enter the contact's **First name**.
1. Enter any other contact details.
1. Select **Create and add**.
1. Complete manager authorization if prompted.

The new contact is created as active and added to the transaction. The **Status** field doesn't appear in this workflow.

### Include contact details on receipts

Administrators can add the selected contact's details to a receipt format. Contact fields are available in both the modern and legacy receipt designers.

1. In Commerce headquarters, go to **Retail and Commerce** > **Channel setup** > **POS setup** > **POS** > **Receipt formats**.
1. Select the receipt format to update.
1. Open the receipt designer.
1. Add the required contact fields to the layout.
1. Save the format.
1. Synchronize the updated receipt configuration to the stores.

The following contact fields are available:

- **Contact First Name**
- **Contact Last Name**
- **Contact Phone**
- **Contact Email**

Contact details don't appear automatically on existing receipt layouts. Add the fields to each format where you want them to appear. If no contact is associated with a transaction, these fields are blank.

Deactivating a contact doesn't prevent their contact details from appearing when a receipt for a previous transaction is rendered.

For more information, see [Set up and design receipt formats](receipt-templates-printing.md).

### Resolve common issues

| Issue | What to check |
| ----- | ------------- |
| The **Contacts** tab isn't available. | Confirm that the feature is enabled, **Enable customer contacts in POS** is set to **Yes** in the functionality profile used by the store, and updated configuration has reached the store. |
| **Add contact** isn't shown on the transaction screen. | Add a customer to the transaction. Confirm that contacts are enabled for the store and **Show contacts** is turned on in the screen layout currently used by the device and associate. |
| A contact is visible on the **Contacts** tab, but not in the transaction's contact list. | Check the contact's status. The transaction selection dialog only shows active contacts for the selected customer. |
| Contact changes can't be saved while offline. | Restore the online connection before you create, edit, or change the status of a contact. |
| Saving a contact requires manager sign-in. | Complete manager authorization or ask an administrator to review the associate's **Manage customer contacts** permission. |
| The selected contact is reported as inactive during checkout. | Remove the contact from the transaction and select an active contact, or have an authorized user reactivate the contact if needed. |
| The selected contact isn't associated with the customer. | Remove the selection and choose a contact associated with the customer account on the transaction. |
| Contact details don't appear on a receipt. | Confirm that a contact was selected for the transaction and that the applicable receipt format contains the contact fields. |

## Related information

[Asynchronous customer creation mode](async-customer-mode.md)
[Convert asynchronous customers to synchronous customers](convert-async-to-sync.md)
[Customer attributes](dev-itpro/customer-attributes.md)
[Offline data exclusion](dev-itpro/implementation-considerations-cdx.md#offline-data-exclusion)
