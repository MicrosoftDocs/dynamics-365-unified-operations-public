---
title: Add POS operations to POS layouts by using Button grid designer
description: This article explains how to create a new POS operation and add it to the POS layout by using Button grid designer.
author: ritakimani
ms.date: 07/29/2024
ms.topic: how-to
ms.custom: 
  - bap-template
ms.reviewer: josaw
ms.search.region: Global
ms.author: ritakimani
ms.search.validFrom: 2017-10-31
ms.dyn365.ops.version: Application update 4
---

# Add POS operations to POS layouts by using Button grid designer

[!include[banner](../includes/banner.md)]

This article explains how to create a new point of sale (POS) operation and add it to the POS layout by using Button grid designer. This article applies to the following applications where Platform update 8 and the Application update 4 hotfix are installed:

- Finance
- Dynamics 365 Commerce

If you want your business logic to be run in the POS when users click a button, you should create POS operations. POS operations can run multiple activities or workflows. For example, they can open a new view, ask for user input, or run business logic. All standard and custom POS operations support pre-triggers and post-triggers.

> [!NOTE]
> If logic should be run as part of another workflow, or if no button click is required, create POS request/response application programming interfaces (APIs). POS operations aren't required in these scenarios.

Every operation should implement the following elements:

- **Operation request** – The operation request is extended from the **ExtensionOperationRequestBase** class. It contains all the input that is required in order to run the operation.
- **Operation response** – The operation response is extended from the **Response** class. It contains the whole response, based on execution of the operation.
- **Operation factory** – The operation factory links the button click for the operation with the operation handler.
- **Operation handler** – The operation handler is extended from the **ExtensionOperationRequestHandlerBase** class. It contains core logic for the operation. All the business logic should be written in the handler, and it should return the operation response after the operation is run.

## Create a POS operation

This section explains how to create a sample operation that does simplified end-of-day (EOD) processing. This operation calls the standard Tender removal, Safe drop, Tender declaration, and Close shift operations in a sequence. Therefore, this one operation combines multiples steps. It is run based on the conditions that you define.

> [!NOTE]
> You can create a new operation and run your own custom logic, you can call existing POS operations, such as Add item to cart and Apply line discount, or you can call existing APIs, such as Get current cart and Set extension properties.

1. Start Microsoft Visual Studio 2015 in administrator mode.
2. From **...\RetailSDK\POSOpen**, open the **ModernPOS** solution.
3. Under the **POS.Extensions** project, create a folder that is named **EODSample**.
4. Under the **EODSample** folder, create a folder that is named **Operations**.

### Create the operation request class

1. In the **Operations** folder, create a typescript (.ts) file that is named **EndOfDayOperationRequest.ts**.
2. Open the **EndOfDayOperationRequest.ts** file, and add the following **import** statements to import the relevant entities and context.

    ```typescript
    import { ExtensionOperationRequestBase } from "PosApi/Create/Operations";
    import EndOfDayOperationResponse from "./EndOfDayOperationResponse";
    ```

3. Add a class that is named **EndOfDayOperationRequest**, and extend it from the **ExtensionOperationRequestBase** class.
    In this example, the operation ID in the **super** method is initialized to **5001**. However, you can use any operation ID starting from 4001. Operation IDs 0 through 4000 are reserved for internal POS operations, and no two operations should have the same operation ID. Additionally, the custom parameters field appears in Button grid designer properties only if the operation ID is 4001 or higher. (You can use custom parameters field to pass parameters to the POS operation from Retail headquarters).

    ```typescript
    /**
     * (Sample) Operation request for executing end of day operations.
     */
    export default class EndOfDayOperationRequest<TResponse extends EndOfDayOperationResponse> extends ExtensionOperationRequestBase<TResponse> {
        constructor(correlationId: string) {
            super(5001, correlationId);
        }
    }
    ```

### Create the operation response class

1. In the **Operations** folder, create a typescript (.ts) file that is named **EndOfDayOperationResponse.ts**.
2. Open the **EndOfDayOperationResponse.ts** file, and add the following **import** statement to import the relevant entities and context.

    ```typescript
    import { Response } from "PosApi/Create/RequestHandlers";
    ```

