---
# required metadata

title: Configure invoice layout for Bahrain
description: This topic explains how to configure the invoice layout for Bahrain.
author: ilkond
manager: AnnBe
ms.date: 08/27/2020
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
ms.search.region: Bahrain
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
| **CONFIGURABLE**                | Yes. See the configurations in [Import Electronic reporting configurations](#ERConfigs).|
| **INTERNAL REFERENCE**                | [Compliance 3982346](https://vstsmbs.visualstudio.com/Compliance/_queries/edit/3982346)|
| **FIRST AVAILABLE IN**                | 2020 Release Wave 2 (Monthly update 10.0.13)|
| **FEATURE UPDATE HISTORY**                |  |
| **FEATURE MANAGEMENT**                | No activation required. See the related features in [Enable features](#features).|
| **BUSINESS NEED**                | The layout of printable invoices must be compliant with Bahraini legal requirements.|
| **FEATURE DESCRIPTION**                | The article explains how to configure printable invoice layouts to ensure compliance with Bahraini legal requirements. Bahrain-specific invoice layouts are implemented using the **Configurable business documents** concept. For more information about configurable business documents, see [Business document management overview](../../fin-and-ops/dev-itpro/analytics/er-business-document-management.md).|

## Prerequisites

The primary address of the legal entity must be in Bahrain.

## <a name="features"></a>Enable features

In the **Feature management** workspace, enable the following features:

- (Bahrain) Credit invoicing layout for sales and project invoice reports
- Convert Electronic reporting outbound documents from Microsoft Office formats to PDF

For more information about how to enable features, see [Feature management overview](../../fin-and-ops/get-started/feature-management/feature-management-overview.md).

## <a name="ERConfigs"></a>Import Electronic reporting configurations

In the **Electronic reporting** workspace, import the following Electronic reporting formats from the repository:

 - Sales invoice (Excel) (BH)
 - Free text invoice (Excel) (BH)
 - Project invoice (Excel) (BH)
 - Project contract line items (Excel) (BH)
 - Project manage invoice (Excel) (BH)

> [!NOTE]
> The formats above are derived from related standard formats based on **Invoice model** and use **Invoice model mapping**. All required additional configurations will be automatically imported.

For more information how to import Electronic reporting configurations, see [Download Electronic reporting configurations from Lifecycle Services](../../dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

## Configure conversion to PDF

By default, invoices are generated as Excel files. To enable their conversion to a PDF format, complete the following setup.

1. In **Electronic reporting** workspace, select **Electronic reporting destinations** and create destinations for the related formats:

 - Sales invoice (Excel) (BH)
 - Free text invoice (Excel) (BH)
 - Project invoice (Excel) (BH)
 - Project contract line items (Excel) (BH)
 - Project manage invoice (Excel) (BH)
 
2. For each format, select the **Convert to PDF** check-box, select the **Portrait** page orientation, and enable printing to **Screen**.

![Enable conversion to PDF](media/emea-bhr-pdf.jpg)

## Configure parameters

### Configure print management 

1. Go to **Accounts receivable** > **Setup** > **Forms** > **Forms setup**.
2. On the **General** tab, select **Print management** and define the references to the imported formats for:

 - **Customer invoice**: Select **Sales invoice (Excel) (BH)**
 - **Free text invoice**: Select **Free text invoice (Excel) (BH)**

![Print management configuration](media/emea-bhr-print_management.jpg)

3. Go to **Project management and accounting** > **Setup** > **Forms** > **Forms setup**.
4. On the **General** tab, select **Print management** and define the references to the imported formats for:

 -  **Project invoice without billing rules**: Select **Project invoice (Excel) (BH)**
  - **Project invoice with billing rules**: Select **Project contract line items (Excel) (BH)**
  - **User defined project invoice**: Select **Project manage invoice (Excel) (BH)**

### Sales tax specification

1. Go to **Accounts receivable** > **Setup** > **Forms** > **Forms setup**.
2. On the **General** tab, in the **Sales tax specification** field, select **Registration and company currency**.

![Sales tax specification](media/emea-bhr-tax-spec.jpg)

3. Go to **Project management and accounting** > **Setup** > **Forms** > **Forms setup**.
4. On the **General** tab, in the **Sales tax specification** field, select**Registration and company currency**.

### Packing slip specification

1. Go to **Accounts receivable** > **Setup** > **Forms** > **Forms setup**.
2. On the **Invoice** tab, select the **Print packing slip specifications** check-box.

![Packing slip specification](media/emea-bhr-packing-spec.jpg)

3. Go to **Project management and accounting** > **Setup** > **Forms** > **Forms setup**.
4. On the **Invoice** tab, select the **Print packing slip specifications** check-box.

### Activate credit invoicing 

1. Go to **Accounts receivable** > **Setup** > **Accounts receivable parameters**.
2. On the **Updates** tab, on the **Invoice** FastTab, enable **Apply the credit invoicing layout into sales and project invoice reports**.

![Credit invoicing activation](media/emea-bhr-credit.jpg)

## Generate invoices

After all of the previous steps in this topic are complete, you can print invoices based on sales orders and free text invoices in accordance with Bahraini legal requirements.
