---
# required metadata

title: Add extension properties to a customer entity | Microsoft Docs
description: This tutorial shows how to use extension properties to extend an entity. 
author: josaw1
manager: AnnBe
ms.date: 2016-09-30 22:06:20
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: 61
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 196163
ms.assetid: ab8563fe-8001-43b3-a3a5-83ddc2c58aa9
ms.region: Global
ms.industry: Retail
ms.author: mumani

---

# Add extension properties to a customer entity

This tutorial shows how to use extension properties to extend an entity. 

In this tutorial, an entity is extended in Microsoft Dynamics AX, and persisted in both Dynamics AX and the channel databases. The point of sale (POS) user interface (UI) then provides access to the value. The new value is also written synchronously to Dynamics AX via the Commerce Data Exchange (CDX) transaction service. No customizations are required for the commerce runtime or Retail Server, because extension properties flow automatically. Changes are required in forms, tables, the Real-time Service (RTS) client, CDX, the channel database, and the POS (both Retail Modern POS and Cloud POS). This tutorial doesn't support offline mode.
Create a new Dynamics AX project
--------------------------------

1.  Create a new table that is named **RetailCustPreference** and that references the CustTable table.
2.  Start Microsoft Visual Studio.
3.  Create a new model and project. On the **Dynamics AX** menu, click **Model Management** &gt; **Create Model**.
4.  Create a new model in the USR layer, and then click **Next**.
5.  Add the model to the existing ApplicationSuite package. Click **Next**, and then click **Finish**.
6.  Enter a name for the project, and then click **OK**.
7.  In Solution Explorer, right-click your new project. Select **Add** &gt; **New Item**, and add a new table that is named **RetailCustPreference**.
8.  In your project, double-click **RetailCustPreference** to open the table designer.
9.  Create a new enumeration field that is named **EmailOptIn**, and set the **Enum Type** property to **NoYes**.
10. Create a new string field that is named **AccountNum**. Set the field's extended data type to **CustAccount**, and set the **Mandatory** property to **Yes**.
11. Create a new relation with the CustTable table, and add a new normal relation between **RetailCustPreference.AccountNum** and **CustTable.AccountNum**.
12. Save your changes.
13. In Solution Explorer, right-click your project, and then select **Properties**.
14. Select the **Synchronize database** **on build** check box.
15. Right-click your project, and then select **Build** to build the new code and synchronize the database.
16. When the build is completed, return to the project properties, and clear the **Synchronize database** **on build** check box.

## Update the CustTable form
1.  In Application Explorer, select **User Interface** &gt; **Forms** &gt; **CustTable**. Right-click **CustTable**, and then select **Create Extension**.
2.  Your project now includes a new element that is named **CustTable.Extension**. Double-click this element to open the form designer.
3.  Add a new data source that is named **RetailCustPreference**, and set the **Link Type** property to **OuterJoin**.
4.  On the **CustTable** form on the **Retail** tab page, add a new group that is named **CustomerPreference** and that has the **Caption** property set to **Customer Preference** .
5.  To the **RetailCustPreference** table in the **CustomerPreference** group, add a new check box field that is named **EmailOptIn**.
6.  Add a new class that is named **CustTable\_Extension**. In the code editor, add the following code.

        public static class CustTable_Extension
        {
            [FormDataSourceEventHandler(formDataSourceStr(CustTable, CustTable), FormDataSourceEventType::ValidatingWrite)]
            public static void foo(FormDataSource fds, FormDataSourceEventArgs e)
            {
                FormRun                             form = fds.formRun();
                CustTable                           custTable = fds.cursor() as CustTable;
                RetailCustPreference                retailCustPreference = form.dataSource(formDataSourceStr(CustTable, RetailCustPreference)).cursor() as RetailCustPreference;
                retailCustPreference.AccountNum     = custTable.AccountNum; form.dataSource(formDataSourceStr(CustTable, RetailCustPreference)).write(); 
            } 
        }

7.  Save all your changes, and build your project again.
8.  Run **iisreset**.
9.  In Dynamics AX, go to **Accounts receivable** &gt; **Common** &gt; **Customers** &gt; **All customers**.
10. Edit a customer record. On the **Retail** FastTab, select the **Email Opt In** check box, and then save your change.

