# Customer information management for Poland
---

title: Customer information management for Poland
[!include [banner](../includes/banner.md)]
description: This article describes how to handle customer information in Retail POS for Poland.

author: josaw1

ms.date: 09/21/2021
## Introduction
ms.topic: article

ms.prod: 
This article describes how you can handle customer information, such as the customer's value-added tax (VAT) number, in Retail point of sale (POS) for Poland.
ms.technology: 

audience: Application User
You can specify the customer's VAT number when you create or edit a customer master record in POS. You can also specify a VAT number for a sales transaction by copying it from the transaction customer or entering it manually. The customer information can then be printed on both regular and fiscal receipts, and it can be used for invoicing purposes.
ms.reviewer: josaw

ms.search.region: Poland
> [!NOTE]
ms.author: josaw
> It isn't possible to specify a VAT number for a customer in POS when **Create customer in async mode** is enabled in the POS functionality profile. Support for the async customer creation mode may be added in future updates.
ms.search.validFrom: 2019-11-11

ms.dyn365.ops.version: 10.0.7
## Setup
ms.search.industry: Retail

ms.search.form: RetailFunctionalityProfile, RetailParameters
You must complete the following configuration to use this functionality:

---
- Set up a registration type for the VAT number.

- Add the **Add customer information** operation to screen layouts.
### Update a development environment
- Activate the inquiry for customer information.

- Set up receipt formats.
Follow these steps to update a development environment.
- Configure channel components.


#### CRT extension components
### Set up a registration type for the VAT number


1. Find the extension configuration file for the Commerce runtime (CRT):
Before VAT numbers can be specified in POS, you must create an appropriate registration type for the VAT number and link it to the **VAT ID** registration category. For more information about how to work with registration types and registration IDs, see [Registration IDs](../../finance/localizations/emea-registration-ids.md).


    - **Commerce Scale Unit:** Find the **CommerceRuntime.Ext.config** file in the **bin\\ext** folder under the Microsoft Internet Information Services (IIS) Commerce Scale Unit site location.
> [!WARNING]
    - **Local CRT on Modern POS:** Find the **CommerceRuntime.MPOSOffline.Ext.config** file under the local CRT client broker location.
> If a registration type isn't created or isn't linked to the **VAT ID** registration category, an error will be generated in POS when VAT number is filled in for a customer address.


1. Register the CRT extension in the extension configuration file.
### Add the Add customer information operation to screen layouts


    ``` xml
The **Add customer information** operation can be used to add customer information, such as the VAT number, to a sales transaction. This information can be copied from the customer that is specified for the transaction, or it can be manually entered.
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.TaxRegistrationIdPoland" />

    ```
On the **Button grids** page, select the button grid where the operation should appear, and open the Button grid designer. Add a new button, and then, in the **Action** field, select **Add customer information**. For more information about how to work with screen layouts and button grids, see [Screen layouts for the point of sale (POS)](../pos-screen-layouts.md).


    > [!WARNING]
### Activate the inquiry for customer information
    > Do **not** edit the CommerceRuntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.


If the customer information isn't specified for a sales transaction, an inquiry for that information can be triggered automatically after the transaction is finalized. This approach is an alternative to the **Add customer information** operation.
#### Modern POS extension components


To activate the inquiry for customer information, enable the **(Poland) Customer information management in Retail POS** feature in the **Feature management** workspace, and set the **Enable inquiry of customer information in sales transactions** option to **Yes** in the **Tax parameters** section on the **Functions** FastTab of the **POS functionality profiles** page.
Follow these steps to make the TaxRegistrationId.PL extension available.


### Set up receipt formats
1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**.

1. In **POS.Extensions\\extensions.json**, turn on the extension.
You can configure receipt formats so that the customer's VAT number is printed on receipts.


    ``` json
> [!NOTE]
    {
> The default company of the user who creates the receipt setup should be the same legal entity where the language text setup is created. Alternatively, the same language texts should be created in both the user's default company and the legal entity of the store that the setup is created for.
        "extensionPackages": [

            {
On the **Language text** page, on the **POS** tab, add the following record for the label of the custom field for receipt formats. Note that the **Language ID**, **Text ID**, and **Text** values that are shown in the following table are just examples. You can change them to meet your requirements. However, the **Text ID** value that you use must be unique, and it must be equal to or more than 900001.
                "baseUrl": "Microsoft/TaxRegistrationId.PL"

            }
| Language ID | Text ID | Text       |
        ]
|-------------|---------|------------|
    }
| en-US       | 900001  | VAT number |
    ```


On the **Custom fields** page, add the following record for the custom field for receipt formats. Note that the **Caption text ID** value must correspond to the **Text ID** value that you specified on the **Language text** page.
1. Build the solution.

1. Open Modern POS, and test the functionality.
| Name                      | Type    | Caption text ID |

|---------------------------|---------|-----------------|
#### Cloud POS extension components
| FISCALCUSTOMER\_VATID\_PL | Receipt | 900001          |


Follow these steps to make the TaxRegistrationId.PL extension available.
In the Receipt format designer, add the custom field to the appropriate receipt section for every receipt format that is required. For more information about how to work with receipt formats, see [Receipt templates and printing](../receipt-templates-printing.md).


