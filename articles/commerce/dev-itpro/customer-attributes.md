---
# required metadata

title: Customer attributes
description: This topic provides information about customer attributes and explains how you can use configurations to add new fields to the customer master record.
author: mugunthanm 
ms.date: 10/12/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: tfehr
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: mumani
ms.search.validFrom: 2017-06-30 
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update


---

# Customer attributes

[!include [banner](../../includes/banner.md)]

We extended the attribute framework in Headquarters to support attributes for customers, customer orders, cash-and-carry transactions, and call center orders.

> [!NOTE]
> The attributes are read-only. However, in the case of customer or order attributes, you can edit and set values at the level of the individual customer or order.

The new customer attribute framework lets you use configurations to add new fields to the customer master record. Those fields then automatically appear on the **Customer add/edit** or **Customer details** screen in Point of Sale (POS) or Headquarters. After you configure the customer attribute group in the Commerce parameters, POS and Headquarters automatically show the new attribute. No code change or customization is required. You can also use the screen layout designer to configure the customer card on the POS transaction screen so that it shows the customer attributes.

## Why and when you should configure customer attributes

If you want to add new fields to the customer master record, and capture the information in POS or Headquarters, you can use this feature. Previously, to add a new field to the customer master record and show it in POS and Headquarters, you had to create a new extension table in Headquarters and the channel database, and make inline modifications to Commerce runtime (CRT) and POS code. You had to write code in CRT and POS to read/write to the extension fields and show them in POS. You had to handle this in various POS views and scenarios, such as the **Customer details** screen and the **Customer** panel on the transaction screen. In addition, in CRT, you had to handle all insert, select, and update operations. However, the new functionality lets you complete all these steps through configuration so you don't have to write any code or create custom extension tables.

The first version of this functionality doesn't support **datetime** and **reference** attribute types. For those attribute types, you should use extension properties and custom controls to show the details in POS.

## Configure customer attributes in POS and Headquarters

### Define attribute types

1. Select **Product information management** > **Setup** &gt; **Categories and attributes** > **Attribute types**.
2. On the **Attribute types** page, select **New** to add a new attribute type.
3. Enter a name for the attribute type.
4. On the **General** FastTab, in the **Type** field, select the type of data that can be entered for attributes that are assigned to this data type.
5. If the attribute type is **Decimal** or **Integer**, select a unit of measure.
6. To define a fixed list of values for the attribute type, select the **Fixed list** check box. Then, on the **Values** FastTab, add the list of values.

    > [!NOTE]
    > The **Fixed list** check box is available only for the **Text** attribute type.

    Alternatively, to define a range of valid values for the attribute type, select the **Value range** check box. Then, on the **Range** FastTab, enter the valid range of values.

### Define attributes

1. Select **Product information management** > **Setup** > **Categories and attributes** > **Attributes**.
2. On the **Attributes** page, select **New** to add a new attribute.
3. Enter the name, friendly name, description, and any Help text that should be shown to the user for the attribute.
4. In the **Attribute type** field, select the attribute type to assign to the attribute.
5. Depending on the attribute type, in the **Default value** field, enter the value or the range of values that is shown by default when this attribute is assigned to a customer.
6. Select **Translate** to open the **Text translation** page, where you can enter the name, description, friendly name, and Help text for the attribute in additional languages.
7. Repeat steps 2 through 6 to add more attributes.

### Define an attribute group

1. Select **Product information management** > **Setup** > **Categories and attributes** > **Attribute groups**.
2. On the **Attribute groups** page, select **New** to add a new attribute group.
3. Enter the name, and then, on the **General** FastTab, enter the friendly name, description, and any Help text for the attribute group.
4. On the **Attributes** FastTab, select **Add** to add attributes to the attribute group. In the **Default value** field, you can enter a default value for the selected attributes.
5. Select **Translate** to open the **Text translation** page, where you can enter the description, friendly name, and Help text for the attribute group in additional languages.

### Link the attribute group to the customers

1. Select **Retail and Commerce** > **Headquarters setup** > **Parameters** > **Commerce parameters**.
2. On the **General** tab, in the **Customer attribute group** field, select the attribute group that should be shown in POS.

### Run the distribution jobs

1. Select **Retail and Commerce** > **Retail and Commerce IT** > **Distribution schedule**.
2. Select the **Customers** job (1010), and then, on the Action Pane, select **Run now**. When you're prompted, select **Yes**.
3. Select the **Global configuration** job (1110), and then, on the Action Pane, select **Run now**. When you're prompted, select **Yes**.

### View customer attributes

#### Headquarters

1. Select **Retail and Commerce** > **Customers** > **All customers**.
2. On the Action Pane, in **Retail and Commerce**, in the **Attribute** section, select **Retail attributes** to view or edit the attribute values.

#### POS

- Start POS, and then either open the **Customer Add/Edit** screen to set or update the attribute values for the customer, or open the **Customer details** screen to view the configured attributes.

### Show customer attributes in the POS transaction screen

#### Headquarters

1. Select **Retail and Commerce** > **Channel setup** > **POS Setup** > **POS** > **Screen layouts**.
2. On the **screen layout** page, select **New** to create a new screen layout, or select an existing screen layout.
3. Enter the ID and name for the screen layout.
4. On the **Layout sizes** FastTab, select the **Add** button to add new layout sizes for the POS.
5. In the **Name** field, select the POS screen resolution.
6. On the **Layout sized** FastTab, select the **Layout designer** button.
7. If you're prompted, select **Yes** to download and install the Retail Designer Host by using the **Install/Run** button.
8. When you're prompted, enter the Microsoft Dynamics 365 user name and password to start the designer.
9. After the designer is started, drag the **Customer** card anywhere in the screen layout designer.
10. Right-click the **Customer** card, and then select **Customize**.
11. When the page for the **Customization - Customer** card appears, select the required attributes in the **Available columns** section, and then select the right arrow button (**>**) to move them to the **Selected columns** section. You can move the attributes up or down by selecting the **Up** or **Down** buttons.

[!NOTE]
>The Customer attributes are legal entity-specific, which means that the screen layout designer fetches the customer attribute that is specific to the legal entity (Company) configured for the user signed in to **System Administration > Users**. If you configured attributes for a different legal entity, the screen layout designer may not show those values.

13. When you've finished, select **OK** to save your changes.
14. Close the screen layout designer by selecting **Close** (**X**) in the upper-right corner. When you're prompted, select **Yes** to save your changes.
15. Select **Retail and Commerce** &gt; **Retail and Commerce IT** &gt; **Distribution schedule**.
16. Select the **Registers** job (1090), and then on the Action Pane, select **Run now**. Select **Yes**.
.

#### POS

1. Start POS, and add a customer to a transaction.
2. Open the transaction screen to view the attributes that have been added.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
