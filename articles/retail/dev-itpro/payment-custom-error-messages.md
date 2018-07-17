---
# required metadata

title: Custom error messages for payment terminal extensions
description: This topic describes how to create custom localized error messages for payment terminal extensions.
author: 
manager: AnnBe
ms.date: 07/20/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: rassadi
ms.search.validFrom: 2018-07-20
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update

---

# Custom error messages for payment terminal extensions
This topic describes how to create custom localized error messages for payment terminal extension. The most common scenario to leverage these custom error messages is when the payment terminal returns additional details on why a specific payment has failed that would be relevant to the cashier operating the POS terminal. For example, sometimes the external payment terminal/gateway might return unique identifiers (e.g. reference numbers or transaction identifiers) that would be relevant for troubleshooting with the payment provider.

## Key terms

| Term | Description |
|---|---|
| Payment connector | An extension library that is written to integrate the POS with a payment terminal. |

## Overview
This topic describes the following steps to create custom localized error messages for payment terminal extensions:

- **[Create custom error messages](#Create-custom-error-messages):** This step describes in detail how to create a custom error message in payment connector that can be returned and displayed in the POS. 
- **[Create localized error messages](#Create-localized-error-messages):** This step describes how to localize the custom error messages created in the payment connector and displayed in the POS.

## Create custom error messages
In order to trigger a custom error message in the POS the `Errors` property of the `paymentInfo` passed to the `AuthorizePaymentTerminalDeviceResponse` object has to be set with the appropriate error. In particular, the `isLocalized` parameter on the constructor of the `PaymentError` object has to be set to `true` to force the POS to use the customized error message rather than the built in error message for a decline.

``` csharp
namespace Contoso.Commerce.HardwareStation.PaymentSample 
{ 
    /// <summary>
    /// <c>Simulator</c> manager payment device class.
    /// </summary>
    public class PaymentDeviceSample : INamedRequestHandler
    {
        /// <summary>
        /// Gets the collection of supported request types by this handler.
        /// </summary>
        public IEnumerable<Type> SupportedRequestTypes
        {
            get
            {
                return new[]
                {
                    typeof(AuthorizePaymentTerminalDeviceRequest),
                    ...
                };
            }
        }

        /// <summary>
        /// Executes the payment device simulator operation based on the incoming request type.
        /// </summary>
        /// <param name="request">The payment terminal device simulator request message.</param>
        /// <returns>Returns the payment terminal device simulator response.</returns>
        public Response Execute(Microsoft.Dynamics.Commerce.Runtime.Messages.Request request)
        {
            ThrowIf.Null(request, "request");

            Type requestType = request.GetType();

            if (requestType == typeof(AuthorizePaymentTerminalDeviceRequest))
            {
                return this.AuthorizePayment((AuthorizePaymentTerminalDeviceRequest)request);
            }
            else if (...)
            {
                ...
            }

            return new NullResponse();
        }

        /// <summary>
        /// Authorize payment.
        /// </summary>
        /// <param name="request">The authorize payment request.</param>
        /// <returns>The authorize payment response.</returns>
        public AuthorizePaymentTerminalDeviceResponse AuthorizePayment(AuthorizePaymentTerminalDeviceRequest request)
        {
            ThrowIf.Null(request, "request");

            ...

            // Assuming the external payment terminal/gateway returned a decline and a reference number.
            // Construct the custom error message and set the payment error on the 'paymentInfo' object set
            // on the response.
            PaymentInfo paymentInfo = new PaymentInfo();
            string errorMessage = string.Format("The payment was declined. Reference number '{0}'.", referenceNumber);
            PaymentError paymentError = new PaymentError(ErrorCode.Decline, "Test Messsage", true);
            paymentInfo.Errors = new PaymentError[] { paymentError };

            return new AuthorizePaymentTerminalDeviceResponse(paymentInfo);
        }
    }
}
```

The following screenshot illustrates how the customized error message will surface in the POS.

![Custom payment error message in POS](media/PAYMENTS/CUSTOM-ERRORS/POS-Custom-Payment-Error.jpg)

## Create localized error messages

### Create resource files for each language
In order to return localized error messages from the payment connector to the POS create distinct files that contain the messages for each language. To create a file right click on your connector project (or a sub-folder if necessary) in Visual Studio, click on `Add` > `New Item ...`. In the new `Add New Item` window select `Visual C# Items` in the left pane and select `Resource File` in the middle pane. 

![Create new resource file in Visual Studio](media/PAYMENTS/CUSTOM-ERRORS/VisualStudio-New-Resource-File.jpg)

You can name and organize the files in your project as you best see fit but the below illustrates one possible naming convention for the files:

- `Messages.en-us.resx`
- `Messages.en-ca.resx`
- `Messages.fr-fr.resx`
- ...

### Create customer localized error messages
Each of the resource files has to contain each error message you would like to customize and localize. The example below illustrates what the content of the `Messages.en-us.resx` would look like. Note the entry for `Microsoft_Dynamics_Commerce_Payments_Decline` at the bottom of the file. Each of the resource files for each locale should have an identical set of localized messages.

``` xml
<?xml version="1.0" encoding="utf-8"?>
<root>
  <xsd:schema id="root" xmlns="" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">
    <xsd:import namespace="http://www.w3.org/XML/1998/namespace" />
    <xsd:element name="root" msdata:IsDataSet="true">
      <xsd:complexType>
        <xsd:choice maxOccurs="unbounded">
          <xsd:element name="metadata">
            <xsd:complexType>
              <xsd:sequence>
                <xsd:element name="value" type="xsd:string" minOccurs="0" />
              </xsd:sequence>
              <xsd:attribute name="name" use="required" type="xsd:string" />
              <xsd:attribute name="type" type="xsd:string" />
              <xsd:attribute name="mimetype" type="xsd:string" />
              <xsd:attribute ref="xml:space" />
            </xsd:complexType>
          </xsd:element>
          <xsd:element name="assembly">
            <xsd:complexType>
              <xsd:attribute name="alias" type="xsd:string" />
              <xsd:attribute name="name" type="xsd:string" />
            </xsd:complexType>
          </xsd:element>
          <xsd:element name="data">
            <xsd:complexType>
              <xsd:sequence>
                <xsd:element name="value" type="xsd:string" minOccurs="0" msdata:Ordinal="1" />
                <xsd:element name="comment" type="xsd:string" minOccurs="0" msdata:Ordinal="2" />
              </xsd:sequence>
              <xsd:attribute name="name" type="xsd:string" use="required" msdata:Ordinal="1" />
              <xsd:attribute name="type" type="xsd:string" msdata:Ordinal="3" />
              <xsd:attribute name="mimetype" type="xsd:string" msdata:Ordinal="4" />
              <xsd:attribute ref="xml:space" />
            </xsd:complexType>
          </xsd:element>
          <xsd:element name="resheader">
            <xsd:complexType>
              <xsd:sequence>
                <xsd:element name="value" type="xsd:string" minOccurs="0" msdata:Ordinal="1" />
              </xsd:sequence>
              <xsd:attribute name="name" type="xsd:string" use="required" />
            </xsd:complexType>
          </xsd:element>
        </xsd:choice>
      </xsd:complexType>
    </xsd:element>
  </xsd:schema>
  <resheader name="resmimetype">
    <value>text/microsoft-resx</value>
  </resheader>
  <resheader name="version">
    <value>2.0</value>
  </resheader>
  <resheader name="reader">
    <value>System.Resources.ResXResourceReader, System.Windows.Forms, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089</value>
  </resheader>
  <resheader name="writer">
    <value>System.Resources.ResXResourceWriter, System.Windows.Forms, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089</value>
  </resheader>
  <data name="Microsoft_Dynamics_Commerce_Payments_Decline" xml:space="preserve">
    <value>The payment was declined. Reference number '{0}'.</value>
  </data>
</root>
```

### Load the localized message in the connector code
The example below illustrates how you can leverage the resource files created above in your payment connector code to load a localized message. Note, the example below is significantly simplified to illustrate the mechanics of loading the localized messages during the runtime of your payment connector code. However, we recommend that you introduce a new set of classes to manage loading the appropriate resource file.

``` csharp
namespace Contoso.Commerce.HardwareStation.PaymentSample 
{ 
    /// <summary>
    /// <c>Simulator</c> manager payment device class.
    /// </summary>
    public class PaymentDeviceSample : INamedRequestHandler
    {
        ...

        /// <summary>
        /// Authorize payment.
        /// </summary>
        /// <param name="request">The authorize payment request.</param>
        /// <returns>The authorize payment response.</returns>
        public AuthorizePaymentTerminalDeviceResponse AuthorizePayment(AuthorizePaymentTerminalDeviceRequest request)
        {
            ThrowIf.Null(request, "request");

            ...

            // Assuming the external payment terminal/gateway returned a decline and a reference number.
            // Construct the custom error message and set the payment error on the 'paymentInfo' object set
            // on the response.
            PaymentInfo paymentInfo = new PaymentInfo();
            string errorMessage = string.Format("The payment was declined. Reference number '{0}'.", referenceNumber);
            PaymentError paymentError = new PaymentError(ErrorCode.Decline, "Test Messsage", true);
            paymentInfo.Errors = new PaymentError[] { paymentError };

            return new AuthorizePaymentTerminalDeviceResponse(paymentInfo);
        }
    }
}
```
