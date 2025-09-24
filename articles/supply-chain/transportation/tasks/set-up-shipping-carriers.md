---
title: Set up shipping carriers
description: Learn how to set up a shipping carrier and define details such as service, shipment mode, transportation tender, transportation constraints, and shipping rate.
author: lisascholz91
ms.author: lisascholz
ms.reviewer: kamaybac
ms.search.form: TMSShippingCarrierCustomerAccount,TMSCarrier
ms.topic: how-to
ms.date: 07/31/2025
ms.custom:
  - bap-template
---

# Set up shipping carriers

[!include [banner](../../includes/banner.md)]

This article shows how to set up a shipping carrier and define details such as service, shipment mode, transportation tender, transportation constraints, and shipping rate. A transportation coordinator can then assign a shipping carrier to an inbound or outbound load.

## Create a new shipping carrier

1. Go to **Transportation management > Setup > Carriers > Shipping carriers**.
1. Select **New** on the Action Pane.
1. In the **Shipping carrier** field, type a value.
1. In the **Name** field, type a value.
1. In the **Mode** field, select an option from the drop-down menu.

## Fill in the general information for the shipping carrier

1. Toggle the expansion of the **Overview** section.
1. Check or uncheck the **Activate shipping carrier** checkbox.
1. In the **Vendor account** field, select an option from the drop-down menu. Select the vendor account to assign the shipping carrier to.  
1. In the **Transportation tender type** field, select an option. Select **Manual** to use the Transportation Tender page, or select **EDI** to update the tender by using Electronic Data Interchange (EDI).  
1. Check or uncheck the **Activate carrier rating** checkbox.

> [!NOTE]
> It's possible to confirm shipment of a load that doesn't have a rating applied (for example, if no rate is assigned to it).

## <a name="create-carrier-services"></a>Create the necessary services for the shipping carrier

1. Toggle the expansion of the **Services** section.
1. Select **New**.
1. In the **Carrier service** field, type a value.
1. In the **Name** field, type a value.
1. In the **Load template ID** field, select a load template to associate with the service. The load template defines the maximum measurements for weight and volume of an entire load. For example, the load template might represent the size of a container or truck. Load template IDs are also specified in load building templates and when using the [load building workbench](load-building-workbench.md), which helps you apply load building strategies to create loads. As a result, the system is able to match each new load to a suitable shipping carrier service by comparing the specified load template IDs.
1. In the **Transportation method** field, select an option from the drop-down menu.

## Set up the address for the carrier (optional)

1. Toggle the expansion of the **Addresses** section.
1. Select **New**.
1. In the **Name or description** field, type a value.
1. In the **Country/region** field, select an option from the drop-down menu.
1. In the **ZIP/postal code** field, select an option from the drop-down menu.
1. In the **Street** field, type a value.
1. Select **OK**.

## Set up the rating profile for the shipping carrier

1. Toggle the expansion of the **Rating profiles** section.
1. Select **New**.
1. In the **Rating profile** field, type a value.
1. In the **Name** field, type a value.
1. In the **Site** field, select an option from the drop-down menu.
1. In the **Warehouse** field, select an option from the drop-down menu.
1. In the **Rate engine** field, select an option from the drop-down menu. Select the Rate engine that is in accordance with the contract that you have with the carrier.  
1. In the **Rate master** field, select an option from the drop-down menu.
1. In the **Transit time engine** field, select an option from the drop-down menu.
1. Select **Save**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]