3. Add a class that is named **EndOfDayOperationResponse**, and extend it from the **Response** class.

    ```typescript
    /**
     * (Sample) Operation response of executing end of day operations.
     */
    export default class EndOfDayOperationResponse extends Response { }
    ```

### Create the operation handler class

1. In the **Operations** folder, create a typescript (.ts) file that is named **EndOfDayOperationRequestHandler.ts**.
2. Open the **EndOfDayOperationRequestHandler.ts** file, and add the following **import** statements to import the relevant entities and context.

    ```typescript
    import { ExtensionOperationRequestType, ExtensionOperationRequestHandlerBase } from "PosApi/Create/Operations";
    import { CloseShiftOperationRequest, CloseShiftOperationResponse } from "PosApi/Consume/Shifts";
    import { SafeDropOperationRequest, SafeDropOperationResponse } from "PosApi/Consume/StoreOperations";
    import { TenderDeclarationOperationRequest, TenderDeclarationOperationResponse } from "PosApi/Consume/StoreOperations";
    import { TenderRemovalOperationRequest, TenderRemovalOperationResponse } from "PosApi/Consume/StoreOperations";
    import EndOfDayOperationResponse from "./EndOfDayOperationResponse";
    import EndOfDayOperationRequest from "./EndOfDayOperationRequest";
    import { ClientEntities } from "PosApi/Entities";|
    ```

3. Add a class that is named **EndOfDayOperationRequestHandler**, and extend it from the **ExtensionOperationRequestHandlerBase** class.

    Each handler should implement two methods:

   - supportedRequestType
   - executeAsync

    ```typescript
    export default class EndOfDayOperationRequestHandler<TResponse extends EndOfDayOperationResponse> extends ExtensionOperationRequestHandlerBase<TResponse> {}
    ```

4. Add the supported request type in the class.

    ```typescript
    /**
     * Gets the supported request type.
     * @return {RequestType<TResponse>} The supported request type.
     */
    public supportedRequestType(): ExtensionOperationRequestType<TResponse> {
        return EndOfDayOperationRequest;
    }
    ```

