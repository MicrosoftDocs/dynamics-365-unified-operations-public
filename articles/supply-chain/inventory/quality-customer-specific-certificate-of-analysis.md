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

# Customer specific certificate of analysis

Supply Chain Management provides the ability to create a basic Certificate of Analysis (COA) from the quality order or from the menu directly after selecting a quality order. Learn more about how to use the basic COA here: [Quality orders](quality-orders.md)

This article describes how you can vary the content of the COA by customer and automatically create/print a COA at sales order packing slip posting time. The customer specific COA has the following main components:

- A way to group customers for COA-related purposes and set up COA customer requirements on Test groups and Quality orders.

- Setup customer specific COA requirements by grouped by Customer, groups of customers, or for all customers to:

    - Include or exclude specific tests from the report

    - Include customer-specific minimum and maximum ranges for test results.

    - Suppress mimum and maximum test values

    - Replace actual passed or failed test results with verbiage

- Make is optionally to include batch attributes and their values in the report.

- Setup customer specific COA requirements grouped by customer, group of customers, or all customers from quality orders that are

    - Manually created

    - Created automatically when a sales order packing slip is posted

    - Created manually from an inventory batch

    - Created direcely from the **Inventory management** menu


## Setting up and maintaining Customer COA requirements

Customers can be grouped for COA purposes by assigning the customer to a **COA Customer group**. To create and add customers to a **COA customer groups** go to: **Inventory management > Setup > Certificate of analysis > COA Customer group**.

To set up **Customer specific COA requirements** go to **Inventory management > Setup > Quality control > Test groups** or **Inventory management > Periodic > Quality management > Quality orders > Line > Customer COA requirements**

Select a test in the test group and then select **Customer COA requirement** button on the toolbar. In the **Customer CAO requirement** page, you can now set up the customer specific requirements for the specific test. 

To add a new requirement for the test select **New** in the Actionpane. The fields for **Test group** and **Test** will be automatically filled out. If the test is associated a batch attribute, that attribute is reflected in the field **Attribute**. Fill out the fields in the grid:

**Customer code** - Choose **All** to make the requirement applicable for all customers, **Group** for a group of customers, and **Table** for a specific customer.
 
**Customer releation** - Dependent on your selection in **Customer code** select a **COA Customer group** or a specific **Customer account**.

**Exclude** - Indicates if the test should appear on customer specific COA. All tests are assumed to be included except those specifically marked as excluded.

**Use customer specific ranges** - Indicates whether the customer specific batch attribute range should be used for the customer specific COA. If no customer specific batch attribute range if found, then the standard range will print.

**Supress Min/Max values** - Indicates if the minimum and maximum values of the Test should be suppressed on the customer specific COA. For example, for a given test, let's assume that the minimum is 1 and the Maximum is 10 and the Result is 1. For certain customers, it might be desirable that the range does not display at all, not to draw attention to the fact that the result just passed the quality test.

**Replace pass results** - When populated, the verbiage will replace the test results on the customer specific COA if the test is passed. Some businesses would prefer to not show the actual test results but instead just show standard verbiage such as "Within specifications" for a pass.

**Replace fail results** - When populated, the verbiage will replace the test results on the customer's COA if the test is failed. Some businesses would prefer to not show the actual test results but instead just show standard verbiage such as *Outside acceptable range* for a failure.

## Include product and customer specific batch attributes in COA

You can mark product and customer specific batch attributes to be included into the COA, even if they are not included in testing through a quality order. 

1. Go to **Product information management > All released products**
1. In the **All released products** list page filter on a batch enabled product
1. Under the **Manage inventory** tab, go to the **Batch attributes** field group and select either **Product specific** or **Customer specific**
1. Select the field **Include in COA independent of Quality order**

Once the customer COA requirements are established on the test group, the requirements will default to all quality orders that use that test group, but the requirements can be modified on the quality order directly. In the example below, if the COA was printed for Customer US-002, T1 would not be included. For all customers in COA-CG1, when the COA was generated for one of them, this test would be included, customer specific batch attribute range would be used, if available, instead of the standard range and if the test passed, the actual result would be replaced with the verbiage: Within spec.

## Using Customer COA requirements

The customer COA requirements will be utilized whenever a customer specific COA is generated. A customer specific COA can be generated from the Inventory management menu, a Quality order, an Inventory batch, or automatically from the Sales order Packing slip process. From the menu, a specific quality order, or a specific Inventory batch, the customer specific COA will be triggered by the user choosing a customer account for the COA. Once a customer account is selected and the print option is chosen, the system will automatically look at the customer COA requirements for the specific customer selected and the details of the COA will be adjusted based on the specific requirements for that customer. Standard print destination options are available such as printing the COA to the screen, printer, file or email. If the standard COA is desired, then no customer account should be selected. This will trigger the system to generate the standard COA and the Customer COA requirements will not be utilized. When generating COA's from the Packing slip posting process, only customer specific COA's are generated for all item/batch combinations on the sales orders that have quality orders identified. The default print destination from this process is defined on the Inventory management parameters under Print Management for Customer specific COA's. The chart below identifies multiple ways to access the COA.

## How to access the customer specific COA

The customer specific COA can be accessed from the following menu path's

1. From the menu directly 
**Inventory management > Inquiries > Quality management > Certificate of analysis** - You can print both the Standard COA and Customer specific COA (triggered by selecting a specific customer account). You must select a quality order in both cases.

