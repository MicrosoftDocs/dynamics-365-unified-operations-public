---
# required metadata

title: Title TBD
description: TBD
author: mugunthanm
manager: AnnBe
ms.date: 02/21/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Developer
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Retail, Operations 
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: retail
ms.author: mumani
ms.search.validFrom: 2017-12-31 
ms.dyn365.ops.version: 7.3 
---

# How to create new POS Operation and add it to Button grid

[!include[banner](../includes/banner.md)]

**How to create new POS Operation:**

This topic explains how to create a new POS operation and add it to the POS layout using Button grid designer. This topic is applicable for Dynamics 365 for Finance and Operations or Dynamics 365 for Retail platform update 8 with retail App update 4 hotfix.

When you want your business logic to be executed in POS based on user button click then you should create POS operations. POS operations can execute multiple activities or workflows. Ex: Navigate to new view or ask user input or execute some business logic etc. all standard and custom POS operation supports pre and post trigger.

Note: If you want our logic to be executed part of some other workflow or no user click is required then you create POS APIs(request/response), POS operations is not required in these scenarios.

Each operation should implement the following:

1.  **Operation request** – Operation request extends from the ExtensionOperationRequestBase and it contains all the inputs for the operation to execute

2.  **Operation response** – Operation response extends from the Response and it contains all the response based on the operation execution.

3.  **Operation factory** – Operation handler links the operation button click with operation handler.

4.  **Operation handler** – Operation handler extends from ExtensionOperationRequestHandlerBase and it contains core logic for the operation. All the business logic should be returned in the handler and it should return the operation response after execution of the operation.

**Scenario:** Lets create a sample new operation to do simplified EOD of processing. In this operation, we will call the standard Tender removal, safe drop, tender declaration and Close shift in a sequence. This one operation combines multiples steps and execute based on the conditions defined.

Note: You can create new operation and execute your own custom logic or call existing POS operations like Add item to cart, Apply line discount etc. or call existing APIs like Get current cart, Set extension properties etc.

1.  Open visual studio 2015 in administrator mode.

2.  Open ModernPOS solution from …\\RetailSDK\\POS

3.  Under the POS.Extensions project create a new folder called EODSample.

4.  Under EODSample folder create new folder called Operations.

    **Create the operation request class:**

5.  In the Operations folder, add a new ts (typescript) file and name it has EndOfDayOperationRequest.ts

6.  Add the below import statement inside the EndOfDayOperationRequest.ts file to import the relevant entities and context.

```typescript
import { ExtensionOperationRequestBase } from "PosApi/Create/Operations"; 
                                                                            
 import EndOfDayOperationResponse from "./EndOfDayOperationResponse";
```
7.  Inside the EndOfDayOperationRequest.ts file add a new class called EndOfDayOperationRequest and extend it from ExtensionOperationRequestBase.

```typescript
 /**                                                                                                                                      * (Sample) Operation request for executing end of day operations.                                                                       
 */                                                                                                                                                        
        
 export default class EndOfDayOperationRequest<TResponse extends EndOfDayOperationResponse> extends ExtensionOperationRequestBase<TResponse> {  
                                                                                                                                                            
 constructor(correlationId: string) {                                                                                                                       
                                                                                                                                                            
 super(5001, correlationId);                                                                                                                                
                                                                                                                                                            
 }                                                                                                                                                          
                                                                                                                                                            
 }                                                                                                                                                          |
```
**Note:** In the Super method, we are initializing the operation id as 5500, you can use any operation id starting from 4001. 0 - 4000 is reserved for internal Retail POS operations and no two operations should have the same operation id. Also the button grid desginer properties will show custom parameters text box (where you can pass parameters to the POS operation from HQ) only if the operation id is greater than 4001.

**Create the operation response class:**

8.  In the Operations folder, add a new ts (typescript) file and name it has EndOfDayOperationResponse.ts

9.  Add the below import statement inside the EndOfDayOperationResponse.ts file to import the relevant entities and context.

    import { Response } from "PosApi/Create/RequestHandlers";