5. Implement the **executeAsync** method.

    ```typescript
    /**
     * Executes the request handler asynchronously.
     * @param {EndOfDayOperationRequest<TResponse>} request The request.
     * @return {Promise<ICancelableDataResult<TResponse>>} The cancelable async result containing the response.
     */
    public executeAsync(printRequest: EndOfDayOperationRequest<TResponse>): Promise<ClientEntities.ICancelableDataResult<TResponse>> {
        this.context.logger.logInformational("Log message from PrintOperationRequestHandler executeAsync().", this.context.logger.getNewCorrelationId());
        // Tender Removal
        let tenderRemovalRequest: TenderRemovalOperationRequest<TenderRemovalOperationResponse> =
        new TenderRemovalOperationRequest(this.context.logger.getNewCorrelationId());
        return this.context.runtime.executeAsync(tenderRemovalRequest).then((result: ClientEntities.ICancelableDataResult<TenderRemovalOperationResponse>)
        : Promise<Commerce.Client.Entities.ICancelableDataResult<SafeDropOperationResponse>> => {
            // Safe Drop
            if (!result.canceled) {
                let safeDropRequest: SafeDropOperationRequest<SafeDropOperationResponse> =
                new SafeDropOperationRequest(this.context.logger.getNewCorrelationId());
                return this.context.runtime.executeAsync(safeDropRequest);
            } else {
                return Promise.resolve({
                    canceled: true,
                    data: null
                });
            }
        }).then((result: Commerce.Client.Entities.ICancelableDataResult<SafeDropOperationResponse>)
        : Promise<ClientEntities.ICancelableDataResult<TenderDeclarationOperationResponse>> => {
            // Tender Declaration
            if (!result.canceled) {
                let tenderDeclarationRequest: TenderDeclarationOperationRequest<TenderDeclarationOperationResponse> =
                new TenderDeclarationOperationRequest(this.context.logger.getNewCorrelationId());
                return this.context.runtime.executeAsync(tenderDeclarationRequest);
            } else {
                return Promise.resolve({
                    canceled: true,
                    data: null
                });
            }
        }).then((result: ClientEntities.ICancelableDataResult<TenderDeclarationOperationResponse>)
        : Promise<ClientEntities.ICancelableDataResult<CloseShiftOperationResponse>> => {
            // Close Shift
            if (!result.canceled) {
                return new Promise(
                    (resolve: (value?: ClientEntities.ICancelableDataResult<CloseShiftOperationResponse>) => void, reject: (reason?: any) => void) => {
                        // A delay of ten seconds is added here as a work-around for issues with printing a second receipt to the windows driver
                        // printer before the first dialog is closed. A ten second delay gives the user a chance to close the first dialog before
                        // the issue occurs.
                        setTimeout(() => { resolve(null); }, 10000);
                    }).then(() => {
                        let closeShiftOperationRequest: CloseShiftOperationRequest<CloseShiftOperationResponse> =
                        new CloseShiftOperationRequest(this.context.logger.getNewCorrelationId());
                        return this.context.runtime.executeAsync(closeShiftOperationRequest);
                    });
            } else {
                return Promise.resolve({
                    canceled: true,
                    data: null
                });
            }
        }).then((result: ClientEntities.ICancelableDataResult<CloseShiftOperationResponse>)
        : ClientEntities.ICancelableDataResult<EndOfDayOperationResponse> => {
                return <ClientEntities.ICancelableDataResult<EndOfDayOperationResponse>>{
                    canceled: result.canceled,
                    data: result.canceled ? null : new EndOfDayOperationResponse()
                };
            });
        }
    }
    ```

    The overall code should look like this.

    ```typescript
    import { ExtensionOperationRequestType, ExtensionOperationRequestHandlerBase } from "PosApi/Create/Operations";
    import { CloseShiftOperationRequest, CloseShiftOperationResponse } from "PosApi/Consume/Shifts";
    import { SafeDropOperationRequest, SafeDropOperationResponse } from "PosApi/Consume/StoreOperations";
    import { TenderDeclarationOperationRequest, TenderDeclarationOperationResponse } from "PosApi/Consume/StoreOperations";
    import { TenderRemovalOperationRequest, TenderRemovalOperationResponse } from "PosApi/Consume/StoreOperations";
    import EndOfDayOperationResponse from "./EndOfDayOperationResponse";
    import EndOfDayOperationRequest from "./EndOfDayOperationRequest";
    import { ClientEntities } from "PosApi/Entities";
    /**
     * (Sample) Request handler for the EndOfDayOperationRequest class.
     */
    export default class EndOfDayOperationRequestHandler<TResponse extends EndOfDayOperationResponse> extends ExtensionOperationRequestHandlerBase<TResponse> {
        /**
         * Gets the supported request type.
         * @return {RequestType<TResponse>} The supported request type.
         */
        public supportedRequestType(): ExtensionOperationRequestType<TResponse> {
            return EndOfDayOperationRequest;
        }
        /**
         * Executes the request handler asynchronously.
         * @param {EndOfDayOperationRequest<TResponse>} request The request.
         * @return {Promise<ICancelableDataResult<TResponse>>} The cancelable async result containing the response.
         */
        public executeAsync(printRequest: EndOfDayOperationRequest<TResponse>): Promise<ClientEntities.ICancelableDataResult<TResponse>> {
            this.context.logger.logInformational("Log message from PrintOperationRequestHandler executeAsync().", this.context.logger.getNewCorrelationId());
            // Tender Removal
            let tenderRemovalRequest: TenderRemovalOperationRequest<TenderRemovalOperationResponse> =
            new TenderRemovalOperationRequest(this.context.logger.getNewCorrelationId());
            return this.context.runtime.executeAsync(tenderRemovalRequest).then((result: ClientEntities.ICancelableDataResult<TenderRemovalOperationResponse>)
            : Promise<Commerce.Client.Entities.ICancelableDataResult<SafeDropOperationResponse>> => {
                // Safe Drop
                if (!result.canceled) {
                    let safeDropRequest: SafeDropOperationRequest<SafeDropOperationResponse> =
                    new SafeDropOperationRequest(this.context.logger.getNewCorrelationId());
                    return this.context.runtime.executeAsync(safeDropRequest);
                } else {
                    return Promise.resolve({
                        canceled: true,
                        data: null
                    });
                }
            }).then((result: Commerce.Client.Entities.ICancelableDataResult<SafeDropOperationResponse>)
            : Promise<ClientEntities.ICancelableDataResult<TenderDeclarationOperationResponse>> => {
                // Tender Declaration
                if (!result.canceled) {
                    let tenderDeclarationRequest: TenderDeclarationOperationRequest<TenderDeclarationOperationResponse> =
                    new TenderDeclarationOperationRequest(this.context.logger.getNewCorrelationId());
                    return this.context.runtime.executeAsync(tenderDeclarationRequest);
                } else {
                    return Promise.resolve({
                        canceled: true,
                        data: null
                    });
                }
            }).then((result: ClientEntities.ICancelableDataResult<TenderDeclarationOperationResponse>)
            : Promise<ClientEntities.ICancelableDataResult<CloseShiftOperationResponse>> => {
                // Close Shift
                if (!result.canceled) {
                    return new Promise(
                        (resolve: (value?: ClientEntities.ICancelableDataResult<CloseShiftOperationResponse>) => void, reject: (reason?: any) => void) => {
                            // A delay of ten seconds is added here as a work-around for issues with printing a second receipt to the windows driver
                            // printer before the first dialog is closed. A ten second delay gives the user a chance to close the first dialog before
                            // the issue occurs.
                            setTimeout(() => { resolve(null); }, 10000);
                    }).then(() => {
                        let closeShiftOperationRequest: CloseShiftOperationRequest<CloseShiftOperationResponse> =
                        new CloseShiftOperationRequest(this.context.logger.getNewCorrelationId());
                        return this.context.runtime.executeAsync(closeShiftOperationRequest);
                    });
                } else {
                    return Promise.resolve({
                        canceled: true,
                        data: null
                    });
                }
            }).then((result: ClientEntities.ICancelableDataResult<CloseShiftOperationResponse>)
            : ClientEntities.ICancelableDataResult<EndOfDayOperationResponse> => {
                return <ClientEntities.ICancelableDataResult<EndOfDayOperationResponse>>{
                    canceled: result.canceled,
                    data: result.canceled ? null : new EndOfDayOperationResponse()
                };
            });
        }
    }
    ```

