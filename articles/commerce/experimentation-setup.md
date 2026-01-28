---
title: Set up an experiment
description: Learn how to set up an experiment in a partner service in Microsoft Dynamics 365 Commerce.
author: sushma-rao 
ms.date: 01/22/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2020-09-30
ms.custom: 
  - bap-template
---

# Set up an experiment

This article describes how to set up an experiment in a partner service in Microsoft Dynamics 365 Commerce.

After you [define a hypothesis and determine what success metrics you want to use](experimentation-identify.md), set up your experiment in the partner service. The following diagram shows all of the steps involved in setting up and running an experiment on an e-Commerce website in Dynamics 365 Commerce. Additional steps are covered in separate articles.

:::image type="content" source="./media/experimentation_setup.svg" alt-text="Screenshot of the experimentation user journey showing the setup step.":::

## Set up your experiment in the partner service
Choose a partner service to run and monitor your experiment, and set up the experimentation connector. These prerequisites are listed in [Experimentation in Dynamics 365 Commerce](experimentation-overview.md).

Follow the steps required to create your experiment in the partner service. If the connector is configured properly, the complete list of experiments you set up in the partner service appears in Commerce site builder within about five minutes.

## Set up your success metrics
Every experiment needs metrics to measure the effect of the variations and to validate the hypothesis. To enable the computation of metrics in the partner service using live telemetry events from Dynamics 365 Commerce, complete the following the steps.

To set up your success metrics for out-of-the-box modules, follow these steps:

1. In Commerce site builder, select **Pages** in the left navigation pane, and then select the page that you want to collect metrics for. 
1. Go to the **Event IDs to track** section in the right property pane of the page or module you want to track.
1. Select **View**. A list of all click event IDs is displayed. Copy the event that you want to track, and then paste the event key into the designated location in the partner service. If you need more than one event, copy the keys one at a time. 
1. For page views, use the SHA-256 hash value of the page name in site builder appended with `.PageView`. For example, the event ID for `Homepage.PageView` is `e217eb66c7808ecc43b0f5c517c6a83b39d72b91412fbd54a485da9d8e186a9`.
1. Take any other steps for tracking metrics as required in the partner service.

For custom module user actions, follow these steps to instrument the click events:

1. Prepare a **TelemetryContent** object for the module by using the following function. This function takes the page name, module name, and SDK-provided default telemetry object as inputs.

    ```TypeScript
    getTelemetryObject(pageName: string, moduleName: string, telemetry: ITelemetry): ITelemetryContent
    ```
    
    The following is an example: 
    
    ```TypeScript
    private readonly telemetryContent: ITelemetryContent = getTelemetryObject(this.props.context.request.telemetryPageName!, this.props.friendlyName, this.props.telemetry);
    ```
    
1. Create the payload data that contains information on what needs to be captured. For buttons and other static controls, you can include **etext** such as "Shop now" or "Search". For components with user actions, such as selecting a product card, you can send the **recid** which is the record ID of the product or the product ID.

    ```TypeScript
    getPayloadObject(eventType: string, telemetryContent: ITelemetryContent, etext: string, recid?: string): IPayLoad
    ```
    As an example for static controls, pass the button text string as shown in the following code:

    ```TypeScript
    const payLoad = getPayloadObject('click', this.props.telemetryContent, 'Shop Now', '');
    ```
    As an example for product user actions, pass the product recordId as shown in the following code:

    ```TypeScript
    const payLoad = getPayloadObject('click', telemetryContent!, '', product.RecordId.toString());
    ```
    
1. Call the **OnClick** function to register the event.

    ```TypeScript
    onTelemetryClick = (telemetryContent: ITelemetryContent, payLoad: IPayLoad, linkText: string) => () =>
    ```

    For example:

    ```TypeScript
    onClick: onTelemetryClick(this.props.telemetryContent, payLoad, linkText)
    ```

## Previous step
[Identify a hypothesis and determine metrics for an experiment](experimentation-identify.md)

## Next step
[Connect and edit an experiment](experimentation-connect-edit.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
