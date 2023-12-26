--- 
# required metadata 
 
title: FR-00003 NAF codes and Siret numbers
description: This article explains how to create and enter NAF codes for legal entities, customers, vendors, and prospects. 
author: EvgenyPopovMBS
ms.date: 09/10/2021
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: CompanyNAFCode, CustTable, VendTable, smmBusRelTable, OMLegalEntity   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: France
# ms.search.industry: 
ms.author: epopov
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# FR-00003 NAF codes and Siret numbers

[!include [banner](../../includes/banner.md)]

This article explains how to create NAF codes and then enter the codes for legal entities, customers, vendors, and prospects. NAF codes are used to identify the business of an enterprise. For example, if your legal entity manufactures computers, the NAF code for your legal entity may be 300C, which is the NAF code for manufacturing computers and other computer hardware. If your legal entity is involved in building houses, your NAF code may be 452A.

This article also shows how to enter siret numbers for customers, vendors, and prospects. The siret is a 14-digit number that identifies a business, a branch of the business, and a person who is associated with the business activity. You can use the siret number to verify that an enterprise is correctly registered and authorized to do business with you.

This procedure was created using the demo data company FRSI. This functionality is available for legal entities whose primary address is in France.


## Set up a NAF code
1. Go to **Organization administration** > **Global address book** > **Addresses** > **NAF codes**.
2. Select **New**.
3. In the **NAF code** field, type a value.
4. In the **Description** field, type a value.
5. Select **Save**.

## Enter a NAF code and a siret number for a customer
1. Go to **Accounts receivable** > **Customers** > **All customers**.
2. Select the customer record that you want to update.
3. Expand the **Sales demographics** section.
4. Select **Edit**.
5. In the **French Siret** field, type a value.
6. In the **NAF code** field, enter or select a value.
7. Select **Save**.

## Enter a NAF code and a siret number for a vendor
1. Go to **Accounts payable** > **Vendors** > **All vendors**.
2. Select the vendor record that you want to update.
3. Expand the **Purchasing demographics** section.
4. Select **Edit**.
5. In the **French Siret** field, type a value.
6. In the **NAF code** field, enter or select a value.
7. Select **Save**.

## Enter a NAF code and a siret number for a prospect
1. Go to **Sales and marketing** > **Relationships** > **Prospects** > **All prospects**.
2. In the list, find and select the prospect record that you want to update.
3. Expand the **Sales demographics** section.
4. Select **Edit**.
5. In the **French Siret** field, type a value.
6. In the **NAF code** field, enter or select a value.
7. Select **Save**.

## Set up commerce registration, a legal form, a NAF code, and a Siret number for a legal entity
1. Go to **Organization administration** > **Organizations** > **Legal entities**.
2. Expand the **Registration numbers** section.
3. Select **Edit**.
4. In the **Commerce registration** field, type a value. Enter the name of the French agency where the legal entity is registered, such as the Registre du commerce et des sociétés.  
5. In the **NAF code field**, enter or select a value.
6. In the **Legal form** field, type a value. Enter the legal type of the legal entity, such as non-profit organization, manufacturing company, or financial institution.  
7. Select **Save**.
8. Expand the **Tax registration** section.
9. In the **Tax registration** field enter a Siret number of the legal entity.
10. Select **Save**. 



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
