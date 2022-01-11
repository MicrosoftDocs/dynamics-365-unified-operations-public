---
# required metadata

title: Batch OData API
description: This topic provides information about the Batch OData application programming interface (API) and explains how you can use Open Data Protocol (OData) to reschedule a job.
author: matapg007
ms.date: 01/06/2022
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: matgupta
ms.search.validFrom: 2021-10-21
---

# Batch OData API

[!include[banner](../includes/banner.md)]

This topic provides information about the Batch OData application programming interface (API) and explains how you can use Open Data Protocol (OData) to reschedule a job.

In the existing [batch processing](batch-processing-overview.md) functionality, if some types of job failures need to be retried, either with or without any changes, based on the interpretation of the error, they must be manually.For jobs that are scheduled to be run during off-peak times to avoid active business hours for customers, monitoring failures and re-triggering the jobs requires either 24/7 support or a wait time until users resume work during normal business hours.

## Business events integration with Batch)

Business event capabilities enable customers to configure notifications about changes in state (started, failed, finished, or canceled) for batch jobs. Integration with [Microsoft Power Automate](../business-events/business-events-flow.md) lets customers capture information about affected jobs without having to sign in to the system. However, manual intervention is required if any action must be taken based on the business events.

For information about how to configure batch events, see [Batch business events](../business-events/system-business-events.md).

## End-to-end automation

In version 10.0.22, the batch functionality now provides an OData API that can be used to requeue batch jobs. Customers can use the OData endpoint to requeue batch jobs that are in a terminal state. This feature can be integrated with any automation by using Power Automate, custom APIs, and so on.

![End-to-end automation.]
![image](https://user-images.githubusercontent.com/90061039/148861172-7ff123f4-1269-40c2-b32d-b49956824c0c.png)

## Automate requeuing of failed batch jobs by using OData API

The Batch OData endpoint lets users consume and automate the end-to-end process to reschedule a batch job by using Power Automate or custom API. It supports updates of the batch job status from a started, failed, finished, or canceled state to a waiting state, based on business requirements.

Steps to automate using Power Automate:
1.	Login to [Power Automate](https://flow.microsoft.com) portal and create new flow following [instructions](https://docs.microsoft.com/en-us/power-automate/get-started-logic-flow)

2.	Specify an event Fin & Ops Apps (Dynamics 365) to start the flow and enter the environment details, business event category, business event as ‘batch Job Failed’ and appropriate legal entity.
![image](https://user-images.githubusercontent.com/90061039/148860987-578b8013-bad5-431d-8fa9-8a61be59889b.png)

3. Add new step from Actions tab to choose an operation named Parse JSON with schema to parse the Jason request. For more information to download JSON schema and [Business events catalog](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/business-events/home-page#business-event-catalog)

4. Add custom logic by including a logical condition to check if event is from the target batch job using Job ID.

![image](https://user-images.githubusercontent.com/90061039/148860962-4cef2156-8138-4c9c-bb8a-be22fee9382e.png)

5. If above condition results to yes, then add an action by choosing an operation Fin & Ops Apps (Dynamics 365) and selecting Execute action to trigger batch OData action to set the job back to execution.
a.	Enter Dynamics 365 for Fin & Ops instance
b.	Select action BatchJobs-SetBatchJobToWaiting from available options
c.	Select the Job Id to rerun the failed job
![image](https://user-images.githubusercontent.com/90061039/148861040-fd70b5ee-5234-4158-8124-3767786e585c.png)

6.	Save the flow

Above configured flow will listen to the batch events and if the configured batch jobs fail flow will set the job back for execution. As best practice we recommend adding custom logic (refer to above example) to validate before retrying batch jobs to avoid unnecessary load on the system. We also suggest specifying a limit on max number of times a batch can be retried [recommended is 5].
There are also other ways to subscribe to Business events and more details how to configure batch events, see [Batch business events](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/business-events/system-business-events)

Batch API endpoint and sample repsonse
- **Service endpoint:** `https://<org url>/data/BatchJobs/Microsoft.Dynamics.DataEntities.SetBatchJobToWaiting`
- **Method type:** POST
- **Header:**

    - **Authorization:** Bearer \<Bearer token for authentication\>
    - **Content-Type:** application/json

- **Body:**

    ```json
    {
        "batchJobId":<BatchJobId>
    }
    ```

- **Sample response:**

    ```json
    {
        "ResponseStatusCode":200,
        "IsSuccess":true,
        "Batch JobId":<BatchJobId>,
        "ExceptionDetails":"",
        "reponseMessage":"Status of supplied BatchJobId: *********** is Successfully updated to waiting state"
    }
    ```

    Here is an explanation of the elements of the response output:

    - **ResponseStatusCode** – A standard HTTP response code, based on the execution of the action.
    - **IsSuccess** – A Boolean value that indicates overall success or failure.
    - **BatchJobId** – The ID of the input batch job.
    - **ExceptionDetails** – Details about any exception that occurred during execution.
    - **ReponseMessage** – The success message.
