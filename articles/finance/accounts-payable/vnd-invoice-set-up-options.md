---
title: Set up options for vendor invoice automation 
description: Learn about the options that are available for setting up and configuring vendor invoice automation, including overviews on parameters.
author: sunfzam
ms.author: shpandey
ms.topic: article
ms.date: 09/03/2024
ms.custom: 
ms.reviewer: twheeloc  
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2017-08-30
ms.search.form:
ms.dyn365.ops.version: 10.0.14
---

# Set up options for vendor invoice automation

[!include [banner](../includes/banner.md)]

This article describes the options that are available for setting up and configuring vendor invoice automation. Invoice automation features use the following types of setup parameters:

- Parameters for automatically applying prepayments in imported invoices.
- Parameters for submitting imported vendor invoices to the workflow system and matching posted product receipt lines to pending vendor invoice lines.
- Parameters for processing automation background tasks:

    - Submitting imported vendor invoices to the workflow system.
    - Automatically matching posted product receipt lines to pending vendor invoice lines.
    - Validating invoice matching for manual invoices that were automatically matched to product receipt lines. Different business processes use this framework to define how often the selected process is run. The available frequencies for the **Match product receipt to invoice lines** and **Submit vendor invoices to workflow** background processes include **Hour** and **Daily**.

To set up or view information about a background task, go to **System administration** \> **Setup** \> **Process automations**, and select the **Background task** tab.

To achieve touchless automation from the import process through vendor invoice posting, you must set up a Vendor invoice workflow. To set up a workflow, go to **Accounts payable** \> **Setup** \> **Accounts payable workflows**. To ensure that the invoice can be processed from start to finish without manual intervention, you must include an automated posting task in your workflow configuration.

## Parameters for automatically applying prepayments in imported invoices

- **Automatically apply prepayment for imported invoices** – When this option is set to **Yes**, the system automatically looks up existing prepayments for a corresponding purchase order when vendor invoices are imported. If any prepayments that can be applied are found, one additional line is added to apply the prepayments in the vendor invoices that are being imported.
- **Block follow-up automation process in case of prepayment application failure** – When this option is set to **Yes**, invoices are blocked if a prepayment can't be applied. Like other automated processes, such as the receipt matching process and the submission to a workflow process, the invoice automation process doesn't pick up blocked invoices until the prepayment is manually applied.

## Parameters for submitting imported vendor invoices to the workflow system

Specific parameters are used to submit imported vendor invoices to the workflow system. Additionally, some parameters are used to match posted product receipt lines to pending vendor invoice lines. On the **Vendor invoice automation** tab of the **Accounts payable parameters** page, the parameters that you must set are divided between the following sections:

- Vendor invoices workflow
- Match product receipts automatically

The following parameters are available:

 - **Automatically submit imported invoices to workflow**:

    - If you set this option to **Yes**, invoices are automatically submitted to the workflow system if they completed the **Match product receipts to invoice lines** job, and if the **Included in automated processing** option is selected. By setting this option to **Yes**, you enable a touchless process from the import results through posting. You can set this option to **Yes** only if an active vendor invoice workflow is set up for your legal entity. To set up a workflow, go to **Accounts payable** \> **Setup** \> **Accounts payable workflow**.
    - If you set this option to **No**, invoices must be manually submitted to the workflow system.

- **Check match product receipt status before workflow submission**:

    - If you set this option to **Yes**, the imported invoice can't be automatically submitted to the workflow system until the matched product receipt quantity equals the invoice quantity.
    - If you set this option to **No**, the invoice is submitted to the workflow system after the number of attempts is reached, even if the product receipt quantity doesn't equal the invoice quantity.

    The **Check match product receipt status before workflow submission** option is available only if the **Enable invoice matching validation** option is selected. When this option is selected, the **Automatically match product receipts to invoice lines** option is automatically set to **Yes**.

- **Automatically match product receipts to invoice lines** – If you set this option to **Yes**, background processing can be used to automatically match posted product receipts to invoice lines that a three-way matching policy is defined for. That process runs either until the matched product receipt quantity equals the invoice quantity, or until the value of the **Number of times to attempt automatic matching** field is reached. The process can be run until the invoice is submitted to the workflow system.

    The **Automatically match product receipts to invoice lines** option is available only if the **Enable invoice matching validation** option is selected. If you set the **Match product receipts to invoice lines prior to automatically matching** option to **Yes**, this option can't be set to **No**. To set this option to **No**, you must first set the **Match product receipts to invoice lines prior to automatically matching** option to **No**.

- **Number of times to attempt automatic matching** – Select the number of times that the system tries to match product receipts to an invoice line before the process fails. When the specified number of attempts is reached, the invoice is removed from automation processing.

## Include invoices in the vendor invoice automation process

When the **Automatically submit imported invoices to workflow** or **Automatically match product receipts to invoice lines** option is enabled (that is, set to **Yes**), the **Include in automated processing** option appears on the invoice header.

- When an invoice is imported from an external source, the **Include in automated processing** option is automatically enabled. This behavior ensures that vendor invoices are incorporated into the vendor invoice automation process, and that the invoices can't be edited.
- For manually created invoices, the **Include in automated processing** option is disabled by default. If the **Automatically match product receipts to invoice lines** option is enabled, the **Automated receipt match status** field is initially set to **Not applicable**. Users can manually enable this option to include an invoice in the vendor invoice automation process after invoice entry is completed. The value of the **Automated receipt match status** field is then changed to **Not yet run**. The **Include manually created invoices in the invoice automation** feature controls this functionality.

## Exclude invoices from the vendor invoice automation process

A vendor invoice that is included in the vendor invoice automation process can be excluded from automation.

- The user can manually exclude the invoice by disabling the **Include in automated processing** option.
- If the **Automatically match product receipts to invoice lines** option is enabled, the invoice is excluded from automation under these conditions:

    1. The **Automatically submit imported invoices to workflow** option is disabled, and the **Automated receipt match status** field is set to **Completed**, **Failed**, or **Not applicable**.
    2. The **Automatically submit imported invoices to workflow** option is enabled.
    3. The invoice isn't approved after it's successfully submitted to the workflow system.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
