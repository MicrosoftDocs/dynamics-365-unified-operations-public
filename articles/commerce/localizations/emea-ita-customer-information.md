---
# required metadata

title: Customer information management for Italy
description: This topic describes how to handle customer information in POS for Italy.
author: sepism
manager: annbe
ms.date: 01/14/2020
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
# Customer information management for Italy

[!include [banner](../includes/banner.md)]


## Introduction

This topic describes how you can handle customer information, such as the customer's lottery code, in the Commerce point of sale (POS) for Italy.

You can specify the customer information, such as the fiscal code or lottery code, when you create or edit a customer master record in POS. You can also specify the lottery code for a sales transaction by copying it from the transaction customer or entering it manually. The lottery code can then be printed on both regular and fiscal receipts, and it can be used for the national lottery. Personal fiscal codes can also be used to search for a customer in POS.

> [!NOTE]
> This functionality is available in version 10.0.7 and later.

## Setup

You must complete the following configuration to use this functionality:

- Set up a registration type for the lottery code.
- Add the **Add customer information** operation to screen layouts.
- Activate the inquiry for customer information.
- Set up receipt formats.
- Add a customer search criterion.
- Configure channel components.

### Set up a registration type for the lottery code

Before lottery codes can be specified in POS, you must create an appropriate registration type for the lottery code and link it to the **Lottery code** registration category. For more information about how to work with registration types and registration IDs, see [Registration IDs](../../finance/localizations/emea-registration-ids.md).

> [!WARNING]
> If a registration type isn't created or isn't linked to the **Lottery code** registration category, an error will be generated in POS when the lottery code is filled in for a customer address.

### Add the Add customer information operation to screen layouts

The **Add customer information** operation can be used to add customer information, such as the lottery code, to a sales transaction. This information can be copied from the customer that is specified for the transaction, or it can be manually entered.

On the **Button grids** page, select the button grid where the operation should appear, and open the Button grid designer. Add a new button, and then, in the **Action** field, select **Add customer information**. For more information about how to work with screen layouts and button grids, see [Screen layouts for the point of sale (POS)](../pos-screen-layouts.md).

### Activate the inquiry for customer information

If the customer information isn't specified for a sales transaction, an inquiry for that information can be triggered automatically after the transaction is finalized. This approach is an alternative to the **Add customer information** operation.

To activate the inquiry for customer information, set the **Enable inquiry of customer information in sales transactions** option to **Yes** in the **Tax parameters** section on the **Functions** FastTab of the **POS functionality profiles** page.

### Set up receipt formats

You can configure receipt formats so that the customer's fiscal code and lottery code are printed on receipts.

> [!NOTE]
> The default company of the user who creates the receipt setup should be the same legal entity where the language text setup is created. Alternatively, the same language texts should be created in both the user's default company and the legal entity of the store that the setup is created for.

On the **Language text** page, on the **POS** tab, add the following records for the labels of the custom fields for receipt formats. Note that the **Language ID**, **Text ID**, and **Text** values that are shown in the following table are just examples. You can change them to meet your requirements. However, the **Text ID** values that you use must be unique, and they must be equal to or more than 900001.

| Language ID | Text ID | Text                |
|-------------|---------|---------------------|
| en-US       | 900001  | Lottery code        |
| en-US       | 900002  | Fiscal code         |

On the **Custom fields** page, add the following records for the custom fields for receipt formats. Note that the **Caption text ID** values must correspond to the **Text ID** values that you specified on the **Language text** page.

| Name                           | Type    | Caption text ID |
|--------------------------------|---------|-----------------|
| FISCALCUSTOMER\_LOTTERYCODE\_IT| Receipt | 900001          |
| CUSTOMER\_FISCALCODE\_IT       | Receipt | 900002          |

In the Receipt format designer, add the custom fields to the appropriate receipt section for every receipt format that is required. For more information about how to work with receipt formats, see [Receipt templates and printing](../receipt-templates-printing.md).

### Add a customer search criterion

You can add a customer search criterion so that customers can be searched for in POS by their fiscal codes.

On the **Commerce parameters** page, on the **POS search criteria** tab, add a new customer search criterion. In the **Customer search criteria** field, select **Tax registration number**. Select the **Display as shortcut** check box, but leave the **Can be refined** check box cleared. Then, on the **Distribution schedules** page, run the **1110** job.

### Configure channel components

