---
# required metadata

title: Default customer
description: This topic presents an overview of how to create a default customer in Microsoft Dynamics 365 Commerce for use when creating a channel.
author: samjarawan
manager: annbe
ms.date: 01/20/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2020-01-20
ms.dyn365.ops.version: Release 10.0.8

---
# Default customer

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic presents an overview of how to create a default customer in Microsoft Dynamics 365 Commerce for use when creating a channel.

## Overview

When creating a retail or online channel, you will need to provide a default customer.  Default customers can easily be created following the below steps including prerequisites of creating a customer group and a customer address book.

## Create a customer group

If no customer groups exist yet, you can create one. Examples may be groups to represent different customer groups such as wholesale, retail, Internet, Employees, ...

1. Go to **Navigation pane** > **Modules** > **Retail** > **Customers** > **Customer groups**.
1. On the **Action pane**, click **New**.
1. In the **Customer group**, provide an ID.
1. In the **Description** field, provide a descriptive description.
1. Select an appropriate **Terms of payment** for the customer group and **Time between invoice due date and payment date**.
1. Select a **Default tax group** if applicable.
1. Select **Prices include sales tax** if applicable.
1. Select a **Default write-off reason** if applicable.

The following image shows several configured customer groups.

![Customer groups](media/customer-groups.png)

## Create a customer address book

A customer needs to be associated with an address book, if one is not created then follow these steps to create one.

1. Go to **Navigation pane** > **Modules** > **Retail** > **Channel setup** > **Address Books**.
1. On the **Action pane**, click **New**.
1. In the **Name** field, provide a name.
1. In the **Description** field, provide a description.

The following image shows an example address book.

![Address book](media/address-book.png)

## Create a customer

1. Go to **Navigation pane** > **Modules** > **Retail** > **Customers** > **All customers**.
1. On the **Action pane**, click **New**.
1. In the **Type** field, select "Person".
1. In the **Customer account** field, provide an account number. "100001" is used in the example below.
1. In the **First name** field, provide a name such as "Default" used in the example below.
1. In the **Middle name** field, provide a name such as "Retail" used in the example below.
1. In the **Last name** field, provide a name such as "Customer" used in the example below.
1. In the **Currency** field, provide a currency such as "USD".
1. Select an appropriate **Customer group** created in the previous section.
1. An address is not necessary for a default customer.
1. Select a pre-configured customer **Address book**.
1. Click the **Save** button to get back to the customer details for the new customer.

The following image shows an example of customer creation.

![Default customer creation](media/default-customer-creation.png)

The following image shows a default customer configuration.

![Sample customer configuration](media/default-customer-configuration1.png)

Most of the defaults for the customer can remain however there are some others that should be changed.
1. Expand the **Sales order defaults**
  1. Select the **Site** drop down and select a pre-configured site.
  1. Select the **Warehouse** drop down and select a pre-configured warehouse.

The following image shows an example customer configuration.

![Example customer configuration](media/default-customer-configuration2.png)

## Additional resources


