---
# required metadata

title: Order attributes
description: This topic explains how to edit and set attributes values for orders directly in Retail headquarters, the POS, and CRT.
author: mugunthanm
manager: AnnBe
ms.date: 10/24/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 83892
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 2017-10-24
ms.dyn365.ops.version: AX 7.0.0, Retail September 2017 update

---

# Order attributes

Previously, the attribute framework supported attributes only in online orders. However, the framework has been extended so that it now supports attributes in cash-and-carry transactions, customer orders, and call center orders. This enhancement lets you edit and set attribute values for orders directly in Retail headquarters, the point of sale (POS), and the Commerce runtime (CRT). Retail headquarters now includes pages for editing and updating attribute values. Therefore, you can set the values for call center orders in Retail headquarters. Although no out-of-box user interface (UI) for setting attribute values is available in the POS, you can extend the POS to add a new UI. If you don't require a UI and just want to add business logic, you can add the business logic directly in CRT. You can create new attributes by using the Retail headquarters configurations. No database changes are required. Previously, you had to create new tables in Retail headquarters and the channel database, and then modify those tables.

## Why and when you should customer attributes

If you want to add new fields to cash-and-carry transactions, customer orders, or call center orders, and if you want to capture the information in the POS or Retail headquarters, use customer attributes. Previously, to add a new field to a cash-and-carry transaction (transaction header or lines) or a customer order in the POS, you had to create a new extension table in Retail headquarters and the channel database, and then make inline changes to CRT and POS code to handle the various screens and operations. You also had to configure Commerce Data Exchange to synchronize the data between the channel database and Retail headquarters. However, customer attributes now let you complete all these actions through configuration. You don't have to write any code or create custom extension tables, but you still need to create the core business logic and the POS UI.

This first version supports only the **String** attribute type, but future versions will support other attribute types. If you want the data to come from the master table, and that data involves complex search logic and core business logic in X++, you should use extension properties.

## Define attribute types

First, you must define the attribute types and assign valid ranges to them.

1. Go to **Product information management** > **Setup** > **Categories and attributes** > **Attribute types**.
2. On the **Attribute types** page, select **New** to add a new attribute type.
3. Enter a name for the attribute type.
4. On the **General** FastTab, in the **Type** field, select the type of data that can be entered for attributes that are assigned to this data type.
5. If the attribute type is **Decimal** or **Integer**, select a unit of measure.
6. If the attribute type is **Text**, you can define a fixed list of values for it. Select the **Fixed list** check box, and then, on the **Values** FastTab, enter the list of values.
7. To define a range of valid values for the attribute type, select the **Value range** check box. Then, on the **Range** FastTab, enter the valid range of values.

## Define the attributes 

Next, you must define the attributes. Follow these steps for each attribute that you want to define.

1. Go to **Product information management** > **Setup** > **Categories and attributes** > **Attributes**.
2. On the **Attributes** page, select **New** to add a new attribute.
3. Enter a name, friendly name, and description for the attribute. Additionally, enter any Help text that should be shown to the user for the attribute.
4. In the **Attribute type** field, select the attribute type to assign to the attribute.
5. Depending on the attribute type, in the **Default value** field, enter the value or range of values that is shown by default when the attribute is assigned to a customer.
6. Select **Translate**. Then, on the **Text translation** page, enter the name, description, friendly name, and Help text for the attribute in additional languages.

## Define attribute groups

1. Go to **Product information management** > **Setup** > **Categories and attributes** > **Attribute groups**.
2. On the **Attribute groups** page, select **New** to add a new attribute group.
3. Enter a name for the attribute group. Then, on the **General** FastTab, enter a friendly name, a description, and any Help text for the attribute group.
4. On the **Attributes** FastTab, select **Add** to add attributes to the attribute group. In the **Default value** field, you can enter a default value for the selected attributes.
5. Select **Translate**. Then, on the **Text translation** page, enter the description, friendly name, and Help text for the attribute group in additional languages.

## Link the attribute group to the channel

1. Go to **Retail** > **Channels** > **Retail stores** > **All retail stores**.
2. Select the channel that the attributes on the **Channel** page should be linked to.
3. On the **Set up** tab, select **Sales order attributes** under **Attribute group**.
4. On the **Sales order attribute groups** page, select **New** to link the attribute group to the channel.
5. In the **Name** field, select the attribute group to link to the channel.
6. In the **Apply attributes to** field, select one of the following options:

    - **Header** – The attributes will apply only to the transaction header.
    - **Lines** – The attribute will apply only to the transaction lines.
    - **Default** – The attribute will apply to both the transaction header and the transaction lines.

