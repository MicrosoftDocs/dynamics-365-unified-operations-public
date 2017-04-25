---
# required metadata

title: Modern POS and Cloud POS trigger extensibility
description: This article explains the client-side trigger functionality in Modern POS and Cloud POS.
author: RobinARH
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: robinr
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 17751
ms.assetid: 6767d342-73e0-432b-a02f-ea8191464506
ms.search.region: Global
# ms.search.industry: 
ms.author: sijoshi
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Modern POS and Cloud POS trigger extensibility

[!include[banner](../includes/banner.md)]


This article explains the client-side trigger functionality in Modern POS and Cloud POS.

Trigger overview
----------------

Triggers are events that are raised by Microsoft Dynamics 365 for Operations for Retail POS. Triggers let you insert custom code before or after operations. There are two kinds of triggers: pre-triggers and post-triggers.

| Pre-triggers                                                                                                                                                                                                                                                    | Post-triggers                                                                                                                                                                                                                                                        |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Pre-triggers can be used to insert custom code before an operation is run. For example, if a customer uses a coupon for a purchase, you can use a pre-trigger to insert custom code to validate that the coupon hasn't expired and hasn't previously been used. | Post-triggers can be used to insert custom code that responds to a completed operation. For example, you can write code that runs after the **CustomerAdd** operation and prompts the cashier to wish the customer a happy birthday if it's the customer’s birthday. |

### Trigger types

In Modern POS and Cloud POS, triggers are either cancelable or non-cancelable.

| Cancelable                                                                                                                                                                                                                                                                                                                                                                                                              | Non-cancelable                                                                                                                                                                                                                                                                                                                                             |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Trigger implementations that extend **ICancelableTriggerCancelable** triggers can succeed, fail, or be canceled. Execution of the workflow is canceled without displaying an error. An example is a trigger to confirm that the user wants to use his or her loyalty points for tender. If the user selects **No**, the workflow to enter loyalty information is canceled without showing an error message to the user. | Trigger implementations that extend **ITriggerNon-cancelable** triggers can either succeed or fail. If the trigger succeeds, the workflow continues. If the trigger fails, a message appears in the UI. An example is a trigger to support Swedish localization requirements by guiding the cashier to create separate transactions for sales and returns. |

### Guidelines

-   **Trigger registration** – All triggers should be registered by using the **TriggerManager::register** method. The **ApplicationStart**, **PreLogOn**, and **PostLogOn** triggers must be registered inside a function that is called when the **DOMContentLoaded** event is raised. Other triggers can be registered in the same manner, but they can also be registered conditionally.
    -   **Conditional registration** – If the decision about whether to register a trigger is based on information in the channel, the trigger can be registered conditionally. Conditional registration should be performed inside a **PostLogOn** trigger. **Note:** It's important that the conditional registration be performed only during the first sign-in after the app has been loaded. For an example implementation, see the sample code later in this article.
-   **Trigger implementation** – Each trigger event that is listed in the "Supported trigger events" section has a trigger interface that is associated with it. These trigger interfaces define the contract between the application and the trigger implementations. Each trigger should implement the predefined interface that is associated with the trigger event type that it's registered for.

### Triggers execution workflow

The following diagram shows the execution workflow for both pre-triggers and post-triggers for the **ItemSaleOperation** workflow/operation. 

[![Trigger Execution Flow](./media/trigger-execution-flow.png)](./media/trigger-execution-flow.png)

### Supported trigger events

Together with pre-operation and post-operation triggers that are triggered for every operation, the following triggers are supported out of the box:

-   Application triggers
    -   Cancelable
        -   **PreLogOn** – Called before sign-in to Modern POS
            -   operatorId
    -   Non-cancelable
        -   **ApplicationStart** – Called when the application is launched
        -   **ApplicationSuspend** – Called when the application is suspended
        -   **PostLogOff** – Called after the sign-out operation is completed
        -   **PostLogOn** – Called after the sign-in operation is completed
-   Cash management triggers
    -   Cancelable
        -   **PreTenderDeclaration** – Called before the tender declaration operation is run
    -   Non-cancelable
        -   **PostTenderDeclaration** – Called as the last step in the tender declaration workflow
