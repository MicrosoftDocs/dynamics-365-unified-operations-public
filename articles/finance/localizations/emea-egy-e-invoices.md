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
The submission of electronic invoices requires the system configuration which consists of 2 parts:
1. **Electronic invoicing add-on** configuration. Please refer to this article for details: [Get started with the Electronic invoicing add-on](e-invoicing-get-started.md)
2. **Microsoft Dynamics 365 Finance** configuration which is covered in this article.

## Prerequisites

- **Electronic invoicing add-on** configuration is completed and all its parts required for Egypt are ready to use.
- In the Feature management workspace, turn on the **Electronic invoicing add-on integration** feature. For more information, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Enable electronic invoicing for Egypt
Complete the following steps to enable electronic invoicing for Egypt.

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
1. Go to **Organization administration** > **Organizations** > **Legal entities**.
2. Expand the **Addresses** FasTab for the selected Legal entity.
3. Add a valid primary adderess for the selected Legal entity.

### Enter Legal entity branch
1. Go to **Organization administration** > **Organizations** > **Legal entities**.
2. Expand the **Statutory reporting** FasTab for the selected Legal entity.
3. In the **Branch/Subsidiary** field, enter a branch code for the selected Legal entity.

### Enter Legal entity registration number
1. Go to **Organization administration** > **Organizations** > **Legal entities**.
2. Go to the **Registration IDs** menu item for the selected Legal entity.
3. Expand the **Registration ID** FasTab for the selected address.
4. Click on the **Add** buttom to create a new regictration ID.
5. In the **Registration type** column, select the registration type previously created in **Configure registration numbers** step.
6. In the **Registration number** column, enter a valid Legal entity registration number obtained from the Tax authority.

### Enter Legal entity activity code
1. Go to **Organization administration** > **Organizations** > **Legal entities**.
2. Go to the **Electronic document properties** menu item for the selected Legal entity.
3. Select the line with **taxpayerActivityCode** value in the **Type** column.
4. In the **Value** column, enter Taxpayer activity code.

## Configure Customers data 
### Enter Customer address
1. Go to **Accounts receivable** > **Customers** > **All customers**.
2. Select a customer and expand the **Addresses** FasTab for the selected customer.
3. Add a valid adderess for the selected customer.

### Enter Customer registration number
1. Go to **Accounts receivable** > **Customers** > **All customers**.
2. Go to the **REGISTRATION** > **Registration IDs** menu item for the selected customer.
3. Expand the **Registration ID** FasTab for the selected address.
4. Click on the **Add** buttom to create a new regictration ID.
5. In the **Registration type** column, select the registration type previously created in **Configure registration numbers** step.
6. In the **Registration number** column, enter a valid customer registration number obtained from the Tax authority.

## Configure Sales tax codes
1. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax codes**.
2. Go to the **Sales tax code** > **SALES TAX CODE** > **External codes** menu item for the selected tax code.
3. In **Overview** section, create a new line for the selected sales tax code.
4. In **Value** section, in **Value** column, enter an external code which will be used for the selected sales tax code according to the official codification for [Tax Types](https://sdk.sit.invoicing.eta.gov.eg/codes/tax-types/).

1. Go to **Tax** > **Setup** > **Sales tax** > **Sales tax exempt codes**.
2. Define exempt codes that will be used as **Tax Subtypes** in case of non-taxable operations.

## Configure Unit codes
1. Go to **Organization administration** > **Setup** > **Units** > **Units**.
2. Go to the **External codes** menu item for the selected unit.
3. In **Overview** section, create a new line for the selected unit.
4. In **Value** section, in **Value** column, enter an external code which will be used for the selected unit according to the official codification for [Unit Types](https://sdk.sit.invoicing.eta.gov.eg/codes/unit-types/).

## Configure Products
According to Egyptian legal requirements, products in electronic invoices must use either GTIN codes or GPC level 4 (brick level) codes.

### Enter GTIN number
1. Go to **Product information management** > **Products** > **Released products**.
2. Go to the **Manage inventory** > **WAREHOUSE** > **GTIN codes** menu item for the selected product.
3. Enter GTIN codes for the selected products.

### Configure GPC codes
1. Go to **Product information management** > **Setup** > **Categories and attributes** > **Category hierarchies**.
2. Create a new category hierarchy with **GPC** name.
3. Create the category nodes which implement 4-levels hierarchy: *Segment* > *Family* > *Class* > *Brick*
4. At *Brick* level, in the **Code** field, enter the code which will be appliable to selected products.
5. Expand the **Products** FasTab
6. **Add** all the products applicable for the defined code.

![Category hierarchy](media/emea-egy-gpc.jpg)

> [!NOTE]
> If neither GTIN nor GPC codes are defined for products then internal product numbers will be used. If no products or services are involved in invoicing (like for free text invoices, for example, or various operations in project invoices) then lines descriptions will be used in electronic invoices.

## Submit electronic invoices

When all the required configuration steps are completed, you can submit electronic invoices. For more information how to submit electronic invoices, see [Issue electronic invoices in Finance and Supply chain management](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/e-invoicing-GA-docs/articles/finance/localizations/e-invoicing-issuing-electronic-invoices-in-finance-and-supply-chain-management.md).

## Related topics

- [Electronic invoicing add-on overview](e-invoicing-service-overview.md)
