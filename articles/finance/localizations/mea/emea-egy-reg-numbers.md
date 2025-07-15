---
title: Configure registration numbers in Egypt
description: Learn how to configure and use registration numbers for Egypt in Microsoft Dynamics 365 Finance.
author: mrolecki
ms.author: mrolecki
ms.topic: how-to
ms.date: 06/05/2025
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Egypt
ms.search.validFrom: 2021-02-01
ms.custom: 
  - bap-template
---

# Configure registration numbers in Egypt

[!include [banner](../../includes/banner.md)]

This article explains how to configure and use registration numbers for Egypt in Microsoft Dynamics 365 Finance.

There are different types of registration numbers that are used in Egypt. This article explains how to configure and use **Commercial registration numbers**, **National numbers**, and **File tax numbers**.

## Prerequisites

The primary address of the legal entity must be in Egypt.

## Configure a commercial registration number

To configure a commercial registration number, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration** \> **Global address book** \> **Registration types** \> **Registration types**.
1. Create a new registration type, and in the **Country/region** field, select **EGY - Egypt**.
1. In **Restricted to** field, select **Organization** value.
1. Go to **Organization administration** \> **Global address book** \> **Registration types** \> **Registration categories**.
1. Create a new registration category, and in the **Registration types** field, select the registration type you created in step 2 for a commercial registration number.
1. In the **Registration categories** field, select **Enterprise ID (COID)**.

## Configure a national number

To configure a national number, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration** \> **Global address book** \> **Registration types** \> **Registration types**.
1. Create a new registration type, and in the **Country/region** field, select **EGY - Egypt**.
1. In **Restricted to** field, select **Person**.
1. Go to **Organization administration** \> **Global address book** \> **Registration types** \> **Registration categories**.
1. Create a new registration category, and in the **Registration types** field, select the registration type you created in step 2 for a national number.
1. In the **Registration categories** field, select **Enterprise ID (COID)**.

## Configure a file tax number

To configure a file tax number, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration** \> **Global address book** \> **Registration types** \> **Registration types**.
1. Create a new registration type, and in the **Country/region** field, select **EGY - Egypt**.
1. Go to **Organization administration** \> **Global address book** \> **Registration types** \> **Registration categories**.
1. Create a new registration category, and in the **Registration types** field, select the registration type you created in step 2 for a tax file number.
1. In the **Registration categories** field, select **VAT ID**.

## Enter registration numbers

After you configure the registration numbers, you can use them for legal entities, customers, and vendors.

### Enter legal entity registration numbers

To enter legal entity registration numbers, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration** \> **Organizations** \> **Legal entities**.
1. Select a legal entity, and then select **Registration IDs**.
1. Expand the **Registration ID** FastTab and then select **Add**.
1. In the **Registration type** column, select a registration type.
1. In the **Registration number** column, enter a valid legal entity registration number.

  > [!NOTE]
  > Repeat steps 1 -5 if you need to enter more than one registration number for the legal entity.

### Enter a customer registration number

To enter a customer registration number, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts receivable** \> **Customers** \> **All customers**.
1. Select a customer, and then select **Registration** \> **Registration IDs**.
1. Expand the **Registration ID** FastTab and then select **Add**.
1. In the **Registration type** column, select a registration type.
1. In the **Registration number** column, enter a valid customer registration number.

### Enter a vendor registration number

To enter a vendor registration number, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts payable** \> **Vendors** \> **All vendors**.
1. Select a vendor, and then select **Registration** \> **Registration IDs**.
1. Expand the **Registration ID** FastTab and then select **Add**.
1. In the **Registration type** column, select a registration type.
1. In the **Registration number** column, enter a valid vendor registration number.


## Additional resources

- [Registration IDs](../europe/emea-registration-ids.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
