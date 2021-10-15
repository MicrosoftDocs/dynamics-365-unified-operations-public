---
# required metadata

title: Configure invoice layout for Bahrain
description: This topic explains how to configure the invoice layout for Bahrain.
author: ilkond
ms.date: 09/08/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Bahrain
# ms.search.industry: 
ms.author: ilyako
ms.search.validFrom: 2020-06-03
ms.dyn365.ops.version: 10.0.13

---

# Configure invoice layout for Bahrain (BH-00003)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This topic explains how to configure printable invoice layouts to ensure compliance with Bahraini legal requirements. Bahrain-specific invoice layouts are implemented by using the concept of *configurable business documents*. For more information about configurable business documents, see the [Business document management overview](../../fin-ops-core/dev-itpro/analytics/er-business-document-management.md). 

## Prerequisites

The primary address of the legal entity must be in Bahrain.

## <a id="features"></a>Turn on features

In the **Feature management** workspace, turn on the following features:

- (Bahrain) Credit invoicing layout for sales and project invoice reports
- Convert Electronic reporting outbound documents from Microsoft Office formats to PDF

For more information about how to turn on features, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## <a id="ERConfigs"></a>Import Electronic reporting configurations

In the **Electronic reporting** workspace, import the following Electronic reporting (ER) formats from the repository:

- Sales invoice (Excel) (BH)
- Free text invoice (Excel) (BH)
- Project invoice (Excel) (BH)
- Project contract line items (Excel) (BH)
- Project manage invoice (Excel) (BH)

> [!NOTE]
> These formats are derived from related standard formats, based on the invoice model, and they use the invoice model mapping. All required additional configurations will be automatically imported.

For more information about how to import ER configurations, see [Download Electronic reporting configurations from Lifecycle Services](../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

## Configure conversion to PDF

By default, invoices are generated as Microsoft Excel files. To enable their conversion to PDF format, follow these steps.

1. In the **Electronic reporting** workspace, in the **Related links** section, select **Electronic reporting destination**.
2. On the **Electronic reporting destination** page, create destinations for the following related formats:

    - Sales invoice (Excel) (BH)
    - Free text invoice (Excel) (BH)
    - Project invoice (Excel) (BH)
    - Project contract line items (Excel) (BH)
    - Project manage invoice (Excel) (BH)
 
3. For each format, follow these steps:

    1. Select the **Convert to PDF** check box.
    2. In the **Page orientation** field, select **Portrait**.
    3. Select **Settings**, and then, on the **Destination settings** page, on the **Screen** tab, set the **Enabled** option to **Yes** to enable printing to the screen.

![Enabling conversion to PDF.](media/emea-bhr-pdf.jpg)

## Configure default model mapping for project invoices

In the **Electronic reporting** workspace, select the **Project invoice model mapping (RDP)** configuration. Turn on **Default model mapping** parameter for the selected configuration.

![Project invoice model mapping configuration.](media/invoice-model-tree.png)

## Configure parameters

### Configure Print management 

1. Go to **Accounts receivable** \> **Setup** \> **Forms** \> **Forms setup**.
2. On the **Form setup** page, on the **General** tab, select **Print management**.
3. On the **Print management setup** page, define the references to the imported formats for the following documents:

    - **Customer invoice:** In the **Report format** field, select **Sales invoice (Excel) (BH)**.
    - **Free text invoice:** In the **Report format** field, select **Free text invoice (Excel) (BH)**.

    ![Configuring Print management.](media/emea-bhr-print_management.jpg)

4. Go to **Project management and accounting** \> **Setup** \> **Forms** \> **Forms setup**.
5. On the **Form setup** page, on the **General** tab, select **Print management**.
6. On the **Print management** page, define the references to the imported formats for the following documents:

    - **Project invoice without billing rules:** In the **Report format** field, select **Project invoice (Excel) (BH)**.
    - **Project invoice with billing rules:** In the **Report format** field, select **Project contract line items (Excel) (BH)**.
    - **User defined project invoice:** In the **Report format** field, select **Project manage invoice (Excel) (BH)**.

### Configure sales tax specification

1. Go to **Accounts receivable** \> **Setup** \> **Forms** \> **Forms setup**.
2. On the **Form setup** page, on the **General** tab, in the **Sales tax specification** field, select **Registration and company currency**.

    ![Configuring sales tax specification.](media/emea-bhr-tax-spec.jpg)

3. Go to **Project management and accounting** \> **Setup** \> **Forms** \> **Forms setup**.
4. On the **Form setup** page, on the **General** tab, in the **Sales tax specification** field, select **Registration and company currency**.

### Configure packing slip specification

1. Go to **Accounts receivable** \> **Setup** \> **Forms** \> **Forms setup**.
2. On the **Form setup** page, on the **Invoice** tab, select the **Print packing slip specifications** check box.

    ![Configuring packing slip specification.](media/emea-bhr-packing-spec.jpg)

3. Go to **Project management and accounting** \> **Setup** \> **Forms** \> **Forms setup**.
4. On the **Form setup** page, on the **Invoice** tab, select the **Print packing slip specifications** check box.

### Activate credit invoicing 

1. Go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
2. On the **Accounts receivable parameters** page, on the **Updates** tab, on the **Invoice** FastTab, set the **Apply the credit invoicing layout into sales and project invoice reports** option to **Yes**.

![Activating credit invoicing.](media/emea-bhr-credit.jpg)

## Generate invoices

After you've completed all the previous procedures in this topic, you can print invoices that are based on sales orders and free text invoices, in accordance with Bahraini legal requirements.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]