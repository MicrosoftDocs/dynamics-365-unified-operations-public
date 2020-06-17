---
# required metadata

title: Configure invoice layout for Bahrain
description: This topic explains how to configure invoice layout for Bahrain.
author: ilkond
manager: AnnBe
ms.date: 06/03/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Italy
# ms.search.industry: 
ms.author: ilyako
ms.search.validFrom: 2020-06-03
ms.dyn365.ops.version: 10.0.13

---

# Configure invoice layout for Bahrain

[!include [banner](../includes/banner.md)]

|                     |  |
|------------------------------|-------------------|
| **COUNTRY/REGION**          | BHR - Bahrain|
| **FEATURE TITLE** | Configure invoice layout for Bahrain |
| **FEATURE REFERENCE**                | BH-00003|
| **BLUEPRINT CLASSIFICATION**                | INVOICING: Invoice layout / e-invoicing|
| **CONFIGURABLE**                | Yes. ER formats: **Sales invoice (Excel) (BH)**, **Free text invoice (Excel) (BH)**.|
| **INTERNAL REFERENCE**                | 3982346|
| **FIRST AVAILABLE IN**                | Monthly update 10.0.13|
| **LATEST FEATURE UPDATE**                | Monthly update 10.0.13|
| **FEATURE MANAGEMENT**                | Not required|
| **BUSINESS NEED**                | The feature allows to configure printable invoice layouts to make it compliant with Bahraini legal requirements.|
| **FEATURE DESCRIPTION**                | The article explains how to configure printable invoice layouts to make it compliant with Bahraini legal requirements. Bahrain-specific invoice layouts are implemented using **Configurable business documents** concept. For more information about Configurable business documents, see [Business document management overview](../../fin-and-ops/dev-itpro/analytics/er-business-document-management.md).|

## Prerequisites

- The primary address of the legal entity must be in Bahrain.

## Features enabling

In the **Feature management** workspace, enable the following features:
- (Bahrain) Credit invoicing layout for sales and project invoice reports;
- Convert Electronic Reporting outbound documents from Microsoft Office formats to PDF.

For more information how to enable features, see [Feature management overview](../../fin-and-ops/get-started/feature-management/feature-management-overview.md).

## Import of Electronic Reporting configurations
In **Electronic reporting** workspace, import the following Electronic Reporting formats from the repository:
 - Sales invoice (Excel) (BH);
 - Free text invoice (Excel) (BH).
 
> [!NOTE]
> The formats above are based on **Invoice model** and use **Invoice model mapping**. These additional configurations will be automatically imported.

For more information how to import Electronic Reporting configurations, see [Download Electronic reporting configurations from Lifecycle Services](../../dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

## Configure conversion to PDF
By default invoices are being generated as Excel files. To enable their conversion to PDF format do the following setup.

In **Electronic reporting** workspace > **Electronic reporting destinations**, create destinations for the related formats:
 - Sales invoice (Excel) (BH);
 - Free text invoice (Excel) (BH).
 
For each format, mark **Convert to PDF** check-box, select **Portrait** page orientation and enable printing to **Screen**.

![Enable conversion to PDF](media/emea-bhr-pdf.jpg)

## Parameters configuration
### Print management configuration
In **Accounts receivable** > **Setup** > **Forms** > **Forms setup**, in **General** tab, select **Print management** and define the references to the imported formats for:
- **Customer invoice** select **Sales invoice (Excel) (BH)**;
- **Free text invoice** select **Free text invoice (Excel) (BH)**

![Print management configuration](media/emea-bhr-print_management.jpg)

### Sales tax specification
In **Accounts receivable** > **Setup** > **Forms** > **Forms setup**, in **General** tab, choose **Registration and company currency** value for **Sales tax specification** field.

![Sales tax specification](media/emea-bhr-tax-spec.jpg)

### Packing slip specification
In **Accounts receivable** > **Setup** > **Forms** > **Forms setup**, in **Invoice** tab, mark **Print packing slip specifications** check-box.

![Packing slip specification](media/emea-bhr-packing-spec.jpg)

### Credit invoicing activation
In **Accounts receivable** > **Setup** > **Accounts receivable parameters**, in **Updates** tab, **Invoice** FastTab, enable **Apply the credit invoicing layout into sales and project invoice reports** option.

![Credit invoicing activation](media/emea-bhr-credit.jpg)

## Invoices generation

Having all the steps above completed, invoices based on sales orders and free text invoices can be printed in accordance with Bahraini legal requirements.
