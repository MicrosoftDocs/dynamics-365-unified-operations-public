---
title: Production dispensing
description: Learn how to use production dispensing to ensure compliance with regulated and controlled standards for dispensing ingredients and materials in production processes.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: SIGProcSetup, QMSScalesDevice, ProdParameters, EcoResProductDetailsExtended, ProdJournalName, QMSScalesDevice
ms.topic: how-to
ms.date: 04/25/2025
ms.custom: 
  - bap-template
---

# Production dispensing

[!include [banner](../../includes/banner.md)]

When you deal with hazardous materials or sensitive components in production processes, accurate dispensing of materials is crucial. It helps minimize the risk of contamination, preserve the integrity of the materials, and ensure the safety of both the product and personnel.

The processing of dispensing materials to a production order involves allocating and providing the raw materials or components that are required for the production process. It's essential in some environments, for several reasons:

- In highly regulated industries, such as pharmaceuticals or chemicals, precise dispensing ensures compliance with strict guidelines and standards, and helps maintain product quality and safety.
- When hazardous or sensitive materials are handled, the dispensing process is often performed in a type of controlled environment that is known as a clean room. A sealed box is transferred from the warehouse to the clean room. There, the box is unsealed, and the materials are dispensed. After dispensing is completed, the box is sealed again and returned to the warehouse. This process ensures that the materials remain uncontaminated and safe throughout the handling and dispensing stages.
- For expensive materials, precise dispensing helps prevent waste and fraud. Therefore, it reduces costs and ensures efficient resource use. Additionally, accurate dispensing contributes to consistent product quality. Therefore, it not only helps meet customer expectations but also protects workers and the environment by ensuring that dangerous substances are handled correctly.

To support the regulated dispensing process, you can take these actions:

- Set up thresholds for over-dispensing and under-dispensing. In this way, you help maintain compliance and quality by ensuring that the correct quantities are dispensed.
- Configure the system to automatically return any remaining, undispensed materials to inventory.
- Restrict the dispensing process to workers who are authorized to perform it. In this way, you ensure that only trained and qualified personnel handle the materials.
- Require that workers use an electronic signature to sign off on the dispensed quantities. An electronic signature helps ensure the authenticity and integrity of a process. It provides a secure and verifiable way to confirm that the correct actions were performed by authorized personnel. Therefore, it helps maintain compliance with regulatory standards. Learn more about electronic signatures in [Electronic signatures overview](../../fin-ops-core/fin-ops/organization-administration/electronic-signature-overview.md)

Workers use the **Dispensing ticket** page to manage the dispensing of materials to the production or batch order. On this page, they register and confirm the amount of material that must be dispensed. After confirmation, the dispensed quantities are registered as consumed in the *dispensing pick journal*. Materials that aren't configured for dispensing on the production or batch order are issued through the production picking list journal.

## Prerequisites

Before you can use the features that are described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.44 or later.
- The following features must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). As of Supply Chain Management version 10.0.47, both of these features are turned on by default.
    - *Advanced quality management*
    - *Dispense management*

## Set up a dispensing pick journal

To set up a journal for dispensing materials to production and batch orders, follow these steps:

1. Go to **Production control** \> **Setup** \> **Production journal names**.
1. Select **New** to create a journal name for the dispensing pick journal.
1. Enter a name and a description.
1. Set the **Dispensing tickets** option to *Yes*.
1. Leave the all other fields set at their default value.
1. On the Action Pane, select **Save**.

## Grant users access to production dispensing features

All users who should be able to dispense products in the production process must have the *Production dispenser* security role assigned to them. To assign this role to a user, follow these steps:

1. Go to **System administration** \> **Users** \> **Users**.
1. Open the user that you want to enable for production dispensing.
1. In the **User's roles** section, select **Assign roles**.
1. In the list, select the *Production dispenser* role.
1. Select **OK**.

## Require electronic signatures for production dispensing

