---
title: Enable label printing using external label service solutions
description: This article describes how to set up and print labels using external label service solutions.
author: GalynaFedorova
ms.author: gfedorova
ms.reviewer: kamaybac
ms.search.form: WHSLabelLayout, WHSLabelLayoutDataSource
ms.topic: how-to
ms.date: 03/27/2023
ms.custom: bap-template
---

# Enable label printing using external label service solutions

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

The label printing integration with external service feature in Microsoft Dynamics 365 Supply Chain Management provides an effective solution for printing labels using any external labeling solutions. This feature allows direct interaction between Microsoft Dynamics 365 Supply Chain Management and third-party solutions by providing framework for communication using HTTP APIs, without the need for a Document Routing Agent. With this functionality, businesses can design and print various types of labels using third-party labeling products, such as Seagull Scientific BarTender, Loftware NiceLabel.

The following illustrations provide a comparison between the current functionality of printing labels using the Document routing agent and using an external service. This will help businesses understand the benefits and drawbacks of each method, enabling them to make an informed decision on the best solution for their needs.

[<img src="media/print-labels-using-dra.png" alt="Print labels using DRA." title="Print labels using DRA" width="720" />](media/print-labels-using-dra.png#lightbox)

For more details about Document routing framework, visit the link: [Document routing agent](../../fin-ops-core/dev-itpro/analytics/install-document-routing-agent.md)

[<img src="media/print-labels-using-external-service.png" alt="Print labels using External service." title="Print labels using External service" width="720" />](media/print-labels-using-external-service.png#lightbox)

In this article we'll focus on the second method, using external service and how to set it up.

## Enable external label printing solution

To enable external label printing solution, you must set up the following:

- **[External service definition](#service-definition)** – Define how to call the external API. The definition consists of one or multiple operations.
- **[External service instance](#service-instance)** – This represents one specific deployment of the service described by the External service definition. It specifies the URL of the service and the authentication secret to be used. For each external service definition, you can use one or more instances; for example, if you have multiple warehouses, each with its own on-premises installation of labeling software.
- **[Label printers](#label-printers)** – Defines the printers that are managed by the labeling service and will be used for printing labels.
- **[Document routing setup](#document-routing)** – Define which printer to use for which layout in a particular business process.
- **[Label layout](#label-layout)** – Define label layout definition.

## <a name="service-definition"></a>External service definition configuration

External service definition defines how the service needs to be called. This configuration depends on the API definitions that external service supports. Typically, such definitions are provided by the external service provider.

Follow these steps to set up external service definition.

1. Go to **Warehouse management \> Setup \> External services \> External service definitions**.
1. On the Action Pane, select **New** to create an external service definition.
1. Set the following values for the new service definition:
    - **External service definition** – Enter a name for the definition (for example, *External*).
    - **Description** – Enter a short description of the definition (for example, *External*).
1. Select **Edit operations** to define the service operation.
External service operations define how the system will format the HTTP request to the external service.
You must add at least one operation to the service, which will be used to print the label.  

1. You can set the following properties on an operation:
    - **HTTP method** – Select the HTTP method used (GET/POST/PUT).
    - **Operation timeout** – Select the operation timeout (for example, *2000*).
    - **Request body type** – Select the type of the body that is expected by the service. Select *Raw* if the service expects an XML or JSON message. Select *form-data* if the service expects HTTP form-data formatted data.
    - **Relative URL** – Define the relative part of the URL.  This value is provided by the external service provider.
    - **HTTP request headers**. If the **Request body type** is *form-data* encoded, you can then provide the names of the form data fields and their values; if the **Request body type** is *Raw*, you can then specify the body itself and the content type (using the MIME Content type identification, for example *application/xml*, *application/json* or *text/plain*)

1. You can use the following substitution placeholders in either the header values, the form-data values or the request body:
    - *$auth.secret$* will be replaced by the authentication secret configured on the External service instance. Use it to store a shared key, token or password required to authenticate to the External service instance.
    - *$label.printer$* will be replaced by the name of the printer configured later in the process. Use it to signal to the external service where to print the label to.
    - *$label.body$* will be replaced by the label generated from a Label layout or Document routing layout. You can also use the base64 formatting option ($label.body:base64$), if the externals service expects a base64 encoded value of ZPL script.
1. Go back to the External service definition.
1. Expand **Label print service** tab.
1. In the **Print operation** field, select API operation that has been created. This operation will be used to print the label.

## <a name="service-instance"></a>External service instance configuration

External service instance defines a specific instance of the external service.

1. Go to **Warehouse Management \> Setup \> External services \> External service instances**.
1. On the Action Pane, select **New** to create an external service instance.
1. Set the following values for the new service instance:
    - **External service instance** – Enter a name for the instance (for example, *External*).
    - **Description** – Enter a short description of the definition (for example, *External*).
    - **External service definition** – Select the service definition to use. The example service definition value that was suggested earlier in this article was *External*.
1. Expand **General** tab and set the following values:
    - **Base URL** – Define the hostname of the external service.
    - **Authentication secret** – Enter the authentication secret (password or shared key) that will be used to authenticate the service.
    - **Logging level** – Select *Successes and errors*.
    - **Log request bodies** – Select *Successes and errors*.

## <a name="label-printers"></a>Printer setup

Use the below procedure to link a printer with the external print service.

1. Go to **Warehouse Management \> Setup \> Document routing \> Label printers**.
1. On the Action Pane, select **New** to setup a printer.
1. Set the following values for the new printer:
    - **Connection type** – Select *Document routing agent/Hybrid* if you're using a DRA printer or *External label service* if you're using a cloud printer setup through external service. *Document routing agent/Hybrid* connection type allows you to use DRA as a fallback if the external service isn't able to print the label. *External label service connection type* allows you to configure a printer that is only accessible through the external label service.
    - **Printer name** – Enter the printer name. This value represents an internal Supply Chain Management printer name. If this printer is already configured as a DRA printer, you can select the printer from the lookup dialog. To set up an external service, you need to specify the printer name. It must not be a name that is already used by a DRA printer. We recommend that you use a prefix or another method to keep the names separate from printers that you might register through the DRA in the future.
    - **Label print service instance** – Select the service instance to use. The example service instance value that was suggested earlier in this article was *External*.
    - **Label print service printer name** – Enter printer name as it is defined in the external service. This value represents an external printer name used within the external service.

## <a name="label-layout"></a>Label layout configuration

For more information on how to set up Label layout follow this link [Print license plate labels using  label layouts](print-license-plate-labels-using-label-layouts.md).

Using label layouts, you have the ability to configure the label layout using different ways:

- Use ZPL or other printer command language directly. This has so far been the default option of specifying label layouts in Supply Chain Management.
- Specify XML, JSON or similarly formatted data to be used by the external service to generate and print the label layout.

An example of using a JSON request body for an external label service.

Let us make the assumption that the external service has an operation that requires the following JSON body to print a label to a specific printer with several variables:

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

Part of this JSON request body will be generated by the label layout (the data specific to one label) and then embedded within the external service operation’s request body definition (selected printer and other data not specific to label). As the printer is provided by the $label.printer$ substitution, this part will go into the external service operation. The label file and the variables are specific to a label, so this part of the request should be placed in the label layout:

External service operation’s request body:

```JSON
{
"printer": "$label.printer$",
$label.body$
}
```

Label layout (for example, a license plate label):

```JSON
"labelfile": "/Labels/SimpleLicensePlateLabel1",
"variables": {
    "Item": "$ItemId$",
    "Container": "$LicensePlateId"
}
```

## <a name="document-routing"></a>Document routing configuration

For more information on how to set up document routing follow this link [Print license plate labels using  label layouts](print-license-plate-labels-using-label-layouts.md).

## Run a scenario to print custom labels

If you want to experiment with printing labels, you can set up a scenario for printing location labels. For more information, see [Custom label layouts printing](custom-label-layouts-and-printing.md). Follow the instructions there, and confirm that the scenario that's described in this article is supported.
