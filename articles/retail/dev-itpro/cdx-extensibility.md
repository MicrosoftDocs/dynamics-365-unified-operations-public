---
# required metadata

title: CDX extensibility
description: This topic explains how you can extend the Retail initialization class to support custom Commerce Data Exchange (CDX) synchronization.
author: mugunthanm
manager: AnnBe
ms.date: 09/15/2017
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
ms.search.scope: AX 7.0.0, Operations, Retail, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 83892
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 2017-09-15
ms.dyn365.ops.version: AX 7.0.0, Retail September 2017 update

---
# CDX extensibility

This topic explains how you can extend the Retail initialization class to support custom Commerce Data Exchange (CDX) synchronization. For this extension, you use the new extension points that were added in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition platform update 8 or Microsoft Dynamics 365 for Retail platform update 8.

CDX is a system that transfers data between Retail headquarters (Retail HQ) and retail channels, such as online stores or brick-and-mortar stores. The data transfer between Retail HQ and the channel database is controlled by scheduler jobs. Each scheduler job contains a list of scheduler subjobs. The scheduler subjobs contain the names of the source tables and destination tables, and the transfer field mapping of those tables. There are two ways to configure the data synchronization between Retail HQ and the channel database:

+ Configure all the custom jobs and subjobs by using the configuration user interface (UI) for CDX.
+ Extend the Retail initialization class by using the extension points that are provided to support custom jobs and subjobs for both push and pull.

The advantage of using the Retail initialization class is that you don't have to configure the custom jobs in different environments (dev, test, and production). Instead, you can run the retail initialization by using the **Initialize** button on the **Retail parameters** page. Information about the custom job for the data synchronization is then automatically created in CDX.

There are various scenarios for data transfer between Retail HQ and the channel database:

+ Send data from a new Retail HQ table to a new channel database table by using a download job.
+ Pull data from a new channel database table to a new Retail HQ table by using a push job.

## Send data from a new Retail HQ table to a new channel database table by using a download job

Before you push or pull data, you must understand various metadata definitions in the XML resource file. The resource file contains the custom job information that will be initialized in your environment to push and pull data. Here is a list of the resource files that you must configure:

+ **ChannelDBSchema** – The extension schema that you created in the channel database.
+ **TargetTableSchema** – The extension schema that you created in the channel database to add your custom tables.
+ **AxTableName** – The table name.
+ **IsUpload** – A flag that determines whether the job is a push job or a pull job. (In other words, the flag indicates whether you want to send data from Retail HQ to the channel database or pull data from the channel database to Retail HQ). The default value is **false**, which indicates that you're sending data from Retail HQ to the channel database.
+ **ScheduledByJob** – This resource file contains one or more subjobs.
+ **Subjob** – Each table is added as a subjob, and each subjob is scheduled by one or more scheduler jobs.
+ **TargetTable** – The name of the channel database table. This table is the target table that the push job or pull job must send data to. If a value isn't specified, the system assumes that name of the target table and the name of the source table are the same.

If you created a new Retail HQ table and a new channel database table, follow these steps to push the data between the two tables.

1. Create a custom project, and use the Application Object Tree (AOT) to add a custom table.
2. Create a new resource file to add all custom job information. Here is the template for the resource file.

    ```
    <RetailCdxSeedData ChannelDBMajorVersion="7" ChannelDBSchema="ext" Name="AX7">
        <Jobs>
        </jobs>
        <Subjobs>
            <Subjob Id="" TargetTableSchema="" TargetTableName="">
        </Subjobs>
     </RetailCdxSeedData>
    ```

