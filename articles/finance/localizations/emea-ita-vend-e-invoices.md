---
# required metadata

title: Vendor electronic invoice 
description: This topic explains how to configure and submit vendor electronic invoices in Italy.
author: ikondo
ms.date: 11/29/2021
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
ms.custom: 3984823
ms.search.region: Italy
# ms.search.industry: 
ms.author: ilyako
ms.search.validFrom: 2021-12-01
ms.dyn365.ops.version: 10.0.21

---

# Vendor electronic invoices

[!include [banner](../includes/banner.md)]

According to Italian legislation, invoices received from foreign vendors that aren't Italian tax residents, must be submitted to the Exchange system (SDI).
This topic describes how configure and submit vendor electronic invoices in the electronic format, **FatturaPA**.

## Prerequisites

- The primary address of the legal entity must be in Italy.
- The export of vendor electronic invoices must be implemented symmetrically to the Italian customers electronic invoices export and use the common **Electronic invoice parameters** that are defined in **Accounts receivable**. These parameters must be configured in advance. For more information, see [Customer electronic invoices](emea-ita-e-invoices.md).

## <a id="apparameters"></a> Configure Accounts payable parameters 

Complete the following steps to set up the electronic invoice configuration in the Accounts payable parameters.

1. Go to **Accounts payable** > **Setup** > **Accounts payable parameters**.
2. On the **Electronic documents** tab, in the **Vandor invoice (export)** field, select the **Vendor invoice (IT)** configuration which is used to create the electronic invoice export XML files for vendor invoices.

  ![Electronic documents in Accounts payable parameters.](media/emea-ita-AP-parameter-e-invoices.jpg)

> [!NOTE]
> The configurations must be imported before they can be selected. For more information, see [Download ER configurations from the Global repository of Configuration service](../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).
> The parent model configuration **Invoice model** and the related model mapping configuration **Vendor invoice model mapping (IT)** will be imported or updated automatically.

## Enable electronic invoice generation

Complete the following steps to enable the eInvoice register and enable electronic invoice generation for a vendor.

1. Go to **Accounts payable** \> **All vendors** and select and open the record of the vendor you want to enable the eInvoice register for. 
2. On the **Invoice and delivery** FasTab, in the **E-invoice** section, turn on the **eInvoice register** option to activate electronic invoices generation for the vendor.

## Configure invoice types 

Invoice type is a mandatory attribute of electronic invoices and must be assigned to an electronic invoice before the invoice is submitted to the Exchange system.

### Define invoice types 

Complete the following steps to define one or more invoice types.

1. Go to **Accounts receivable** > **Setup** > **Electronic invoice parameters**. 
2. On the **Invoice types** tab, define one or more codes and the descriptions of required invoice types.

  ![Invoice types dictionary.](media/emea-ita-invoice-types.jpg)

### Assign invoice types to sales tax codes

You can assosiate invoice types with specific sales tax codes. 

1. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax codes**.
2. On the **General** FastTab, in the **Invoice type** field, enter the reference to a specific invoice type.

    ![Invoice types in tax codes](media/emea-ita-invoice-types-tax-codes.jpg)

## Invoice types processing

Invoice types that are associated with the sales tax code used in the invoice are automatically populated into the **TipoDocumento** tag of the generated electronic invoice XML file.

If no invoice type is associated with the sales tax code, the following types of vendor invoice documents will be automatically filled in:

- TD16: For vendors located in Italy, if an invoice contains a sales tax code with either **Use tax** or **Reverse charge** activated.
- TD17: For vendors located in European Union, if an invoice is issued for **services** provision.
- TD18: For vendors located in European Union, if an invoice is issued for **products** selling.

If a required invoice type isn't populated, you can manually adjust the invoice type in the vendor invoice journal.

### Electronic properties configuration

1. Go to **Accounts receivable** > **Setup** > **Electronic document property types** and select **New** to add a new property type.
2. In the **Type** field, enter **DocumentType**. 
3. In the **Applicable to** field, select **Vendor invoice journal**.

    ![Invoice type parameter](media/emea-ita-invoice-type-parameter.jpg)

### Invoice types registration

Complete the following steps to register invoice types.

1. Go to **Accounts payable** > **Inquiries and reports** > **Invoice** > **Invoice journal**.
2. Select an invoice from the list, and then select **Electronic document properties**.

    ![Invoice type in invoices](media/emea-ita-invoice-type-in-invoice.jpg)

3. Enter a required invoice type.

   ![Invoice type value](media/emea-ita-invoice-type-value.jpg)

This invoice type value overrides any automatically created codes during when e-invoice XML files are created.


## Process vendor electronic invoices

To view all electronic invoices for vendors and perform various actions, go to **Accounts payable** > **Invoices** > **E-Invoices** > **Electronic invoices**.
The functionality is similar to customers electronic invoices processing. For more information, see the **Electronic invoice register** section, in the topic, [Customer electronic invoices](emea-ita-e-invoices.md).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]

