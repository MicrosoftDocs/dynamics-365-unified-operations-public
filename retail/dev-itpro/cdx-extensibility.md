---
# required metadata

title: CDX extensibility
description: This topic covers how you can extend the Retail initialization class to support custom Commerce Data Exchange (CDX) synchronization.
author: mugunthanm
manager: AnnBe
ms.date: 09/15/207
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
# CDX Extensibility

This topic covers how you can extend the Retail initialization class to support custom Commerce Data Exchange (CDX) synchronization using the extension points newly added in Dynamics 365 for Finance and Operations or Dynamics 365 for Retail platform update 8.

Commerce Data Exchange is a system that transfers data between Retail headquarters (Retail HQ) and retail channels, such as online stores or brick-and-mortar stores. The data transfer between Retail HQ and the channel database is controlled by scheduler jobs. Each scheduler job contains a list of scheduler subjobs. The scheduler subjobs contain the source and destination table names and the transfer field mapping of these tables. There are two ways to configure the data sync between the Retail HQ and the channel database:

+ Configure all the custom jobs and subjobs using the CDX configuration user interface.
+ Extend the retail initialization class using the extension points provided to support custom jobs and subjobs for both push and pull.

The advantage of using the retail initialization class is you don't need to configure the custom jobs in different environments (dev, test, production). Instead, you can run the retail initialization button under Retail parameters which will automatically create the custom job information’s in CDX for the data sync.

There are different scenarios for data transfer data between Retail HQ and the channel database:
+ Sending data from new HQ table to new channel database table using download job.
+ Pull data from new channel database table to new HQ table using push job.

## Sending data from new HQ table to new channel database table using download job

Before pushing or pulling data, you need to understand the different metadata definitions in the xml resource file. The resource file contains the custom job information which will be initialized in your environment to push and pull data. The resource files you'll need to configure are:

+ ChannelDBSchema – Extension schema you created in the channel database.
+ TargetTableSchema - Extension schema you created in the channel database to add your custom tables.
+ AxTableName – The table name.
+ IsUpload – This flag determines whether the job is push or pull (whether you want to send data from the HQ to channel or pull data from channel to HQ) by default the value is false, it means you are sending data from HQ to channel.
+ ScheduledByJob - It contains one or more subjobs.
+ Subjob – Each individual table is added as subjob and each subjob is scheduled by one or more scheduler jobs.
+ TargetTable – Channel database table name, the target table which the push or pull job need to send data. If this value is not specified, the system assumes the target and source table name is same.

If you created a new Retail HQ and a new channel table and if you want to push the data between two tables, follow the below steps:

1. Create your custom Dynamics 365 project and add a custom table using the AOT.
1. Create a new resource file to add all custom job information. The template for the resource file is:

    ```
    <RetailCdxSeedData ChannelDBMajorVersion="7" ChannelDBSchema="ext" Name="AX7">
        <Jobs>
        </jobs>
        <Subjobs>
            <Subjob Id="" TargetTableSchema="" TargetTableName="">
        </Subjobs>
     </RetailCdxSeedData>
    ```

1. Create a new Xml resource in Dynamics 365 using the AOT. In the resource xml file specify the new table and new job details as shown in the followig code example. Note: Either you can add the new table part of the existing job or create a new job and add this table. In this case we are creating a new job id =”7000” and custom table = “ContosoRetailSeatingArrangementData”.

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

    TargetTable name is not specified here by default. The system assumes the target table name on the channel side has the same name as AXTable. If the target table name on the channel side is different than the source (AX table) name, then in the <Subjob> node you can set the channel table name using the <TargetTableName> attribute.

    Similarly, in the mapping section only the AxField name is specified. By default the assumption is same field name is being used on the channel side as well. If the field name on the corresponding channel table is different than the AX side then you can specify that in the mapping by setting the channel field name in the ToName attribute of the <Field> node.

1. Right click the project and click Add > New Item.
1. In the Add New item window, select Resources and name the resource file as RetailCDXSeedDataAX7\_Custom and click **Add**.

    ![Add new item](media/cdx-ext-1.png)

