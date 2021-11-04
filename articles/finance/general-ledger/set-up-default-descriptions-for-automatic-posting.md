---
# required metadata

title: Set up default descriptions for automatic posting
description: This topic explains how to set up default text that is used to describe accounting entries that are posted automatically to the general ledger. You can set up default description text by using free-form text or by selecting fixed variables.
author: aprilolson
ms.date: 07/23/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
ms.custom: 222564
ms.assetid: 
ms.search.region: global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2019-07-30
ms.dyn365.ops.version: Version 1611

---

# Set up default descriptions for automatic posting

[!include [banner](../includes/banner.md)]

This topic explains how to set up default text that is used to describe accounting entries that are posted automatically to the general ledger. You can set up default description text by using free-form text or by selecting fixed variables.

> [!NOTE]
> For some transaction types in some countries or regions, you can also include text from fields in the Microsoft Dynamics AX database that are related to those transaction types. For a list of the transaction types, and the countries and regions, see the [Optional: Add other text to default descriptions](#optional-add-other-text-to-default-descriptions) section later in this topic.

## Set up default descriptions

1. Go to **Organization administration** \> **Setup** \> **Default descriptions**.
2. On the Action Pane, select **New**.
3. In the **Description** field, select the type of transaction to create a default description for.
4. In the **Language** field, select the language that the description applies to.
5. In the **Text** field, enter the default description. You can type text in the field, or you can use one or more of the following free-text variables:

    - **%1** – Add the transaction date.
    - **%2** – Add an identifier that corresponds to the document type that is being posted to the general ledger. For example, for transaction types that are related to invoices, the **%2** variable adds the invoice number.
    - **%3** – Add an identifier that is related to the document type that is being posted to the general ledger. For example, for transaction types that are related to invoices, the **%3** variable adds the customer account number.

## Optional: Add other text to default descriptions

For some transaction types in some countries or regions, default descriptions can include text that comes from fields in your data that are related to those transaction types. The following lists show the transaction types, and the countries and regions, that this option is available for.

**Transaction types**

You can add other text to default descriptions for transaction types that are related to the following document types:

- Customer invoices
- Customer credit notes
- Customer cash payments
- Vendor payments
- Sales orders
- Purchase orders
- Inventory journals
- Master planning (MRP)
- Fixed assets

**Countries and regions**

This option is available for the following countries and regions:

- Brazil
- China
- Czech Republic
- Eastern Europe
- Hungary
- India
- Japan
- Lithuania
- Latvia
- Poland
- Russia

### Add text to default descriptions

After you complete the steps in the [Set up default descriptions](#set-up-default-descriptions) section earlier in this topic, follow these steps to add other text to the default descriptions.

1. On the **Parameters** FastTab, select **Add**.
2. In the **Reference table** field, select the database table from which to add parameter data to the description.
3. In the **Reference field** field, select the field from which to add parameter data to the description.
4. Repeat steps 1 through 3 to add more parameters.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]