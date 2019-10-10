---
# required metadata

title: Customer credit limit management
description: This topic describes the process for managing customer credit limits and using those limits to block and release sales orders. 
author: mikefalkner
manager: AnnBe
ms.date: 01/25/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mfalkner
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Customer credit limit management

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic describes the process for managing customer credit limits and using those limits to block and release sales orders. **Customer credit limit management** uses a defined process, and data, to managing customer credit limits. You can update credit limits using adjustments in which you can either manually enter changes, or automatically create new credit limits based on percentage increases or risk factors such as years in business or credit rating. These updates can be reviewed via workflow and then applied to customers using a posting process.

## Credit management setup	

To begin using credit management features, enable the parameters in **Credit management > Setup > Credit management parameters**. 

### Credit parameters
There are four tabs where you can change the parameters that control credit management.
 
#### Order on hold
1. Select **Yes** for **Allow edit of sales orders after order hold is released** to require the sales order to check the rules again if it has been edited after being released from the on-hold list. Normally, if the posting rules have been set up with grace days, the order will only be placed on hold if it is processed again after the number of grace days.  
2. Select the default **release reason** for the **Reasons for canceled orders**. This will be the default reason used when a sales order that was on credit management hold is cancelled.
3. Select **Yes** for the **Check customer credit groups credit limit** to check the credit limit of a customer credit group when the customer on a sales order belongs to a customer credit group. The credit limit for the group will be checked and, if the credit limit is sufficient, then the credit limit of the customer will be checked.
4. Select **Yes** for **Check credit limit when payment terms are increased** to check the payment terms rankings to see if the payment terms on the sales order are different from the payment terms on the sales order. If the ranking of the new payment term is higher than the original payment term, then the order is placed on credit management hold.
5. Select **Yes** for **Check credit limit when a settlement discount is increased** to check the settlement discount rankings to see if the cash discount on the sales order is different from the cash discount on the sales order. If the new cash discount ranking is higher than the original cash discount, the order is placed on credit management hold.
6. Select the default **release reason** for **Reason for releasing modified orders** that will be used when modified orders are automatically released from credit management hold.
7. Select **Yes** for **Ignore credit limit expired rule when expiration date is blank** to ignore the blocking rule that checks for expired credit limits when the expiration date is blank. Select **No** to have the blocking rule interpret the blank expiration as an expired credit limit.
8. Within warehouse management, it is possible to automatically create loads at sales order entry. Select **No** for **Remove blocked load lines** to leave the sales order lines on the load when a sales order is on credit hold. The load cannot be processed when the sales order is on hold. Select **Yes** to remove the sales order lines from the load when a sales order is on credit hold. The load can then be processed. 
9. Sales orders can be automatically released from the credit management hold list. Select the **release reason** for **Reason to release automatically** that will be used as the default release reason when sales orders are released automatically.
10. Sales orders can be automatically released from credit management review. Select **With posting** for **Automatically release** to post the order using the same posting process that was executed when the sales order was placed on hold. Select **Without posting** to set the allow an order to be posted using the same posting process that was executed when the sales order was placed on hold. 

#### Credit management checkpoints

You can set the timing for checking sales orders for credit issues. The credit management checkpoints tab is used to identify which document posting processes will include processing of credit management rules. You can also choose to check the credit rules while doing either a proforma posting or full posting of the sales order. Select each check box to define which posting processes will put an order on hold if an issue is found after processing the credit management blocking rules.

You can also define the number of grace days before the credit rules are rechecked after they've been checked the first time. Although you may specify that the credit management rules are checked at posting, the rules will not be checked for the specified number of grace days. For example, if you confirm a sales order on day 1 and you specify 2 grace days for the confirmation step, then credit rules won't be checked at the next posting step, such as creating a packing slip, invoicing the order, and so on, until day 4. On or after day 4, the rules will be checked again when posting occurs and the number of grace days will be changed to the number of grace days for the next posting checkpoint. 

If you don't specify the number of grace days,  the credit rules will be checked at every posting step that is set to execute credit management rules.  

You can't specify grace days for some posting checkpoints and not for other checkpoints. You must set up all posting checkpoints with grace days or set up none of them with grace days.

