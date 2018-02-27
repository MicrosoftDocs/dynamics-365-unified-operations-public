---
# required metadata

title: Extension points for packing slips during customer order fulfillment
description: This topic shows how to use customizations to add extension points to packing slips during customer order fulfillment.
author: mugunthanm
manager: AnnBe
ms.date: 02/13/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: mumani
ms.search.validFrom: 2018-03-31
ms.dyn365.ops.version: 7.3.2
---

#  Extension points for packing slips during customer order fulfillment
When you generate packing slips for customer orders from POS, you might want to include the item weight and print it on the packing slip. You might also want to add custom information about the package or add information about how to call the shipping carrier for the shipping rates, or add information about how to return the package. For these different scenarios we’ve added extension points in headquarters (HQ), common runtime (CRT), and point of sale (POS) during the order fulfillment packing slip process for extensions to add custom flow and logic.

## POS
In POS, a new request handler called **PrintPackingSlipClientRequestHandler** allows you to override extensions. You can override this request and use custom logic in POS. This request will be called when you click the **Print packing slip** button in POS. By overriding this request, you can call your own printing methods and print additional information. For example, by default, you can change the packing slip to print in PDF format. You can override the POS client request to print the packing slip in a different format or check for a certain condition, and then print or stop printing based those conditions. You can also do some validation before printing and prevent printing or custom logic. To change the data (what’s get printed) you need do that in the CRT (business logic).

### Override PrintPackingSlipClientRequestHandler
To override any request in POS, use the following the override handler pattern in POS.

**Sample**

```Typescript
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
After overriding, update the manifest.json file with the new request handler information.
```Typescript 
     "requestHandlers": [
        {
          "modulePath": "Handlers/PrintPackingSlipClientRequestHandlerExt"
        }
      ]
```
## CRT
Similar to the client, new requests have been added in the commerce runtime (business logic layer) for extending custom logic.

### MarkAsPickedRealtimeRequest
The **MarkAsPickedRealtimeRequest** request marks the fulfillment lines as picked. You can add custom logic, such as changing a property, before marking the line as picked. The picked line information will be later used for printing the packing slip. You can override this request or add pre- or post-triggers according to your scenario. 

**Example** For the fulfillment lines if you want to calculate item weight etc. the you can customize this service. 

> [!Note]
> If you need logic for your customization that must be determined in HQ, you can customize at the HQ level without customizing in the CRT. For example, for each line, if you want to get the item weight that is available only in HQ, then you can customize the relevant real-time service methods and return the result to CRT from HQ.

### PackFulfillmentLinesRealtimeRequest
The **PackFulfillmentLinesRealtimeRequest** request updates the status of the fulfillment lines to partially packed or packed. You can override this service or add pre- or post-triggers according to your extension scenario. 

## HQ
New real-time service methods added in Headquarters to get the packing slip information and for extension to add some custom information or logics. If your customization needs data or logic to be performed in Headquarters, then you can customize these methods using the extension patterns. You can also call these methods from the CRT in case you need an extension scenario that uses the transaction service client class.

### RetailTransactionServiceFulfillment
We added all the new methods related to this order fulfillment packing slip process in this class.

### GetPackingSlipsData
This method returns all the packing slip information by passing the Sales ID as the parameter. 

### GetFulfillmentLinesByPackingSlipId
Return the fulfillment lines based on the packing slip ID. For example, if you have the packing slip ID and want to get the sales lines that is relevant to that packing slip ID, then you can use this method.

### MarkFulfillmentLinesAsPacked
This method updates the status of the fulfillment lines to packed by taking the fulfillment details as parameter in XML string format. POS calls CRT to mark the selected lines from the POS user interface as picked. **MarkAsPickedRealtimeRequest** in CRT calls the **MarkFulfillmentLinesAsPacked** real-time service method in HQ to set the line status as marked. You can customize the **packingSlipExtensionPoint** method to add custom logic or return additional information when the line is marked as packed and returned for printing.

### packingSlipExtensionPoint
You can customize this method to add custom logic or return custom information along with the packing slip ID, such as packing information or delivery note. This method is typically added for extensions for custom scenarios. This method is called from the **MarkFulfillmentLinesAsPacked** method using the chain of command extensibility point. The **MarkFulfillmentLinesAsPacked** method is executed from the real-time service call made by the CRT code.
