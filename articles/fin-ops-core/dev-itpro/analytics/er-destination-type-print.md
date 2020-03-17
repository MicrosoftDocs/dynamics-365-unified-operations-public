---
# required metadata

title: Printer ER destination type
description: This topic explains how you can configure a printer destination for each FOLDER or FILE component of an Electronic reporting (ER) format that is configured to generate outbound documents in either PDF or Microsoft Office formats (Excel\Word). 
author: NickSelin
manager: AnnBe
ms.date: 03/17/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: DocuType, ERSolutionTable, ERFormatDestinationTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 97423
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2020-04-01
ms.dyn365.ops.version: AX 10.0.9

---

# <a name="PrinterDestinationType"></a>Printer destination

[!include [banner](../includes/banner.md)]

You can send a generated document directly to a network printer for direct printing.

## Prerequisites

Before you begin, you must install and configure the Document Routing Agent, and then register the network printers. For more information, see [Install the Document Routing Agent to enable network printing](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/analytics/install-document-routing-agent).

## Make the Printer destination available

To make the **Printer** destination available in the current instance of Microsoft Dynamics 365 Finance, go to the **Feature management** workspace, and turn on the following features, in this order:

1. Convert Electronic Reporting outbound documents from Microsoft Office formats to PDF
2. Document Routing Agent as Electronic Reporting destination for outbound documents

[![Turning on the ER printer destination feature in Feature management](./media/ER_Destinations-EnablePrinterDestinationFeature.png)](./media/ER_Destinations-EnablePrinterDestinationFeature.png)

### Applicability

The **Printer** destination can be configured only for file components that are used to generate output in either printable PDF format (PDF Merger or PDF file format elements) or Microsoft Office Excel/Word format (Excel file). When output is generated in PDF format, it's sent to a printer. When output is generated in Microsoft Office format, it's automatically converted to PDF format and then sent to a printer.

### Limitations

This feature is a preview feature and is subject to the terms of use that are described in [Supplemental Terms of Use for Microsoft Dynamics 365 Previews](https://go.microsoft.com/fwlink/?linkid=2105274).

The **Printer** destination is implemented only for cloud deployments.

### Use the Printer destination

1. Set the **Enabled** option to **Yes** to send a generated document to a printer.
2. In the **Printer name** field, select the required network printer.
3. Set the **Save in print archive?** option to **Yes** to store the generated output in the print archive, so that it's available for further printing. To access archived output later, go to **Organization administration** \> **Inquiries and reports** \> **Report archive**.

[![Using the Printer destination](./media/ER_Destinations-PrinterDestination.png)](./media/ER_Destinations-PrinterDestination.png)

> [!NOTE]
> The **Convert to PDF** option doesn't have to be turned on when you configure the **Printer** destination. The PDF conversion for printing purposes will occur even if the option is turned off.

If you want to print out an outbound document in Excel format using a particular [page orientation](electronic-reporting-destinations.md#SelectPdfPageOrientation), you must enable the **Convert to PDF** option. To do this, set the **Convert to PDF** field to **Yes** to make the **Page orientation** option available, and then in the **Page orientation** field, select the page orientation.

## Additional resources

- [Electronic reporting (ER) overview](general-electronic-reporting.md)
- [Electronic reporting (ER) destinations](electronic-reporting-destinations.md)
