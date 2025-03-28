---
title: Production dispensing
description: Production Dispensing ensures compliance with regulated and controlled standards for dispensing ingredients and materials in production processes, particularly in industries such as life sciences and pharmaceuticals.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 04/25/2025
ms.custom: 
  - bap-template
---

# Production dispensing

When dealing with hazardous materials or sensitive components, accurate dispensing minimizes the risk of contamination, preserving the integrity of the materials and ensuring the safety of both the product and personnel. 

Dispensing materials to a production order involves allocating and providing the necessary raw materials or components required for the production process. Production dispensing is essential in certain environments for several reasons. 

- In highly regulated industries, such as pharmaceuticals or chemicals, precise dispensing ensures compliance with strict guidelines and standards, maintaining product quality and safety.  
- When dealing with hazardous or sensitive materials, the dispensing process is often carried out in a clean room. In this controlled environment, a sealed box is transferred from the warehouse to the clean room, where it is unsealed and the materials are dispensed. After dispensing, the box is sealed again and returned to the warehouse. This process ensures that the materials remain uncontaminated and safe throughout the handling and dispensing stages. 
- For expensive materials, precise dispensing helps prevent waste and fraud, reducing costs and ensuring efficient resource utilization. Additionally, accurate dispensing contributes to consistent product quality, meeting customer expectations, and protecting workers and the environment by handling dangerous substances correctly.
- To support the regulated dispensing process, you can:
    - Set up thresholds for over and under dispensing. This ensures that the correct quantities are dispensed, maintaining compliance and quality.
    - Configure the system to automatically return any remaining, un-dispensed material back to inventory.
    - Restrict the dispensing process to workers who are authorized to perform it, ensuring that only trained and qualified personnel handle the materials.
    - Set up requirements for workers to sign off the dispensed quantities using an electronic signature. An electronic signature is sometimes required to ensure the authenticity and integrity of a process. It provides a secure and verifiable way to confirm that the correct actions have been performed by authorized personnel, maintaining compliance with regulatory standards. Learn more about the use of electronic signatures here: [Electronic signatures overview](../../fin-ops-core/fin-ops/organization-administration/electronic-signature-overview.md)
- Manage a mix of dispensed and non-dispensed items on a single production order. Non-dispensed products are registered as consumed in the production picking list journal. For items configured for the dispense process, the *Dispensing ticket* and *Dispensing pick journal* are used. Workers use the dispensing ticket to register and confirm the quantities of material dispensed to the production order, and the Dispensing pick journal is used to register the dispensed quantity as consumed.

This article describes how to set up and use production dispensing in Dynamics 365 Supply Chain Management.

## Set up a dispensing pick journal

Set up a journal for dispensing materials to production and batch orders. Follow these steps to set up a journal.

1. Go to **Production control > Setup > Production journal names**.
1. Select **New** to create a new journal name for dispensing.
1. Enter a **Name** and **Description**.
1. Set **Dispensing tickets** to *Yes*. 
1. Leave the all other settings at their default values.
1. On the Action Pane, select **Save**.

## Grant users access to production dispensing features

All users who should be able to dispense products in the production process must be assigned the *Production dispenser* security role. To assign the role, follow the following steps.

1. Go to **System administration > Users > Users**.
1. Open the user you want to enable for production dispensing.
1. In the **Users's roles** section select **Assign roles**.
1. From the list, select the role *Production dispenser* and select **OK**.

## Enable electronic signatures for production dispensing

To require electronic signatures from users that post the production picking list journal for dispensed and non-dispensed products, follow these steps.

1. Go to **Organization administration > Setup > Electronic signature > Electronic signature requirements**.
1. On the list pane, select the row with a **Name** of *Post dispensing ticket production journal*.
1. Set **Signature required** to *Yes*.
1. On the list pane, select the row with a **Name** of *Post picking list production journal (non-dispensing)*.
1. Set **Signature required** to *Yes*.
1. On the Action Pane, select **Save**.

## Set up measuring devices

You can create a catalog of measuring devices used in the dispensing process. This will typically be a scale. Every dispense ticket can have a measuring device assigned to it, and you can set up a default device in the production control parameters. To create a measuring device, follow these steps.

