---
# required metadata

title: Setup options for vendor invoice automation
description: This topics describes the options that are available to setting up and configuring the vendor invoice automation process.  
author: abruer
manager: AnnBe
ms.date: 08/30/2020
ms.topic: articl
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2017-08-30
ms.dyn365.ops.version: 10.0.14

---

# Setup options for vendor invoice automation (Preview)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

The Accounts payable automation features have the following setup options:

- Parameters for submitting imported vendor invoices to workflow and matching posted product receipt lines to pending vendor invoice lines
- Parameters for process automation background tasks. Submitting imported vendor invoices to workflow and matching posted product receipt lines to pending vendor invoice lines automations use the Process automation framework. Different business processes use this framework to define the recurrence of a selected process. You can use a frequency of Hour or Daily for the Match product receipt to invoice lines and the Submit vendor invoices to workflow background processes. To set up or view the background task information, navigate to System administration > Setup > Process automations > click on the Background task tab. 
- Vendor invoice workflow must be set up to achieve touchless automation, from the import process through the vendor invoice posting. To ensure that the invoice can be processed straight-through, without manual intervention, an automated posting task must be included in the workflow configuration. To set up workflow, navigate to Accounts payable > Setup > Accounts payable workflows.

## Parameters for submitting imported vendor invoices to workflow
Some specific parameters are used to submitting imported vendor inovices to workflow. There are also parameters usedto match posted product receipt lines to pending vendor invoice lines. Submitting imported invoices to workflow and matching posted product receipt lines to pending vendor invoice line settings are configured on the Vendor invoice automation tab of the Accounts payable parameters page (Accounts payable > Setup > Accounts payable parameters). The following settings are available:

- Automatically submit imported invoices to workflow – Set this option to Yes to enable the system to automatically submit imported invoices to workflow. If this option is not selected, vendor invoices must be submitted to workflow manually. This is the switch to enable a touchless process from import results through posting. 
  
  There must be an active Vendor invoice workflow set up for your legal entity, to activate this option. Set up workflow using the Accounts payable > Setup > Accounts payable workflow menu option.

- Match product receipts to invoice lines prior to automatically submitting – Set this option to Yes to require that the matched product receipt quantity is equal to the invoice quantity in order for the imported invoice to be automatically submitted to workflow. Setting this option will enable automatic matching of posted product receipts to invoice lines that have a three-way matching policy defined. The process will run until the matched product receipt quantity is equal to the invoice quantity. Once the process is complete, the invoice will be submitted automatically to workflow.
  This field is available only if the Enable invoice matching validation option is selected. When this option is selected, the Automatically match product receipts to invoice lines option will be selected.
- Require the calculated totals to equal the imported totals for automatic workflow submission – Set this option to Yes to ensure that the totals calculated for the invoice must equal provided imported totals before the invoice can be submitted automatically to workflow. If this option is not selected, the invoice can be automatically submitted to workflow, but cannot be posted, until the calculated totals are corrected to match the imported totals. If you do not import the Invoice amount or the Sales tax amount, this option should not be selected.

- Automatically match product receipts to invoice lines – Set this option to Yes to enable automatic matching of posted product receipts to invoice lines that have a three-way matching policy defined using background processing. The process will run until the matched product receipt quantity is equal to the invoice quantity or until the Number of times to attempt automatic matching is reached. The process can be run until the invoice has been submitted into workflow.
This field is available only if the Enable invoice matching validation option is selected.
If you have enabled the option “Match product receipts to invoice lines prior to automatically matching”, this option cannot be set to No. To set this option to No, you must first set the option “Match product receipts to invoice lines prior to automatically matching” to No.

- Number of times to attempt automatic matching - Select the number of times the system should try to match product receipts to an invoice line before concluding that the process failed and then the invoice is removed from automation processing

- Validate only when the matched product receipt quantity is equal to the invoice quantity - Select this option to perform invoice matching validation automatically only when the invoice line’s matched product receipt quantity is equal to the invoice line’s invoice quantity. If this option is not selected, invoice matching validation will be performed each time the system automatically matches a product receipt line to an invoice line.
