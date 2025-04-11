---
title: Production dispensing (preview)
description: Production Dispensing ensures compliance with regulated and controlled standards for dispensing ingredients and materials in production processes, particularly in industries such as life sciences and pharmaceuticals.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: SIGProcSetup, QMSScalesDevice, ProdParameters, EcoResProductDetailsExtended, ProdJournalName, QMSScalesDevice
ms.topic: how-to
ms.date: 04/25/2025
ms.custom: 
  - bap-template
---

# Production dispensing (preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

<!-- KFM: This needs to go into the TOC. But where? -->

When dealing with hazardous materials or sensitive components in production processes, accurate dispensing of materials is crucial. It minimizes the risk of contamination, preserves the integrity of the materials, and ensures the safety of both the product and personnel.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

Dispensing materials to a production order involves allocating and providing the necessary raw materials or components required for the production process. This is essential in certain environments for several reasons.

- In highly regulated industries, such as pharmaceuticals or chemicals, precise dispensing ensures compliance with strict guidelines and standards, maintaining product quality and safety. 
- When handling hazardous or sensitive materials, the dispensing process is often carried out in a clean room. In this controlled environment, a sealed box is transferred from the warehouse to the clean room, where it is unsealed and the materials are dispensed. After dispensing, the box is sealed again and returned to the warehouse. This process ensures that the materials remain uncontaminated and safe throughout the handling and dispensing stages
- For expensive materials, precise dispensing helps prevent waste and fraud, reducing costs and ensuring efficient resource utilization. Additionally, accurate dispensing contributes to consistent product quality, meeting customer expectations, and protecting workers and the environment by handling dangerous substances correctly.
To support the regulated dispensing process, you can:
- Set up thresholds for over and under dispensing. This ensures that the correct quantities are dispensed, maintaining compliance and quality.
- Configure the system to automatically return any remaining, un-dispensed material back to inventory.
- Restrict the dispensing process to workers who are authorized to perform it, ensuring that only trained and qualified personnel handle the materials.
- Set up requirements for workers to sign off the dispensed quantities using an electronic signature. An electronic signature is sometimes required to ensure the authenticity and integrity of a process. It provides a secure and verifiable way to confirm that the correct actions have been performed by authorized personnel, maintaining compliance with regulatory standards. Learn more about the use of electronic signatures here: [Electronic signatures overview](../../fin-ops-core/fin-ops/organization-administration/electronic-signature-overview.md)

Workers use the *Dispensing ticket* page to manage the dispensing of material to the production or batch order. On this page, they register and confirm the amount of material to be dispensed. After confirmation, the dispensed quantities are registered as consumed in the *Dispensing pick journal*. Materials that are not configured for dispensing on the production or batch order are issued through the production picking list journal.

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.44 or later.
- The following features must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). <!-- KFM: Confirm feature requirements -->
    - *(Preview) Advanced quality management*
    - *(Preview) Dispense management*

## Set up a dispensing pick journal

Set up a journal for dispensing materials to production and batch orders. Follow these steps to set up a journal.

1. Go to **Production control** \> **Setup** \> **Production journal names**.
1. Select **New** to create a new journal name for dispensing.
1. Enter a **Name** and **Description**.
1. Set **Dispensing tickets** to *Yes*.
1. Leave the all other settings at their default values.
1. On the Action Pane, select **Save**.

## Grant users access to production dispensing features

All users who should be able to dispense products in the production process must be assigned the *Production dispenser* security role. To assign the role, follow the following steps.

1. Go to **System administration** \> **Users** \> **Users**.
1. Open the user you want to enable for production dispensing.
1. In the **Users's roles** section select **Assign roles**.
1. From the list, select the role *Production dispenser* and select **OK**.

## Enable electronic signatures for production dispensing

To mandate electronic signatures for users posting the *Dispensing pick journal*, follow these steps.

1. Go to **Organization administration** \> **Setup** \> **Electronic signature** \> **Electronic signature requirements**.
1. On the list pane, select the row with a **Name** of *Post dispensing ticket production journal*.
1. Set **Signature required** to *Yes*.
1. On the list pane, select the row with a **Name** of *Post picking list production journal (non-dispensing)*.
1. Set **Signature required** to *Yes*.
1. On the Action Pane, select **Save**.

## Set up measuring devices

You can create a catalog of measuring devices used in the dispensing process. This will typically be a scale. Every dispense ticket can have a measuring device assigned to it, and you can set up a default device in the production control parameters. To create a measuring device, follow these steps.

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Measuring devices**
1. Use buttons in the action pane to add, edit, or delete a measuring device.
1. Make the following settings for your new or selected device
    - **Name**
    - **Description**
    - **Test instrument tag** – Unique identifier of the measuring device and lets you track it's calibration history. Learn more about instrument calibration in [Test instrument calibration (preview)](../inventory/quality-instrument-calibration.md).

## Set up production control parameters

Several settings on the **Production control parameters** page must be configured to enable production dispensing and configure how it works on your system. Follow these steps to set up the parameters.

1. Go to **Production control** \> **Setup** \> **Production control parameters**.
1. Open the **Standard update** tab and make the following settings:
    - **Enable dispensing for production** – Set to *Yes* to enable using production dispensing in a production flow.
    - **Allow over-dispensing with reverse pick** – Set to *Yes* to allow for the over-dispensing or over-picking of material and then have the remainder returned to inventory with an automatically generated pick list.
1. Open the **Journals** tab and make the following setting:
    - **Dispensing tickets** – Select the journal name you created for the dispensing pick journal. This is the default journal for dispensed products.