## Customize the existing RetailTransactionService class so that it handles the new data correctly
1.  In Application Explorer, right-click the **RetailTransactionService (sys)** class, and then select **Customize**.
2.  Add the following two methods at the end.

        /// <summary>
        /// Processes all Extension properties. This is a sample only. Should be re-factored into its own class for better reuse and better decoupling from RetailTransactionService
        /// </summary>
        /// <param name = "extensionProperties"></param>
        private static void processExtensionProperties(AccountNum accountNum, str extensionProperties)
        {
            XmlElement                  xmlElementExtensionProperties;
            XmlNodeList                 xmlListExtensionProperties;
            int                         i;
            XmlElement                  xmlElementExtensionProperty;
            str                         propertyName;
            str                         propertyValue;
            int                         emailOptInValue;
            if(extensionProperties != null && extensionProperties != '')
            {
                XmlDocument xmlExtensionProperties = new XmlDocument();
                xmlExtensionProperties.loadXml(extensionProperties);
                xmlElementExtensionProperties = xmlExtensionProperties.getNamedElement('ExtensionProperties');
                xmlListExtensionProperties = xmlElementExtensionProperties.childNodes();
                if (xmlListExtensionProperties)
                {
                    for (i = 0; i < xmlListExtensionProperties.length(); i++)
                    {
                        xmlElementExtensionProperty = xmlListExtensionProperties.item(i);
                        if(xmlElementExtensionProperty)
                        {
                            propertyName = xmlElementExtensionProperty.tagName();
                            propertyValue = xmlElementExtensionProperty.innerText();
                            switch(propertyName)
                            {
                                case "EMAILOPTIN":
                                    // update the EMAILOPTIN value
                                    if(propertyValue != null && propertyValue != '')
                                    {
                                        emailOptInValue = str2Int(propertyValue);
                                    }
                                    else
                                    {
                                        emailOptInValue = 0;
                                    }
                                    RetailTransactionService::updateOptIn(accountNum, emailOptInValue);
                                    break;
                                default:
                                    // do something else here...
                                    break; 
                            } 
                        } 
                    } 
                } 
            } 
        }

        /// <summary>
        /// Updates the customer email optin value. This is a sample only. Should be re-factored into its own class for better reuse and better decoupling from RetailTransactionService
        /// </summary>
        /// <param name = "accountnum"></param>
        /// <param name = "emailOptIn"></param>
        /// <returns></returns>
        private static container updateOptIn(AccountNum accountnum, int emailOptIn)
        {
            RetailCustPreference        retailCustPreference;
            boolean validUpdate = false;
            str error = "NO error";
            int fromLine;
            try
            {
                //Extensibility code for cust preference
                select forUpdate EmailOptIn from retailCustPreference  where  retailCustPreference.AccountNum == accountnum;
                if(retailCustPreference.RecId)
                {
                    //retailCustPreference.clear();
                    ttsBegin;
                    retailCustPreference.EmailOptIn = emailOptIn;
                    retailCustPreference.update();
                    ttscommit;
                }
                else
                {
                    retailCustPreference.clear();
                    retailCustPreference.AccountNum = accountNum;
                    retailCustPreference.EmailOptIn = emailOptIn;
                    retailCustPreference.insert();
                }
                validUpdate = true;
            }
            catch(Exception::Error)
            {
                ttsabort;
                error = RetailTransactionServiceUtilities::getInfologMessages(fromLine);
                RetailTracer::Error('RetailTransactionService', funcName(), error);
            }
            // Returning the status as a container
            return [validUpdate, error,retailCustPreference.AccountNum];
        }

3.  Update the **updateCustomerExt** method by adding the following code to the end. (Also add the variable declaration for **customerContainer** on the first line of code.)

        // the third element in container is the account number
        AccountNum accountNum = conPeek(customerContainer, 3);
        RetailTransactionService::processExtensionProperties(accountNum, extensionProperties);
        return customerContainer;

4.  Compile the project.

## Configure CDX to sync the new table
1.  In Dynamics AX, go to **Retail** &gt; **Setup** &gt; **Retail scheduler** &gt; **Retail channel** **schema**, and edit the channel schema by adding a new table:
    1.  Click **Channel tables**, and then click **New**.
    2.  Name the table **ax.RetailCustPreference**, and save it.
    3.  Add the following fields: **ACCOUNTNUM**, **DATAAREAID**, **EMAILOPTIN**, and **RECID**.
    4.  Click **OK**.

2.  Go to **Retail** &gt; **Setup** &gt; **Retail scheduler** &gt; **Scheduler subjobs**, and create a new subjob:
    1.  Set the **Name** field to **RetailCustPreference** and the **Description** field to **RetailCustPreference**.
    2.  Set the **Channel table name** field to **ax.RetailCustPreference**.
    3.  Set the **AX table** field to **RetailCustPreference**.
    4.  Click **Match fields**.
    5.  Click **Save**.

3.  **Retail** &gt; **Setup** &gt; **Retail Scheduler** &gt; **Scheduler subjobs**, add the new subjob to the **Customers - 1010** job, and save your change.
4.  Go to **Retail** &gt; **Setup** &gt; **Retail Scheduler** &gt; **Retail channel schema**, **export, edit,** **save with new name**, **import**, and edit the CDX table distribution XML. Add the following XML fragment inside both **CustTable** nodes. (By adding this XML fragment, you're explicitly including changes in this table when it's synced with the channels.)

        <Table name="RetailCustPreference">
            <LinkGroup>
                <Link type="FieldMatch" fieldName="accountNum" parentFieldName="AccountNum" />
            </LinkGroup>
        </Table>

