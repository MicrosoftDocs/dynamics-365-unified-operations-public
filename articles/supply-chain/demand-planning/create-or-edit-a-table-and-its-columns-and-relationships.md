# Create or edit a table and its columns and relationships

You can create your own non-system tables or extend system tables by adding extra non-system columns. Custom tables and columns can be used in Demand planning equally as system tables and columns. For example, you could add important signals such as weather data, inflation stats, or other macro-economic data.

To create or edit a table, follow these steps:

1.  On the navigation pane, select **Configurations &gt; Tables**.

2.  Do one of the following steps:

    -   To add a new non-system table, select **New** from the Action Pane.

    -   To edit an existing table, select a link in the **Name** column.

    -   To delete one or more existing non-system table, select the check box next to the names of the target tables and then select **Delete** from the Action Pane.

3.  Open the **General** tab and make the following settings:

    - **Name** – For new tables, enter the table name. For existing tables, this is read only.

    - **Owner** – Select the user account, master data manager or similar role, that owns the table.

    - **Key** – Identify one or more columns whose combined values will uniquely identify each row in the table. If you're making a new table, then you won't be able to make this setting until after you've added the column(s) you will use as keys. This is important for avoiding creating duplicate records with each import.

4.  On the Action Pane, select **Save**.

5.  Open the **Columns** tab. Here you can see the name, data type, and system status of each column. Use buttons on the toolbar to add new columns or delete existing non-system columns. Each column must have a **Name** and a **Data Type**.

**Note**: To be able to transform a table and its data into a time series, the table must include at least three types of columns

-   1 *timestamp* column (DateTime)

-   1 *measure* column (Decimal or Integer)

-   1 *dimension* column (String)

6.  If necessary, go back to the **General** tab and identify your **Key** column(s).

7.  Open the **Relationships** tab. Relationships between tables let you construct a data model suitable for your organization's needs. As with tables and columns, pre-defined system relationships are required and are therefore marked with **Is System** set to *Yes*. You can also add custom relationships as needed (with **Is System** set to *No*). System relationships can't be deleted or changed.

Each relationship links two tables together, which enables you to match related information stored in different tables. Only columns from related tables can be selected in transformation. You can set up both *many to one* and*many to many* relationships. In the case of a*many to many* relationship, the system will display first matching record

Relations are currently *directional*, so it is important to pay attention to which table is the**From Table** and which is the **To Table**. Often, the **From table** will be a transactional table like **Historical Demand**.

![A close up of a white background Description automatically generated](media/image5.png)

8.  To add a new relationship, select **New Relationship** from the toolbar and then make the following settings in the **Quick Create: Relationship** dialog:

    - **From Table** – This is the current table. It's usually a table that holds transaction data.

    - **From Column** – Select the field from the **From table** that holds values to be matched in the related table.

    - **To Table** – Select the target table that contains the data you want to relate to.

    - **To Column** – Select the target field, which holds data values that will be matched to the value found in the **From Column**.

Select **Save and Close**.

All relationships are *Active* by default, which means that columns from related tables can be selected in transformation. You can change the activation status of a relationship, or delete the relationship entirely by selecting it on the **Relationship** tab and selecting the appropriate action on the toolbar.

9.  Open the **Data** tab to inspect the data your table contains.

10. Select **Save** on the Action Pane to save your changes.

