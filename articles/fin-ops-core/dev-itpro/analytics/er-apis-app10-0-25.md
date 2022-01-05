---
# required metadata

title: Electronic reporting framework API changes for Application update 10.0.25
description: This topic describes how the APIs of the Electronic reporting framework have been changed in Microsoft Dynamics 365 Finance version 10.0.25.
author: NickSelin
ms.date: 01/05/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global 
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2022-01-01
ms.dyn365.ops.version: 10.0.25
---

# Electronic reporting framework API changes for Application update 10.0.25

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This topic describes how the application programming interfaces (APIs) of the [Electronic reporting (ER)](general-electronic-reporting.md) framework have been changed in Microsoft Dynamics 365 Finance version 10.0.25.

## API to enable running a model mapping in batch mode

The [initial](er-apis-app73.md#code-to-run-a-format-mapping-for-data-import) API of the ER framework allows you to run an ER [model mapping](er-overview-components.md#model-mapping-component) for data import in interactive mode. To specify an ER [format](er-overview-components.md#format-component) for inbound file parsing and an ER model mapping for application data update, this API uses the format name as well as the integration point.

The new `ERIModelMappingDestinationWithVirtualSourceRun` public interface of the ER framework lets you run an ER model mapping in batch mode for data import of an inbound file. To provide the file, you can manually select it by using the ER user interface (UI) or provide it programmatically.

The code of the `ERModelMappingDestinationRun` class shows how this new API can be used to include the **Run in the background** tab on the dialog box to run data import in batch mode.

```xpp
private ERModelMappingDestinationRunController getControllerInternal()
    {
        if (!controller)
        {
            controller = ERModelMappingDestinationRunController::construct();
            controller.parmShowDialog(showPromptDialog);
            controller.showBatchTab(showPromptDialog && showBatchTab && this.isBatchEnabledForFileSource());
            controller.parmDialogCaption(this.getBatchJobCaption());
            controller.parmModelMappingRun(this);
            controller.parmModelDefinitionParameters(parameters);
            controller.parmHiddenParameters(hiddenParameters);
            controller.parmIsImportLoadingFilesFromSource(this.getImportFormatFileSourceContract() != null);
        }
        return controller;
    }

    private boolean isBatchEnabledForFileSource()
    {
        var fileSource = this.getImportFormatFileSourceContract();
        if (ERCast::asAny(fileSource) is ERImportFormatDatasourceByVirtualFileSourceContract)
        {
            return useVirtualImportFormatSource;
        }
        else
        {
            return ERCast::asAny(fileSource) is ERImportFormatDatasourceByFileSourceContract;
        }
    }
```

To learn more about this interface, complete the examples in the topic, [Import data from manually selected files in batch mode](er-configure-data-import-batch.md).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
