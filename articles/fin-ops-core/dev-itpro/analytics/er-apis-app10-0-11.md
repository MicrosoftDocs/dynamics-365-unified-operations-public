---
# required metadata

title: ER framework API changes for Application release 10.0.11
description: This topic describes how the API of the Electronic reporting (ER) framework has been changed in Microsoft Dynamics 365 Finance, release 10.0.11
author: NickSelin
manager: AnnBe
ms.date: 04/02/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope:  Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global 
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2020-04-01
ms.dyn365.ops.version: 10.0.11
---

# ER framework API changes for Application release 10.0.11

[!include [banner](../includes/banner.md)]

This topic describes how the API of the Electronic reporting (ER) framework has been changed in Microsoft Dynamics 365 Finance, release 10.0.11.

## API to run a format mapping for generation of outbound documents

When you need to generate an [outbound document](general-electronic-reporting.md#configuring-data-model-mappings-for-outgoing-documents),
you run an ER [format mapping](general-electronic-reporting.md#FormatComponentInbound). Most of ER format mappings are configured as containing a data source of the **Data model** type. A certain [model mapping](general-electronic-reporting.md#data-model-and-model-mapping-components) must be found at runtime as the implementation of a [data model](general-electronic-reporting.md#data-model-and-model-mapping-components) for which this data source has been configured.

When an ER format mapping is called from an execution point in the source code by using the [initial](er-apis-app73.md#code-to-run-a-format-mapping-for-data-export) API of the ER framework, a model mapping is found taking into account the
settings of the corresponding ER [configurations](general-electronic-reporting.md#Configuration) (default model mapping flag and country/region codes) containing a model mapping component. See [Configure country context dependent ER model mappings](er-country-dependent-model-mapping.md) for more.

In some cases, you need to specify an additional criteria to find the most appropriate model mapping while an ER format mapping is called from a particular place of the X++ code. For instance, you have an ER format mapping that has been configured as using a data model for which you have 2 model mappings. The 1st model mapping is marked as a default one as it can guarantee the smooth execution of this ER format mapping whenever it is called from every available at this moment execution point. You implement in X++ a new execution point from
which you want to call this ER format mapping forcing it to use the 2nd model mapping as it will perform better with other conditions of this call (provided arguments, available resource of the current application instance, etc.).

For doing this, you need to configure your model mapping as containing an integration point. At the data source properties page, you can mark a singe data source of your model mapping as the component of this integration point.

![ER model mapping designer page](./media/er-api-ds-integration-point.gif)

Then, you can use a new API of the ER framework to call an ER format mapping
forcing it to use a model mapping that has been configured as containing a
particular integration point. The sample code below explains how this new API
can be used.

```
using Microsoft.Dynamics365.LocalizationFramework;
using Microsoft.Dynamics365.LocalizationFramework.XppSupportLayer;

class ERIntegrationPointCodeSamples extends RunBaseBatch
{
    private ERFormatMappingId formatMappingId;

    public void run()
    {
        var runner = ERObjectsFactory::createFormatMappingRunByFormatMappingId(this.formatMappingId, 'OutboundFileName', true);
        var integration_point = new ERIntegrationPointFactory().WithObjectIntegrationPoint('SalesInvoiceDP').ToIntegrationPoint();
        /// new ERIntegrationPointFactory().WithTableRecordsIntegrationPoint(tableName)
        /// new ERIntegrationPointFactory().WithTableIntegrationPoint(tableName)
        /// new ERIntegrationPointFactory().WithObjectIntegrationPoint(className)
        /// new ERIntegrationPointFactory().WithClassIntegrationPoint(className)
        runner.withIntegrationPoint(integration_point).run();
    }
}
```

>
> Note that the only data source of the **Table record**, **Table**, **Class** or **Object** type can be marked as the component of the model mapping integration point. 
> 
> Note that the only a single data source can be currently used as the component
of the model mapping integration point.
>
> Note that the integration point will be considered in the selection of the most appropriate model mapping as one more criterion in addition to all existing ones.

Similar to the current behavior, an error will be thrown at runtime when more than one model mapping with the requested integration point will be found among model mappings that are applicable for the running ER format mapping.

## API to display a format mapping lookup

The [initial](er-apis-app73.md#code-to-display-a-format-mapping-lookup) API of the ER framework to lookup an ER format mapping utilizes the data model name and container name as text constants. This lookup offers the only ER format mappings of the only one data model that has the specified names and has been met first in the ER configurations list.

A new API of the ER framework allows you to implement the same lookup by using the configured integration point. This lookup will offer all ER format mappings containing a data source of the **Data model** type for which a model mapping with the specified integration point is available regardless of a data model for which it has been configured.

```
using Microsoft.Dynamics365.LocalizationFramework;
using Microsoft.Dynamics365.LocalizationFramework.XppSupportLayer;

class ERIntegrationPointCodeSamples extends RunBaseBatch
{
    private ERFormatMappingId formatMappingId;

    public void formatMappingLookup(FormReferenceControl _referenceGroupControl)
    {
        var integration_point = new ERIntegrationPointFactory().WithIntegrationPointKey('SalesInvoiceDP').ToIntegrationPoint();
        ERObjectsFactory::createFormatMappingTableLookupForIntegrationPoint(
            integration_point,
            _referenceGroupControl
            ).performFormLookup();
    }
}
```
