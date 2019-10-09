---
# required metadata

title: Customer information management (Italy)
description: This topic describes how to handle customer information in Retail POS for Italy.
author:
manager: annbe
ms.date: 10/08/2019
ms.topic: article
ms.prod:
ms.service: dynamics-365-retail
ms.technology:

# optional metadata

ms.search.form: RetailFunctionalityProfile, RetailParameters
audience: Application User
# ms.devlang:
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm:
# ms.custom:
ms.search.region: Italy
ms.search.industry: Retail
ms.author: sepism
ms.search.validFrom: 2019-10-08
ms.dyn365.ops.version: 10.0.7

---
# Customer information management (Italy)

[!include [banner](../includes/banner.md)]

## Introduction

This topic describes how customer information, such as the customer's fiscal code, can be handled in the Retail point of sale (POS) for Italy.

You can specify the customer's fiscal code when you create or edit a customer master record in POS. You can also specify the fiscal code for a sales transaction by copying it from the transaction customer or by entering it manually. The customer information can then be printed on both regular and fiscal receipts and be used for the purposes of the National lottery. Personal fiscal codes can also be used to search for a customer in POS.

> [!Note]
> This functionality is available in Finance and Operations apps version 10.0.7 and later.

## Setup

You must configure the following in order to use this functionality.

- Add the "Add customer information" operation to screen layouts.
- Activate the inquiry for customer information.
- Set up receipt formats.
- Enable the customer search criterion.
- Configure Retail channel components.

### Add new operation to screen layouts

The "Add customer information" operation can be used to add the customer information, such as Fiscal code, to a sales transaction by either copying it from the customer that is specified for the transaction or by entering it manually.

On the **Button grids** page, select the button grid that you want the operation to be displayed in, open the Button grid designer, add a new button, and select **Add customer information** in the **Action** field. For more information about how to work with screen layouts and button grids, see [Screen layouts for the point of sale (POS)](../pos-screen-layouts.md).

### Activate customer information inquiry

If the customer information is not specified for a sales transaction, an inquiry of customer information can be triggered automatically after a sales transaction is finalized, as an alternative to using the "Add customer information" operation.

To activate the inquiry of customer information, select the **Enable inquiry of customer information in sales transactions** parameter in the **Tax parameters** field group on the **Functions** fast tab of the **POS Functionality profiles** page.

### Set up receipt formats

You can configure receipt formats so that the customer's fiscal code is printed on receipts.

> [!Note]
> The default company of the user who creates the receipt setup should be the same legal entity where the language text setup is created. Alternatively, the same language texts should be created in both the user's default company and the legal entity of the store that the setup is created for.

On the **Language text** page, add the following records for the labels of the custom fields for receipt formats. Note that the **Language ID**, **Text ID**, and **Text** values that are shown in the table are just examples. You can change them to meet to your requirements. However, the **Text ID** values that you use must be unique, and they must be equal to or greater than 900001.

Add the following POS labels to the **POS** section of **Language text** from the table:

| Language ID | Text ID | Text                |
|-------------|---------|---------------------|
| en-US       | 900001  | Fiscal code         |

On the **Custom fields** page, add the following records for the custom fields for receipt formats. Note that the **Caption text ID** values must correspond to the **Text ID** values that you specified on the **Language text** page:

| Name                         | Type    | Caption text ID |
|------------------------------|---------|-----------------|
| FISCALCUSTOMER_FISCALCODE_IT | Receipt | 900001          |

For every required receipt format, in the Receipt format designer, add the custom fields to the appropriate receipt section. For more information about how to work with receipt formats, see [Receipt templates and printing](../receipt-templates-printing.md).

### Enable customer search criterion

You can add a customer search criterion to enable searching for customers in POS by their fiscal codes.

On the **POS search criteria** tab of the **Retail parameters** page, add a new customer search criterion and select "Tax registration number" in the **Customer search criteria** drop-down list. Select the **Display as shortcut** checkbox while keeping the **Can be refined** checkbox clear. Run the 1110 job on the **Distribution schedules** page.

### Configure Retail channel components

