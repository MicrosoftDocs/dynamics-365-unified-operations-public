---
title: Customer information management for Poland
description: Learn how to handle customer information in Retail POS for Poland.
author: EvgenyPopovMBS
ms.date: 02/27/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Poland
ms.author: anupamar
ms.search.validFrom: 2019-11-11
ms.custom: 
  - bap-template
---
# Customer information management for Poland

[!include [banner](../../../finance/includes/banner.md)]

This article describes how you can handle customer information, such as the customer's value-added tax (VAT) number, in Retail point of sale (POS) for Poland.

You can specify the customer's VAT number when you create or edit a customer master record in POS. You can also specify a VAT number for a sales transaction by copying it from the transaction customer or entering it manually. You can print the customer information on both regular and fiscal receipts, and use it for invoicing purposes.

> [!IMPORTANT]
> You can't specify a VAT number for a customer in POS when **Create customer in async mode** is enabled in the POS functionality profile. Support for the async customer creation mode might be added in future updates.

## Setup

Complete the following configuration steps to use this functionality:

- Set up a registration type for the VAT number.
- Add the **Add customer information** operation to screen layouts.
- Activate the inquiry for customer information.
- Set up receipt formats.
- Configure channel components.

> [!NOTE]
> For Commerce version 10.0.38 and earlier, enable the **(Poland) Customer information management in Retail POS** feature in the Commerce headquarters **Feature management** workspace.

### Set up a registration type for the VAT number

Before you can specify VAT numbers in POS, create an appropriate registration type for the VAT number and link it to the **VAT ID** registration category. For more information about how to work with registration types and registration IDs, see [Registration IDs](../../../finance/localizations/europe/emea-registration-ids.md).

> [!WARNING]
> If you don't create a registration type or link it to the **VAT ID** registration category, POS generates an error when you enter a VAT number for a customer address.

### Add the Add customer information operation to screen layouts

Use the **Add customer information** operation to add customer information, such as the VAT number, to a sales transaction. You can copy this information from the customer that you specify for the transaction, or you can enter it manually.

On the **Button grids** page, select the button grid where the operation should appear, and open the Button grid designer. Add a new button, and then, in the **Action** field, select **Add customer information**. For more information about how to work with screen layouts and button grids, see [Screen layouts for the point of sale (POS)](../../pos-screen-layouts.md).

### Activate the inquiry for customer information

If you don't specify the customer information for a sales transaction, an inquiry for that information can be triggered automatically after the transaction is finalized. This approach is an alternative to the **Add customer information** operation.

To activate the inquiry for customer information in Commerce headquarters, on the **POS functionality profiles** page, on the **Functions** FastTab, in the **Tax parameters** section, set the **Enable inquiry of customer information in sales transactions** option to **Yes**.

### Set up receipt formats

You can configure receipt formats so that the customer's VAT number prints on receipts.

> [!NOTE]
> The default company of the user who creates the receipt setup should be the same legal entity where the language text setup is created. Alternatively, the same language texts should be created in both the user's default company and the legal entity of the store that the setup is created for.

On the **Language text** page, on the **POS** tab, add the following record for the label of the custom field for receipt formats. The **Language ID**, **Text ID**, and **Text** values that are shown in the following table are examples. You can change them to meet your requirements. However, the **Text ID** value that you use must be unique, and it must be equal to or greater than 900001.

| Language ID | Text ID | Text       |
|-------------|---------|------------|
| en-US       | 900001  | VAT number |

On the **Custom fields** page, add the following record for the custom field for receipt formats. The **Caption text ID** value must correspond to the **Text ID** value that you specified on the **Language text** page.

| Name                      | Type    | Caption text ID |
|---------------------------|---------|-----------------|
| FISCALCUSTOMER\_VATID\_PL | Receipt | 900001          |

In the Receipt format designer, add the custom field to the appropriate receipt section for every receipt format that you require. For more information about how to work with receipt formats, see [Receipt templates and printing](../../receipt-templates-printing.md).

### Configure channel components

