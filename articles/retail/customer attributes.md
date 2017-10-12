---
# required metadata

title: Customer attributes
description: 
author: mugunthanm 
manager: AnnBe
ms.date: 10/12/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: Retail, Operations 
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: 
ms.search.validFrom: 2017-06-30 
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update


---

# Customer attributes

We extended the attribute framework in headquarters (HQ) to support attributes for Customers, Customer orders, Cash and carry transactions, and Call center orders.

> [!NOTE]
> The attributes are read-only, but in the case of Customer or Order attributes, you can edit and set the values at the individual customer or order level too.

With the new Customer attribute framework, you can use configurations to add new fields to the customer master, and show that automatically in customer add/edit or customer details screens in POS or HQ. After configuring the customer attribute group in retail parameters, POS and HQ will automatically show up the new attribute without any code change or customization. The customer card in the POS transaction screen can also be configured to show the customer attributes using the screen layout designer.

# Why and when you should customer attributes

If you want to add new fields to customer master and capture the information in POS or HQ then you can use this feature. Previously to add a new field in customer master and to show it in HQ and POS, you must create new extension table in HQ, channel DB and modify CRT and POS code inline to do this. You must write code in CRT and POS to read/write to the extension fields and to show it in POS, handle this in different POS views and scenarios like Customer details screen, customer panel in transaction screen etc. and in CRT you need to handle all insert, Select and update operation. Now with the new functionality all this can be done through configuration without writing any code or creating custom extension tables in HQ or channel. With the first version we are not supporting datetime and reference attribute type, in those you should use extension properties and custom control to show the details in POS.

## How to configure customer attributes in POS and HQ

### Define attribute types

1.  Click **Product information management** &gt; **Setup** &gt; **Categories and** **Attributes** &gt; **Attribute types**.

2.  In the **Attribute types** form, click **New** to add a new attribute type.

3.  Enter a name for the attribute type.

4.  On the **General** FastTab, in the **Type** field, select the type of data that can be entered for attributes that are assigned to this data type.

5.  If the attribute type is **Decimal** or **Integer**, select a unit of measure.

6.  To define a fixed list of values for the attribute type, select the **Fixed list** check box. Then, on the **Values** FastTab, add the list of values.

    > [!NOTE]
    > The **Fixed list** check box is available only for the **Text** attribute type.

7.  To define a range of valid values for the attribute type, select the **Value range** check box. Then, on the **Range** FastTab, enter the valid range of values.

### Define attributes

1.  Click **Product information management** &gt; **Setup** &gt; **Categories and** **Attributes** &gt; **Attributes**.

2.  In the **Attributes** form, click **New** to add a new attribute.

3.  Enter the name, friendly name, description, and any help text that you want to display to the user for the attribute.

4.  In the **Attribute type** field, select the attribute type to assign to the attribute.

5.  Depends on the attribute type, in the **Default value** field enter the value or range of values that is displayed by default when this attribute is assigned to a customer.

6.  Click **Translate**, and then, in the **Text translation** form, enter the name, description, friendly name, and help text for the attribute in different languages.

7.  Repeat steps 2 through 6 to add more attributes.

### Define attribute group

1.  Click **Product information management** &gt; **Setup** &gt; &gt; **Categories and** **Attributes** &gt; **Attribute groups**.

2.  In the **Attribute groups** form, click **New** to add a new attribute group.

3.  Enter the name, and in the **General** FastTab enter friendly name, description, and any help text for the attribute group.

4.  Click the **Attributes** FastTab.

5.  Click **Add** to add attributes to the attribute group. In the **Default value** field, you can enter a default value for the selected attributes.

6.  Click **Translate** to open the **Text translation** form, where you can enter the description, friendly name, and help text for the attribute group in additional languages.

### Link the attribute group to the customers in Retail parameters

1.  Click **Retail** &gt; **Headquarters** **setup** &gt; **Parameters** &gt; **Retail** **parameters**.

2.  On the **General** tab, select the attribute group to be displayed in POS in the Customer attribute group field.

### Run the distribution jobs

1.  Click **Retail** &gt; **Retail** **IT** &gt; **Distribution** **schedule**.

2.  Select the **Customers** job (1010) and click the **Run now** button in the Action Pane. When prompted, click **Yes**.

3.  Select the **Global configuration** job (1110) and click the **Run now** button in the Action Pane. When prompted, click **Yes**.

### View customer attributes

#### HQ

1.  Click **Retail &gt;** **Customers** &gt; **All Customers**.

2.  Click the **Retail tab** in the Action Pane, and then click  **Retail attributes** under **Attribute section** to view or edit the attribute values.

#### POS

1.  Launch POS and navigate to the **Customer Add/Edit** screen to set or update the attribute values for the customer, or navigate to the **Customer details** screen to view the configured attributes.

### Display customer attribute in Customer panel in POS transaction screen

#### HQ

1.  Click **Retail &gt;** **Channel** **setup** &gt; **POS Setup** &gt; **POS &gt; Screen layouts**.

2.  In the **screen layout** form, click **New** to create a new screen layout or use any existing screen layout.

3.  Enter the screen layout ID and name.

4.  In the **Layout sizes** FastTab, click the **Add** button to add new layout sizes for the POS.

5.  In the **Name** drop-down list, select the desired POS screen resolution.

6.  Click the **Layout designer** button under the **Layout sized** FastTab.

7.  If prompted, click **Yes** to download and install the Retail Designer Host by clicking the **Install/Run** button.

8.  When prompted, enter the Dynamics 365 username and password to open the designer.

9.  When the designer is launched, drag and drop the **Customer** card anywhere in the screen layout designer.

10. Right click the **Customer** card, and click **Customize**.

11. When the **Customization - Customer** card form opens, select the required attributes form the **Available columns** section and click the **&gt**; button to move it to the **Selected columns** section. You can move the attributes up or down by clicking the **Up** or **Down** buttons.

12. When done, click **OK** to save the changes.

13. Close the screen layout designer by clicking the **X** button on the top-right corner, and when prompted click **Yes** to save the changes.

14. Click **Retail** &gt; **Retail** **IT** &gt; **Distribution** **schedule**.

15. Select the **Registers** job (1090) and click the **Run now** button in the Action Pane. When prompted, click **Yes**.

**POS:**

1.  Launch POS and add a customer to a transaction. 

2.  Navigate to transaction screen to view the attributes added to the **Customer** card.