5.  On the **Retail channel schema** page, select **AX** as the schema name, and then click **Generate queries**.

## Channel database
You will manually change the channel database for development. For the live deployment, see the "Live deployment" section later in this topic. You must apply the schema change from ChannelDBUpgrade.sql to the correct channel database to add the new table.

1.  Change \[crt\].\[CUSTOMERSVIEW\]:
    -   Before the UNION All, add ", isnull(rcp.EMAILOPTIN, 0) as EMAILOPTIN" to the end of the list of columns that should be selected.
    -   Before the UNION All, add "LEFT OUTER JOIN \[ax\].RETAILCUSTPREFERENCE rcp ON ct.ACCOUNTNUM = rcp.ACCOUNTNUM AND ct.DATAAREAID = rcp.DATAAREAID".
    -   After the UNION All, add ", 0  as EMAILOPTIN" to the end of the list of columns that should be selected.
    -   Change sproc \[crt\].\[CREATEUPDATECUSTOMER\]:

2.  Add the following code just before line "MERGE INTO \[ax\].DIRADDRESSBOOKPARTY":

        MERGE INTO [ax].RETAILCUSTPREFERENCE
        USING (SELECT DISTINCT
        tp.PARENTRECID, tp.PROPERTYVALUE as [EMAILOPTIN], ct.ACCOUNTNUM, ct.DATAAREAID
        FROM @TVP_EXTENSIONPROPERTIESTABLETYPE tp
        JOIN [ax].CUSTTABLE ct on ct.RECID = tp.PARENTRECID
        WHERE tp.PARENTRECID <> 0 and tp.PROPERTYNAME = 'EMAILOPTIN') AS SOURCE
        ON [ax].RETAILCUSTPREFERENCE.RECID = SOURCE.PARENTRECID
            and [ax].RETAILCUSTPREFERENCE.DATAAREAID = SOURCE.DATAAREAID
            and [ax].RETAILCUSTPREFERENCE.ACCOUNTNUM = SOURCE.ACCOUNTNUM
        WHEN MATCHED THEN
        UPDATE SET [EMAILOPTIN] = source.[EMAILOPTIN]
        WHEN NOT MATCHED THEN
        INSERT
        (
            RECID
            ,DATAAREAID
            ,EMAILOPTIN
            ,ACCOUNTNUM
        )
        VALUES
        (
            SOURCE.PARENTRECID
            ,SOURCE.DATAAREAID
            ,SOURCE.EMAILOPTIN
            ,SOURCE.ACCOUNTNUM
        );
        SELECT @i_Error = @@ERROR;
        IF @i_Error <> 0
        BEGIN
        SET @i_ReturnCode = @i_Error;
        GOTO exit_label;
        END;

## Verify CDX
1.  Run the 1010 job by using full synchronization (channel data group).
2.  Check the download sessions and the channel database to verify that the data arrived (it should appear as **Applied**).

**Note:** No customizations are required for the commerce runtime or Retail Server. Extension properties flow automatically.

## Test the customization's business logic by using the Retail Server test client
1.  Open the project at **RetailSdk\\SampleExtensions\\RetailServer\\Extensions.TestClient**, and then compile and run it.
2.  In the field next to the **Activate New** button, enter the Retail Server URL, and then click **Activate New**.
3.  Enter the device and register IDs, and then click **Activate**.
4.  Enter the Microsoft Azure Active Directory (Azure AD) credentials that have registration privileges, and then click **OK**.
5.  Wait for the test client to show which device is registered.
6.  Click the sign-in button, and sign in by using worker credentials.
7.  Click **Sdk Tests**. This button calls the new functionality that saves a customer with the **EmailOptIn** extension property applied.
8.  In Dynamics AX or the database, verify that the customer's **EmailOptIn** value is stored correctly. **Note: **To see a console that includes errors/logs, use the **Debug** button.

## Extend Modern POS
1.  Open the **ModernPos.sln** solution.
2.  Do a global search for **BEGIN SDKSAMPLE\_CUSTOMERPREFERENCES** in the solution.
3.  Enable the code at all places that you found, and recompile. Only one resources file is required. You can select the required locale.
4.  Run Modern POS, and verify that you can create a new customer. When an existing customer is updated, the flag should be updated correctly in both the channel database and the Dynamics AX database.

## Live deployment
1.  Add the channel database change file to the database folder, and register it in **customization.settings**.
2.  Run **msbuild** for the whole Retail SDK solution. All packages will have all appropriate changes.
3.  Deploy packages, either by using Microsoft Dynamics Lifecycle Services (LCS) or manually.