7. Select **Save**.

## Run the distribution jobs

1. Go to **Retail** > **Retail IT** > **Distribution schedule**.
2. Select **Products (1040)**, and then, on the Action Pane, select **Run now**. When you're prompted, select **Yes**. This step is required only if you added any new attributes, attribute types, or attribute groups.
3. Select **Channel configuration job (1070)**, and then, on the Action Pane, select **Run now**. When you're prompted, select **Yes**.

## Set attribute values for call center orders

After you configure the order attributes for the channel, go to **Customer service** or **All Sales orders**, and create a new call center order.

1. After or during the creation of a customer order, if you want to set an attribute value for the transaction header, on the Action Pane, on the **Retail** tab, select **Retail Attributes**.
2. On the **Sales order attributes values** page, you can set the values for the attributes. The list of attributes on this page is based on the attribute group that you configured for the channel.
3. To set attribute values at the line level, on the **Sales order** page, select the **Lines** view, and then select the line to set the attribute value for. Under **Sales order lines group**, select **Retail** > **Retail attributes**.
4. Repeat step 3 for all the sales lines that you want to set the values for.

## View the attributes values for cash-and-carry transactions in Retail headquarters

After you've run the distribution job and pulled a cash-and-carry transaction into Retail headquarters, you can view the attribute values for that transaction. The POS doesn't provide a UI for viewing order attributes. Therefore, to view the order attribute values, you must extend the POS.

1. Go to **Retail** > **Inquires and reports** > **Retail store transactions**.
2. To view the transaction header attributes, on the Action Pane, select **Retail attributes**.
3. To view the transaction lines attributes, on the Action Pane, select **Transaction** > **Sales transaction**.
4. On the **Sales transactions** page, select any line, and then, on the Action Pane, select **Retail attributes** to view the line attributes.

> [!NOTE]
> Only the attributes that are configured as part of your attribute group and linked to the channel will appear in the Retail headquarters UI.

## Extend attributes to add business logic in CRT

A new sample that has been added to the Retail SDK adds business logic for order attributes in CRT. This sample includes code only for the business logic. It doesn't show how to save or read the attributes, because read and write operations for attributes are automated.

The sample implements the following scenario: Whenever you suspend a cart, you set set an attribute value. When you resume the cart, you want to clear that value. A pre-trigger was added for **SuspendCartRequest**, and the business logic was written. You can extend any trigger or override any request in CRT to set the logic, based on your scenario.

You can find the full sample code in the Retail SDK at Retail SDK\\SampleExtensions\\CommerceRuntime\\Extensions.TransactionAttributesSample.

- Create a new C# portable class library project, and paste in the following code.

    ```C#
    public class CustomSuspendCartTrigger : IRequestTrigger
    {
        // summary
        // Gets the list of supported request types.
        public IEnumerable<Type> SupportedRequestTypes
        {
            get
            {
                return new [ ] { typeof(SuspendCartRequest)};
            }
         }

        // Pre-trigger code.

        // summary
        // param name="request" The request param
        public void OnExecuting(Request request)
        {
            ThrowIf.Null(request, "request");
            Type requestedType = request.GetType();
            if (requestedType == typeof(SuspendCartRequest))
            {
                SuspendCartRequest suspendCartRequest = request as SuspendCartRequest;
                // Get the cart.
                var getCartServiceRequest = new GetCartServiceRequest(
                    new CartSearchCriteria(suspendCartRequest.CartId), QueryResultSettings.SingleRecord);
                Cart cart = request.RequestContext.Execute<GetCartServiceResponse>(getCartServiceRequest).Carts.Single();
                // Update the transaction header attribute for customer order.
                if (cart.CartType == CartType.CustomerOrder)
                {
                    bool cartUpdated = CustomCartHelper.CreateUpdateTransactionHeaderAttribute(
                        cart, reserveNow: false, updateAttribute: true);
                    if (cartUpdated)
                    {
                        // Save the cart after updating the header attribute.
                        var saveCartRequest = new SaveCartRequest(cart);
                        request.RequestContext.Execute<SaveCartResponse>(saveCartRequest);
                    } 
                } 
            } 
        }

        // Post-trigger code.

        // summary
        // param name="request" The request param
        // param name="response" The response param
        public void OnExecuted(Request request, Response response)
        {
        }
    ```