3. Use the AOT to create a new XML resource. In the XML file for the resource, specify the new table and new job details, as shown in the following example.

    > [!NOTE]
    > You can either add the new table as part of the existing job, or create a new job and add this table. In this case, we are creating a new job, where the job ID is **7000** and the custom table is named **ContosoRetailSeatingArrangementData**.

    ```
    [<RetailCdxSeedData ChannelDBMajorVersion="7" ChannelDBSchema="ext" Name="AX7">](file:///C:\Users\mumani\AppData\Local\Microsoft\Windows\INetCache\Content.Outlook\LQW97M2L\RetailCDXSeedDataAX7_ContosoRetailExtension%20(002).xml)
        [<Jobs>](file:///C:\Users\mumani\AppData\Local\Microsoft\Windows\INetCache\Content.Outlook\LQW97M2L\RetailCDXSeedDataAX7_ContosoRetailExtension%20(002).xml)
            <Job DescriptionLabelId="REX4520710" Description="Custom job" Id="7000"/>
        </Jobs>
        <Subjobs>
            [<Subjob Id="ContosoRetailSeatingArrangementData" TargetTableSchema="ext" AxTableName="ContosoRetailSeatingArrangementData">](file:///C:\Users\mumani\AppData\Local\Microsoft\Windows\INetCache\Content.Outlook\LQW97M2L\RetailCDXSeedDataAX7_ContosoRetailExtension%20(002).xml)
                [<ScheduledByJobs>](file:///C:\Users\mumani\AppData\Local\Microsoft\Windows\INetCache\Content.Outlook\LQW97M2L\RetailCDXSeedDataAX7_ContosoRetailExtension%20(002).xml)
                    <ScheduledByJob>7000</ScheduledByJob>
                </ScheduledByJobs>
                [<AxFields>](file:///C:\Users\mumani\AppData\Local\Microsoft\Windows\INetCache\Content.Outlook\LQW97M2L\RetailCDXSeedDataAX7_ContosoRetailExtension%20(002).xml)
                    <Field Name="seatNumber"/>
                    <Field Name="capacity"/>
                    <Field Name="channelRecId"/>
                    <Field Name="RecId"/>
                 </AxFields>
            </Subjob>
        </Subjobs>
    </RetailCdxSeedData>
    ```

    By default, the name of the target table isn't specified here. The system assumes the name of the target table on the channel side is the same as the name of the source table on the Finance and Operations side (**AXTableName**). However, the name of the target table on the channel side might sometimes differ from the name of the source table on the Finance and Operations side. In this case, in the **&lt;Subjob&gt;** node, you can use the **&lt;TargetTableName&gt;** attribute to set the name of the target table on the channel side.

    Similarly, in the mapping section, only the names of fields on the Finance and Operations side are specified (**AxFields**). By default, it's assumed that the same field name is also used on the channel side. However, the field name on the corresponding channel table might sometimes differ from the field name on the Finance and Operations side. In this case, in the mapping, you can use the **ToName** attribute of the **&lt;Field&gt;** node to set the name of the field on the channel side.

4. Right-click the project, and then select **Add** &gt; **New Item**.
5. In the **Add New item** dialog box, select **Resources**, name the resource file **RetailCDXSeedDataAX7\_Custom**, and then select **Add**.

    ![Add a new item](media/cdx-ext-1.png)

6. In the **Select a Resource file** dialog box, find the resource file that you created in step 2, and then select **Open**.
7. Add a new class that should be used to handle the **registerCDXSeedDataExtension** event. Search for the **RetailCDXSeedDataBase** class, and then open it in the designer. Right-click the **registerCDXSeedDataExtension** delegate, and then select **Copy event handler**.
8. Go to the event handler class that you created, and paste the following event handler code into it.

    ```
    if (originalCDXSeedDataResource == resourceStr(RetailCDXSeedDataAX7))
    {
        resources.addEnd(resourceStr(RetailCDXSeedDataAX7_Custom));
    }
    ```

    > [!NOTE]
    > Because there are two definitions for CDX seed data in the system, you must specify that your extension CDX seed data should be added only if the CDX seed data that is being generated is the version that you're trying to extend. If the **if** condition is removed, your extension CDX seed data could also be applied on top of the N-1 CDX seed data and cause unintended results.

    You don't have to create separate resource files for the various scenarios that are mentioned later. You can have one file that contains all the custom job information and register that file from the extension class.

    Whenever the Retail initialization class runs, it looks for any extension that implements this handler. If an extension is found, the runtime will also initialize the custom information that is found in the resource file.

9. Run the Retail initialization by selecting the **Initialize** button on the **General** tab of the **Retail parameters** page.

## Pull data from a new channel database table to a new Retail HQ table by using a push job

To pull data from a new channel table to Retail HQ, you have two options:

