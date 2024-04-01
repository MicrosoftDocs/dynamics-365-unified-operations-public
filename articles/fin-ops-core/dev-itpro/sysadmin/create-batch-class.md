---
# required metadata

title: Create a Batch Class
description: Create a Batch Class in Visual Studio.
author: cwithfourplus
ms.date: 04/01/2024
ms.topic: article
audience: IT Pro
# ms.devlang: 
ms.reviewer: johnmichalak
# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: vikaush
ms.search.validFrom: 2024-03-07
ms.dyn365.ops.version: Platform Update50
---
# Create a Batch Class

[!include [banner](../includes/banner.md)]

In Dynamics 365 Finance and Operations, batch processing allows you to perform tasks efficiently in the background, without impacting the performance of the system. In this tutorial, we learn how to create a Batch Class using Batch Run Base as the base class.

## Prerequisites
- Access to Dynamics 365 Finance and Operations environment.
- Basic understanding of X++ programming language.
- Visual Studio with Dynamics 365 Finance and Operations development tools installed.

## Create a new Batch Class using Run Base Batch

1. **Open Visual Studio**: Launch Visual Studio and connect to your Dynamics 365 Finance and Operations development environment.

2. **Create a New Class**: Right-click on your project in Solution Explorer and select **Add** > **New Item**. Choose **FinNaceOperations** > **Dynamics 365 Items** > **Code** > **Class**. Give your class a meaningful name, for example, **MyBatchClass**.

3. **Define the Class**: Inside your class, define it by extending the **RunBaseBatch** class. This class provides the basic functionality required for batch processing.

```X++
class MyBatchClass extends RunBaseBatch
{
    // Your code will go here
}
```

4. **Override Methods**: Override the necessary methods provided by the **RunBaseBatch** class. The most commonly overridden methods are **run()** and **main()**.

```X++
public void run()
{
    // This method is the entry point for the batch class
    super();
}

public static void main(Args _args)
{
    // This method is used to create an instance of the batch class, prompt the user for input using dialog(),
    // and then execute the batch job using runBase().
}
```

5. **Implement Batch Logic**: Inside the **run()** method, implement the logic that you want the batch job to perform. It could include data processing, calculations, or any other tasks. Inside **main()** method, instantiate batch class and invoke **runBase()**.

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
    batch.runBase();
}
```

6. **Configure Batch Parameters**: Let's integrate the **dialog()** method into our Batch Class. The **dialog()** method allows you to prompt users for input when they schedule the batch job. 

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
        // for input using dialog(), and then execute the batch job using runBase().

        MyBatchClass batch = new MyBatchClass();
        batch.dialog();
        batch.runBase();
    }
}
```

7. **Deploy and Schedule**: Once your batch class is ready, deploy it to your Dynamics 365 Finance and Operations environment. You can then schedule the batch job to run at specific intervals using the batch job scheduler in the application.

## Best Practices

- **Implement Batch Retry Logic**: Ensure that your batch classes can be retried, meaning they can be reattempted automatically if there's failure. This helps in handling transient errors and ensures robustness in processing.
- **Effective Error Handling**: Implement robust error handling mechanisms within your batch class to gracefully handle exceptions and errors. Log errors appropriately for troubleshooting and monitoring purposes.
- **Short Transaction Duration**: Keep the duration of individual transactions within your batch class as short as possible to minimize locking and contention issues in the database. This helps in improving concurrency and overall system performance.
- **Avoid Adding Too Many Tasks**: Exercise caution when adding tasks to a single batch job, as exceeding 1,000 tasks would lead to inefficiencies, and surpassing 4,000 tasks is considered excessive. It's advisable to decompose intricate Batch Job processing into smaller jobs, more manageable tasks to enhance both maintainability and performance.
- **Limit Batch Task Dependencies**: Avoid excessive dependencies between batch tasks within a job. Minimize dependencies to ensure that tasks can be executed independently, improving parallelism and scalability.
- **Optimize Batch Parameter Usage**: Efficiently use batch parameters to pass necessary information to the batch job. Avoid overloading parameters with excessive data to maintain clarity and simplicity.
- **Keep Execution Duration Short**: Ensure that the execution duration of your batch class remains short to mitigate the effect of transient infrastructure issues. By keeping processing times brief, you can minimize the window of vulnerability and better manage system interruptions.
- **Design for Idempotency**: Design batch class operations to be idempotent, meaning that executing the same operation multiple times has the same result as executing it once. It ensures that retrying a failed batch job doesn't lead to duplicate or unintended processing, maintaining data integrity.
- **Implement Transactional Integrity**: Ensure that batch class operations maintain transactional integrity, so that if there was a failure, transactions can be rolled back to prevent partial or inconsistent data updates. This helps in preserving data consistency and reliability.
- **Use Checkpoints for Resuming**: Implement checkpoints within your batch class to track progress and facilitate resuming from the last successfully processed record if there was failure. It allows for efficient recovery without reprocessing already completed tasks.
- **Handle Partial Failures Gracefully**: Implement error handling mechanisms to gracefully handle partial failures within batch class operations. Log errors, rollback transactions if necessary, and provide appropriate notifications for troubleshooting and resolution.
- **Utilize Batch Concurrency Control**: Implement [batch concurrency control](priority-based-batch-scheduling.md#batch-concurrency) mechanisms to manage parallel processing and avoid excessive load on similar data entities. By controlling the degree of parallelism, you can prevent contention and performance degradation caused by concurrent access to the same data. Configure batch concurrency settings appropriately based on workload characteristics and system resources to optimize throughput and maintain system stability.
- **Enable Batch History for Errors Only in Production**:
Configure batch history settings to log detailed information only for error situations in production environments. This approach helps to prevent the accumulation of large batch history, especially in batch jobs with numerous tasks or frequently recurring schedules. By limiting batch history to errors, you can effectively manage storage usage and maintain clarity in monitoring batch job performance and troubleshooting issues.
- **Test Idempotency and Recovery**: Thoroughly test the idempotency and recovery capabilities of your batch class under various failure scenarios. Validate that retrying a failed batch job doesn't result in duplicate or inconsistent data, ensuring robustness in production environments.
- **Monitor Batch Job Performance**: Regularly monitor the performance of your batch jobs to identify any bottlenecks or areas for optimization. Use monitoring tools and logs to track resource utilization and processing times.
- **Schedule Batch Jobs Wisely**: Schedule batch jobs during off-peak hours to ensure it doesn't interfere with system performance and user experience. Consider workload patterns and resource availability when scheduling batch processing. For recuring workloads you can consider [active batch periods](activeperiod.md).
- **Test Batch Jobs Thoroughly**: Perform comprehensive testing of batch jobs in a development or test environment before deploying them to production. Validate functionality, error handling, and performance under various scenarios.

## Next Steps

After creating a Batch Class, you can further enhance it by adding error handling, logging, and other features to make it more robust and efficient. You can also explore advanced articles such as:

- [Enable batch retries](retryable-batch.md)
- [Batch parameter versioning](batch-parameter-versioning.md) 
- [Create batch jobs](../../fin-ops/sysadmin/create-batch-job.md)