### Create the operation factory class

1. In the **Operations** folder, create a typescript (.ts) file that is named **EndOfDayOperationRequestFactory.ts**.
2. Open the **EndOfDayOperationRequestFactory.ts** file, and add the following **import** statements to import the relevant entities and context.

    ```typescript
    import EndOfDayOperationResponse from "./EndOfDayOperationResponse";
    import EndOfDayOperationRequest from "./EndOfDayOperationRequest";
    import { ExtensionOperationRequestFactoryFunctionType, IOperationContext } from "PosApi/Create/Operations";
    import { ClientEntities } from "PosApi/Entities";
    ```

3. Add a function to link the operation handler and the operation button.

    ```typescript
    let getOperationRequest: ExtensionOperationRequestFactoryFunctionType<EndOfDayOperationResponse> =
    /**
     * Gets an instance of EndOfDayOperationRequest.
     * @param {number} operationId The operation Id.
     * @param {string[]} actionParameters The action parameters.
     * @param {string} correlationId A telemetry correlation ID, used to group events logged from this request together with the calling context.
     * @return {EndOfDayOperationRequest<TResponse>} Instance of EndOfDayOperationRequest.
     */
    function (
        context: IOperationContext,
        operationId: number,
        actionParameters: string [],
        correlationId: string
    ): Promise<ClientEntities.ICancelableDataResult<EndOfDayOperationRequest<EndOfDayOperationResponse>>> {
        let operationRequest: EndOfDayOperationRequest<EndOfDayOperationResponse> = new EndOfDayOperationRequest<EndOfDayOperationResponse>(correlationId);
        return Promise.resolve(<ClientEntities.ICancelableDataResult<EndOfDayOperationRequest<EndOfDayOperationResponse>>>{
            canceled: false,
            data: operationRequest
        });
    };
    export default getOperationRequest;
    ```

    The overall code should look like this.

    ```typescript
    import EndOfDayOperationResponse from "./EndOfDayOperationResponse";
    import EndOfDayOperationRequest from "./EndOfDayOperationRequest";
    import { ExtensionOperationRequestFactoryFunctionType, IOperationContext } from "PosApi/Create/Operations";
    import { ClientEntities } from "PosApi/Entities";
    let getOperationRequest: ExtensionOperationRequestFactoryFunctionType<EndOfDayOperationResponse> =
    /**
     * Gets an instance of EndOfDayOperationRequest.
     * @param {number} operationId The operation Id.
     * @param {string[]} actionParameters The action parameters.
     * @param {string} correlationId A telemetry correlation ID, used to group events logged from this request together with the calling context.
     * @return {EndOfDayOperationRequest<TResponse>} Instance of EndOfDayOperationRequest.
     */
    function (
        context: IOperationContext,
        operationId: number,
        actionParameters: string[],
        correlationId: string
    ): Promise<ClientEntities.ICancelableDataResult<EndOfDayOperationRequest<EndOfDayOperationResponse>>> {
        let operationRequest: EndOfDayOperationRequest<EndOfDayOperationResponse> = new EndOfDayOperationRequest<EndOfDayOperationResponse>(correlationId);
        return Promise.resolve(<ClientEntities.ICancelableDataResult<EndOfDayOperationRequest<EndOfDayOperationResponse>>>{
            canceled: false,
            data: operationRequest
        });
    };
    export default getOperationRequest;
    ```

