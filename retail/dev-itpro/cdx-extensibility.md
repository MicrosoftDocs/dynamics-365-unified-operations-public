---
# required metadata

title: CDX extensibility
description: This topic describes the POS topology.
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

Commerce Data Exchange is a system that transfers data between Retail headquarters and retail channels, such as online stores or brick-and-mortar stores. The data transfer between Retail HQ and channel database is controlled by scheduler jobs. Each scheduler job contains a list of scheduler sub jobs. The scheduler sub jobs contain the source and destination table names and the transfer field mapping of these tables. There are two ways to configure the data sync between the Retail HQ and channel database:

+ Configure all the custom jobs and sub jobs using the CDX configuration UI
+ Extend the retail initialization class using the extension points provided to support custom jobs and sub jobs for both push and pull.

The advantage of using option 2 is you no need to configure the custom jobs in different environments (dev, test, production) instead run the retail initialization button under Retail parameters which will automatically create the custom job information’s in CDX for the data sync.

This topic covers how you can extend Retail initialization class to support custom Commerce Data Exchange (CDX) sync using the extension points newly added in Dynamics 365 for Finance and Operations or Dynamics 365 for Retail platform update 8.

There are different scenarios for data transfer data between Retail Headquarters and channel database:
+ Sending data from new HQ table to new channel database table using download job.
+ Pull data from new channel database table to new HQ table using push job.

## Sending data from new HQ table to new channel database table using download job

If you created a new Retail HQ and channel table and if you want to push the data between two tables, follow the below steps:

Before pushing or pulling the data, you need to understand the different metadata definition in the xml resource file (The resource file contains the custom job information which will be initialized in your environment to push and pull data). How to create a new resources files is described below:

+ ChannelDBSchema – Extension schema you created in the channel database.
+ TargetTableSchema - Extension schema you created in the channel database to add your custom tables.
+ AxTableName – AX table name
+ IsUpload – This flag determines whether the job is push or pull (whether you want to send data from the HQ to channel or pull data from channel to HQ) by default the value is false, it means you are sending data from HQ to channel.
+ ScheduledByJob - It contains one or more sub jobs
+ Subjob – Each individual table is added as subjob and each subjob is scheduled by one or more scheduler jobs.
+ TargetTable – Channel database table name, the target table which the push or pull job need to send data. If this value is not specified, the system assumes the target and source table name is same.

1. Create your custom Dynamics 365 project and add custom table using AOT.
1. Create a new resource file to add all custom job information’s. The template for the resource file is:

```
<RetailCdxSeedData ChannelDBMajorVersion="7" ChannelDBSchema="ext" Name="AX7">
    <Jobs>
    </jobs>
    <Subjobs>
        <Subjob Id="" TargetTableSchema="" TargetTableName="">
    </Subjobs>
 </RetailCdxSeedData>
```

1. Create a new Resource (xml file) in Dynamics 365 using AOT, in the resource xml file specify the new table and new job details like below. Note: Either you can add the new table part of the existing job or create a new job and add this table, in this case we are creating a new job id =”7000” and custom table = “ContosoRetailSeatingArrangementData”

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

    TargetTable name is not specified here by default the system assume the target table name on the channel side is same name as the AXTable. If the target table name on the channel side is different than the source (AX table) name then in the &lt;Subjob&gt; node you can set the channel table name using the &lt;TargetTableName&gt; attribute.

    Similarly, in the mapping section only the ax field name is specified, by default the assumption is same field name is being used on the channel side as well. If the field name on the corresponding channel table is different than the AX side then you can specify that in the mapping by setting the channel field name on the &lt;ToName&gt; attribute of the &lt;Field&gt; node.

1. Right click the project and click Add > New Item

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

    Note: Since there are two CDX seed data definition in the system it’s imperative to specify that your extension CDX seed data is only added if the CDX seed data being generated is the version you are trying to extend that why the condition is important. If the if condition is removed your extension cdx seed data could be applied on top of the N-1 CDX seed data as well which may cause unintended consequences.

    Also, you no need to create separate resource file for different scenarios mentioned below you can have one file with all the custom job information and register it from the extension class.

    Whenever the retail initialize class runs it looks for any extension which implemented this handler if found along with the standard it will also initialize the custom information found in the resource file.

1. Run the retail initialize by clicking the Initialize button under Retail parameters &gt; General tab.

## Pull data from new channel database table to new HQ table using push job:

To pull data from new channel table to HQ the pattern remains the same, either create a new resource file and add the new resource to the event handler as second line:

