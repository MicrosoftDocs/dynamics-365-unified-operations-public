---
# required metadata

title: Add customer preference data to a channel database
description: This tutorial shows how to add the RetailCustPreferences table to the commerce runtime (CRT) for the retail channel, and how to create a subjob to move the data in the new table to the channel database.
author: kfend
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 18081
ms.assetid: 3c13fe1d-2078-4539-b865-e266b6f56e60
ms.search.region: Global
ms.search.industry: Retail
ms.author: meeram
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Add customer preference data to a channel database

[!include[banner](../includes/banner.md)]


This tutorial shows how to add the RetailCustPreferences table to the commerce runtime (CRT) for the retail channel, and how to create a subjob to move the data in the new table to the channel database.

Add the RetailCustPreferences table in the data distribution to the CRT for the retail channel
----------------------------------------------------------------------------------------------

The channel schema is the XML description of the data that is sent to the channel database.

1.  Click **Retail and commerce** &gt; **Headquarters setup** &gt; **Retail scheduler** &gt; **Retail channel schema**.
2.  Select the schema name that corresponds to the channel. Then click **Channel tables**.
3.  Click **New**, and then, in the **Table name** field, enter **ax.RetailCustPreference** as the name of the new table.
4.  On the **Channel table fields** tab, click **New**, and then enter the field names **ACCOUNTNUM**, **EMAILOPTIN**, and **RECID**.
5.  Close the **Channel tables** page.

## Create a subjob
Next, you create a subjob of the CustTable job to move data in the new table to the channel database.

1.  In Retail Headquarters, click **Retail and commerce** &gt; **Headquarters setup** &gt; **Retail scheduler** &gt; **Scheduler subjobs**, and then click **New**.
2.  In the **Subjob number** and **Description** fields, enter **RetailCustPreference**.
3.  In the **Retail channel schema** field, select **Dynamics 365 for Operations.**
4.  In the **Channel table name** field, select **ax.RetailCustPreference**.
5.  In the **table name** field, select **RetailCustPreference**.
6.  On the **Channel field mapping** tab, click **Match fields**. The **From** field and **To** field columns are filled in. **Alternative approach, instead of using the UI in the steps above this can also accomplished in code:**
    1.  Start Microsoft Visual Studio, and then, in the Application Object Tree (AOT) find the **RetailCDXSeedData\_AX7** class.
    2.  Add the following method.

            private void C_RetailCustPreference()
            {
                jobIDContainer = ['1010'];
                subjobID = 'RetailCustPreference';
                axTableName = tableStr(RetailCustPreference);
                axFieldNames = [
                fieldStr(RetailCustPreference, AccountNum),
                fieldStr(RetailCustPreference, EmailOptIn),
                fieldStr(RetailCustPreference, RecId)
                ];
            }

    3.  Compile the class.
    4.  Reset Internet Information Services (IIS).
    5.  Switch to the client.
    6.  Click **Retail and commerce** &gt; **Headquarters setup** &gt; **Retail scheduler** &gt; **Initialize retail scheduler**. The required scheduler subjob definition is generated, and the subjob is added to the scheduler job.

7.  Click **Retail and commerce** &gt; **Headquarters setup** &gt; **Retail scheduler** &gt; **Retail channel schema**.
8.  On the **Retail channel schema** page, in the left navigation pane, click **Dynamics 365 for Operations.**
9.  On the **Retail data distribution** tab, click **Export**.
10. Follow one of these steps, depending on the browser that you're using:
    -   If you're using Google Chrome, you should be prompted to download an XML file. Save the file to a path.
    -   If you're using Internet Explorer, a webpage will open. Right-click in the page, and then click **View source**. Then save the contents of the page source to a file path.

11. In a text editor such as Notepad++, open the XML file that you just saved, and follow these steps.
    1.  Search for the following line: **&lt;Table name=“RetailCustTable”&gt;**. There are two instances, at approximately line 29 and line 744.
    2.  Add the following code after the last line in both **&lt;Table name=“RetailCustTable”&gt;** code blocks. You add the code after the **&lt;/Table&gt;** tag.

            <Table name="RetailCustPreference">
                <LinkGroup>
                    <Link type="FieldMatch" fieldName="accountNum" parentFieldName="AccountNum" />
                </LinkGroup>
            </Table>

12. After you've finished editing the file, go back to client and the **Retail channel schema** page. In the left navigation pane, click **Dynamics 365 for Operations.**
13. On the **Retail data distribution** tab, click **Import**.
14. In the dialog box that opens, click **Browse**, select the XML file that you just edited, and then click **OK** to import the file.
15. Close the **Retail channel schema** page.
16. Click **Retail and commerce** &gt; **Headquarters setup** &gt; **Retail scheduler** &gt; **Scheduler job**.
17. On the **Scheduler job** page, click **1010** to select the “Customers” job.
18. On the **Subjobs** tab, click **New**, and then enter **RetailCustPreference** as the subjob number. Click **Save**.
19. On the **Retail channel schema** page, select **Dynamics 365 for Operations **as the schema name, and then click **Generate queries**.




