---
# required metadata

title: Master planning with purchase trade agreements
description: This topic describes how Planning Optimization can find the vendor and/or lead time for a planned order, based on the best price or lead time that is found in purchase trade agreements.
author: t-benebo
ms.date: 06/29/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ReqCreatePlanWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: benebotg
ms.search.validFrom: 2020-05-29
ms.dyn365.ops.version: AX 10.0.12

---
# Master planning with purchase trade agreements

[!include [banner](../../includes/banner.md)]

This topic describes how Planning Optimization can find the vendor and/or lead time for a planned order, based on the best price or lead time that is found among all purchase trade agreements that have been specified for a given product.

## Turn on the Purchase trade agreements for Planning Optimization feature

Before you can use this feature, it must be turned on in your system. Admins can use the [Feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace to check the status of the feature and turn it on if it's required. There, the feature is listed in the following way:

- **Module:** *Master planning*
- **Feature name:** *Purchase trade agreements for Planning Optimization*

## Prepare your system to evaluate purchase trade agreements during master planning

Follow these steps to configure your system to apply Planning Optimization that evaluates purchase trade agreements.

1. Go to **Master planning \> Setup \> Master planning parameters**. On the **Planned orders** tab, in the **Vendor** section, set the following values:

    - **Find trade agreement** – Set this option to **Yes** to include purchase trade agreements in master planning.
    - **Search criterion** – Select the factor that you want to prioritize for each purchase trade agreement: **Minimum lead time** or **Lowest unit price**.

1. Go to **Procurement and sourcing \> Setup \> Prices and discounts \> Activate price/discount**, and make sure that the **Vendor** option is set to **Yes**.
1. Go to **Product information management \> Setup \> Dimension and variant groups \> Storage dimension groups**, and select a storage dimension group that applies to products that master planning should evaluate purchase trade agreements for. Make sure that each relevant storage dimension in this group has a check mark in the **For purchase prices** column. Repeat this step for every other relevant storage dimension group.

## Prepare a released product to evaluate purchase trade agreements during master planning

After your system is prepared as described in the previous section, you should follow these steps to make sure that each product that you want to use with this feature is correctly set up.

1. Go to **Product information management \> Products \> Released products**, and open a target product.
1. On the **Purchase** FastTab, make sure that no vendor is assigned in the **Vendor** field.
1. On the Action Pane, on the **Plan** tab, in the **Coverage** group, select **Item coverage** to open the **Item coverage** page for the selected product. Verify the following settings:

    - On the **General** tab, you can set up vendor overrides. If you want Planning Optimization to use purchase trade agreements to select a vendor, you should prevent vendor overrides by clearing the **Use specific setting** check box.
    - On the **Lead time** tab, you can set up lead-time overrides. If you want Planning Optimization to use purchase trade agreements to select lead times, you should prevent lead-time overrides. Clear the check box for each type of lead time that you want to select by using purchase trade agreements (**Purchase**, **Production**, and/or **Transfer**).

1. Close the **Item coverage** page to return to the details page for the selected product.
1. On the Action Pane, on the **Plan** tab, in the **Forecast** group, select **Supply forecast** to open the **Supply forecast** page. Make sure that no row that is shown here has a value in the **Vendor account** column.
1. Close the **Supply forecast** page to return to the details page for the selected product.
1. On the Action Pane, on the **Purchase** tab, in the **Trade agreements** group, select **View trade agreements**. Make sure that all the relevant purchase trade agreements are listed. Also make sure that the **Disregard lead time** option is set to **No** for each agreement where you want Planning Optimization to use the lead time that is specified for that agreement.
1. On the Action Pane, on the **Plan** tab, in the **Order settings** group, select **Default order settings** to open the **Default order settings** page for the selected product. On the **Purchase order** FastTab, view the value of the **Purchase lead time** field. If no item coverage lead-time override is defined, Planning Optimization will use this value when it selects trade agreements where the **Disregard lead time** option is set to **Yes**. Therefore, you should adjust this value as you require.
1. Repeat this procedure for each relevant product.

> [!NOTE]
> Planning Optimization supports multi-currency purchase trade agreements. When searching for a trade agreement using the **Lowest unit price** option, the system will consider purchase trade agreement lines with different currencies provided an exchange rate has been defined between the trade agreement line currency and the accounting currency of the legal entity. Otherwise, the trade agreement line will be ignored, and you will see an error during master planning. Therefore, master planning will include information from all relevant purchase trade agreement lines where prices can be converted to the accounting currency. It is important to note that rounding rules will not be taken into account during the trade agreement line price conversion.

## Examples of how Planning Optimization finds vendor and lead times

The following table provides examples that show how various settings for a released product and its associated purchase trade agreements affect the values that are found for the resulting planned purchase order. The **bold** values in the two rightmost columns are the values that are selected by Planning Optimization. The ***bold and italic*** values in the other columns are the settings that produced those resulting values for each row.

| Released product: Vendor | Default order settings: Lead time | Item coverage: Override vendor | Item coverage: Override lead time | Trade agreement: Vendor | Trade agreement: Lead time | Trade agreement: Disregard lead time | Resulting vendor | Resulting lead time |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| ***US001*** | ***1*** | No | No | US003 | 3 | No | **US001** | **1** |
| US001 | 1 | ***Yes: US002*** | ***Yes: 2*** | US003 | 3 | No | **US002** | **2** |
| *(Blank)* | 1 | No | No | ***US003*** | ***3*** | No | **US003** | **3** |
| *(Blank)* | ***1*** | No | No | ***US003*** | 3 | Yes | **US003** | **1** |
| *(Blank)* | ***1*** | ***Yes: US002*** | No | US003 | 3 | No | **US002** | **1** |
| *(Blank)* | ***1*** | ***Yes: US002*** | No | US003 | 3 | No | **US002** | **1** |
| *(Blank)* | 1 | No | Yes: 2 | ***US003*** | ***3*** | No | **US003** | **3** |
| *(Blank)* | 1 | No | ***Yes: 2*** | ***US003*** | 3 | Yes | **US003** | **2** |

## Additional resources

[Purchase agreements](../../procurement/purchase-agreements.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