> [!IMPORTANT]
> Implement the steps described in this section only if you're using Microsoft Dynamics 365 Commerce version 10.0.28 or earlier. As of Commerce version 10.0.29, all Commerce channel components that are required to activate customer information management for Poland are enabled by default. If you're using Commerce version 10.0.28 or earlier and are migrating to Commerce version 10.0.29 or later, follow the steps in [Migrate to version 10.0.29 or later](#migrate-to-commerce-version-10029-or-later).

To make the functionality that's specific to Poland available, you must configure extensions for channel components. For more information, see the [Deployment guidelines](#deployment-guidelines) section later in this article.

## Example scenarios

The following example scenarios show how to work with customer information in POS for Poland.

### Scenario 1: Make a sale to an anonymous customer

1. Sign in to POS.
1. Add items to the cart.
1. Select **Add customer information**, and then select **Enter manually**.
1. Enter the customer's VAT number, and then select **OK**.
1. Register payments for the transaction, and then finalize the transaction.
1. Verify that the printed receipt contains the customer's VAT number.

### Scenario 2: Make a sale to a new named customer

1. Sign in to POS.
1. Add items to the cart.
1. Select **Add customer**, and then select **New**.
1. Specify the new customer's attributes.
1. Select **Create a new address**. Then specify the new customer's contact information and an address.
1. In the **VAT number** field, enter the customer's VAT number.
1. Save the customer record and the customer address record, and add the customer to the transaction.
1. Register payments for the transaction, and then finalize the transaction.
1. Because the inquiry for customer information is activated, but customer information isn't added to the transaction, the **Enter customer information** dialog box opens. Select **Yes**, and then select **Copy from transaction customer**.
1. Verify the customer's VAT number, and then select **OK**.
1. Verify that the printed receipt contains the customer's VAT number.

> [!NOTE]
> If you must specify a different customer for the transaction, clear the customer information and then copy it again after the new customer is added.

### Scenario 3: Change the customer information for a sale to a named customer

1. Sign in to POS.
1. Add items to the cart.
1. Select **Add customer**, and then select a customer account to add it to the transaction.
1. Select **Add customer information**, and then select **Copy from transaction customer**.
1. Verify the customer's VAT number, and then select **OK**.
1. Select **Add customer information**, and then select **Clear** to clear the customer information from the transaction.
1. Select **Add customer information**, and then select **Enter manually**.
1. Specify the customer's VAT number, and then select **OK**.
1. Register payments for the transaction, and then finalize the transaction.
1. Verify that the printed receipt contains the customer's VAT number.

## Deployment guidelines

> [!IMPORTANT]
> Implement the steps described in this section only if you're using Commerce version 10.0.28 or earlier. As of Commerce version 10.0.29, all Commerce channel components that are required to activate customer information management for Poland are enabled by default. If you're using Commerce version 10.0.28 or earlier and are migrating to the Commerce version 10.0.29 or later, follow the steps in [Migrate to version 10.0.29 or later](#migrate-to-commerce-version-10029-or-later).

This section provides deployment guidance for enabling customer information management in the localization of Dynamics 365 Commerce for Poland.

> [!NOTE]
> If you want to enable the integration of POS with fiscal printers for Poland, and specifically if you want to print customer VAT numbers on fiscal receipts, you must deploy the [fiscal printer integration sample for Poland](../dev-itpro/emea-pol-fpi-sample.md).

### Update customizations

If your customizations reference the `TaxRegistrationIdFiscalCustomerService` service, remove those references.

### Update a development environment

Follow these steps to update a development environment.

#### CRT extension components

1. Find the extension configuration file for the Commerce runtime (CRT):

    - **Commerce Scale Unit:** Find the **CommerceRuntime.Ext.config** file in the **bin\\ext** folder under the Microsoft Internet Information Services (IIS) Commerce Scale Unit site location.
    - **Local CRT on Modern POS:** Find the **CommerceRuntime.MPOSOffline.Ext.config** file under the local CRT client broker location.

1. Register the CRT extension in the extension configuration file.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.TaxRegistrationIdPoland" />
    ```

    > [!WARNING]
    > Don't edit the CommerceRuntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

#### Modern POS extension components

Follow these steps to make the TaxRegistrationId.PL extension available.

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**.
1. In the **POS.Extensions\\extensions.json** file, turn on the extension.

    ``` json
    {
        "extensionPackages": [
            {
                "baseUrl": "Microsoft/TaxRegistrationId.PL"
            }
        ]
    }
    ```

1. Build the solution.
1. Open Modern POS, and test the functionality.

#### Cloud POS extension components

Follow these steps to make the TaxRegistrationId.PL extension available.

1. Open the solution at **RetailSdk\\POS\\CloudPOS.sln**.
1. In the **POS.Extensions\\extensions.json** file, turn on the extension.

    ``` json
    {
        "extensionPackages": [
            {
                "baseUrl": "Microsoft/TaxRegistrationId.PL"
            }
        ]
    }
    ```

1. Build the solution.
1. Open Cloud POS, and test the functionality.

### Update a production environment

Follow these steps to create deployable packages that contain Commerce components, and to apply the packages in a production environment.

1. In the **CommerceRuntime.Ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files under the **RetailSdk\Assets** folder, add the following lines to the **composition** section.

    ``` xml
    <add source="assembly" value="Microsoft.Dynamics.Commerce.Runtime.TaxRegistrationIdPoland" />
    ```

1. Turn on the **TaxRegistrationId.PL** POS extension.

    ``` json
    {
        "extensionPackages": [
            {
                "baseUrl": "Microsoft/TaxRegistrationId.PL"
            }
        ]
    }
    ```

1. Run **msbuild** for the whole Retail software development kit (SDK) to create deployable packages.
1. Apply the packages via Microsoft Dynamics Lifecycle Services (LCS) or manually. For more information, see [Retail SDK packaging](../../dev-itpro/retail-sdk/retail-sdk-packaging.md).

## Migrate to Commerce version 10.0.29 or later

If you're using Commerce version 10.0.28 or earlier and are migrating to version 10.0.29 or later, complete the steps described in this section. You must follow these steps to correctly update your Commerce environment.

1. Update Commerce headquarters.
1. For Commerce version 10.0.38 and earlier, enable the **(Poland) Customer information management in Retail POS** feature in the Commerce headquarters **Feature management** workspace and distribute the changes to channels.
1. Update CRT, Cloud POS, and Modern POS, and exclude the following legacy Poland-specific extensions:

    1. In the **commerceruntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** files, exclude the **Microsoft.Dynamics.Commerce.Runtime.TaxRegistrationIdPoland** CRT extension.
    1. In the **extensions.json** file, exclude the **Microsoft/TaxRegistrationId.PL** POS extension.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
