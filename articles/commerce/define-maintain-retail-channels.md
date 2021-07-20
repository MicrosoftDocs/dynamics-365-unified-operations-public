---
# required metadata

title: Define and maintain retail channels
description: This topic provides an overview of the process for setting up brick-and-mortar stores, which are referred to as stores in Dynamics 365 Commerce. It includes information about the tasks that you must complete both before and after you set up a store.
author: mugunthanm
ms.date: 01/06/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: RetailStoreTable, RetailStoreTableListPagePreviewPane
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 16481
ms.assetid: 14496d96-1c72-43ce-a2e7-8467bab4ae46
ms.search.region: Global
ms.search.industry: Retail
ms.author: mumani
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update

---

# Define and maintain retail channels

[!include [banner](includes/banner.md)]

This topic provides an overview of the process for setting up brick-and-mortar stores, which are referred to as stores in Dynamics 365 Commerce. It includes information about the tasks that you must complete both before and after you set up a store.

Commerce supports multiple channels, such as online stores, call centers, and brick-and-mortar stores. A brick-and-mortar store is called a store. Each store can have its own payment methods, price groups, point of sale (POS) registers, income accounts and expense accounts, and staff. You must set up all these elements for a store before you create it. After you create the store, you assign the products that you want it to carry. You also assign employees, registers, and customers to the store. Finally, you add the new store to an organization hierarchy.

## Setting up stores

Before you can set up a store in Commerce, you must complete some prerequisite tasks. You can then create the store and add details.

### Prerequisites

You must complete the following tasks before you can set up a store:

1. Configure your organization structure, and set up organization hierarchies for retail assortments, replenishment, and reporting.
2. Set up a warehouse that represents the store.
3. Set up number sequences for stores, store statements, and statement vouchers.
4. Configure parameters for Commerce.
5. Set up the methods of payment that the store accepts.
6. To process credit card transactions at POS registers, you can also set up payment services.
7. Set up sales tax groups.
8. Set up products. As part of this task, you also set up product hierarchies, product variants, and product assortments.
9. Set up product price groups.
10. Set up product pricing. As part of this task, you also set up price adjustments, discounts, and discount periods.
11. Set up staff members.

    > [!NOTE]
    > You must also assign appropriate permissions to the workers, so that they can sign in and perform tasks by using the POS system.

12. Configure the POS profiles to assign to the store. This task includes many other tasks, such as setting up registers, setting up offline profiles, and setting up receipt formats and profiles.

Review all the tasks that are included in the prerequisites, and complete only the tasks that apply to you.

### Set up a store

After you complete the prerequisite tasks, complete these tasks to set up the details for the store:

1. Create a store.
2. Assign a sales tax group to the store.
3. Assign the accepted payment methods to the store.
4. Add details to the product descriptions for products that you offer in your stores. For example, you can add rich text and images. These product details appear in various contexts, such as on the POS register or on printed labels.
5. Add the store to the default organization hierarchy that is assigned to a purpose of **Retail assortment**, **Retail replenishment**, or **Retail reporting**.

### After you set up a store

After you enter the details for the store, complete these tasks to send the new store data to POS:

1. Configure the POS registers for the store.
2. Assign product assortments to the store.
3. Process assortments to generate the list of products that are included in the assortment and to make the products available in the store.
4. Send data such as number sequences, hardware profiles, and POS screen layouts to the POS registers.
5. Publish the store to send store data to POS.
6. Run the jobs to send the store data to POS.

## Organization hierarchies

Commerce uses organization hierarchies to structure channels. Organization hierarchies represent the relationships between the organizations that make up your business. When you set up stores, you can add them to an organization hierarchy. The stores then share data that is used for assortments, replenishment, and reporting.

> [!NOTE]
> To use Commerce sales functionality, the configuration key for **Multiple ship-to** must be enabled. This configuration key can be found in the **Trade configuration** keys under **System Administration**\> **Setup** \> **License Configuration**. This is required due to various validations based on the delivery address configured at the sales order line level.



[!INCLUDE[footer-include](../includes/footer-banner.md)]