'''
if (originalCDXSeedDataResource == resourceStr(RetailCDXSeedDataAX7))

{

resources.addEnd(resourceStr(RetailCDXSeedDataAX7\_Custom));

resources.addEnd(resourceStr(RetailCDXSeedDataAX7\_Custom1));

}
'''

Or update the existing resource file with the new information, so that you don’t need to add new line.

To upload you have set the attribute IsUpload=”true”, In the resource file add information about your custom pull job:

**Sample:**

```
<Subjob Id="ContosoRetailSeatReservationTrans" TargetTableSchema="ext" IsUpload="true" ReplicationCounterFieldName="ReplicationCounterFromOrigin" AxTableName="ContosoRetailSeatReservationTrans">
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
For the rest of the push and pull scenarios only the sample resource file information is described because how to initialize is same as what we did in previous steps.

### Push existing columns which is not mapped part of any sub jobs:

You can either push the existing unmapped column to new extension columns or existing columns in channel DB:

**Sample resource file:**

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

Suppose if the table has a non RecId primary key then your channel side extension table should also contain the non-RecId primary keys.

**Sample resource file:**

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

**Pull new columns to existing table:**

Suppose if you added new columns and want it to pull part of the existing table:

Sample resource:

```
<Subjob Id="RetailTransactionTable" TargetTableSchema="ext" TargetTableName="RetailTransactionTableView">
    <AxFields>
        <Field Name="seatNumber"/>
        <Field Name="serverStaffId"/>
    </AxFields>
</Subjob>
```

**Move existing sub job to another sub job:**

Suppose if you want to move existing sub job to another job then just change the scheduled by job attribute in the resource file and execute it part of the event handler.

```
<Subjob Id="DirPartyTable">
    <ScheduledByJobs>
        <ScheduledByJob>1000</ScheduledByJob>
        <!--add existing subjob to another job-->
    </ScheduledByJobs>
