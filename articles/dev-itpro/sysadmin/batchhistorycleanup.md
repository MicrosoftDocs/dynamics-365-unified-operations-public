# Batch History cleanup

[!include [banner](../includes/banner.md)]

When you execute a batch job, execution history is saved to monitor proper execution of jobs, with a lot of batch jobs, especially those with a high recurrence 
will generate a lot of batch job history entries.

Keeping too many entries in the history table can negatively affect the performance of future jobs

We improved the functionality to clean up batch jobs history which was introduced in an early platform update. 
Two forms have been added to the System Administration workspace:

1. Batch job history clean-up.
2. Batch job history clean-up (custom).

![Cleanup menu](./media/batch-cleanup-menu.png) 

>[!NOTE] 
>We strongly recommend cleaning batch history regularly and outside of business hours.


## Batch job history clean-up

This version of batch job history clean-up allows you to quickly clean all history entries older than a specified timeframe (in days).

1.	Click on the Batch job history clean-up from the menu
2.	specify the number of days to keep

![Regular Job](./media/batch-cleanup-regular.png) 
 
# Batch job history clean-up (Custom)

The custom batch job allows you to add additional filtering based on criteria such as status, job description, company, or user. Other criteria can be added by clicking on the filter button.

![Custom Job](./media/batch-cleanup-custom.png) 

1.	Click on the Batch job history clean-up (custom) from the menu
2.	specify the number of days to keep
3.  Enter you filter criteria
