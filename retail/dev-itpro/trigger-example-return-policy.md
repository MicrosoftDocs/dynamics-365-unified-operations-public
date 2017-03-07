---
# required metadata

title: Implement a return policy using triggers
description: This topic has two examples which show how you can implement a new policy using a trigger.
author: josaw1
manager: AnnBe
ms.date: 2016-03-17 18 - 37 - 11
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: josaw1
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 65863
ms.assetid: 539105e2-097d-4723-84a1-8084c2c32652
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.dyn365.ops.intro: 01-02-2016
ms.dyn365.ops.version: AX 7.0.0

---

# Implement a return policy using triggers

This topic has two examples which show how you can implement a new policy using a trigger.

The examples in this topic assume that you have a new return policy. The maximum time period for returning an item is 30 days and no item may be returned more than 30 days after the date of purchase. Additionally, the cashier or manager is not allowed to void more than three items in a single transaction.

## Extend the MPOS trigger
1.  Open Visual Studio as an administrator.
2.  Open the ModernPOS solution from K:\\RainMainStab\\7.0.1265.3014\\retail\\Services\\RetailSDK\\Code\\POS.
3.  Add new a TypeScript file in the POS.Core project, under the **Triggers** folder, and name it ExtensionTrigger.ts.
4.  Add reference to the triggers interface and create a new module for the code. In the ExtensionTrigger.ts file, add the following code.

        <///<reference path="TransactionTriggers.ts" />
        ///<reference path="TriggerHelper.ts" />
        ///<reference path="TriggerManager.ts" />
        ///<reference path="ApplicationTriggers.ts" />
        ///<reference path="ProductTriggers.ts" />
        ///<reference path="../IAsyncResult.ts" />
        ///<reference path="../Entities/CommerceTypes.g.ts" />
        ///<reference path='ITrigger.ts' />
        module Commerce.Triggers.Samples {
            "use strict";
        }

## Scenario 1: 30day return policy
To implement the 30-day return policy, extend the IPreConfrimReturnTransactionTrigger by creating a new class and implementing the IPreConfirmReturnTransactionTrigger interface. This trigger will be invoked before returning any item from the transaction.

1.  Create a new class that implements IPreConfirmReturnTransactionTrigger in the module Commerce.Triggers.Samples. Name it PreConfirmReturnTransactionTrigger, as shown in the following code example.

        /*** Implementation of a pre-confirm return transaction trigger that validates that the transaction being returned is within the return period. */
        export class PreConfirmReturnTransactionTrigger implements IPreConfirmReturnTransactionTrigger {
        }

2.  Implement the **execute** method from the interface and add code to validate the return condition.

        private static MILLISECONDS_PER_DAY: number = 100;
        private static RETURN_PERIOD_IN_DAYS: number = 0;
        private static RETURN_PERIOD_ENDED_ERROR_CODE: string = "Cannot return, you are past return date";
        /*** Executes the trigger. */
        public execute(options: IPreConfirmReturnTransactionTriggerOptions):     Commerce.IAsyncResult<Commerce.ICancelableResult> {
            var timeDiff: number = Math.abs(new Date().getTime() - options.originalTransaction.BusinessDate.getTime());
            var diffDays: number = Math.ceil(timeDiff / PreConfirmReturnTransactionTrigger.MILLISECONDS_PER_DAY);
            if (diffDays > PreConfirmReturnTransactionTrigger.RETURN_PERIOD_IN_DAYS) {
                var error: Proxy.Entities.Error = new     Proxy.Entities.Error(PreConfirmReturnTransactionTrigger.RETURN_PERIOD_ENDED_ERROR_CODE);
                return Commerce.AsyncResult.createRejected([error]);
            }
            return Commerce.AsyncResult.createResolved({ canceled: false });
        }

## Scenario 2: Limit of three returns per transaction
To implement the three-time limit, create a new class and implement the IPreVoidProductsTrigger interface. This trigger will be invoked before voiding any item in a transaction.

1.  Create a new class named PreVoidProductsTrigger that implements the IPreVoidProductsTrigger interface in the module Commerce.Triggers.Samples. Make sure this code is outside of the PreConfirmReturnTransactionTrigger class that you created in the previous step.

        /*** Implementation of a pre-customer add trigger that is used to ensure a blocked customer is not added to sale. */
        export class PreVoidProductsTrigger implements IPreVoidProductsTrigger {
        }