1. Select the check box in the **Posting column** to execute the credit management rules when the posting checkpoint shown on the line is executed. If you don't select the check box, the rules will not be checked for that posting process.
2. If you selected the **Posting column** check box, add **Grace days** to identified how many days will pass before the blocking rules will be checked again. You can't add grace days unless the box is checked.
3. Select the check box in the **Pro forma column** to execute the credit management rules when the proforma posting checkpoint shown on the line is executed. In most cases, the posting box is set to **No** on the dialog that shows when a sales order is posted.
4. If you checked the **Pro forma column** box, add **Grace days** to identified how many days will pass before the blocking rules will be checked again. You can't add grace days unless the box is checked.

#### Credit management statistics

There are several credit management statistics included in the credit management statistics fact box on the **Customer** page. These statistics require you to specify several values that will be used to calculate those statistics. Enter the number of months used to calculate the following values shown in the customer credit management statistics fact box:

1. **Days Sales Outstanding 1**
2. **Days Sales Outstanding 2**
3. **Average balance 1**
4. **Average balance 2**
5. **Average credit limit %**
6. **Average exposure %**

#### Credit limits

1. In Credit management, the customer credit limit is shown using the customer's currency. You must define the exchange rate type for the credit limit using the customer's currency. Select the **Credit Limit exchange rate type** that will be used to convert the primary credit limit to the customer's credit limit.
2. Select **No** for **Allow manual editing of credit limits** to stop users from editing credit limits on the customer form. When this field is set to No, changes to a customer's credit limit can be only by posting credit limit adjustment transactions.  

#### Number sequences and shared number sequences parameters

You must set up the following number sequences for credit management:
1. Add the **Credit limit adjustment number** that will be used to generate the journal ID needed for processing credit limit adjustments.

## Set up information

### Credit management workflow

Select **Credit and collections > Setup > Credit management workflows** to define the workflows that are used to manage credit limit adjustments. You can create a workflow that allows you to approve all of the credit limits adjustments with a single approval. You can also add workflow at the line level that allow you to approve each credit limit adjustment line. 

### Blocking rules

### Rank payment terms

You can place a sales order on hold if the payment terms on the order don't match the default payment terms for the customer. Sometimes however, the payment terms are similar enough that you do not want to put the order on hold when they are different. You can rank payment terms so that some payment terms have the same rank and some payment terms have a higher or lower rank. 

If the rankings for payment terms are active, the sales orders will be placed on hold if the payment term on the order has a higher rank than the default payment terms for the customer.

### Rank settlement discounts

You can place a sales order on hold if the cash discount on the order doesn't match the default cash discount for the customer. Sometimes however, the cash discounts are similar enough that you do not want to put the order on hold when they are different. You can rank cash discounts so that some cash discounts have the same rank and some cash discounts have a higher or lower rank. 

If settlement discounts rankings are active, the sales orders will be placed on hold if the cash discount on the order has a higher rank than the default cash discount on the customer.

### Reasons

There are several types of reasons used in credit management:
1) **Hold** reasons are used to define why a sales order was placed on hold
2) **Release** reasons are assigned to an order when the order that was on hold is released
3) **Status** reasons are used to indicate the reason that an account status was assigned to a customer

### Credit management groups
 
Credit management groups are used to identify a customer or group of customers that share a credit limit as a group. The group can contain customers from any and all legal entities. However, a customer can only belong to one group. 

You can create the groups on the **Credit management > Customers> Credit management groups** page. 

1. Click **New** to create a new line
2. Enter a **Group ID**, using up to 10 characters, and enter a **Group name** using up to 60 characters in the description field.

### Account statuses

You can create an **Account status** to identify the credit standing of a customer account. You can define the status and its effect on the invoicing and delivery on hold processes.  Account statuses can also be used to determine blocking rules for a customer.  

You can create **Account statuses** from the **Credit management > Setup> Credit management> Account statuses** page.

1. Add an account status and a description for the status that represents the credit standing for a customer. For example, use **Normal** to represent a customer is in good standing and open orders are to go through standard credit management processing.
2. In the **Invoicing and Delivery on Hold**, select the type of hold that will occur for customers with this status. You can hold all processing, hold only invoice processing, or do no hold processing when executing the credit limit rules. 

### Scoring Groups

You can set up scoring groups to define risk factors and the criteria for how these risk factors can be measured. When information about a customer is applied to a scoring group, a score is calculated for each risk factor and used to place the customer in a risk group. The risk group can be used for identifying credit worthiness and for calculating automatic credit limits.

You can create scoring groups on the **Credit management > Setup > Credit management> Risk > Scoring groups** page.