1. Go to **Inventory management > Setup > Quality control > Measuring devices**
1. Use buttons in the action pane to add, edit, or delete a measuring device.
1. Make the following settings for your new or selected device
    - **Name**
    - **Description**
    - **Test instrument tag** - Unique identifier of the measuring device and lets you track it's calibration history. Learn more about instrument calibration here: [Instrument Calibration](../inventory/quality-management/ConvertedFromWord/instrument-calibration.md).

## Set up production control parameters

Several settings on the **Production control parameters** page must be configured to enable production dispensing and configure how it works on your system. Follow these steps to set up the parameters.

1. Go to **Production control > Setup > Production control parameters**.
1. Open the **Standard update** tab.
1. Make the following settings:
    - **Enable dispensing for production** – Set to *Yes* to enable using production dispensing in a production flow.
    - **Allow over-dispensing with reverse pick** – Set to *Yes* to allow for the over-dispensing or over-picking of material and then have the remainder returned to inventory with an automatically generated pick list.
1. Open the **Journals** tab and make the following setting.
    - **Dispensing tickets** – Select the journal name you created for the dispensing pick journal. This is the default journal for dispensed products.
1. Open the **General** tab to make the following setting.
    - **Default measuring device** – Select the measuring device that should be defaulted in the **Dispense ticket** page <!-- KFM: Explain why we need to specify a measuring device here. What does this have to do with dispensing? --> . <!-- KFM: The **Dispense ticket** page is not described anywhere. What is it for? Should we have a section about this? --> If you have not defined a device, go to **Inventory management > Setup > Quality control > Measuring devices** to set it up <!-- KFM: The **Measuring devices** page is not described anywhere. What is it for? Is it added as part of this feature? Should we have a section about this? -->.  
1. On the Action Pane, select **Save**.

## Set up a product for the dispensing process

To use a dispensing process, you must configure dispensing options for each relevant product.

> [!NOTE]
> Only products enabled for warehouse management processes (WMS) can enabled for the dispensing process.

1. Go to **Product information management > Products > Released products**.
1. Open a product that you want to set up for dispensing.
1. Expand the **Manage inventory** FastTab.
1. From the **Dispensing** field group, make the following settings:
    - **Dispensing control** – Set to *Yes* to enable dispensing control for the product.
    - **Underdispense** – Enter the percentage by which the dispensed quantity is allowed to be less than the proposed quantity. <!-- KFM: Proposed by whom? How, where? -->
    - **Overdispense** – Enter the percentage by which the dispensed quantity is allowed to be larger than the proposed quantity. <!-- KFM: Proposed by whom? How, where? -->
    - **Authorized personnel** – Set to *Yes* to only allow authorized personnel to dispense materials for production. <!-- KFM: How do we know/control which users are authorized? -->
1. On the Action Pane, select **Save**.

## Set up BOM and formula lines for the dispensing process

On BOM and formula lines, you can override the thresholds for over and under dispensing. Follow these steps to override. <!-- KFM: We 0ny describe formulas in this procedure. Are BOMs set up differently? -->

1. Go to **Product information management > Products > Released products**.
1. Select a product that is configured for batch production.
1. On the Action Pane, open the **Engineer** tab and select **Formula versions**.
1. The **Formula versions** page opens. On this list pane, select the formula version you want to set up for dispensing.
1. On the Action pane, open the **Formulas** tab and select **Formula**.
1. The **Formula** page opens. Expand the **Formula lines** FastTab and select a line for which you want to set up dispensing options.
1. Expand the **Lines details** FastTab and open the **Setup** tab.
1. Under the **Dispensing** field group, make the following settings. <!-- KFM: These settings are read-only for me. Why?! -->
    - **Allow over-dispensing with reverse pick** – Set to *Yes* to allow for the over-dispensing or over-picking of material and then have the remainder returned to inventory with an automatically generated pick list.
    - **Overdispense** – Enter the percentage by which the dispensed quantity is allowed to be larger than the proposed quantity. This setting overrides the over-dispensing value specified for the released product.
    - **Underdispense** – Enter the percentage by which the dispensed quantity is allowed to be less than the proposed quantity. This setting overrides the under-dispensing value specified for the released product.
