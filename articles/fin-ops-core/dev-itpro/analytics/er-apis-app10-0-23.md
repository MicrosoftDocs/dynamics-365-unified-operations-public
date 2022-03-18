---
# required metadata

title: Electronic reporting framework API changes for Application update 10.0.23
description: This topic describes how the APIs of the Electronic reporting (ER) framework have been changed in Microsoft Dynamics 365 Finance version 10.0.23.
author: NickSelin
ms.date: 10/05/2021
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
ms.search.validFrom: 2021-10-01
ms.dyn365.ops.version: 10.0.23

---

# Electronic reporting framework API changes for Application update 10.0.23

[!include [banner](../includes/banner.md)]

This topic describes how the application programming interfaces (APIs) of the [Electronic reporting (ER)](general-electronic-reporting.md) framework have been changed in Microsoft Dynamics 365 Finance version 10.0.23.

## <a name="er-api-extend-file-source"></a>API to extend the list of ER sources of inbound documents

To implement a custom ER [source](er-configure-data-import-sharepoint.md#configure-er-sources-for-the-er-format) of inbound documents, use the following public interfaces:

- `ERIImportFile`
- `ERIImportFileSourceSettings`
- `ERIImportFileSourceSettingsStorage`

```cs
using Microsoft.Dynamics365.LocalizationFramework.XppSupportLayer;

namespace Microsoft.Dynamics365.LocalizationFramework
{
    /// <summary>
    /// The import file object.
    /// </summary>
    public interface ERIImportFile : ERIFile
    {
        /// <summary>
        /// Gets or sets a file source settings key.
        /// </summary>
        string SourceSettingsKey { get; set; }

        /// <summary>
        /// Sets a file id. File ID should be unique string with max length 300.
        /// </summary>
        string FileId { set; }

        /// <summary>
        /// Gets or sets a file name. File name with max length 259.
        /// </summary>
        string Name { get; set; }

        /// <summary>
        /// Gets or sets a file created date time.
        /// </summary>
        utcdatetime CreatedDateTime { get; set; }

        /// <summary>
        /// Sets a file modified date time.
        /// </summary>
        utcdatetime ModifiedDateTime { set; }
    }
}
```

```xpp
using Microsoft.Dynamics365.LocalizationFramework;
using System.IO;

/// <summary>
/// Format source settings required to store settings for a specific sources for the import format.
/// </summary>
/// <remarks>
/// The implementation object should have static create(container) method for a proper packing.
/// </remarks>
public interface ERIImportFileSourceSettings extends SysPackable
{
    /// <summary>
    /// Gets a name of the source.
    /// </summary>
    /// <returns>The name.</returns>
    str getName()
    {
    }

    /// <summary>
    /// Validates the settings.
    /// </summary>
    /// <returns>True, if validated successful; otherwise - false.</returns>
    boolean validate()
    {
    }

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
    /// Gets a settings key, this key should start with or be an implementation class name. This key should also be persistent and shouldn't be changed over time.
    /// This key will be used to retrieve this type of settings from a settings storage.
    /// </summary>
    /// <remarks>Examples of good keys: MyCustomFileSourceSettings, MyCustomFileSourceSettings#UniqueKey.</remarks>
    /// <returns>The settings key.</returns>
    str getKey()
    {
    }

    /// <summary>
    /// Creates a file source for current settings.
    /// </summary>
    /// <param name = "_fileMask">A file mask.</param>
    /// <returns>A new instance of a file source.</returns>
    ERIFileSource createFileSource(str _fileMask)
    {
    }

    /// <summary>
    /// Post processing for resulted file. An action after file importing.
    /// </summary>
    /// <param name = "_args">Arguments for file post import process.</param>
    void fileImported(ERFileImportedArgs _args)
    {
    }

}
```

```xpp
/// <summary>
/// Provides access to the source settings storage.
/// </summary>
public interface ERIImportFileSourceSettingsStorage
{
    /// <summary>
    /// Adds settings to the format source settings storage.
    /// </summary>
    /// <param name = "_settings">A given settings to add.</param>
    public void addSettings(ERIImportFileSourceSettings _settings)
    {
    }

    /// <summary>
    /// Gets source settings by the key.
    /// </summary>
    /// <param name = "_key">A given key.</param>
    /// <returns>The source settings.</returns>
    public ERIImportFileSourceSettings getSettingsByKey(str _key)
    {
    }

}
```

These interfaces let you offer custom source parameters in the **ER source settings** dialog box, so that they can be set at design time. The configured source can be used to access, in a configured custom source, inbound documents that must be imported at runtime.

To learn more about this interface, complete the example in [Implement a custom source of inbound documents](er-custom-file-source.md).

## Additional resources

[Electronic reporting (ER) overview](general-electronic-reporting.md)

[Parse incoming documents](er-parse-incoming-documents.md)

[Configure access to SharePoint for file storage](er-configure-data-import-sharepoint.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