```

**SAMPLE OVERVIEW:**

We added new sample in RetailSDK\\Code\\Documents\\SampleExtensionsInstructions\\CDX in Dynamics 365 for Retail – App update 4 to help with the CDX extensibility. This sample describes the steps and best practices for customizing retail transactional tables by using extension tables and also show how to customize CDX to upload the customized (extension) channel side tables back to AX. At the end there is also a section that describes how to test the customization.

**SETUP STEPS:**

It is advised that you do these changes on an untouched Retail SDK. Or have it under source control (VSO or similar), so that you could revert at any steps easily. import the. axpp package located in the SDK and run the SQL update script on your channel database before going through the below steps: descriptions below.

**How to import the AX side package that contains the customization code:**

1.  copy the. axpp package from the SDK folder

2.  open VS &gt; click on Dynamics 365&gt; click on "Import project"

3.  in the import project form specify the. axpp file path.

4.  select 'current solution' or 'new solution' based on your preference.

5.  click OK to start importing the package.

6.  once the import is done you will have the ax files in your solution explorer.

7.  build the solution.

8.  right click on the project and click on Synchronize database.

**Run the SQL update script:**

1.  copy the ContosoRetailExtensionTablesUpdate.sql. from the Retail SDK folder. Similarly, you can run the other sample files.

2.  open the script in SQL browser and run it against your channel database.

3.  This will create the extension tables and views required to customize the transactional tables. Note the script also creates other tables which are used for other sample scenarios.

**SAMPLE HOW TO STEPS AND EXPLANATIONS**

**1. Extending the AX data:**

The AX side table extension is already created in the sample. But if you want to create manually then follow the below steps:

1.  Launch Visual Studio.

2.  Go to View &gt; Application Explorer.

3.  Select Data Model &gt; Tables &gt; RetailTransactionTable, right-click on it, select "Create extension".

As a best practice, it's good to change the default name to something like RetailTransactionTable.ContosoRetailExtension. always add your unique prefix. In this sample 'ContosoRetail' is used as a unique prefix. This is helpful to avoid naming conflicts if table is extended by multiple ISVs.

1.  In new table "RetailTransactionTable.ContosoRetailExtension" create two new fields:

    1.  Type=string, name=ContosoRetailServerStaffId - set the Extended data type property to RetailStaffId.

    2.  Type=int, name=ContosoRetailSeatNumber - Extended data type property is set to ContosoRetailSeatNumber.

2.  Save the changes and build your project.

3.  Right click on your project and click on synchronize the database.

**Note:** The unique prefix is added to the new column names as a best practice to avoid future naming conflicts. The naming conflict can occur if another ISV creates a column with the same name or if microsoft ships an update which uses a column with the same name. Even though the extension table is created in a different AOT asset, in SQL the new columns are added to the original table.

**2. Extending the channel side database:**

From the Retail SDK folder, open and run at SQL Server file 'ContosoRetailExtensionTablesUpdate.sql' This will create:

> 1. Table \[ext\].ContosoRetailTransactionTable with the foreign key and custom (extension) fields.

In addition to the extension columns we added in the AX side tables, the channel side extension table also need to have the same primary key columns as the original channel side table. That's why \[ext\].RetailTransactionTable\_ContosoRetailExtension has the four primary key columns used in \[ax\].RetialTransactionTable. As a best practice when you add the primary key columns to the channel side extension table keep the name of the columns same as the primary key column names on original. This will help you to uptake the CDX enhancement Microsoft will ship out in the future easily.

> 2. View: \[ext\].RetailTransactionTableView joining the original channel side table and the extension channel side table.

This view is required for CDX to properly upload/pull the records from the channel extension table back to HQ tables. Channel side table \[ax\].RetailTransactionTable is left joined with the extension table \[ext\].ContosoRetailTransactionTable. Using an inner join in this view may have unintended consequence. For example if a record is created in \[ax\].RetailTransactionTable but your custom code doesn't create a corresponding record in the extension table, then the resulting view will filter out this records. When corresponding record is not found in the extension table, left join will set the custom columns to Null. This could cause issues when CDX pulls that record to AX. To avoid this, make sure the custom columns are defaulted (Coalesced) to a proper value as shown in the sample.

> 3. Configure CDX to upload/pull the custom columns from the channel extension table back to AX.

The resource RetailCDXSeedDataAX7 contains the AX to channel table mapping information that is used by CDX to create the necessary data transfer scheduler jobs and sub jobs. To include your new extension tables or columns in the data transfer you must provide a resource file that specifies the CDX data transfer customization. As a best practice use this naming convention to avoid conflicts. RetailCDXSeedDataAX7\_ContosoRetailExtension. 'ContosoRetial' your unique extension.

The sample CDX resource file contain additional customizations but for our RetailTransactionTable extension example this is the only section that would be required to pull data from the channel side and back to HQ.

&lt;RetailCdxSeedData Name="AX7" ChannelDBSchema="ext" ChannelDBMajorVersion="7"&gt;

&lt;Subjobs&gt;

> &lt;!--Adding additional columns to (existing) RetailTransactionTable and wants to pull it back to HQ. For this to work partner must create a view which joins the channel table with the customized column and the original table which has all existing default columns--&gt;
>
> &lt;Subjob Id="RetailTransactionTable" TargetTableName ="RetailTransactionTableView" TargetTableSchema="ext"&gt;
>
> &lt;!--Notice that there is no mention of the &lt;ScheduledByJobs&gt;&lt;/ScheduledByJobs&gt; because the subjob is already part of an upload job. --&gt;

&lt;AxFields&gt;

> &lt;!--If you notice the existing columns are not listed here in the &lt;Field&gt; tag, this is because the existing fields are already mapped in the main RetailCdxSeedData resource file, we only add the delta here. --&gt;
>
> &lt;Field Name="SeatNumber" /&gt;
>
> &lt;Field Name="ServerStaffId" /&gt;
>
> &lt;/AxFields&gt;
>
> &lt;/Subjob&gt;
>
> &lt;/Subjobs&gt;
>
> &lt;/RetailCdxSeedData&gt;

Notice the following fields at this resource (which contains the CDX seed data extension):

> ChannelDBSchema='ext' so it reads from the extension schema at channel DB.
>
> &lt;Subjob Id="RetailTransactionTable" TargetTableName ="RetailTransactionTableView" TargetTableSchema="ext"&gt;

We are using the same subjob Id that is shipped by Microsoft to pull data from the channel side RetailTransactionTable back to HQ. It's important to make sure the Id is the same so that the extensibility framework knows that you are customizing that subjob. The "TargetTableName" attribute is set to the view \[ext\].RetailTransactionTableView created above so that CDX can read from the unified view and upload that data to the AX table. The AxTableName attribute is not specified as the framework already knows the AxTableName that the specified subjob uses as a sink. A pattern that will be evident to you soon is that you only need to specify the deltas when customizing the RetailCDXSeedDataAX7 resource. Any data that the framework can infer is not required to be added by extensions. If you apply the above pattern to the &lt;AXFields&gt;&lt;/AXFields&gt; section, you can see that we only specified the custom/new fields. The reason for this is that the extensibility framework can figure out the remaining list of fields from the specified subjob Id.

> 4. Updating the CDX module with the CDX customization resource.

To apply the customization specified in RetailCDXSeedDataAX7\_ContosoRetailExtension we need to subscribe to the registerCDXSeedDataExtension delegate. Subscribing to this event guarantee that the customization is applied when the CDX seed data initialization is run.

**How to subscribe to the registerCDXSeedDataExtension delegate:**

1.  Go to View &gt; Application Explorer.

2.  Search for the class RetailCDXSeedDataBase

3.  Right click on the class and click open in designer.

4.  Select the registerCDXSeedDataExtension delegate from the list of delegates and methods shown on the designer.

5.  Right-click and click on copy event handler. This will copy the method signature you need to implement so that CDX picks up the customized CDX seed data resource.

6.  Create a new class, and name the class ContosoRetailCDXSeedDataAX7EventHandler, any name will do but as a best practice don't forget to prefix the class name with your prefix.

7.  Paste the code you copied in step 5.

class ContosoRetailCDXSeedDataAX7EventHandler

{

> /// &lt;summary&gt;
>
> /// Registers the extension CDX seed data resource to be used during CDX seed data generation..
>
> /// &lt;/summary&gt;
>
> /// &lt;param name="result"&gt;The result object which is used to return the resource name.&lt;/param&gt;
>
> \[SubscribesTo(classStr(RetailCDXSeedDataBase), delegateStr(RetailCDXSeedDataBase, registerCDXSeedDataExtension))\]
>
> public static void RetailCDXSeedDataBase\_registerCDXSeedDataExtension(str originalCDXSeedDataResource, List resources)
>
> {
>
> }

}

1.  This method will be called by the CDX extensibility framework when you clikc the retail initialization.

To ensure the CDX customization is used by the CDX extensibility module copy the below code in the above method

> if (originalCDXSeedDataResource == resourceStr(RetailCDXSeedDataAX7))
>
> {
>
> resources.addEnd(resourceStr(RetailCDXSeedDataAX7\_ContosoRetailExtension));
>
> }

It's important to check the originalCDXSeedDataResource being processed is RetailCDXSeedDataAX7 before adding your custom resource to the list. Not doing so may result in unintended consequence that we won't delve into at this point.

1.  To (re)initialize CDX module with the customized configuration execute the following steps.

<!-- -->

1.  Go to Retail&gt; Headquarters setup&gt; Retail scheduler&gt; Scheduler jobs&gt;

2.  Click on Initialize retail scheduler

3.  On the dialog that opens check the Delete existing configuration.

4.  Click ok to start the initialization.

when the initialization is completed the CDX scheduler jobs, subjob definitions and distribution schedules will be updated using the original RetailCDXSeedDataAX7 and the customized RetailCDXSeedDataAX7\_ContosoRetailExtension resources.

**How to test the customization**:

1) To see that your customization is working properly.

1.  After the initialization is completed go to Retail &gt; Headquarters setup &gt; Retail scheduler &gt; and click on "Scheduler subjobs" link

2.  On the subjobs table search for "RetailTransactionTable" subjob id.

3.  On the "Set up" fast tab verify that the "Channel table name" is set to \[ext\].RetailTransactionTableView.

4.  On the detail section go to the "Channel field mapping" section and verify that the new custom (extension) columns are listed in the mapping.

2) To test that the CDX job will upload/pull from the channel side original and extension table using their unified view.

1.  Create a couple of transactions in MPOS.

2.  Since the extension table is not used in the CRT/MPOS we must manually insert data to the extension table.

**Run the following script after changing the necessary values:**

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

Repeat the same for the other transactions. Do not add a corresponding data in the \[ext\].\[CONTOSORETAILTRANSACTIONTABLE\] for some of the transactions you created in POS. This is required to check that the data from \[ax\].RetailTransactionTable is pulled/uploaded even if there is no corresponding data in the extension table.

1.  Go to AX &gt; Retail &gt; Retail IT &gt; click on Distribution schedule.

2.  From the list of distribution schedule select P-0001 which contains the RetialTransactionTable subjob we customized.

3.  Click on "Run" from the top Action menu pane. Click Yes when the confirmation dialog pops up.

4.  Click on "History" from the Action menu pane. (This is where we check if the uploaded session is completed successfully or not.

5.  On the history page - Check if there is a new upload session record and that its status is set to Applied and Rows Affected is not zero.

If the upload session is applied successfully, Go to Retail &gt; Inquiries and reports &gt; Retail store transactions and search for the new transaction that were just uploaded and verify the transactions, seat number and the server staff Id custom columns have the expected value.

Also verify the transactions which do not have a corresponding record in the channel side extension table \[ext\].ContosoRetailTransactionTable are also uploaded. Check whether these transactions have default value for seat number and server staff ID, seat number = 0 and serer staff id = ''000160''
