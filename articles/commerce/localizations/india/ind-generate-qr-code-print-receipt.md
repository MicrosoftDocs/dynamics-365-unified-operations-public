---
title: Generate QR codes and print them on receipts for India
description: This article explains how to generate Unified Payments Interface (UPI) Quick Response (QR) codes and print them on receipts for India.
author: ritakimani
ms.date: 07/29/2024
ms.topic: how-to
ms.custom: 
  - bap-template
ms.reviewer: josaw
ms.search.region: India
ms.author: ritakimani

---
# Generate QR codes and print them on receipts for India

[!include [banner](../../../finance/includes/banner.md)]

This article provides customization guidelines and explains how to generate Unified Payments Interface (UPI) Quick Response (QR) codes and print them on receipts for India.

## Prerequisites

Functionality for generating QR codes in the Commerce runtime (CRT) was introduced in Microsoft Dynamics 365 Commerce version 10.0.13. Therefore, the information in this article is valid only for version 10.0.13 and later.

Commerce versions 10.0.17 and later support printing QR codes on receipts using Retail Hardware Station. In versions 10.0.16 and earlier, QR codes can only be printed from Modern POS (MPOS).

## Data schema changes

Because invoice printing isn't supported in Dynamics 365 Commerce, there are no UPI-related fields in Point of sale (POS). Therefore, the fields should be added in the scope of code customization. We recommend that you extend the RetailStoreTenderTypeTable table by adding two string fields: **UPIId** and **UPIName**. As part of this customization, you should extend the **RetailStoreTenderTypeTable** form to edit the fields in the user interface (UI). You should also extend the channel data schema and download jobs. For more information, see [Channel database extensions](../../dev-itpro/channel-db-extensions.md).

## Set up receipts in Commerce headquarters

1. Create a new language text that will be used for a new custom receipt field for a QR code:

    1. Go to **Retail and Commerce** > **Retail and commerce IT** > **Channel setup** > **POS profiles** > **Language text**.
    2. On the **POS** tab, on the **POS language text** FastTab, select **Add** to create a language text.
    3. In the **Language ID** field, specify the language of the new language text (for example, **en-us** for US English).
    4. In the **Text ID** field, enter the identifier of the new language text.
    5. In the **Text** field, enter the new language text (for example, **Tax invoice QR code**).

       ![Creating a language text for a QR code receipt field.](../media/language-text-page.png)

2.  Create a new custom receipt field for a QR code:

    1. Go to **Retail and Commerce** > **Retail and commerce IT** > **Channel setup** > **POS profiles** > **Custom field**.
    2. On the Action Pane, select **New** to add a field.
    3. In the **Name** field, enter a name for the new field (for example, **TAXINVOICE_QR**).
    4. In the **Type** field, select **Receipt**.
    5. In the **Caption text ID** field, enter the **Text ID** value from the language text that you created earlier.

        ![Creating a receipt custom field for a QR code.](../media/custom-fields.png)

3.  Add a custom field for a QR code to a receipt:

    1. Go to **Retail and Commerce** > **Retail and commerce IT** > **Channel setup** > **POS** > **Receipt formats**.
    2. Select the receipt to add a QR code to.
    3. On the Action Pane, select **Designer**.
    4. Download the receipt designer, run it, and sign in.
    5. Add a custom field to the receipt header or footer.

4. Sync the changes with the channel database:

    1. Go to **Retail and Commerce** > **Retail and commerce IT** > **Distribution schedule**.
    2. Run jobs **1070** and **1090**.

## Create a CRT extension to support printing QR codes

To support the new custom receipt field for a QR code, you must create a CRT extension that will create a URL string and generate a QR code for it. For an example that shows how to add a custom field to a receipt, see [Extend Commerce Store receipts](../../dev-itpro/retail-sdk/retail-sdk-samples.md).

Follow these steps to handle the new custom receipt field for a QR code.

1. Install the Retail software development kit (SDK). For more information, see [Retail software development kit (SDK)](../../dev-itpro/retail-sdk/retail-sdk-overview.md).
2.  In the Retail SDK, create a C\# project.
3.  In the new C\# project, add references to the following packages per Commerce release:

# [Commerce 10.0.24 and before](#tab/commerce-10-0-24)

```C#
- Microsoft.Dynamics.Commerce.Runtime.DataModel.India
- Microsoft.Dynamics.Commerce.Runtime.DataServices
- Microsoft.Dynamics.Commerce.Runtime.ElectronicReporting
- Microsoft.Dynamics.Commerce.Runtime.GenericTaxEngine
- Microsoft.Dynamics.Commerce.Runtime.Services.Messages
```

# [Commerce 10.0.25](#tab/commerce-10-0-25)

```C#
- Microsoft.Dynamics.Commerce.Runtime.ElectronicReporting
- Microsoft.Dynamics.Commerce.Runtime.Services.Messages
- Microsoft.Dynamics.Commerce.Runtime.Localization.Data.Services.Messages
```

# [Commerce 10.0.26 and later](#tab/commerce-10-0-26)

```C#
- Microsoft.Dynamics.Commerce.Runtime.Services.Messages
- Microsoft.Dynamics.Commerce.Runtime.Localization.Data.Services.Messages
- Microsoft.Dynamics.Commerce.Runtime.Localization.Services.Messages
```
    
---

4. Create a class to handle. 

    ```C#
    public class GetSalesTransactionCustomReceiptFieldService : IRequestHandlerAsync, ICountryRegionAware.
    {
        // Add code here.
    }
    ```
       
