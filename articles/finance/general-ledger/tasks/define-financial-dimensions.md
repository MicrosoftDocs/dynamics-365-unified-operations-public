--- 
title: Define financial dimensions
description: Learn how to create entity-backed and custom financial dimensions, including naming requirements and how to activate dimensions.
author: JodiChristiansen
ms.author: jchrist
ms.topic: how-to
ms.date: 09/05/2025
ms.custom:
ms.reviewer: twheeloc
audience: Application User  
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: DimensionDetails, DimensionAttributeTableExtensionActivate, DimensionValueDetails
ms.dyn365.ops.version: Version 7.0.0 
---

# Define financial dimensions

[!include [banner](../../includes/banner.md)]

This procedure shows how to add an entity backed financial dimension and a custom financial dimension. The guide uses the USMF demo company.

## Naming requirements

### Financial dimension names

When you create a financial dimension, the name must follow these rules:

- Must start with a letter or an underscore.
- After the first character, can only contain letters, numbers, or underscores.
- Can't contain spaces or special characters.
- Can't use reserved system field names such as RecId.

For entity-backed dimensions, the dimension name can differ from the source entity name. If a name doesn't meet these requirements, you receive a **The financial dimension name [DIMENSION NAME] contains invalid characters** error.

### Dimension value requirements

When you create or enter dimension values, keep the following in mind:

- Dimension values have a maximum length of 30 characters.
- For custom dimensions, you can set up a format mask to control what users can enter. Use number signs (\#) as placeholders for numbers and ampersands (&) as placeholders for letters. For example, **CC-\#\#\#** limits values to the letters "CC" followed by three numbers.
- Dimension values must not contain hidden or invisible characters, such as invisible Unicode characters or hard spaces (ALT+0160). These characters can look identical to normal text but cause lookup failures because the values don't match exactly. If a dimension value contains hidden characters, open the source record, temporarily change the key field to a different value, save, then change it back and save again to remove the hidden characters.

### Avoid using the chart of accounts delimiter

The chart of accounts delimiter is the character that separates segments in a ledger account (for example, the hyphen in **110-020-300**). Don't use this character in financial dimension names, dimension values, or main account numbers.

If a dimension value contains the delimiter character, the system can misinterpret it when parsing ledger accounts. For example, if the delimiter is "-" and a dimension value is "Cust-049", the system might treat "049" as the next segment, which causes errors.

> [!WARNING]
> Dimension values that contain the delimiter character may appear to work correctly when used in default dimensions, but will cause errors when you enter ledger accounts through the segmented entry control or when you post transactions. This is because the system only parses the full segmented account string in those contexts, where it misinterprets the delimiter within the value as a segment separator.

To avoid issues:

- **Recommended**: Don't use the delimiter character in any dimension values. If conflicting values already exist, rename them.
- **Alternative**: Change the delimiter to a different character. To learn how, see [Change the segment delimiter](/dynamics365/finance/general-ledger/plan-chart-of-accounts#change-the-segment-delimiter).

## Create an entity backed financial dimension
1. Go to **General ledger > Chart of accounts > Dimensions > Financial dimensions**.
2. Click **New**.
3. In the **Use values from** field, select a system-defined entity to base the financial dimension on.
4. In the **Dimension name** field, type a value to describe the financial dimension. The name must comply with the [naming requirements](#naming-requirements).
5. Click **Activate**. Activating the financial dimension updates the table with the financial dimension name and removes deleted dimensions. You can enter dimension values before you activate a financial dimension, but a financial dimension can't be used until it's activated.  
6. Click **Close** on the activation message.
7. Click **Activate**. Dimension activation can be scheduled to run by batch at a specific date and time.  
8. Click **Dimension values**. Some dimension values are company specific. You can verify if they are company specific by if the company name is showing in the dimension values list.  

## Create a custom financial dimension
1. Click **New**.
2. In the **Use values from** field, select **Custom dimension**.
3. In the **Dimension name** field, type a value to describe the financial dimension. The name must comply with the [naming requirements](#naming-requirements).
    - You can specify an account mask to limit the amount and type of information that you can enter for dimension values.   
    - You can enter characters that remain the same for each dimension value, such as letters or a hyphen. You can also enter number signs (#) and ampersands (&) as placeholders for letters and numbers that will change every time that a dimension value is created. Use a number sign (#) as a placeholder for a number and an ampersand (&) as a placeholder for a letter. Example: To limit the dimension value to the letters CC and three numbers, you enter CC-### as the format mask.  
4. Click **Activate**. Activating the financial dimension updates the table with the financial dimension name and removes deleted dimensions. You can enter dimension values before you activate a financial dimension, but a financial dimension cannot be used until it is activated.     
5. Click **Activate**. Dimension activation can be scheduled to run by batch at a specific date and time.      
6. On **Action pane**, click **Dimension values**.
7. Click **New**.
8. In the **Dimension value** field, type a name to describe your financial dimension value.
9. In the **Description** field, type a description that describes your financial dimension value.

## Activate financial dimensions

After you create a financial dimension, you must activate it before it can be used anywhere in the system, such as in account structures or on transactions.

When you activate a financial dimension, the table updates to include the name of the financial dimension. Deleted dimensions are removed. You can create and edit dimension values before you activate a financial dimension. However, you can't consume a financial dimension anywhere until you activate it. For example, you can't add a financial dimension to an account structure until you activate the financial dimension.

When you select **Activate all**, the system updates all inactive or renamed dimensions to active, which the **Status changes** field shows. As **Activate all** processes every pending addition, rename, or deletion across all dimensions at once, there is no need to rerun the operation for each dimension. The system must be in maintenance mode when activating financial dimensions. For a list of conditions that can prevent dimension activation, see [Financial dimension activation](/dynamics365/fin-ops-core/dev-itpro/financial/activate-financial-dimensions#conditions-that-can-prevent-activation).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