+ Create a new resource file, and add the new resource to the event handler as a second line, as shown here.

    ```
    if (originalCDXSeedDataResource == resourceStr(RetailCDXSeedDataAX7))
    {
        resources.addEnd(resourceStr(RetailCDXSeedDataAX7\_Custom));
        resources.addEnd(resourceStr(RetailCDXSeedDataAX7\_Custom1));
    }
    ```

+ Update the existing resource file with the new information, so that you don't have to add a new line. To upload you set the **IsUpload** attribute to **true** in the resource file and add information about your custom pull job, as shown in the following example.

    ```
    <Subjob Id="ContosoRetailSeatReservationTrans" TargetTableSchema="ext" IsUpload="true"
    ReplicationCounterFieldName="ReplicationCounterFromOrigin" AxTableName="ContosoRetailSeatReservationTrans">
        <ScheduledByJobs>
            <ScheduledByJob>P-1000</ScheduledByJob>
        </ScheduledByJobs>
        <AxFields>
            <Field Name="transactionId"/>
            <Field Name="storeId"/>
            <Field Name="terminalId"/>
            <Field Name="contactPhoneNo"/>
            <Field Name="numberOfCustomers"/>
            <Field Name="customerName"/>
            <Field Name="reservationDate"/>
            <Field Name="reservationTime"/>
            <Field Name="replicationCounterFromOrigin"/>
        </AxFields>
    </Subjob>
    ```
> [!NOTE]
> You can either add this new table as part of the existing pull job (P-1000) or create a new pull job.

## Other scenarios
For the remaining push and pull scenarios, only the information for the sample resource file is described, because initialization is the same as we described in the previous sections.

### Push existing columns that aren't mapped as part of any subjobs

You can push the existing unmapped column to either new extension columns or existing columns in the channel database, as shown in the following example. 

```
<Subjob Id="RetailChannelTable" TargetTableSchema="ext">
    <AxFields>
        <Field Name="Payment"/>
        <!-- Existing column which was not pushed to channel db-->
        <Field Name="PaymMode"/>
        <!-- Existing column which was not pushed to channel db-->
        <Field Name="ContosoRetailWallPostMessage"/>
        <!-- New column from the extended table -->
    </AxFields>
</Subjob>
```

If the table has a primary key that isn't **RecId**, your extension table on the channel side should also contain the non-**RecId** primary keys, as shown in the following example.

```
    <Subjob Id="RetailCustTable" TargetTableSchema="ext">
        <AxFields>
            <Field Name="ReturnTaxGroup_W"/>
            <!-- Existing column which was not pushed to channel db-->
            <Field Name="SSNNumber"/>
            <!-- New column from the extended table-->
        </AxFields>
    </Subjob>
</Subjobs>
```

### Pull new columns to an existing table

If you add new columns and want pull in part of the existing table, use the following code.

```
<Subjob Id="RetailTransactionTable" TargetTableSchema="ext" TargetTableName="RetailTransactionTableView">
    <AxFields>
        <Field Name="seatNumber"/>
        <Field Name="serverStaffId"/>
    </AxFields>
</Subjob>
```

### Move an existing subjob to another subjob

To move an existing subjob to another job, you can change the **ScheduledByJob** attribute in the resource file and it is run as part of the event handler.

```
<Subjob Id="DirPartyTable">
    <ScheduledByJobs>
        <ScheduledByJob>1000</ScheduledByJob>
        <!--add existing subjob to another job-->
    </ScheduledByJobs>
```

## CDX sample

In Microsoft Dynamics 365 for Retail App update 4, we added a new sample in RetailSDK\\Code\\Documents\\SampleExtensionsInstructions\\CDX. In the next sections, we discuss the steps and best practices for customizing Retail transactional tables by using extension tables. Another section shows how to customize CDX to upload the customized (extension) tables on the channel side back to Finance and Operations. We have also included a section that describes how to test the customization.

### Setup steps

We recommend that you implement these changes on an untouched Retail software development kit (SDK). Alternatively, you can put the SDK under source control, such as Microsoft Visual Studio Team Services (VSTS), so that you can easily revert your changes at any step. To begin, you import the .axpp package that is located in the SDK. You then run the SQL update script on your channel database.