5. Implement a handler method that will handle the new custom receipt field and return a QR code as a string.

    ```C#
    /// <summary>
    /// Gets the custom receipt field value for sales receipt.
    /// </summary>
    /// <param name="request>The service request to get custom receipt field value.</param>
    /// <returns>The value of custom receipt field.</returns>
    private async Task<Response>
    GetCustomReceiptFieldForSalesTransactionReceiptsAsync(GetSalesTransactionCustomReceiptFieldServiceRequest
    request)
    {
      ThrowIf.Null(request.SalesOrder, "sales order");
      string receiptFieldName = request.CustomReceiptField;
      string receiptFieldValue = string.Empty;
      switch (receiptFieldName)
      {
          case "TAXINVOICE_QR":
            receiptFieldValue = await GetQRCode(request).ConfigureAwait(false);
            break;
          default:
            return new NotHandledResponse();
      }
      return new GetCustomReceiptFieldServiceResponse(receiptFieldValue);
    }
    ```

    The handler should include the following steps.

    1. Generate UPI link based on the sales order (**SalesOrder**) that is passed as the request parameter.
    2. Run **EncodeQrCodeServiceRequest** to generate a QR code. (**EncodeQrCodeServiceRequest** is part of the **Microsoft.Dynamics.Commerce.Runtime.ElectronicReporting** package.)
    3. Wrap the QR code string that is returned in a `<>` tag.

        ```C#
        var qrCodeRequest = new
            EncodeQrCodeServiceRequest(stringBuilder.ToString())
            {
              Width = 150, // Replace with desired QR code width
              Height = 150 // Replace with desired QR code width
            };

            EncodeQrCodeServiceResponse qrCodeDataResponse = await
            request.RequestContext.ExecuteAsync<EncodeQrCodeServiceResponse>(qrCodeRequest).ConfigureAwait(false);
            receiptFieldValue = $"<I:{qrCodeDataResponse.QRcode}>";
            return receiptFieldValue;
        ```  

6. Add the required extensions to **CommerceRuntime.Ext.config**. Here, **Contoso.Commerce.Runtime.ReceiptsIndia** is the name of the new extension for printing the QR code assembly.

    ```xml 
    <commerceRuntimeExtensions>
          <composition>
            <!--
            Register your own assemblies or types here.
            The following example registers MyNewCrtService (and all its request handlers). 
            Any other services are not being overridden:
            <add source="type" value="Contoso.Commerce.Runtime.MyNewCrtService, Contoso.Commerce.Runtime.Services" />
            >add source="assembly" value="Contoso.Commerce.Runtime.Services" />
            -->
           <add source="assembly" value="Contoso.Commerce.Runtime.ReceiptsIndia" />
           <add source="assembly" 
       value="Microsoft.Dynamics.Commerce.Runtime.ElectronicReporting" />
           <add source="assembly" 
       value="Microsoft.Dynamics.Commerce.Runtime.GenericTaxEngine" />
          </composition>
       </commerceRuntimeExtensions>
    ```
   
## Printing QR code images on OPOS printers

When using an OPOS printer, you may need to convert the QR code image from the *png* format to the *bmp* format. Below is an example of this conversion.

   ```C#
    ...
        var qrCodeRequest = new
            EncodeQrCodeServiceRequest(stringBuilder.ToString())
            {
              Width = 150, // Replace with desired QR code width
              Height = 150 // Replace with desired QR code width
            };

            EncodeQrCodeServiceResponse qrCodeDataResponse = await
            request.RequestContext.ExecuteAsync<EncodeQrCodeServiceResponse>(qrCodeRequest).ConfigureAwait(false);

            string qrCode = ConvertImagePNGToBMP(qrCodeDataResponse.QRcode);
            receiptFieldValue = $"<I:{qrCode}>";
            return receiptFieldValue;
    ...
    /// <summary>
    /// Converts an image from "png" to "bmp".
    /// </summary>
    /// <param name="qrCode">Base64 represents the image to convert.</param>
    /// <returns>The image as base64.</returns>
    private static string ConvertImagePNGToBMP(string qrCode)
    {
        string convertedQRCode = qrCode;

        byte[] imageBytes = Convert.FromBase64String(qrCode);
        using (MemoryStream msFrom = new MemoryStream(imageBytes))
        {
            var image = Image.FromStream(msFrom);
            using (MemoryStream msTo = new MemoryStream())
            {
                image.Save(msTo, ImageFormat.Bmp);
                convertedQRCode = Convert.ToBase64String(msTo.ToArray());
            }
        }

        return convertedQRCode;
    }
   ```

## Samples of a CRT extension class for printing QR codes

The following code blocks grouped by Commerce release provide samples of CRT extension classes for printing QR codes.

# [Commerce 10.0.24 and before](#tab/commerce-10-0-24)

