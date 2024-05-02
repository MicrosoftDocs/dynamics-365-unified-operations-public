---
title: Create a batch class
description: Learn about how to create a batch class for Microsoft Dynamics 365 finance and operations apps to efficiently perform tasks in the background in Visual Studio.
author: cwithfourplus
ms.author: johnmichalak
ms.topic: how-to
ms.date: 04/01/2024
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2024-03-07
ms.dyn365.ops.version: Platform Update50
---

# Create a batch class

[!include [banner](../includes/banner.md)]

In Microsoft Dynamics 365 finance and operations apps, batch processing lets you efficiently perform tasks in the background, without affecting system performance. This article explains how to create a batch class by using `RunBaseBatch` as the base class.

## Prerequisites

To create a batch class, you must have the following prerequisites:

- Access to a finance and operations apps environment
- A basic understanding of the X++ programming language
- Visual Studio with finance and operations development tools installed

## Create a batch class by using RunBaseBatch

1. In Visual Studio, connect to your finance and operations apps development environment.
1. In Solution Explorer, select and hold (or right-click) your project, and then select **Add** \> **New Item**.
1. Select **FinNaceOperations** \> **Dynamics 365 Items** \> **Code** \> **Class**.
1. Enter a meaningful name for the class, such as **MyBatchClass**.
1. Inside the new class, define the class by extending the `RunBaseBatch` class. The `RunBaseBatch` class provides the basic functionality that's required for batch processing.

    ```X++
    class MyBatchClass extends RunBaseBatch
    {
        // Your code will go here
    }
    ```

1. As required, override the methods that the `RunBaseBatch` class provides. The most commonly overridden methods are `run()` and `main()`.

    ```X++
    public void run()
    {
        // This method is the entry point for the batch class
        super();
    }

    public static void main(Args _args)
    {
        // This method is used to create an instance of the batch class, prompt the user for input using dialog,
        // and then execute the batch job using run().
    }
    ```

1. Inside the `run()` method, implement the logic that you want the batch job to perform. This logic might include data processing, calculations, or any other tasks. Inside the `main()` method, instantiate the batch class, and invoke `run()`.

    ```X++
    public void run()
    {
        // Perform batch processing tasks here
        // For example:
        info("Batch job started!");
        // Your logic goes here
        info("Batch job completed!"); 
    }

    public static void main(Args _args)
    {
        MyBatchClass batch = new MyBatchClass();
        // Run the batch class
        batch.run();
    }
    ```

1. Integrate the `dialog()` method into the batch class. The `dialog()` method lets you prompt users for input when they schedule the batch job. 

    ```X++
    class MyBatchClass extends RunBaseBatch
    {
        DialogField dialogMyParameter;

        str myParameter = "Default value";

        #define.CurrentVersion(1)
        #localmacro.CurrentList
            myParameter
        #endmacro

        public container pack()
        {
            // This method is used by batch platform to serialize batch parameters in a container
            return [#CurrentVersion, #CurrentList];
        }

        public boolean unpack(container _packedClass)
        {
            // This method is used by batch platform to deserialize batch parameters from stored 
            // batch parameter container

            Integer version = RunBase::getVersion(_packedClass);
            container packedData;

            switch (version)
            {
                case #CurrentVersion:
                    [version, #CurrentList] = _packedClass;
                    break;
                default:
                    return false;
            }

            return true;
        }

        public Object dialog()
        {
            // This method is invoked when user opens batch parameter dialog
            // It helps to add parameters to batch class and set their default value

            DialogRunbase dialog = super();

            dialogMyParameter = dialog.addField(enum2Str(Types::Integer), "My Parameter");

            // Set a default value of parameter
            dialogMyParameter.value(myParameter);

            return dialog;
        }

        public boolean getFromDialog()
        {
            // This method is invoked by batch platform to read the values of parameters from batch 
            // parameter dialog method
            myParameter = dialogMyParameter.value(); 

            return super();
        }

        public void run()
        {
            // This method is the entry point for the batch class

            info("Batch job started!");
            // Access the parameter value entered by the user
            info("My Parameter: " + this.myParameter);
            // Your main batch logic goes here
            info("Batch job completed!");
        }

        public static void main(Args _args)
        {
            // This method is used to create an instance of the batch class, prompt the user 
            // for input using dialog, and then execute the batch job using run().

            MyBatchClass batch = new MyBatchClass();
            if (batch.prompt())
            {
                batch.run();
            }
        }
    }
    ```