-   Customer triggers
    -   Cancelable
        -   **PreCustomerAdd** – Called before a new customer is created
        -   **PreCustomerClear** – Called before the customer is cleared from the current transaction
        -   **PreCustomerSearch** – Called before a search for a customer
        -   **PreCustomerSet** – Called before the customer is set on the transaction
    -   Non-cancelable
        -   **PostCustomerAdd** – Called after a new customer is created
        -   **PostCustomerClear** – Called after the customer is cleared from the transaction
        -   **PostCustomerSearch** – Called after a search for a customer
-   Discount triggers
    -   Cancelable
        -   **PreLineDiscountAmount** – Called during the line discount amount operation, after validation determines whether a discount can be applied
        -   **PreLineDiscountPercent** – Called during the line discount percent operation, after validation determines whether a discount can be applied
        -   **PreTotalDiscountAmount** – Called during the total discount amount operation, after validation determines whether a discount can be applied
        -   **PreTotalDiscountPercent** – Called during the total discount percent operation, after validation determines whether a discount can be applied
    -   Non-cancelable
        -   **PostLineDiscountAmount** - Called as the last step in the line discount amount workflow
        -   **PostLineDiscountPercent** – Called as the last step in the line discount percent workflow
        -   **PostTotalDiscountAmount** – Called as the last step in the total discount amount workflow
        -   **PostTotalDiscountPercent** – Called as the last step in the total discount percent workflow
-   Operation triggers
    -   Cancelable
        -   **PreOperation** – Called before every operation is run, before the prehandler and operation validators
    -   Non-cancelable
        -   **OperationFailure** – Called when an operation fails, and can be used to perform recovery actions
        -   **PostOperation** – Called when an operation is completed successfully
-   Payment triggers
    -   Cancelable
        -   **PreAddTenderLine** – Called before a tender line is added to the transaction
        -   **PrePayment** – Called before any payment operation is started
        -   **PreVoidPayment** – Called before the void payment operation is started
    -   Non-cancelable
        -   **PostPayment** – Called after the payment has been added
        -   **PostVoidPayment** – Called after the payment has been voided
-   Printing triggers
    -   Cancelable
        -   **PrePrintReceiptCopy** – Called before a copy of the receipt is printed
-   Product Triggers
    -   Cancelable
        -   **PreClearQuantity** – Called before the clear quantity operation
        -   **PrePriceOverride** – Called before the price override operation
        -   **PreProductSale** – Called before the item sale operation
        -   **PreReturnProduct** – Called before the return product operation
        -   **PreSetQuantity** – Called before the set quantity operation
        -   **PreVoidProducts** – Called after the user confirms that he or she wants to void the transaction, but before the transaction is voided
    -   Non-cancelable
        -   **PostClearQuantity** – Called after the clear quantity operation
        -   **PostPriceOverride** – Called after the price override operation
        -   **PostProductSale** – Called after the item sale operation
        -   **PostReturnProduct** – Called after the return product operation
        -   **PostSetQuantity** – Called after the set quantity operation
        -   **PostVoidProducts** – Called after the void products operation
-   Transaction triggers
    -   Cancelable
        -   **PreConfirmReturnTransaction** – Called after a search for a transaction to return, but before the cart lines appear as available for return
        -   **PreEndTransaction** – Called before a sales transaction is completed
        -   **PreRecallTransaction** – Called before a transaction is recalled
        -   **PreReturnTransaction** – Called before a transaction is returned
        -   **PreSuspendTransaction** – Called before a transaction is suspended
        -   **PreVoidTransaction** – Called before a transaction is voided
    -   Non-cancelable
        -   **BeginTransaction** – Called before a cart is created and a transaction is started
        -   **PostEndTransaction** – Called after a sales transaction is completed
        -   **PostRecallTransaction** – Called after a transaction is recalled
        -   **PostReturnTransaction** – Called after items from a transaction are added to the cart for return
        -   **PostSuspendTransaction** – Called after suspending a transaction
        -   **PostVoidTransaction** – Called after a transaction is voided

## Trigger example implementation
The best way to understand triggers is to look at a sample implementation scenario.

### Modern POS/Cloud POS changes to support Swedish localization requirements by using POS triggers

