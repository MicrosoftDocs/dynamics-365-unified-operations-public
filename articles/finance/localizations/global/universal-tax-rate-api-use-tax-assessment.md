---
title: Use tax assessment
description: Learn about the use tax assessment functionality, including overviews on the Accrue use tax option and the Adjust sales tax option.
author: Kai-Cloud
ms.author: kailiang
ms.topic: how-to
ms.date: 03/19/2026
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
audience: Application user
ms.search.region: Global
ms.search.validFrom: 2024-02-01
---

# Use tax assessment

[!INCLUDE[banner](../../includes/banner.md)]

Use tax assessment is a feature that US legal entities can use to calculate the tax liability for purchases that are subject to use tax. Use tax is a type of sales tax that applies when a taxable item is purchased from an out-of-state vendor or an online retailer that doesn't collect sales tax from the buyer. The buyer is responsible for paying the use tax to the state where the item is used, stored, or consumed.

By using the **Accrue use tax** option in Tax calculation parameters, US legal entities can comply with the tax laws and regulations of their states by automatically generating use tax transactions, based on the purchase transactions and the tax rates of the states.​

Enable the **Accrue use tax** option to activate the use tax assessment–related fields and functionality in Accounts Payable (AP) invoicing scenarios. After you enable it, the following fields and parameters are activated for use tax assessment.

- The **Vendor charged sales tax** field is available on the header of a vendor invoice. Use it to record the total sales tax amount that the vendor charges on the invoice. If you import the vendor invoice, the amount in the **Imported sales tax** field automatically carries over to the **Vendor charged sales tax** field.
- The **Accrue sales tax type** field is available in the vendor master and on the header of the vendor invoice. It controls the tax assessment process. Select one option for each vendor in the vendor master to set the default behavior for processing of the **Vendor charged sales tax** value. On the header of the vendor invoice, you can select a different behavior for each invoice transaction.

    - **Default** – Use the default behavior, which ignores the amount in the **Vendor charged sales tax** field. The system calculates and populates the sales tax amount and sales tax transactions through sales tax logic. No other assessment is done.
    - **[Adjust sales tax](#adjust-sales-tax)**
    - **Accrue use tax** – This option is available if you enabled the **Accrue use tax** option according to the guidance in [Configure a tax solution provider](./universal-tax-rate-api-configure-tax-solution-provider.md). The system populates use tax transactions when the **Vendor charged sale tax** value is less than the tax liability that your tax solution provider calculates. For more details, contact your tax solution provider.
    - **Advanced** – Select this option when your tax solution provider supports advanced use tax assessment processes that consider the fields in the **Overcharge tolerance** section. For more details, contact your tax solution provider.

- The fields in the **Overcharge tolerance** section are available in both Tax calculation parameters and the vendor master. Use them to perform advanced tax transaction handling when the **Vendor charged sales tax** value differs from the tax calculation result. For more details, contact your tax solution provider.

## Adjust sales tax

The **Adjust sales tax** option is available after you enable the **Adjust sales tax amount per vendor charged sales tax** feature (in version 10.0.39 and later). Select this option if you want to fully accept the sales tax amount that the vendor charges. In this case, the system generates a sales tax adjustment transaction to override the tax calculation result.

> [!NOTE]
> The **Adjust sales tax amount per vendor charged sales tax** feature is a standalone core feature. It doesn't require that you enable a tax solution provider. You can enable the feature to activate the **Vendor charged sales tax** and **Accrue sales tax type** fields without connecting to an external tax solution provider.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