```C#
namespace Contoso
{
    namespace Commerce.Runtime.ReceiptsIndia
    {
        using System;
        using System.Collections.Generic;
        using System.Globalization;
        using System.Linq;
        using System.Text;
        using System.Threading.Tasks;
        using Microsoft.Dynamics.Commerce.Runtime;
        using Microsoft.Dynamics.Commerce.Runtime.DataModel;
        using Microsoft.Dynamics.Commerce.Runtime.DataServices.Messages;
        using Microsoft.Dynamics.Commerce.Runtime.Messages;
        using Microsoft.Dynamics.Commerce.Runtime.Services.Messages;

        /// <summary>
        /// The extended service to get custom sales receipt field.
        /// </summary>
        public class GetSalesTransactionCustomReceiptFieldService : IRequestHandlerAsync, ICountryRegionAware
        {
            /// <summary>
            /// Gets the supported request types.
            /// </summary>  
            public IEnumerable<Type> SupportedRequestTypes
            {
              get
                {
                    return new[]
                    {
                        typeof(GetSalesTransactionCustomReceiptFieldServiceRequest),
                   };
                }
            }

            /// <summary>
            /// Gets a collection of companies supported by this request handler.
            /// </summary>
            public IEnumerable<string> SupportedCountryRegions
            {
                get
                {
                    return new[]
                    {
                        nameof(CountryRegionISOCode.IN),
                    };
                }
            }
            /// <summary>
            /// Executes the requests.
            /// </summary>
            /// <param name="request">The request parameter.</param>
            /// <returns>The GetReceiptServiceResponse that contains the formatted receipts.</returns>
            public async Task<Response> Execute(Request request)
            {
                ThrowIf.Null(request, nameof(request));
                Type requestedType = request.GetType();
                if (requestedType == typeof(GetSalesTransactionCustomReceiptFieldServiceRequest))
                {
                    return await
           this.GetCustomReceiptFieldForSalesTransactionReceiptsAsync((GetSalesTransactionCustomReceiptFieldServiceRequest)request).ConfigureAwait(false);
                }
                throw new NotSupportedException(string.Format("Request '{0}' is not supported.", request.GetType()));
                }
                /// <summary>
                /// Gets the custom receipt field value for sales receipt.
                /// </summary>
                /// <param name="request">The service request to get custom receipt field value.</param>
                /// <returns>The value of custom receipt field.<returns>
                private async Task<Response>
           GetCustomReceiptFieldForSalesTransactionReceiptsAsync(GetSalesTransactionCustomReceiptFieldServiceRequest request)
                {
                    ThrowIf.Null(request.SalesOrder, 
           $"{nameof(request)},{nameof(request.SalesOrder)}");
                    string receiptFieldName = request.CustomReceiptField;
                    string receiptFieldValue = string.Empty;
                    switch (receiptFieldName)
                    {
                        case "TAXINVOICE_QR":
                            receiptFieldValue = await 
           GetQRCode(request).ConfigureAwait(false);
                                   break;
                              default:
                                   return new NotHandledResponse();
                    }

                    return new GetCustomReceiptFieldServiceResponse(receiptFieldValue);
                }
                /// <summary>
                /// Gets the QR code for the receipt.
                /// </summary>
                /// <param name="request">The service request to get customreceipt field value.</param>
                /// <returns>QR code custom field value.</returns>
                private static async Task<string>
        GetQRCode(GetSalesTransactionCustomReceiptFieldServiceRequest request)
                {
                    var salesOrder = request.SalesOrder;
                    string receiptFieldValue = string.Empty;
                    bool isB2C = await IsB2CTransactionAsync(request.RequestContext, salesOrder).ConfigureAwait(false);
                    if (isB2C)
                    {
                        string gstNumber = await GetStoreGSTIN(request.RequestContext).ConfigureAwait(false);
                        var paymentInfo = await GetPaymentUPIInfo(request.RequestContext, salesOrder).ConfigureAwait(false);
                        string totalAmount = FormatAmount(salesOrder.TotalAmount);
                        string igstAmt = FormatAmount(GetTaxComponentAmount(salesOrder,
                        "IGST"));
                        string cgstAmt = FormatAmount(GetTaxComponentAmount(salesOrder,
                        "CGST"));
                        string sgstAmt = FormatAmount(GetTaxComponentAmount(salesOrder,
                        "SGST"));
                        string cessAmt = FormatAmount(GetTaxComponentAmount(salesOrder,
                        "CESS"));
                        StringBuilder stringBuilder = new
               StringBuilder($"upi://pay?cu={salesOrder.CurrencyCode}");
                        stringBuilder.Append($"&am={totalAmount}");
                        stringBuilder.Append($"&pa={paymentInfo.Item1}");
                        stringBuilder.Append($"&pn={paymentInfo.Item2}");
                        stringBuilder.Append($"&tr={salesOrder.ReceiptId}");
               stringBuilder.Append($"&dt={salesOrder.TransactionDateTime.ToString("dd/MM/yyyy")}");                    
                        stringBuilder.Append($"&no={gstNumber}");
                        stringBuilder.Append($"&IgstAmt = {igstAmt}");
                        stringBuilder.Append($"&CgstAmt = {cgstAmt}");
                        stringBuilder.Append($"&SgstAmt = {sgstAmt}");
                        stringBuilder.Append($"&CesAmt = {cessAmt}");
                        var qrCodeRequest = new
               EncodeQrCodeServiceRequest(stringBuilder.ToString())
                        {
                            Width = 150, // Replace with desired QR code width
                            Height = 150 // Replace with desired QR code width
                        };
               EncodeQrCodeServiceResponse qrCodeDataResponse = await
               request.RequestContext.ExecuteAsync<EncodeQrCodeServiceResponse>(qrCodeRequest).ConfigureAwait(false);
                        receiptFieldValue = $"<I:{qrCodeDataResponse.QRcode}>";
                    }
                    return receiptFieldValue;
                }

                /// <summary>
                /// Gets store GSTIN.
                /// </summary>
                /// <param name="requestContext">Request context.</param>
                /// <returns>Store GSTIN.</returns>
                private static async Task<string> GetStoreGSTIN(RequestContext
                requestContext)
                {
                    var dataRequest = new GetReceiptHeaderGteTaxInfoIndiaDataRequest
                    {
                        QueryResultSettings = QueryResultSettings.SingleRecord,
                    };
                    var headerTaxInformation = await
          requestContext.ExecuteAsync<SingleEntityDataServiceResponse<ReceiptHeaderGteTaxInfoIndia>>(dataRequest).ConfigureAwait(false);
                    return headerTaxInformation.Entity?.GstRegistrationNumber;
                }

                /// <summary>
                /// Gets payment UPI info for the sales order.
                /// </summary>
                /// <param name="requestContext">Request context.</param>
                /// <param name="salesOrder">Sales order.</param>
                /// <returns>Payment info.</returns>
                private static async Task<Tuple<string, string>>
          GetPaymentUPIInfo(RequestContext requestContext, SalesOrder salesOrder)
                {
                    var channelTenderDataRequest = new
          GetChannelTenderTypesDataRequest(requestContext.GetPrincipal().ChannelId,
          QueryResultSettings.AllRecords);
                    var channelTenderTypes = (await
          requestContext.Runtime.ExecuteAsync<EntityDataServiceResponse<TenderType>>(channelTenderDataRequest,
          requestContext).ConfigureAwait(false)).PagedEntityCollection.Results;
                    string upiId = string.Empty;
                    string upiName = string.Empty;
                    int count = salesOrder.ActiveTenderLines.Count;
                    foreach (var tenderLine in salesOrder.ActiveTenderLines)
                    {
                        TenderType tenderType = channelTenderTypes.Where(type =>
                    type.TenderTypeId == tenderLine.TenderTypeId).SingleOrDefault();
                        if (tenderType == null)
                        {
                            continue;
                        }
                        if (!string.IsNullOrEmpty(upiId))
                        {
                            upiId += ",";
                        }
                        if (!string.IsNullOrEmpty(upiName))
                        {
                            upiName += ",";
                        }
                        upiId += tenderType.TenderTypeId; // Here should be customized field UPIId
                        upiName += tenderType.Name; // Here should be customized field UPIName
                        if (count > 1)
                        {
                            string amount = FormatAmount(tenderLine.Amount);
                            upiId += $":{amount}";
                            upiName += $":{amount}";
                        }
                    }
                    return new Tuple<string, string>(upiId, upiName);
                }

                /// <summary>
                /// Gets tax component amount.
                /// </summary>
                /// <param name="salesOrder">Sales order.</param>
                /// <param name="taxComponent">Tax component.</param>
                /// <returns>Tax component amount.</returns>
                private static decimal GetTaxComponentAmount(SalesOrder salesOrder, string taxComponent)
                {
                    decimal taxAmount = 0m;
                    IEnumerable<TaxLineGTE> taxLineGte = 
                salesOrder.ActiveSalesLines.SelectMany(x => x.TaxLines).OfType<TaxLineGTE>();
                    var groups = taxLineGte.GroupBy(x => new { x.TaxComponent }).OrderBy(x =>
                x.Key.TaxComponent);
                    var group = groups.Where(g => string.Equals(g.Key.TaxComponent, 
                taxComponent, StringComparison.InvariantCultureIgnoreCase)).FirstOrDefault();
                    if (group != null)
                    {
                        taxAmount = group.Sum(l => l.Amount);
                    }
                    return taxAmount;
                }

                /// <summary>
                /// Gets the store customer account number based on store type.
                /// </summary>
                /// <returns>The store customer account number.</returns>
                internal static string
            GetStoreCustomerAccountNumberFromChannelProperties(RequestContext requestContext)
                {
                    if (requestContext.GetChannelConfiguration().IsOnlineStore())
                    {
                        if (requestContext.GetPrincipal().IsCustomer)
                        {
                            return requestContext.GetPrincipal().UserId;
                        }
                    }
                    return requestContext.GetChannel().DefaultCustomerAccount;
                }

                ///<summary>
                /// Defines whether the customer is store default customer.
                /// </summary>
                /// <param name="requestContext">Request context.</param>
                /// <param name="customerId">Customer id.</param>
                /// <returns>rue if the customer is store default customer; false otherwise.</returns>
                private static bool IsStoreCustomer(RequestContext requestContext, string customerId)
                {
                    return string.IsNullOrEmpty(customerId)
                        || string.Equals(customerId,
            GetStoreCustomerAccountNumberFromChannelProperties(requestContext),
            StringComparison.InvariantCultureIgnoreCase);
                }
                /// <summary>
                /// Defines whether the transaction is B2C.
                /// </summary>
                /// <param name="requestContext">Request context.</param>
                /// <param name="salesOrder">Sales order.</param>
                /// <returns>True if the transaction is B2C; false otherwise.</returns>
                private static async Task<bool> IsB2CTransactionAsync(RequestContext requestContext, SalesOrder salesOrder)
                {
                    if (IsStoreCustomer(requestContext, salesOrder.CustomerId))
                    {
                        return true;
                    }
                    var customer = await GetCustomerAsync(requestContext, salesOrder.CustomerId).ConfigureAwait(false);
                    if (customer == null)
                    {
                        return true;
                    }
                    var address = customer.GetPrimaryAddress();
                    if (address == null)
                    {
                        return true;
                    }
                    GetPrimaryAddressTaxInformationDataRequest
            getPrimaryAddressTaxInformationDataRequest = new
            GetPrimaryAddressTaxInformationDataRequest(address.LogisticsLocationRecordId);
                    AddressTaxInformationIndia addressTaxInformationIndia = (await
            requestContext.Runtime.ExecuteAsync
            <SingleEntityDataServiceResponse<AddressTaxInformationIndia>>(getPrimaryAddressTaxInformationDataRequest,
            requestContext)
                        .ConfigureAwait(false)).Entity;
                    if (addressTaxInformationIndia == null ||
            addressTaxInformationIndia.GstinRegistrationNumber == null
                            ||
            string.IsNullOrEmpty(addressTaxInformationIndia.GstinRegistrationNumber.RegistrationNumber))
                    {
                        return true;
                    }
                    return false;
                }

                /// <summary>
                /// Gets customer by customer identifier.
                /// </summary>
                /// <param name="customerId">Customer identifier.</param>
                /// <returns>Customer object.</returns>
                private static async Task<Customer> GetCustomerAsync(RequestContext requestContext, string customerId)
                {
                    Customer customer = null;
                    if (!string.IsNullOrWhiteSpace(customerId))
                    {
                        var getCustomerDataRequest = new GetCustomerDataRequest(customerId);
                        SingleEntityDataServiceResponse<Customer> getCustomerDataResponse = await
                requestContext.ExecuteAsync<SingleEntityDataServiceResponse<Customer>>(getCustomerDataRequest).ConfigureAwait(false);
                        customer = getCustomerDataResponse.Entity;
                    }
                    return customer;
                }

                /// <summary>
                /// Formats amount.
                /// </summary>
                /// <param name="amount">Amount to format.</param>
                /// <returns>Formatted amount.</returns>
                private static string FormatAmount(decimal amount)
                {
                    return amount.ToString("0.00", CultureInfo.InvariantCulture);
                }
            }
        }
    }
```     

