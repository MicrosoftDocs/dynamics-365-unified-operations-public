---
# required metadata

title: Customer electronic invoices in Egypt
description: This topic explains how to configure and submit customer electronic invoices in Egypt.  
author: Ilya Kondratenko
manager: AnnBe
ms.date: 01/22/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 547940
ms.search.region: Egypt
# ms.search.industry: 
ms.author: ilyako
ms.search.validFrom: 2021-02-01
ms.dyn365.ops.version: 10.0.17

---

# Customer electronic invoices in Egypt

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

According to Egyptian legal requirements, the invoices issued for customers must be submitted to the Tax authority in an electronic format.
The submission requires the system configuration which consists of 2 parts:
1. **Electronic invoicing add-on** configuration. Please refer to this article for details: [Get started with the Electronic invoicing add-on service administration](e-invoicing-get-started-service-administration.md)
2. **Microsoft Dynamics 365 Finance** configuration which is covered in this article.

## Prerequisites

In the Feature management workspace, turn on the **Electronic invoicing add-on integration** feature. For more information, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Enable electronic invoicing for Egypt
Complete the following steps to nable electronic invoicing for Egypt.

1. Go to **Organization administration** > **Setup** > **Electronic document parameters** 
2. On the **Features** tab, select feature reference for **EG00008 E-invoicing for Egypt** 
3. Turn on **Enabled** option for the selected feature reference.

## Configure registration numbers
Complete the following steps to configure registration numbers.

1. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration types**.
2. Create a new **Registration type** with **Country/region** assigned to **EGY - Egypt**.
3. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration categories**.
4. Create a new **Registration category**, in the **Registration types** field make the reference to registration type created in point 2.
5. In the **Registration categories** field, select **Enterprise ID (COID)** value.
> [!NOTE]
> If registration type with **Enterprise ID (COID)** registration category already exists, then you can skip points 1 - 5 above.

## Configure Electronic document property types
Complete the following steps to configure Electronic document property type reqiored for Taxpayer activity code definition.

1. Go to **Accounts receivable** > **Setup** > **Electronic document property types**.
2. Create a new type and enter ***taxpayerActivityCode*** value in the **Type** field.
3. Go to the **Applicability** menu item.
4. Select the **CompanyInfo** value in the **Table name** field. 
5. Save and close the **Electronic document property type applicability setup** form.
6. Save and close the **Electronic document property types** form. 

## Configure Legal entity data
### Enter Legal entity address
### Enter Legal entity branch
### Enter Legal entity registration number
### Configure Legal entity activity code

## Configure Customers data 

## Configure Sales tax codes

## Configure Unit codes

## Configure Products
### Enter GTIN number
### Configure GPC codes

> [!NOTE]
> For some countries, .
