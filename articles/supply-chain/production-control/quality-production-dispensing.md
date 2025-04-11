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

To require electronic signatures from users that post the production picking list journal for dispensed and non-dispensed products, follow these steps.

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
1. Open the **Standard update** tab.
1. Make the following settings:
    - **Enable dispensing for production** – Set to *Yes* to enable using production dispensing in a production flow.
    - **Allow over-dispensing with reverse pick** – Set to *Yes* to allow for the over-dispensing or over-picking of material and then have the remainder returned to inventory with an automatically generated pick list.
1. Open the **Journals** tab and make the following setting.
    - **Dispensing tickets** – Select the journal name you created for the dispensing pick journal. This is the default journal for dispensed products.
1. Open the **General** tab to make the following setting.
    - **Default measuring device** – Select the measuring device that should be defaulted in the **Dispense ticket** page.
1. On the Action Pane, select **Save**.

## Set up a product for the dispensing process

To use a dispensing process, you must configure dispensing options for each relevant product.

> [!NOTE] > Only products enabled for warehouse management processes (WMS) can enabled for the dispensing process.

1. Go to **Product information management** \> **Products** \> **Released products**.
1. Open a product that you want to set up for dispensing.
1. Expand the **Manage inventory** FastTab.
1. From the **Dispensing** field group, make the following settings:
    - **Dispensing control** – Set to *Yes* to enable dispensing control for the product.
    - **Underdispense** – Set the threshold in percent by which the dispensed quantity is allowed to be less than the proposed quantity. This configuration ensures that when workers enter the dispensed quantity in the dispense ticket on a production order, the system validates that the quantity does not fall below the defined threshold.
    - **Overdispense** – et the threshold in percent by which the dispensed quantity is allowed to be larger than the proposed quantity. This configuration ensures that when workers enter the dispensed quantity in the dispense ticket on a production order, the system validates that the quantity does not go above the defined threshold.
    - **Authorized personnel** – Set to *Yes* to only allow workers who are assigned the Production dispenser security role to do dispensing.

## Set up BOM and formula lines for the dispensing process

On BOM and formula lines, you can override the thresholds for over and under dispensing. Follow these steps to override. 

1. Go to **Product information management** \> **Products** \> **Released products**.
1. Select a product that is configured for batch production.
1. On the Action Pane, open the **Engineer** tab and select **Formula versions**.
1. The **Formula versions** page opens. On this list pane, select the formula version you want to set up for dispensing.
1. On the Action pane, open the **Formulas** tab and select **Formula**.
1. The **Formula** page opens. Expand the **Formula lines** FastTab and select a line for which you want to set up dispensing options.
1. Expand the **Lines details** FastTab and open the **Setup** tab.
1. Under the **Dispensing** field group, make the following settings. 
    - **Allow over-dispensing with reverse pick** – Set to *Yes* to allow for the over-dispensing or over-picking of material and then have the remainder returned to inventory with an automatically generated pick list.
    - **Overdispense** – Enter the percentage by which the dispensed quantity is allowed to be larger than the proposed quantity. This setting overrides the over-dispensing value specified for the released product.
    - **Underdispense** – Enter the percentage by which the dispensed quantity is allowed to be less than the proposed quantity. This setting overrides the under-dispensing value specified for the released product.
1. On the Action Pane, select **Save**.

## Example scenario: Using production dispensing

The following scenario shows and example of how to use production dispensing where the picking list journal for non-dispensed products. This procedure use the USPI demo data.

1. Open Supply Chain Management and select the USPI demo data company.
1. Make sure the required settings for using production dispensing are set up as described in the previous sections.
1. Go to **Production control** \> **Setup** \> **Production control parameters**.
1. Open the **Standard update** tab and make the following setting.
    - **Allow over-dispensing with reverse pick** – Set to *true*.
1. Go to **Product information management** \> **Products** \> **Released products**
1. Enable a product for dispensing as described in previous the sections. Make sure the product has the following setting for dispensing
    - **Allow over-dispensing with reverse pick** – Set to *true*.
    - **Overdispense** – Set to *10* percent.
    - **Underdispense** – Set to *10* percent.
1. In the released products list page set a filter on product *P4000*.
1. In the action pane, under the Engineer tab, select Formula versions.
1. In the action pane, under the Formula tab, select Formula.
1. In the Formula lines section, select New to and add the product enabled for dispensing to the formula for product *P4000*.
1. Go to **Production control** \> **Production orders** \> **All production orders**.
1. Select **New production order** or **New batch order** to create a new order for product *P4000*.
1. On the Action Pane, open the **Production order** tab and select **Estimate**. Select **OK** in the dialog to move the order to the *Estimated* state.
1. On the Action Pane, open the **Production order** tab and select **Release**. Make the following settings in the dialog. <!-- 
    - **Picking list** – Select a picking list.
    - **Dispensing ticket** – Select a dispensing ticket.
1. Select **OK** in the release dialog to confirm the release step for the order.
1. Return to the **All production orders** list page. Notice the values in the following two columns.
    - **Picking list status** = *Open*.
    - **Dispensing ticket status** = *Open*.
1. On the Action Pane, open the View tab and select **Dispensing pick journal**.
1. Open the relevant journal in the grid.
1. Change the quantity in the **Consumption** field to a value that is greater then the value in the **Proposal** field. The quantity in the **Consumption** field represents the amount of material you have staged to the process.
1. Close journal and return to the **All production orders** page.
1. Select the production order you are working with. On the Action Pane, open the **View** tab and select **Dispensing tickets**.  
1. In the **Dispensing details** section, select **New** to create a new line for the dispensed quantity for the product. You can create multiple lines, which will then represents multiple measurements for the same dispensed amount.
1. Select **Post dispensed** to complete the registered values for dispensing. This process calculates the average of registered values and updates the **Dispensed** field for the product in the **Journal lines** section. You'll get an error in this process if the dispensed quantity exceeds the thresholds defined on the product.
1. When you have completed all the lines in the **Dispensing ticket**, select **Confirm** from the toolbar. This action updates the calculated value in the **Dispensed** field in the **Dispensing pick journal**.
1. After confirming the dispensed quantities, select **Post**, which posts the **Dispensing pick list** journal with the dispensed quantities. This action also creates a **Dispensing adjustment** journal with a proposal to return a quantity that equals the difference between the quantity that has been staged to the production order and the quantity that has been dispensed.
