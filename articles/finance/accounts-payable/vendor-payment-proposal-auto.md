
# Vendor payment proposal automation

Organizations that have a cyclical schedule for vendor payments can now automate the vendor payment proposal process. The payment proposal automation is used to define when payment proposals are run, what criteria is used to select the invoices to pay, and the vendor payment journal that the resulting payments are saved in.  The payment proposal automation does not automatically post the payments, allowing validation and workflow approvals to occur on the payments created. 

## Define vendor payment proposal occurrence
The vendor payment proposal automation uses the Process automation framework which can be used by different business processes to define the recurrence of the selected process. For vendor payment proposal, the automation can be accessed under Accounts payable – Payment setup – Process automation.
To begin, navigate to [can we get them to the page where they’ll do this?]. From the Create new process automation field select the Vendor payment proposal option. A wizard will open to walk through the setup of the vendor payment proposal. 
General page in wizard
Enter the name of the vendor proposal you are creating.  For example, if you pay all domestic vendors by check on Monday, you could enter a descriptive name such as Domestic_Check. The name is shown on the process automation calendar, which is displayed on the Vendor payment workspace. 
Define the owner of the payment journal that is created. Typically, this would be the AP payment clerk who is responsible for the payment journal after it’s created.  
The remaining settings are [generic to the process automation and are] used to define the recurrence pattern used for this version of the vendor payment proposal. For example, if this occurrence is for check payments on Monday, you could define the occurrence to run Weekly and Monday selected for the day of the week. Also, enter an early Schedule time such as 2:00 am so the process automation will be complete when arriving in the office. 
It’s important to understand that the wizard is used to set the timing for generating vendor payment proposals; it does not determine when the vendor payments are actually generated or printed or posted. The days on which payment proposals are generated is displayed in the calendar by the process automation. 
Refer to the Process automation documentation for more details on the other fields found on the General tab.  
## Vendor payment proposal page in wizard
The next page in the wizard is the Vendor payment proposal page, which is used to define the criteria for selecting the vendor invoices to pay.  Most options are the same as found in the payment proposal on the vendor payment journal, with a few exceptions. For example, all dates must be defined as a relative date since the payment proposal date changes each time the proposal is run according to the occurrence pattern.  