1. On the Action Pane, select **Save**.

## Example scenario: Using production dispensing

In a normal production run, workers use the production picking list journal to register the amount of materials consumed for a production order. For orders that have materials configured for dispensing, workers use the dispensing ticket journal to register the dispensed amounts prior to consumption. For orders using the dispensing process, the dispensing ticket and the production picking list journal can be configured to be created when the order is *Released*, as opposed to normal production runs, which creates the ticket and journal when the order is *Started*. The production dispensing feature also offers an option to return remaining material that was staged to the production area for dispensing. You enable this option in the production control parameters and on the product configured for dispensing.

The following scenario shows and example of how to use production dispensing where the picking list journal for non-dispensed products and the dispensing ticket for dispensed products are created at production order release. After completing the dispensing ticket, the system creates a picking list journal for the remaining material that was staged for the dispensing process.

1. Make sure the required settings for using production dispensing are set up as described in the previous sections.
1. Go to **Production control > Setup > Production control parameters**.
1. Open the **Standard update** tab and make the following setting.
    - **Allow over-dispensing with reverse pick** – Set to *true*.
1. Go to **Product information management > Products > Released products** and create a finished good with a bill of material that contains at least one product enabled for dispensing and one product that is not enabled for dispensing. <!-- KFM: Can we name a product from USMF that meets these requirements? I don't know how to set this up, which means I can't complete this procedure. -->
1. For the product enabled for dispensing, make the following settings.
    - **Allow over-dispensing with reverse pick** – Set to *true*.
    - **Overdispense** – Set to *10* percent.
    - **Underdispense** – Set to *10* percent.
1. Go to **Production control > Production orders > All production orders**.
1. Select **New production order** or **New batch order** to create a new order for the finished product defined previously.
1. Open or select the new production order. <!-- KFM: I think we need to do this here. -->
1. On the Action Pane, open the **Production order** tab and select **Estimate**. Select **OK** in the dialog to move the order to the *Estimated* state.
1. On the Action Pane, open the **Production order** tab and select **Release**. Make the following settings in the dialog. <!-- KFM: I don't see the following settings here, but it could be because I haven't set everything up right. -->
    - **Picking list** – Select a picking list.
    - **Dispensing ticket** – Select a dispensing ticket.

    > [!NOTE]
    > You can set up the journal names to default in **Default values** dialog. <!-- KFM: I'm not sure what this is referring to. -->

1. Select **OK** in the release dialog to confirm the release step for the order.
1. Return to the **All production orders** list page. Notice the values in the following two columns.
    - **Picking list status** = *Open*.
    - **Dispensing ticket status** = *Open*.

    These two fields indicate the existence of an un-posted picking list journal and an un-posted dispensing ticket. <!-- KFM: I don't see this.  -->

1. On the Action Pane, open the **View** tab and select **Dispensing pick journal**.
1. Open the relevant journal in the grid.
1. Change the quantity in the **Consumption** field to a value that is greater then the value in the **Proposal** field. The quantity in the **Consumption** field represents the amount of material you have staged to the process.
1. Close journal and return to the **All production orders** page.
1. Select the production order you are working with. On the Action Pane, open the **View** tab and select **Dispensing tickets**.  <!-- KFM: This is read-only for me. I couldn't get any further here.  -->
1. In the **Dispensing details** section, select **New** to create a new line for the dispensed quantity for the product. You can create multiple lines, which will then represents multiple measurements for the same dispensed amount.
1. Select **Post dispensed** to complete the registered values for dispensing. This process calculates the average of registered values and updates the **Dispensed** field for the product in the **Journal lines** section. You'll get an error in this process if the dispensed quantity exceeds the thresholds defined on the product.
1. When you have completed all the lines in the **Dispensing ticket**, select **Confirm** from the toolbar. This action updates the calculated value in the **Dispensed** field in the **Dispensing pick journal**.
1. After confirming the dispensed quantities, select **Post**, which posts the **Dispensing pick list** journal with the dispensed quantities. This action also creates a **Dispensing adjustment** journal with a proposal to return a quantity that equals the difference between the quantity that has been staged to the production order and the quantity that has been dispensed.
