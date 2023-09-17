---
title: Set up the Dynamics 365 Commerce localization for Russia
description: This article explains how to set up the Microsoft Dynamics 365 Commerce localization for Russia.
author: EvgenyPopovMBS
ms.date: 09/21/2021
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: v-chgriffin
ms.search.region: Russia
ms.author: josaw
ms.search.validFrom: 2021-07-01
ms.dyn365.ops.version: 
ms.search.industry: Retail
---
# Set up the Dynamics 365 Commerce localization for Russia

[!include[banner](../includes/banner.md)]

This article explains how to set up the Microsoft Dynamics 365 Commerce localization for Russia.

The Dynamics 365 Commerce localization for Russia includes an extension of the point of sale (POS) components. This extension provides the option to work with simplified Russian address formats for retail customers.

For more information about the Commerce localization for Russia, see [Russian localization scope](../../finance/localizations/russia.md) and [Commerce localization for Russia](rus-commerce-localization.md).

## Enable Russia-specific Commerce functionality

This section describes how to configure Commerce headquarters settings that are specific to and recommended for Russia. For more information, see the [Commerce home page](../welcome.md).

To configure Commerce headquarters settings to enable and use Russia-specific functionality, follow these steps.

1. In the primary address of the legal entity, set the **Country/region** field to **RUS** (Russia).
1. In the POS functionality profile of every store that is located in Russia, set the **ISO** field to **RU** (Russia).
1. Go to **System administration \> Workspaces \> Feature management**.
1. On the **All** tab, turn on the **Enable Russian simplified customer address format** feature.

## Enable Russia-specific Commerce components

This section provides deployment guidance that will help you enable the components of the Commerce localization for Russia.
	
### Enable Modern POS extension components

To enable Modern POS extension components, follow these steps.

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**, and make sure that it can be compiled without errors. Additionally, confirm that you can run Modern POS from Visual Studio by using the **Run** command.

    > [!NOTE]
    > Modern POS must not be customized. You must enable User Account Control (UAC) and uninstall previously installed instances of Modern POS as required.

1. Enable the extensions to be loaded by adding the following lines in the **extensions.json** file.

    ```json
    {
        "extensionPackages": [
            {
                "baseUrl": "Microsoft/Addresses.RU"
            },
            {
                "baseUrl": "Microsoft/FiscalCustomer.RU"
            }
        ]
    }
    ```

    > [!NOTE]
    > For more information, and for samples that show how to include source code folders and enable extensions to be loaded, see the instructions in the readme.md file of the **Pos.Extensions** project.

1. Rebuild the solution.
1. Run Modern POS in the debugger, and test the functionality.

### Enable Cloud POS extension components

To enable the Cloud POS extension components to be loaded in the **extensions.json** file, add the following lines in the appropriate part of the file.

```json
{
    "extensionPackages": [
        {
            "baseUrl": "Microsoft/Addresses.RU"
        },
        {
            "baseUrl": "Microsoft/FiscalCustomer.RU"
        }
    ]
}
```	
	
## Set up parameters for cash management

To set up parameters for cash management, follow the steps described in [Set up for cash management for POS](emea-eeu-petty-cash-for-retail.md#set-up-for-cash-management-for-pos).
	
## Set up aggregation parameters for registering POS sales and return transactions

You can set up aggregation parameters that are used to aggregate POS sales and return transactions when those transactions are registered in Commerce. When you select the aggregation parameters, Commerce aggregates the positive sales quantities and negative return quantities for items that have identical inventory dimensions.

To set up the aggregation parameters in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters**.
1. On the **Posting** tab, in the **Aggregation** section, select the **Voucher transactions** checkbox to aggregate voucher transactions.
1. Select the **Sales and returns** checkbox to aggregate POS sales and return transactions.

    > [!NOTE]
    > The **Sales and returns** checkbox is available only if you select the **Voucher transactions** checkbox.

## Set up miscellaneous charges for customer order cancellations

To set up charges that can be applied to customer order cancellation operations in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters**.
1. On the **Customer order** tab, in the **Cancellation charge percentage** field, specify the required value.
1. Go to **Accounts receivable \> Charges setup \> Charges posting**.
1. Set up accounts so that you can apply and post charges for a customer order cancellation.

## Additional resources

[Commerce home page](../welcome.md)

[Russian localization scope](../../finance/localizations/russia.md)

[Petty cash management for Commerce for Eastern Europe](emea-eeu-petty-cash-for-retail.md)

[Commerce localization for Russia](rus-commerce-localization.md)