1. From a quality order
**Inventory management > Periodic > Quality management > Quality order > Ribbon: Inquiries > Certificate of analysis** - You can print both the standard COA and customer specific COA (triggered by selecting a specific customer account). Since access is from a quality order, the Quality order is assumed in both cases.

1. From an inventory batch
**Inventory management > Inquiries> Dimensions > Batches > Ribbon: Inquiries > Certificate of analysis** - You can print both the standard COA and the customer specific COA (triggered by selecting a specific customer account). Since access is from an inventory batch, the Certificate of analysis Quality order (found on the General tab) on the Inventory Batch is used in both cases to generate the COA. If the Certificate of analysis quality order needs to be updated, the ribbon action **Reset COA Quality order** can be used to change the quality order that drives the details of the COA.

1. As part of processing the Sales order packing slip
**Sales and marketing > Common > Sales orders > All sales orders > Ribbon: Pick and pack > Generate > Packing slip** or 
**Sales and marketing > Periodic > Sales update > Packing slip** (Add new orders to the list, select the checkbox to Print customer specific Certificate of analysis.) - Only customer specific COA's are printed from this process. Based on the customer placing the order, the system will print a customer specific COA for every item/batch combination on the order that has a Certificate of analysis Quality order specified on the Batch. No COA will be printed for items not batch-controlled or for items where the batch does not have a Quality order specified.
Note: The option to Print Customer specific COA is initially defaulted from the Accounts Receivable parameters from the Updates tab. This parameter will default to new customers. The checkbox on the Packing slip process form will default from the customer if processing for a single order. If processing for multiple orders, this checkbox will need to be selected if printing customer specific COA's are desired


| **<u>Options</u>** | **<u>Menu path</u>** | **<u>Helpful hints</u>** |
|-------------------------|-------------------------|-------------------------|
| Menu directly | Inventory management** \> **Inquiries** \> **Quality management** \> **Certificate of analysis | Can print both the Standard COA and Customer-specific COA (triggered by selecting a specific customer account). Must select a quality order in both cases. |
| Quality order | Inventory management** \> **Periodic** \> **Quality management** \> **Quality order</br>Ribbon: Inquiries** \> **Certificate of analysis | Can print both the Standard COA and Customer-specific COA (triggered by selecting a specific customer account). Since access is from a quality order, the Quality order is assumed in both cases. |
| Inventory batch | Inventory management** \> **Inquiries&gt; Dimensions** \> **Batches</br>Ribbon: Inquiries** \> **Certificate of analysis | Can print both the Standard COA and Customer-specific COA (triggered by selecting a specific customer account). Since access is from an inventory batch, the Certificate of analysis Quality order (found on the General tab) on the Inventory Batch is used in both cases to generate the COA. If the Certificate of analysis quality order needs to be updated, the ribbon action "Reset COA Quality order" can be used to change the quality order that drives the details of the COA.</br>Note: This option, including generating the standard COA from here, is new functionality only available with Supply Chain Management. |
| Sales order packing slip post process | <u>For individual sales order:</u></br>Sales and marketing** \> **Common** \> **Sales orders** \> **All sales orders</br>Ribbon: Pick and pack** \> **Generate** \> **Packing slip</br><u>For multiple sales orders:</u></br>Sales and marketing** \> **Periodic** \> **Sales update** \> **Packing slip</br>(Add new orders to the list, select the checkbox to Print customer specific Certificate of analysis.) | Only customer specific COA's are printed from this process. Based on the customer placing the order, the system will print a customer specific COA for every item/batch combination on the order that has a Certificate of analysis Quality order specified on the Batch. No COA will be printed for items not batch-controlled or for items where the batch does not have a Quality order specified.</br>Note: The option to Print Customer specific COA is initially defaulted from the Accounts Receivable parameters from the Updates tab. This parameter will default to new customers. The checkbox on the Packing slip process form will default from the customer if processing for a single order. If processing for multiple orders, this checkbox will need to be selected if printing customer specific COA's are desired. |

## Printing Customer specific COA

Customer specific COA's can be adjusted based on the customer and will include more information than what is included on the standard COA. The customer COA requirements for the specific customer will drive details such as whether a specific test should be included, if minimum/maximum values should be suppressed, if customer-specific batch attribute ranges should be used instead of the standard range and if results should be replaced with standard verbiage. In addition, customer specific COA's provide a specific customer section on the report which includes Customer name, description, and contact information. Product and Tracking dimensions will also be included as well as batch dates such as Batch expiration date and Best Before Batch Date. Optionally, customer specific COA's can include independent batch attributes and their values. These are batch attributes associated to the batch that were not specifically tested on the quality order in question but are still important details about the quality of the product. There is a parameter on the Batch attribute (Include on COA independent of quality order) that will default to the Batch attribute by product if the batch attribute should be included in the independent batch attribute section of the COA if not specifically tested on the quality order. If the Customer specific COA was generated automatically from the Sales Order Packing slip process, the Sales order number and packing slip date will also display on the report. Here is an example of the Customer specific COA requested from a quality order for Customer US-027. Notice that the Customer COA requirements were used. For example, for Test T1, the actual test result was suppressed and replaced with the standard verbiage: Within spec. Also notice the Customer details section and the independent batch attribute section. These are only available on customer specific COA's.

|     |
|-----|
|     |
