---
title: Testing and validations
description: Learn about how to create and run test cases, including prerequisites, key concepts, and a step-by-step process of using the SysTest framework to author test code.
author: josaw1
ms.author: josaw
ms.topic: how-to
ms.date: 03/16/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 41dcbbda-e377-45a8-b180-5daa0e63c4a9
---

# Testing and validations

[!include [banner](../includes/banner.md)]

This tutorial shows you how to create and run test cases.

## Prerequisites

You need to deploy Developer Topology with Developer and Build VM.

## Key concepts

- Use SysTest Framework to author unit and component test code.
- Test isolation.
- Test module creation to manage test code and FormAdaptors.
- Import Task Recorder recordings into Visual Studio to generate test code.
- Integrate a test module with a build machine.

:::image type="content" source="./media/54.png" alt-text="Screenshot of integrating a test module.":::  

## Use SysTest Framework to author unit/component test code

You can create new test cases to test the functionality in an application.

1. Open Visual Studio as an administrator.
1. On the **File** menu, select **Open** > **Project/Solution**, and then select the **FleetManagement** solution from the desktop folder. If the solution file isn't on your computer, see [End-to-end scenario for the Fleet Management sample application](../dev-tools/fleet-management-sample.md).
1. In **Solution Explorer**, right-click the **Fleet Management** solution, point to **Add**, and then select **New Project**.
1. Choose **finance and operations** as the project type to create.
1. Name this new project *FleetManagementUnitTestSample*, specify the FleetManagement folder on the desktop (C:\Users\Public\Desktop\FleetManagement) as the location, and then select **OK**.
1. In **Solution Explorer**, right-click the new project, and then select **Properties**.
1. Set the **Model** property to **FleetManagementUnitTests**, and then select **OK**.

   :::image type="content" source="./media/56.png" alt-text="Screenshot of the Model property setting.":::

1. Right-click the FleetManagementUnitTestSample project, point to **Add**, and then select **New Item**.
1. In the **Add New Item** window, select **Class** as the type of element to add. Name the new class FMUnitTestSample, and then select **Add**.

   :::image type="content" source="./media/57.png" alt-text="Screenshot of the Add New Item window.":::

1. In the first line of the code for the new class, indicate that the class extends the SysTestCase class.
1. Add the following code to define the methods for the class. These methods define two additional tests.

    ```xpp
    class FMUnitTestSample extends SysTestCase
    {
        public void setup()
        {
            // Reset the test data to be sure things are clean
            FMDataHelper::main(null);
        }

        [SysTestMethodAttribute]
        public void testFMTotalsEngine()
        {
            FMRental rental;
            FMTotalsEngine fmTotals;
            FMRentalTotal fmRentalTotal;
            FMRentalCharge rentalCharge;
            FMRentalTotal expectedtotal;
            str rentalID = '000022';

            // Find a known rental
            rental = FMRental::find(rentalID);

            // Get the rental charges associated with the rental
            // Data is seeded randomly, so this will change for each run
            select sum(ExtendedAmount) from rentalCharge
                    where rentalCharge.RentalId == rental.RentalId;

            fmTotals = FMTotalsEngine::construct();
            fmTotals.calculateRentalVehicleRate(rental);

            // Get the totals from the engine
            fmRentalTotal = fmTotals.totals(rental);

            // Set the expected amount
            expectedTotal = rental.VehicleRateTotal + rentalCharge.ExtendedAmount;

            this.assertEquals(expectedTotal,fmRentalTotal);
        }

        [SysTestMethodAttribute]
        public void testFMCarValidateField()
        {
            FMCarClass fmCar;

            fmCar.NumberOfDoors = -1;
            this.assertFalse(fmCar.validateField(Fieldnum("FMCarClass", "NumberOfDoors")));

            fmCar.NumberOfDoors = 4;
            this.assertTrue(fmCar.validateField(Fieldnum("FMCarClass", "NumberOfDoors")));
        }
    }
    ```

1. Save the new class. After the save is complete, the two additional test cases appear in **Test Explorer**. Right-click the FleetManagementUnitTestSample project in **Solution Explorer**, and then select **Build**.
1. On the **View** menu, open **Test Explorer**.
1. Select **Run selected test** to execute a specific test case.
1. **Test Explorer** shows the results of the test after it completes.

   :::image type="content" source="./media/59-300x290.png" alt-text="Screenshot of a completed test in Test Explorer.":::

## Test isolation