1. Open the **General** tab to make the following setting:
    - **Default measuring device** – Select the measuring device that should be defaulted in the **Dispense ticket** page.

## Set up a product for the dispensing process

To use a dispensing process, you must configure dispensing options for each relevant product.

> [!NOTE] 
> Only products that are not enabled for warehouse management processes (WMS) can be enabled for the dispensing process.

1. Go to **Product information management** \> **Products** \> **Released products**.
1. Create a new product or open an existing product that you want to set up for dispensing.
1. Expand the **Manage inventory** FastTab.
1. From the **Dispensing** field group, make the following settings.
    - **Dispensing control** – Set to *Yes* to enable dispensing control for the product.
    - **Underdispense** – Set the threshold in percent by which the dispensed quantity is allowed to be less than the proposed quantity. This configuration ensures that when workers enter the dispensed quantity in the **Dispensing ticket** on a production order, the system validates that the quantity does not fall below the defined threshold.
    - **Overdispense** – Set the threshold in percent by which the dispensed quantity is allowed to be larger than the proposed quantity. This configuration ensures that when workers enter the dispensed quantity in the **Dispensing ticket** on a production order, the system validates that the quantity does not go above the defined threshold.
    - **Authorized personnel** – Set to *Yes* to only allow workers who are assigned the *Production dispenser* security role to do dispensing.
  
> [!NOTE] 
> When you add a BOM or Formula line with a product enabled for dispensing, the above mentioned thresholds set for over- and under dispensing are inherited to the BOM or Formula line. On the BOM and Formula lines, you can override the inherited values. The overridden values on the BOM and formula lines will always be used in the validation of the dispensed quantity in the dispense process.

## Generate the dispensing ticket and dispensing pick journal

For a production or batch order with BOM or Formula lines enabled for dispensing, follow these steps to create the **Dispensing ticket** and **Dispensing pick journal**  

1. Go to **Production control** \> **Production orders** \> **All production orders**.
1. Select **New production order** or **New batch order** and make the following settings in the dialog.
    - **Item number** - Select a product with and approved BOM or formula version with items enabled for dispensing.
    - Leave all other fields in the dialog with its default value.
1. Select **OK** to create the order.
1. From the Action Pane, select **Estimate** to set the order in the *Estimated* state.
1. From the Action Pane, select **Release** and make the following settings in the **General** tab in the dialog.
    - **Picking list** - Select a name for the picking list from the drop down list.
    - **Dispensing tickets** - Select a name for the dispensing tickets from the drop down list.
1. Confirm the dialog with **OK** to move the order to the *Released* state.
1. In the Action Pane in the batch order page, select the **View** tab
1. In the **Journals** field group, select make the following selections.
    - **Dispensing ticket** - Opens the dispensing ticket that was created when the batch order was released.
    - **Dispensing pick journal** - Opens the dispensing pick journal that was created when the batch order was released.

## Working with the dispensing ticket and dispensing pick journal

After releasing the batch or production order as described in the previous sections, workers can open the **Dispensing ticket** to register the amount of materials dispensed for the order.

1. Open the **Dispensing ticket** from the **View** tab on the production or batch order.
1. In the **Journal** column, click on the journal that you want to open.
1. In the **Dispensing details** section, select **New** to create a new line for registering a dispensed quantity. If you are making multiple measurements of the same portion of the material you are dispensing, you can create a new line for each distinct measurement. 
1. In the Action Pane in the **Dispensing details** section, select **Post dispensed** to calculate the average value of the registered measurements. The calculated average value will be updated on the line item for the dispensed material in the **journal lines** section in the **Dispensed** field.  
1. In the Action Pane, select **Confirm** to transfer the value for the calculated dispensed quantity to the **Dispensing pick journal**.
1. In the Action Pane, you can select **Post** to post the **Dispensing pick journal** which will register the dispensed quantity as consumed in inventory.
1. Instead of posting the dispensing pick journal from the dispensing ticket, you can also post it directly fro the dispensing pick journal page. 

## Option to auto-create dispensing pick journal for reverting remaining material from the dispense process

By setting the **Allow over-dispensing with reverse pick** configuration as described in a previous section, the system can automatically generate a dispensing pick list that will reverse material that has been over-picked for the dispensing process. This can be relevant when you stage material in full handling unit, such as a container or bag, to the location where the dispensing operation is done. Follow these steps to use it, if you have set the option for **Allow over-dispensing with reverse pick** that is described in a previous section.

1. Generate the **Dispensing ticket** and **Dispense pick journal** by releasing the production or batch order as described in the previous step.
1. Select **Dispense pick journal** from the **View** tab on the order.
1. In the **Journal** column, click on the Journal you want to open.
1. In the **Journal lines** section, increase the quantity in the **Consumption** field to match the quantity of the material that you want to stage to the dispensing area.
1. Close the dispense pick journal.
1. Select **Dispensing ticket** from the **View** tab on the order.
1. In the **Dispensing details** section, select **New** to create lines for the measurements of the dispensed material.
1. Select **Post dispensed** to update the **Dispensed** field on the material line in the **Journal lines** section.
1. In the Action Pane, select **Confirm** to transfer the value from the calculated dispensed quantity to the **Dispensing pick journal**
1. In the Action Pane, select **Post** to post the **Dispense pick journal**
1. Navigate back to batch order page.
1. Under the **View** tab, select **All** in the **Journals** field group.
1. Select the journal with the description starting with *Dispensing adjustment for..*
1. Open the journal, and notice that the journal line has a negative quantity that is calculated as the difference between the quantity that was registered as staged and the quantity that was confirmed and posted as dispensed. 
1. Post this journal to update the inventory with the quantity that was over-picked for the dispense process.