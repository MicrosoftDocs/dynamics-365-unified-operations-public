---
title: Extension points for packing slips during order fulfillment
description: This article shows how to use customizations to add extension points to packing slips during customer order fulfillment.
author: josaw1
ms.date: 03/29/2018
ms.topic: article
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2018-03-31
ms.dyn365.ops.version: 7.3.2
ms.custom: 
ms.search.industry: Retail
---

# Extension points for packing slips during order fulfillment

[!include [banner](../includes/banner.md)]

When you generate packing slips for customer orders from the point of sale (POS), you might want to print the item weight on the packing slip. You might also want to add custom information about the package, information about how to call the shipping carrier for the shipping rates, or information about how to return the package. To handle these scenarios, extension points for the packing slip process for order fulfillment have been added in Headquarters, in the commerce runtime (CRT), which is the business logic layer, and in the POS. These extension points let you add custom flow and logic through extensions.

## POS
In the POS, a new request handler that is named **PrintPackingSlipClientRequestHandler** lets you override extensions. This request is called when you select the **Print packing slip** button in the POS. By overriding this request, you can use custom logic in the POS. For example, you can call your own printing methods and print additional information.

For example, by default, you can print the packing slip in PDF format. By overriding the POS client request, you can print the packing slip in a different format. Alternatively, you can check for a specific condition, and then print or stop printing the packing slip, based on that condition. You can also do validation before you print, and prevent printing or custom logic. However, if you want to change the actual data that is printed, you must modify the business logic in CRT and Headquarters.

### Override PrintPackingSlipClientRequestHandler
To override any request in the POS, use the following override handler pattern in the POS.

**Example**

```typescript
import { PrintPackingSlipClientRequestHandler } from "PosApi/Extend/RequestHandlers/StoreFulfillmentRequestHandlers";
import { PrintPackingSlipClientRequest, PrintPackingSlipClientResponse } from "PosApi/Consume/SalesOrders";
import { ClientEntities } from "PosApi/Entities";
/**
 * Override request handler class for printing packing slip request.
 */
export default class PrintPackingSlipClientRequestHandlerExt extends PrintPackingSlipClientRequestHandler {
    /**
     * Executes the request handler asynchronously.
     * @param {PrintPackingSlipClientRequest<PrintPackingSlipClientResponse>} The request containing the response.
     * @return {Promise<ICancelableDataResult<PrintPackingSlipClientResponse>>} The cancelable promise containing the response.
     */
    public executeAsync(request: PrintPackingSlipClientRequest<PrintPackingSlipClientResponse>):
        Promise<ClientEntities.ICancelableDataResult<PrintPackingSlipClientResponse>> {
            // Do the extension logic here before calling the default handler.
            return this.defaultExecuteAsync(request);
        }
}
```

After you override the request, update the manifest.json file with the new request handler information.

```typescript 
"requestHandlers": [
    {
        "modulePath": "Handlers/PrintPackingSlipClientRequestHandlerExt"
    }
]
```

## CRT
Similar to the POS client request handler, new requests have been added in the CRT to enable extension of custom logic.

### MarkAsPickedRealtimeRequest
The **MarkAsPickedRealtimeRequest** request marks the fulfillment lines as picked. You can add custom logic before the line is marked as picked. For example, you can change a property. Later, the picked line information will be used to print the packing slip. Based on your scenario, you can override this request, or add pre-triggers or post-triggers. 

For example, for the fulfillment lines, you want to calculate item weight, and so on. In this case, you can customize the service. 

> [!NOTE]
> If the logic that you require for your customization must be determined in Headquarters, you can customize at the Headquarters level instead of customizing in the CRT. For example, if you want to get the item weight for each line, but that information is available only in Headquarters. In this case, you can customize the relevant real-time service methods and then return the result from Headquarters to the CRT.

### PackFulfillmentLinesRealtimeRequest
The **PackFulfillmentLinesRealtimeRequest** request updates the status of the fulfillment lines to **Partially packed** or **Packed.** Based on your scenario, you can override this service, or add pre-triggers or post-triggers. 

## Headquarters
In Headquarters new real-time service methods have been added to get the packing slip information, and to add custom information or logic through extension. If your customization requires that data or logic be done in Headquarters, you can customize these methods by using the extension patterns. Additionally, if you require an extension scenario that uses the transaction service client class, you can call these methods from the CRT.

### RetailTransactionServiceFulfillment
All the new methods that are related to the packing slip process for order fulfillment were added in the **RetailTransactionServiceFulfillment** class.

### GetPackingSlipsData
The **GetPackingSlipsData** method returns all the packing slip information by passing the sales ID as a parameter. 

### GetFulfillmentLinesByPackingSlipId
The **GetFulfillmentLinesByPackingSlipId** method returns the fulfillment lines, based on the packing slip ID. For example, you can use this method if you have the packing slip ID, and you want to get the sales lines that are relevant to that packing slip ID.

### MarkFulfillmentLinesAsPacked
The **MarkFulfillmentLinesAsPacked** method updates the status of the fulfillment lines to packed by taking the fulfillment details as a parameter in XML string format. The POS calls the CRT to mark the selected lines from the POS user interface (UI) as picked. The **MarkAsPickedRealtimeRequest** request in the CRT then calls the **MarkFulfillmentLinesAsPacked** real-time service method in Headquarters to set the line status as **Packed**.

To add custom logic or return additional information when the line is marked as packed and returned for printing, you can customize the **packingSlipExtensionPoint** method.

### packingSlipExtensionPoint
You can customize the **packingSlipExtensionPoint** method to add custom logic or return custom information together with the packing slip ID. This custom information includes packing information or a delivery note. This method is typically added for extensions for custom scenarios. This method is called from the **MarkFulfillmentLinesAsPacked** method by using the chain of command extensibility point. The **MarkFulfillmentLinesAsPacked** method is run from the real-time service call that the CRT code makes.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
