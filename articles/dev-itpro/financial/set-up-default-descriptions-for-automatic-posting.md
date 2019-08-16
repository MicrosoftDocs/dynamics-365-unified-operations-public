---
# required metadata

title: Set up default descriptions for automatic posting
description: This topic explains how to set up default text that is used to describe accounting entries that are posted automatically to the general ledger. You can set up default description text by using freeform text or by selecting fixed variables.
author: aprilolson
manager: AnnBe
ms.date: 07/23/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
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

This topic explains how to set up default text that is used to describe accounting entries that are posted automatically to the general ledger. You can set up default description text by using freeform text or by selecting fixed variables.

> [!NOTE]
> <P>For certain transaction types in some countries/regions, you can also include text from fields in the Microsoft Dynamics AX database that are related to those transaction types. These transaction types and countries/regions are listed in Optional: Add other text to default descriptions, later in this topic.</P>



## Set up default descriptions

1.  Click **Organization administration** \> **Setup** \> **Default descriptions**.

2.  On the menu bar, click **New**.

3.  In the **Description** field, select the type of transaction to create a default description for.

4.  In the **Language** field, select the language that this description applies to.

5.  In the **Text** field, enter the default description. You can type text in the field, or you can use one or more of the following free text variables:
    
      - %1 – Add the transaction date.
    
      - %2 – Add an identifier that corresponds to the document type that is being posted to the general ledger. For example, for transaction types that are related to invoices, the %2 variable adds the invoice number.
    
      - %3 – Add an identifier that is related to the document type that is being posted to the general ledger. For example, for transaction types that are related to invoices, the %3 variable adds the customer account number.

## Optional: Add other text to default descriptions

For certain transactions types in some countries/regions, you can include text in your default descriptions that come from fields in your data that are related to those transaction types. The following lists show the transaction types and countries/regions for which this option is available.

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

**Countries/regions**

This option is available for the following countries/regions:

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

**Add text to default descriptions**

After you complete the steps in Set up default descriptions, earlier in this topic, follow these steps to add other text to the default descriptions:

1.  In the **Parameters** area, click **Add**.

2.  In the **Reference table** field, select the database table from which to add parameter data to the description.

3.  In the **Reference field** field, select the field from which to add parameter data to the description.

4.  Repeat steps 1 through 3 to add more parameters.



  