Transactions can't have both return and sale operations if a fiscal register is connected. An **IPreProductSaleTrigger** trigger is implemented to detect this situation if it occurs and to show a message to prompt the cashier. This is a requirement in Sweden.

1.  Implement an **IPreProductSaleTrigger** trigger to detect the situation and show a message to prompt the cashier.
2.  Write trigger business logic in the **Execute** method in the implementation class.
3.  Register the trigger as part of the **PostLogonTrigger** implementation on the **DOMContentLoad** event. 

[![Trigger01](./media/trigger01.png)](./media/trigger01.png)

**Purpose:** To customize Modern POS/Cloud POS to implement the Swedish localization requirement that the same transaction not include both sale and return lines when a fiscal register is connected. Open a Modern POS project, and add a new TypeScript (.ts) file to add the trigger implementation. We are creating a new TypeScript file for our customization to keep our customization separate from the product code and make upgrades easier to manage.

1.  Start Microsoft Visual Studio 2015 as an administrator.
2.  Open the Modern POS solution from the Retail SDK directory:
    -   If you're using a cloud-hosted computer, the path is I:/RetailSDK.
    -   If you're using a locally downloaded machine, the path is C:\\Microsoft Dynamics AX\\70\\Retail SDK.

3.  In POS.Core\\Triggers\\, create a new TypeScript file that is named **TriggerSample.ts**. 

[![Trigger02](./media/trigger02-1024x411.png)](./media/trigger02.png)

4.  Add the following code to the TriggerSample.ts file.

        ///<reference path="ITrigger.ts" />
        ///<reference path="ApplicationTriggers.ts" />
        ///<reference path="TransactionTriggers.ts" />
        module Commerce.Triggers.Samples {
            "use strict";
            /**
             * Implementation of a pre product sale trigger that is used to ensure there are no return lines in the cart.
             */
            export class ValidateProductSalePreProductSaleTrigger implements IPreProductSaleTrigger {
                private static SALE_NOT_ALLOWED_IN_SAME_TRANSACTION_AS_RETURN_ERROR_CODE: string = "Return and sale not allowed in same transaction";
                /**
                 * Executes the trigger.
                 */
                public execute(options: Operations.IItemSaleOperationOptions): IAsyncResult<ICancelableResult> {
                    var hasReturnLine: boolean = Session.instance.cart.CartLines.some((cartLine: Proxy.Entities.CartLine): boolean => {
                        return cartLine.Quantity < 0 && !cartLine.IsVoided;
                    });
                    var result: AsyncResult<ICancelableResult> = new AsyncResult<ICancelableResult>(null);
                    if (hasReturnLine) {
                        var error: Proxy.Entities.Error =
                            new Proxy.Entities.Error(ValidateProductSalePreProductSaleTrigger.SALE_NOT_ALLOWED_IN_SAME_TRANSACTION_AS_RETURN_ERROR_CODE);
                        result.reject([error]);
                    } else {
                        result.resolve({ canceled: false });
                    }
                    return result;
                }
            }
            /**
             * Implementation of a post log on trigger that is used to perform conidtional registration of other triggers.
             */
            export class ConditionalRegistrationPostLogOnTrigger implements IPostLogOnTrigger {
                private static alreadyRegistered: boolean = false;
                /**
                 * Executes the trigger.
                 */
                public execute(options: IPostLogOnTriggerOptions): IVoidAsyncResult {
                    // Check to ensure the triggers have not already been registered.
                    if (!ConditionalRegistrationPostLogOnTrigger.alreadyRegistered) {
                        this.performRegistration();
                        // Set already registered field to true to prevent duplicate trigger registration.
                        ConditionalRegistrationPostLogOnTrigger.alreadyRegistered = true;
                    }
                    return VoidAsyncResult.createResolved();
                }
                /**
                 * Perform the conditional registration of triggers.
                 */
                private performRegistration(): void {
                    var conditionIsMet: boolean = true;
                    if (conditionIsMet) {              
                        TriggerManager.instance.register(
                            CancelableTriggerType.PreProductSale,
                            new ValidateProductSalePreProductSaleTrigger());
                    }
                }
            }
        }
        /**
         * Trigger types that do not support conditional registration should be registered when the DOMContentLoaded event is fired.
         * @remarks These trigger types include: ApplicationStart, PreLogOn and PostLogOn.
         */
        document.addEventListener("DOMContentLoaded", function (): void {
            Commerce.Triggers.TriggerManager.instance.register(
                Commerce.Triggers.NonCancelableTriggerType.PostLogOn,
                new Commerce.Triggers.Samples.ConditionalRegistrationPostLogOnTrigger());
        });

