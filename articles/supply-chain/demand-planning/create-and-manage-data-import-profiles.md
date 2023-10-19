# Create and manage data import profiles

Each time your organization needs to run a new type of data import, a manager or admin must create a new data import profile. Once the profile is created, it will be available to users, who can run it as often as needed.

Each data import profile makes use of a *data provider*, which is optimized for importing from a specific type of external data source or file type. The following types of data providers are currently available:

- **Power Query providers** – Each of these providers import data from a specific type of file ((CSV, Excel, and Azure data lake storage) through Power Query, which enables you to transform and map the data for the relevant table in Demand planning.

- **Microsoft finance and operations apps** – Connects directly to Dynamics 365 Supply Chain Management (or another Microsoft finance and operations app) and imports data provided by one or more data entities into the relevant tables in Demand planning.

## Create an import profile for importing directly from Supply Chain Management

To import directly from Supply Chain Management (and other Microsoft finance and operations app), create an import profile that uses the *Microsoft finance and operations apps* data provider.

It is a pre-requisite that your Demand Planning app and your Supply Chain Management are connected so they can be used for both import and export. Follow the instructions in the Get started page for connecting both.

Follow these steps:

1.  On the navigation pane, select **Data Providers &gt; Import**.

2.  On the Action Pane, select **New**.

3.  On the **Select data provider** page, select the **Microsoft finance and operations apps** tile.

4.  A setup wizard launches, open to the **Get started** page. Enter a **Name** and **Description** for your new profile. Then select **Next**.

5.  The **Configure data provider** page opens. In the **Connection URL** field, enter the URL of your Supply Chain Management environment. Then select **Next**.

6.  The **Entity selection** page opens. It lists each Supply Chain Management data entity that the solution supports and shows which Demand planning table it maps to. Turn on the **Enabled** slider for each entity you want to import from for this profile. Then select **Next**.

7.  The **Review and finish page** opens. It summarizes the settings you've made. Review your settings and then select **Review and finish** to create the new profile.

8.  You return to the **Active Import Data Profiles** page, which now shows your new profile in the list. The profile is now available but hasn't run yet. To run it, follow the instructions in [Work with existing data import profiles](view-and-run-existing-data-import-profiles.md).

## Create an import profile for importing from exported files through Power Query

To import from a text or spreadsheet file exported from an external system, create an import profile that uses one of the *Power Query* data providers. The provider you choose must match the format of the exported file, but the procedure is the same. Follow these steps:

1.  On the navigation pane, select **Data Providers &gt; Import**.

2.  On the Action Pane, select **New**.

3.  On the **Select data provider** page, select one of the tiles under the **Power Query providers** heading. Choose the tile that matches the format of the exported file you will import using this profile.

4.  A setup wizard launches, open to the **Get started** page. Enter a **Name** and **Description** for your new profile. Then select **Next**.

5.  The **Select target table** page opens. From the **Select table** drop-down list, select the name of the table in Demand planning that you want to import data into using this profile. Then select **Next**.

6.  The **Configure provider** page opens. The settings on this page let you choose the file you want to import and then send it to Power Query, where you can transform the data and map the columns from the source document to the selected Demand planning table. The connection, transformation, and mapping features are all provided by Power Query. The procedure differs slightly depending on which Power Query provider you are using, as described in the following list.

    - **Excel** – For details about how to select the target file, connect to Power Query, and work with data, see [Excel](/power-query/connectors/excel) in the Power Query documentation.

    - **CSV** – For details about how to select the target file, connect to Power Query, and work with data, see [Text/CSV](/power-query/connectors/text-csv) in the Power Query documentation.

    - **Dataverse** – For details about how to select the target file, connect to Power Query, and work with data, see [Dataverse](/power-query/connectors/dataverse) in the Power Query documentation.

7.  When you're done transforming and mapping your data with Power Query, select **Next** to continue to the **Refresh settings** page. Do one of the following steps:

    -   If you want to delete all the data currently in the destination table in Demand planning, select the **Delete all data for the chosen table before import** check box. You might use this option, for example, if the incoming data includes all the required records that are already in your table and/or you have not selected a key fields for the table. This setting guarantees that you won't have any duplicate records but also deletes all the data currently in the target table.

    -   If you want to keep all the data currently in the destination table in Demand planning, clear the **Delete all data for the chosen table before import** check box. You might use this option, for example, if the incoming data is an incremental export that only contains new records and/or if you have selected key fields for the table. Incoming records with key field values that match existing records will update those records, while incoming records with unique key field values will create new records. If your key fields aren't configured and mapped correctly, this setting risks creating duplicate records.

8.  Select **Next** to continue to the **Review and finish page**. It summarizes the settings you've made. Review your settings and then select **Review and finish** to create the new profile.

9.  You return to the **Active Import Data Profiles** page, which now shows your new profile in the list. The profile is now available but hasn't run yet. To run it, follow the instructions in [Work with existing data import profiles](view-and-run-existing-data-import-profiles.md).

