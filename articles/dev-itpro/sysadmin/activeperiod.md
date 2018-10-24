
# Batch active period

It is now possible to have an additional level of control over when batch jobs execute. E.g. prior to Platform Update 21, it was only possible to say that a batch job should execute every hour for a specified number of hours or until a given date (or indefinitely). Now it is possible to provide an additional active period so that a batch job can run every hour but only between 6pm and 8am, 
Administrators will be able to easily specify time ranges during which jobs within a batch group can start execution. 

Uses: 
- Run your Batch Jobs outside of office hours.
- Set recurrence Within the Active Period anytime 

> [!NOTE]
> This feature is available as of platform update 21.

## Setup Active Periods for Batch Jobs 

1.	Go to System administration > Setup > 
2.	Click on Active periods for batch jobs.
3.	Enter the Name and Specify the From/to
4.	Click Save

![Menu](./media/menu-setup-activejobs.png)

![Active Period Form](./media/active-periods.png)

## Assign Active Periods to Batch Jobs

1.	Go to System administration > Inquiries > 
2.	Click on Batch jobs.
3.	Select the batch Job and Click on Edit
4.	Assign your Active Period to the Job
5.	Click Save

![Assign Active Period](./media/assign-active-period.png)
 


