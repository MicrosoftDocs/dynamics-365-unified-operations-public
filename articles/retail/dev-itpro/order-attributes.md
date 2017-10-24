---
# required metadata

title: Order attributes
description: This topic shows how to edit and set attributes values for orders directly in HQ , POS, and CRT.
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
ms.search.scope: AX 7.0.0, Operations, Retail, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 83892
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 2017-10-24
ms.dyn365.ops.version: AX 7.0.0, Retail September 2017 update

---

# Order attributes

The attribute framework was previously supported only in online orders, now it is extended to support attributes in cash and carry transactions, customer orders, and call center orders. With this new enhancement, you can edit and set attributes values for orders directly in HQ , POS and CRT. To set the values in HQ for call center orders we added the HQ forms to edit and update the values, but there is no out of the box UI available in POS to set the value. You can extend POS to add new UI. If you don’t need any UI and want to add only business logic then you can do that in CRT directly. New attributes can be created using the HQ configurations, without any database changes. Previously you had to create new tables in HQ and channel DB and then modify.

## Why and when you should customer attributes

If you want to add new fields to cash & carry transactions or customer or call center orders and capture the information in POS or HQ then you would use customer attributes. Previously to add a new field to cash and carry transaction (Transaction Header or lines) or customer order in POS you had to create a new extension table in HQ and channel DB and then modify CRT and POS code inline to handle different screens and operations. You also had to configure CDX to sync the data between channel DB and HQ. With customer attributes, all this can be done through configuration without writing any code or creating custom extension tables other than the the core business logic and POS UI. With this first version we are supporting only the string attribute type. In the future, we will support other attribute types. If you want the data to come from the master table and it involves complex search and core business logic in X++, then you should use extension properties.

## Define attribute types

First you need to define the attribute types and assign valid ranges to them.

1. Click **Product information management** > **Setup** > **Categories and Attributes** > **Attribute types**.
2. In the **Attribute types** form, click **New** to add a new attribute type.
3. Enter a name for the attribute type.
4. On the **General** FastTab, in the **Type** field, select the type of data that can be entered for attributes that are assigned to this data type.
5. If the attribute type is **Decimal** or **Integer**, select a unit of measure.
6. To define a fixed list of values for the attribute type, select the **Fixed list** check box. Then, on the **Values** FastTab, add the list of values.
    [!NOTE] The **Fixed list** check box is available only for the **Text** attribute type.  
7. To define a range of valid values for the attribute type, select the **Value range** check box. Then, on the **Range** FastTab, enter the valid range of values.

## Define the attributes 

Next you define the attributes. For each attribute you want to define, follow these steps:

1.  Click **Product information management** > **Setup** > **Categories and Attributes** > **Attributes**.
2.  In the **Attributes** form, click **New** to add a new attribute.
3.  Enter the name, friendly name, description, and any help text that you want to display to the user for the attribute.
4.  In the **Attribute type** field, select the attribute type to assign to the attribute.
5.  Depending on the attribute type, in the **Default value** field enter the value or range of values that is displayed by default when this attribute is assigned to a customer.
6.  Click **Translate**. In the **Text translation** form, enter the name, description, friendly name, and help text for the attribute in different languages.

## Define attribute groups

1.  Click **Product information management** > **Setup** > **Categories and Attributes** > **Attribute groups**.
2.  In the **Attribute groups** form, click **New** to add a new attribute group.
3.  Enter the name, and On the **General** FastTab enter friendly name, description, and any help text for the attribute group.
4.  Click the **Attributes** FastTab.
5.  Click **Add** to add attributes to the attribute group. In the **Default value** field, you can enter a default value for the selected attributes.
6.  Click **Translate** to open the **Text translation** form, where you can enter the description, friendly name, and help text for the attribute group in additional languages.

## Link the attribute group to the channel

1.  Click **Retail** > **Channels** > **Retail stores** > **All retail stores**.
2.  Select the channel for which you want to link the attributes in the channel form.
3.  On the **Set up** tab, click the **Sales order attributes** under the **attribute group**.
4.  In the **Sales order attribute groups** form click **New** to link the attribute group to the channel.
5.  In the **Name** field select the attribute group you want to link from the drop down.
6.  In the **Apply attributes to** filed select any of the below options:
    - Header – The attributes will apply only to the transaction header.
    - Lines – The attribute will apply only to the transaction lines.
    - Default – The attribute will apply to both transaction header and lines.
7.  Click Save.

## Run the distribution jobs

1. Click **Retail** > **Retail IT** > **Distribution schedule**.
2. Select **Products (1040)** and click the **Run now** button in the action bar. When prompted, click **Yes**. This required only if you added any new attributes, attribute types or attribute groups.
3. Select **Channel configuration job (1070)** and click the **Run now** button in the action bar. When prompted, click **Yes**. 