## Extend attributes to do some business logic in the POS

A new sample that has been added to the Retail SDK sets the business logic for order attributes in the POS. This sample includes code only for the business logic. It doesn't show how to save or read attribute values, because read and write operations for attributes are automated. You can set the values for attributes in either CRT or the POS, based on your scenario. If your values are based on customer input, set them in the POS client. If some business logic is involved, set the values in CRT.

The sample implements the following scenario: You create a business-to-business (B2B) order and want to set the B2B attribute value (**Yes** or **No**), based on customer input. **PreEndTransactionTrigger** was extended in the POS to set the values. You can extend any POS trigger or override the request as appropriate.

You can find the full sample code in the Retail SDK at Retail SDK\\POS\\Extensions\\B2BSample.

> [!NOTE]
> Only the configured attributes will appear in the Retail headquarters UI, even if you set or add attributes and attribute values in the code. If an attribute isn't part of the attribute group that you linked to the channel, it won't appear in the Retail headquarters UI.

1. From the Retail SDK, open **ModernPOS.sln\\CloudPos.sln**.
2. In the Retail SDK, create a new extension folder under the **POS.Extension** project.
3. In the new extension folder, add a new **manifest.json** file.
4. Paste in the following code.

    ```typescript
    {
        "$schema": "..manifestSchema.json",
        "name": "Pos_Extensibility_B2BSample",
        "publisher": "Microsoft",
        "version": "7.2.0",
        "minimumPosVersion": "7.2.0.0",
        "components": {
        "resources": {
        "supportedUICultures": [ "en-US" ],
        "fallbackUICulture": "en-US",
        "culturesDirectoryPath": "Resources/Strings",
        "stringResourcesFileName": "resources.resjson" 
    },
    "extend": {
        "triggers": [
        {
            "triggerType": "PreEndTransaction",
            "modulePath": "TriggerHandlers/PreEndTransactionTrigger"
        }  
        ]
    } } }
    ```
