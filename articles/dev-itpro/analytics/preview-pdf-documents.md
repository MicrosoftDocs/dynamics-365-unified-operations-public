---
# required metadata

title: Preview PDF documents with an embedded viewer 
description: TBD
author: tjvass
manager: AnnBe
ms.date: 05/21/2019
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

# Preview PDF documents with an embedded viewer

[!include[banner](../includes/banner.md)]

### Enhanced document report viewing experience
Streamline application experiences that include the production of business documents by taking advantage of the embedded PDF 'Preview' option.  Dynamics 365 for Finance & Operations applications deliver a modern experience previewing business documents produced by the service.  Use the built-in toolbar to navigate and download the document or print to locally connected devices.

The embedded viewer offers customers consistency between the screen presentation and the output printed on paper. In addition, report viewing times are drastically reduced when compared to the legacy experience. The new 'Preview' option is available on all supported devices and does not require any additional 3rd party software. Documents can be downloaded and quickly navigated using built-in viewer toolbar options.

Here's a screen shot of the preview experience with a modern business document



The legacy HTML based preview experience is being replaced by a true document preview experience. There are several key advantages in the modern PDF preview experience.<br> 

For instance…
- The hosted PDF viewer delivers fidelity between the screen presentation and the printed output<br>
- Provides a consistent document report preview experience across devices and platforms including Local Business Data deployments<br>
- Server side rendering improves the performance when producing the document<br>
- Built-in tooling allows users to quickly navigate the contents of the business document<br>

### Accessing the PDF preview experience
The hosted PDF document viewer control is presented by default in most deployment types. However, the PDF preview experience must be enabled on 1Box deployments using the Report Options form.  

**Here are the steps…**<br>
1) Navigate to the Report Options form by adding "&mi=SysReportAdministration" to the URL<br>
2) Set the Preview documents using embedded viewer option to **Yes**<br>
3) Click on the **Save** button<br>

### Note-worthy items…
- Expandable/Collapsible sections presented with the default visibility state. These interactive function do not function in the PDF document.<br>
- The printer drop-down allows users to choose from locally connected devices. This list does NOT include network printers connected to the F&O service.<br>
- Documents can be downloaded to the local device using the built-in toolbar actions<br>
- Application extensions are available to enable drill-thru links in PDF documents<br>
