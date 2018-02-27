---
# required metadata

title: Extensions required on packing slip print on Order fulfilment for the purposes of Shipping carrier integration
description: TBD
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

#  HQ, CRT and POS Extensions points for packing slip process during Customer order fulfillment:
Whenever you generate packing slip for customer orders from POS there may be scenario where you want to get the item weight and print it on the packing slip or add some custom information about the package or call shipping carrier to get the shipping rates and delivery process or how to return the package information etc. For these different scenarios we added the below extension points in HQ, CRT and POS during order fulfillment packing slip process for extensions to add custom flows and logics.

## Below is the list of extension points we added for this scenario:

## POS:
In POS we added new Request handler called PrintPackingSlipClientRequestHandler for the extensions to override. You can override this request and do some custom logic in POS. This request will be called whenever you click print packing slip button in POS. By overriding this request, you can call your own printing methods and print any additional information. Ex: By default, we print packing slip in receipt format you can change it to print in PDF format etc. You will override this POS client request to print packing slip in different format or check some condition and print or stop printing based some conditions or do some validation before printing and prevent printing, custom logic etc. To change the data (what’s get printed) you need do that in CRT (business logic).

## How to override PrintPackingSlipClientRequestHandler:
To override any request in POS you should follow the override handler pattern in POS:

### Sample:

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
After overriding, update the manifest.json file with this new request handler information:
```Typescript 
     "requestHandlers": [
        {
          "modulePath": "Handlers/PrintPackingSlipClientRequestHandlerExt"
        }
      ]
```
## Commerce Runtime (CRT):

Like the client side we have added few new requests in Commerce runtime (business logic layer) for extension to do some custom logics.

## Below are the new requests added for the packing slip fulfillment scenario:

## MarkAsPickedRealtimeRequest:
This request marks the fulfillment lines as picked. You can add some custom logic according to your scenario if you want to change some property or add some logic etc. before marking the line as picked. This picked line information will be later used for printing the packing slip. You can override this request or add pre or post trigger according to your scenario. 

**Ex:** For the fulfillment lines if you want to calculate item weight etc. the you can customize this service. 

> [!Note]
> If you need some logic for your customization that need to be determined in HQ then you can customize at HQ level also no need to customize in CRT. Ex: For each line if you want to get the item weight which is available only in HQ then you customize the relevant real time service methods and return the result to CRT form HQ itself.

## PackFulfillmentLinesRealtimeRequest:
Updates the status of the fulfillment lines to partially packed or packed. You can override this service or add pre or post trigger according to your extension scenario. 

## Real time service methods added in HQ: 
New real time service methods added in Headquarters to get the packing slip information and for extension to add some custom information or logics. If your customization need data or logic to be performed in Headquarters, then you can customize these methods using the extension patterns. You can also call these methods from CRT in case you need this for your extension scenario using transaction service client class.

### RetailTransactionServiceFulfillment:
We added all the new methods related to this order fulfillment packing slip process in this class.

### GetPackingSlipsData:
This method returns the all the packing slip information by passing the Sales ID as the parameter. 

### GetFulfillmentLinesByPackingSlipId:
Return the fulfillment lines based on the packing slip ID. Suppose if you have the packing slip ID and want to get the sales lines relevant to that packing slip ID then you can use this method.

### MarkFulfillmentLinesAsPacked
This method updates the status of the fulfillment lines to packed by taking the fulfillment details as parameter in Xml string format. POS calls CRT to mark the selected lines from the POS UI as picked. **MarkAsPickedRealtimeRequest** in CRT calls the **MarkFulfillmentLinesAsPacked** real time service method in HQ to set the line status as marked. You can customize the **packingSlipExtensionPoint** method to add custom logic or return additional information when the line marked as packed and returned for printing.

### packingSlipExtensionPoint:
You can customize this method to add any custom logic or return any custom information along with the packing slip id Ex: Packing information, delivery note etc. This method is mainly added for extensions to do some custom scenarios. This method is called from **MarkFulfillmentLinesAsPacked** method using the chain of command extensibility point and **MarkFulfillmentLinesAsPacked** method is executed from the real time service call made by the CRT code.