1. In the Select a Resource file window locate the resource file you created in step 2 and click Open.
1. Add a new AX class that will be used to handle the registerCDXSeedDataExtension event. Search for RetailCDXSeedDataBase class. Open the class in the designer. Right click on registerCDXSeedDataExtension delegate and click 'Copy event handler'
1. Go to the even handler class you created in step 6 and paste the below event handler code.

    ```
    if (originalCDXSeedDataResource == resourceStr(RetailCDXSeedDataAX7))
    {
        resources.addEnd(resourceStr(RetailCDXSeedDataAX7\_Custom));
    }
    ```

    Note: Since there are two CDX seed data definitions in the system, you must specify that your extension CDX seed data is only added if the CDX seed data being generated is the version you are trying to extend. If the if condition is removed your extension CDX seed data could be applied on top of the N-1 CDX seed data as well which may cause unintended consequences.

    Also, you don't have to create separate resource files for the different scenarios mentioned belo. You can have one file with all the custom job information and register it from the extension class.

    Whenever the retail initialize class runs it looks for any extension which implemented this handler. If found along with the default, it will also initialize the custom information found in the resource file.

1. Run the retail initialization by clicking the Initialize button under Retail parameters > General tab.

## Pull data from new channel database table to new HQ table using push job:

To pull data from new channel table to Retail HQ, there are two options:

+ Create a new resource file and add the new resource to the event handler as second line:

    ```
    if (originalCDXSeedDataResource == resourceStr(RetailCDXSeedDataAX7))
    {
        resources.addEnd(resourceStr(RetailCDXSeedDataAX7\_Custom));
        resources.addEnd(resourceStr(RetailCDXSeedDataAX7\_Custom1));
    }
    ```

+ Update the existing resource file with the new information, so that you don’t need to add new line. To upload you have set the attribute IsUpload=”true”, in the resource file add information about your custom pull job as shown in the following code example:

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
Note: You can either add this new table part of the existing pull job (P-1000) or create a new one.

## Other scenarios
For the rest of the push and pull scenarios only the sample resource file information is described, because initialization is same as in the previous steps.

### Push existing columns which is not mapped part of any subjobs

You can either push the existing unmapped column to new extension columns or existing columns in channel DB, as shown in the following code example. 

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

If the table has a non RecId primary key then your channel side extension table should also contain the non-RecId primary keys, as shown in the following code example:

```
    <Subjob Id="RetailCustTable" TargetTableSchema="ext">
        <AxFields>
            <Field Name="ReturnTaxGroup\_W"/>
            <!-- Existing column which was not pushed to channel db-->
            <Field Name="SSNNumber"/>
            <!-- New column from the extended table-->
        </AxFields>
    </Subjob>
</Subjobs>
```

### Pull new columns to existing table:

If you add new columns and want it to pull part of the existing table, you would use the following code:

```
<Subjob Id="RetailTransactionTable" TargetTableSchema="ext" TargetTableName="RetailTransactionTableView">
    <AxFields>
        <Field Name="seatNumber"/>
        <Field Name="serverStaffId"/>
    </AxFields>
</Subjob>
```

### Move existing sub job to another sub job

If you want to move an existing subjob to another job, you can change the scheduled by job attribute in the resource file and execute it part of the event handler.

```
<Subjob Id="DirPartyTable">
    <ScheduledByJobs>
        <ScheduledByJob>1000</ScheduledByJob>
        <!--add existing subjob to another job-->
    </ScheduledByJobs>
```

## CDX sample

We added new sample in RetailSDK\\Code\\Documents\\SampleExtensionsInstructions\\CDX in Dynamics 365 for Retail – App update 4. The next sections discuss the steps and best practices for customizing retail transactional tables by using extension tables. Another section shows you how to customize CDX to upload the customized (extension) channel side tables back to Dynamics AX for Finance and Operations. We also included a section that describes how to test the customization.

## Setup steps