5.  Inspect the TriggerSample.ts file to see the implementation of **IPreProductSaleTrigger**.

        export class ValidateProductSalePreProductSaleTrigger implements IPreProductSaleTrigger {
            private static SALE_NOT_ALLOWED_IN_SAME_TRANSACTION_AS_RETURN_ERROR_CODE: string = "Return and sale not allowed in same transaction";       
            /**
            * Executes the trigger.
            */
            public execute(options: Operations.IItemSaleOperationOptions): IAsyncResult<ICancelableResult> {
                var hasReturnLine: boolean = Session.instance.cart.CartLines.some((cartLine: Proxy.Entities.CartLine): boolean => {
                    return cartLine.Quantity < 0 && !cartLine.IsVoided;
                });
                var result: AsyncResult<ICancelableResult> = new AsyncResult<ICancelableResult>(null);
                if (hasReturnLine) {
                    var error: Proxy.Entities.Error =
                    new Proxy.Entities.Error(ValidateProductSalePreProductSaleTrigger.SALE_NOT_ALLOWED_IN_SAME_TRANSACTION_AS_RETURN_ERROR_CODE);
                    result.reject([error]);
                } else {
                    result.resolve({ canceled: false });
                }
                return result;
            }    
        }

6.  Inspect the registration of **ValidateProductSalePreProductSaleTrigger**.

        /**
        * Implementation of a post log on trigger that is used to perform conidtional registration of other triggers.
        */
        export class ConditionalRegistrationPostLogOnTrigger implements IPostLogOnTrigger {
            private static alreadyRegistered: boolean = false;
            /**
            * Executes the trigger.
            */
            public execute(options: IPostLogOnTriggerOptions): IVoidAsyncResult {
                // Check to ensure the triggers have not already been registered.
                if (!ConditionalRegistrationPostLogOnTrigger.alreadyRegistered) {
                    this.performRegistration();
                // Set already registered field to true to prevent duplicate trigger registration.
                ConditionalRegistrationPostLogOnTrigger.alreadyRegistered = true;
            }
            return VoidAsyncResult.createResolved();
        }

7.  Inspect the **performRegistration** method where the trigger is registered.

        private performRegistration(): void {
            var conditionIsMet: boolean = true;
            if (conditionIsMet) {
                //TriggerManager.instance.register(
                //    CancelableTriggerType.PreConfirmReturnTransaction,
                //    new ValidateReturnPreConfirmReturnTransactionTrigger());
                TriggerManager.instance.register(
                    CancelableTriggerType.PreProductSale,
                    new ValidateProductSalePreProductSaleTrigger());
                //TriggerManager.instance.register(
                //    NonCancelableTriggerType.PostCustomerAdd,
                //    new GiveBirthDayDiscountTrigger());
        }

8.  Inspect the registration of **PostLogonTrigger** on the **DOMContentLoad** event.

        /**
        * Trigger types that do not support conditional registration should be registered when the DOMContentLoaded event is fired.
        * @remarks These trigger types include: ApplicationStart, PreLogOn and PostLogOn.
        */
        document.addEventListener("DOMContentLoaded", function (): void {
            Commerce.Triggers.TriggerManager.instance.register(
            Commerce.Triggers.NonCancelableTriggerType.PostLogOn,
            new Commerce.Triggers.Samples.ConditionalRegistrationPostLogOnTrigger());
        });

9.  Compile and rebuild Modern POS to verify the implementation:
    1.  Go to **Show Journal**, and select a transaction to return. If the transaction has multiple lines, return one line. A return line should be added in the cart.
    2.  In the left navigation pane, use product search (the search icon) to search for the text "shirt."
    3.  Select one of the shirt products, and then, on the app bar, click **Sell now**.
    4.  Observe that **IPreProductSaleTrigger** trigger is run. You should receive a message that states that you can't perform a sale and a return in same transaction.