1. Create a **Scoring group** name for the group.
2. Create a **Description** to further describe the scoring group.
3. Select a **Group type** to select one of eight predefined types that you are defining. You can also select **User defined** to define your own type of group.
4. Enter a **Score type** to define how the scoring group calculates the risk score. The options are:
   - Use **Range** to define ranges of values that will calculate a score.
   - Use **User defined** to define a list of values manually with the value that will be used for the score.

For **Range** score types, add lines to define the range of values and the corresponding scores. 
1. Enter the **From value** that is the lowest value in the range.
2. Enter the **To value** that is the highest value in the range.
3. Enter the **Score** that will be assigned when the value being provided falls within the from/to range.

For **User defined** score types, add lines to define the user defined values and the corresponding scores. 
1. Enter the user defined **Value** that will be provided from the customer information.
2. Enter the **Score** that will be assigned when the value being provided falls within the from/to range.

### Risk Assessments

You can define **Risk assessments** that can be assigned to customers based on their risk scores. A risk score is calculated by comparing customer information to each of the scoring groups. The scores are summed together and the total score is compared to the values in the risk group setup to identify the risk group the customer belongs to. The risk group is then used to define credit management blocking and exclusion rules for the customer.

You can set up risk groups on the **Credit management > Setup > Credit management> Risk > Risk assessments** page.

1. Enter a **Risk group** identifier. 
2. Enter a risk group **Description** to further explain the group.
3. Enter a **From** value that defines the lowest score that will fall into this group.
4. Enter a **To** value that defines the highest score that will fall into this group.
5. Select a **Risk group indicator** to identify an icon that represents the risk group.

### Guarantee/Insurance Types

You can set up guarantee/insurance types using the **Credit management > Setup > Guarantee/insurance setup > Guarantee/insurance types**  page.

1. Enter a **Guarantee/Insurance type** to identify the name of the guarantor or insurance broker.
2. Enter a **Description** to describe the guarantor/insurance broker.

### Coverage Types

Coverage types can be used to further classify the insurance policy; they cannot be used with guarantees. You can add coverage types on the **Credit management > Setup > Guarantee/insurance setup > Coverage types** page.

1. Enter a **Coverage type** to identify the type of coverage that will be added as insurance or a guarantee. 
2. Enter a **Description** to describe of the coverage type.

## Add credit management information for a customer  

When you have set up the parameters that control advanced credit management, you can add additional details to each customer that will control the credit management processes and provide additional information that helps members of the collections team manage customers.

### Credit and collections tab on the customer page

You can add the additional infomation on the **Account receivable > Customers > All customers** page on the **Credit and collections** fast tab. 

1. Select **Yes** for **Unlimited credit limit** if you don't want your customer to be limited by any credit limit tests.
2. Select **Yes** for **Exclude from credit management** to exclude the customer from any actions that would normally occur during  credit management processes.
3. Enter an **Ignore until date** that temporarily disables credit management processes until that date is reached.
4. Select the **Credit management group** to be used for this customer.
5. If you want to calculate the credit limit in the customer's currency, enter the customer’s credit limit in the **Credit limit in customer's currency** field. The credit limit in the company currency will be converted using the exchange rates defined by the **credit limit exchange rate type** selected in the Credit management parameters.
6. Enter the **Last review date** that the customer credit limit was last reviewed by a credit manager.
7. Enter the **Next scheduled review date** on which the customer is scheduled for credit review and update.
8. Enter the **Eligible credit limit**, which is the highest possible credit limit that is allowed for the customer. The eligible credit limit represents the maximum credit that you could assign to a customer based on your review of their credit history. It can be different from the credit limit shown on the **Credit and collections** FastTab.
9. Enter the **currency value** of the eligible credit limit in the **Eligible credit limit currency** field.
10. Enter the **Eligible credit limit date** that the **eligible credit limit** was created for.
11. Enter the credit **Account status** for the customer.
12. Enter the **Status reason** that's associated the account status.
13. Select **Yes** for **With agency** to indicate that the customer is currently assigned to a credit agency. This value is only for informational purposes and is not used in any credit management processes. 
14. Select **Yes** for **Title held** to indicate that a title is held for the company. This value is only for informational purposes and is not used in any credit management process. 
15. Enter the **Business started** date that the customer first started its business. This information will be used in creating risk scores.
16. Enter the **Customer since** date that indicates when the first transactions were processed for this customer. This information will be used in creating risk scores.
17. Enter **Notes** that the credit team can use to further evaluate the customer's credit worthiness.


