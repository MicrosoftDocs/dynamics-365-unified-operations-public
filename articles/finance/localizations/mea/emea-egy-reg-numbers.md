---
title: Configure registration numbers in Egypt
description: Learn how to configure and use registration numbers in Egypt, including an outline and step-by-step process for configuring commerical registration numbers.
author: mrolecki
ms.author: mrolecki
ms.topic: article
ms.date: 09/15/2021
ms.custom: 
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Egypt
ms.search.validFrom: 2021-02-01
ms.dyn365.ops.version: 10.0.17
---

# Configure registration numbers in Egypt

[!include [banner](../../includes/banner.md)]

There are different types of registration numbers that are used in Egypt. This article explains how to configure and use **Commercial registration numbers**, **National numbers**, and **File tax numbers**.

## Prerequisites

The primary address of the legal entity must be in Egypt.

## Configure a commercial registration number

Complete the following steps to configure commercial registration numbers.

1. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration types**.
2. Create a new registration type, and in the **Country/region** field, select **EGY - Egypt**.
3. In **Restricted to** field, select **Organization** value.
4. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration categories**.
5. Create a new registration category, and in the **Registration types** field, select the registration type you created in step 2 for a commercial registration number.
6. In the **Registration categories** field, select **Enterprise ID (COID)**.

## Configure a national number

Complete the following steps to configure national numbers

1. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration types**.
2. Create a new registration type, and in the **Country/region** field, select **EGY - Egypt**.
3. In **Restricted to** field, select **Person**.
4. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration categories**.
5. Create a new registration category, and in the **Registration types** field, select the registration type you created in step 2 for a national number.
6. In the **Registration categories** field, select **Enterprise ID (COID)**.

## Configure a file tax number

Complete the following steps to configure file tax numbers.

1. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration types**.
2. Create a new registration type, and in the **Country/region** field, select **EGY - Egypt**.
3. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration categories**.
4. Create a new registration category, and in the **Registration types** field, select the registration type you created in step 2 for a tax file number.
5. In the **Registration categories** field, select **VAT ID**.

## Enter registration numbers

After you configure the registration numbers, you can use them for legal entities, customers, and vendors.

### Enter legal entity registration numbers

1. Go to **Organization administration** > **Organizations** > **Legal entities**.
2. Select a legal entity, and then select **Registration IDs**.
3. Expand the **Registration ID** FastTab and then select **Add**.
4. In the **Registration type** column, select a registration type.
5. In the **Registration number** column, enter a valid legal entity registration number.

  > [!NOTE]
  > Repeat steps 1 -5 if you need to enter more than one registration number for the legal entity.

### Enter a customer registration number

1. Go to **Accounts receivable** > **Customers** > **All customers**.
2. Select a customer, and then select **Registration** > **Registration IDs**.
3. Expand the **Registration ID** FastTab and then select **Add**.
5. In the **Registration type** column, select a registration type.
6. In the **Registration number** column, enter a valid customer registration number.

### Enter a vendor registration number

1. Go to **Accounts payable** > **Vendors** > **All vendors**.
2. Select a vendor, and then select **Registration** > **Registration IDs**.
3. Expand the **Registration ID** FastTab and then select **Add**.
5. In the **Registration type** column, select a registration type.
6. In the **Registration number** column, enter a valid vendor registration number.


## Additional resources

- [Registration IDs](../europe/emea-registration-ids.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
