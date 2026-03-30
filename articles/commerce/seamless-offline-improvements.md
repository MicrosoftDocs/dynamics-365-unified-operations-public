---
title: Seamless offline switch for gift card and credit memo operations
description: This article provides an overview of improvements that provide a seamless offline switch for specific payment types in Microsoft Dynamics 365 Commerce.
author: BrianShook
ms.date: 01/29/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 20120-02-28
ms.custom: 
  - bap-template
---

# Seamless offline switch for gift card and credit memo operations

[!include [banner](../finance/includes/banner.md)]

This article provides an overview of improvements that provide a seamless offline switch for specific payment types in Microsoft Dynamics 365 Commerce.

If a point of sale (POS) device loses its connection to the channel database, most POS operations and transactions that are in progress can proceed after the cashier receives a warning message about the loss of connectivity. However, in some cases, transactions have elements that rely on the real-time service, and those elements aren't supported when the POS is offline. This article describes some functionality that helps reduce the impact of lost connectivity in these scenarios.

## Completing gift card transactions in offline mode

Internal gift cards depend on the real-time service, because the balance for the gift cards must be centrally maintained in Microsoft Dynamics 365 Commerce Headquarters. To help prevent fraud or other synchronization problems, the system locks gift cards as soon as you add them to a transaction. The locking function ensures that a gift card can't be used on multiple terminals at the same time. When you complete a transaction, the system updates and unlocks the gift card.

However, if the POS loses connectivity after you add a gift card to a transaction, the gift card can become unusable. To help prevent this situation, Dynamics 365 Commerce has a parameter that enables transactions that include a gift card line to be completed while the POS is offline. When you turn on this parameter, the system saves gift card transactions that are forced offline together with offline transactions, and it syncs them to Commerce Headquarters when the offline transactions are synced. The synchronization also unlocks the gift card so that it can be used at another terminal.

To enable the functionality to conclude gift card transactions after switching to offline mode, go to the **Posting** tab on the **Commerce parameters** page. On that tab, locate the **Gift card** FastTab and set **Allow concluding gift card transactions in offline mode** to **Yes**.

:::image type="content" source="media/gift.png" alt-text="Screenshot of the offline gift card setting.":::

Typically, the system caches Commerce parameters. Therefore, after you update the setting of this parameter and initiate the distribution schedule to sync the change to the channel, the change can take up to 24 hours to take effect. To make the change effective immediately, reset Microsoft Internet Information Services (IIS).

## Completing credit memo transactions in offline mode

Like internal gift cards, Commerce headquarters centrally maintains credit memos. Commerce has a parameter that enables credit memo transactions to be completed while the POS is offline. This parameter works like the gift card parameter that was mentioned in the previous section. When you turn on the parameter, the system syncs credit memo transactions that are forced offline back to the channel database, together with other transactions that you performed while the POS was offline.

To enable the functionality to conclude credit memo transactions after switching to offline mode, go to the **Posting** tab on the **Commerce parameters** page. On that tab, locate the **Credit memo** FastTab and set **Allow concluding credit memo transactions in offline mode** to **Yes**.

:::image type="content" source="media/creditmemo.png" alt-text="Screenshot of the offline credit memo setting.":::

Typically, the system caches Commerce parameters. Therefore, after you update the setting of this parameter and initiate the distribution schedule to sync the change to the channel, the change can take up to 24 hours to take effect. To make the change effective immediately, reset IIS.

## Additional resources

[Offline point of sale (POS) functionality](dev-itpro/pos-offline-functionality.md)

[Online and offline point of sale (POS) operations](pos-operations.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
