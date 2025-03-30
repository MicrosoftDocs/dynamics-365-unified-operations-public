---
title: 
description: 
ms.date: 04/25/2025
ms.topic: how-to
ms.service: 
author: johanhoffmann
ms.author: johanho
manager: 
---

# Customer specific certificate of analysis (COA)

Supply Chain Management provides the ability to create a basic Certificate of Analysis (COA) from the quality order or from the menu directly after selecting a quality order. Learn more about how to use the basic COA here: [Quality orders](quality-orders.md)

This article describes how you can vary the content of the COA to meet customer specific requirement and automatically print the COA when issuing a sales order packing slip. The customer specific COA has the following main components:

## Setting up a COA customer group

Customers can be grouped for COA purposes by assigning the customer to a COA Customer group. To create and add customers to a COA customer groups follow these steps.

1. Go to: **Inventory management > Setup > Certificate of analysis > COA Customer group**.
1. Use buttons in the action pane to add, edit, or delete a COA customer group.
1. Make the following selections for your new or selected COA customer group
    - **COA customer group** - Identification of the COA customer group.
    - **Description** - Description of the COA customer group.

## Setting up and maintaining Customer COA requirements on test groups

To set up Customer specific COA requirements on test groups follow these steps:

1. Go to **Inventory management > Setup > Quality control > Test groups**
1. In the lower section of the page, select a test 
1. In the tool bar, select Customer COA requirements to open the customer COA requirements page.
1. Use the buttons in the action pane to add, edit, or delete a customer COA requirement.
1. When making a new customer COA requirement the fields test and test group will be automatically filled our. The field Attribute will be filled out if the test is associated a Batch attribute. 
1. Fill out the fields in the grid to complete the creation of the requirement.
    - **Customer code** - Choose **All** to make the requirement applicable for all customers, **Group** for a group of customers, and **Table** for a specific customer.
    - **Customer relation** - Dependent on your selection in **Customer code** select a **COA Customer group** or a specific **Customer account**.
    - **Exclude** - Indicates if the test should appear on customer specific COA. All tests are assumed to be included except those specifically marked as excluded.
    - **Use customer specific ranges** - Indicates whether the customer specific batch attribute range should be used for the customer specific COA. If no customer specific batch attribute range if found, then the standard range will print.
    - **Suppress Min/Max values** - Indicates if the minimum and maximum values of the Test should be suppressed on the customer specific COA. For example, for a given test, let's assume that the minimum is 1 and the Maximum is 10 and the Result is 1. For certain customers, it might be desirable that the range does not display at all, not to draw attention to the fact that the result just passed the quality test.
    - **Replace pass results** - When populated, the verbiage will replace the test results on the customer specific COA if the test is passed. Some businesses would prefer to not show the actual test results but instead just show standard verbiage such as "Within specifications" for a pass.
    - **Replace fail results** - When populated, the verbiage will replace the test results on the customer's COA if the test is failed. Some businesses would prefer to not show the actual test results but instead just show standard verbiage such as *Outside acceptable range* for a failure.

## Setting up and maintaining Customer COA requirements from a quality order

You can also set up and maintain customer COA requirements from a quality order. To do so, follow these steps. 

1. Go to **Inventory management > Periodic > Quality management > Quality orders**
1. Select a quality order
1. Select a line on the selected quality order
1. From the action pane, select Customer COA requirements
1. Follow the same steps for adding, deleting, or editing Customer COA requirements as described in previous section about test groups.

## Include product and customer specific batch attributes in COA

You can mark product and customer specific batch attributes to be included into the COA, even if they are not included in testing through a quality order. 

1. Go to **Product information management > All released products**
1. In the All released products list page, filter on a batch enabled product.
1. Under the Manage inventory tab, go to the Batch attributes field group and select either Product specific or Customer specific.
1. Select the field Include in COA independent of quality order.

Once the customer COA requirements are set for a test group, they will automatically apply to all quality orders using that test group. However, these requirements can be adjusted directly on the quality order if needed.

## How to access the customer specific COA

The customer specific COA can be accessed from the following menu path's

- From the menu directly 
**Inventory management > Inquiries > Quality management > Certificate of analysis** - You can print both the Standard COA and Customer specific COA (triggered by selecting a specific customer account). You must select a quality order in both cases.

1. From a quality order
**Inventory management > Periodic > Quality management > Quality order > Ribbon: Inquiries > Certificate of analysis** - You can print both the standard COA and customer specific COA (triggered by selecting a specific customer account). Since access is from a quality order, the Quality order is assumed in both cases.

1. From an inventory batch
**Inventory management > Inquiries> Dimensions > Batches > Ribbon: Inquiries > Certificate of analysis** - You can print both the standard COA and the customer specific COA (triggered by selecting a specific customer account). Since access is from an inventory batch, the Certificate of analysis Quality order (found on the General tab) on the Inventory Batch is used in both cases to generate the COA. If the Certificate of analysis quality order needs to be updated, the ribbon action **Reset COA Quality order** can be used to change the quality order that drives the details of the COA.

1. As part of processing the Sales order packing slip
**Sales and marketing > Common > Sales orders > All sales orders > Ribbon: Pick and pack > Generate > Packing slip** or 
**Sales and marketing > Periodic > Sales update > Packing slip** (Add new orders to the list, select the checkbox to Print customer specific Certificate of analysis.) - Only customer specific COA's are printed from this process. Based on the customer placing the order, the system will print a customer specific COA for every item/batch combination on the order that has a Certificate of analysis Quality order specified on the Batch. No COA will be printed for items not batch-controlled or for items where the batch does not have a Quality order specified.
 
[!NOTE] The option to Print Customer specific COA is initially defaulted from the Accounts Receivable parameters from the Updates tab. This parameter will default to new customers. The checkbox on the Packing slip process form will default from the customer if processing for a single order. If processing for multiple orders, this checkbox will need to be selected if printing customer specific COA's are desired
