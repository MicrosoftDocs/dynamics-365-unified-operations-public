**<u>How to move in process revenue schedules to a deferral schedule in Revenue and expense deferrals</u>**

In the first example, we'll take a revenue recognition schedule that was by fiscal period with even amounts starting January 1 and has been recognized through June 30. We'll start by exporting the information we need from the Revenue recognition entity "Deferred line" (RevRecRevRecDeferredLine). The screenshot below shows the information for the revenue schedule for sales order 000861.

![Graphical user interface  application  table Description automatically generated](media/image1.png)

We will import the information into the "Subscription billing deferral table" (SubBillDeferralScheduleTable) entity. Listed below are mapping details as well as general tips.

| Subscription billing deferral table | Deferred line                | Notes                                                                                                                      |
|-------------------------------------|------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| Deferral schedule number            |                              | Can specify own number, or copy Sales order number which was the revenue schedule number in Revenue recognition.           |
| Schedule type                       |                              | Straight line or event-based                                                                                               |
| Description                         | Revenue schedule description |                                                                                                                            |
| Deferral account                    | Deferred revenue account     | Will need to match the dimension structure for integrating applications. Empty dimensions will need to show with delimeter |
| Recognition Account                 | REVACCOUNT                   | Will need to match the dimension structure for integrating applications. Empty dimensions will need to show with delimiter |
| Recognition type                    |                              | Credit for revenue schedules, Debit for consumption                                                                        |
| Date                                | Date of invoice              |                                                                                                                            |
| Start date                          |                              | Deferral start date                                                                                                        |
| End date                            |                              | Deferral end date                                                                                                          |

The screenshot below shows the revenue recognition schedule after being imported as a deferral schedule.

![Graphical user interface  text  application  email Description automatically generated](media/image2.png)

We have a final step to take as this schedule was recognized through June 30 in revenue recognition. We will use the stubbing option to set the January – June periods as stubbed so we do not recognize those through this deferral schedule. We do this through the Recognition processing periodic task (Subscription billing – Revenue and expense deferrals – Periodic tasks – Recognition processing). We will use Recognition action = Stub and set the Cutoff date = 6/30/2023. In this example, I did add a filter for the individual billing schedule.

![A screenshot of a computer Description automatically generated with medium confidence](media/image3.png)  
View preview shows us 6 periods will be stubbed.

![Table Description automatically generated](media/image4.png)

Click Process. We should see a notification that Schedule lines processed: 6.

Now if we look at the deferral schedule we will see that the first 6 periods are marked as stubbed.

![Graphical user interface  text  application  email Description automatically generated](media/image5.png)

When recognition processing is run the next period for this schedule that will be recognized will be July 1 – July 31.
