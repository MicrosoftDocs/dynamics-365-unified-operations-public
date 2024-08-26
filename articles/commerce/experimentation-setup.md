---
title: Set up an experiment
description: This article describes how to set up an experiment in a third-party service in Microsoft Dynamics 365 Commerce.
author: sushma-rao 
ms.date: 07/26/2024
ms.topic: how-to
audience: Application User
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2020-09-30
ms.custom: 
  - bap-template
---

# Set up an experiment

This article describes how to set up an experiment in a third-party service in Microsoft Dynamics 365 Commerce.

After you [define a hypothesis and determine what success metrics you want to use](experimentation-identify.md), you'll need to set up your experiment in the third-party service. The following diagram shows all of the steps involved in setting up and running an experiment on an e-Commerce website in Dynamics 365 Commerce. Additional steps are covered in separate articles.

[ ![Experimentation user journey - Setup.](./media/experimentation_setup.svg) ](./media/experimentation_setup.svg#lightbox)


## Set up your experiment in the third-party service
By now you should have chosen your third-party service to run and monitor your experiment, and set up the experimentation connector. These prerequisites are listed in  [Experimentation in Dynamics 365 Commerce](experimentation-overview.md).

Follow the steps required to create your experiment in the third-party service. If the connector is configured properly, the complete list of experiments you set up in the third-party service will appear in Commerce site builder within about 5 minutes.

## Set up your success metrics
Every experiment needs metrics to measure the impact of the variations and to validate the hypothesis. Follow the steps below to enable the computation of metrics in the third-party service using live telemetry events from Dynamics 365 Commerce.

To set up your success metrics for out-of-the-box modules, follow these steps.

1. In Commerce site builder, select **Pages** in the left navigation pane, and then select the page that you want to collect metrics for. 
1. Go to the **Event IDs to track** section in the right property pane of the page or module you want to track.
1. Select **View**. A list of all click event IDs is displayed. Copy the event that you want to track, and then paste the event key into the designated location in the third-party service. If you need more than one event, copy the keys one at a time. 
1. For page views, use the SHA-256 hash value of the page name in site builder appended with `.PageView`. For example, the event ID for `Homepage.PageView` would be `e217eb66c7808ecc43b0f5c517c6a83b39d72b91412fbd54a485da9d8e186a9`.
1. Take any other steps for tracking metrics as required in the third-party service.

For custom module clicks, follow these steps to instrument the click events:

1. Prepare a **TelemetryContent** object for the module using the function below. This function takes the page name, module name, and SDK-provided default telemetry object as inputs.

    ```TypeScript
    getTelemetryObject(pageName: string, moduleName: string, telemetry: ITelemetry): ITelemetryContent
    ```
    
    The following is an example: 
    
    ```TypeScript
    private readonly telemetryContent: ITelemetryContent = getTelemetryObject(this.props.context.request.telemetryPageName!, this.props.friendlyName, this.props.telemetry);
    ```
    
1. Create the payload data that contains information on what needs to be captured. For buttons and other static controls, you can include **etext** such as “Shop now” or “Search”. And for components with clicks such as clicking on a product card, you can send the **recid** which is the record ID of the product or the product ID.

    ```TypeScript
    getPayloadObject(eventType: string, telemetryContent: ITelemetryContent, etext: string, recid?: string): IPayLoad
    ```
    As an example for static controls, pass the button text string as shown below:

    ```TypeScript
    const payLoad = getPayloadObject('click', this.props.telemetryContent, 'Shop Now', '');
    ```
    As an example for product clicks, pass the product recordId as shown below:

    ```TypeScript
    const payLoad = getPayloadObject('click', telemetryContent!, '', product.RecordId.toString());
    ```
    
1. Call the **OnClick** function to register the event.

    ```TypeScript
    onTelemetryClick = (telemetryContent: ITelemetryContent, payLoad: IPayLoad, linkText: string) => () =>
    ```

    The following is an example:

    ```TypeScript
    onClick: onTelemetryClick(this.props.telemetryContent, payLoad, linkText)
    ```

## Previous step
[Identify a hypothesis and determine metrics for an experiment](experimentation-identify.md) 


## Next step
[Connect and edit an experiment](experimentation-connect-edit.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
