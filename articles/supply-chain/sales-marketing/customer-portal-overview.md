---
# required metadata

title: XXXX
description: XXXX
author: XXXX
manager: tfehr
ms.date: mm/dd/yyyy
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: XXXX
ms.search.validFrom: yyyy-mm-dd
ms.dyn365.ops.version: Release 10.0.xx
---

# Customer portal for Dynamics 365 Supply Chain Management: Overview

## What is the customer portal?

Modern supply chain systems rely on integration. They require that inventory, customer demand, and sales departments be integrated, not residing in separate silos. The Customer portal helps organizations that run Supply Chain Management enhance this integration and more effectively keep their customers informed.

The Customer portal is a [Power Apps portals](https://docs.microsoft.com/en-us/powerapps/maker/portals/overview) template that lets companies create an externally facing business-to-business (B2B) website for scenarios that are related to sales-order processing. The template uses [dual-write](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/dual-write-home-page), Supply Chain Management, and Power Apps portals to enable external enterprise customers to view and create data from the company's Dynamics 365 environment.

The Customer portal template has all the customization capabilities that the portals feature of Power Apps offers. The template can easily be modified to represent the company's brand, add increased functionality, and change the user experience. All the functionality that the template offers out of the box can be modified as desired.

_ **By itself, the template isn't expected to be completely functional: it just serves as an enabler for customers who want to create an externally facing website so that enterprise customers can engage with data from Supply Chain Management.** _

**Note:** This document is directed at admins, customizers, and system integrators who will set up the Customer portal for a Supply Chain Management installation. It uses the terms _customer_ and _user_ to describe people who are customers of the organization that is running Supply Chain Management, and who will use the final portal itself.

## Who should use it?

The Customer portal is designed for companies that run Supply Chain Management and that have these characteristics:

- They want to build an externally facing website that communicates order processing information (such as order status or account information) directly from their Supply Chain Management system to their enterprise customers.
- They are transitioning from Dynamics AX 2012 to Supply Chain Management and previously used the [AX 2012 Customer self-service portal.](https://docs.microsoft.com/en-us/dynamicsax-2012/appuser-itpro/about-the-customer-self-service-portal)

The following types of organizations are **not** good candidates for implementing the Customer portal:

- Companies that want to build a website for non-enterprise customers. These companies should consider creating a [Dynamics 365 Commerce e-commerce website](https://docs.microsoft.com/en-us/dynamics365/commerce/create-ecommerce-site).
- Companies that are already using an existing Power Apps portals website for a similar purpose. These companies won't receive any additional benefits from the Customer portal. The Customer portal is delivered as a template that acts as a guide and a starting point for customers who want to "connect the dots" between dual-write, Supply Chain Management, and Power Apps portals. If you've already set up a website that serves this purpose, you might not gain much value from using the Customer portal template to re-provision that website.

## How does it work?

The Customer portal is provided as a Power Apps portals template. It depends on Power Apps portals and dual-write.

[Power Apps portals](https://docs.microsoft.com/en-us/powerapps/maker/portals/overview) is a feature that lets users create an externally facing website that people from outside the organization can sign in to. Little to no coding is required to make portals. The Customer portal is one of many [Dynamics 365 portal templates](https://docs.microsoft.com/en-us/powerapps/maker/portals/portal-templates#environment-with-model-driven-apps-in-dynamics-365) that are available from Microsoft.

[Dual-write](https://docs.microsoft.com/en-us/powerapps/maker/portals/overview) is an out-of-box infrastructure product that provides near-real-time interaction between model-driven apps in Dynamics 365 and Finance and Operations apps. Dual-write provides bidirectional integration between Finance and Operations apps and Common Data Service. Therefore, it provides an integrated user experience across the apps.

The Customer portal depends on entities that are synced with dual-write. Before data from Supply Chain Management can be surfaced in the Customer portal, dual-write must be enabled for all the appropriate entities

The Customer portal acts as a starting point for organizations that want to use Power Apps portals to build an externally facing website that uses data from their Supply Chain Management installation. It helps organizations connect dual-write, Supply Chain Management, and Power Apps portals.

# Install, set up, and update the portal

## Licensing requirements

To implement the Customer portal, you must have the following licenses:

- **Dynamics 365 for Supply Chain Management P2 license** – This license is required to use dual-write to create and view sales orders. For details and links to complete licensing information, see the [Dynamics 365 Pricing webpage](https://dynamics.microsoft.com/en-us/pricing/#Operations). If you don't have a P2 license make sure you have the Dynamics 365 Sales solution.
- **Power Apps portals** – This license is required to host the Customer portal. Portals are licensed based on usage. For details, see the [Power Apps portals licensing requirements](https://docs.microsoft.com/en-us/power-platform/admin/powerapps-flow-licensing-faq#portals).

## Dependencies on dual-write and Power Apps portals

The Customer portal depends on Power Apps portals and dual-write, as shown in the following illustration.

Unlike other features from Supply Chain Management, the template resides in Power Apps portals. Therefore, the Customer portal is limited by the functionality and capabilities that are provided by Power Apps portal and the entities in dual-write.

## Required setup to enable the Customer portal

After you've made sure that you have the required licenses, you can set up dual-write as described in the [dual-write initial synchronization instructions](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/initial-sync).

Be sure to enable the following entity mappings in dual-write:

- Sales Order Header
- Sales Order Details
- Accounts
- Contacts
- Products

After these entities are enabled, you can provision the Customer portal template.

## Provision the Customer portal

Before you provision the Customer portal, make sure that you've already completed the [required setup](https://theazimuthgroupllc-my.sharepoint.com/personal/chris_read_azimuth-grp_com/Documents/Desktop/To%20edit/Customer%20Portal%20Documentation.docx#_Required_setup_to). To provision the Customer portal, follow these steps.

1. Go to [make.powerapps.com](http://make.powerapps.com/).
2. Make sure that you're using the environment where you enabled dual-write.
3. On the **Create** tab, scroll down to the **Start from template** section, and select the template that is named **Supply Chain Management Customer**.
4. Follow the on-screen instructions.

After provisioning is completed, you can access the Customer portal in the **Your apps** section of the **Home** page.

**Note:** If the dual-write solution isn't installed in the environment that you're working in, you will receive an error message, and the Customer portal won't be provisioned.

## Update the Customer portal

More functionality might be added to the Customer portal later. Any changes that Microsoft makes to the underlying solution components will automatically appear in your environment. However, changes in the configuration data won't automatically be present on the provisioned website. You will have to manually apply these changes by getting the code from the new template and merging it with the website that is provisioned in your environment.

## Resources

To learn how you can set up and customize the Customer portal, you should start by reviewing the following documentation for the underlying technologies:

- [Power Apps portals documentation](https://docs.microsoft.com/en-us/powerapps/maker/portals/overview)
- [Dual-write documentation](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/dual-write-home-page)

To effectively manage your portals, you must understand the Power Apps portals and Common Data Service lifecycle. For details, review the following resources:

- [About portal lifecycle](https://docs.microsoft.com/en-us/powerapps/maker/portals/admin/portal-lifecycle)
- [Upgrade a portal](https://docs.microsoft.com/en-us/powerapps/maker/portals/admin/upgrade-portal)
- [Migrate portal configuration](https://docs.microsoft.com/en-us/powerapps/maker/portals/admin/migrate-portal-configuration)
- [Solution Lifecycle Management: Dynamics 365 for Customer Engagement apps](https://www.microsoft.com/en-us/download/details.aspx?id=57777)

# User administration for the Customer portal

Out of the box, there is no way for users to self-register for websites that are created using the Customer portal. To sign in and use the website, users must be invited by the admin. Microsoft has intentionally blocked the ability of users to self-register.

Before a user can use the website, a contact record must be created for that user. This contact record indicates which customer account and legal entity the user belongs to. This information is essential for ensuring that the user can create and view sales orders.

When users self-register, contact records are automatically created for them. Therefore, you can't ensure that a user selects the correct customer account and legal entity. On the other hand, the invitation process lets an admin assign the correct customer account and legal entity to the contact record before an invitation is sent. If you're thinking about customizing the solution so that users can self-register, be sure to consider the possible consequences.

## Prerequisite setup

Contacts in Power Apps portals are stored as records in the **Contacts** entity in Common Data Service. Dual-write then syncs these records to Supply Chain Management as required.

Before you start to invite new customers, make sure that you've enabled the **Contact** entity mapping in dual-write.

## The invitation process

To invite an existing contact to the Customer portal, follow the steps in [Invite contacts to your portals](https://docs.microsoft.com/en-us/powerapps/maker/portals/configure/invite-contacts) in the Power Apps portals documentation.

Before you invite a customer to join the Customer portal, make sure that the customer's [contact record](https://docs.microsoft.com/en-us/powerapps/maker/portals/configure/configure-contacts) is available and set up in the following way:

1. Set the **Company** field to the legal entity that you want the customer to belong to in Supply Chain Management.
2. Set the **Account Number** field to the customer account number that you want the user to have in Supply Chain Management.

After a contact is created, you should be able to see the same contact in Supply Chain Management.

For more information, see [Configure a contact for use on a portal](https://docs.microsoft.com/en-us/powerapps/maker/portals/configure/configure-contacts) in the Power Apps portals documentation.

## Out-of-box web roles and entity permissions

User roles in Power Apps portals are defined by [web roles](https://docs.microsoft.com/en-us/powerapps/maker/portals/configure/create-web-roles) and [entity permissions](https://docs.microsoft.com/en-us/powerapps/maker/portals/configure/assign-entity-permissions). A few roles are defined for the Customer portal out of the box. You can create new roles, and you can modify or remove existing roles.

### Out-of-box web roles

This section describes the web roles that are delivered with the Customer portal.

For more information about how to modify the out-of-box user roles, see [Create web roles for portals](https://docs.microsoft.com/en-us/powerapps/maker/portals/configure/create-web-roles) and [Add record-based security by using entity permissions for portals](https://docs.microsoft.com/en-us/powerapps/maker/portals/configure/assign-entity-permissions) in the Power Apps portals documentation.

#### Administrator

The administrator oversees and maintains the website. This person will provision and set up the Customer portal. The administrator maintains the IT and security aspects of the portal, and makes sure that everything runs smoothly. The administrator might also customize and/or change the portal by adding new functionalities, creating new roles, and more.

#### Customer representative

A customer representative works for a customer company and is responsible for managing the orders that the company places. The customer representative can see all the orders that have been placed for the company and the users who placed them. Additionally, the customer representative can see information about the overall account and which contacts can place orders on behalf of that account.

#### Authorized users

Authorized users can place orders and view the status of the orders that they have placed, but not the orders that other users at their company have placed.

#### Unauthorized users

Unauthorized users can't view any data. They can see only public information, such as terms and conditions, and details about the company that is running the Customer portal.

#### Example

The following table shows which sales orders the users in each web role will be able to see in the system.

| **Sales order** | **Administrator** | **Customer representative for customer X** | **Authorized user: Jane** | **Authorized user: Sam** | **Unauthorized user: May** |
| --- | --- | --- | --- | --- | --- |
| Customer: XOrderer: Jane | ü | ü | ü | X | X |
| Customer: XOrderer: Sam | ü | ü | X | ü | X |
| Customer: YOrderer: May | ü | X | X | X | X |

**Note:** Even though both Sam and Jane are contacts who work for customer X, they can see only the orders that they themselves have placed and nothing else. Although May has an order in the system, she can't see that order in the Customer portal, because she is an unauthorized user. (Additionally, she must have placed the order through some channel other than the portal.)

# Customize and use the Customer portal

This section describes the different pages that available in the Customer portal out of the box. It explains what the page does and how you can customize them.

The Customer portal offers a few webpages and actions out of the box. The following site map provides an overview of all the pages, actions, and who can perform those actions.

## Typical customizations

The following topics will help you learn the basics about Power Apps portals and how you can customize portals:

- [Work with templates](https://docs.microsoft.com/en-us/powerapps/maker/portals/work-with-templates) – This topic provides a general overview of how Power Apps portals works and how you can do simple customizations of portals.
- [Manage portal content](https://docs.microsoft.com/en-us/dynamics365/portals/manage-portal-content) – This topic explains how you can manage and customize the content that you surface in your portal.
- [Edit CSS](https://docs.microsoft.com/en-us/powerapps/maker/portals/edit-css) – This topic helps you make more complex customizations to the user interface (UI) of your portal.
- [Create a theme for your portal](https://docs.microsoft.com/en-us/dynamics365/portals/create-theme) – This topic helps you create a UI theme for your portal.
- [Create and expose portal content easily](https://docs.microsoft.com/en-us/dynamics365/portals/create-expose-portal-content) – This topic helps you manage the underlying data and entities that you use for your portal.
- [Configure a contact for use on a portal](https://docs.microsoft.com/en-us/powerapps/maker/portals/configure/configure-contacts) – This topic explains how to create and customize user roles, and how security and authentication work in Power Apps portals.
- [Configure notes for entity forms and web forms on portals](https://docs.microsoft.com/en-us/powerapps/maker/portals/configure-notes) – This topic explains how to add documents and additional storage to your portal.
- [Error handling for portal website](https://docs.microsoft.com/en-us/powerapps/maker/portals/admin/view-portal-error-log) - This topic explains how to view portal error logs and store them in your Azure Blob storage account

## Customize the order creation process

When a user submits an order by using the Customer portal, the order is automatically synced to the corresponding Supply Chain Management environment. Because the user is an external customer, some required information is intentionally hidden from him or her. This information will automatically be filled when the form is submitted.

This section shows how you should set up contacts to avoid errors. It explains fields are automatically set and how you can modify the value of those fields if you must.

### The out-of-box order creation process

Here are the standard steps for submitting an order from the Customer portal.

1. On the home page, select the **Create order** tile to open the **Create Order** wizard.
2. On the **Order Information** page, set the following fields:

  - **Requested receipt date** – Specify the date of delivery.
  - **Delivery address** – Enter the address that the order should be delivered to.
  - **Company** – Select the name of the customer company. This field is automatically set for non-admin users.
  - **Requisition number** – Enter the requisition number of the order. This field isn't required.
  - **Ship to country/region** – Enter the country/region that the items will be delivered to. This field is automatically set for non-admin users.

1. Select **Next**.
2. On the **Items** page, select **Add Item**.

1. In the **Item Information** dialog box, set the following fields:

  - **Product Name** – Find and select a product to add to the order.
  - **Quantity** – Enter the quantity of the selected product.
  - **Unit** – Specify the unit of measure (for example, **ea.** , **kgs** , or **box** ).
  - **Estimated net amount** – The value is calculated as the estimated price of the item × the quantity for the selected unit.

1. Select **Submit** to add the item to the order.
2. Repeat steps 4 through 6 until you've added all the items that you want to order.
3. When you've finished adding items, select **Next** on the **Items** page.
4. The **Review and submit** page provides a summary of the order. Review the order contents and delivery details. If everything looks correct, select **Submit** to submit the order.

1. Standard data setup

To help ensure a smooth user experience, the Customer portal automatically fills values for several required fields. These values are based on information in the contact record of the customer who is submitting the order.

For each [contact record](https://docs.microsoft.com/en-us/powerapps/maker/portals/configure/configure-contacts) that belongs to a customer who will submit orders by using the Customer portal, values must be specified for the following required fields. Otherwise, errors will occur.

- **Company** – The legal entity that the order belongs to
- **Potential customer** – The customer account that is associated with the order
- **Price list** – The custom price list for the customer
- **Currency** – The currency of the price
- **Ship to country/region** – The country/region that the items will be delivered to

The following fields are automatically set for the sales order entity:

- **Language** – The language of the order (By default, the value is taken from the contact record.)
- **Ship to country/region** – The country/region that the items will be delivered to (By default, the value is taken from the contact record.)
- **Contact person** – The user who can be contacted for information about the order (By default, the value is taken from the contact record.)
- **Company** – The legal entity that the order belongs to (By default, the value is taken from the contact record.)
- **Potential customer** – The customer account associated with the order (defaulted from contact)
- **Invoice customer** – The billing account of the order (The default value is the potential customer from the contact record.)
- **Sales order name** – The name of the sales order (The default value is **sales order**.)
- **Currency** – The currency of the price (By default, the value is taken from the contact record.)
- **Price list** – The custom price list for the customer (By default, the value is taken from the contact record.)
- **Delivery address description** – The delivery address of the sales order (The default value is **delivery address description**.)

### Modify the order creation process

You can freely modify the appearance and UI of the Customer portal, if you don't change the basic order creation process. However, if you want to change the creation process, there are a few things that you must keep in mind.

Don't remove the following fields from the sales order entity in Common Data Service, because they are required to create a sales order in dual-write:

- **Company** – The legal entity that the order belongs to
- **Name** – The name of the sales order
- **Currency** – The currency of the price
- **Price list** – The custom price list for the customer
- **Ship to country/region** – The country/region that the items will be delivered to
- **Potential customer** – The customer account that is associated with the order
- **Language** – The language of the order (Typically, this language is the language of the potential customer.)
- **Delivery address description** – The delivery address of the sales order

For items, the following fields are required:

- **Product** – The product to order
- **Quantity** – The quantity of the selected product
- **Unit** – The unit of measure (for example, **ea.** , **kgs** , or **box** )
- **Ship to country/region** – The country/region of delivery
- **Delivery address description** – The delivery address of the order

You must make sure that your Customer portal submits values for each of these fields in one way or another.

If you want to add fields to the page, or remove fields, see [Create or edit quick create forms for a streamlined data entry experience](https://docs.microsoft.com/dynamics365/customerengagement/on-premises/customize/create-edit-quick-create-forms%22HYPERLINK%20https://docs.microsoft.com/dynamics365/customerengagement/on-premises/customize/create-edit-quick-create-forms).

If you want to change how fields are preset and how values are set when the page is saved, see the following information in the Power Apps portals documentation:

- [Prepopulate field](https://docs.microsoft.com/en-us/powerapps/maker/portals/configure/configure-web-form-metadata#prepopulate-field)
- [Set Value On Save](https://docs.microsoft.com/en-us/powerapps/maker/portals/configure/configure-web-form-metadata#set-value-on-save)

## Customize the home page

All the controls in the Customer portal are built-in Power Apps portals controls. You can customize them by following the steps in [Compose a page](https://docs.microsoft.com/powerapps/maker/portals/compose-page%22HYPERLINK%20https://docs.microsoft.com/powerapps/maker/portals/compose-page) in the Power Apps portals documentation.

The only custom control that is included in the Customer portal template is used to create the tiles on the home page.

To modify the tiles, follow these steps.

1. Open the [Portal Management app](https://docs.microsoft.com/en-us/powerapps/maker/portals/configure/configure-portal).
2. In the navigation pane on the left, select **Page Templates**.

1. Select the page template that is named **Home**.
2. In the **Web Template** field, select the **Home** link to open the source code for that page.

1. You should now see all the source code for the home page and can modify it as you require.
