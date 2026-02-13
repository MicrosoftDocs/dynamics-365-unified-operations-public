---
title: Output conversion to PDF using ER destinations
description: Learn about the Output conversion to PDF using ER destinations.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 10/01/2025
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2016-05-31
ms.search.form: DocuType, ERSolutionTable
ms.dyn365.ops.version: AX 7.0.1
ms.assetid: f3055a27-717a-4c94-a912-f269a1288be6
---

# Output conversion to PDF

[!include [banner](../includes/banner.md)]

Use the PDF conversion option to convert output in Microsoft Office (Excel or Word) format to PDF format.

Turn on the PDF conversion option for **Excel\\File** and **Common\\File** components that generate output in Office (Excel or Word) format. 
When you turn on this option, the output that you generate in Office format is automatically converted to PDF format.

> [!NOTE]
> Pay attention to the warning message that you receive when you turn on the PDF conversion option for an ER component of the **Common\\File** type.
> This message informs you that there's no way to guarantee, at design time, that the selected file component exposes the content in PDF format or the PDF-convertible content at runtime.
> Therefore, turn on the option only if you're sure that the selected file component was configured to expose the content in PDF format or the PDF-convertible content at runtime.
> 
> If you turn on the PDF conversion option for a format component, and if that component exposes content in a format other than PDF that can't be converted to PDF format, an exception occurs at runtime.
> The message that you receive informs you that the generated content can't be converted to PDF format.

## Limitations

In versions earlier than Dynamics 365 Finance version 10.0.43, you can only convert PDFs outside the current Finance instance. 
A generated file is sent out of Finance to the conversion service, and that service returns the converted document. This solution has the following limitations:

- You can use the PDF conversion option for cloud deployments and on-premises deployment that has [Internet connectivity](../user-interface/client-disconnected.md) enabled.
- The PDF document that you produce has a maximum length of 300 pages.

In Dynamics 365 Finance version **10.0.43** and later, you can enable the **In-App PDF conversion for Configurable Business Documents \(CBD\)** feature in **Feature management** to facilitate 
the seamless conversion of configurable business documents from Word or Excel formats to PDF. 

> [!NOTE]
> The **In-App PDF conversion for Configurable Business Documents \(CBD\) \(preview\)** feature is available in Finance version 10.0.43 and the 10.0.2095.**124** build and later of the 10.0.42 version.

This feature uses Application Object Server (AOS) resources to remove the need for external conversion services. 
By using in-app capabilities, you get efficient and secure document processing and reduce dependency on tools outside of Finance while maintaining high performance and reliability. 
This enhancement supports a wide range of business scenarios to provide users with the flexibility to generate and distribute professional-grade PDF documents directly within the application.

The following advantages come with in-app PDF conversion when you enable the **In-App PDF conversion for Configurable Business Documents \(CBD\)** feature:

- The PDF document that you produce doesn't have a maximum of 300 pages.
- The Word document that you convert can have a [large number of content controls](https://fix.lcs.dynamics.com/Issue/Details?bugId=647877&dbType=3).
- On-premises deployments don't require Internet connectivity.

> [!NOTE]
> Only the common system fonts of the Windows operating system are used to convert output that contains no embedded fonts.

> [!TIP]
> When using the **In-App PDF conversion for Configurable Business Documents (CBD)**, you might notice the font in the generated PDFs has a lighter weight compared to the one in Excel templates. This difference can result in small visual discrepancies between your original template and the final PDF output. Configuration engineers should preview the generated PDF before completing and sharing their configurations.

## <a name="ConvertToPDF"></a>Use the PDF conversion option

To turn on PDF conversion for a file destination, select the **Convert to PDF** check box.

:::image type="content" source="./media/ER_Destinations-TurnOnPDFConversion.png" alt-text="Screenshot of turning on PDF conversion for a file destination.":::

## Use the PDF conversion component in ER format configurations

You can use PDF conversion directly in format configurations. In this case, you don't have to use the [**Convert to PDF**](#ConvertToPDF) checkbox on the **Electronic reporting destination** page. 
A format component, **PDF Converter**, is available.

:::image type="content" source="./media/ERformatPDFconverter.jpg" alt-text="Screenshot of PDF Converter component in formats.":::

> [!NOTE]
> You can add the **PDF Converter** component only in the format configurations of a **PDF** format type, or when the format type isn't explicitly defined but is left blank.
> The **PDF Converter** component can contain only one **Excel\\File** subcomponent.

## <a name="SelectPdfPageOrientation"></a> Select a page orientation for PDF conversion

If you generate an ER configuration in Excel format and want to convert it to PDF format, you can specify the page orientation of the PDF document. 
When you select the **Convert to PDF** checkbox to turn on PDF conversion for a file destination that produces an output file in Excel format, the **Page orientation** field becomes available on the **PDF conversion settings** FastTab. 
In the **Page orientation** field, select your preferred orientation.

:::image type="content" source="./media/ER_Destinations-SelectPDFConversionPageOrientation.png" alt-text="Screenshot of selecting a page orientation for PDF conversion.":::

The following page orientation options are supported:

- Portrait
- Landscape
- Worksheet specific

The selected page orientation applies to all pages of an outbound document that you generate in Excel format and convert to PDF format. 
When you select the **Worksheet specific** option, every worksheet of a generated Excel workbook is converted to PDF using the page orientation that you configured for this worksheet in the Excel template. 
You might have a final PDF document containing portrait and landscape pages. 

> [!NOTE]
> For ER configuration in Word format converted to PDF format, the page orientation of the PDF document always comes from the Word document.