Also note that some information that is shown on the customer page is created by another process:
1. The **Credit limit expiration date** is the date on which the credit limit will expire. If this field is blank, the customers' credit limit won't expire. 
2. The **Credit limit date** is the date on which the credit limit was created. This date is updated whenever the credit limit is adjusted.
3. The **Temporary credit limit** represents a temporary credit limit that is active at the time that you are viewing the customer record. It will be used instead of the credit limit to calculate the total credit limit.
4. The amount displayed on **Insurance and guarantees** field indicates the total value of insurance and guarantees that can increase the credit limit for the customer.
5. The **Total credit limit** fields shows the final credit limit for the customer including insurance and guarantees, and temporary credit limits.

### Temporary credit limits

Temporary credit limits override the customer credit limit for a period of time. You can add temporary credit limits using **Credit limit adjustments**.

## Customer credit groups
  
You can define a group of customers so that members of the group can share a credit limit. In addition, the individual credit limit defined on the customer invoice account is also considered. Members of a customer credit group can be selected from different legal entities. If a customer is added to a customer credit group, the customer credit group credit limit is assigned to that customers, although you can use the standard credit limit functionality.  

You can set up the customer credit groups on the **Credit management > Customer credit groups > Customer credit groups** page. 

1. Enter a **Group number** and a **Description** of the group.
2. Enter the **Credit limit** and **Currency** that will be used when the credit limit for any member of the group is checked.
3. Enter the **Credit limit to date**, which is the date that the credit limit expires. Customer credit groups must have expiration dates.
4. Select **Yes** to use the days overdue for each customer in the group when the credit rules are processed.

After the customer credit group has been set up, you can add customers to the group by specifying their legal entity and customer account ID. When adding a new customer to the customer credit group, the system will search for the same customer account across all legal entities and prompt you to add them to the customer credit group.

Open the **Aged balances** menu to view the details of the aging balance for all invoice customers within the customer credit group.  The **Aging balance** page shows a summary of the invoice customer account aged balances. 

## Create Insurance Policies and Guarantees

You can create one or more insurance policies and guarantees for each customer and use them to calculate the exposure that your company has when offering credit to a customer. Insurance policies and guarantees can also be included in the credit limit for a customer.

You can create insurance policies and guarantees on the **Accounts receivable > Customers > All customers** page. Select a customer, select the **Credit management** action pane and select **Insurance and guarantees**.

[!Note] In the following procedure, you'll select an insurer/guarantor from the global address book. If the insurers and guarantors haven't been added to the address book, they must be added before beginning this procedure.

1. Enter  **Guarantee** or **Insurance** in the **Identifier** field.
2. Select the **Guarantee/Insurance type** from the list of Guarantee/Insurance types that you set up previously.
3. Select the **Insurer/Guarantor** from the global address book. 
4. If the Identifier that you selected is **Insurance**, then select the **Policy coverage type** from the list of coverage types that you set up previously. You cannot select a policy coverage type for a guarantee.
5. Enter an **Identification** for the policy. This is usually a policy Number.
6. Enter the **Effective** start date for the guarantee or insurance policy.
7. Enter the **Expiration** date on which the guarantee or insurance policy expires.
8. Enter the **Value** of the insurance or guarantee. This is the full value of the policy.
9. Select the **Currency** for the policy value. 
10. Select the **Update credit limit** percentage using a number between 0 and 100. The percentage will be applied to the policy value and the resulting amount will be used to increase the credit limit used in credit limit calculations. The calculated value is called the **Effective credit limit** and is displayed on the **Customers** page in the **Credit management statistics** fact box.
For Example:
  -  Assume a credit limit of 100,000 (A)
  -  Assume a policy value of 50,000 (B)
  -  Assume an update credit limit value of 50.00 (C)
  -  The effective credit limit will now be 125,000 (A + (B * C))
11. Select **Included in exposure** to reduce the credit limit used in credit limit calculations by the full value of the policy. The value calculated when specifying the **Update credit limit** percentage won't be used in credit limit calculations when this check box is selected.   
For Example:
  -  Assume a credit limit of 100,000 (A)
  -  Assume a policy value of 50,000 (B)
  -  Assume an update credit limit value of 50.00 (C)
  -  The effective credit limit will now be 125,000 (A + (B * C))
  -  Selct the check box to change the Included in exposure value to **Checked**.
  -  Remove the update credit limit value of 50,000
  -  The exposure value is 75,000 (A + (B * C)) – B

## Credit Limit Adjustments	

### Credit Limit Adjustments

