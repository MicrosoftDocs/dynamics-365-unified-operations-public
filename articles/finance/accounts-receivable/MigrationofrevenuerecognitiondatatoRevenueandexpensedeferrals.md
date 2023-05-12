**Migration of revenue recognition data to Revenue and expense deferrals**

This topic will cover the set up and configuration options in Revenue recognition and how to move the information to Revenue and expense deferrals.

A key set up component in Revenue recognition is the recognition basis. This can be set to Monthly by days, Monthly, Occurrences, or Fiscal period by days. More information on these options can be found [here](https://learn.microsoft.com/en-us/dynamics365/finance/accounts-receivable/revenue-recognition-setup).

<u>Recognition basis scenarios</u>

Example 1: One year deferral with equal amounts per month, starting on the date of the invoice.

**  
Revenue recognition**

Revenue schedule in revenue recognition with Occurrences = 12, Recognition basis = Monthly, Recognition convention = Actual start date. Sales order amount = 1500

![Graphical user interface  application Description automatically generated](media/image1.png)

![Table Description automatically generated](media/image2.png)

Revenue recognition schedule showing monthly recognition of 124.95, with exception being the final period for 125.55.

![Table Description automatically generated](media/image3.png)

**Revenue and expense deferrals**

Deferral template with Period frequency = Monthly. Lines set up with Type = Recognized, Period length = 12. With Revenue and expense deferrals there is a parameter that will either pro-rate the amount by the number of days in a month or not. This parameter is called "Equal amounts per period." In this example, the deferral schedule was created with Equal amounts per period = Yes.

![](media/image4.png)

![Graphical user interface  application Description automatically generated](media/image5.png)

Example 2: One year deferral with monthly amounts based on the number of days per month, starting on the date of the invoice.

**Revenue recognition**

Revenue schedule in revenue recognition with Occurrences = 12, Recognition basis = Monthly by days, Recognition convention = Actual start date. Sales order amount = 1500  
![Table Description automatically generated](media/image6.png)

![Table Description automatically generated](media/image7.png)

Revenue recognition amounts will vary by period due to the number of days in each month being different.

![Table Description automatically generated](media/image8.png)

**Revenue and expense deferrals**

Deferral template with Period frequency = Monthly. Lines set up with Type = Recognized, Period length = 12. With Revenue and expense deferrals there is a parameter that will either pro-rate the amount by the number of days in a month or not. This parameter is called "Equal amounts per period." In this example, the deferral schedule was created with Equal amounts per period = No which allows us to pro-rate by day.

![](media/image4.png)

In Revenue and expense deferrals we get the same values as we saw in the Revenue recognition example when setting Equal amounts per period = No.

![Graphical user interface  application  email Description automatically generated](media/image9.png)

Example 3: One year deferral with equal amounts per occurrence (12), starting on the date of the invoice.

**  
Revenue recognition**

Revenue schedule in revenue recognition with Occurrences = 12, Recognition basis = Monthly, Recognition convention = Actual start date. Sales order amount = 1500

![Table Description automatically generated](media/image10.png)

![Table Description automatically generated](media/image11.png)

Revenue recognition schedule showing monthly recognition of 125.00.

![Graphical user interface  application Description automatically generated](media/image12.png)

**Revenue and expense deferrals**

Deferral template with Period frequency = Monthly. Lines set up with Type = Recognized, Period length = 12. With Revenue and expense deferrals there is a parameter that will either pro-rate the amount by the number of days in a month or not. This parameter is called "Equal amounts per period." In this example, the deferral schedule was created with Equal amounts per period = Yes.

![](media/image4.png)

![Graphical user interface  application Description automatically generated](media/image5.png)

Example 4: One year deferral with monthly amounts based on fiscal period starting on the date of the invoice.

**Revenue recognition**

Revenue schedule in revenue recognition with Occurrences = 12, Recognition basis = Monthly by days, Recognition convention = Actual start date. Sales order amount = 1500  
![Table Description automatically generated](media/image13.png)

![Table Description automatically generated](media/image14.png)

Revenue recognition amounts will vary by period due to the number of days in each month being different.

\*\*Note that there appears to be a bug in this scenario as one of the periods gets allocated two period's worth of revenue. See October period in this example, which impacts the December amount.

![Graphical user interface  application  table Description automatically generated](media/image15.png)

**Revenue and expense deferrals**

Deferral template with Period frequency = Monthly. Lines set up with Type = Recognized, Period length = 12. With Revenue and expense deferrals there is a parameter that will either pro-rate the amount by the number of days in a month or not. This parameter is called "Equal amounts per period." In this example, the deferral schedule was created with Equal amounts per period = No which allows us to pro-rate by day.

![](media/image4.png)

In Revenue and expense deferrals we get the same values as we saw in the Revenue recognition example when setting Equal amounts per period = No.

![Graphical user interface  application Description automatically generated](media/image16.png)

<u>Recognition convention scenarios</u>

The **Recognition convention** in Revenue recognition determines the dates that are set on the revenue schedule for the invoice. In Revenue and expense deferrals, the deferral start date is determined based on the Revenue and expense deferral parameter **Default deferral start date**.

| Revenue recognition convention           | Revenue and expense deferrals Default deferral start date |
|------------------------------------------|-----------------------------------------------------------|
| Actual start date                        | Transaction date                                          |
| 1<sup>st</sup> day of month/period       | Beginning of current month                                |
| Mid month split                          | Rule of 15                                                |
| 1<sup>st</sup> date of next month/period | Beginning of next month                                   |
| End of month/period                      | \*Override deferral start date on transaction             |

Revenue recognition

![Graphical user interface  application Description automatically generated](media/image17.png)

Revenue and expense deferrals

![Graphical user interface  application Description automatically generated](media/image18.png)

![Graphical user interface  application Description automatically generated](media/image19.png)

![Table Description automatically generated with medium confidence](media/image20.png)

<u>Revenue schedule options</u>

Automatic hold

**Revenue recognition**

Marking **Automatic hold** will automatically put all revenue schedule lines on hold when the invoice is posted.

**Revenue and expense deferrals**

Deferral schedules can be placed on hold individually, but do not have an option to be created in an on hold state.

Automatic contract terms

**Revenue recognition**

Post contract support (PCS) items will have the contract start date set to the sales order line's requested ship date. The end date will be calculated based on the number of months or occurrences on the revenue schedule.

**Subscription billing**

A deferral template will set the deferral start date and deferral end date based on the template definition along with the **Default deferral start date**.

**<u>How to move in process revenue schedules to a deferral schedule in Revenue and expense deferrals</u>**

In the first example, we'll take a revenue recognition schedule that was by fiscal period with even amounts starting January 1 and has been recognized through June 30. We'll start by exporting the information we need from the Revenue recognition entity "Deferred line" (RevRecDeferredLineEntity). The screenshot below shows the information for the revenue schedule for sales order 000861.

![Graphical user interface  application  table Description automatically generated](media/image21.png)

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

![Graphical user interface  text  application  email Description automatically generated](media/image22.png)

We have a final step to take as this schedule was recognized through June 30 in revenue recognition. We will use the stubbing option to set the January – June periods as stubbed so we do not recognize those through this deferral schedule. We do this through the Recognition processing periodic task (Subscription billing – Revenue and expense deferrals – Periodic tasks – Recognition processing). We will use Recognition action = Stub and set the Cutoff date = 6/30/2023. In this example, I did add a filter for the individual billing schedule.

![](media/image23.png)  
View preview shows us 6 periods will be stubbed.

![Table Description automatically generated](media/image24.png)

Click Process. We should see a notification that Schedule lines processed: 6.

Now if we look at the deferral schedule we will see that the first 6 periods are marked as stubbed.

![Graphical user interface  text  application  email Description automatically generated](media/image25.png)

When recognition processing is run the next period for this schedule that will be recognized will be July 1 – July 31.
