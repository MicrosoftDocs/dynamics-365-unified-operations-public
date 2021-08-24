---
# required metadata

title: Electronic reporting framework API changes for Application update 10.0.21
description: This topic describes how the APIs of the Electronic reporting (ER) framework have been changed in Microsoft Dynamics 365 Finance version 10.0.21.
author: NickSelin
ms.date: 08/03/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ERFormatDestinationTable
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global 
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2021-08-01
ms.dyn365.ops.version: 10.0.21
---

# Electronic reporting framework API changes for Application update 10.0.21

[!include [banner](../includes/banner.md)]

This topic describes how the application programming interfaces (APIs) of the Electronic reporting (ER) framework have been changed in Microsoft Dynamics 365 Finance version 10.0.21.

## <a name="er-api-set-print-management-record-specific-destination"></a>API to enable users to configure ER destinations that are print management record specific

This new API lets you configure ER destinations for a specific type of business document and assign a configured named destination to a [print management](document-reporting-services.md) record. Therefore, you can make ER destinations print management record specific.

```xpp
/// <summary>Class for enabling NamedDestinationFeature for current document type.</summary>
/// <remarks>To enable the document type you should wrap a <c>isNamedDestinationEnabledByDocumentType</c> method.</remarks>
public class ERNamedDestinationReportEnabler
{
    /// <summary>Checks that feature enabled for current document type. Make extension for this method.</summary>
    /// <param name = "_typeId">Print mgmt document type</param>
    /// <returns>True if feature enabled.</returns>
    [Wrappable(true), SuppressBPWarning('BPParameterNotUsed', 'Required by signature')]
    public static boolean isNamedDestinationEnabledByDocumentType(PrintMgmtDocumentType _typeId)
    {
        return false;
    }
}
```

## <a name="er-api-pass-print-management-record-specific-destination"></a>API to run a format mapping where the destination that is provided is print management record specific

This new API can be used to force ER to deliver generated documents by using a named ER destination.

```xpp
using Microsoft.Dynamics365.LocalizationFramework;

/// <summary>
/// Format mapping run interface to provide an ability to specify destination preset.
/// </summary>
public interface ERIFormatMappingRunWithNamedDestination
{
    /// <summary>
    /// Sets the named destination to the format mapping run object.
    /// </summary>
    /// <param name = "_destinationNamedId">A rec id of named destination.</param>
    /// <returns>The format mapping run object.</returns>
    ERIFormatMappingRun withDestinationNamed(RefRecId _destinationNamedId)
    {
    }
}
```

## Applicability

To set up named destinations and force the ER framework to use the named destination that is provided, you must first turn on the **Allow to set up ER destinations per print management item** feature in the [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md#the-feature-management-workspace) workspace.

## Additional resources

[Electronic reporting (ER) overview](general-electronic-reporting.md)

[Electronic reporting (ER) destinations](electronic-reporting-destinations.md)

[Change code to enable users to configure and use named ER destinations](er-api-named-destinations.md)

[Configure action-dependent ER destinations](er-action-dependent-destinations.md)

[Configure print management record-specific ER destinations](er-named-destinations.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