**Credit limit adjustments** allow credit managers to update the credit limits and expiration dates of a single customer, group of customers, or all customers using a submission process. You can add credit limit adjustment entries to update customers and customer credit groups or use it to calculate automatic credit limits. The entries can then be reviewed, sent for approval through workflow, and posted to the customer accounts. 

You can create **Credit limit adjustments** entires on the **Credit management > Credit limit adjustments > Credit limit adjustments** page.

1. When you select **New**, a new adjustment batch is created with a **Credit limit adjustment number**
2. Select the **Credit limit adjustment type**. You can select **Credit limit** to adjust the customer credit limit. You can select **Temporary credit limit** to create temporary credit limits instead of changing the existing credit limits. Temporary credit limits override a customer's credit limit for a defined period of time, after which the customer's credit limit is used again. 
2. Enter a journal **Description**
4. The **Posted** check box indicates that the credit limits have been applied.
5. The **Approval status** indicates the workflow status of the journal.

Selecting  **Lines**, lets you enter credit limit changes manually onto the adjustment page. You can also use the **Generate** menu to create the credit limit changes automatically. 

To enter credit limit changes manually, add the following information to the journal lines:
1. Select the **Customer adjustments** menu to create an adjustment for a customer. Select **Customer credit group adjustments** to add a credit limit for a customer credit group.
2. Enter a **Customer account** for the invoice customer account that will be updated with the new credit limit. If you selected **Customer credit group adjustments**, then enter the customer credit group.
3. The **Name** will appear automatically.
4. If you want to update the credit for a customer credit group, enter the **Customer credit group ID** of the group. You cannot enter both a customer account and customer credit group ID on the same journal line.
5. The current **Credit limit** will be displayed.
6. Enter the **New credit limit** that will replace the current credit limit when the credit limit journal is posted.
7. Enter the **New to date** to define the new expiration date for the customer credit limit. You must enter credit limit expiration dates when you create a credit limit adjustment journal.
8. The **Approval status** indicates the workflow status of the journal line.

To enter temporary credit limit changes manually, add the following information to the journal lines:

1. Select the **Customer adjustments** menu to create an adjustment for a customer. Select **Customer credit group adjustments** to add a credit limit for a customer credit group.
2. Enter a **Customer account** for the invoice customer account that will be updated with the new credit limit. If you selected **Customer credit group adjustments**, then enter the customer credit group.
3. The **Name** will appear automatically.
4. The current **Credit limit** will be displayed.
5. The current **From date** and **To date** for the advanced credit limit will be displayed.
6. Enter the **New credit limit** that will replace the current credit limit when the credit limit journal is posted.
7. Enter the **New from date** to define the new expiration date for the advanced credit limit.  
8. Enter the **New to date** to define the new expiration date for the advanced credit limit. You must enter credit limit expiration dates when you create a credit limit adjustment journal.
7. The **Approval status** indicates the workflow status of the journal line.

You can also generate credit limits automatically using the **Generate** menu in the action pane. 
1. From existing – customer
2. From existing – linked customer
3. Automatic credit limits

#### From existing customers

You can create journal lines to adjust credit limits for existing customers. When you select **Generate > From existing customers**, a dialog is presented that you can use to provide criteria for selecting customers and calculating the new limits:

1. Enter an **Adjustment value** to add or subtract an amount from the credit limit. Enter a negative value to adjust the credit limit down or a positive to adjust it up. The **Value type** controls how the value will be used to calculate the new credit limit.
2. Select a **Value type** that will control how the value is used in the credit limit calculation. Select **Fixed value**, to change the credit limit by an amount,  or **Percentage** to change it by a percentage.
3. Enter a **Round off** value to round off the calculated credit limit.  For example, 10.00 will round the credit limit to the nearest 10.00.
4. Select the **Rounding form** to determine if the rounded remainder is rounded up or down.
5. Select the method for adjusting dates. If you select **Absolute**, you can enter a **New from date** and **New to date** to define the date range for the credit limits. If you select **Relative**, you can enter a **From date offset** and a **To date offset** that will adjust the current from and to date ranges for the credit limits by the offset.

Click **OK** to create the credit limit adjustment entries.

#### From existing customer credit groups

You can create adjustment entries from existing customers. When you select **Generate > From existing customer credit groups**, a dialog is presented that you can use to provide criteria for selecting linked customers and calculating the new limits. The criteria is the same as shown above for **From existing customers**.

Click **OK** to create the credit limit adjustment journal entries.

