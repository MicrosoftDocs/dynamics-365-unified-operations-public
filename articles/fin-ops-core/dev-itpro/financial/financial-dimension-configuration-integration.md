---
# required metadata

title: Financial dimension configuration
description: This article describes the Financial dimension configuration for integrating applications page.
author: RyanCCarlson2
ms.date: 12/01/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.assetid: 6be04fc8-5e2b-4ea6-b9bc-940fb5b811e5
ms.search.region: Global
# ms.search.industry: 
ms.author: rcarlson
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1

---

# Financial dimension configuration

[!include [banner](../includes/banner.md)]

This article describes the Financial dimension configuration. There are two important areas for setup: 

- The order of financial dimensions for financial reporting. The order is configured on the **Financial reporting setup** page. 
- The data entity integration formats. The formats are configured on the **Integrating applications** page. Data entity integration formats are required in order to import transactions that contain accounts and financial dimensions.

## Financial reporting

The **Financial reporting setup** page has a list of all financial dimensions in the system (**General ledger** > **Ledger setup** > **Financial reporting setup**).  

The **Financial reporting setup** page has two sections that determine the data you report on in Financial reporting:

- **Dimensions** tab - Because different companies use different dimensions and account structures, there is no way to determine the order in which users want to view all financial dimensions on reports. This page allows you set the order in which you want financial dimensions to appear when you build and view a report in Financial reporting. 
- **Attributes** tab - This tab is where you can select whether you want the ability to use **Vendors** and **Customers** as attributes for filtering and report design. Reporting on Vendor and Customer will only be valuable if you do not enter multiple vendors or customers in a single voucher when posting transactions. Choosing Vendor and/or Customer will add additional time to the integration.  
>[!NOTE]
>Changes to this setup requires a reset to the Data Mart in order to see the changes in the financial reports. 

## Data entities

The **Data entities** tab is where you define the order of financial dimensions for importing data. There is no rule about how you should set the order of your dimension formats. They are designed to be flexible enough that you can take your source files from an external system and import the data without spending time to make the source files match your account structures. Dimension validation still occurs during the import process, to verify that you aren't importing financial dimension values that don't exist for a particular segment. However, outside validation, account structures and dimension formats are independent of each other. There are four dimension format types:

- **Default dimension format** – This format type is required when you import default dimensions, through both Data Management and the Microsoft Excel integration. For example, you might require a default dimension format if you're importing the financial dimensions that are associated with a customer or vendor account. Main account is not included in this format.
- **Ledger dimension format** – This format type is required when you import ledger dimensions, through both Data Management and the Excel integration. The ledger dimension format is the most common format, because it's used any time that transactions are imported, such as through the general journal. The main account is specified on this format. This setting applies across all legal entities and the account structures used in your environment. The setup must include a cumulative set of all dimensions that can be used for transaction import across your legal entities. Any dimensions not used for a given legal entity are to be left blank in the import file. 
- **Budget register dimension format** – This format type is required any time that you import dimensions for budgeting and budget control, through both Data Management and the Excel integration.
- **Budget planning dimension format** – This format type is required any time that you import dimensions for budget planning, through both Data Management and the Excel integration.

> [!NOTE]
> *The dimension format types are not company-specific. The setup is a global setup.* You can set up as many of each format type as you need, but only one format type can be active at one time. If no dimension format type is set up, you will receive an error when you import. You will also receive errors if the order is incorrect. 
 
Let's look at some examples that show how the dimension formats work. We will use the ledger dimension format for these examples.

### Example 1

You're importing the following file.

| Date     | Main account and dimensions | Amount   |
|----------|-----------------------------|----------|
| 6/1/2016 | 605140-001-02               | $150.00  |
| 6/1/2016 | 110110-002-04-ABC           | $-150.00 |

When you import the file, the system reviews the **Main account and dimensions** column, and maps it to what you've set up in the active ledger dimension format. For this example, the active ledger dimension format is as follows: **Main account - Department - Cost Center** 

The system reads the first segment in the **Main account and dimensions** column as the main account. In this example, that segment is 605140 in the first row. Therefore, the mapping from the import file to the active ledger dimension format is as follows: **Main account == 605140** **Department == 001** **Cost Center == 02** 

Now let's look at the second row. The second row contains a fourth segment, ABC. In this example, ABC is dropped during the import from the line: **Main account == 110110** **Department == 002** **Cost Center == 04** **Segment 4, ABC, isn't imported.**

### Example 2

For this example, we will use the same import file.

| Date     | Main account and dimensions | Amount   |
|----------|-----------------------------|----------|
| 6/1/2016 | 605140-001-02               | $150.00  |
| 6/1/2016 | 110110-002-04-ABC           | $-150.00 |

However, we will use the following active ledger dimension format: **Main account - Department - Cost Center - Customer** 

For the first row of the import file, because only three segments are defined, a blank or dash is assumed for the Customer segment: **Main account == 605140** **Department == 001** **Cost Center == 02** **Customer == blank** 

Therefore, the string looks like this: **605140-001-02-** 

The second row is imported as defined in the import file: **Main account == 110110** **Department == 002** **Cost Center == 04** **Customer == ABC**

## Additional resources

[Add dimensions to Excel templates](dimensions-overview.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