For a test to be valuable, it must be reliable. A test passes or fails consistently, independent of other factors such as other tests. One typical cause of unreliable tests is leaking state, such as data left behind in the database that influences downstream tests. To prevent this type of issue, use the ```SysTestTransaction``` attribute.

|  TestTransactionMode | Description  |
|---|---|
| AutoRollback | **Default**. Provides the best isolation.<br><br> All transactions roll back by using SQL save points, and all database statements route to the main connection, including user connections. No data persists. |
| LegacyRollback | All insert statements are tracked and deleted during clean-up.<br><br> All insert statements downgrade to row-by-row. One typical use case is when testing user connections or concurrency scenarios. This isolation level cleans up setup data. Wrap each test method in a `ttsBegin` and `ttsAbort`. |
| LegacyRollbackWithUpdateTracking | All update, delete, and insert statements are tracked and reverted during clean-up.<br><br> All insert, update, and delete statements are tracked and downgraded to row-by-row. This isolation level is the slowest. |
| None | **Only use for debugging**. Provides no isolation.<br><br> This setting can be useful to temporarily debug a test, as it allows you to use the regular user interface to navigate the data that the test created. |

Example:

```xpp
    [SysTestTransaction(TestTransactionMode::LegacyRollback)]
    class MyTestSample extends SysTestCase
```

## Test module creation to manage test code and FormAdaptors

Create a test-specific module to keep test code together and manageable.

1. Open **Visual Studio** and go to **Dynamics 365** > **Model Management** > **Create model**.

1. Enter the model name, select the layer, and then enter any additional details. Include the word **Test** in the name of the test module. The default build definition is configured to discover all test modules that contain the word **Test**.

1. Because this model holds forms from the Application Platform/Foundation, add references to the following models.

   :::image type="content" source="./media/62-1024x786.png" alt-text="Screenshot of model references.":::

After you create the base test module, import a Task Recorder recording to generate test code. When you import a Task Recorder recording XML, you generate test code by using FormAdaptors. Form adaptors are wrapper classes over forms, and they provide a strongly typed API that you can use to test form functionality. The product includes pregenerated FormAdaptors for each package for built-in forms. In the test module, add a reference to the corresponding FormAdaptor for packages and Test Essentials, which has helper methods to execute test code.

## Import a Task Recorder recording into Visual Studio to generate test code

You can generate test code from a Task Recorder recording to execute a headless (non-UI) test.

1. Record a scenario by using Task Recorder.

2. To import a Task Recording, in Visual Studio, select **Dynamics 365** > **Addins** > **Import Task Recording**.

3. In the **Import Task Recording** dialog, select the test module (ISVTestModule) under which you want to import the task recording, and browse to the recording XML file.

   :::image type="content" source="./media/64-249x300.png" alt-text="Screenshot of the Import Task Recording dialog with Test Module selected.":::

4. The task recording import process generates test code that's based on the SysTestAdapter and FormAdaptor. You can view this test code in the Visual Studio IDE. You don't need to change any test source code that's generated as part of this step.
  
5. After the test code is generated, set up Visual Studio options for test discovery and execution:
   - If you have a 64-bit machine, you can run unit tests and capture code coverage information as a 64-bit process.
   - To configure this option, select **Test** > **Test Settings** > **Default Processor Architecture**, and then select **X64**.
   - You might run into a situation where the test execution engine opens and locks an assembly in your test project. When this condition happens, you can't, for example, save changes to the assembly. To fix this problem, select **Test** > **Test Settings**, and then select **Keep Test Execution Engine Running**.
    - Now that you have test code generated in the Visual Studio IDE, it's time to discover the tests and try executing them locally.

6. From the menu options, select **Test** > **Windows**, and then select **Test Explorer**. After the **Test Explorer** window opens, it attempts to discover tests from the test code and lists all the available tests as shown in the following image.

    :::image type="content" source="./media/67-1024x658.png" alt-text="Screenshot of the Test Explorer window with available tests listed.":::

7. Select the test and then select **Run** > **Execute selected**. This action executes the test against the locally deployed environment.

   :::image type="content" source="./media/68-1024x652.png" alt-text="Screenshot of executing selected tests in Test Explorer.":::

## Integration of the test module with the build process

When you add the test module to source control, the build process template finds all test modules that have the word **Test** in their names. The following illustration shows build and test execution as part of Visual Studio Codespace.

:::image type="content" source="./media/69.png" alt-text="Screenshot of build and test execution as part of Visual Studio Codespace.":::

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