We recommend that you implement these changes on an untouched Retail SDK. Another options is to place the SDK under source control, such as VSTS, so that you can easily revert at any step. You start by importing the axpp package located in the SDK and running the SQL update script on your channel database.

1. Import the AX side package that contains the customization code.

    a. Copy the. axpp package from the SDK folder.

    b. Open Visual Studio. Click on Dynamics 365 > Import project.

    c. In the import project form specify the axpp file path.

    d. Select 'Current solution' or 'New solution' based on your preference.

    e. Click OK to start importing the package.

    f. Once the import is done you will have the files in Solution Explorer.

    g. Build the solution.

    h. Right-click on the project and click on Synchronize database.

2. Run the SQL update script.

    a. Copy the ContosoRetailExtensionTablesUpdate.sql. from the Retail SDK folder. Similarly, you can run the other sample files.

    b. Open the script in SQL browser and run it against your channel database.

    This will create the extension tables and views required to customize the transactional tables. Note the script also creates other tables which are used for other sample scenarios.

### Extending the Dynamics AX data in the sample

The Dynamics AX side table extension is already created in the sample. If you want to create it manually then follow the below steps:

1. Start Visual Studio.

2. On the menu, click View > Application Explorer.

3. Select Data Model > Tables > RetailTransactionTable, right-click on it, select "Create extension".

    As a best practice, it's good to change the default name to something like RetailTransactionTable.ContosoRetailExtension. always add your unique prefix. In this sample 'ContosoRetail' is used as a unique prefix. This is helpful to avoid naming conflicts if table is extended by multiple ISVs.

4. In new table "RetailTransactionTable.ContosoRetailExtension" create two new fields:

    - Type=string, name=ContosoRetailServerStaffId - set the Extended data type property to RetailStaffId.
    - Type=int, name=ContosoRetailSeatNumber - Extended data type property is set to ContosoRetailSeatNumber.

5.  Save the changes and build your project.
6.  Right click on your project and click on synchronize the database.

    Note: The unique prefix is added to the new column names as a best practice to avoid future naming conflicts. The naming conflict can occur if another ISV creates a column with the same name or if microsoft ships an update which uses a column with the same name. Even though the extension table is created in a different AOT asset, in SQL the new columns are added to the original table.

### Extending the channel side database

From the Retail SDK folder, open and run at SQL Server file 'ContosoRetailExtensionTablesUpdate.sql'. Several items are created and configured:

+ The **\[ext\].ContosoRetailTransactionTable** with the foreign key and custom (extension) fields is created. In addition to the extension columns we added in the AX side tables, the channel side extension table also need to have the same primary key columns as the original channel side table. That's why \[ext\].RetailTransactionTable\_ContosoRetailExtension has the four primary key columns used in \[ax\].RetialTransactionTable. As a best practice when you add the primary key columns to the channel side extension table keep the name of the columns same as the primary key column names on original. This will help you to uptake the CDX enhancement Microsoft will ship out in the future easily.

+ The **\[ext\].RetailTransactionTableView** view that joins the original channel side table and the extension channel side table is created. This view is required for CDX to properly upload/pull the records from the channel extension table back to HQ tables. Channel side table \[ax\].RetailTransactionTable is left joined with the extension table \[ext\].ContosoRetailTransactionTable. Using an inner join in this view may have unintended consequence. For example if a record is created in \[ax\].RetailTransactionTable but your custom code doesn't create a corresponding record in the extension table, then the resulting view will filter out this records. When corresponding record is not found in the extension table, left join will set the custom columns to Null. This could cause issues when CDX pulls that record to AX. To avoid this, make sure the custom columns are defaulted (Coalesced) to a proper value as shown in the sample.

