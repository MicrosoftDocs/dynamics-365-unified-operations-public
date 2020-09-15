# Priority-based Throttling FAQ

[!include[banner](../includes/banner.md)]

This topic provides answers to some frequently asked questions about [Priority-based throttling](priority-based-batch-scheduling.md). 

## Can you post the link to the Data managment Yammer group?

Group link https://www.yammer.com/dynamicsaxfeedbackprograms/#/threads/inGroup?type=in_group&feedId=13408417 

## Will a retry request get preferential treatment over a brand new request?

No. 

## Is the report that was used to determine when throttling might happen ?

Yes, a report will be provided than can be accessed through LCS Raw logs within environment monitoring page.

## Will throttling impact DIXF and Batch?

No, Throttling is only for Odata and custom service integrations.

## In Preview, if Priorities are not configured , will my requests get throttled ?

No, Only telemetry will be available, but the actual throttling happen if you configure priorities and this is the recommended approach in NON prod environment within the Preview period

## What happens to the requests if user didn't retry the throttled request? 

Current if the request is not retried when a 429 error received, it will not be processed.

## Will historic throttling information be used to advise on resizing of environments?

Yes, for 1 month, you can export to ecxel for more analysis and archiving.

## Is throttling functionality D365 version specific? If yes in which version is this available?

Priority based throttling (This feature) will be available in Preview starting platform update 37.

## Any plans to provide and Enable/Disable option per "Priority mapping" grid entry?

We will consider this request in a future release.

## Will my interactive users’ requests get throttled ?

No, there will be no impact on interactive (Online) users requests.

## If I am facing performance issue in F&O while loading a form or processing a business document how that performance issue is different from Throttling?

Throttling will help maintain a healthy system when there is a resource constraint, it will not impact any forms actions.

## How can I determine the wait time before retrying a throttled request?

When a request get throttled, the response header will include a time to be used in retry logic.

## Is it recommended to use a dedicated integration account, instead of just the generic admin user account?

Yes, but it is not mandatory.

## Is Throttling dependable of the Tier your FO environment is running on?

In the initial release, No. throttling will calculate its threshold based on the resources available per environment.

## Is there any specification on legal entity  ?

No.

## is throttling impact BYOD export ?

No.

## Will throttling monitoring be available (when) in Azure Application Insights?

Monitoring will be onboarded to any available tool in the future.

## If a Production environment is regularly running out of resources wouldn't Microsoft need to re-size it? Is that not correct?

Correct, Sizing estimate will also need to be revalidated and uploaded.

## After April 2021, could priority-based throttling be overridden by the system?

System will use default values if no priorities are configured after April 2021.

## Can the throttling engine be configured (thresholds)?

No.