## Set attribute values for call center orders

After you configure the order attributes for the channel, go to **Customer service** or **All Sales order** and create a new call center order.

1. After or during the creation of a customer order, if you want to set an attribute value for the transaction header then click the **Retail** tab in the Action bar and then click **Retail Attributes**.
2. In the **Sales order attributes values** form you can set the values for the attributes. The list of attributes shown in this form is based on the attribute group you configured for that channel.
3. If you want to set attribute values at the line level then select the **Lines** view in the **Sales order form** and then select the line for which you want to set the attribute value. Click **Retail** > **Retail attributes** under the **Sales order lines group**.
4. Repeat for all the sales lines for which you want to set the values.

## View the attributes values for Cash and Carry transaction in HQ

After you run the job and have pulled your transaction to HQ, you can view the attribute values for the cash and carry transaction. There is no UI available in POS to view the order attributes. You must extend POS to show the order attribute values.

1.  Navigate to **Retail** > **Inquires and reports** > **Retail store transactions**.
2.  To view the transaction header attributes, click the **Retail attributes** button in the action bar.
3.  To view the transaction lines attributes, click **Transaction** > **Sales transaction** button in the action bar.
4.  In the **Sales transactions form** select any line and open the **Retail attributes** menu in the action bar to view the lines attributes.

[!NOTE] Only the attributes configured part of your attribute group and linked to the channel will show up in the HQ UI.

## Extend attributes to add business logic in CRT

We added a new sample to the Retail SDK that adds business logic for order attributes in CRT. In this sample we have written code only for the business logic and not for how to save or read the attributes because read and write for attribute is automated. The scenario we implemented was whenever you suspend a cart and then set some attribute value and clear it when you resume the cart. We added pretrigger for **SuspendCartRequest** and wrote the business logic. You can extend any trigger or override any request in CRT based on your scenario to set the logic.

The full sample code is located in the Retail SDK at **Retail SDK\\SampleExtensions\\CommerceRuntime\\Extensions.TransactionAttributesSample**.

1. Create a new C# portable class library project and copy paste the below code:

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

    // Pre trigger code.

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

    // Post trigger code.

    // summary
    // param name="request" The request param

    // param name="response" The response param
    public void OnExecuted(Request request, Response response)
    {
    }
```

## Extend attributes to do some business logic in POS

We added a new sample to the Retail SDK to set business logic for order attributes in POS. In this sample we have written code only for the business logic and not for how to save or read attribute values because read and write for attribute is automated. You can set values for attributes either in CRT or POS based on your scenario if your values are based on customer input then do it in client and if there is some business logic involved then do in CRT.

The scenario we implemented was where you create any B2B order and you want to set the B2B attribute value (Yes or No) based on customer input. We extended the **PreEndTransactionTrigger** in POS to set the values. You can extend any POS trigger or override the request accordingly.

The full sample code is located in the Retail SDK at **Retail SDK\\POS\\Extensions\\B2BSample**.

[!NOTE] Only the configured attributes will show up in the HQ UI, even if you set or add attributes and attribute values in the code. If it's not part of the attribute group you linked to the channel then it will not show up in the HQ UI.

1.  Open ModernPOS.sln\CloudPos.sln from Retail SDK.
2.  Create a new extension folder under the POS.Extension project in the Retail SDK.
3.  Add a new manifest.json file in the new extension folder you created.
4.  Copy paste the below code:
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
1.  Create a new TypeScript file to implement the PreEndTransactionTrigger and add this code:

```typescript
/**
 * Executes the trigger functionality.
 * @param {Triggers.IPreEndTransactionTriggerOptions} options The options provided to the trigger.
 */

public execute(options: Triggers.IPreEndTransactionTriggerOptions): Promise&lt;ClientEntities.ICancelable {
    console.log("Executing PreEndTransactionTrigger with options " + JSON.stringify(options) + ".");
    let currentCart: ProxyEntities.Cart;
    return this.context.runtime.executeAsync<GetCurrentCartClientResponse>(new GetCurrentCartClientRequest())
then((getCurrentCartClientResponse: ClientEntities.ICancelableDataResult<GetCurrentCartClientResponse>):
    Promise<ClientEntities.ICancelableDataResult<GetCustomerClientResponse>> => {
        currentCart = getCurrentCartClientResponse.data.result;
        // Gets the current customer.
        let result: Promise<ClientEntities.ICancelableDataResult<GetCustomerClientResponse>>;
        if (!ObjectExtensions.isNullOrUndefined(currentCart) && !ObjectExtensions.isNullOrUndefined(currentCart.CustomerId)) {
            let getCurrentCustomerClientRequest: GetCustomerClientRequest&lt;GetCustomerClientResponse =
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
.then((showMessageDialogClientResponse: ClientEntities.ICancelableDataResult&lt;ShowMessageDialogClientResponse):
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



