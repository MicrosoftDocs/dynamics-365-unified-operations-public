---
# required metadata

title: Electronic reporting framework API changes for Application update 10.0.17
description: This topic describes how the APIs of the Electronic reporting (ER) framework have been changed in Microsoft Dynamics 365 Finance version 10.0.17.
author: NickSelin
ms.date: 12/07/2020
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
ms.search.validFrom: 2020-12-01
ms.dyn365.ops.version: 10.0.17
---

# Electronic reporting framework API changes for Application update 10.0.17

[!include [banner](../includes/banner.md)]

This topic describes how the application programming interfaces (APIs) of the Electronic reporting (ER) framework have been changed in Microsoft Dynamics 365 Finance version 10.0.17.

## <a name="er-api-run-format-with-action-code"></a>API to run a format mapping that provides a user action code to run action-dependent destinations

To generate an [outbound document](general-electronic-reporting.md#configuring-data-model-mappings-for-outgoing-documents), you must run an ER format mapping. When the [initial](er-apis-app73.md#code-to-run-a-format-mapping-for-data-export) API of the ER framework is used to call an ER format mapping, all [destinations](electronic-reporting-destinations.md#applicability) that were configured for components of the format are always run. To review the sample code for a call of this type, see [Add a report service class](er-quick-start1-new-solution.md#ServiceClass).

```xpp
// Call ER to generate the report.
ERIFormatMappingRun formatMappingRun = ERObjectsFactory::createFormatMappingRunByFormatMappingId(formatMappingId, DefaultExportedFileName);
if(formatMappingRun.parmShowPromptDialog(true))
{
    formatMappingRun.withParameter(parameters);
    formatMappingRun.withFileDestination(_contract.getFileDestination());
    formatMappingRun.run();
}
```

In some cases, when an ER format mapping is called from a specific place in the X++ code, you must specify an action that the user performs by running an ER format, so that only action-dependent destinations are run instead of all the ER destinations that are configured for that format.

For example, you have an ER format that is based on [Print management](document-reporting-services.md) settings. When you call this ER format to preview a generated document, you expect that only the [Screen](er-destination-type-screen.md) destination will be run. However, when you call the same ER format to send a generated document as the attachment of an outbound email message, you expect that only the [Email](er-destination-type-email.md) destination will be run.

To achieve these results, you must configure action-dependent ER destinations for the ER format. For more information, see [Configure action-dependent ER destinations](er-action-dependent-destinations.md).

After you've completed the configuration, you can use the new API of the ER framework to call an ER format mapping that provides a user action code that runs only destinations that were configured for the provided action. The following example shows how you can change the previously mentioned sample code to use this new API to run an ER format that provides the **View** action.

```xpp
// Call ER to generate the report.
ERIFormatMappingRun formatMappingRun = ERObjectsFactory::createFormatMappingRunByFormatMappingId(formatMappingId, DefaultExportedFileName);
if(formatMappingRun.parmShowPromptDialog(true))
{
    formatMappingRun.withParameter(parameters);
    formatMappingRun.withFileDestination(_contract.getFileDestination());

    var formatMappingRunWithAction = formatMappingRun as ERIFormatMappingRunWithDestinationAction;
    formatMappingRunWithAction.withDestinationAction(ERDestinationAction::View);
    formatMappingRun.run();
}
```

> [!IMPORTANT]
> To set up action-dependent destinations and force the ER framework to use the provided action code, you must first turn on the **Configure specific ER destinations to be used for different PM actions** feature in the [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md#the-feature-management-workspace) workspace.

## Additional resources

[Electronic reporting (ER) overview](general-electronic-reporting.md)

[Electronic reporting (ER) destinations](electronic-reporting-destinations.md)

[Configure action-dependent ER destinations](er-action-dependent-destinations.md)

[Design a new ER solution to print a custom report](er-quick-start1-new-solution.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