#### Automatic Credit Limits
You can create **Automatic credit limits** to define and update customer credit limits. The automatic credit limits are created for a risk group and are based on specific values used in the scoring groups. You can use these automatic credit limits to generate credit limits in the credit limit adjustment journals. If a customer has been assigned a specific risk group and the customer's credit information matches the criteria for an automatic credit limit, then a line in the credit limit adjustment journal is created.

#### Defining automatic credit limit criteria
You can create **Automatic credit limits** criteria on the **Credit management > Setup > Credit management > Risk > Automatic credit limits** page.

1. Select a **Risk group** to which the automatic credit limit is assigned.
2. Select the **Currency** for the automatic credit limit. You can create multiple automatic credits limits for the same risk group for credit limits in different currencies.
3. Enter the **Revenue** amount that represents the maximum company revenue that can be used for this automatic credit limit. When credit limits are created, the revenue amount is compared to a revenue value found on the **Financials page** under **Accounts Receivable > All customers> Select a customer > General > Statistics > Financial**. It looks at the latest value in the Overview section. 

Add lines that represent the credit limit that will be generated based on criteria selected.

1. Select the **Scoring group** that defines the customer information that will be used to calculate the credit limit.
2. Select the **Comparison operator** that will be used to define how the scoring group information will be evaluated
3. Enter the **Value** that will be compared to scoring group value.  
4. Enter the **Credit limit** that will be assigned if the customer information matches the value specified for the scoring group. 

For example, you can create an automatic credit limit for the Low scoring group. If the Dun and Bradsheet score is one of the scoring groups, you can define one line that will assign a 100,000 credit limit if the Dun and Bradstreet score is A2 and define another line that will assign a 200,000 credit limit if the Dun and Bradstreet score is A1.

#### Creating automatic credit limits 

You create automatic credit limits using **Credit limit adjustments**. When you select **Generate > Automatic credit limits**, a dialog is presented that you can use to provide a **New expiry date** for the new credit limits that will be created based on the risk groups that customers have. If you are creating temporary credit limits, provide a **Start date**. Click **OK** to create the credit limit adjustment lines.

### Posting adjustments 

Once you have created credit limit adjustment lines, you can use the **Post** button in the action pane to post the lines and update the customer credit limits. However, if you have set up workflow for the journal, you will need to use the **Workflow > Submit** button on the action pane to submit the journal for approval.

#### Credit Limit Adjustment Journal Workflow

The **Credit limit adjustment journal workflow** can be used to send credit limit adjustments through a workflow approval. There are two workflows that you can create on the **Credit management > Setup > Credit management worfklow** page.: 
1. The **Credit limit adjustment workflow** can be used to approve journals at the header level.
2. The **Credit limit adjustment line workflow** can be use to approve the adjustment lines so that the lines can be approved by different people based on the criteria in the workflow.

[!NOTE] When creating the Credit limit adjustment workflow, you can set up the workflow to Post the adjustment journal once the lines are approved.  Include the Post Journal automatic task in the workflow to automatically post all of the adjustments.

## Periodic tasks	

### Update risk scores

As you process invoices, the risk for a customer can change. You must periodically review the criteria for each risk score and update the scores for each customer. You can use **Credit and collections > Periodic tasks > Credit management > Update risk scores** to update the following scores:

#### Payment days
  
Payment days is one of the scoring group criteria that must be calculated periodically. The process calculates the number of days that a customer is waiting to pay their invoices. This value is then used in the scoring group to calculate a score for this criteria for each customer. 

#### Years in business
  
Years in business is one of the scoring group criteria that must be calculated periodically. The process calculates the number of years that a customer has been in business using the **Business start** value in the **Customers** page. This value is then used in the scoring group to calculate a score for this criteria for each customer. 

#### Customer since
  
Customer since is one of the scoring group criteria that must be calculated periodically. The process calculates the number of years that a customer has been a customer of the company using the **Customer since** value in the **Customers** page. This value is then used in the scoring group to calculate a score for this criteria for each customer. 

### Update Customer Balance Statistics

You can run the **Update customer balance statistics** process to update the balance statistics calculation that viewed on the **Balance statistics inquiry** page. You can run the process and set up a periodic batch job on the **Credit management > Periodic tasks > Credit management > Calculate balance statistics** page.


## See also
sales order holds [Production output location](https://docs.microsoft.com/dynamics365/unified-operations/supply-chain/production-control/production-output-location)
margin control
managing claims