To enable the functionality that is specific to Italy, you must configure extensions for Retail channel components. For more information, see the [Deployment guidelines](#deployment-guidelines) section below.

## Example scenarios

The following example scenarios demonstrate how to work with customer information in POS for Italy.

### Scenario 1: Sale to ananymous customer

1. Sign in to POS.
1. Add items to the cart.
1. Click **Add customer information** and select **Enter manually**.
1. Specify the customer's fiscal code and click **OK**.
1. Register payments for the transaction and finalize the transaction.
1. Verify that the printed receipt contains the customer's fiscal code.

### Scenario 2: Sale to new named customer

1. Sign in to POS.
1. Add items to the cart.
1. Click **Add customer** and click **New**.
1. Populate the new customer's attributes. Specify the customer's fiscal code in the **Fiscal code** field. Save the customer record and add the customer to the transaction.
1. Register payments for the transaction and finalize the transaction.
1. Click **Yes** in the **Enter customer information** dialog, and select **Copy from transaction customer**.
1. Verify the customer's fiscal code and click **OK**.
1. Verify that the printed receipt contains the customer's fiscal code.

> [!NOTE]
> If you need to specify a different customer for the transaction, you must clear the customer information and copy it again after the new customer is added.

### Scenario 3: Change customer information for sale to named customer

1. Sign in to POS.
1. Add items to the cart.
1. Click **Add customer** and select a customer account to add it to the transaction.
1. Click **Add customer information** and select **Copy from transaction customer**.
1. Verify the customer's fiscal code and click **OK**.
1. Click **Add customer information** and select **Clear** to clear the customer information from the transaction.
1. Click **Add customer information** and select **Enter Manually**.
1. Specify the customer's fiscal code and click **OK**.
1. Register payments for the transaction and finalize the transaction.
1. Verify that the printed receipt contains the customer's fiscal code.

## Deployment guidelines
This section provides deployment guidance for enabling the customer information management in the Microsoft Dynamics 365 Retail localization for Italy.

> [!NOTE]
> Some steps in the procedures in this topic differ depending on the version of Retail that you're using. For more information, see [What's new or changed in Dynamics 365 for Retail](../get-started/whats-new.md).

> [!NOTE]
> If you want to enable the integration of POS with fiscal printers for Italy, and in particular, to print customers' fiscal codes in fiscal receipts, you need to deploy the [fiscal printer integration sample for Italy](emea-ita-fpi-sample.md).

### Update customizations

Follow these steps if any of your customizations include request handlers for the following requests: `SaveCartRequest`, `CreateSalesOrderServiceRequest`.

1. Find the request handler for the `SaveCartRequest` request.
1. Find the line of code executing the original handler.
1. Replace the original handler class with `TaxRegistrationIdFiscalCustomerService`:

    ```cs
    using Microsoft.Dynamics.Commerce.Runtime.TaxRegistrationIdItaly.Services;

    ...

    var requestHandler = new TaxRegistrationIdFiscalCustomerService();
    var response = request.RequestContext.Runtime.Execute<SaveCartResponse>(request, request.RequestContext, requestHandler, skipRequestTriggers: false);
    ```
1. Repeat the above steps for the `CreateSalesOrderServiceRequest` request.

### Update development environment

Follow these steps to update a development environment.

#### CRT extension components

1. Find the extension configuration file for CRT:

    - **Retail Server:** Find the `CommerceRuntime.Ext.config` file in the `bin\ext` folder under the Microsoft Internet Information Services (IIS) Retail server site location.
    - **Local CRT on Modern POS:** Find the `CommerceRuntime.MPOSOffline.Ext.config` file under the local CRT client broker location.

1. Register the CRT extension in the extension configuration file:

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.TaxRegistrationIdItaly" />
    ```

    > [!WARNING]
    > Do **not** edit the `CommerceRuntime.config` and `CommerceRuntime.MPOSOffline.config` files. These files aren't intended for any customizations.

#### Modern POS extension components

Enable the `TaxRegistrationId.IT` extension.

1. Open the solution at `RetailSdk\POS\ModernPOS.sln`.
1. Enable the extension in `POS.Extensions\extensions.json`.

    ``` json
    {
        "extensionPackages": [
            {
               "baseUrl": "Microsoft/TaxRegistrationId.IT"
            }
        ]
    }
    ```
1. Build the solution.
1. Run Modern POS and test the functionality.

#### Cloud POS extension components

Enable the `TaxRegistrationId.IT` extension.

1. Open the solution at `RetailSdk\POS\CloudPOS.sln`.
1. Enable the extension in `POS.Extensions\extensions.json`.

    ``` json
    {
        "extensionPackages": [
            {
               "baseUrl": "Microsoft/TaxRegistrationId.IT"
            }
        ]
    }
    ```

1. Build the solution.
1. Run Cloud POS and test the functionality.

### Update production environment

Follow these steps to create deployable packages that contain Retail components, and to apply the packages in a production environment.

1. In the `CommerceRuntime.Ext.config` and `CommerceRuntime.MPOSOffline.Ext.config` configuration files under the `RetailSdk\Assets` folder, add the following lines to the `composition` section.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.TaxRegistrationIdItaly" />
    ```

1. Enable the `TaxRegistrationId.IT` POS extension.

    ``` json
    {
        "extensionPackages": [
            {
                "baseUrl": "Microsoft/TaxRegistrationId.IT"
            }
        ]
    }
    ```

1. Run `msbuild` for the whole Retail SDK to create deployable packages.

1. Apply the packages via Microsoft Dynamics Lifecycle Services (LCS) or manually. For more information, see [Retail SDK packaging](../dev-itpro/retail-sdk/retail-sdk-packaging.md).
