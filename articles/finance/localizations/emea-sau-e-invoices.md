---
# required metadata

title: Customer electronic invoices in Saudi Arabia
description: This topic explains how to configure and submit customer electronic invoices in Saudi Arabia.
author: ikondo
ms.date: 10/26/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 574540
ms.search.region: Saudi Arabia
# ms.search.industry: 
ms.author: ilyako
ms.search.validFrom: 2021-10-15
ms.dyn365.ops.version: 10.0.21

---

# Customer electronic invoices in Saudi Arabia

[!include [banner](../includes/banner.md)]


According to Saudi Arabiaian legal requirements, invoices that are issued to customers must be generated in an electronic format. To generate electronic invoices, the following two-part system configuration is required.

- **Electronic invoicing service** configuration. For more information, see [Get started with the Electronic invoicing add-in for Saudi Arabia](e-invoicing-sa-get-started.md).
- **Dynamics 365 Finance** configuration, which is covered in this topic.

## Prerequisites

- Electronic invoicing service configuration is complete, and all required parts for Saudi Arabia are ready to use.
- The primary address of the legal entity must be in Saudi Arabia.
- In the **Feature management** workspace, enable the feature, **(Saudi Arabia) QR codes in Tax and Simplified invoices**. For more information, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Configure registration numbers

If the **Enterprise ID (COID)** registration category already exists and has been assigned to a registration type, you can skip this procedure.

1. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration types**.
2. Create a registration type.
3. In the **Country/region** field, select **SAU - Saudi Arabia**.
4. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration categories**.
5. Create a registration category.
6. In the **Registration types** field, select the registration type that you created in step 2.
7. In the **Registration categories** field, select **Enterprise ID (COID)**.

## Configure legal entity data

### Enter a legal entity address

1. Go to **Organization administration** > **Organizations** > **Legal entities**.
2. Select a legal entity and on the the **Addresses** FastTab, add a valid primary address for the selected legal entity.

### Enter the legal entity tax registration number

1. Go to **Organization administration** > **Organizations** > **Legal entities**.
2. Select a legal entity, and then expand **Tax registration** FastTab.
3. In the **Tax registration number** field, enter a valid legal entity tax registration number. This number will be then used as seller's VAT identifier.

### Enter the legal entity commercial registration number

1. Go to **Organization administration** > **Organizations** > **Legal entities**.
2. Select a legal entity, and on the Action Pane, select **Registration IDs**.
3. On the **Registration ID** FastTab, select **Add** to create a registration ID.
4. In the **Registration type** field, select the registration type that you created earlier.
6. In the **Registration number** field, enter a valid legal entity registration number. This number will be used as the seller's commercial registration identifier.

## Configure customer data

### Enter a customer address

1. Go to **Accounts receivable** > **Customers** > **All customers**.
2. Select a customer and on the **Addresses** FastTab, add a valid address.

### Enter the customer tax registration number

1. Go to **Accounts receivable** > **Customers** > **All customers**.
2. Select a customer, and then expand the **Invoice and delivery** FastTab.
3. In the **Tax exempt number** field, enter a valid customer tax registration number. This number will be used as buyer's VAT identifier.

### Enter the customer registration number

1. Go to **Accounts receivable** > **Customers** > **All customers**.
2. Select a customer, and on the Action Pane, on the **Customer** tab, in the **Registration** group, select **Registration IDs**.
3. On the **Registration ID** FastTab, select **Add** to create a registration ID.
5. In the **Registration type** field, select the registration type that you created earlier.
6. In the **Registration number** field, enter a valid customer registration number. This number will be used as the buyer's commercial registration identifier.

## Configure sales tax codes

1. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax codes**.
2. Select a sales tax code, and on the Action Pane, on the **Sales tax code** tab, in the **Sales tax code** group, select **External codes**.
3. In **Overview** section, create a line for the selected sales tax code.
4. In **Value** section, in **Value** field, enter an external code to use for the selected sales tax code, according to the official codification.

## Configure unit codes

1. Go to **Organization administration** > **Setup** > **Units** > **Units**.
2. Select a unit, and on the Action Pane, select **External codes**.
3. In **Overview** section, create a line for the selected unit.
4. In the **Value** section, in **Value** field, enter an external code to use for the selected unit, according to the official codification.

## Enter product codes

1. Go to **Product information management** > **Products** > **Released products**.
2. Select a product, and on the Action Pane, on the **Manage inventory** tab, in the **Warehouse** group, select **GTIN codes**.
3. Enter the GTIN code for the selected product. This code will be used as a standard product identifier.
4. On the Action Pane, on the **Sell** tab, in the **Related information** group, select **External item desription**.
5. In **External item number** field, enter a customer-specific code for the selected product. This code will be used as the buyer's product identifier.

> [!NOTE]
> By default, internal item numbers that are defined in the system will be used as the seller's product identifiers.

## Define the invoice type

You can define an invoice type as a **Tax invoice** or a **Simplified invoice**.

1. Go to **Accounts receivable** > **Orders** > **All sales orders**.
2. Create a new sales order or select an open order and navigate to the order header.
3. On the **General** FastTab, in the **Status** group, in the **Invoice type** field, select a required value.

Similarly, the invoice type can be defined for free text invoices.

1. Go to **Accounts receivable** > **Invoices** > **All free text invoices**.
2. Create a new free text invoice or select an open free text invoice and navigate to the invoice header.
3. On the **General** FastTab, in the **Invoice** group, in the **Invoice type** field, select a required value.

## Configure printable invoice layouts

### Enable specific invoice layouts for Saudi Arabia 

1. Go to **Accounts receivable** > **Setup** > **Forms** > **Form setup**.
2. Select **Print management**.
3. Select the **Customer invoice** report and then refer to the **SalesInvoice.Report_SA** layout in the **Report format** field.
4. Select the **Free text invoice** report and then refer to the **FreeTextInvoice.Report_SA** layout in the **Report format** field.

### Enable VAT numbers prining on invoices 

1. Go to **Accounts receivable** > **Setup** > **Forms** > **Form setup**.
2. In the **Invoice** section, turn on the **Print tax exempt number on invoice** option.
3. In the **Free text invoice** section, turn on the **Print tax exempt number on invoice** option.
4. Go to **Project management and accounting** > **Setup** > **Forms** > **Form setup**.
5. In **Invoice** section, turn on the **Print tax exempt number on invoice** option.


## Print invoices

When printing customer invoices based on sales orders or free text invoices, the title of an invoice reflects the type, **Tax invoice** or **Simplified invoice**.
Additionally, QR codes are printed.

![Invoice printout](media/sau-qr-invoice.jpg)

## Issue electronic invoices

When you've completed all the required configuration steps, you can generate electronic invoices for posted invoices. For more information about how to generate electronic invoices, see [Issue electronic invoices in Finance and Supply chain management](e-invoicing-issuing-electronic-invoices-finance-supply-chain-management.md).

## Related topics

- [Get started with the Electronic invoicing add-in for Saudi Arabia](e-invoicing-sa-get-started.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