+ CDX is configured to upload/pull the custom columns from the channel extension table back to AX. The resource RetailCDXSeedDataAX7 contains the AX to channel table mapping information that is used by CDX to create the necessary data transfer scheduler jobs and sub jobs. To include your new extension tables or columns in the data transfer you must provide a resource file that specifies the CDX data transfer customization. As a best practice use this naming convention to avoid conflicts. RetailCDXSeedDataAX7\_ContosoRetailExtension. 'ContosoRetial' your unique extension.

    The sample CDX resource file contain additional customizations but for our RetailTransactionTable extension example this is the only section that would be required to pull data from the channel side and back to HQ.

    ```
    <RetailCdxSeedData Name="AX7" ChannelDBSchema="ext" ChannelDBMajorVersion="7">
        <Subjobs>
            <!--Adding additional columns to (existing) RetailTransactionTable and wants to pull it back to HQ. For this to work partner must create a view which joins the channel table with the customized column and the original table which has all existing default columns-->
            <Subjob Id="RetailTransactionTable" TargetTableName ="RetailTransactionTableView" TargetTableSchema="ext">
                <!--Notice that there is no mention of the <ScheduledByJobs></ScheduledByJobs> because the subjob is already part of an upload job. -->
                <AxFields>
                    <!--If you notice the existing columns are not listed here in the <Field> tag, this is because the existing fields are already mapped in the main RetailCdxSeedData resource file, we only add the delta here. -->
                    <Field Name="SeatNumber" />
                    <Field Name="ServerStaffId" />
                </AxFields>
            </Subjob>
        </Subjobs>
    </RetailCdxSeedData>
    ```

    Notice the following fields at this resource (which contains the CDX seed data extension):

        - ChannelDBSchema='ext' so it reads from the extension schema at channel DB.
        - <Subjob Id="RetailTransactionTable" TargetTableName ="RetailTransactionTableView" TargetTableSchema="ext">

    We are using the same subjob Id that is shipped by Microsoft to pull data from the channel side RetailTransactionTable back to HQ. It's important to make sure the Id is the same so that the extensibility framework knows that you are customizing that subjob. The "TargetTableName" attribute is set to the view \[ext\].RetailTransactionTableView created above so that CDX can read from the unified view and upload that data to the AX table. The AxTableName attribute is not specified as the framework already knows the AxTableName that the specified subjob uses as a sink. A pattern that will be evident to you soon is that you only need to specify the deltas when customizing the RetailCDXSeedDataAX7 resource. Any data that the framework can infer is not required to be added by extensions. If you apply the above pattern to the &lt;AXFields&gt;&lt;/AXFields&gt; section, you can see that we only specified the custom/new fields. The reason for this is that the extensibility framework can figure out the remaining list of fields from the specified subjob Id.

+ The CDX module with the CDX customization resource is updated. To apply the customization specified in RetailCDXSeedDataAX7\_ContosoRetailExtension we need to subscribe to the registerCDXSeedDataExtension delegate. Subscribing to this event guarantee that the customization is applied when the CDX seed data initialization is run.

#### How to subscribe to the registerCDXSeedDataExtension delegate

1.  Go to View > Application Explorer.
2.  Search for the class RetailCDXSeedDataBase
3.  Right click on the class and click open in designer.
4.  Select the registerCDXSeedDataExtension delegate from the list of delegates and methods shown on the designer.
5.  Right-click and click on copy event handler. This will copy the method signature you need to implement so that CDX picks up the customized CDX seed data resource.
6.  Create a new class, and name the class ContosoRetailCDXSeedDataAX7EventHandler, any name will do but as a best practice don't forget to prefix the class name with your prefix.
7.  Paste the code you copied in step 5.


    ```
    class ContosoRetailCDXSeedDataAX7EventHandler
    {
        /// <summary>
        /// Registers the extension CDX seed data resource to be used during CDX seed data generation..
        /// </summary>
        /// <param name="result">The result object which is used to return the resource name.</param>
        [SubscribesTo(classStr(RetailCDXSeedDataBase), delegateStr(RetailCDXSeedDataBase, registerCDXSeedDataExtension))]
        public static void RetailCDXSeedDataBase\_registerCDXSeedDataExtension(str originalCDXSeedDataResource, List resources)
        {
        }
    }
    ```