To make the functionality that is specific to Italy available, you must configure extensions for commerce channel components. For more information, see the [Deployment guidelines](#deployment-guidelines) section later in this topic.

## Example scenarios

The following example scenarios show how to work with customer information in POS for Italy.

### Scenario 1: Make a sale to an anonymous customer

1. Sign in to POS.
1. Add items to the cart.
1. Select **Add customer information**, and then select **Enter manually**.
1. Enter the customer's lottery code, and then select **OK**.
1. Register payments for the transaction, and then finalize the transaction.
1. Verify that the printed receipt contains the customer's lottery code.

### Scenario 2: Make a sale to a new named customer

1. Sign in to POS.
1. Add items to the cart.
1. Select **Add customer**, and then select **New**.
1. Specify the new customer's attributes. In the **Fiscal code** field, enter the customer's fiscal code.
1. Select **Create a new address**. Then specify the new customer's contact information and an address.
1. In the **Lottery code** field, enter the customer's lottery code.
1. Save the customer record and the customer address record, and add the customer to the transaction.
1. Register payments for the transaction, and then finalize the transaction.
1. Because the inquiry for customer information has been activated, but customer information hasn't been added to the transaction, the **Enter customer information** dialog box is opened. Select **Yes**, and then select **Copy from transaction customer**.
1. Verify the customer's lottery code, and then select **OK**.
1. Verify that the printed receipt contains the customer's lottery code.

> [!NOTE]
> If you must specify a different customer for the transaction, you must clear the customer information and then copy it again after the new customer is added.

### Scenario 3: Change the customer information for a sale to a named customer

1. Sign in to POS.
1. Add items to the cart.
1. Select **Add customer**, and then select a customer account to add it to the transaction.
1. Select **Add customer information**, and then select **Copy from transaction customer**.
1. Verify the customer's lottery code, and then select **OK**.
1. Select **Add customer information**, and then select **Clear** to clear the customer information from the transaction.
1. Select **Add customer information**, and then select **Enter manually**.
1. Specify the customer's lottery code, and then select **OK**.
1. Register payments for the transaction, and then finalize the transaction.
1. Verify that the printed receipt contains the customer's lottery code.

## Deployment guidelines

This section provides deployment guidance for enabling customer information management in the localization of Commerce for Italy.

> [!NOTE]
> Some steps in these procedures vary, depending on the version of Commerce that you're using. For more information, see [What's new or changed in Dynamics 365 for Retail](../get-started/whats-new.md).
>
> If you want to enable the integration of POS with fiscal printers for Italy, and specifically if you want to print customer lottery codes on fiscal receipts, you must deploy the [fiscal printer integration sample for Italy](emea-ita-fpi-sample.md).

### Update customizations

Follow these steps to update customizations.

# [Retail 10.0.7 and later](#tab/retail-10-0-7)

If any of your customizations include request handlers for the `SaveCartRequest` or `CreateSalesOrderServiceRequest` requests:

1. Find the request handler for `SaveCartRequest`.
1. Find the line of code that runs the original request handler.
1. Add the following lines before calling the original request handler:

    ```cs
    using Microsoft.Dynamics.Commerce.Runtime.TaxRegistrationIdItaly.Services;

    ...

    new TaxRegistrationIdFiscalCustomerService().Execute(request);
    ```

1. Find the request handler for `CreateSalesOrderServiceRequest`.
1. Find the line of code that runs the original request handler.
1. Replace it with the following code:

    ```cs
    using Microsoft.Dynamics.Commerce.Runtime.TaxRegistrationIdItaly.Services;

    ...

    return new TaxRegistrationIdFiscalCustomerService().Execute(request);
    ```

# [Retail 10.0.12 and later](#tab/retail-10-0-12)

If customizations have references to the `TaxRegistrationIdFiscalCustomerService` service, they must be removed.

---

### Update a development environment

Follow these steps to update a development environment.

#### CRT extension components

1. Find the extension configuration file for the Commerce runtime (CRT):

    - **Commerce Scale Unit:** Find the **CommerceRuntime.Ext.config** file in the **bin\\ext** folder under the Microsoft Internet Information Services (IIS) Commerce Scale Unit site location.
    - **Local CRT on Modern POS:** Find the **CommerceRuntime.MPOSOffline.Ext.config** file under the local CRT client broker location.

1. Register the CRT extension in the extension configuration file.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.TaxRegistrationIdItaly" />
    ```

    > [!WARNING]
    > Do **not** edit the CommerceRuntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### Modern POS extension components

Follow these steps to make the TaxRegistrationId.IT extension available.

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**.
1. In **POS.Extensions\\extensions.json**, turn on the extension.

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
1. Open Modern POS, and test the functionality.

#### Cloud POS extension components

Follow these steps to make the TaxRegistrationId.IT extension available.

1. Open the solution at **RetailSdk\\POS\\CloudPOS.sln**.
1. In **POS.Extensions\\extensions.json**, turn on the extension.

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
1. Open Cloud POS, and test the functionality.

### Update a production environment

Follow these steps to create deployable packages that contain Commerce components, and to apply the packages in a production environment.

1. In the **CommerceRuntime.Ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files under the **RetailSdk\\Assets** folder, add the following lines to the **composition** section.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.TaxRegistrationIdItaly" />
    ```

1. Turn on the **TaxRegistrationId.IT** POS extension.

    ``` json
    {
        "extensionPackages": [
            {
                "baseUrl": "Microsoft/TaxRegistrationId.IT"
            }
        ]
    }
    ```

1. Run **msbuild** for the whole Retail software development kit (SDK) to create deployable packages.
1. Apply the packages via Microsoft Dynamics Lifecycle Services (LCS) or manually. For more information, see [Retail SDK packaging](../dev-itpro/retail-sdk/retail-sdk-packaging.md).
