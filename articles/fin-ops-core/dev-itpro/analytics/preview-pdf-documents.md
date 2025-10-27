---
title: Preview PDF documents using a PDF viewer
description: Learn how to use the embedded PDF Preview option to view business documents, including additional feature information and limitations.
author: johnmichalak
ms.author: johnmichalak
ms.topic: article
ms.date: 10/27/2025
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2019-05-21
ms.dyn365.ops.version: Platform update 28
---

# Preview PDF documents by using a PDF viewer

[!include[banner](../includes/banner.md)]

Streamline application experiences that result in the production of business documents by taking advantage of the embedded PDF Preview option. Finance and operations applications deliver a modern experience to preview business documents that the service produces. You can use the built-in toolbar to navigate and download the document or to print to locally connected devices.

The embedded viewer offers consistency between the screen presentation and the printed output. In addition, report viewing times are drastically reduced when compared to the legacy experience. The Preview option is available on all supported devices and doesn't require any additional third-party software. You can easily download and navigate documents by using the built-in viewer toolbar options.

The following illustration shows a preview of the experience with a modern business document.
:::image type="content" source="./media/pdf-document-preview.png" alt-text="Screenshot of PDF preview form showing a modern business document preview experience.":::

The legacy HTML-based preview experience is being replaced by a true document preview experience. The modern PDF preview experience offers several key advantages. These advantages include:

- Fidelity between the screen presentation and the printed output.
- A consistent document report preview experience across devices and platforms, including on-premises deployments.
- Server-side rendering that improves the performance when producing the document.
- Built-in tooling that allows users to quickly navigate the contents of the business document.

## Accessing the PDF preview experience (Platform update 36 or later)

The PDF preview experience is enabled by default in [Self-Service deployments](../deployment/infrastructure-stack.md) and in environments hosted on Platform update 39 or later. To use the PDF preview experience in cloud-hosted and Microsoft-managed environments running Platform updates 36 through 38, use Feature Management to enable the **Report PDF viewer** feature.

## Additional feature information

- Expandable and collapsible sections are available by default. These interactive operations don't function after the PDF document is created.
- The printer drop-down menu allows users to choose from locally connected devices. This list doesn't include network printers connected through the service.
- The built-in toolbar actions download documents to the local device.
- Use the **Print destination** options to produce documents in formats other than PDF.
- Use the **Enable accessibility feature on report PDF Files** feature flag to render PDF files as an accessible and tagged PDF, which is larger in size but easier for screen readers and other assistive technologies to read and navigate. The default is off.

## Feature limitations

The Embedded PDF viewer experience delivers a closed document that exactly matches the printed output of the document.  Recipients can't modify these documents, making the format ideal for business operations.  However, as a closed format, the documents are far less interactive on the screen when compared to HTML presentations.  The following end-user capabilities aren't supported when previewing documents by using the embedded PDF viewer.

- By default, embedded drill-thru navigation links are only available while previewing PDF documents.
- PDF documents don't support expandable and collapsible sections.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