1. This method will be called by the CDX extensibility framework when you clikc the retail initialization. To ensure the CDX customization is used by the CDX extensibility module copy the below code in the above method
    
    ```
    if (originalCDXSeedDataResource == resourceStr(RetailCDXSeedDataAX7))
    {
        resources.addEnd(resourceStr(RetailCDXSeedDataAX7\_ContosoRetailExtension));
    }
    ```
    
    It's important to check the originalCDXSeedDataResource being processed is RetailCDXSeedDataAX7 before adding your custom resource to the list. Not doing so may result in unintended consequence that we won't delve into at this point.

1. To (re)initialize CDX module with the customized configuration execute the following steps.

    a. Go to Retail&gt; Headquarters setup&gt; Retail scheduler&gt; Scheduler jobs&gt;
    a. Click on Initialize retail scheduler
    a. On the dialog that opens check the Delete existing configuration.
    a. Click ok to start the initialization.

    When the initialization is completed the CDX scheduler jobs, subjob definitions and distribution schedules will be updated using the original RetailCDXSeedDataAX7 and the customized RetailCDXSeedDataAX7\_ContosoRetailExtension resources.

#### How to test the customization

1. To see that your customization is working properly.
    a. After the initialization is completed go to Retail &gt; Headquarters setup &gt; Retail scheduler &gt; and click on "Scheduler subjobs" link
    a. On the subjobs table search for "RetailTransactionTable" subjob id.
    a. On the "Set up" fast tab verify that the "Channel table name" is set to \[ext\].RetailTransactionTableView.
    a. On the detail section go to the "Channel field mapping" section and verify that the new custom (extension) columns are listed in the mapping.
1. To test that the CDX job will upload/pull from the channel side original and extension table using their unified view.
    a. Create a couple of transactions in MPOS.
    a. Since the extension table is not used in the CRT/MPOS we must manually insert data to the extension table. Run the following script after changing the necessary values

        ```
        INSERT INTO \[ext\].\[CONTOSORETAILTRANSACTIONTABLE\] (
        \[CONTOSORETAILSEATNUMBER\],
        \[CONTOSORETAILSERVERSTAFFID\],
        \[TRANSACTIONID\],
        \[STORE\],
        \[CHANNEL\],
        \[TERMINAL\],
        \[DATAAREAID\])
        VALUES (
        1, /\*normally this needs to be an existing seat number from ContosoRetailSeatingData table, but for this test add any number\*/
        '000160' /\*add any staff ID here\*/,
        'HOUSTON-HOUSTON-11-101',/\*add the transaction id you just created \*/
        'HOUSTON', /\*add the store used to create the transaction \*/
        5637144592, /\*add the channel RecId of the store used to create the transaction\*/
        'HOUSTON-11', /\*add the terminalId used to create the transaction\*/
        'USRT' /\*add the dataareaId used by the store\*/)
        GO
        ```

    Repeat the same for the other transactions. Do not add a corresponding data in the \[ext\].\[CONTOSORETAILTRANSACTIONTABLE\] for some of the transactions you created in POS. This is required to check that the data from \[ax\].RetailTransactionTable is pulled/uploaded even if there is no corresponding data in the extension table.

    a. Go to AX &gt; Retail &gt; Retail IT &gt; click on Distribution schedule.
    a. From the list of distribution schedule select P-0001 which contains the RetialTransactionTable subjob we customized.
    a. Click on "Run" from the top Action menu pane. Click Yes when the confirmation dialog pops up.
    a. Click on "History" from the Action menu pane. (This is where we check if the uploaded session is completed successfully or not.
    a. On the history page - Check if there is a new upload session record and that its status is set to Applied and Rows Affected is not zero.

    If the upload session is applied successfully, Go to Retail &gt; Inquiries and reports &gt; Retail store transactions and search for the new transaction that were just uploaded and verify the transactions, seat number and the server staff Id custom columns have the expected value.

    Also verify the transactions which do not have a corresponding record in the channel side extension table \[ext\].ContosoRetailTransactionTable are also uploaded. Check whether these transactions have default value for seat number and server staff ID, seat number = 0 and serer staff id = ''000160''