10.  Inside the EndOfDayOperationResponse.ts add a new class called EndOfDayOperationResponse and extend it from Response class.
```typescript
 /**                                                               
                                                                      
 * (Sample) Operation response of executing end of day operations.   
                                                                      
 */                                                                  
                                                                      
 export default class EndOfDayOperationResponse extends Response { }  
```
**Create the operation handler class:**

11.  In the Operations folder, add a new ts (typescript) file and name it has EndOfDayOperationRequestHandler.ts

12.  Add the below import statement inside the EndOfDayOperationRequestHandler.ts to import the relevant entities and context.

```typescript
 import { ExtensionOperationRequestType, ExtensionOperationRequestHandlerBase } from "PosApi/Create/Operations";         
                                                                                                                          
 import { CloseShiftOperationRequest, CloseShiftOperationResponse } from "PosApi/Consume/Shifts";                         
                                                                                                                          
 import { SafeDropOperationRequest, SafeDropOperationResponse } from "PosApi/Consume/StoreOperations";                    
                                                                                                                          
 import { TenderDeclarationOperationRequest, TenderDeclarationOperationResponse } from "PosApi/Consume/StoreOperations";  
                                                                                                                          
 import { TenderRemovalOperationRequest, TenderRemovalOperationResponse } from "PosApi/Consume/StoreOperations";          
                                                                                                                          
 import EndOfDayOperationResponse from "./EndOfDayOperationResponse";                                                     
                                                                                                                          
 import EndOfDayOperationRequest from "./EndOfDayOperationRequest";                                                       
                                                                                                                          
 import { ClientEntities } from "PosApi/Entities";                                                                        |
```
13.  Inside the EndOfDayOperationRequestHandler.ts add a new class called EndOfDayOperationRequestHandler and extend it from ExtensionOperationRequestHandlerBase class.
```typescript
    export default class EndOfDayOperationRequestHandler<TResponse extends EndOfDayOperationResponse> extends ExtensionOperationRequestHandlerBase<TResponse> {}
```
14.  Each handler should implement two methods:

     1.  Supported request

     2.  Execute Async

15.  Add the supported request type in the class:

```typescript
/**                                                                           
                                                                                  
 * Gets the supported request type.                                              
                                                                                  
 * @return {RequestType<TResponse>} The supported request type.            
                                                                                  
 */                                                                              
                                                                                  
 public supportedRequestType(): ExtensionOperationRequestType<TResponse> {  
                                                                                  
 return EndOfDayOperationRequest;                                                 
                                                                                  
 }                                                                                |
```
16.  Implement the executeAsync method:
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
                                                                                                                                                           
 }                                                                                                                                                         |
```
The overall code should look like this:
```typescript
/**                                                                                                                                                                   
                                                                                                                                                                          
 * SAMPLE CODE NOTICE                                                                                                                                                    
                                                                                                                                                                          
 *                                                                                                                                                                       
                                                                                                                                                                          
 * THIS SAMPLE CODE IS MADE AVAILABLE AS IS. MICROSOFT MAKES NO WARRANTIES, WHETHER EXPRESS OR IMPLIED,                                                                  
                                                                                                                                                                          
 * OF FITNESS FOR A PARTICULAR PURPOSE, OF ACCURACY OR COMPLETENESS OF RESPONSES, OF RESULTS, OR CONDITIONS OF MERCHANTABILITY.                                          
                                                                                                                                                                          
 * THE ENTIRE RISK OF THE USE OR THE RESULTS FROM THE USE OF THIS SAMPLE CODE REMAINS WITH THE USER.                                                                     
                                                                                                                                                                          
 * NO TECHNICAL SUPPORT IS PROVIDED. YOU MAY NOT DISTRIBUTE THIS CODE UNLESS YOU HAVE A LICENSE AGREEMENT WITH MICROSOFT THAT ALLOWS YOU TO DO SO.                       
                                                                                                                                                                          
 */                                                                                                                                                                      
                                                                                                                                                                          
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
                                                                                                                                                                          
 \* Executes the request handler asynchronously.                                                                                                                          
                                                                                                                                                                          
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
                                                                                                                                                                          
 }                                                                                                                                                                        |
