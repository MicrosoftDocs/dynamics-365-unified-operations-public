**<u>How to move in process revenue schedules to a deferral schedule in Revenue and expense deferrals</u>**

This topic will detail how to move in-process Revenue recognition **Revenue schedules** to Revenue and expense deferrals **Deferral schedules.**

For example, a revenue schedule that was configured by fiscal period with even amounts starting on January 1 has been recognized through June 30.

1.  Export Revenue recognition entity **Deferred line (RevRecDeferredLineEntity)**

2.  Import the data into Revenue and expense deferrals entity **Subscription billing deferral table (SubBillDeferralScheduleTableEntity).** The below table illustrates how the fields can be mapped to each other.

| Subscription billing deferral table | Deferred line                | Notes                                                                                                                      |
|-------------------------------------|------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| Deferral schedule number            |                              | Can specify number, or copy Sales order number which was the revenue schedule number in Revenue recognition.               |
| Schedule type                       |                              | Straight line or event-based                                                                                               |
| Description                         | Revenue schedule description |                                                                                                                            |
| Deferral account                    | Deferred revenue account     | Will need to match the dimension structure for integrating applications. Empty dimensions will need to show with delimeter |
| Recognition Account                 | REVACCOUNT                   | Will need to match the dimension structure for integrating applications. Empty dimensions will need to show with delimiter |
| Recognition type                    |                              | Credit for revenue schedules, Debit for consumption                                                                        |
| Date                                | Date of invoice              |                                                                                                                            |
| Start date                          |                              | Deferral start date                                                                                                        |
| End date                            |                              | Deferral end date                                                                                                          |

The newly imported deferral schedules will need to be Stubbed to the date which they were previously recognized in revenue recognition. In the example, this date is June 30. The stubbing option is used to set the January – June periods as stubbed to prevent recognition for periods recognized through the Revenue schedule.

3\. This is done through the **Recognition processing** periodic task (Subscription billing – Revenue and expense deferrals – Periodic tasks – Recognition processing).

4\. Use Recognition action = Stub and set the Cutoff date = 6/30/2023. Fitlers can be used to filter deferral schedules to stub.

5\. Click Process. We should see a notification that Schedule lines processed: 6.

6\. Review the deferral schedule and observe the first 6 periods are marked as stubbed.