# [Commerce 10.0.25](#tab/commerce-10-0-25)

```C#
namespace Contoso
{
    namespace Commerce.Runtime.ReceiptsIndia
    {
        using System;
        using System.Collections.Generic;
        using System.Globalization;
        using System.Linq;
        using System.Text;
        using System.Threading.Tasks;
        using Microsoft.Dynamics.Commerce.Runtime;
        using Microsoft.Dynamics.Commerce.Runtime.DataModel;
        using Microsoft.Dynamics.Commerce.Runtime.DataServices.Messages;
        using Microsoft.Dynamics.Commerce.Runtime.Localization.Data.Services.Messages.India;
        using Microsoft.Dynamics.Commerce.Runtime.Localization.Entities.India;
        using Microsoft.Dynamics.Commerce.Runtime.Messages;
        using Microsoft.Dynamics.Commerce.Runtime.Services.Messages;

        /// <summary>
        /// The extended service to get custom sales receipt field.
        /// </summary>
        public class GetSalesTransactionCustomReceiptFieldService : IRequestHandlerAsync, ICountryRegionAware
        {
            /// <summary>
            /// Gets the supported request types.
            /// </summary>  
            public IEnumerable<Type> SupportedRequestTypes
            {
                get
                {
                    return new[]
                    {
                       typeof(GetSalesTransactionCustomReceiptFieldServiceRequest),
                    };
                }
            }

            /// <summary>
            /// Gets a collection of companies supported by this request handler.
            /// </summary>
            public IEnumerable<string> SupportedCountryRegions
            {
                get
                {
                    return new[]
                    {
                       nameof(CountryRegionISOCode.IN),
                    };
                }
            }

            /// <summary>
            /// Executes the requests.
            /// </summary>
            /// <param name="request">The request parameter.</param>
            /// <returns>The GetReceiptServiceResponse that contains the formatted receipts.</returns>
            public async Task<Response> Execute(Request request)
            {
                ThrowIf.Null(request, nameof(request));
                Type requestedType = request.GetType();
                if (requestedType == typeof(GetSalesTransactionCustomReceiptFieldServiceRequest))
                {
                    return await this.GetCustomReceiptFieldForSalesTransactionReceiptsAsync((GetSalesTransactionCustomReceiptFieldServiceRequest)request).ConfigureAwait(false);
                }
                throw new NotSupportedException(string.Format("Request '{0}' is not supported.", request.GetType()));
            }

            /// <summary>
            /// Gets the custom receipt field value for sales receipt.
            /// </summary>
            /// <param name="request">The service request to get custom receipt field value.</param>
            /// <returns>The value of custom receipt field.<returns>
            private async Task<Response> GetCustomReceiptFieldForSalesTransactionReceiptsAsync(GetSalesTransactionCustomReceiptFieldServiceRequest request)
            {
                ThrowIf.Null(request.SalesOrder, $"{nameof(request)},{nameof(request.SalesOrder)}");
                string receiptFieldName = request.CustomReceiptField;
                string receiptFieldValue = string.Empty;
                switch (receiptFieldName)
                {
                    case "TAXINVOICE_QR":
                        receiptFieldValue = await GetQRCode(request).ConfigureAwait(false);
                        break;
                    default:
                        return new NotHandledResponse();
                }

                return new GetCustomReceiptFieldServiceResponse(receiptFieldValue);
            }

            /// <summary>
            /// Gets the QR code for the receipt.
            /// </summary>
            /// <param name="request">The service request to get customreceipt field value.</param>
            /// <returns>QR code custom field value.</returns>
            private static async Task<string> GetQRCode(GetSalesTransactionCustomReceiptFieldServiceRequest request)
            {
                var salesOrder = request.SalesOrder;
                string receiptFieldValue = string.Empty;
                bool isB2C = await IsB2CTransactionAsync(request.RequestContext, salesOrder).ConfigureAwait(false);
                if (isB2C)
                {
                    string gstNumber = await GetStoreGSTIN(request.RequestContext).ConfigureAwait(false);
                    var paymentInfo = await GetPaymentUPIInfo(request.RequestContext, salesOrder).ConfigureAwait(false);
                    string totalAmount = FormatAmount(salesOrder.TotalAmount);
                    string igstAmt = FormatAmount(GetTaxComponentAmount(salesOrder,
                    "IGST"));
                    string cgstAmt = FormatAmount(GetTaxComponentAmount(salesOrder,
                    "CGST"));
                    string sgstAmt = FormatAmount(GetTaxComponentAmount(salesOrder,
                    "SGST"));
                    string cessAmt = FormatAmount(GetTaxComponentAmount(salesOrder,
                    "CESS"));
                    StringBuilder stringBuilder = new StringBuilder($"upi://pay?cu={salesOrder.CurrencyCode}");
                    stringBuilder.Append($"&am={totalAmount}");
                    stringBuilder.Append($"&pa={paymentInfo.Item1}");
                    stringBuilder.Append($"&pn={paymentInfo.Item2}");
                    stringBuilder.Append($"&tr={salesOrder.ReceiptId}");
                    stringBuilder.Append($"&dt={salesOrder.TransactionDateTime.ToString("dd/MM/yyyy")}");
                    stringBuilder.Append($"&no={gstNumber}");
                    stringBuilder.Append($"&IgstAmt = {igstAmt}");
                    stringBuilder.Append($"&CgstAmt = {cgstAmt}");
                    stringBuilder.Append($"&SgstAmt = {sgstAmt}");
                    stringBuilder.Append($"&CesAmt = {cessAmt}");
                    var qrCodeRequest = new EncodeQrCodeServiceRequest(stringBuilder.ToString())
                    {
                        Width = 150, // Replace with desired QR code width
                        Height = 150 // Replace with desired QR code width
                    };
                    EncodeQrCodeServiceResponse qrCodeDataResponse = await
                    request.RequestContext.ExecuteAsync<EncodeQrCodeServiceResponse>(qrCodeRequest).ConfigureAwait(false);
                    receiptFieldValue = $"<L:{qrCodeDataResponse.QRcode}>";
                }
                return receiptFieldValue;
            }

            /// <summary>
            /// Gets store GSTIN.
            /// </summary>
            /// <param name="requestContext">Request context.</param>
            /// <returns>Store GSTIN.</returns>
            private static async Task<string> GetStoreGSTIN(RequestContext requestContext)
            {
                var dataRequest = new GetReceiptHeaderTaxInformationDataRequest
                {
                    QueryResultSettings = QueryResultSettings.SingleRecord,
                };
                var headerTaxInformation = await requestContext.ExecuteAsync<SingleEntityDataServiceResponse<ReceiptHeaderTaxInformation>>(dataRequest).ConfigureAwait(false);
                return headerTaxInformation.Entity?.GstRegistrationNumber;
            }

            /// <summary>
            /// Gets payment UPI info for the sales order.
            /// </summary>
            /// <param name="requestContext">Request context.</param>
            /// <param name="salesOrder">Sales order.</param>
            /// <returns>Payment info.</returns>
            private static async Task<Tuple<string, string>> GetPaymentUPIInfo(RequestContext requestContext, SalesOrder salesOrder)
            {
                var channelTenderDataRequest = new GetChannelTenderTypesDataRequest(requestContext.GetPrincipal().ChannelId, QueryResultSettings.AllRecords);
                var channelTenderTypes = (await requestContext.Runtime.ExecuteAsync<EntityDataServiceResponse<TenderType>>(channelTenderDataRequest, requestContext).ConfigureAwait(false)).PagedEntityCollection.Results;
                string upiId = string.Empty;
                string upiName = string.Empty;
                int count = salesOrder.ActiveTenderLines.Count;
                foreach (var tenderLine in salesOrder.ActiveTenderLines)
                {
                    TenderType tenderType = channelTenderTypes.Where(type => type.TenderTypeId == tenderLine.TenderTypeId).SingleOrDefault();
                    if (tenderType == null)
                    {
                        continue;
                    }
                    if (!string.IsNullOrEmpty(upiId))
                    {
                        upiId += ",";
                    }
                    if (!string.IsNullOrEmpty(upiName))
                    {
                        upiName += ",";
                    }
                    upiId += tenderType.TenderTypeId; // Here should be customized field UPIId
                    upiName += tenderType.Name; // Here should be customized field UPIName
                    if (count > 1)
                    {
                        string amount = FormatAmount(tenderLine.Amount);
                        upiId += $":{amount}";
                        upiName += $":{amount}";
                    }
                }
                return new Tuple<string, string>(upiId, upiName);
            }

            /// <summary>
            /// Gets tax component amount.
            /// </summary>
            /// <param name="salesOrder">Sales order.</param>
            /// <param name="taxComponent">Tax component.</param>
            /// <returns>Tax component amount.</returns>
            private static decimal GetTaxComponentAmount(SalesOrder salesOrder, string taxComponent)
            {
                decimal taxAmount = 0m;
                IEnumerable<TaxLineGTE> taxLineGte = salesOrder.ActiveSalesLines.SelectMany(x => x.TaxLines).OfType<TaxLineGTE>();
                var groups = taxLineGte.GroupBy(x => new { x.TaxComponent }).OrderBy(x => x.Key.TaxComponent);
                var group = groups.Where(g => string.Equals(g.Key.TaxComponent, taxComponent, StringComparison.InvariantCultureIgnoreCase)).FirstOrDefault();
                if (group != null)
                {
                    taxAmount = group.Sum(l => l.Amount);
                }
                return taxAmount;
            }

            /// <summary>
            /// Gets the store customer account number based on store type.
            /// </summary>
            /// <returns>The store customer account number.</returns>
            internal static string GetStoreCustomerAccountNumberFromChannelProperties(RequestContext requestContext)
            {
                if (requestContext.GetChannelConfiguration().IsOnlineStore())
                {
                    if (requestContext.GetPrincipal().IsCustomer)
                    {
                        return requestContext.GetPrincipal().UserId;
                    }
                }
                return requestContext.GetChannel().DefaultCustomerAccount;
            }

            ///<summary>
            /// Defines whether the customer is store default customer.
            /// </summary>
            /// <param name="requestContext">Request context.</param>
            /// <param name="customerId">Customer id.</param>
            /// <returns>rue if the customer is store default customer; false otherwise.</returns>
            private static bool IsStoreCustomer(RequestContext requestContext, string customerId)
            {
                return string.IsNullOrEmpty(customerId)
                    || string.Equals(customerId, GetStoreCustomerAccountNumberFromChannelProperties(requestContext), StringComparison.InvariantCultureIgnoreCase);
            }

            /// <summary>
            /// Defines whether the transaction is B2C.
            /// </summary>
            /// <param name="requestContext">Request context.</param>
            /// <param name="salesOrder">Sales order.</param>
            /// <returns>True if the transaction is B2C; false otherwise.</returns>
            private static async Task<bool> IsB2CTransactionAsync(RequestContext requestContext, SalesOrder salesOrder)
            {
                if (IsStoreCustomer(requestContext, salesOrder.CustomerId))
                {
                    return true;
                }
                var customer = await GetCustomerAsync(requestContext, salesOrder.CustomerId).ConfigureAwait(false);
                if (customer == null)
                {
                    return true;
                }
                var address = customer.GetPrimaryAddress();
                if (address == null)
                {
                    return true;
                }
                GetPrimaryAddressTaxInformationDataRequest getPrimaryAddressTaxInformationDataRequest = new GetPrimaryAddressTaxInformationDataRequest(address.LogisticsLocationRecordId);
                AddressTaxInformationIndia addressTaxInformationIndia = (await requestContext.Runtime.ExecuteAsync<SingleEntityDataServiceResponse<AddressTaxInformationIndia>>(getPrimaryAddressTaxInformationDataRequest, requestContext).ConfigureAwait(false)).Entity;
                if (addressTaxInformationIndia == null
                    || addressTaxInformationIndia.GstinRegistrationNumber == null
                    || string.IsNullOrEmpty(addressTaxInformationIndia.GstinRegistrationNumber.RegistrationNumber))
                {
                    return true;
                }
                return false;
            }

            /// <summary>
            /// Gets customer by customer identifier.
            /// </summary>
            /// <param name="customerId">Customer identifier.</param>
            /// <returns>Customer object.</returns>
            private static async Task<Customer> GetCustomerAsync(RequestContext requestContext, string customerId)
            {
                Customer customer = null;
                if (!string.IsNullOrWhiteSpace(customerId))
                {
                    var getCustomerDataRequest = new GetCustomerDataRequest(customerId);
                    SingleEntityDataServiceResponse<Customer> getCustomerDataResponse = await requestContext.ExecuteAsync<SingleEntityDataServiceResponse<Customer>>(getCustomerDataRequest).ConfigureAwait(false);
                    customer = getCustomerDataResponse.Entity;
                }
                return customer;
            }

            /// <summary>
            /// Formats amount.
            /// </summary>
            /// <param name="amount">Amount to format.</param>
            /// <returns>Formatted amount.</returns>
            private static string FormatAmount(decimal amount)
            {
                return amount.ToString("0.00", CultureInfo.InvariantCulture);
            }
        }
    }
}
```   

