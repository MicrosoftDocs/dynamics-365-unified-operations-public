---
title: Print labels using an external service
description: This article describes how to set up and print labels using an external service.
author: GalynaFedorova
ms.author: gfedorova
ms.reviewer: kamaybac
ms.search.form: WHSLabelLayout, WHSLabelLayoutDataSource
ms.topic: how-to
ms.date: 03/27/2023
ms.custom: bap-template
---

# Print labels using an external service

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

This article describes how to set up and print labels using an external service. This feature allows direct interaction between Supply Chain Management and third-party solutions by providing a framework for communicating using HTTP APIs, without requiring the [Document Routing Agent](../../fin-ops-core/dev-itpro/analytics/install-document-routing-agent.md) (DRA). With this functionality, you can design and print various types of labels using third-party labeling products, such as Seagull Scientific BarTender, Loftware NiceLabel.

The following illustrations show how printing through the DRA compares to printing through an external service. They highlight the benefits and drawbacks of each method and can help you decide which printing solution best fits your business needs.

[<img src="media/print-labels-using-dra.png" alt="Print labels using DRA." title="Print labels using DRA" width="720" />](media/print-labels-using-dra.png#lightbox)

[<img src="media/print-labels-using-external-service.png" alt="Print labels using External service." title="Print labels using External service" width="720" />](media/print-labels-using-external-service.png#lightbox)

For more information about the document routing framework, see [Install the Document Routing Agent to enable network printing](../../fin-ops-core/dev-itpro/analytics/install-document-routing-agent.md).

For an example of how to set up this feature with a specific third-party label printing service (Loftware NiceLabel), see [Print labels using the Loftware NiceLabel label service solution](label-printing-using-nicelabel.md).

## Overview of required configurations

To enable label printing through an external service, you must set up the following elements:

- **[External service definition](#service-definition)** – Define how to call the external API. The definition consists of one or more operations.
- **[External service instance](#service-instance)** – Represents a specific deployment of the service described by the external service definition. It specifies the URL of the service and the authentication secret to be used. For each external service definition, you can use one or more instances (for example, to set up multiple warehouses, each with its own on-premises installation of labeling software).
- **[Label printers](#label-printers)** – Defines the label printers that are managed by the labeling service.
- **[Document routing setup](#document-routing)** – Defines which printer to use for which layout in a particular business process.
- **[Label layout](#label-layout)** – Defines a label layout.

The remaining sections of this article describe how to configure each of these elements.

## <a name="service-definition"></a>External service definition configuration

An external service definition defines how a particular service needs to be called. This configuration depends on the API definitions that the external service supports. Typically, such definitions are provided by the external service provider.

Follow these steps to set up external service definition.

1. Go to **Warehouse management \> Setup \> External services \> External service definitions**.
1. On the Action Pane, select **New** to create an external service definition.
1. Set the following values for the new service definition:
    - **External service definition** – Enter a name for the definition (for example, *External*).
    - **Description** – Enter a short description of the definition (for example, *External*).
1. On the Action Pane, select **Save**.
1. Expand the **External service operations** FastTab and select **Edit operations** from the FastTab toolbar.
1. The **External service operations** page opens. External service operations define how the system will format its HTTP requests to the external service. You must add at least one operation, which will be used to print labels. On the Action Pane, select **New** to add a new operation and then make the following settings for it:
    - In the header of the new record, make the following settings:
        - **External service definition** – This read-only field shows a value of *External*.
        - **External service operation** – Enter a name for the operation.
        - **Description** – Enter a short description of the operation.
    - On the **General** FastTab, make the following settings:
        - **HTTP method** – Select the HTTP method to use (*GET*, *POST*, or *PUT*).
        - **Operation timeout** – Select the operation timeout, in milliseconds (for example, *2000*). <!--KFM: In the NiceLabel topic, we have a discussion about this setting. Should we repeat that here? -->
        - **Request body type** – Select the type of the body that is expected by the service. Select one of the following values:
            - *Raw* – The service expects an XML or JSON message.
            - *form-data* – The service expects data formatted as an HTTP form.
        - **Relative URL** – Enter the relative part of the URL for calling the service. Your external service provider must provide this value.
    - Use the **Request query string** FastTab to ... <!--KFM: Description needed -->
    - Use the **HTTP request headers** FastTab to ... <!--KFM: Description needed -->
    - The **Request body (form data)** FastTab is shown when **Request body type** is *Form-data*. Use it to provide the names of the form data fields and their values. Use the toolbar to add or remove rows in the grid as needed and make the following settings for each of them:
        - **Key** – Enter the name of the form data field.
        - **Value** – Enter the value of the form data field.
        - **File name** – <!--KFM: Description needed -->
    - The **Request body (raw)** FastTab is shown when **Request body type** is *Raw*. Use it to specify the body content and the content type. Make the following settings:
        - **Content type** – Specify the MIME Content type identification (for example *application/xml*, *application/json*, or *text/plain*).
        - **Request body** – Enter the body content.

    You can use the following substitution placeholders in either the header values, the form-data values, or the request body:
    - `$auth.secret$` – Will be replaced by the authentication secret configured on the external service instance. Use it to store a shared key, token, or password required to authenticate with the external service instance.
    - `$label.printer$` – Will be replaced by the name of the printer configured later in the process. Use it to signal to the external service where to print the label to.
    - `$label.body$` or `$label.body:base64$` – Will be replaced by the label generated from a label layout or document routing layout. Use the base64 formatting version (`$label.body:base64$`) if the externals service expects a base64 encoded ZPL script.
1. On the Action Pane, select **Save**. Then select the **Close** button to return to the **External service definitions** page.
1. Expand **Label print service** tab and make the following settings:
    - **Printer operation** – Select the external service operation that will be used to print the label. This must be an operation that has already been defined for the current service definition, as described previously in this procedure (where we suggested a name of *External*).
    - **Variables print operation** – <!--KFM: Description needed -->
    - **Variable label layout template** – <!--KFM: Description needed -->
1. On the Action Pane, select **Save**.

## <a name="service-instance"></a>External service instance configuration

Each external service instance defines a specific instance of an external service.

1. Go to **Warehouse Management \> Setup \> External services \> External service instances**.
1. On the Action Pane, select **New** to create an external service instance.
1. Set the following values for the new service instance:
    - **External service instance** – Enter a name for the instance (for example, *External*).
    - **Description** – Enter a short description of the definition (for example, *External*).
    - **External service definition** – Select the service definition to use with this instance. The example service definition value that was suggested earlier in this article was *External*.
1. Expand **General** tab and make the following settings:
    - **Base URL** – Enter the hostname of the external service.
    - **Authentication secret** – Enter the authentication secret (password or shared key) that will be used to authenticate with the service.
    - **Logging level** – Specify the level at which to generate log entires. Choose one of the following values: <!--KFM: Maybe mention where we can read these log entries? -->
        - *Errors only* – Only log errors.
        - *Successes and errors* – Log both successes and errors (recommended <!--KFM: Right? -->).
        - *None* – Don't create any log entries.
    - **Log request bodies** –<!--KFM: Briefly describe what this means. -->Choose one of the following values: <!--KFM: Maybe mention where we can read these log entries? -->
        - *Errors only* – <!--KFM: Description needed -->
        - *Successes and errors* – <!--KFM: Description needed. Recommended? -->
        - *None* – <!--KFM: Description needed -->
    - **Service offline** – <!--KFM: Description needed -->
1. On the Action Pane, select **Save**.

## <a name="label-printers"></a>Printer setup

Use the following procedure to link a printer with the external print service.

1. Go to **Warehouse Management \> Setup \> Document routing \> Label printers**.
1. On the Action Pane, select **New** to add a printer to the grid.
1. Set the following values for the new printer:
    - **Connection type** – Select the type of connection used to communicate with the printer. Choose one of the following values:
        - *External label service* – To connect to a cloud printer through an external service, including printers that are only accessible through the external label service.
        - *Document routing agent/Hybrid* – To connect to a DRA printer or to use DRA as a fallback for the external service when the service isn't able to print the label.
    - **Printer name** – Enter or select the printer name. This value represents an internal Supply Chain Management printer name. If this printer is already configured as a DRA printer, you can select its name from the lookup dialog. To set up an external service, you must specify the printer name (the name must not already be used for a DRA printer). When entering a name for an external-service printer, we recommend that you use a prefix or another method to keep the names of external-service printers separate from printers that you might register through the DRA in the future.
    - **Batch print** – <!--KFM: Description needed -->
    - **Maximum file size** – <!--KFM: Description needed -->
    - **Label print service instance** – Select the service instance to use. The example service instance value that was suggested earlier in this article was *External*.
    - **Label print service printer name** – Enter printer name as it is defined in the external service. This value represents an external printer name used within the external service.
    - **Label print service execution policy** – <!--KFM: Description needed -->

## <a name="label-layout"></a>Label layout configuration

By using label layouts, you can configure the label layout in either of the following ways:

- Use ZPL or other printer command language directly.
- Specify XML, JSON, or a similar data format used by the external service to generate and print label layouts.

For more information on how to set up label layouts, see [License plate label layouts and printing](print-license-plate-labels-using-label-layouts.md).

The remainder of this section provides an example of how to use a JSON request body for an external label service. Suppose that the external service has an operation that requires the following JSON body to print a label to a specific printer (including several variables):

```JSON
{
"printer": "LABELPRINTER",
"labelfile": "/Labels/SimpleLicensePlateLabel1",
"variables": {
    "Item": "ITEM1",
    "Container": "CONTAINER1"
}
}
```

Part of this JSON request body will be generated by the label layout (with data for a specific label) and then embedded within the external service operation's request body definition (which specifies a printer and other data not specific to the label). Because the printer is provided by the `$label.printer$` substitution, this part will go into the external service operation. The label file and the variables are specific to each label, so this part of the request should be placed in the label layout.

The external service operation's request body could therefore look like this:

```JSON
{
"printer": "$label.printer$",
$label.body$
}
```

The label layout (for example, for a license plate label) could look like this:

```JSON
"labelfile": "/Labels/SimpleLicensePlateLabel1",
"variables": {
    "Item": "$ItemId$",
    "Container": "$LicensePlateId"
}
```

<!-- KFM: I assumed both code sames were JSON. True? -->

## <a name="document-routing"></a>Document routing configuration

For instructions on how to set up document routing, see [License plate label layouts and printing](print-license-plate-labels-using-label-layouts.md)

## Run a scenario to print custom labels

If you want to experiment with printing labels, you can set up a scenario for printing location labels. For more information, see [Custom label layouts printing](custom-label-layouts-and-printing.md). Follow the instructions there, and confirm that the scenario that's described in this article is supported.

## Additional resources

- [Label Layouts](print-license-plate-labels-using-label-layouts.md)
- [Document routing label layouts](document-routing-layout-for-license-plates.md)
- [Print labels using the Loftware NiceLabel label service solution](label-printing-using-nicelabel.md)
