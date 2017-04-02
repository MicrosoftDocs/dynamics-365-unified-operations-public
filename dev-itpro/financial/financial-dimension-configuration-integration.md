---
# required metadata

title: Financial dimension configuration for integrating applications
description: This topic describes the Financial dimension configuration for integrating applications page. This page contains two important areas for setup, the order of financial dimensions for financial reporting and the data entity integration formats. Data entity integration formats are required in order to import transactions that contain accounts and financial dimensions.
author: RobinARH
manager: AnnBe
ms date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 61
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 91363
ms.assetid: 6be04fc8-5e2b-4ea6-b9bc-940fb5b811e5
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1

---

# Financial dimension configuration for integrating applications

This topic describes the Financial dimension configuration for integrating applications page. This page contains two important areas for setup, the order of financial dimensions for financial reporting and the data entity integration formats. Data entity integration formats are required in order to import transactions that contain accounts and financial dimensions.

Financial reporting
-------------------

The **Financial reporting** tab has a list of all financial dimensions in the system. Because different companies use different dimensions and account structures, there is no way to determine the order in which users want to view all financial dimensions on reports. This tab lets you set the order in which you want financial dimensions to appear when you build and view a report in Financial reporting. The Financial reporting tab is not available in Dynamics 365 for Operations. Instead, please see the Financial reporting setup page to select your Financial dimensions and Attributes.

## Data entities
The **Data entities** tab is where you define the order of financial dimensions for importing data. There is no rule about how you should set the order of your dimension formats. They are designed to be flexible enough that you can take your source files from an external system and import the data without spending time to make the source files match your account structures. Dimension validation still occurs during the import process, to verify that you aren't importing financial dimension values that don't exist for a particular segment. However, outside validation, account structures and dimension formats are independent of each other. There are four dimension format types:

-   **Default dimension format** – This format type is required any time that you import default dimensions, through both Data Management and the Microsoft Excel integration. For example, you might require a default dimension format if you're importing the financial dimensions that are associated with a customer account.
-   **Ledger dimension format** – This format type is required any time that you import ledger dimensions, through both Data Management and the Excel integration. The ledger dimension format is the most common format, because it's used any time that transactions are imported, such as through the general journal, or any time that setup information is imported, such as on posting profiles.
-   **Budget register dimension format** – This format type is required any time that you import dimensions for budgeting and budget control, through both Data Management and the Excel integration.
-   **Budget planning dimension format** – This format type is required any time that you import dimensions for budget planning, through both Data Management and the Excel integration.

The dimension format types are not company-specific. The setup is a global setup. You can set up as many of each format type as you require, but only one format type can be active at one time. If no dimension format type is set up, you will receive an error when you import. You will also receive errors if the order is incorrect. Let's look at some examples that show how the dimension formats work. We will use the ledger dimension format for these examples.

### Example 1

You're importing the following file.

| Date     | Main account and dimensions | Amount   |
|----------|-----------------------------|----------|
| 6/1/2016 | 605140-001-02               | $150.00  |
| 6/1/2016 | 110110-002-04-ABC           | $-150.00 |

When you import the file, the system reviews the **Main account and dimensions** column, and maps it to what you've set up in the active ledger dimension format. For this example, the active ledger dimension format is as follows: **Main account - Department - Cost Center** The system reads the first segment in the **Main account and dimensions** column as the main account. In this example, that segment is 605140 in the first row. Therefore, the mapping from the import file to the active ledger dimension format is as follows: **Main account == 605140** **Department == 001** **Cost Center == 02** Now let's look at the second row. The second row contains a fourth segment, ABC. In this example, ABC is dropped during the import from the line. **Main account == 110110** **Department == 002** **Cost Center == 04** **Segment 4, ABC, isn't imported.**

### Example 2

For this example, we will use the same import file.

| Date     | Main account and dimensions | Amount   |
|----------|-----------------------------|----------|
| 6/1/2016 | 605140-001-02               | $150.00  |
| 6/1/2016 | 110110-002-04-ABC           | $-150.00 |

However, we will use the following active ledger dimension format: **Main account - Department - Cost Center - Customer** For the first row of the import file, because only three segments are defined, a blank or dash is assumed for the Customer segment. **Main account == 605140** **Department == 001** **Cost Center == 02** **Customer == blank** Therefore, the string looks like this: 605140-001-02- The second row is imported just as defined in the import file. **Main account == 110110** **Department == 002** **Cost Center == 04** **Customer == ABC**

See also
--------

[Dimensions in Excel](dimensions-overview.md)

