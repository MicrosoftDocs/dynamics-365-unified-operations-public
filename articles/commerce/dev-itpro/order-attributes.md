---
title: Define and set order attributes
description: Learn how to edit and set attributes values for orders directly in Microsoft Dynamics 365 Commerce headquarters, the point of sale (POS), and Commerce runtime (CRT).
author: josaw1
ms.date: 02/18/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2017-10-24
ms.custom: 
  - bap-template
---

# Define and set order attributes

[!include [banner](../../includes/banner.md)]

This article explains how to edit and set attribute values for orders directly in Microsoft Dynamics 365 Commerce headquarters, the point of sale (POS), and Commerce runtime (CRT).

Previously, the attribute framework supported attributes only in online orders. However, the framework now supports attributes in cash-and-carry transactions, customer orders, and call center orders. This enhancement lets you edit and set attribute values for orders directly in Commerce headquarters, the POS, and the CRT.

Headquarters now includes pages for editing and updating attribute values, which means that you can set the values for call center orders in headquarters. In POS, use the Attributes panel to set or update the attribute value in POS. If you don't need to use a user interface and just want to add business logic, you can add the business logic directly in CRT. You can create new attributes by using the headquarters configurations. No database changes are required. Previously, you had to create new tables in headquarters and the channel database, and then modify those tables.

## Why and when you should add order attributes

If you want to add new fields to cash-and-carry transactions, customer orders, or call center orders, and if you want to capture the information in the POS or headquarters, use order attributes. Previously, to add a new field to a cash-and-carry transaction (transaction header or lines) or a customer order in the POS, you had to create a new extension table in headquarters and the channel database, and then make inline changes to CRT and POS code to handle the various screens and operations. You also had to configure Commerce Data Exchange to synchronize the data between the channel database and headquarters. However, order attributes now let you complete all these actions through configuration. You don't have to write any code or create custom extension tables, but you still need to create the core business logic and the POS UI.

This first version supports only the **String** attribute type, but future versions will support other attribute types. If you want the data to come from the master table, and that data involves complex search logic and core business logic in X++, use extension properties.

> [!NOTE]
> Attributes are supported only on customer orders and cash-and-carry transactions. No other transaction types support attributes.

## Define attribute types

To define the attribute types and assign valid ranges to them, follow these steps:

1. In Commerce headquarters, go to **Product information management** > **Setup** > **Categories and attributes** > **Attribute types**.
1. On **Attribute types**, select **New** to add a new attribute type.
1. Enter a name for the attribute type.
1. On the **General** FastTab, in the **Type** field, select the type of data that users can enter for attributes that are assigned to this data type.
1. If the attribute type is **Decimal** or **Integer**, select a unit of measure.
1. If the attribute type is **Text**, define a fixed list of values for it. Select the **Fixed list** check box, and then, on the **Values** FastTab, enter the list of values.
1. To define a range of valid values for the attribute type, select the **Value range** check box. Then, on the **Range** FastTab, enter the valid range of values.

## Define the attributes

To define the attributes, follow these steps for each attribute that you want to define:

1. In headquarters, go to **Product information management** > **Setup** > **Categories and attributes** > **Attributes**.
1. On **Attributes**, select **New** to add a new attribute.
1. Enter a name, friendly name, and description for the attribute. Additionally, enter any Help text that you want to show to the user for the attribute.
1. In the **Attribute type** field, select the attribute type to assign to the attribute.
1. Depending on the attribute type, in the **Default value** field, enter the value or range of values that you want to show by default when the attribute is assigned to a channel.
1. Select **Translate**. Then, on the **Text translation** page, enter the name, description, friendly name, and Help text for the attribute in more languages.

## Define attribute groups

To define attribute groups, follow these steps:

1. In headquarters, go to **Product information management** > **Setup** > **Categories and attributes** > **Attribute groups**.
1. On **Attribute groups**, select **New** to add a new attribute group.
1. Enter a name for the attribute group. Then, on the **General** FastTab, enter a friendly name, a description, and any Help text for the attribute group.
1. On the **Attributes** FastTab, select **Add** to add attributes to the attribute group. In the **Default value** field, enter a default value for the selected attributes.
1. Select **Translate**. Then, on the **Text translation** page, enter the description, friendly name, and Help text for the attribute group in more languages.

## Link the attribute group to the channel

To link the attribute group to the channel, follow these steps:

1. In headquarters, go to **Retail and Commerce** > **Channels** > **Stores** > **All stores**.
1. Select the channel that you want to link the attributes on the **Channel** page to.
1. On the **Set up** tab, select **Sales order attributes** under **Attribute group**.
1. On **Sales order attribute groups**, select **New** to link the attribute group to the channel.
1. In the **Name** field, select the attribute group to link to the channel.
1. In the **Apply attributes to** field, select one of the following options:

    - **Header** – The attributes apply only to the transaction header.
    - **Lines** – The attribute applies only to the transaction lines.
    - **Default** – The attribute applies to both the transaction header and the transaction lines.