1. After the batch class is ready, deploy it to your finance and operations apps environment. You can then use the batch job scheduler in the application to schedule the batch job so that it runs at specific intervals.

## Best practices

- **Implement batch retry logic.** Ensure that your batch classes can be retried. In other words, they can automatically be reattempted if there's a failure. This approach helps handle transient errors and ensures robustness in processing.
- **Implement effective error handling.** Implement robust error handling mechanisms in your batch class to gracefully handle exceptions and errors. Appropriately log errors for troubleshooting and monitoring purposes.
- **Keep the transaction duration short.** Keep the duration of individual transactions in your batch class as short as possible to minimize locking and contention issues in the database. This approach helps improve concurrency and overall system performance.
- **Avoid adding too many tasks.** Be careful when you add tasks to a single batch job. More than 1,000 tasks lead to inefficiencies, and more than 4,000 tasks are considered excessive. We recommend that you decompose intricate batch job processing into smaller jobs and more manageable tasks to enhance both maintainability and performance.
- **Limit batch task dependencies.** Avoid excessive dependencies between the batch tasks in a job. Minimize dependencies to ensure that tasks can be run independently. This approach helps improve parallelism and scalability.
- **Optimize batch parameter use.** Efficiently use batch parameters to pass necessary information to the batch job. To maintain clarity and simplicity, avoid overloading parameters with excessive data.
- **Keep the execution duration short.** To mitigate the effect of transient infrastructure issues, ensure that the execution duration of your batch class remains short. By keeping processing times short, you can minimize the window of vulnerability and better manage system interruptions.
- **Design for idempotency.** Design batch class operations so that they're idempotent. In other words, multiple executions of the same operation should have the same result as a single execution. This approach ensures that retries of a failed batch job don't lead to duplicate or unintended processing. Therefore, it helps maintain data integrity.
- **Implement transactional integrity.** Ensure that batch class operations maintain transactional integrity. Therefore, if there's a failure, transactions can be rolled back to prevent partial or inconsistent data updates. This approach helps preserve data consistency and reliability.
- **Use checkpoints for resumption.** Implement checkpoints in your batch class to track progress and facilitate resumption from the last successfully processed record if there's failure. This approach allows for efficient recovery without requiring reprocessing of previously completed tasks.
- **Gracefully handle partial failures.** Implement error handling mechanisms to gracefully handle partial failures in batch class operations. Log errors, rollback transactions as required, and provide appropriate notifications for troubleshooting and resolution purposes.
- **Use batch concurrency control.** Implement [batch concurrency control](priority-based-batch-scheduling.md#batch-concurrency) mechanisms to manage parallel processing and avoid excessive load on similar data entities. By controlling the degree of parallelism, you can prevent contention and performance degradation that are caused by concurrent access to the same data. To optimize throughput and maintain system stability, appropriately configure the batch concurrency settings based on workload characteristics and system resources.
- **Enable batch history for errors only in production.** Configure batch history settings so that detailed information is logged only for error situations in production environments. This approach helps prevent the accumulation of large batch history, especially in batch jobs that have numerous tasks or in frequently recurring schedules. By limiting batch history to errors, you can effectively manage storage use and maintain clarity when you monitor batch job performance and troubleshoot issues.
- **Test idempotency and recovery.** Thoroughly test the idempotency and recovery capabilities of your batch class in various failure scenarios. To ensure robustness in production environments, validate that retries of a failed batch job don't lead to duplicate or inconsistent data.
- **Monitor batch job performance.** Regularly monitor the performance of your batch jobs to identify any bottlenecks or areas for optimization. Use monitoring tools and logs to track resource utilization and processing times.
- **Wisely schedule batch jobs.** Schedule batch jobs during off-peak hours to ensure that they don't interfere with system performance and the user experience. When you schedule batch processing, consider workload patterns and resource availability. For recuring workloads, consider [active batch periods](activeperiod.md).
- **Thoroughly test batch jobs.** Perform comprehensive testing of batch jobs in a development or test environment before you deploy them to production. Validate functionality, error handling, and performance in various scenarios.

## Next steps

After you create a batch class, you can enhance it by adding error handling, logging, and other features to make it more robust and efficient. You can also explore advanced articles such as the following list:

- [Enable batch retries](retryable-batch.md)
- [Batch parameter versioning](batch-parameter-versioning.md) 
- [Create batch jobs](../../fin-ops/sysadmin/create-batch-job.md)