5.  Create a new TypeScript file to implement **PreEndTransactionTrigger**, and add the following code.

    ```typescript
    /**
     * Executes the trigger functionality.
     * @param {Triggers.IPreEndTransactionTriggerOptions} options The options provided to the trigger.
     */

    public execute(options: Triggers.IPreEndTransactionTriggerOptions): Promise<ClientEntities.ICancelable {
        console.log("Executing PreEndTransactionTrigger with options " + JSON.stringify(options) + ".");
        let currentCart: ProxyEntities.Cart;
        return this.context.runtime.executeAsync<GetCurrentCartClientResponse>(new GetCurrentCartClientRequest())
    then((getCurrentCartClientResponse: ClientEntities.ICancelableDataResult<GetCurrentCartClientResponse>):
        Promise<ClientEntities.ICancelableDataResult<GetCustomerClientResponse>> => {
            currentCart = getCurrentCartClientResponse.data.result;
            // Gets the current customer.
            let result: Promise<ClientEntities.ICancelableDataResult<GetCustomerClientResponse>>;
            if (!ObjectExtensions.isNullOrUndefined(currentCart) && !ObjectExtensions.isNullOrUndefined(currentCart.CustomerId)) {
                let getCurrentCustomerClientRequest: GetCustomerClientRequest<GetCustomerClientResponse =
                    new GetCustomerClientRequest(currentCart.CustomerId);
                result = this.context.runtime.executeAsync<GetCustomerClientResponse>(getCurrentCustomerClientRequest);
            } else {
                result = Promise.resolve({ canceled: false, data: new GetCustomerClientResponse(null) });
            }
            return result;
        })
     .then((getCurrentCustomerClientResponse: ClientEntities.ICancelableDataResult<GetCustomerClientResponse>):
        Promise<ClientEntities.ICancelableDataResult<ShowMessageDialogClientResponse>> => {
        let currentCustomer: ProxyEntities.Customer = getCurrentCustomerClientResponse.data.result;
        // If the cart is a customer order with a B2B customer, then we display a dialog to determine if the order should be B2B.
        let result: Promise<ClientEntities.ICancelableDataResult<ShowMessageDialogClientResponse>>;
        if (!ObjectExtensions.isNullOrUndefined(currentCart)
            && currentCart.CustomerOrderModeValue === ProxyEntities.CustomerOrderMode.CustomerOrderCreateOrEdit
            && !ObjectExtensions.isNullOrUndefined(currentCustomer)
            && this.isCustomerB2B(currentCustomer)) {
            let yesButton: ClientEntities.Dialogs.IDialogResultButton = {
                id: PreEndTransactionTrigger.DIALOG_YES_BUTTON_ID,
                label: this.context.resources.getString("string_0"),  "Yes"
                result: PreEndTransactionTrigger.DIALOG_RESULT_YES
            };
            let noButton: ClientEntities.Dialogs.IDialogResultButton = {
                id: PreEndTransactionTrigger.DIALOG_NO_BUTTON_ID,
                label: this.context.resources.getString("string_1"),  "No"
                result: PreEndTransactionTrigger.DIALOG_RESULT_NO
            };
            let showMessageDialogClientRequestOptions: ClientEntities.Dialogs.IMessageDialogOptions = {
                title: this.context.resources.getString("string_2"),  "B2B Order"
                subTitle: StringExtensions.EMPTY,
                message: this.context.resources.getString("string_3"),  "Do you want to mark this order as a B2B order?"
                button1: yesButton,
                button2: noButton
            };
            let showMessageDialogClientRequest: ShowMessageDialogClientRequest<ShowMessageDialogClientResponse> =
                new ShowMessageDialogClientRequest(showMessageDialogClientRequestOptions);
            result = this.context.runtime.executeAsync<ShowMessageDialogClientResponse>(showMessageDialogClientRequest);
        } else {
            result = Promise.resolve({ canceled: false, data: new ShowMessageDialogClientResponse(null) });
        }
        return result;
    })
    .then((showMessageDialogClientResponse: ClientEntities.ICancelableDataResult<ShowMessageDialogClientResponse):
        Promise<ClientEntities.ICancelableDataResult<SaveAttributesOnCartClientResponse>> => {
        // Save the B2B attribute value depending on the dialog result.
        let messageDialogResult: ClientEntities.Dialogs.IMessageDialogResult = showMessageDialogClientResponse.data.result;
        let result: Promise<ClientEntities.ICancelableDataResult<SaveAttributesOnCartClientResponse>>;
        if (!ObjectExtensions.isNullOrUndefined(messageDialogResult)) {
            let attributeValue: ProxyEntities.AttributeTextValue = new ProxyEntities.AttributeTextValueClass();
            attributeValue.Name = PreEndTransactionTrigger.B2B_CART_ATTRIBUTE_NAME;
            attributeValue.TextValue = messageDialogResult.dialogResult === PreEndTransactionTrigger.DIALOG_RESULT_YES?
            PreEndTransactionTrigger.B2B_ATTRIBUTE_VALUE_TRUE : PreEndTransactionTrigger.B2B_ATTRIBUTE_VALUE_FALSE;
            let attributeValues: ProxyEntities.AttributeValueBase[] = [attributeValue];
            let saveAttributesOnCartRequest: SaveAttributesOnCartClientRequest<SaveAttributesOnCartClientResponse> =
            new SaveAttributesOnCartClientRequest(attributeValues);
            result = this.context.runtime.executeAsync(saveAttributesOnCartRequest);
        } else {
            result = Promise.resolve({ canceled: false, data: new SaveAttributesOnCartClientResponse(null) });
        }
        return result;
    });
    }
    /**
    * Returns whether or not the given customer is a B2B customer.
    * @param {ProxyEntities.Customer} customer The customer.
    * @returns {boolean} Whether or not the given customer is a B2B customer.
    */
    private isCustomerB2B(customer: ProxyEntities.Customer): boolean {
        let isB2B: boolean = false;
        if (!ObjectExtensions.isNullOrUndefined(customer.Attributes)) {
            for (let i: number = 0; i < customer.Attributes.length; i++) {
                let currentAttribute: ProxyEntities.CustomerAttribute = customer.Attributes[i];
                if (currentAttribute.Name === PreEndTransactionTrigger.B2B_CUSTOMER_ATTRIBUTE_NAME) {
                    if (!ObjectExtensions.isNullOrUndefined(currentAttribute.AttributeValue.BooleanValue)) {
                        isB2B = currentAttribute.AttributeValue.BooleanValue;
                    }
                    break;
                }
            }  
        }
        return isB2B;
    } } } }
    ```
