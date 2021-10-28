---
# required metadata

title: Vendor electronic invoices in Italy
description: This topic explains how to configure and submit vendor electronic invoices in Italy.
author: ikondo
ms.date: 10/27/2021
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

# Vendors electronic invoices export

[!include [banner](../includes/banner.md)]

According to Italian legislation, invoices received from foreign vendors which are not tax residents in Italy, must be submitted to the Exchange system (SDI).
This topic describes how configure and submit vendor electronic invoices in the electronic format **FatturaPA**.

## Prerequisites

The primary address of the legal entity must be in Italy.

The export of vendors electronic invoices is implemented symmetrically to Italian customers electronic invoices export and uses common **Electronic invoice parameters** defined in **Accounts receivable** module. These parameters must be configured in advance. For details, see the article for [Customer electronic invoices](emea-ita-e-invoices.md).


## <a id="apparameters"></a>Accounts payable parameters configuration

In **Accounts payable** \> **Setup** \> **Accounts payable parameters**, on the **Electronic documents** tab, in the **Vandor invoice (export)** field,select the configuration that is used to create electronic invoice export XML files for vendor invoices.

![Electronic documents in Accounts payable parameters](media/emea-ita-AP-parameter-e-invoices.jpg)

Use the **Vendor invoice (IT).version.YYY.ZZ** electronic reporting configuration, or later version of it.

> [!NOTE]
> The configurations must be imported before they can be selected. For more information, see [Download ER configurations from the Global repository of Configuration service](../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).


## Vendor data configuration

Select a specific vendor in **Accounts payable** \> **All vendors**. On the **Invoice and delivery** FasTab, in the **E-invoice** section, turn on the **eInvoice register** option to activate electronic invoices generation for the vendor.

## Invoice types configuration

**Invoice type** is a mandatory attribute of electronic invoices and must be assigned to an electronic invoice before its submission to the Exchange system.

### Define invoice types dictionary

In **Accounts receivable** \> **Setup** \> **Electronic invoice parameters**, on the **Invoice types** tab, define the codes and the descriptions of required invoice types.

![Invoice types dictionary](media/emea-ita-invoice-types.jpg)

### Assign invoice types to sales tax codes

You can assosiate invoice types with specific salse tax codes. In **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax codes**, on the **General** FastTab, in the **Invoice type** field, enter the reference to a specific invoice type.

![Invoice types in tax codes](media/emea-ita-invoice-types-tax-codes.jpg)

## Invoice types processing

Invoice type associated with the sales tax code used in the invoice will be automatically populated into the **TipoDocumento** tag of the generated electronic invoice XML file.

In no invoice type is associated with the sales tax code, then the following types of vendor invoice documents will automatically be filled in:

- TD16 – for vendors located in Italy, if an invoice contains a sales tax code with either **Use tax** or **Reverse charge** option activated.
- TD17 – for vendors located in European Union, if an invoice is issued for **services** provision.
- TD18 – for vendors located in European Union, if an invoice is issued for **products** selling.

If a required invoice type wasn't populated, you can manually adjust the invoice type in the vendor invoice journal. 
To enable manual adjustment, complete the following steps.

### Electronic properties configuration

In **Accounts receivable** > **Setup** > **Electronic document property types**, add a new property type **DocumentType** (exactly as written here) applicable to **Vendor invoice journal**

![Invoice type parameter](media/emea-ita-invoice-type-parameter.jpg)

### Invoice types regisration

In **Accounts payable** > **Inquiries and reports** > **Invoice** > **Invoice journal**, open **Electronic document properties** for a selected invoice.

![Invoice type in invoices](media/emea-ita-invoice-type-in-invoice.jpg)

In the next form enter a required Invoice type.

![Invoice type value](media/emea-ita-invoice-type-value.jpg)

This invoice type value will override automatically created codes during creation of e-invoices XML files.


## Process vendor electronic invoices

To view all vendors electronic invoices and perform various actions, go to **Accounts payable** > **Invoices** > **E-Invoices** > **Electronic invoices**.
The functionality is similar to customers electronic invoices processing. For details, see the chapter **Electronic invoice register** of the [Customer electronic invoices](emea-ita-e-invoices.md) article.


- [Accounts receivable parameters](#apparameters)



[!INCLUDE[footer-include](../../includes/footer-banner.md)]