1. Import the package on the Finance and Operations side that contains the customization code:

    1. Copy the .axpp package from the Retail SDK folder.
    2. Start Microsoft Visual Studio.
    3. Select **Dynamics 365** &gt; **Import project**.
    4. In the **Import project** dialog box, specify the path of the .axpp file.
    5. Select either **Current solution** or **New solution**, according to your preference.
    6. Select **OK** to begin to import the package.

        After the import is completed, you have the files in Solution Explorer.

    7. Build the solution.
    8. Right-click the project, and then select **Synchronize database**.

2. Run the SQL update script:

    1. Copy the **ContosoRetailExtensionTablesUpdate.sql** file from the Retail SDK folder. You can run the other sample files in a similar manner.
    2. Open the script in Microsoft SQL Server Browser, and run the script against your channel database.

    This step creates the extension tables and views that are required in order to customize the transactional tables. Note that the script also creates other tables that are used for other sample scenarios.

### Extend the Finance and Operations data in the sample

The table extension on the Finance and Operations side is already created in the sample. To create it manually, follow these steps.

1. Start Visual Studio.
2. On the menu, select **View** &gt; **Application Explorer**.
3. Select **Data Model** &gt; **Tables** &gt; **RetailTransactionTable**, right-click **RetailTransactionTable**, and then select **Create extension**.

    As a best practice, you should change the default name to something like **RetailTransactionTable.ContosoRetailExtension**. Always add your unique prefix. In this sample, **ContosoRetail** is used as a unique prefix. By using a unique prefix, you help prevent naming conflicts if a table is extended by multiple independent software vendors (ISVs).

4. In the new **RetailTransactionTable.ContosoRetailExtension** table, create two new fields:

    - **Type=string, name=ContosoRetailServerStaffId**: Set the **Extended data type** property to **RetailStaffId**.
    - **Type=int, name=ContosoRetailSeatNumber**: Set the **Extended data type** property to **ContosoRetailSeatNumber**.

5. Save the changes, and build your project.
6. Right-click your project, and then select **Synchronize the database**.

    > [!NOTE]
    > As a best practice, the unique prefix is added to the new column names to help prevent future naming conflicts. A naming conflict can occur if another ISV creates a column that has the same name, or if Microsoft releases an update that uses a column that has the same name. Even though the extension table is created in a different AOT asset, the new columns are added to the original table in SQL.

### Extend the database on the channel side

From the Retail SDK folder, open and run the SQL Server **ContosoRetailExtensionTablesUpdate.sql** script. Several items are created and configured:

