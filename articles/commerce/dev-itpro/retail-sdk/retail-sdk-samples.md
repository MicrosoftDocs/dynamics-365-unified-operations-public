---
title: Extend Commerce Store receipts
description: Learn how to extend Microsoft Dynamics 365 Commerce store receipts.
author: ritakimani
ms.date: 02/20/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: ritakimani
ms.search.validFrom: 2016-08-30
ms.custom: 
  - bap-template
---

# Extend Commerce Store receipts

[!include [banner](../../includes/banner.md)]

This article describes how to extend Microsoft Dynamics 365 Commerce store receipts. Receipts can have two types of extensions:

- **Custom fields** - Adds new receipt fields to the existing receipts.
- **Custom receipt types** - Creates new receipts for custom scenarios.

## Custom fields

**Scenario:** Fabrikam wants to print a special receipt whenever products that have a warranty are sold. Sales receipts should include the warranty expiration date, the warranty ID, and other information. Here are the business requirements:

- Print special receipts.
- Print additional warranty information on sale receipts.

The following steps show the Commerce headquarters configuration and CRT code changes for the custom fields.

## Configure headquarters for custom fields

In headquarters, you create two custom receipt fields: **EXPIRATIONDATE** for the warranty expiration date and **WARRANTYID** for the warranty ID. You add these fields to the receipt format layout.

To configure headquarters for custom fields, follow these steps:

1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Language text**.
1. On the **POS** tab, select **Add** to add a new POS language text.

    You can localize the text that appears in the **Receipt** panel. Therefore, you can create multiple texts in different languages for the same text ID. Here's an example.

    | Language ID | Text ID | Text   |
    |-------------|---------|--------|
    | en-US       | 1       | WARRANTYID |
    | en-UK       | 1       | WARRANTYID   |

1. On the Action Pane, select **Save** to save your changes.
1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Custom fields**.
1. On the Action Pane, select **New** to add a new custom field, and specify the following information: 

    1. In the **Name** field, enter the name of the custom field.
    1. In the **Type** field, select **Receipt**.
    1. In the **Caption text ID** field, specify the text ID that you used in step 3.

    Here's an example.

    | Name   | Type        | Caption text ID |
    |--------|-------------|-----------------|
    | WARRANTYID | Receipt | 1               |

1. On the Action Pane, select **Save** to save your changes.
1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS \> Receipt formats**.
1. Select an existing or create a new receipt format and then select **Designer** on the Action Pane.
1. If you're prompted to confirm that you want to open the application, select **Open**, and then follow the installation instructions.
1. After the designer is installed, you're asked for Microsoft Entra credentials. Enter the information to start the designer.
1. In the designer, drag and drop the **Custom** field from the left pane to the receipt designer.

> [!NOTE]
> The Custom fields are legal-entity specific, which means that the screen layout designer fetches the custom fields that are specific to the legal entity (Company) configured for the user signed in to **System Administration > Users**. If you configured custom fields for different legal entities, the screen layout designer might not show those values.

1. Save the changes.
1. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**.
1. Select the **Channel configuration** (**1070**) job, and then select **Run now**.

## Sample code to implement custom fields

To add custom fields to sales receipts or any receipt format, implement **GetSalesTransactionCustomReceiptFieldServiceRequest** and the business logic for the custom fields in CRT, as shown in the following code. For more information, see [Commerce runtime (CRT) extensibility](../commerce-runtime-extensibility.md).

```C#
public IEnumerable<Type> SupportedRequestTypes
{
    get
    {
        return new[] { typeof(GetSalesTransactionCustomReceiptFieldServiceRequest) };
    }
}
public Response Execute(Request request)
{
    Type requestedType = request.GetType();
    if (requestedType == typeof(GetSalesTransactionCustomReceiptFieldServiceRequest))
    {
        return this.GetCustomReceiptFieldForSalesTransactionReceipts( (GetSalesTransactionCustomReceiptFieldServiceRequest)request);
    }
    throw new NotSupportedException(string.Format("Request '{0}' is not supported.", request.GetType()));
}
```

### Add the business logic for the custom fields

```C#
private GetCustomReceiptFieldServiceResponse GetCustomReceiptFieldForSalesTransactionReceipts( GetSalesTransactionCustomReceiptFieldServiceRequest request)
{
    string receiptFieldName = request.CustomReceiptField;
    string returnValue = null;
    switch (receiptFieldName)
    {
        case "WARRANTYID":
            {
                // Write your logic
            }
            break;
        case "EXPIRATIONDATE":
            {
                // Write your logic
            }
            break;
    }
    return new GetCustomReceiptFieldServiceResponse(returnValue);
}
```

## Custom receipt types

### Custom receipt type configuration in headquarters

1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS \> Receipt formats**.
1. Create new Receipt format and then select the **Receipt type** and choose one of the CustomReceiptType(1...20).
1. Save the changes.
1. Select **Designer** on the Action Pane.
1. If you're prompted to confirm that you want to open the application, select **Open**, and then follow the installation instructions.
1. After the designer is installed, you're asked for Microsoft Entra credentials. Enter the information to start the designer.
1. In the designer, drag and drop the required receipt fields from the left pane to the receipt designer.
1. Save the changes.
1. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**.
1. Select the **Channel configuration** (**1070**) job, and then select **Run now**.

### Sample code to implement custom receipt type

To add logic for the new receipt type, implement **GetCustomReceiptsRequest** in CRT.

```C#
protected override GetReceiptResponse Process(GetCustomReceiptsRequest request)
{
    Collection<Receipt> result = new Collection<Receipt>();
        // 2. Now we can handle any additional receipt here.
    switch (request.ReceiptRetrievalCriteria.ReceiptType)
    {
        // An example of getting custom receipts.
        case ReceiptType.CustomReceipt1:
            {
                IEnumerable<Receipt> customReceipts = this.GetCustomReceipts(salesOrder, request.ReceiptRetrievalCriteria);
                    result.AddRange(customReceipts);
            }
            break;
        default:
            // Add more logic to handle more types of custom receipt types.
            break;
    }
    return new GetReceiptResponse(new ReadOnlyCollection<Receipt>(result));
}
```

The full sample code is available in the RetailSDK\\SampleExtensions\\CommerceRuntime\\Extensions.ReceiptsSamplefolder folder.

> [!NOTE]
> You should call the printing of the custom receipt type from the client. For more information, see [Printing custom receipt from POS](../pos-trigger-printing.md).

### Best practice

Avoid making database calls for each custom receipt field. Instead, use extension properties that you previously set on entities. Any logic can call custom receipt types (per sales line, one time per some condition). See the sample for a more complete scenario.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
