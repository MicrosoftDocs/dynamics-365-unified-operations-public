---
# required metadata

title: Preview PDF documents using a PDF viewer 
description: This topic explains how to use the embedded PDF Preview option to view business documents.
author: tjvass
manager: AnnBe
ms.date: 07/22/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:
# ROBOTS:
audience: IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom:
ms.search.region: Global
# ms.search.industry:
ms.author: tjvass
ms.search.validFrom: 2019-05-21 
ms.dyn365.ops.version: Platform update 28
---

# Preview PDF documents using a PDF viewer

[!include[banner](../includes/banner.md)]

You can streamline application experiences that result in the production of business documents by taking advantage of the embedded PDF Preview option. Finance and Operations applications deliver a modern experience to preview business documents that are produced by the service. You can use the built-in toolbar to navigate and download the document or to print to locally connected devices.

The embedded viewer offers consistency between the screen presentation and the printed output. In addition, report viewing times are drastically reduced when compared to the legacy experience. The Preview option is available on all supported devices and does not require any additional third-party software. Documents can be easily downloaded and navigated by using the built-in viewer toolbar options.

The following illustration shows a preview of the experience with a modern business document.
![PDF preview form](./media/pdf-document-preview.png)

The legacy HTML-based preview experience is being replaced by a true document preview experience. There are several key advantages in the modern PDF preview experience. These advantages include:

- A fidelity between the screen presentation and the printed output.
- A consistent document report preview experience across devices and platforms, including on-premises deployments.
- The server-side rendering improves the performance when producing the document.
- A built-in tooling that allows users to quickly navigate the contents of the business document.

## Accessing the PDF preview experience (Platform update 35 or earlier)
The hosted PDF document viewer control is presented by default in most deployment types. However, the PDF preview experience must be enabled on OneBox environments using the **Report Administration** page.

1. Go to the **Report Options** page by adding "**&mi=SysReportAdministration**" to the URL.
2. Set the **Preview documents using embedded viewer** option to **Yes**.
3. Select **Save**.

## Accessing the PDF preview experience (Platform update 36 or later)
In Platform updates 36 or later, use Feature Management to enable the **Report PDF viewer** feature.

## Additional feature information

- Expandable/collapsible sections are available by default. These interactive operations do not function after the PDF document has been created.
- The printer drop-down menu allows users to choose from locally connected devices. This list does not include network printers connected through the service.
- Documents are downloaded to the local device using the built-in toolbar actions.
- Use the **Print destination** options to produce documents in formats other than PDF.

## Feature limitations
The Embedded PDF viewer experience delivers a closed document that exactly matches the printed output of the document.  These documents cannot be modified by the recipient making the format ideal for business operations.  However, as a closed format, the documents are far less interactive on the screen when compared to HTML presentations.  The following end-user capabilities are not supported when previewing documents using the embedded PDF viewer.

- Embedded drill-thru navigation is not actionable while previewing PDF documents. 
- PDF documents do not support expandable and collapsible sections. 
