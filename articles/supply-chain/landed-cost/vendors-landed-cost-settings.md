---
title: Vendor settings added for Landed cost
description: Learn about the new fields that are added to the existing Vendors page when you enable the Landed cost module, including a table that defines various fields.
author: lisascholz
ms.author: lisascholz
ms.topic: article
ms.date: 12/07/2020
ms.custom:
ms.reviewer: kamaybac
ms.search.form: VendTable
---

# Vendor settings added for Landed cost

[!include [banner](../../includes/banner.md)]

When you enable the **Landed cost** module, several new fields are added to the existing **Vendors** page. You use these fields to set up the vendors that you will use together with Landed cost features.

To set the relevant fields, go to **Procurement and sourcing \> Vendors \> All vendors**. Open an existing vendor, or create a new vendor, and then select the **Miscellaneous details** FastTab. All the new fields that the **Landed cost** module adds appear under the **Voyages** heading. The following table describes these fields.

| Field | Description |
|---|---|
| Shipping type | <p>Select the vendor's role in relation to Landed cost:</p><ul><li>**None** – The vendor has no specific role that is related to Landed cost. This value is the default setting, because most vendors will probably have no specific role.</li><li>**Shipping company** – The vendor is a shipping company. Vendors that have this shipping type are available for selection in the **Shipping company** field on the **Voyages** page.</li><li>**Customs broker** – The vendor is a customs broker. Vendors that have this shipping type are available for selection in the **Customs broker** field on the **Folios** page.</li><li>**Agent** – The vendor is an agent. Vendors that have this shipping type are available for selection in the **Agent** field on the **Vendors** and **Purchase orders** pages.</li></ul> |
| Cost type group | Assign the vendor to a cost type group for the purpose of selecting [auto costs](auto-cost-setup.md). |
| From port | Select the port of origin for the voyage. |
| Agent | The default agent when purchases are made from the vendor. |
| Import costing vendor | <p>Indicate whether the vendor is a Landed cost vendor.</p><p>**Tip:** You can use this field together with record-level security to limit the purchase orders that are shown when a voyage is created.</p> |
| Shipping company | Select the default shipping company that is used when purchase orders are created for the vendor. |
| Services provider | Indicate whether the vendor is services provider. |
| Over/Under tolerance group | Select the default over/under tolerance group for the vendor. |