# [Commerce 10.0.26 and later](#tab/commerce-10-0-26)

```C#
namespace Contoso
{
    namespace Commerce.Runtime.ReceiptsIndia
    {
        using System;
        using System.Collections.Generic;
        using System.Globalization;
        using System.Linq;
        using System.Text;
        using System.Threading.Tasks;
        using Microsoft.Dynamics.Commerce.Runtime;
        using Microsoft.Dynamics.Commerce.Runtime.DataModel;
        using Microsoft.Dynamics.Commerce.Runtime.DataServices.Messages;
        using Microsoft.Dynamics.Commerce.Runtime.Localization.Data.Services.Messages.India;
        using Microsoft.Dynamics.Commerce.Runtime.Localization.Entities.India;
        using Microsoft.Dynamics.Commerce.Runtime.Localization.Services.Messages;
        using Microsoft.Dynamics.Commerce.Runtime.Messages;
        using Microsoft.Dynamics.Commerce.Runtime.Services.Messages;

        /// <summary>
        /// The extended service to get custom sales receipt field.
        /// </summary>
        public class GetSalesTransactionCustomReceiptFieldService : IRequestHandlerAsync, ICountryRegionAware
        {
            /// <summary>
            /// Gets the supported request types.
            /// </summary>  
            public IEnumerable<Type> SupportedRequestTypes
            {
                get
                {
                    return new[]
                    {
                       typeof(GetSalesTransactionCustomReceiptFieldServiceRequest),
                    };
                }
            }

            /// <summary>
            /// Gets a collection of companies supported by this request handler.
            /// </summary>
            public IEnumerable<string> SupportedCountryRegions
            {
                get
                {
                    return new[]
                    {
                       nameof(CountryRegionISOCode.IN),
                    };
                }
            }

            /// <summary>
            /// Executes the requests.
            /// </summary>
            /// <param name="request">The request parameter.</param>
            /// <returns>The GetReceiptServiceResponse that contains the formatted receipts.</returns>
            public async Task<Response> Execute(Request request)
            {
                ThrowIf.Null(request, nameof(request));
                Type requestedType = request.GetType();
                if (requestedType == typeof(GetSalesTransactionCustomReceiptFieldServiceRequest))
                {
                    return await this.GetCustomReceiptFieldForSalesTransactionReceiptsAsync((GetSalesTransactionCustomReceiptFieldServiceRequest)request).ConfigureAwait(false);
                }
                throw new NotSupportedException(string.Format("Request '{0}' is not supported.", request.GetType()));
            }

            /// <summary>
            /// Gets the custom receipt field value for sales receipt.
            /// </summary>
            /// <param name="request">The service request to get custom receipt field value.</param>
            /// <returns>The value of custom receipt field.<returns>
            private async Task<Response> GetCustomReceiptFieldForSalesTransactionReceiptsAsync(GetSalesTransactionCustomReceiptFieldServiceRequest request)
            {
                ThrowIf.Null(request.SalesOrder, $"{nameof(request)},{nameof(request.SalesOrder)}");
                string receiptFieldName = request.CustomReceiptField;
                string receiptFieldValue = string.Empty;
                switch (receiptFieldName)
                {
                    case "TAXINVOICE_QR":
                        receiptFieldValue = await GetQRCode(request).ConfigureAwait(false);
                        break;
                    default:
                        return new NotHandledResponse();
                }

                return new GetCustomReceiptFieldServiceResponse(receiptFieldValue);
            }

            /// <summary>
            /// Gets the QR code for the receipt.
            /// </summary>
            /// <param name="request">The service request to get customreceipt field value.</param>
            /// <returns>QR code custom field value.</returns>
            private static async Task<string> GetQRCode(GetSalesTransactionCustomReceiptFieldServiceRequest request)
            {
                var salesOrder = request.SalesOrder;
                string receiptFieldValue = string.Empty;
                bool isB2C = await IsB2CTransactionAsync(request.RequestContext, salesOrder).ConfigureAwait(false);
                if (isB2C)
                {
                    string gstNumber = await GetStoreGSTIN(request.RequestContext).ConfigureAwait(false);
                    var paymentInfo = await GetPaymentUPIInfo(request.RequestContext, salesOrder).ConfigureAwait(false);
                    string totalAmount = FormatAmount(salesOrder.TotalAmount);
                    string igstAmt = FormatAmount(GetTaxComponentAmount(salesOrder,
                    "IGST"));
                    string cgstAmt = FormatAmount(GetTaxComponentAmount(salesOrder,
                    "CGST"));
                    string sgstAmt = FormatAmount(GetTaxComponentAmount(salesOrder,
                    "SGST"));
                    string cessAmt = FormatAmount(GetTaxComponentAmount(salesOrder,
                    "CESS"));
                    StringBuilder stringBuilder = new StringBuilder($"upi://pay?cu={salesOrder.CurrencyCode}");
                    stringBuilder.Append($"&am={totalAmount}");
                    stringBuilder.Append($"&pa={paymentInfo.Item1}");
                    stringBuilder.Append($"&pn={paymentInfo.Item2}");
                    stringBuilder.Append($"&tr={salesOrder.ReceiptId}");
                    stringBuilder.Append($"&dt={salesOrder.TransactionDateTime.ToString("dd/MM/yyyy")}");
                    stringBuilder.Append($"&no={gstNumber}");
                    stringBuilder.Append($"&IgstAmt = {igstAmt}");
                    stringBuilder.Append($"&CgstAmt = {cgstAmt}");
                    stringBuilder.Append($"&SgstAmt = {sgstAmt}");
                    stringBuilder.Append($"&CesAmt = {cessAmt}");
                    var qrCodeRequest = new EncodeQrCodeServiceRequest(stringBuilder.ToString())
                    {
                        Width = 150, // Replace with desired QR code width
                        Height = 150 // Replace with desired QR code width
                    };
                    EncodeQrCodeServiceResponse qrCodeDataResponse = await
                    request.RequestContext.ExecuteAsync<EncodeQrCodeServiceResponse>(qrCodeRequest).ConfigureAwait(false);
                    receiptFieldValue = $"<L:{qrCodeDataResponse.QRCode}>";
                }
                return receiptFieldValue;
            }

            /// <summary>
            /// Gets store GSTIN.
            /// </summary>
            /// <param name="requestContext">Request context.</param>
            /// <returns>Store GSTIN.</returns>
            private static async Task<string> GetStoreGSTIN(RequestContext requestContext)
            {
                var dataRequest = new GetReceiptHeaderTaxInformationDataRequest
                {
                    QueryResultSettings = QueryResultSettings.SingleRecord,
                };
                var headerTaxInformation = await requestContext.ExecuteAsync<SingleEntityDataServiceResponse<ReceiptHeaderTaxInformation>>(dataRequest).ConfigureAwait(false);
                return headerTaxInformation.Entity?.GstRegistrationNumber;
            }

            /// <summary>
            /// Gets payment UPI info for the sales order.
            /// </summary>
            /// <param name="requestContext">Request context.</param>
            /// <param name="salesOrder">Sales order.</param>
            /// <returns>Payment info.</returns>
            private static async Task<Tuple<string, string>> GetPaymentUPIInfo(RequestContext requestContext, SalesOrder salesOrder)
            {
                var channelTenderDataRequest = new GetChannelTenderTypesDataRequest(requestContext.GetPrincipal().ChannelId, QueryResultSettings.AllRecords);
                var channelTenderTypes = (await requestContext.Runtime.ExecuteAsync<EntityDataServiceResponse<TenderType>>(channelTenderDataRequest, requestContext).ConfigureAwait(false)).PagedEntityCollection.Results;
                string upiId = string.Empty;
                string upiName = string.Empty;
                int count = salesOrder.ActiveTenderLines.Count;
                foreach (var tenderLine in salesOrder.ActiveTenderLines)
                {
                    TenderType tenderType = channelTenderTypes.Where(type => type.TenderTypeId == tenderLine.TenderTypeId).SingleOrDefault();
                    if (tenderType == null)
                    {
                        continue;
                    }
                    if (!string.IsNullOrEmpty(upiId))
                    {
                        upiId += ",";
                    }
                    if (!string.IsNullOrEmpty(upiName))
                    {
                        upiName += ",";
                    }
                    upiId += tenderType.TenderTypeId; // Here should be customized field UPIId
                    upiName += tenderType.Name; // Here should be customized field UPIName
                    if (count > 1)
                    {
                        string amount = FormatAmount(tenderLine.Amount);
                        upiId += $":{amount}";
                        upiName += $":{amount}";
                    }
                }
                return new Tuple<string, string>(upiId, upiName);
            }

            /// <summary>
            /// Gets tax component amount.
            /// </summary>
            /// <param name="salesOrder">Sales order.</param>
            /// <param name="taxComponent">Tax component.</param>
            /// <returns>Tax component amount.</returns>
            private static decimal GetTaxComponentAmount(SalesOrder salesOrder, string taxComponent)
            {
                decimal taxAmount = 0m;
                IEnumerable<TaxLineGTE> taxLineGte = salesOrder.ActiveSalesLines.SelectMany(x => x.TaxLines).OfType<TaxLineGTE>();
                var groups = taxLineGte.GroupBy(x => new { x.TaxComponent }).OrderBy(x => x.Key.TaxComponent);
                var group = groups.Where(g => string.Equals(g.Key.TaxComponent, taxComponent, StringComparison.InvariantCultureIgnoreCase)).FirstOrDefault();
                if (group != null)
                {
                    taxAmount = group.Sum(l => l.Amount);
                }
                return taxAmount;
            }

            /// <summary>
            /// Gets the store customer account number based on store type.
            /// </summary>
            /// <returns>The store customer account number.</returns>
            internal static string GetStoreCustomerAccountNumberFromChannelProperties(RequestContext requestContext)
            {
                if (requestContext.GetChannelConfiguration().IsOnlineStore())
                {
                    if (requestContext.GetPrincipal().IsCustomer)
                    {
                        return requestContext.GetPrincipal().UserId;
                    }
                }
                return requestContext.GetChannel().DefaultCustomerAccount;
            }

            ///<summary>
            /// Defines whether the customer is store default customer.
            /// </summary>
            /// <param name="requestContext">Request context.</param>
            /// <param name="customerId">Customer id.</param>
            /// <returns>rue if the customer is store default customer; false otherwise.</returns>
            private static bool IsStoreCustomer(RequestContext requestContext, string customerId)
            {
                return string.IsNullOrEmpty(customerId)
                    || string.Equals(customerId, GetStoreCustomerAccountNumberFromChannelProperties(requestContext), StringComparison.InvariantCultureIgnoreCase);
            }

            /// <summary>
            /// Defines whether the transaction is B2C.
            /// </summary>
            /// <param name="requestContext">Request context.</param>
            /// <param name="salesOrder">Sales order.</param>
            /// <returns>True if the transaction is B2C; false otherwise.</returns>
            private static async Task<bool> IsB2CTransactionAsync(RequestContext requestContext, SalesOrder salesOrder)
            {
                if (IsStoreCustomer(requestContext, salesOrder.CustomerId))
                {
                    return true;
                }
                var customer = await GetCustomerAsync(requestContext, salesOrder.CustomerId).ConfigureAwait(false);
                if (customer == null)
                {
                    return true;
                }
                var address = customer.GetPrimaryAddress();
                if (address == null)
                {
                    return true;
                }
                GetPrimaryAddressTaxInformationDataRequest getPrimaryAddressTaxInformationDataRequest = new GetPrimaryAddressTaxInformationDataRequest(address.LogisticsLocationRecordId);
                AddressTaxInformationIndia addressTaxInformationIndia = (await requestContext.Runtime.ExecuteAsync<SingleEntityDataServiceResponse<AddressTaxInformationIndia>>(getPrimaryAddressTaxInformationDataRequest, requestContext).ConfigureAwait(false)).Entity;
                if (addressTaxInformationIndia == null
                    || addressTaxInformationIndia.GstinRegistrationNumber == null
                    || string.IsNullOrEmpty(addressTaxInformationIndia.GstinRegistrationNumber.RegistrationNumber))
                {
                    return true;
                }
                return false;
            }

            /// <summary>
            /// Gets customer by customer identifier.
            /// </summary>
            /// <param name="customerId">Customer identifier.</param>
            /// <returns>Customer object.</returns>
            private static async Task<Customer> GetCustomerAsync(RequestContext requestContext, string customerId)
            {
                Customer customer = null;
                if (!string.IsNullOrWhiteSpace(customerId))
                {
                    var getCustomerDataRequest = new GetCustomerDataRequest(customerId);
                    SingleEntityDataServiceResponse<Customer> getCustomerDataResponse = await requestContext.ExecuteAsync<SingleEntityDataServiceResponse<Customer>>(getCustomerDataRequest).ConfigureAwait(false);
                    customer = getCustomerDataResponse.Entity;
                }
                return customer;
            }

            /// <summary>
            /// Formats amount.
            /// </summary>
            /// <param name="amount">Amount to format.</param>
            /// <returns>Formatted amount.</returns>
            private static string FormatAmount(decimal amount)
            {
                return amount.ToString("0.00", CultureInfo.InvariantCulture);
            }
        }
    }
}
```     
