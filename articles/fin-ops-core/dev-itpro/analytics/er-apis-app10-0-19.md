---
# required metadata

title: Electronic reporting framework API changes for Application update 10.0.19
description: This topic describes how the APIs of the Electronic reporting (ER) framework have been changed in Microsoft Dynamics 365 Finance version 10.0.19.
author: NickSelin
ms.date: 06/17/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ERFormatDestinationTable, ERParameters
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global 
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2021-04-23
ms.dyn365.ops.version: 10.0.19

---

# Electronic reporting framework API changes for Application update 10.0.19

[!include [banner](../includes/banner.md)]


This topic describes how the application programming interfaces (APIs) of the [Electronic reporting (ER)](general-electronic-reporting.md) framework have been changed in Microsoft Dynamics 365 Finance version 10.0.19.

## <a name="er-api-extend-destination"></a>API to extend the list of ER destinations

To implement a [custom](electronic-reporting-destinations.md#destination-types) ER [destination](electronic-reporting-destinations.md), you must use the `ERIFormatFileDestinationSettings` public interface.

```xpp
using Microsoft.Dynamics365.LocalizationFramework;
using Microsoft.Dynamics365.LocalizationFramework.Format.FileGeneration;

using SL = Microsoft.Dynamics365.LocalizationFramework.XppSupportLayer;

/// <summary>
/// Destination settings are required to store settings of a FILE destination type for the format file component.
/// </summary>
/// <remarks>
/// The implementation object should have static create(container) method for a proper packing.
/// </remarks>
public interface ERIFormatFileDestinationSettings extends SysPackable
{
    /// <summary>
    /// Determines if current settings are enabled.
    /// </summary>
    /// <returns>True if enabled; otherwise - false.</returns>
    boolean isEnabled()
    {
    }

    /// <summary>
    /// Sets settings enabling state.
    /// </summary>
    /// <param name = "_value">An enabling state.</param>
    void setEnabled(boolean _value)
    {
    }

    /// <summary>
    /// Gets a name of the destination.
    /// </summary>
    /// <returns>The name.</returns>
    str getName()
    {
    }

    /// <summary>
    /// Creates a file destination for current settings.
    /// </summary>
    /// <param name = "_destinationContext">A destination context.</param>
    /// <param name = "_isGrouped">Determines whether the current file destination is grouped with others.</param>
    /// <returns>A new instance of a file destination.</returns>
    ERIFileDestination createDestination(ERDestinationExecutionContext _destinationContext, boolean _isGrouped)
    {
    }

    /// <summary>
    /// Gets a settings key. This key should start with or be an implementation class name. It should also be persistent and should not be changed over time.
    /// This key will be used to retrieve this type of settings from a settings storage.
    /// </summary>
    /// <remarks>Examples of good keys: MyCustomDestinationSettings, MyCustomDestinationSettings#UniqueKey.</remarks>
    /// <returns>The settings key.</returns>
    str getKey()
    {
    }

    /// <summary>
    /// Validates the settings.
    /// </summary>
    void validate()
    {
    }
}
```

This interface lets you offer parameters of a custom destination in the ER destinations dialog box, so that they can be set at design time. The configured destination can then be used at runtime to store generated outbound documents.

To learn more about this interface, complete the example in [Implement a custom destination for generated documents](er-custom-file-destination.md).

## Additional resources

[Electronic reporting (ER) overview](general-electronic-reporting.md)

[Electronic reporting (ER) destinations](electronic-reporting-destinations.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
