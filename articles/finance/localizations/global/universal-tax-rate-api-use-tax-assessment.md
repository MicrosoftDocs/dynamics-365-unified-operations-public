---
title: Use tax assessment
description: This article explains the use tax assessment functionality.
author: Kai-Cloud
ms.date: 12/15/2023
ms.topic: overview
ms.prod: 
ms.technology: 
audience: Application user
ms.reviewer: 
ms.search.region: Global
ms.author: kailiang
ms.search.validFrom: 2024-02-01
ms.dyn365.ops.version: 10.0.39
ms.search.form: 
---

# Use tax assessment

Use tax assessment is a feature that allows USA legal entities to calculate the tax liability for purchases that are subject to use tax. Use tax is a type of sales tax that applies when a taxable item is purchased from an out-of-state vendor or an online retailer that does not collect sales tax from the buyer. The buyer is responsible for paying the use tax to the state where the item is used, stored, or consumed. Accrue use tax helps US legal entities to comply with the tax laws and regulations of their states by automatically generating use tax transactions based on the purchase transactions and the tax rates of the states.​

1. Enable the **Accrue use tax** option to activate the use tax assessment related fields and functionalities in AP invoicing scenarios. Once enabled, the following fields and parameters shall be activated for use tax assessment.
    - The **Vendor charged sales tax** field is on the header of a vendor invoice. You can record the total sales tax amount that is charged by the vendor invoice in this field. If the vendor invoice is imported, the amount in the **IMPORTED SALES TAX** field will be automatically carried to the **Vendor charged sales tax** field.
    - The **Accrue sales tax type** parameter is introduced in the vendor master and the header of the vendor invoice to control the tax assessment process. Select one option for each vendor in the vendor master to set the default behavior of processing the **Vendor charged sales tax**. On the header of the vendor invoice, you may change the option to select a different behavior per each invoice transaction:
        - **Default**
        This is the default behavior which ignores the amount in the **Vendor charged sales tax**. The sales tax amount and sales tax transactions will be calculated and populated via sales tax logic without other assessment.
        - **[Adjust sales tax](#adjust-sales-tax)**

        - **Accrue use tax**
            This option is available when you enabled the **Accrue use tax** parameter following the guidance of [configure tax solution provider](./universal-tax-rate-api-configure-tax-solution-provider.md). Use tax transactions will be populated when the **Vendor charged sale tax** is lower than the tax liability calculated by your tax solution provider. Check by your tax solution provider to get more details.
        - **Advanced**
            Select this option when your tax solution provider support advanced use tax assessment processes with **OVERCHARGE TOLERANCE** consideration. Check by your tax solution provider to get more details.
    - The fields in **OVERCHARGE TOLERANCE** parameter group are introduced in the **Tax calculation parameters** as well as in the vendor master to perform advanced tax transaction handling when the amount of **vendor charged sales tax** is different than the tax calculation result. Check by your tax solution provider to get more details.

## Adjust sales tax

This option is available after you enabled the **Adjust sales tax amount per vendor charged sales tax** feature (in 10.0.39 and above). Select this option when you want to fully accept the vendor charged sales tax amount. It will create the sales tax adjustment transaction which overrrides the tax calculation result.
> [!Note]
> The **Adjust sales tax amount per vendor charged sales tax** feature is a standalone core feature which does not depend on enabling the **tax solution provider**. You can enable the feature to activate **Vendor charged sales tax** and **Accrue sales tax type** already without connecting to an external tax solution provider.
