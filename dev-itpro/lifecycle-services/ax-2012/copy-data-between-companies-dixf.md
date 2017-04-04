---
# required metadata

title: Copy data between Dynamics AX companies (AX 2012)
description: You can use the Microsoft Dynamics AX 2012 Data Import/Export Framework to copy an entity, such as customers, from one Microsoft Dynamics AX legal entity (company) to another. In this example, we will export customers in a specific customer group from the CEU company to the CEC company in the Contoso data set.
author: kfend
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Lifecycle Services
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: AX 2012
# ms.tgt_pltfrm: 
ms.custom: 17821
ms.assetid: cd9b30d2-d4e0-4da7-9408-34bda5888070
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 
ms.dyn365.ops.version: 2012

---

# Copy data between Dynamics AX companies (AX 2012)

You can use the Microsoft Dynamics AX 2012 Data Import/Export Framework to copy an entity, such as customers, from one Microsoft Dynamics AX legal entity (company) to another. In this example, we will export customers in a specific customer group from the CEU company to the CEC company in the Contoso data set.

**Note: **This walkthrough is not intended for users of the versions of the Data Import/Export Framework that ship with cumulative update 7 for Microsoft Dynamics AX 2012 R2 or Microsoft Dynamics AX 2012 R3. Those users should refer to the topic [Copying and comparing entity data between companies (DIXF, DMF)](copy-compare-entity-data-between-companies-dixf.md). This walkthrough illustrates the following tasks:

-   Define the format of your source data
-   Define a processing group
-   Process data from source to staging
-   Switch companies to copy data to another legal entity
-   Validate the data in staging
-   Validate the data in target

The following diagram illustrates the path that data takes during the export and import processes. [![WalkthroughCopyDataBetweenAXCompanies1](./media/walkthroughcopydatabetweenaxcompanies1.jpg)](./media/walkthroughcopydatabetweenaxcompanies1.jpg)

## Prerequisites
To complete this walkthrough you will need:

-   Microsoft Dynamics AX 2012 or Microsoft Dynamics AX 2012 R2
-   Data Import/Export Framework
-   Demo data for Microsoft Dynamics AX 2012 or Microsoft Dynamics AX 2012 R2

## Define the format of your source data
1.  Open **Data Import/Export Framework** &gt; **Setup** &gt; **Source data formats**.
2.  Click **New**, enter a name and a description, and then select **AX** from the **Type** list.

## Define a processing group to export data from Microsoft Dynamics AX
1.  Change the company to **CEU**.
2.  In **Data Import/Export Framework**, click **Common** &gt; **Processing group**, and then click **New** to create a new processing group.
3.  Set the group name to **Export-Cust** and add a description.
4.  Click **Entities** to select the entities to include in the processing group.
    1.  In the **Select entities for processing group** form, click **New**, and then, for an entity name, select **Customer**.
    2.  In the **Source data format** field, select the Microsoft Dynamics AX source data format that you created.
    3.  Click **Select**, and then in the **DMFCustomerTargetEntity** form, on the **Range** tab, for **Field**, select **Customer group**, and for **Criteria**, select **20**, and then click **OK**.
    4.  Close the **Select entities for processing group** form.

## Process data from source to staging
1.  In the **Processing group** form, select the Export-Cust group that you created, and click **Get staging data**.The **Create a job ID for the staging data job** form opens.
2.  By default, an ID for the job is generated. If needed, you can modify the ID and add a description. Click **OK**.The **Staging data execution form** opens.
3.  In the **Get data from source to staging** form, click **OK** to run immediately.The source data is copied to the staging tables.

## Validate the data in staging
1.  In **Data Import/Export Framework**, click **Common** &gt; **Processing group** &gt; **Execution history**, and then select the job that ran.
2.  Click **View staging data**.
3.  Review the staging data to validate that it matches the source.
4.  Click **Validate all** to verify that all the related reference data is correct and present in the system.

## Switch companies to copy data to another company
1.  Switch to the **CEC** company.
2.  In **Data Import/Export Framework**, click **Common** &gt; **Processing group**, and then select the processing group to work with.
3.  Click **Copy data to target**. The **Select a job ID to run** form opens.
4.  Select a job and click **OK**. The **Target data execution** form opens.
5.  Click **Run**, and then click **OK**. The data is copied to the target entity.

## Validate the data in target
Verify that the customer data from the original company is displayed in either of the following ways:

-   View staging data:
    1.  In **Data Import/Export Framework**, click **Common** &gt; **Processing group** &gt; **Execution history** &gt; **View staging data**, and then select the job that ran.
    2.  Review the staging data to validate that it matches the source.
    3.  Click **Validate all** to verify that all the related reference data is correct and present in the system.
-   Verify that the customer data from the CEU company is now displayed in the **All Customers form**. Click **Accounts receivable** &gt; **Common** &gt; **Customer** &gt; **All Customers **form.