+ The **[ext].ContosoRetailTransactionTable** table that has the foreign key and custom (extension) fields is created. In addition to the extension columns that we added in the tables, the extension table on the channel side must have the same primary key columns as the original table on the channel side. Therefore, [ext].RetailTransactionTable\_ContosoRetailExtension has the four primary key columns that are used in [ax].RetailTransactionTable. As a best practice, when you add the primary key columns to the extension table on the channel side, keep the names of the columns the same as the names of the primary key column on the original table. This approach will help you uptake the CDX enhancement that we will release later.
+ The **[ext].RetailTransactionTableView** view that joins the original table on the channel side and the extension table on the channel side is created. This view is required so that CDX can correctly upload and pull the records from the channel extension table back to Retail HQ tables. The [ax].RetailTransactionTable table on the channel side is left-joined with the [ext].ContosoRetailTransactionTable extension table. An inner join in this view could cause unintended results. For example, if a record is created in [ax].RetailTransactionTable, but your custom code doesn't create a corresponding record in the extension table, the resulting view will filter out these records. If a corresponding record isn't found in the extension table, the left join sets the custom columns to **Null**. This behavior could cause issues when CDX pulls that record into Finance and Operations. To avoid these issues, make sure that the custom columns are set (coalesced) to a correct default value, as shown in the sample.
+ CDX is configured to upload and pull the custom columns from the channel extension table back to Finance and Operations. The RetailCDXSeedDataAX7 resource contains the information for the table mapping from Finance and Operations to the channel database. CDX uses this information to create the required data transfer scheduler jobs and subjobs. To include your new extension tables or columns in the data transfer, you must provide a resource file that specifies the customization for the CDX data transfer. As a best practice, use the following naming convention to prevent conflicts: **RetailCDXSeedDataAX7\_ContosoRetailExtension**. (Here, **ContosoRetail** is your unique extension.)

    The sample CDX resource file contains additional customizations. However, for our example for the RetailTransactionTable extension, the section in the following code is the only section that is required in order to pull data from the channel side back to Retail HQ.

    ```
    <RetailCdxSeedData Name="AX7" ChannelDBSchema="ext" ChannelDBMajorVersion="7">
        <Subjobs>
            <!--Adding additional columns to (existing) RetailTransactionTable and wants to pull it back to HQ. For this to work partner must create a view which joins the channel table with the customized column and the original table which has all existing default columns-->
            <Subjob Id="RetailTransactionTable" TargetTableName ="RetailTransactionTableView" TargetTableSchema="ext">
                <!--Notice that there is no mention of the <ScheduledByJobs></ScheduledByJobs> because the subjob is already part of an upload job. -->
                <AxFields>
                    <!--If you notice the existing columns are not listed here in the <Field> tag, it's because the existing fields are already mapped in the main RetailCdxSeedData resource file, we only add the delta here. -->
                    <Field Name="SeatNumber" />
                    <Field Name="ServerStaffId" />
                </AxFields>
            </Subjob>
        </Subjobs>
    </RetailCdxSeedData>
    ```

    This resource contains the extension of the CDX seed data. Notice the following fields in this resource:

    - **ChannelDBSchema='ext'** – This field is included so that the resource reads from the extension schema in the channel database.
    - **&lt;Subjob Id="RetailTransactionTable" TargetTableName ="RetailTransactionTableView" TargetTableSchema="ext"&gt;** – We are using the same subjob ID that Microsoft released to pull data from RetailTransactionTable on the channel side back to Retail HQ. You must make sure that the ID is the same, so that the extensibility framework can determine that you're customizing that subjob. The **TargetTableName** attribute is set to the [ext].RetailTransactionTableView view that you created earlier, so that CDX can read from the unified view and upload that data to the Finance and Operations table. The **AxTableName** attribute isn't specified, because the framework can already determine the **AxTableName** value that the specified subjob uses as a sink. You only have to specify the differences when you customize the RetailCDXSeedDataAX7 resource. Any data that the framework can infer doesn't have to be added by extensions. Similarly, in the **&lt;AXFields&gt;&lt;/AXFields&gt;** section, you can see that we specified only the custom or new fields, because the extensibility framework can determine the list of remaining fields from the specified subjob ID.

+ The CDX module that has the CDX customization resource is updated. To apply the customization that is specified in RetailCDXSeedDataAX7\_ContosoRetailExtension, you must subscribe to the registerCDXSeedDataExtension delegate. By subscribing to this event, you help guarantee that the customization is applied when initialization of the CDX seed data is run.

#### Subscribe to the registerCDXSeedDataExtension delegate

1. Select **View** &gt; **Application Explorer**.
2. Search for the **RetailCDXSeedDataBase** class.
3. Right-click the class, and then select **Open in designer**.
4. In the designer, in the list of delegates and methods, select the **registerCDXSeedDataExtension** delegate.
5. Right-click, and then select **Copy event handler**. The method signature that you must implement is copied, so that CDX picks up the customized resource for CDX seed data.
6. Create a new class, and give it a name, such as **ContosoRetailCDXSeedDataAX7EventHandler**. You can specify any name. However, as a best practice, be sure to prefix the class name with your prefix.
7. Paste the code that you copied in step 5.

    ```
    class ContosoRetailCDXSeedDataAX7EventHandler
    {
        /// <summary>
        /// Registers the extension CDX seed data resource to be used during CDX seed data generation.
        /// </summary>
        /// <param name="result">The result object which is used to return the resource name.</param>
        [SubscribesTo(classStr(RetailCDXSeedDataBase), delegateStr(RetailCDXSeedDataBase, registerCDXSeedDataExtension))]
        public static void RetailCDXSeedDataBase_registerCDXSeedDataExtension(str originalCDXSeedDataResource, List resources)
        {
        }
    }
    ```