4. Open the **manifest.json** file, and paste in the following code.

    ```typescript
    {
        "$schema": "../manifestSchema.json",
        "name": "Pos_Extensibility_EODSample",
        "publisher": "Microsoft",
        "version": "7.3.0",
        "minimumPosVersion": "7.3.0.0",
        "components": {
            "create": {
                "operations": [
                    {
                        "operationId": "5001",
                        "operationRequestFactoryPath": "Operations/ EndOfDayOperationRequestFactory",
                        "operationRequestHandlerPath": "Operations/ EndOfDayOperationRequestHandler"
                    }
                ]
            }
        }
    }
    ```

5. Open the **extensions.json** file under the **POS.Extensions** project, and update it with **EODSample**, so that the POS will include the extension at runtime.

    ```typescript
    {
        "extensionPackages": [
            {
                "baseUrl": "SampleExtensions"
            },
            {
            "baseUrl": "EODSample"
            }
        ]
    }
    ```

6. Open the **tsconfig.json** file, and comment out the extension package folders in the exclude list. The POS will use this file to include or exclude the extension. By default, the list contains the whole excluded extensions list. To include an extension as part of the POS, you must add the name of the extension folder and comment out the extension in the extension list, as shown here.

    ```typescript
    "extends": "../tsconfigs/tsmodulesconfig",
    "exclude": [
        "AuditEventExtensionSample",
        "B2BSample",
        "CustomerSearchWithAttributesSample",
        "FiscalRegisterSample",
        //"EODSample",
        "PromotionsSample",
        "SalesTransactionSignatureSample",
        "SampleExtensions2",
        //"SampleExtensions",
        "StoreHoursSample",
        "SuspendTransactionReceiptSample"
    ],
     ```

7. Compile and rebuild the project.

## Add a custom operation button to the POS layout in Retail headquarters

1. In Retail go to **Retail and commerce &gt; Channel setup &gt; POS setup &gt; POS &gt; Operations**.
2. Create an operation that is named **EOD** and that has an operation ID of **5001**.
3. Go to **Retail and commerce &gt; Channel setup &gt; POS setup &gt; POS &gt; Button grids**.
4. Filter for **'F2W2'**.
5. Select the **Designer** button, and then follow the instructions to install the designer. If you're prompted for credentials, enter the Retail user name and password.
6. Right-click in the designer area, and then select **Add new row**.
7. Right-click the new button, and then select **Button properties**.
8. Set the **Action** property to **EOD**. Then select **OK**, and close the designer.
9. Go to **Retail and commerce** &gt; **Retail IT** &gt; **Distribution schedule**.
10. Select **1090**, and then select **Run now**.

    > [!NOTE]
    > The preceding steps assume that you're using demo data. If you aren't using demo data, create and add the button according to your custom configurations.

## Validate your extension

1. Press F5, and deploy the POS to test your customization.
2. On the transaction screen, select the new **EOD** operation button, and follow the steps.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