2.  Implement the **execute** method from the interface and add the code to validate the void condition.

        private static VOID_ERROR_CODE: string = "Void is not allowed anymore.";
        /*** Executes the trigger. */
        public execute(options: IPreVoidProductsTriggerOptions): IAsyncResult<ICancelableResult> {
            var result: AsyncResult<ICancelableResult> = new AsyncResult<ICancelableResult>(null);
            if (!options.cartLines[0].IsVoided && this.getVoidedQuantity(options.cart) > 2) {
                var error: Proxy.Entities.Error =
                new Proxy.Entities.Error(PreVoidProductsTrigger.VOID_ERROR_CODE);
                result.reject([error]);
            } else {
                result.resolve({ canceled: false });
            }
            return result;
        }

        private getVoidedQuantity(cart: Proxy.Entities.Cart): number {
            var voidedQuantity: number = 0;
            cart.CartLines.forEach((cartLine: Proxy.Entities.CartLine) => {
            if (cartLine.IsVoided) {
                voidedQuantity = voidedQuantity + 1;
            }
            });
            return voidedQuantity;
        }

3.  Register the two triggers after the MPOS logon. Copy the following code to the same file after the two classes that you created in the previous steps but within the same module Commerce.Triggers.Samples.

        /*** Implementation of a post log on trigger that is used to perform conditional registration of other triggers.*/
        export class ConditionalRegistrationPostLogOnTrigger implements IPostLogOnTrigger {
            private static alreadyRegistered: boolean = false;
            /*** Executes the trigger.*/
            public execute(options: IPostLogOnTriggerOptions): IVoidAsyncResult {
                // Check to ensure the triggers have not already been registered.
                if (!ConditionalRegistrationPostLogOnTrigger.alreadyRegistered) {
                    this.performRegistration();
                    // Set already registered field to true to prevent duplicate trigger registration.
                    ConditionalRegistrationPostLogOnTrigger.alreadyRegistered = true;
                }
                return VoidAsyncResult.createResolved();
            }

            /*** Perform the conditional registration of triggers.*/
            private performRegistration(): void {
            var conditionIsMet: boolean = true;
            TriggerManager.instance.register(
                CancelableTriggerType.PreVoidProducts,
                new PreVoidProductsTrigger());
            if (conditionIsMet) {
                TriggerManager.instance.register(
                CancelableTriggerType.PreReturnTransaction,
                new PreConfirmReturnTransactionTrigger());
        }}}

4.  Register the PostLogon trigger during the DOMCOntentLoaded event. Copy the following code outside of all the classes but within the module Commerce.Triggers.Samples.

        /**
        * Trigger types that do not support conditional registration should be registered when the DOMContentLoaded event is fired.
        * @remarks These trigger types include: ApplicationStart, PreLogOn, and PostLogOn.
        */
        document.addEventListener("DOMContentLoaded", function (): void {
            Commerce.Triggers.TriggerManager.instance.register(
            Commerce.Triggers.NonCancelableTriggerType.PostLogOn,
            new Commerce.Triggers.Samples.ConditionalRegistrationPostLogOnTrigger());
        });

## Build the project
1.  Compile and rebuild the project.
2.  Deploy the MPOS in Local Machine by clicking the **Deploy** button in Visual Studio. If you get an error which states that “The project POS.App needs to be deployed before it can be started.”, then follow the steps below to resolve the error and try again.
3.  Right-click the ModernPOS solution in Visual Studio and click **Properties**.
4.  In the **Property** window, select **Configuration**.
5.  Select the **Deploy** check box for the Pos.App project and click **OK**.

## Validate the customization
1.  Log in to MPOS using 000160 as the operator ID and 123 as the password. Complete a sales transaction.
2.  Click **Show Journal** and try to return the merchandise. You will get the error message “Cannot return, you are past return date”.
3.  Create another new transaction and add four different items. Try to return all four items. You will get an error for the fourth item with the message, "Void is not allowed anymore.”

**Note:** In the sample code, the return the time period is configured as 100ms, so that you can test your code immediately. You should change the configuration as needed.

