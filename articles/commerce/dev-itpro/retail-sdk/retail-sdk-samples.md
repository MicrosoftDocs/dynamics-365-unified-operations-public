---
# required metadata

title: Extend Commerce Store receipts
description: This topic describes how to extend Commerce store receipts.
author: mugunthanm
ms.date: 03/02/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: tfehr
# ms.tgt_pltfrm: 
ms.custom: 266164
ms.assetid: d24470fd-07ad-4c3f-b23a-3f6c1401edc6
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 2016-08-30
ms.dyn365.ops.version: Platform update 2

---

# Extend Commerce Store receipts

[!include [banner](../../includes/banner.md)]

This topic describes how to extend Commerce store receipts. Receipts can have two types of extensions:

 - **Custom fields** - Adds new receipt fields to the existing receipts.
 - **Custom receipt types** - Creates new receipts for custom scenarios.

## Custom fields

**Scenario:** Fabrikam wants to print a special receipt whenever products that have a warranty are sold. Sales receipts should include the warranty expiration date, the warranty ID, and other information. Here are the business requirements:

- Print special receipts.
- Print additional warranty information on sale receipts.

The following steps shows the HQ configuration and CRT code changes for the custom fields.

## Configure Headquarters for custom fields

At the headquarters (HQ), create two custom receipt fields: **EXPIRATIONDATE** for the warranty expiration date and **WARRANTYID** for the warranty ID. Add these fields to the receipt format layout.

1. Sign in to HQ.
2. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Language text**.
3. On the **POS** tab, select **Add** to add a new POS language text.

    The text that appears in the **Receipt** panel can be localized. Therefore, you can create multiple texts in different languages for the same text ID. Here is an example.

    | Language ID | Text ID | Text   |
    |-------------|---------|--------|
    | en-US       | 1       | WARRANTYID |
    | en-UK       | 1       | WARRANTYID   |

4. On the Action Pane, select **Save** to save your changes.
5. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Custom fields**.
6. On the Action Pane, select **New** to add a new custom field, and specify the following information: 

    1. In the **Name** field, enter the name of the custom field.
    2. In the **Type** field, select **Receipt**.
    3. In the **Caption text ID** field, specify the text ID that you used in step 3.

    Here is an example.

    | Name   | Type        | Caption text ID |
    |--------|-------------|-----------------|
    | WARRANTYID | Receipt | 1               |


7. On the Action Pane, select **Save** to save your changes.
8. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS \> Receipt formats**.
9. Select an existing or create a new receipt format and then select **Designer** on the Action Pane.
10. If you're prompted to confirm that you want to open the application, select **Open**, and then follow the installation instructions.
11. After the designer is installed, you're asked for Azure Active Directory (Azure AD) credentials. Enter the information to start the designer.
12. In the designer, drag and drop the **Custom** field from the left pane to the receipt designer.

> [!NOTE]
> The Custom fields are legal-entity specific, which means that the screen layout designer fetches the custom fields that are specific to the legal entity (Company) configured for the user signed in to **System Administration > Users**. If you configured custom fields for the different legal entities, then screen layout designer may not show those values.

14. Save the changes.
15. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**.
16. Select the **Channel configuration** (**1070**) job, and then select **Run now**.

## Sample code to implement Custom fields

To add the custom fields to the sales receipts or any receipt format, implement **GetSalesTransactionCustomReceiptFieldServiceRequest** and the business logic for the custom fields in CRT, as shown in the following code. For more information, see [Commerce runtime (CRT) extensibility](../commerce-runtime-extensibility.md).

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

### Custom receipt type configuration in HQ

1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS \> Receipt formats**.
2. Create new Receipt format and then select the **Receipt type** and choose one of the CustomReceiptType(1...20).
3. Save the changes.
4. Select **Designer** on the Action Pane.
5. If you're prompted to confirm that you want to open the application, select **Open**, and then follow the installation instructions.
6. After the designer is installed, you're asked for Azure Active Directory (Azure AD) credentials. Enter the information to start the designer.
7. In the designer, drag and drop the required receipt fields from the left pane to the receipt designer.
8. Save the changes.
9. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**.
10. Select the **Channel configuration** (**1070**) job, and then select **Run now**.

### Sample code to implement Custom receipt type

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

Avoid making database calls for each custom receipt field. Instead, use extension properties that were previously set on entities. Custom receipt types can be called by any logic (per sales line, one time per some condition). See the sample for a more complete scenario.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]