To require an electronic signature when users post the dispensing pick journal, follow these steps:

1. Go to **Organization administration** \> **Setup** \> **Electronic signature** \> **Electronic signature requirements**.
1. In the list pane, select the row where the **Name** field is set to *Post dispensing ticket production journal*.
1. Set the **Signature required** option to *Yes*.
1. In the list pane, select the row where the **Name** field is set to *Post picking list production journal (non-dispensing)*.
1. Set the **Signature required** option to *Yes*.
1. On the Action Pane, select **Save**.

## Set up measuring devices

You can create a catalog of measuring devices that are used in the dispensing process. These devices are typically scales. Every dispensing ticket can have a measuring device assigned to it. In the production control parameters, you can set up a default device. To set up a measuring device, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Measuring devices**.
1. Use the buttons on the Action Pane to add a new measuring device or edit an existing one. (You can also delete an existing device.)
1. For the new or selected measuring device, set the following fields:

    - **Name**
    - **Description**
    - **Test instrument tag** – Specify a unique identifier for the measuring device. You can use this ID to track the device's calibration history. Learn more about instrument calibration in [Test instrument calibration](../inventory/quality-instrument-calibration.md).

## Set up production control parameters

To enable production dispensing and configure how it works in your system, you must configure several settings on the **Production control parameters** page. To configure the required production control parameters, follow these steps:

1. Go to **Production control** \> **Setup** \> **Production control parameters**.
1. On the **Standard update** tab, set the following fields:

    - **Enable dispensing for production** – Set this option to *Yes* to enable production dispensing to be used in a production flow.
    - **Allow over-dispensing with reverse pick** – Set this option to *Yes* to enable material to be over-dispensed or over-picked, and any remainder to be returned to inventory through an automatically generated pick list.

1. On the **Journals** tab, in the **Dispensing tickets** field, select the journal name that you created for the dispensing pick journal. This journal is the default journal for dispensed products.
1. On the **General** tab, in the **Default measuring device** field, select the measuring device that should appear by default on the **Dispensing ticket** page.

## Set up a product for the dispensing process

To use a dispensing process, you must configure dispensing options for each relevant product.

> [!NOTE]
> Products that are enabled for warehouse management processes (WMS) can't be enabled for the dispensing process.

To set up a product for the dispensing process, follow these steps:

1. Go to **Product information management** \> **Products** \> **Released products**.
1. Create a new product, or open an existing product that you want to set up for dispensing.
1. On the **Manage inventory** FastTab, in the **Dispensing** section, set the following fields:

    - **Dispensing control** – Set this option to *Yes* to enable dispensing control for the product.
    - **Underdispense** – Define the under-dispending threshold. In other words, specify the percentage by which the dispensed quantity can be less than the proposed quantity. In this way, when workers enter the dispensed quantity in the dispensing ticket on a production order, the system validates that the quantity doesn't fall below the defined threshold.
    - **Overdispense** – Define the over-dispensing threshold. In other words, specify the percentage by which the dispensed quantity can exceed the proposed quantity. In this way, when workers enter the dispensed quantity in the dispensing ticket on a production order, the system validates that the quantity doesn't go above the defined threshold.
    - **Authorized personnel** – Set this option to *Yes* to allow only workers who have the *Production dispenser* security role to perform dispensing.

> [!NOTE]
> When you add a bill of materials (BOM) or formula line that includes a product that is enabled for dispensing, that line inherits the item's over-dispensing and under-dispensing thresholds. However, you can override the inherited values on the BOM or formula line. The new values are then used when the dispensed quantity is validated during the dispensing process.

## Generate the dispensing ticket and dispensing pick journal

To create the dispensing ticket and dispensing pick journal for a production or batch order where BOM or formula lines are enabled for dispensing, follow these steps:

