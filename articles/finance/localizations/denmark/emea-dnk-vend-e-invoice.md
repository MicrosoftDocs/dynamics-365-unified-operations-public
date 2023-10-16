---
title: Vendor electronic invoices import in Denmark
description: This article explains how to configure and use vendor electronic invoices import in Denmark in Microsoft Dynamics 365 Finance.
author: ilikond
ms.date: 10/13/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Denmark
ms.author: ikondratenko
ms.search.validFrom: 2023-11-03
ms.dyn365.ops.version: AX 10.0.38
ms.custom: 853863
ms.assetid: 
ms.search.form: 
---

# Vendor electronic invoices import in Denmark

[!include [banner](../../includes/banner.md)]

This article explains how to configure and use vendor electronic invoices import for Denmark from the country specific **OIOUBL** format in Microsoft Dynamics 365 Finance.

## Prerequisites

Before you complete the tasks in this article, the following prerequisites must be met:

- The primary address of the legal entity must be in Denmark.
- The latest version of the following Electronic reporting (ER) format configuration must be imported. For more information, see [Import Electronic reporting (ER) configurations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-import-ger-configurations.md).


    - Vendor Invoice Import (DK)
        
> [!NOTE]
> The ER format is based on the **Invoice model** configuration and use the **Vendor Invoice Mapping to Destination** configuration. All required additional configurations are automatically imported.

## Configure parameters

### Reference the imported ER format configurations

1. Go to **Accounts payable** \> **Setup** \> **Accounts payable parameters**.
2. On the **Electronic documents** tab, on the **Electronic reporting** FastTab, in the **Vendor invoice** field select the imported format **Vendor Invoice Import (DK)**.
    
### Configure the sources to import files in a batch mode

You can configure a Sharepoint folder to be used as a source location of incoming vendors invoices files.

1. Go to **Organization administration** \> **Document management** \> **Document types**.
2. Create a new or configure an existing Document type.
3. On the **General** FastTab, in the **Location** field, select the **SharePoint** value.
4. In the **SharePoint Address** field, select the folder where import files will be located.
5. Go to **Organization administration** \> **Electronic reporting** \> **Electronic reporting source**.
6. Create a new Electronic reporting source
7. In the **Format** field select, **Vendor Invoice Import (DK)** format configuration.
8. It the **File source** FastTab, assign a source name in the **Name** field and click on **Settings** button.
9. It the **Source settings** form, enable **Sharepoint** option.
10. It the **Document type for input sources** field, select the document type created at step 2.
11. Optionally, three more Document types can be preliminary set up and used to define different *post-process* locations:
  - To move there files which were successfully imported in the **Document type for imported files** field;
  - To move there files which were imported with warnings in the **Document type for files with warnings** field;
  - To move there files which were failed with errors in the **Document type for failed files** field.
    
    ![ER source settings](../media/emea-dnk-er-source.jpg)

> [!NOTE]
> If no source is defined for import in batch mode then the system will request to define an individual import file right before the start of import process.

### Configure vendor data

During import process vendors are identified via their tax exempt numbers. To enable proper vendors identification, do the following configuration steps.

1. Go to **Accounts payable** \> **Vendors** \> **All vendors**, and select a vendor.
2. On the **Invoice and delivery** FastTab, in the **Tax exempt number** field, enter a valid tax registration number for the vendor. This number will be used for the vendor identification during import process via matching to **Invoice\cac:AccountingSupplierParty\cac:Party\cac:PartyLegalEntity\cbc:CompanyID** element's value in the import XML file.

### Configure products

During import process products are identified via their external descriptions which are usually vendor specific. To enable proper productss identification, do the following configuration steps.

1. Go to **Product information management** \> **Products** \> **Released products**.
2. Select a product, and then, in the **Purchase** menu, in the **Related information** section, select **External item description**.
3. Create a new external description for the selected product.
4. In the **Account code** column, select the **Table** value if you define an external product description for a specific vendor. 
5. In the **Vendor relation** columnn, select a specific vendor.
6. In the **External item number** columnn, enter an external product code. This code will be used for the product identification during import process via matching to **Invoice\cac:InvoiceLine\cac:Item\cbc:Name** element's value in the import XML file.

### Configure units of measure

Optionally, you can configure external codes for units of measure, if specific units will be explicitly defined in the incoming import files. Do the following steps.

1. Go to **Organization administration** \> **Setup** \> **Units** \> **Units**.
2. Select a unit ID, and then select **External codes**.
3. On the **External codes** page, in the **Overview** section, in the **Code** field, enter a code that corresponds to the selected unit ID.
4. In **Value** section, in **Value** field, enter the external unit code which is expected to be used in import files.


## Import vendor electronic invoices

To run the procedure of vendor electronic invoices import, do the following steps.

1. Go to **Accounts payable** \> **Periodic tasks** \> **Import vendor invoices**.
2. In the **Electronic report parameters** form, in the **File source** FastTab, in the **Source settings** field, select the previously configured source location for batch mode import. In case no source for batch import is defined, the system will request to select a single file for import.
3. Click **OK** to immediately start import process or schedule import running in the background.

### Import process description

1. During import process, Vendors will be identified via Tax exempt number defined in Vendor's master data. If no vendor with matching data is found in the system then the import process will fail with a related error-message.
2. Products used in invoices lines will be identified via External item number which can be vendor-specific. If no product with matching external description is found in the system then the import process will fail with a related error-message.
3. Units of measure, if used in invoices lines, will be identified via External codes values. If no unit with matching external code value is found in the system then the import process will fail with a related error-message.
4. If an incoming import file contains the information about purchase orders and its lines in **Invoice\cac:OrderReference\cbc:ID** and **Invoice\cac:InvoiceLine\cac:OrderLineReference\cbc:LineID** elements then these numbers will be used for the invoice matching with purchase orders and lines entered in the system.
5. If no orders or lines references are defined in an incoming file then the system will try to automatically match incoming vendor invoices with existing purchase orders.
6. If no purchase order is found, the system will raise a warning but continue import considering products in invoice lines as "Non-stock" items and will expect that such products belong to Item model group with unmarked Stocked product check-box in Inventory policy. 
7. If no related "Non-stock" products exist then the system will try to import invoice lines refering to **DEFAULT_ITEM**. The default item must be preliminary configured in the system with the product code defined exactly as **DEFAULT_ITEM** and also belong to Item model group with unmarked Stocked product check-box in Inventory policy. If no default item is configured in the system then the import process will fail with a related error-message.
8. Taxes will be calculated in the system based on the imported data and tax settings, not imported as fixed amounts from the incoming XML file. The results of the calculation can be then manually adjusted, if needed.

Successfully imported vendor electronic invoices will be shown in the system as pending invoices. To review imported invoices, go to **Accounts payable** > **Invoices** > **Pending vendor invoices**. 

> [!NOTE]
> **Limitations**
>  - Import of miscellaneous charges is not supported;
>  - Only line-level discounts import is supported.

## Additional resources

- [Customer electronic invoices in Denmark](../norway/emea-dnk-e-invoices.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]


