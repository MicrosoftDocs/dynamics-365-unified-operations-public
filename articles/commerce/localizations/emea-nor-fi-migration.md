---
# required metadata

title: Migrate from legacy Commerce functionality for Norway
description: This article explains how to migrate from the legacy digital signing solution in the Microsoft Dynamics 365 Commerce localization for Norway to the solution that is based on the Commerce fiscal integration framework.
author: EvgenyPopovMBS
ms.date: 02/03/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Norway
ms.author: josaw
ms.search.validFrom: 2022-8-1

---

# Migrate from legacy Commerce functionality for Norway

[!include [banner](../includes/banner.md)]

This article explains how to migrate from the [legacy digital signing solution](./emea-nor-loc-deployment-guidelines.md) in the Microsoft Dynamics 365 Commerce localization for Norway to the solution that is based on the [Commerce fiscal integration framework](./emea-nor-fi-deployment.md).

If you're using the [legacy digital signing solution for Norway](./emea-nor-loc-deployment-guidelines.md) in Commerce version 10.0.28 or earlier, you must migrate to the [current Commerce fiscal integration solution](./emea-nor-fi-deployment.md) in Commerce version 10.0.29 or later to uptake the changes and receive timely updates for future Norway-specific features. No major changes are required in the extension logic that you created. However, because this update is a major update, some of your customizations will stop working unless changes are made on your side. Therefore, you should plan, prepare for, and complete the uptake for your environment.

## Migration process

The migration process from the legacy digital signing solution to the current fiscal integration solution is based on the concept of a gradual update. In other words, all Commerce headquarters and Commerce Scale Unit (CSU) components should already be updated before you start to update the point of sale (POS).

To help prevent scenarios where an event or transaction is signed twice (by both the legacy extension and the current extension), or where an event or transaction can't be signed because of an incorrect or incomplete configuration, we recommend that you turn off all POS devices that use the legacy solution and then update all of them simultaneously. For example, you can do this simultaneous update on a store-by-store basis, by updating each store's functionality profile.

To complete the migration process, follow these steps.

1. Update the Commerce headquarters components.
1. In Commerce headquarters, [configure the fiscal integration functionality for Norway](#configure-fiscal-integration).
1. Ensure that all offline transactions are uploaded from offline-enabled Store Commerce app devices to the channel database.
1. Close shifts, and sign out of all POS devices.
1. Update the Commerce Scale Unit components.
1. Update the POS components.
1. [Configure channel components](./emea-nor-fi-deployment.md#configure-channel-components).
1. In Commerce headquarters, [enable Norway-specific features](./emea-nor-cash-registers.md#enable-features-for-norway).
1. [Adjust receipt formats](#adjust-receipt-formats) so that they use updated custom fields.
1. [Enable the fiscal integration functionality](#enable-fiscal-integration).
1. Restart the POS.

### Configure fiscal integration

To configure the fiscal integration functionality for Norway, follow the steps in [Set up fiscal registration](./emea-nor-fi-deployment.md#set-up-fiscal-registration-for-norway) and [Configure the digital signature parameters](./emea-nor-fi-deployment.md#configure-the-digital-signature-parameters).

> [!IMPORTANT]
> At this point, don't enable fiscal integration on the **Commerce shared parameters** page.

### Adjust receipt formats

You must adjust your receipt formats so that they use updated custom fields. For up-to-date information about custom fields for Norway, see [Configure custom fields so that they can be used in receipt formats for sales receipts](./emea-nor-cash-registers.md#configure-custom-fields-so-that-they-can-be-used-in-receipt-formats-for-sales-receipts).

### Enable fiscal integration

When you're ready to enable the fiscal integration functionality in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**.
1. On the **General** tab, set the **Enable fiscal integration** option to **Yes**.
1. Go to **Retail and Commerce \> Channel setup \> POS setup \> POS profiles \> Functionality profiles**.
1. Select a functionality profile that is linked to the store where the registration process should be activated.
1. On the **Fiscal registration process** FastTab, select the fiscal registration process that you created earlier.
1. On the **Fiscal services** FastTab, select the connector technical profile that you created earlier.
1. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**.
1. Open the distribution schedule, and select jobs **1070** and **1090** to transfer data to the channel database.

> [!WARNING]
> After you complete the preceding steps, your previous customizations of the digital signing functionality will stop working.
