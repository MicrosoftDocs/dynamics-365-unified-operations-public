---
# required metadata

title: Configure invoice layout for Egypt
description: This topic explains how to configure the invoice layout for Egypt.
author: ilkond
ms.date: 02/01/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Egypt
# ms.search.industry: 
ms.author: ilyako
ms.search.validFrom: 2021-02-01
ms.dyn365.ops.version: 10.0.17

---

# Configure invoice layout for Egypt

[!include [banner](../includes/banner.md)]


This topic explains how to configure printable invoice layouts to ensure compliance with Egyptian legal requirements. Egypt-specific invoice layouts are implemented by using the concept of *configurable business documents*. For more information about configurable business documents, see [Business document management overview](../../fin-ops-core/dev-itpro/analytics/er-business-document-management.md). 

## Prerequisites

- The primary address of the legal entity must be in Egypt.
- Required registration numbers are configured. For more information about how to configure registration numbers, see [Configure registration numbers in Egypt](emea-egy-reg-numbers.md)

## <a id="features"></a>Turn on features

In the **Feature management** workspace, turn on the following features:

- Credit invoicing layout for sales and project invoice reports
- Convert Electronic reporting outbound documents from Microsoft Office formats to PDF

For more information about how to turn on features, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## <a id="ERConfigs"></a>Import Electronic reporting configurations

In the **Electronic reporting** workspace, import the following Electronic reporting (ER) formats from the repository:

- Sales invoice (Excel) (EG)
- Free text invoice (Excel) (EG)
- Project invoice (Excel) (EG)
- Project contract line items (Excel) (EG)
- Project manage invoice (Excel) (EG)

> [!NOTE]
> These formats are derived from related standard formats. The formats are based on the invoice model, and use the invoice model mapping. All required additional configurations are automatically imported.

For more information about how to import ER configurations, see [Download Electronic reporting configurations from Lifecycle Services](../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

## Configure conversion to PDF

By default, invoices are generated as Microsoft Excel files. To enable their conversion to PDF format, follow these steps.

1. In the **Electronic reporting** workspace, in the **Related links** section, select **Electronic reporting destination**.
2. On the **Electronic reporting destination** page, create destinations for the following related formats:

    - Sales invoice (Excel) (EG)
    - Free text invoice (Excel) (EG)
    - Project invoice (Excel) (EG)
    - Project contract line items (Excel) (EG)
    - Project manage invoice (Excel) (EG)
 
3. For each format, follow these steps:

    1. Select the **Convert to PDF** check box.
    2. In the **Page orientation** field, select **Portrait**.
    3. Select **Settings**, and then, on the **Destination settings** page, on the **Screen** tab, set the **Enabled** option to **Yes** to enable printing to the screen.

## Configure default model mapping for project invoices

In the **Electronic reporting** workspace, select the **Project invoice model mapping (RDP)** configuration. Turn on the **Default model mapping** parameter for the selected configuration.

## Configure parameters

### Configure Print management 

1. Go to **Accounts receivable** \> **Setup** \> **Forms** \> **Forms setup**.
2. On the **Form setup** page, on the **General** tab, select **Print management**.
3. On the **Print management setup** page, define the references to the imported formats for the following documents:

    - **Customer invoice**: In the **Report format** field, select **Sales invoice (Excel) (EG)**.
    - **Free text invoice**: In the **Report format** field, select **Free text invoice (Excel) (EG)**.

4. Go to **Project management and accounting** \> **Setup** \> **Forms** \> **Forms setup**.
5. On the **Form setup** page, on the **General** tab, select **Print management**.
6. On the **Print management** page, define the references to the imported formats for the following documents:

    - **Project invoice without billing rules**: In the **Report format** field, select **Project invoice (Excel) (EG)**.
    - **Project invoice with billing rules**: In the **Report format** field, select **Project contract line items (Excel) (EG)**.
    - **User defined project invoice**: In the **Report format** field, select **Project manage invoice (Excel) (EG)**.

### Activate credit invoicing 

1. Go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
2. On the **Accounts receivable parameters** page, on the **Updates** tab, on the **Invoice** FastTab, set the **Apply the credit invoicing layout into sales and project invoice reports** option to **Yes**.

## Generate invoices

After you complete all the procedures in this topic, you can print invoices that are based on sales orders, free text invoices, and project invoices, in accordance with Egyptian legal requirements.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]