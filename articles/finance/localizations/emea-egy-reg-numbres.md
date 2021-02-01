---
# required metadata

title: Configure registration numbers in Egypt
description: This topic explanis how to configure and use registration numbers in Egypt. 
author: ilkond
manager: AnnBe
ms.date: 02/01/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Egypt
# ms.search.industry: 
ms.author: roschlom
ms.search.validFrom: 2021-02-01
ms.dyn365.ops.version: 10.0.17

---

# Configure registration numbers in Egypt

[!include [banner](../includes/banner.md)]

There are different types of registration numbers used in Egypt.
This topic explanis how to configure and use **Commercial registration number**, **National number** and **File tax number**.

## Prerequisites

- The primary address of the legal entity must be in Egypt.

## Configure commercial registration number

Complete the following steps to configure commercial registration number.
1. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration types**.
2. Create a new registration type and in the **Country/region** field, select **EGY - Egypt**.
3. In **Restricted to** field, select **Organization** value.
4. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration categories**.
5. Create a new registration category, and in the **Registration types** field, select the registration type you created in step 2 for commercial registration number.
6. In the **Registration categories** field, select **Enterprise ID (COID)**.

## Configure National number

Complete the following steps to configure national number.
1. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration types**.
2. Create a new registration type and in the **Country/region** field, select **EGY - Egypt**.
3. In **Restricted to** field, select **Person** value.
4. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration categories**.
5. Create a new registration category, and in the **Registration types** field, select the registration type you created in step 2 for national number.
6. In the **Registration categories** field, select **Enterprise ID (COID)**.

## File tax number

Complete the following steps to configure file tax number.
1. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration types**.
2. Create a new registration type and in the **Country/region** field, select **EGY - Egypt**.
3. In **Restricted to** field, select **Person** value.
4. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration categories**.
5. Create a new registration category, and in the **Registration types** field, select the registration type you created in step 2 for tax file number.
6. In the **Registration categories** field, select **VAT ID**.