1. Open the solution at **RetailSdk\\POS\\CloudPOS.sln**.
### Configure channel components
1. In **POS.Extensions\\extensions.json**, turn on the extension.


To make the functionality that is specific to Poland available, you must configure extensions for channel components. For more information, see the [Deployment guidelines](#deployment-guidelines) section later in this article.
    ``` json

    {
## Example scenarios
        "extensionPackages": [

            {
The following example scenarios show how to work with customer information in POS for Poland.
                "baseUrl": "Microsoft/TaxRegistrationId.PL"

            }
### Scenario 1: Make a sale to an anonymous customer
        ]

    }
1. Sign in to POS.
    ```
1. Add items to the cart.

1. Select **Add customer information**, and then select **Enter manually**.
1. Build the solution.
1. Enter the customer's VAT number, and then select **OK**.
1. Open Cloud POS, and test the functionality.
1. Register payments for the transaction, and then finalize the transaction.

1. Verify that the printed receipt contains the customer's VAT number.
### Update a production environment


### Scenario 2: Make a sale to a new named customer
Follow these steps to create deployable packages that contain Commerce components, and to apply the packages in a production environment.


1. Sign in to POS.
1. In the **CommerceRuntime.Ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files under the **RetailSdk\\Assets** folder, add the following lines to the **composition** section.
1. Add items to the cart.

1. Select **Add customer**, and then select **New**.
    ``` xml
1. Specify the new customer's attributes.
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.TaxRegistrationIdPoland" />
1. Select **Create a new address**. Then specify the new customer's contact information and an address.
    ```
1. In the **VAT number** field, enter the customer's VAT number.

1. Save the customer record and the customer address record, and add the customer to the transaction.
1. Turn on the **TaxRegistrationId.PL** POS extension.
1. Register payments for the transaction, and then finalize the transaction.

1. Because the inquiry for customer information has been activated, but customer information hasn't been added to the transaction, the **Enter customer information** dialog box is opened. Select **Yes**, and then select **Copy from transaction customer**.
    ``` json
1. Verify the customer's VAT number, and then select **OK**.
    {
1. Verify that the printed receipt contains the customer's VAT number.
        "extensionPackages": [

            {
> [!NOTE]
                "baseUrl": "Microsoft/TaxRegistrationId.PL"
> If you must specify a different customer for the transaction, you must clear the customer information and then copy it again after the new customer is added.
            }

        ]
### Scenario 3: Change the customer information for a sale to a named customer
    }

    ```
1. Sign in to POS.

1. Add items to the cart.
1. Run **msbuild** for the whole Retail software development kit (SDK) to create deployable packages.
1. Select **Add customer**, and then select a customer account to add it to the transaction.
1. Apply the packages via Microsoft Dynamics Lifecycle Services (LCS) or manually. For more information, see [Retail SDK packaging](../dev-itpro/retail-sdk/retail-sdk-packaging.md).
1. Select **Add customer information**, and then select **Copy from transaction customer**.

1. Verify the customer's VAT number, and then select **OK**.

1. Select **Add customer information**, and then select **Clear** to clear the customer information from the transaction.
[!INCLUDE[footer-include](../../includes/footer-banner.md)]
1. Select **Add customer information**, and then select **Enter manually**.
1. Specify the customer's VAT number, and then select **OK**.
1. Register payments for the transaction, and then finalize the transaction.
1. Verify that the printed receipt contains the customer's VAT number.

## Deployment guidelines

This section provides deployment guidance for enabling customer information management in the localization of Dynamics 365 Commerce for Poland.

> [!NOTE]
> Some steps in these procedures vary, depending on the product version you're using. For more information, see [What's new or changed in Dynamics 365 for Retail](../get-started/whats-new.md).
>
> If you want to enable the integration of POS with fiscal printers for Poland, and specifically if you want to print customer VAT numbers on fiscal receipts, you must deploy the [fiscal printer integration sample for Poland](emea-pol-fpi-sample.md).

### Update customizations

Follow these steps to update customizations.

# [Retail 10.0.7 and later](#tab/retail-10-0-7)

If any of your customizations include request handlers for the `SaveCartRequest` or `CreateSalesOrderServiceRequest` requests:

1. Find the request handler for `SaveCartRequest`.
1. Find the line of code that runs the original request handler.
1. Add the following lines before calling the original request handler:

    ```cs
    using Microsoft.Dynamics.Commerce.Runtime.TaxRegistrationIdPoland.Services;

    ...

    new TaxRegistrationIdFiscalCustomerService().Execute(request);
    ```

1. Find the request handler for `CreateSalesOrderServiceRequest`.
1. Find the line of code that runs the original request handler.
1. Replace it with the following code:

    ```cs
    using Microsoft.Dynamics.Commerce.Runtime.TaxRegistrationIdPoland.Services;

    ...

    return new TaxRegistrationIdFiscalCustomerService().Execute(request);
    ```

# [Retail 10.0.12 and later](#tab/retail-10-0-12)

If customizations have references to the `TaxRegistrationIdFiscalCustomerService` service, they must be removed.

---