8. The CDX extensibility framework calls this method when you select the Retail initialization. To help guarantee that the CDX extensibility module uses the CDX customization, paste the following code into the preceding method.
    
    ```
    if (originalCDXSeedDataResource == resourceStr(RetailCDXSeedDataAX7))
    {
        resources.addEnd(resourceStr(RetailCDXSeedDataAX7_ContosoRetailExtension));
    }
    ```
    
    Before you add your custom resource to the list, you must verify that the originalCDXSeedDataResource resource that is being processed is RetailCDXSeedDataAX7. Otherwise, you might cause unintended results.

9. To initialize or reinitialize the CDX module with the customized configuration, follow these steps:

    1. Go to **Retail** &gt; **Headquarters setup** &gt; **Retail scheduler** &gt; **Scheduler jobs** &gt; **Initialize retail scheduler**.
    2. In the dialog box that appears, select **Delete existing configuration**.
    3. Select **OK** to start the initialization.

    When the initialization is completed, the CDX scheduler jobs, subjob definitions, and distribution schedules are updated by using the original RetailCDXSeedDataAX7 resource and the customized RetailCDXSeedDataAX7\_ContosoRetailExtension resource.

#### Test the customization

1. Verify that your customization works correctly:

    1. After the initialization is completed, go to **Retail** &gt; **Headquarters setup** &gt; **Retail scheduler**, and then select the **Scheduler subjobs** link.
    2. On the subjobs table, search for the **RetailTransactionTable** subjob ID.
    3. On the **Set up** FastTab, verify that the **Channel table name** field is set to **[ext].RetailTransactionTableView**.
    4. In the details section, in the **Channel field mapping** section, verify that the new custom (extension) columns are listed in the mapping.

2. Test that the CDX job will upload and pull from the original and extension tables on the channel side by using their unified view:

    1. Create some transactions in Retail Modern POS (MPOS).
    2. Because the extension table isn't used in the Commerce Runtime (CRT) and MPOS, you must manually insert data into the extension table. Run the following script after you change the required values.

        ```
        INSERT INTO [ext].[CONTOSORETAILTRANSACTIONTABLE] (
        [CONTOSORETAILSEATNUMBER],
        [CONTOSORETAILSERVERSTAFFID],
        [TRANSACTIONID],
        [STORE],
        [CHANNEL],
        [TERMINAL],
        [DATAAREAID])
        VALUES (
        1, /*normally this needs to be an existing seat number from ContosoRetailSeatingData table, but for this test add any number*/
        '000160' /*add any staff ID here*/,
        'HOUSTON-HOUSTON-11-101',/\*add the transaction id you just created */
        'HOUSTON', /*add the store used to create the transaction */
        5637144592, /*add the channel RecId of the store used to create the transaction*/
        'HOUSTON-11', /*add the terminalId used to create the transaction*/
        'USRT' /*add the dataareaId used by the store*/)
        GO
        ```

        Repeat this step for the other transactions. Don't add corresponding data in [ext].[CONTOSORETAILTRANSACTIONTABLE] for some of the transactions that you created in MPOS. In this way, you can verify that the data from [ax].RetailTransactionTable is pulled and uploaded even if there is no corresponding data in the extension table.

    3. Go to **Dynamics 365** > **Retail** &gt; **Retail IT**, and then select **Distribution schedule**.
    4. In the list of distribution schedules, select **P-0001**. This distribution schedule contains the RetailTransactionTable subjob that you customized.
    5. On the Action Pane, select **Run**. When the confirmation message appears, select **Yes**.
    6. On the Action Pane, select **History** to open the **History** page, where you can verify that the uploaded session was completed successfully.
    7. On the **History** page, verify that there is a new upload session record. Also verify that the status of the record is set to **Applied**, and that the **Rows Affected** value isn't **0** (zero).

3. If the upload session is applied successfully, go to **Retail** &gt; **Inquiries and reports** &gt; **Retail store transactions**, and search for the new transactions that you just uploaded. Verify that the transactions, seat number, and server staff ID custom columns have the expected values.

    Additionally, verify that the transactions that don't have a corresponding record in the [ext].ContosoRetailTransactionTable extension table on the channel side are also uploaded. Verify that these transactions have default values for the seat number and server staff ID. The seat number should be set to **0** (zero), and the server staff ID should be set to **000160**.
