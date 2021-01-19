---
# required metadata

title: Electronic reporting framework API changes for Application update 10.0.17
description: This topic describes how the application programming interfaces (APIs) of the Electronic reporting (ER) framework have been changed in Microsoft Dynamics 365 Finance version 10.0.17.
author: NickSelin
manager: AnnBe
ms.date: 12/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
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

## <a name="er-api-run-format-with-action-code">API to run a format mapping providing a user action code to execute action dependent destinations</a>

To generate an [outbound document](general-electronic-reporting.md#configuring-data-model-mappings-for-outgoing-documents), you must run an ER [format mapping](general-electronic-reporting.md#FormatComponentInbound). When the [initial](er-apis-app73.md#code-to-run-a-format-mapping-for-data-export) API of the ER framework is used to call an ER format mapping, all [destinations](electronic-reporting-destinations.md#applicability) that were configured for components of this format are always executed. You can review the sample code of such a call in the [Add a report service class](er-quick-start1-new-solution.md#ServiceClass) section of the [Design a new ER solution to print a custom report](er-quick-start1-new-solution.md) page.

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

In some cases, when an ER format mapping is called from a specific place in the X++ code, you must specify an action that user performs by running an ER format to execute the only action dependent destinations from all configured for this format destinations. For example, you might call an ER format based on [Print management](document-reporting-services.md) (PM) settings to preview a generated document expecting that the only [Screen](er-destination-type-screen.md) destination will be executed at this time. At the same time, you might call the same ER format to send a generated document out as the attachment of an outbound email expecting that the only [Email](er-destination-type-email.md) destination will be executed at this time.  

To achieve this, you must configure action dependent ER destinations for an ER format. To learn how action dependent ER destination can be configured, see [Configure action dependent ER destinations](er-action-dependent-destinations.md).

You can then use the new API of the ER framework to call an ER format mapping providing a user action code to execute the only destinations that were configured for the provided action. The presented below example shows how the mentioned above sample code can be changed to use this new API for running an ER format providing the **View** action.

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

> [!NOTE]
> Be aware that you can set up action dependent destinations and force ER framework to use the provided action code accordingly only when you enabled the **Configure specific ER destinations to be used for different PM actions** feature in the [Feature management](https://docs.microsoft.com/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview#the-feature-management-workspace) workspace.

## Additional resources

[Electronic reporting (ER) overview](general-electronic-reporting.md)

[Electronic reporting (ER) destinations](electronic-reporting-destinations.md)

[Design a new ER solution to print a custom report](er-quick-start1-new-solution.md)