```
**Create the operation factory class:**

17.  In the Operations folder, add a new ts (typescript) file and name it has EndOfDayOperationRequestFactory.ts

18.  Add the below import statement inside the EndOfDayOperationRequestFactory.ts to import the relevant entities and context.
```typescript
import EndOfDayOperationResponse from "./EndOfDayOperationResponse";                                        
                                                                                                              
 import EndOfDayOperationRequest from "./EndOfDayOperationRequest";                                           
                                                                                                              
 import { ExtensionOperationRequestFactoryFunctionType, IOperationContext } from "PosApi/Create/Operations";  
                                                                                                              
 import { ClientEntities } from "PosApi/Entities";                                                            |
```
19.  Let’s add a function inside the EndOfDayOperationRequestFactory.ts to link the operation handler and the operation button.
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
                                                                                                                                                                  
 export default getOperationRequest;;                                                                                                                             |
```
The overall code should look like this:
```typescript
/**                                                                                                                                                           
                                                                                                                                                                  
 * SAMPLE CODE NOTICE                                                                                                                                            
                                                                                                                                                                  
 *                                                                                                                                                               
                                                                                                                                                                  
 * THIS SAMPLE CODE IS MADE AVAILABLE AS IS. MICROSOFT MAKES NO WARRANTIES, WHETHER EXPRESS OR IMPLIED,                                                          
                                                                                                                                                                  
 * OF FITNESS FOR A PARTICULAR PURPOSE, OF ACCURACY OR COMPLETENESS OF RESPONSES, OF RESULTS, OR CONDITIONS OF MERCHANTABILITY.                                  
                                                                                                                                                                  
 * THE ENTIRE RISK OF THE USE OR THE RESULTS FROM THE USE OF THIS SAMPLE CODE REMAINS WITH THE USER.                                                             
                                                                                                                                                                  
* NO TECHNICAL SUPPORT IS PROVIDED. YOU MAY NOT DISTRIBUTE THIS CODE UNLESS YOU HAVE A LICENSE AGREEMENT WITH MICROSOFT THAT ALLOWS YOU TO DO SO.               
                                                                                                                                                                  
 */                                                                                                                                                              
                                                                                                                                                                  
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
                                                                                                                                                                  
 export default getOperationRequest;                                                                                                                              |
```
20.  In the manifest.json file, copy and paste the below code:
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
                                                                                
 }                                                                              |
```
21.  Open the extensions.json file under POS.Extensions project and update it with EODSample, so that POS during runtime will include this extension.
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
22.  Open the tsconfig.json to comment out the extension package folders from the exclude list. POS will use this file to include or exclude the extension. By default, the list contains all the excluded extensions list, if you want to include any extension part of the POS then you need add the extension folder name and comment the extension from the extension list like below.
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
"SampleExtensions",
 //"SampleExtensions",
"StoreHoursSample",
"SuspendTransactionReceiptSample"
],
```
23.  Compile and rebuild the project.

**Add Custom operation button to the POS layout in HQ:**

1.  Go to Retail and commerce > Channel setup > POS setup > POS > Operations in Dynamics 365 for Retail.

2.  Create a new operation named “EOD” with ID "5001".

3.  Go to Retail and commerce > Channel setup > POS setup > POS > Button grids.

4.  Filter for " F2W2".

5.  Click on button "Designer" and follow the instructions to install the designer. If prompted enter the dynamics 365 for Retail username and password.

6.  Right-click on the designer area and select Add new row and in the new button right click and select "Button properties".

7.  Select Action = "EOD”. Click OK and close the Designer.

8.  Go to Retail and commerce > Retail IT > Distribution schedule, select "1090" and click "Run now".

    **Note:** The above steps assumes you are using demo data, if not create and add the button according to your custom configurations.

**How to validate your extension:**

1.  Press F5 and deploy the POS to test your customization.

2.  On the transaction screen click the new EOD operation button and follow the steps.