1. Select **Save**.

## Run the distribution jobs

To run the distribution jobs, follow these steps:

1. In headquarters, go to **Retail and Commerce** > **Retail and Commerce IT** > **Distribution schedule**.
1. Select **Products (1040)**, and then, on the Action Pane, select **Run now**. When prompted, select **Yes**. This step is required only if you added any new attributes, attribute types, or attribute groups.
1. Select **Channel configuration job (1070)**, and then, on the Action Pane, select **Run now**. When prompted, select **Yes**.

## Show order attributes in the POS transaction screen using the Attribute control (this feature is available in version 8.1.3 and later)

### Headquarters

1. In headquarters, go to **Retail and Commerce > Channel setup > POS Setup > POS > Screen layouts**.
1. On the screen layout page, select **New** to create a new screen layout, or select an existing screen layout.
1. Enter the ID and name for the screen layout.
1. On the **Layout sizes** FastTab, select the **Add** button to add new layout sizes for the POS.
1. In the **Name** field, select the POS screen resolution.
1. On the **Layout sizes** FastTab, select the **Layout designer** button.
1. If you're prompted, select **Yes** to download and install the Designer Host by using the **Install/Run** button.
1. When prompted, enter the Microsoft Dynamics 365 user name and password to start the designer.
1. After the designer starts, drag the Attributes panel anywhere in the screen layout designer and adjust the size according to your screen width.
1. When you finish, select **OK** to save your changes.
1. Close the screen layout designer by selecting the **Close** button (X) in the upper-right corner. When prompted, select **Yes** to save your changes.
1. Go to **Retail and Commerce > Retail and Commerce IT > Distribution schedule**.
1. Select the Registers job (1090), and then, on the Action Pane, select **Run now**. When prompted, select Yes.

### POS

1. Start POS, and add any item to a transaction. You should see the Attribute panel in the transaction screen with the configured attributes both for header and lines.
1. Select the **Edit** icon in the attribute panel to update the attribute value.
1. Select the header or lines tab in the attribute panel to view the header or lines attribute.
1. The lines attribute refreshes automatically based on the lines selected in the transaction.

## Set attribute values for call center orders

After you configure the order attributes for the channel, go to **Customer service** or **All Sales orders**, and create a new call center order.

1. After or during the creation of a customer order, if you want to set an attribute value for the transaction header, on the Action Pane, go to the **Commerce** tab, select **Attributes**.
1. On the **Sales order attributes values** page, set the values for the attributes. The list of attributes on this page is based on the attribute group that you configured for the channel.
1. To set attribute values at the line level, on the **Sales order** page, select the **Lines** view, and then select the line to set the attribute value for. Under **Sales order lines group**, select **Retail and Commerce** > **Attributes**.
1. Repeat step 3 for all the sales lines that you want to set the values for.

## View the attributes values for cash-and-carry transactions in headquarters

After you run the distribution job and pull a cash-and-carry transaction into headquarters, you can view the attribute values for that transaction. The POS doesn't provide a UI for viewing order attributes. Therefore, to view the order attribute values, you must extend the POS.

1. Go to **Retail and Commerce** > **Inquires and reports** > **Store transactions**.
1. To view the transaction header attributes, on the Action Pane, select **Attributes**.
1. To view the transaction lines attributes, on the Action Pane, select **Transaction** > **Sales transaction**.
1. On the **Sales transactions** page, select any line, and then, on the Action Pane, select **Attributes** to view the line attributes.

> [!NOTE]
> Only the attributes that you configure as part of your attribute group and link to the channel appear in the headquarters UI.

## Extend attributes to add business logic in CRT

A sample is added to the Retail SDK adds business logic for order attributes in CRT that includes code only for the business logic. It doesn't show how to save or read the attributes, because read and write operations for attributes are automated.

The sample implements the following scenario: When you suspend a cart, you set an attribute value. When you resume the cart, you clear that value. The sample adds a pre-trigger for **SuspendCartRequest** and writes the business logic. You can extend any trigger or override any request in CRT to set the logic, based on your scenario.

