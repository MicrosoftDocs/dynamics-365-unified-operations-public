---
# required metadata

title: Customer electronic invoices in Egypt
description: This topic explains how to configure and submit customer electronic invoices in Egypt.  
author: Ilya Kondratenko
manager: AnnBe
ms.date: 01/27/2021
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

According to Egyptian legal requirements, invoices issued for customers must be submitted to the Tax authority in an electronic format.
Electronic invoice submission requires the following two-part system configuration:

1. **Electronic invoicing add-on** configuration. For more information, see [Get started with the Electronic invoicing add-on](e-invoicing-get-started.md)
2. **Dynamics 365 Finance** configuration which is covered in this article.

## Prerequisites

- Electronic invoicing add-on configuration is complete and all required parts for Egypt are ready to use.
- In the **Feature management workspace**, turn on the **Electronic invoicing add-on integration** feature. For more information, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Enable electronic invoicing for Egypt
Complete the following steps to enable electronic invoicing for Egypt.

1. Go to **Organization administration** > **Setup** > **Electronic document parameters**.
2. On the **Features** tab, select feature reference for **EG00008 E-invoicing for Egypt**.
3. Turn on **Enabled** option for the selected feature reference.

## Configure registration numbers
Complete the following steps to configure registration numbers.

> [!NOTE]
> If the registration category **Enterprise ID (COID)** already exists and has been assigned to a registration type, skip this procedure.

1. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration types**.
2. Create a new registration type and in the **Country/region** field, select **EGY - Egypt**.
3. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration categories**.
4. Create a new registration category, and in the **Registration types** field, select the registration type you created in step 2.
5. In the **Registration categories** field, select **Enterprise ID (COID)**.

## Configure Electronic document property types
Complete the following steps to configure the electronic document property type required to define the taxpayer activity code.

1. Go to **Accounts receivable** > **Setup** > **Electronic document property types**.
2. Create a new type, and in the **Type** field, enter ***taxpayerActivityCode***.
3. Select **Applicability**, and in the **Table name** field, select **CompanyInfo**. 
5. Save and close the **Electronic document property type applicability setup** page.
6. Save and close the **Electronic document property types** page. 

## Configure legal entity data
### Enter legal entity address

1. Go to **Organization administration** > **Organizations** > **Legal entities**.
2. Select a legal entity and expand the **Addresses** FasTab.
3. Add a valid primary adderess for the legal entity.

### Enter a legal entity branch
1. Go to **Organization administration** > **Organizations** > **Legal entities**.
2. Select a legal entity and expand the **Statutory reporting** FasTab.
3. In the **Branch/Subsidiary** field, enter a branch code for the selected legal entity.

### Enter the legal entity registration number
1. Go to **Organization administration** > **Organizations** > **Legal entities**.
2. Select a legal entity, and then select **Registration IDs**.
3. Expand the **Registration ID** FasTab and then select **Add** to create a new regictration ID.
4. In the **Registration type** column, select the registration type that you created in the **Configure registration numbers** section.
6. In the **Registration number** column, enter a valid legal entity registration number. This number can be obtained from the Tax authority.

### Enter an activity code for a legal entity
1. Go to **Organization administration** > **Organizations** > **Legal entities**.
2. Select a legal entity and then select **Electronic document properties**.
3. Select the line with the value **taxpayerActivityCode** in the **Type** column.
4. In the **Value** column, enter the Taxpayer activity code.

## Configure customer data 
### Enter a customer address

1. Go to **Accounts receivable** > **Customers** > **All customers**.
2. Select a customer and then expand the **Addresses** FasTab.
3. Add a valid adderess for the selected customer.

### Enter the customer registration number
1. Go to **Accounts receivable** > **Customers** > **All customers**.
2. Select a customer, and then select **Registration** > **Registration IDs**.
3. Expand the **Registration ID** FasTab and then select **Add** to create a new regictration ID.
5. In the **Registration type** column, select the registration type that you created in the **Configure registration numbers** section.
6. In the **Registration number** column, enter a valid customer registration number. This number is obtained from the Tax authority.

## Configure sales tax codes
1. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax codes**.
2. Select a sales tax code, and then select **Sales tax code** > **Sales tax code** > **External codes**.
3. In **Overview** section, create a new line for the selected sales tax code.
4. In **Value** section, in **Value** column, enter an external code to use for the selected sales tax code according to the official codification for [Tax Types](https://sdk.sit.invoicing.eta.gov.eg/codes/tax-types/).

5. Go to **Tax** > **Setup** > **Sales tax** > **Sales tax exempt codes**.
6. Define exempt codes that will be used as **Tax subtypes** in case of non-taxable operations.

## Configure unit codes
1. Go to **Organization administration** > **Setup** > **Units** > **Units**.
2. Select a unit and then select **External codes**.
3. In **Overview** section, create a new line.
4. In the **Value** section, in **Value** column, enter an external code which will be used for the selected unit according to the official codification for [Unit Types](https://sdk.sit.invoicing.eta.gov.eg/codes/unit-types/).

## Configure products
According to Egyptian legal requirements, products in electronic invoices must use either GTIN codes or GS1 - Global Product Classification (GPC) level 4 (brick) codes.

### Enter the GTIN number
1. Go to **Product information management** > **Products** > **Released products**.
2. Select a product, and then select **Manage inventory** > **Warehouse** > **GTIN codes**.
3. Enter GTIN codes for the selected products.

### Configure GPC codes
1. Go to **Product information management** > **Setup** > **Categories and attributes** > **Category hierarchies**.
2. Create a new category hierarchy with the name, **GPC**.
3. Create the category nodes to implement 4-levels hierarchy: *Segment* > *Family* > *Class* > *Brick*.
4. At the *Brick* level, in the **Code** field, enter the code which will be appliable to selected products.
5. Expand the **Products** FasTab and select **Add** to add all the products applicable for tohe defined code.

  ![Category hierarchy](media/emea-egy-gpc.jpg)

> [!NOTE]
> If neither the GTIN nor GPC codes are defined for products, internal product numbers will be used. If no products or services are involved in invoicing, for example free text invoices, or various operations in project invoices, then line descriptions will be used in electronic invoices.

## Submit electronic invoices

When all of the required configuration steps are complete, you can submit electronic invoices. For more information how to submit electronic invoices, see [Issue electronic invoices in Finance and Supply chain management](e-invoicing-issuing-electronic-invoices-finance-supply-chain-management.md).

## Related topics

- [Electronic invoicing add-on overview](e-invoicing-service-overview.md)