1. Go to **Production control** \> **Production orders** \> **All production orders**.
1. Select **New production order** or **New batch order**.
1. In the dialog, in the **Item number** field, select a product that has an approved BOM or formula version where items are enabled for dispensing.
1. Leave all other fields in the dialog set at their default value.
1. Select **OK** to create the order.
1. On the Action Pane, select **Estimate** to move the order to the *Estimated* state.
1. On the Action Pane, select **Release**.
1. In the dialog, on the **General** tab, set the following fields:

    - **Picking list** – Select a name for the picking list.
    - **Dispensing tickets** – Select a name for the dispensing ticket.

1. Select **OK** to close the dialog and move the order to the *Released* state.
1. On the batch order page, on the Action Pane, on the **View** tab, in the **Journals** group, select the following buttons:

    - **Dispensing ticket** – Open the dispensing ticket that was created when the batch order was released.
    - **Dispensing pick journal** – Open the dispensing pick journal that was created when the batch order was released.

## Work with the dispensing ticket and dispensing pick journal

After the batch or production order is released as described in previous sections, workers can open the dispensing ticket to register the amount of material that is dispensed for the order.

1. On the production or batch order page, on the Action Pane, on the **View** tab, in the **Journals** group, select **Dispensing ticket**.
1. In the **Journal** column, select the journal that you want to open.
1. In the **Dispensing details** section, select **New** to create a line for registering a dispensed quantity. If you're making multiple measurements of the same portion of the material that you're dispensing, you can create a separate line for each measurement.
1. Select **Post dispensed** to calculate the average value of the registered measurements. In the **Journal lines** section, the **Dispensed** field of the line item for the dispensed material is updated with the calculated average value.
1. On the Action Pane, select **Confirm** to transfer the value for the calculated dispensed quantity to the dispensing pick journal.
1. On the Action Pane, select **Post** to post the dispensing pick journal. The dispensed quantity is registered as consumed in inventory.

    > [!NOTE]
    > Instead of posting the dispensing pick journal from the dispensing ticket, you can post it directly from the dispensing pick journal page.

## Automatically create a dispensing pick journal to revert remaining material from the dispensing process

If you set the **Allow over-dispensing with reverse pick** option to *Yes* as described in the [Set up production control parameters](#set-up-production-control-parameters) section, the system can automatically generate a dispensing pick list to reverse material that was over-picked for the dispensing process. This capability can be relevant when you stage materials in full handling units, such as a container or bag, to the location where the dispensing process is performed.

To have any remainder from over-dispensed or over-picked material returned to inventory through an automatically generated pick list, follow these steps:

> [!NOTE]
> Before you begin, ensure that the **Allow over-dispensing with reverse pick** option is set to *Yes* on the **Production control parameters** page.

1. Generate the dispensing ticket and dispensing pick journal by releasing the production or batch order as described in previous sections.
1. On the production or batch order page, on the Action Pane, on the **View** tab, in the **Journals** group, select **Dispensing pick journal**.
1. In the **Journal** column, select the journal that you want to open.
1. In the **Journal lines** section, in the **Consumption** field, increase the value so that it matches the quantity of the material that you want to stage to the dispensing area.
1. Close the dispensing pick journal.
1. On the order page, on the **View** tab, select **Dispensing ticket**.
1. In the **Dispensing details** section, select **New** to create lines for the measurements of the dispensed material.
1. Select **Post dispensed**. In the **Journal lines** section, the **Dispensed** field on the material line is updated.
1. On the Action Pane, select **Confirm** to transfer the value for the calculated dispensed quantity to the dispensing pick journal.
1. On the Action Pane, select **Post** to post the dispensing pick journal.
1. Return to the order page.
1. On the Action Pane, on the **View** tab, in the **Journals** group, select **All**.
1. Select the journal where the description starts with "Dispensing adjustment for."
1. Open the journal, and notice that the journal line has a negative quantity. This quantity was calculated as the difference between the quantity that was registered as staged and the quantity that was confirmed and posted as dispensed.
1. Post the journal to update the inventory with the quantity that was over-picked for the dispensing process.