> [!NOTE]
> Before adding an attribute to the cart, check whether the attribute already exists in the cart or cart line. If the attribute already exists, update it instead of adding it again. If you add a duplicate attribute to the cart or cart line, CRT displays a runtime error. Sample code for this scenario can be found in the following sample code section.

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
        // Sample code to check for the duplicate attribute, before adding attributes to the cart check whether the attribute already exists if so then don’t add the attribute again, instead update it.
        
        public static class CustomCartHelper
        {
            /// <summary>
            /// Updates the transaction header attribute.
            /// </summary>
            /// <param name="cart">The cart.</param>
            /// <param name="reserveNow">The value of the transaction header attribute.</param>
            /// <param name="updateAttribute">A flag indicating whether or not to override an existing attribute value.</param>
            /// <returns>A flag indication whether or not the cart was updated.</returns>
            public static bool CreateUpdateTransactionHeaderAttribute(Cart cart, bool reserveNow, bool updateAttribute)
            {
                ThrowIf.Null(cart, "cart");
                bool cartUpdated = false;
                IList<AttributeValueBase> transactionAttributes = cart.AttributeValues;
                string reserveNowAttributeName = "Reserve now";
                string reserveNowAttributeValue = reserveNow ? "Yes" : "No";
                AttributeValueBase reserveNowAttribute = transactionAttributes.SingleOrDefault(attribute => attribute.Name.Equals(reserveNowAttributeName));

                if (reserveNowAttribute == null)
                {
                    transactionAttributes.Add(new AttributeTextValue() { Name = reserveNowAttributeName, TextValue = reserveNowAttributeValue });
                    cartUpdated = true;
                }
                else if (updateAttribute && !((AttributeTextValue)reserveNowAttribute).TextValue.Equals(reserveNowAttributeValue))
                {
                    ((AttributeTextValue)reserveNowAttribute).TextValue = reserveNowAttributeValue;
                    cartUpdated = true;
                }

                return cartUpdated;
            }
        }
```

## Extend a Dynamics 365 Commerce e-commerce site to set values for order attributes in the cart

Use this code to set values for order attributes in the cart.

```javascript
public _addOrUpdateSalesOrderAttributes = (cart: Cart): void => {
    // Create the array of attribute and add attributes
    const attributeArr: AttributeValueBase[] = [];
    let attributeObj = {
        // @ts-ignore
        '@odata.type': '#Microsoft.Dynamics.Commerce.Runtime.DataModel.AttributeTextValue',
        Name: 'Brand',
        ExtensionProperties: [],
        TextValue: 'OscarBrand-2',
        TextValueTranslations: []
    };
    attributeObj.Name = 'Brand';
    attributeArr.push(attributeObj);

    attributeObj = {
        // @ts-ignore
        '@odata.type': '#Microsoft.Dynamics.Commerce.Runtime.DataModel.AttributeTextValue',
        Name: 'Connector',
        ExtensionProperties: [],
        TextValue: 'OscarConnector-2',
        TextValueTranslations: []
    };
    attributeObj.Name = 'Connector';
    attributeArr.push(attributeObj);

    cart.AttributeValues = attributeArr;
    updateAsync({ callerContext: this.props.context.actionContext}, cart)
                .then(newCart => {
                    console.log('Success');
                    this.props.context.actionContext.update(new GetCheckoutCartInput(this.props.context.request.apiSettings), newCart);
                })
                .catch(error => {
                    console.log(error);
                });
};
```

## Extend attributes to do some business logic in the POS

> [!NOTE]
> The following changes are required only if you're running the application with version 8.1.2 or earlier.
Starting in 8.1.3, you can use the Attributes panel to set or update the attribute value in POS. By using this control, you no longer need to write any additional code or create a UI to set the attribute value in POS. The attribute control UI is added to set or update the attribute value. For more information, see the **Show Order attributes in the POS transaction screen using the Attribute control** section in this document.

A new sample that was added to the Retail SDK sets the business logic for order attributes in the POS. This sample includes code only for the business logic. It doesn't show how to save or read attribute values, because read and write operations for attributes are automated. You can set the values for attributes in either CRT or the POS, based on your scenario. If your values are based on customer input, set them in the POS client. If some business logic is involved, set the values in CRT.

The sample implements the following scenario: You create a business-to-business (B2B) order and want to set the B2B attribute value (**Yes** or **No**), based on customer input. **PreEndTransactionTrigger** was extended in the POS to set the values. You can extend any POS trigger or override the request as appropriate.

You can find the full sample code in the Retail SDK at Retail SDK\\POS\\Extensions\\B2BSample.

> [!NOTE]
> Only the configured attributes appear in the headquarters UI, even if you set or add attributes and attribute values in the code. If an attribute isn't part of the attribute group that you linked to the channel, it doesn't appear in the headquarters UI.

1. From the Retail SDK, open **ModernPOS.sln\\CloudPos.sln**.
1. In the Retail SDK, create a new extension folder under the **POS.Extension** project.
1. In the new extension folder, add a new **manifest.json** file.
1. Paste in the following code.

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

1. Create a new TypeScript file to implement **PreEndTransactionTrigger**, and add the following code.

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
    .then((showMessageDialogClientResponse: ClientEntities.ICancelableDataResult<ShowMessageDialogClientResponse>):
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

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
