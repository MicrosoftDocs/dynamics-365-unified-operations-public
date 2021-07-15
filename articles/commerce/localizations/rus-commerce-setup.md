---
# required metadata

title: Set up the Dynamics 365 Commerce localization for Russia
description: This topic covers how to set up the Microsoft Dynamics 365 Commerce localization for Russia.
author: akviklis@microsoft.com
ms.date: 07/02/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Developer
# ms.devlang: 
ms.reviewer:
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
ms.search.industry: Retail
ms.author: akviklis
ms.search.validFrom: 07/01/2021
ms.dyn365.ops.version: 

---
# Set up the Dynamics 365 Commerce localization for Russia

[!include[banner](../includes/banner.md)]

This topic covers how to set up the Microsoft Dynamics 365 Commerce localization for Russia.

The Dynamics 365 Commerce localization for Russia includes an extension of the point of sale (POS) component. This extension provides you a possibility to work with Russian address format in a simplified way for retail customers.

For more information about the Commerce localization for Russia, see [Russian localization scope](../../finance/localizations/russia.md) and [Commerce localization for Russia](rus-commerce-localization.md).

## Enable Russia-specific Commerce functionality

This section describes how to configure Commerce headquarters settings that are specific to and recommended for Russia. For more information, see the [Commerce home page](../index.md).

To enable and use the Russia-specific functionality, you must configure the following settings in Commerce headquarters.

1. In the primary address of the legal entity, set the **Country/region** field to **RUS** (Russia).
1. In the POS functionality profile of every store that is located in Russia, set the **ISO** field to **RU** (Russia).
1. Go to **System administration \> Workspaces \> Feature management**, and then, on the **All** tab, enable the following feature keys:

    - Enable Russian simplified customer address format.

## Enable Russia-specific Commerce components

This section provides deployment guidance that will help you enable Commerce components of the Commerce localization for Russia.
	
### Enable Modern POS extension components

To enable Modern POS extension components, follow these steps.

1. Open the solution at **RetailSdk\\POS\\ModernPOS.sln**, and make sure that it can be compiled without errors. Additionally, confirm that you can run Modern POS from Visual Studio by using the **Run** command.

    > [!NOTE]
    > Modern POS must not be customized. You must enable User Account Control (UAC), and you must uninstall previously installed instances of Modern POS as required.

1. Enable the extensions to be loaded by adding the following lines in the **extensions.json** file.

    ```json
    {
        "extensionPackages": [
            {
                "baseUrl": "Microsoft/Addresses.RU"
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
        }
    ]
}
```	
	
## Set up micsellaniuos charges for customer order cancellations

To set up charges that can be appiled to customer order cancellation operations, follow these steps.

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters**.
1. On the **Customer order** tab, in the **Cancellation charge percentage** field, specify the required value.
1. Go to **Accounts receivable \> Charges setup \> Charges posting**.
1. Set up accounts so that you can apply and post charges for a customer order cancellation. 

## Set up aggregation parameters for registering POS sales and return transactions
You can set up the aggregation parameters that are used to aggregate the point of sale (POS) sales and return transactions when the transactions are registered in Microsoft Dynamics 365 Commerce. 
When you select the aggregation parameters, Microsoft Dynamics 365 Commerce aggregates the positive sales quantities and negative return quantities for items that have identical inventory dimensions.

Use this procedure to set up the aggregation parameters that are used to aggregate POS sales and return transactions in Microsoft Dynamics 365 Commerce.

1.  Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters**.
1.  Under the **Posting** tab, in the **Aggregation** field group, select the **Voucher transactions** check box to aggregate voucher transactions.
1.  Select the **Sales and returns** check box to aggregate POS sales and return transactions.
    
    > [!NOTE]
    > This check box is available only if you select the **Voucher transactions** check box.


## Additional resources

[Commerce home page](../index.md)

[Russian localization scope](../../finance/localizations/russia.md)

[Commerce localization for Russia](rus-commerce-localization.md)