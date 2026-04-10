---
title: Batch OData API
description: Learn about the Batch OData application programming interface (API) and explains how you can use Open Data Protocol (OData) to reschedule a job.
author: matapg007
ms.author: matgupta
ms.topic: how-to
ms.date: 03/13/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2021-10-21
---

# Batch OData API

[!include[banner](../includes/banner.md)]

This article provides information about the batch Open Data Protocol (OData) application programming interface (API) and explains how you can use OData to reschedule a job.

In the existing [batch processing](batch-processing-overview.md) functionality, you must manually retry some types of job failures, either with or without any changes, based on the interpretation of the error. To avoid active business hours for customers, schedule jobs to run during off-peak times. Monitoring failures and re-triggering the jobs requires either 24/7 support or a wait time until users resume work during normal business hours.

## Integration of business events with batch functionality

By using business event capabilities, you can configure notifications about changes in state (started, failed, finished, or canceled) for batch jobs. By integrating with [Microsoft Power Automate](../business-events/business-events-flow.md), you can capture information about affected jobs without having to sign in to the system. However, manual intervention is required if you need to take any action based on the business events.

For information about how to configure batch events, see [Batch business events](../business-events/system-business-events.md).

## End-to-end automation

In version 10.0.22, the batch functionality provides an OData API that you can use to requeue batch jobs. You can use the OData endpoint to requeue batch jobs that are in a terminal state. You can integrate this feature with any automation by using Power Automate, custom APIs, and so on.

:::image type="content" source="./media/end-to-end-automation.png" alt-text="Screenshot of end-to-end automation.":::

## Automate requeuing of failed batch jobs by using the OData API

By using the batch OData endpoint, you can consume and automate the end-to-end process to reschedule a batch job by using Power Automate or custom APIs. It supports updates of the batch job status from a started, failed, finished, or canceled state to a waiting state, based on business requirements.

Follow these steps to automate requeuing of failed batch jobs by using Power Automate.

1. Sign in to the [Power Automate portal](https://flow.microsoft.com), and create a flow by following the instructions in [Create a cloud flow in Power Automate](/power-automate/get-started-logic-flow).
1. Specify an event in finance and operations apps to start the flow. Enter the environment details, a business event category, a business event (such as **Batch Job Failed**), and an appropriate legal entity.

   :::image type="content" source="./media/business-event-occurs.png" alt-text="Screenshot of specifying an event in Power Automate.":::

1. On the **Actions** tab, add a new step to select an operation named **Parse JSON with schema** to parse the JavaScript Object Notation (JSON) request. For more information about how to download a JSON schema, see [Business events catalog](../business-events/home-page.md#business-event-catalog).
1. Add custom logic by including a logical condition that uses the job ID to determine whether the event is from the target batch job.

   :::image type="content" source="./media/condition.png" alt-text="Screenshot of adding custom logic with a logical condition.":::

1. If the condition is true, add an action by selecting an operation in finance and operations apps, and then selecting **Execute action** to trigger the batch OData action to set the job back for execution.

   1. Enter the finance and operations apps instance.
   1. Select the **BatchJobs-SetBatchJobToWaiting** action.
   1. Select the job ID to rerun the failed job.

   :::image type="content" source="./media/execute-odata-api.png" alt-text="Screenshot of adding an action to execute the OData API.":::

1. Save the flow.

The flow that you just configured listens to the batch events. If the configured batch jobs fail, the flow sets the job back for execution. As a best practice, add custom logic (see the previous example) to perform validation before batch jobs are retried. This approach helps prevent unnecessary load on the system. Also, specify a limit on the maximum number of times that a batch can be retried. The recommended number of retries is five.

You can subscribe to business events in other ways. For more information, and for information about how to configure batch events, see [Batch business events](../business-events/system-business-events.md).

## Batch API endpoint and sample response

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
  - **ResponseMessage** – The success message.

