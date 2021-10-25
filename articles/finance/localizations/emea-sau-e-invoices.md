---
# required metadata

title: Customer electronic invoices in Saudi Arabia
description: This topic explains how to configure and submit customer electronic invoices in Saudi Arabia.
author: ikondo
ms.date: 09/07/2021
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


According to Saudi Arabiaian legal requirements, invoices that are issued to customers must be generated in an electronic format. Electronic invoices generation requires the following two-part system configuration:

1. **Electronic invoicing service** configuration. For more information, see [Get started with the Electronic invoicing add-in for Saudi Arabia](e-invoicing-sa-get-started.md).
2. **Microsoft Dynamics 365 Finance** configuration, which is covered in this topic.

## Prerequisites

- Electronic invoicing service configuration is completed, and all required parts for Saudi Arabia are ready to use.
- The primary address of the legal entity must be in Saudi Arabia.
- In the **Feature management** workspace, turn on the **(Saudi Arabia) QR codes in Tax and Simplified invoices** feature. For more information, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Configure registration numbers

> [!NOTE]
> If the **Enterprise ID (COID)** registration category already exists and has been assigned to a registration type, skip this procedure.

1. Go to **Organization administration** \> **Global address book** \> **Registration types** \> **Registration types**.
2. Create a registration type.
3. In the **Country/region** field, select **SAU - Saudi Arabia**.
4. Go to **Organization administration** \> **Global address book** \> **Registration types** \> **Registration categories**.
5. Create a registration category.
6. In the **Registration types** field, select the registration type that you created in step 2.
7. In the **Registration categories** field, select **Enterprise ID (COID)**.

## Configure legal entity data

### Enter a legal entity address

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
2. Select a legal entity.
3. On the **Addresses** FastTab, add a valid primary address for the selected legal entity.

### Enter the legal entity tax registration number

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
2. Select a legal entity, and then, expand **Tax registration** FastTab.
3. In the **Tax registration number** field, enter a valid legal entity tax registration number. This number will be then used as Seller's VAT identifier.

### Enter the legal entity commercial registration number

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
2. Select a legal entity, and then, on the Action Pane, select **Registration IDs**.
3. On the **Registration ID** FastTab, select **Add** to create a registration ID.
4. In the **Registration type** field, select the registration type that you created in the [Configure registration numbers](#configure-registration-numbers) section earlier in this topic.
6. In the **Registration number** field, enter a valid legal entity registration number. This number will be then used as Seller's commercial registration identifier.

## Configure customer data

### Enter a customer address

1. Go to **Accounts receivable** \> **Customers** \> **All customers**.
2. Select a customer.
3. On the **Addresses** FastTab, add a valid address for the selected customer.

### Enter the customer tax registration number

1. Go to **Accounts receivable** \> **Customers** \> **All customers**.
2. Select a customer, and then, expand **Invoice and delivery** FastTab.
3. In the **Tax exempt number** field, enter a valid customer tax registration number. This number will be then used as Buyer's VAT identifier.

### Enter the customer registration number

1. Go to **Accounts receivable** \> **Customers** \> **All customers**.
2. Select a customer, and then, on the Action Pane, on the **Customer** tab, in the **Registration** group, select **Registration IDs**.
3. On the **Registration ID** FastTab, select **Add** to create a registration ID.
5. In the **Registration type** field, select the registration type that you created in the [Configure registration numbers](#configure-registration-numbers) section earlier in this topic.
6. In the **Registration number** field, enter a valid customer registration number. This number will be then used as Buyer's commercial registration identifier.

## Configure sales tax codes

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax codes**.
2. Select a sales tax code, and then, on the Action Pane, on the **Sales tax code** tab, in the **Sales tax code** group, select **External codes**.
3. In **Overview** section, create a line for the selected sales tax code.
4. In **Value** section, in **Value** field, enter an external code to use for the selected sales tax code, according to the official codification.

## Configure unit codes

1. Go to **Organization administration** \> **Setup** \> **Units** \> **Units**.
2. Select a unit, and then, on the Action Pane, select **External codes**.
3. In **Overview** section, create a line for the selected unit.
4. In the **Value** section, in **Value** field, enter an external code to use for the selected unit, according to the official codification.

## Enter products codes

1. Go to **Product information management** \> **Products** \> **Released products**.
2. Select a product, and then, on the Action Pane, on the **Manage inventory** tab, in the **Warehouse** group, select **GTIN codes**.
3. Enter the GTIN code for the selected product. This code will be then used as a standard product identifier.
4. On the Action Pane, on the **Sell** tab, in the **Related information** group, select **External item desription**.
5. In **External item number** field, enter a customer-specific code for the selected product. This code will be then used as a Buyer's product identifier.

> [!NOTE]
> Internal item numbers defined in the system will be used as Seller's products identifiers by default.

## Define invoice type

The system allows to define an invoice type either as **Tax invoice** or **Simplified invoice**.

1. Go to **Accounts receivable** \> **Orders** \> **All sales orders**.
2. Create a new or select an existing open order and navigate to the order header.
3. On **General** FastTab, in **Status** group, in **Invoice type** field, select a required value.

Similarly, the invoice type can be defined for Free text invoices.

1. Go to **Accounts receivable** \> **Invoices** \> **All free text invoices**.
2. Create a new or select an existing open free text invoice and navigate to the invoice header.
3. On **General** FastTab, in **Invoice** group, in **Invoice type** field, select a required value.

## Configure printable invoice layouts

### Enable specific invoice layouts for Saudi Arabia 

1. Go to **Accounts receivable** \> **Setup** \> **Forms** \> **Form setup**.
2. Click on **Print management**.
3. Select **Customer invoice** report and refer to **SalesInvoice.Report_SA** layout in the **Report format** field.
4. Select **Free text invoice** report and refer to **FreeTextInvoice.Report_SA** layout in the **Report format** field.

### Enable VAT numbers prining on invoices 

1. Go to **Accounts receivable** \> **Setup** \> **Forms** \> **Form setup**.
2. In **Invoice** section turn on the **Print tax exempt number on invoice** option.
3. In **Free text nvoice** section turn on the **Print tax exempt number on invoice** option.
4. Go to **Project management and accounting** \> **Setup** \> **Forms** \> **Form setup**.
5. In **Invoice** section turn on the **Print tax exempt number on invoice** option.


## Print invoices

When printing Customer invoices based on Sales orders or Free text invoices, the title of an invoice will reflect the type, **Tax invoice** or **Simplified invoice**.
Additionally, QR codes will be printed.

![Invoice printout](media/sau-qr-invoice.jpg)

## Issue electronic invoices

When you've completed all the required configuration steps, you can generate electronic invoices for posted invoices. For more information about how to generate electronic invoices, see [Issue electronic invoices in Finance and Supply chain management](e-invoicing-issuing-electronic-invoices-finance-supply-chain-management.md).

## Related topics

- [Get started with the Electronic invoicing add-in for Saudi Arabia](e-invoicing-sa-get-started.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
