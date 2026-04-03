---
title: Data task automation
description: Learn how you can use data task automation to repeat many types of data tasks and validate the outcome of each task.
author: twheeloc
ms.author: twheeloc
ms.topic: article
ms.custom: 
  - bap-template
ms.date: 04/03/2026
ms.reviewer: twheeloc
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: 
ms.dyn365.ops.version: Platform update 16
---

# Data task automation

[!include[banner](../includes/banner.md)]

Data task automation makes it easy to repeat many types of data tasks and validate the outcome of each task. Data task automation is very useful for projects that are in the implementation phase. For example, you can automate the creation and configuration of data projects. You can also automate the configuration and triggering of import/export operations, such as the setup of demo data and golden configuration data, and other tasks that are related to data migration. You can also create automated testing of data entities by using task outcome validation.

> [!IMPORTANT]
> Data task automation isn't currently supported for on-premises environments.
> The user who executes data task automation must be in the same tenant as the application environment and Lifecycle Services project.

Use the following approach for data task automation.

1. Identify the data-related tasks that benefit from automation.

    Review your configuration management plan and data migration plan to identify potential data tasks for automation. Also identify data entity test cases.

1. Define tasks.

    Define tasks in an XML manifest. Keep your manifest under source control as part of configuration management in your application lifecycle management (ALM) strategy.

1. Put the data packages that are related to data task automation in the Shared asset library of Microsoft Dynamics Lifecycle Services. You can also use a specific Lifecycle Services project as you require.

    Data task automation manager can consume packages from any sandbox and production environment that is related to the Lifecycle Services project.

    > [!IMPORTANT]
    > - The user account that runs Data task automation manager must have access to Lifecycle Services and to the Lifecycle Services project that the manifest references for data packages.
    > - Although you can run data task automation in any environment in the cloud, don't run any import/export tasks that use integration application programming interfaces (APIs) in a production environment. Use data task automation that involves integration APIs only for automated testing.

1. Run the data tasks, and then review the outcomes.

    Data task automation manager provides the success or failure outcome for each task. It also provides insights into the reason why a task failed.

    > [!IMPORTANT]
    > Although you can run data task automation in any environment in the cloud, don't run any import/export tasks that use integration APIs in a production environment. Use data task automation that involves integration APIs only for automated testing.

The following video is a 55-minute TechTalk that walks you through an early release of [Task automation framework](https://community.dynamics.com/365/b/techtalks/posts/task-automation-framework-for-data-management-march-3-2018).

## Task manifest
Define a task in an XML manifest. This section describes the manifest. For guidance about how to name and design the manifest, see the "Best practices for manifest design" section later in this article.

### Manifest root
The **\<TestManifest\>** element is the root of the manifest. All other elements are children of this element.

```xml
<?xml version='1.0' encoding='utf-8'?>
<TestManifest name='Data management demo data set up'>
    <SharedSetup />
        <JobDefinition ID='ImportJobDefinition_1' />
        <EntitySetup ID='Generic' />
    </SharedSetup>
    <TestGroup />
</TestManifest>
```

| Element          | Element Cardinality | Attributes | Attribute description                                     |
|------------------|---------------------|------------|-----------------------------------------------------------|
| \<TestManifest\> | 1..1                | name       | The *name* helps to identify the purpose of the manifest. |

### Shared setup
The **Shared setup** section defines general task parameters and behaviors for all tasks in the manifest.

| Parent element   | Element         | Element Cardinality | Attributes | Attribute description            |
|------------------|-----------------|---------------------|------------|----------------------------------|
| \<TestManifest\> | \<SharedSetup\> | 1..1                | \-         | This element takes no attributes. |

### Data files
**\<DataFile\>** elements define the data packages and data files that the tasks in the manifest use. The data files must be either in the Lifecycle Services asset library of your Lifecycle Services project or in the Shared asset library.

```xml
<DataFile ID='SharedSetup' name='Demo data-7.3-100-System and Shared'  assetType='Data package' lcsProjectId=''/>
<DataFile ID='FinancialsHQUS' name='Demo data-7.3-200-Financials-HQUS' assetType='Data package' lcsProjectId=''/>
<DataFile ID='FinancialsPICH' name='Demo data-7.3-200-Financials-PICH' assetType='Data package' lcsProjectId=''/>
<DataFile ID='FinancialsPIFB' name='Demo data-7.3-200-Financials-PIFB' assetType='Data package' lcsProjectId=''/>
```

| Parent element  | Element      | Element Cardinality | Attributes   | Attribute description |
|-----------------|--------------|---------------------|--------------|-----------------------|
| \<SharedSetup\> | \<DataFile\> | 1..n                | \-           | \- |
|                 | \<DataFile\> | \-                  | ID           | |
|                 | \<DataFile\> | \-                  | name         | Name of the asset that represents the data file. |
|                 | \<DataFile\> | \-                  | assetType    | The asset type in Lifecycle Services asset library that stores the data file. This is the asset type name as shown in Lifecycle Services asset library. |
|                 | \<DataFile\> | \-                  | lcsProjectId | The Lifecycle Services project that has the data file in its asset library. If the project ID is specified as '' then, it indicates the Shared asset library. |

### Data project definition
The **\<JobDefinition\>** element defines the data project definition. A manifest can contain more than one job definition.

```xml
<JobDefinition ID='ImportJobDefinition_1'>
    <Operation>Import</Operation>
    <ConfigurationOnly>No</ConfigurationOnly>
    <Truncate></Truncate>
    <Mode>Import async</Mode>
    <BatchFrequencyInMinutes>1</BatchFrequencyInMinutes>
    <NumberOfTimesToRunBatch >2</NumberOfTimesToRunBatch>
    <UploadFrequencyInSeconds>1</UploadFrequencyInSeconds>
    <TotalNumberOfTimesToUploadFile>1</TotalNumberOfTimesToUploadFile>
    <SupportedDataSourceType>Package</SupportedDataSourceType>
    <ProcessMessagesInOrder>No</ProcessMessagesInOrder>
    <PreventUploadWhenZeroRecords>No</PreventUploadWhenZeroRecords>
    <UseCompanyFromMessage>Yes</UseCompanyFromMessage>
    <LegalEntity>DAT</LegalEntity>
    <PackageAPIExecute>true</PackageAPIExecute>
    <PackageAPIOverwrite>false</PackageAPIOverwrite>
    <PackageAPIReexecute>false</PackageAPIReexecute>
    <DefinitionGroupID>TestExport</DefinitionGroupID>
    <PackageName>TestExportPackage</PackageName>
</JobDefinition>
```

| Parent element    | Element                          | Element cardinality | Attribute | Description |
|-------------------|----------------------------------|---------------------|-----------|-------------|
| \<SharedSetup\>   | \<JobDefinition\>                | 1..n                | ID        | Use the job definition ID in the tasks to reference the definition for the data project. |
| \<JobDefinition\> | \<Operation\>                    | 1..1                | \-        | Specify the operation to perform by using the following values: <br> - Import <br> - Export |
|                   | \<Truncate\>                     | 1..1                | \-        | This Boolean field has possible values of Yes or No. This field is applicable only when operation is set to *Import*. |
|                   | \<Mode\>                         | 1..1                | \-        | The mode specifies the method to use for the operation. The possible values are:<br>- Import async <br>- Export async <br>- Recurring batch: This value uses the enqueue API. Dequeue API isn't supported yet. Package API supports both export and import.|
|                   | \<ConfigurationOnly\>            | 0..1                | \-        | This Boolean field has possible values of Yes or No. Set this value to Yes if the task is only to configure the data project but not to perform the specified operation. |
|                   | \<BatchFrequencyInMinutes\>      | 1..1                | \-        | This value specifies the frequency in which the batch must be scheduled. This value is applicable only when mode is set to *recurring batch*. |
|                   | \<NumberOfTimesToRunBatch\>      | 1..1                | \-        | Set a limit to how many times the scheduled batch should run. This value is applicable only when mode is set to *recurring batch*. |
|                   | \<UploadFrequencyInSeconds\>     | 1..1                | \-        | This value controls the rate at which a file is uploaded to the recurring batch job for import. Use this value only for automated testing of recurring integrations in non-production environments. This value is applicable only when mode is set to *recurring batch* and operation is set to *Import*. |
|                   | \<TotalNumberOfTimesToUpload\>   | 1..1                |           | This value controls the total number of times the file should be uploaded to the recurring batch. Use this value only for automated testing of recurring integrations in non-production environments. This value is applicable only when mode is set to *recurring batch* and operation is set to *Import*. |
|                   | \<SupportedDataSoureType\>       | 1..1                |           | Use this value to specify if a file is being sent to the recurring batch or a package. This value is only applicable when mode is set to 'recurring batch'. |
|                   | \<ProcessMessagesInOrder\>       | 1..1                |           | This Boolean field has possible values of Yes or No. This field is applicable only when mode is set to *recurring batch* and operation is *Import*. |
|                   | \<PreventUploadWhenZeroRecords\> | 1..1                |           | This Boolean field has possible values of Yes or No. This field is applicable only when mode is set to *recurring batch* and operation is *Export*. |
|                   | \<UseCompanyFromMessage\>        | 1..1                |           | This Boolean field can be set to Yes or No. This field is applicable only when mode is set to *recurring batch* and operation is *Import*. |
|                   | \<LegalEntity\>                  | 1..1                |           | Use this value to specify the legal entity in which the import/export job must be executed. |
|                   | \<PackageAPIExecute\>            | 1..1                |           | Refer to package API documentation to understand this parameter. This Boolean field takes 'true' or 'false'. |
|                   | \<PackageAPIOverwrite\>            | 1..1                |           | Refer to package API documentation to understand this parameter. This Boolean field takes 'true' or 'false'. |
|                   | \<PackageAPIReexecute\>            | 1..1                |           | Refer to package API documentation to understand this parameter. This Boolean field takes 'true' or 'false'. |
|                   | \<DefinitionGroupID\>            | 1..1                |           | Refer to package API documentation to understand this parameter. This string field. |
|                   | \<PackageName\>            | 1..1                |           | Refer to package API documentation to understand this parameter. This string field. |

### Entity setup
The **Entity setup** section defines the characteristics of an entity that a task in the manifest uses. You can include more than one definition, with each definition corresponding to an entity that the tasks in the manifest use.

```xml
<EntitySetup ID='Generic'>
    <Entity name='*'>
        <SourceDataFormatName>Package</SourceDataFormatName>
        <ChangeTracking></ChangeTracking>
        <PublishToBYOD></PublishToBYOD>
        <DefaultRefreshType>Full push only</DefaultRefreshType>
        <ExcelWorkSheetName></ExcelWorkSheetName>
        <SelectFields>All fields</SelectFields>
        <SetBasedProcessing></SetBasedProcessing>
        <FailBatchOnErrorForExecutionUnit>No</FailBatchOnErrorForExecutionUnit>
        <FailBatchOnErrorForLevel>No</FailBatchOnErrorForLevel>
        <DisableEntity>No</DisableEntity>
        <SkipStaging>Yes</SkipStaging>
        <ParallelProcessing>
            <Threshold></Threshold>
            <TaskCount></TaskCount>
        </ParallelProcessing>
        <MappingDetail StagingFieldName='RoundingRulePrices' AutoGenerate='Yes' AutoDefault='No' DefaultValue='' IgnoreBlankValues='No' TextQualifier='No' UseEnumLabel='No'/>
        </Entity>
</EntitySetup>
```

| Parent element         | Element                              | Element cardinality | Attribute         | Description |
|------------------------|--------------------------------------|---------------------|-------------------|-------------|
| \<SharedSetup\>        | \<EntitySetup\>                      | 1..n                | ID                | An identification that tasks use to reference an entity definition. |
| \<EntitySetup\>        | \<Entity\>                           | 1..1                | name              | The entity element is identified by the entity's name. To facilitate easy manifest definition, this element also supports \* as a wildcard which means all entities used in a task. This support comes in very handy when using data packages with hundreds of entities in a task. |
| \<Entity\>             | \<SourceDataFormatName\>             | 1..1                | \-                | The file format to use for the entity. |
|                        | \<ChangeTracking\>                   | 1..1                | \-                | A Boolean field with possible values of Yes or No. It enables or disables change tracking on the entire entity. |
|                        | \<PublishToBYOD\>                    | 1..1                | \-                | A Boolean field with possible values of Yes or No. |
|                        | \<DefaultRefreshType\>               | 1..1                | \-                | Sets the default refresh rate on the entity. The possible values are *Incremental push only* or *Full push*. |
|                        | \<ExcelWorkSheetName\>               | 1..1                | \-                | Specifies the worksheet to use for the entity. |
|                        | \<SelectFields\>                     | 1..1                | \-                | Specifies the fields to include in the template for an export operation. |
|                        | \<SetBasedProcessing\>               | 1..1                | \-                | A Boolean field with possible values of Yes or No. It enables or disables set based processing on an entity. |
|                        | \<FailBatchOnErrorForExecutionUnit\> | 1..1                | \-                | A Boolean field with possible values of Yes or No. It enables or disables failure at execution unit level on an entity. |
|                        | \<FailBatchOnErrorForLevel\>         | 1..1                | \-                | A Boolean field with possible values of Yes or No. It enables or disables failure at execution level on an entity. |
|                        | \<DisableEntity\>                    | 1..1                | \-                | A Boolean field with possible values of Yes or No. It enables or disables an entity in a data project. |
|                        | \<SkipStaging\>                      | 1..1                | \-                | A Boolean field with possible values of Yes or No. It skips staging table for an entity during exports. |
|                        | \<ParallelProcessing\>               | 1..1                | \-                | Defines the parallel processing set up for an entity. The task deletes these settings if they already exist at the beginning of the task and it deletes the created settings at the end of its execution. |
| \<ParallelProcessing\> | \<Threshold\>                        | 1..1                | \-                | Specifies the threshold for the parallel processing rule. |
|                        | \<TaskCount\>                        | 1..1                | \-                | Specifies the number of parallel tasks to use for parallel processing. |
| \<Entity\>             | \<MappingDetail\>                    | 0..n                | \-                | Allows you to configure the *auto generate*, *auto default*, and other settings on the mapping for an entity. |
|                        | \<MappingDetail\>                    | \-                  | StagingFieldName  | Identifies the entity column for which to specify the settings. |
|                        | \<MappingDetail\>                    | \-                  | AutoGenerate      | A Boolean field with possible values of Yes or No for enabling or disabling auto generate option. |
|                        | \<MappingDetail\>                    | \-                  | AutoDefault       | A Boolean field with possible values of Yes or No for enabling or disabling auto default option. |
|                        | \<MappingDetail\>                    | \-                  | DefaultValue      | The default value to use if auto defaulting is enabled. |
|                        | \<MappingDetail\>                    | \-                  | IgnoreBlankValues | A Boolean field with possible values of Yes or No for enabling or disabling this option. |
|                        | \<MappingDetail\>                    | \-                  | TextQualifier     | A Boolean field with possible values of Yes or No for enabling or disabling this option. |
|                        | \<MappingDetail\>                    | \-                  | UseEnumLabel      | A Boolean field with possible values of Yes or No for enabling or disabling this option. |

### Test groups
Use test groups to organize related tasks in a manifest. A manifest can contain more than one test group.

```xml
<TestGroup name='Set up Financials'>
    <TestCase Title='Import shared set up data package' ID='3933885' RepeatCount='1' TraceParser='off' TimeOut='20'>
        <DataFile RefID='SharedSetup' />
        <JobDefinition RefID='ImportJobDefinition_1' />
        <EntitySetup RefID='Generic' />
    </TestCase>
    
    <TestCase Title='Import financials for HQUS' ID='3933886' RepeatCount='1' TraceParser='off' TimeOut='20'>
        <DataFile RefID='FinancialsHQUS' />
        <JobDefinition RefID='ImportJobDefinition_1'>
            <LegalEntity>HQUS</LegalEntity>
        </JobDefinition>
        <EntitySetup RefID='Generic' />
    </TestCase>

    <TestCase Title='Import financials for PICH' ID='3933887' RepeatCount='1' TraceParser='off' TimeOut='20'>
        <DataFile RefID='FinancialsPICH' />
        <JobDefinition RefID='ImportJobDefinition_1'>
            <LegalEntity>PICH</LegalEntity>
        </JobDefinition>
        <EntitySetup RefID='Generic' />
    </TestCase>

    <TestCase Title='Import financials for PIFB' ID='3933888' RepeatCount='1' TraceParser='off' TimeOut='20'>
        <DataFile RefID='FinancialsPIFB' />
        <JobDefinition RefID='ImportJobDefinition_1'>
            <LegalEntity>PIFB</LegalEntity>
        </JobDefinition>
        <EntitySetup RefID='Generic' />
    </TestCase>
</TestGroup>
```

| Parent element   | Element           | Element Cardinality | Attributes  | Description |
|------------------|-------------------|---------------------|-------------|-------------|
| \<TestManifest\> | \<TestGroup\>     | 1..n                | \-          | \- |
|                  | \<TestGroup\>     | 1..1                | Name        | The name for the group that identifies its functional reason. |
| \<TestGroup\>    | \<TestCase\>      | 1..n                | \-          | Defines the task. The task can refer to the shared set up to inherit task parameters and task behavior. The task can also override parameters and behavior at its level, which simplifies the management of the manifest. |
|                  | \<TestCase\>      | \-                  | Title       | The title for the task. |
|                  | \<TestCase\>      | \-                  | ID          | The ID for the task. This value can be alphanumeric with a maximum character limit of 10. |
|                  | \<TestCase\>      | \-                  | RepeatCount | A placeholder for a future functionality. However, you must specify this value as *1*. |
|                  | \<TestCase\>      | \-                  | TraceParser | A placeholder for a future functionality. However, you must specify this value as *off*. |
|                  | \<TestCase\>      | \-                  | Timeout     | The maximum duration that the task automation manager monitors a task. If the task is still active beyond the timeout specified, the manager proceeds to the next task in the manifest. |
| \<TestCase\>     | \<DataFile\>      | 1..n                | \-          | Defines the file or data package to use by the task. This element can reference an already declared file or a data package in the shared section of the manifest. A task can have more than one data file specified for recurring batch import scenarios only. For other scenarios, even if you specify more than one file, the task uses the first file. |
|                  | \<JobDefinition\> | 1..1                | \-          | Defines the data project to use by the task. This element can reference an already declared job definition in the shared section of the manifest. The task can override elements of job definition to a new value that you define in the shared set up. |
|                  | \<EntitySetup\>   | 1..1                | \-          | Defines the entity set up for entities used by the task. This element can reference an already declared entity set up in the shared section of the manifest. The task can override elements of entity setup to a new value that you define in the shared set up. |

## Best practices for manifest design
You can define a manifest in many ways. Consider the following pointers when you design a manifest.

### Granularity
Determine the granularity of your manifest as a functional decision. Your team must decide whether it wants to manage many manifests or manage changes in a single manifest.

- Start with as many manifests as your team thinks you logically need. Later, when the team actually starts to run the manifests, it might find that it uses fewer manifests than it expected, and it might want to merge them. In this case, you can merge manifests.
- Consider separation of duties. For example, you might have one manifest for the setup of demo data and another manifest for the setup of the golden configuration for your environment. By using this approach, you make sure that team members use only the manifests that they're supposed to use.
- Consider user access to Lifecycle Services. For example, larger and globally distributed implementation teams might have multiple instances of the application or multiple Lifecycle Services projects.

### Inheritance
The manifest schema supports inheritance of common elements that apply to all tasks in the manifest. A task can override a common element to define a unique behavior. The **Shared setup** section minimizes repetition of configuration elements by reusing elements as much as possible. This approach keeps the manifest concise and clean, improving maintenance and readability.

### Source control
Store manifests that all members of an implementation team must use in source control in the Application Object Tree (AOT). This approach not only provides the benefits of source control, but also enables a process to distribute or make manifests available to all users in a consistent manner. This approach also enables configuration management for data projects that are related to data management, if manifests are used for configuration.

### Number of job definitions and entity definitions
For most use cases, one job definition in a manifest is enough, because you can use inheritance to change the behavior at the task level. This principle also applies to entity definitions.

## Validations
Data task automation manager performs validations based on the setup of a task. If a task fails, you can quickly determine the reason for the failure by viewing the validations after the task completes. The level of information that Data task automation manager provides is optimized to facilitate initial discovery. For detailed investigation, you must look at the corresponding data project and its execution details.

The following data validations are currently supported:

- **Job status** – This validation checks whether the job was successful.
- **Batch status** – This validation checks whether the batch was successful.
- **Message status** – If the test is about integrations, this validation checks the message status.
- **Truncation** – If truncation is enabled, this validation checks whether truncation occurred.
- **Skip staging** – If **Skip staging** is enabled on a test, this validation checks whether staging was skipped.

## Example 1: Configuration management for data projects
Use the **\<ConfigurationOnly\>** element to create configuration tasks for data projects. When you set ConfigurationOnly to Yes, the data projects are only created but not executed. This setting allows you to manage data projects across environments in an automated manner.

```xml
<?xml version='1.0' encoding='utf-8'?>
<TestManifest name='Data management demo data set up'>
    <SharedSetup>
        <DataFile ID='SharedSetup' name='Demo data-7.3-100-System and Shared'  assetType='Data package' lcsProjectId=''/>
        <DataFile ID='FinancialsHQUS' name='Demo data-7.3-200-Financials-HQUS' assetType='Data package' lcsProjectId=''/>
        <DataFile ID='FinancialsPICH' name='Demo data-7.3-200-Financials-PICH' assetType='Data package' lcsProjectId=''/>
        <DataFile ID='FinancialsPIFB' name='Demo data-7.3-200-Financials-PIFB' assetType='Data package' lcsProjectId=''/>

        <JobDefinition ID='ImportJobDefinition_1'>
            <ConfigurationOnly>Yes</ConfigurationOnly>
            <Operation>Import</Operation>
            <Truncate>No</Truncate>
            <Mode>Import async</Mode>
            <BatchFrequencyInMinutes>1</BatchFrequencyInMinutes>
            <NumberOfTimesToRunBatch >2</NumberOfTimesToRunBatch>
            <UploadFrequencyInSeconds>1</UploadFrequencyInSeconds>
            <TotalNumberOfTimesToUploadFile>1</TotalNumberOfTimesToUploadFile>
            <SupportedDataSourceType>Package</SupportedDataSourceType>
            <ProcessMessagesInOrder>No</ProcessMessagesInOrder>
            <PreventUploadWhenZeroRecords>No</PreventUploadWhenZeroRecords>
            <UseCompanyFromMessage>Yes</UseCompanyFromMessage>
            <LegalEntity>DAT</LegalEntity>
        </JobDefinition>

        <EntitySetup ID='Generic'>
            <Entity name='*'>
                <SourceDataFormatName>Package</SourceDataFormatName>
                <ChangeTracking>No</ChangeTracking>
                <PublishToBYOD>No</PublishToBYOD>
                <DefaultRefreshType>Full push only</DefaultRefreshType>
                <ExcelWorkSheetName></ExcelWorkSheetName>
                <SelectFields>All fields</SelectFields>
                <SetBasedProcessing>No</SetBasedProcessing>
                <FailBatchOnErrorForExecutionUnit>No</FailBatchOnErrorForExecutionUnit>
                <FailBatchOnErrorForLevel>No</FailBatchOnErrorForLevel>
                <FailBatchOnErrorForSequence>No</FailBatchOnErrorForSequence>
                <ParallelProcessing>
                    <Threshold></Threshold>
                    <TaskCount></TaskCount>
                </ParallelProcessing>
            </Entity>
        </EntitySetup>
    </SharedSetup>

    <TestGroup name='Set up import jobs for Financials'>
        <TestCase Title='Set up import job for shared set up data package' ID='3933885' RepeatCount='1' TraceParser='off' TimeOut='20'>
            <DataFile RefID='SharedSetup' />
            <JobDefinition RefID='ImportJobDefinition_1' />
            <EntitySetup RefID='Generic' />
        </TestCase>

        <TestCase Title='Set up import job for financials HQUS' ID='3933886' RepeatCount='1' TraceParser='off' TimeOut='20'>
            <DataFile RefID='FinancialsHQUS' />
                <JobDefinition RefID='ImportJobDefinition_1'>
                    <LegalEntity>HQUS</LegalEntity>
                </JobDefinition>
                <EntitySetup RefID='Generic' />
        </TestCase>

        <TestCase Title='Set up import job for financials PICH' ID='3933887' RepeatCount='1' TraceParser='off' TimeOut='20'>
            <DataFile RefID='FinancialsPICH' />
                <JobDefinition RefID='ImportJobDefinition_1'>
                    <LegalEntity>PICH</LegalEntity>
                </JobDefinition>
                <EntitySetup RefID='Generic' />
        </TestCase>

        <TestCase Title='Set up import job for financials PIFB' ID='3933888' RepeatCount='1' TraceParser='off' TimeOut='20'>
            <DataFile RefID='FinancialsPIFB' />
                <JobDefinition RefID='ImportJobDefinition_1'>
                    <LegalEntity>PIFB</LegalEntity>
                </JobDefinition>
                <EntitySetup RefID='Generic' />
        </TestCase>
    </TestGroup>
</TestManifest>
```

## Example 2: Automated setup of demo data
The following manifest shows the setup of demo data for three legal entities when the demo data packages are stored in the Shared asset library. The difference in this example from the previous example is the actual execution of the data projects to set up the demo data. For consistency of the manifest, don't use the `ConfigurationOnly` option or set it to `No`.

```xml
<?xml version='1.0' encoding='utf-8'?>
<TestManifest name='Data management demo data set up'>
    <SharedSetup>
        <DataFile ID='SharedSetup' name='Demo data-7.3-100-System and Shared'  assetType='Data package' lcsProjectId=''/>
        <DataFile ID='FinancialsHQUS' name='Demo data-7.3-200-Financials-HQUS' assetType='Data package' lcsProjectId=''/>
        <DataFile ID='FinancialsPICH' name='Demo data-7.3-200-Financials-PICH' assetType='Data package' lcsProjectId=''/>
        <DataFile ID='FinancialsPIFB' name='Demo data-7.3-200-Financials-PIFB' assetType='Data package' lcsProjectId=''/>

        <JobDefinition ID='ImportJobDefinition_1'>
                <Operation>Import</Operation>
                <Truncate></Truncate>
                <Mode>Import async</Mode>
                <BatchFrequencyInMinutes>1</BatchFrequencyInMinutes>
                <NumberOfTimesToRunBatch >2</NumberOfTimesToRunBatch>
                <UploadFrequencyInSeconds>1</UploadFrequencyInSeconds>
                <TotalNumberOfTimesToUploadFile>1</TotalNumberOfTimesToUploadFile>
                <SupportedDataSourceType>Package</SupportedDataSourceType>
                <ProcessMessagesInOrder>No</ProcessMessagesInOrder>
                <PreventUploadWhenZeroRecords>No</PreventUploadWhenZeroRecords>
                <UseCompanyFromMessage>Yes</UseCompanyFromMessage>
                <LegalEntity>DAT</LegalEntity>
        </JobDefinition>

        <EntitySetup ID='Generic'>
            <Entity name='*'>
                <SourceDataFormatName>Package</SourceDataFormatName>
                <ChangeTracking></ChangeTracking>
                <PublishToBYOD></PublishToBYOD>
                <DefaultRefreshType>Full push only</DefaultRefreshType>
                <ExcelWorkSheetName></ExcelWorkSheetName>
                <SelectFields>All fields</SelectFields>
                <SetBasedProcessing></SetBasedProcessing>
                <FailBatchOnErrorForExecutionUnit>No</FailBatchOnErrorForExecutionUnit>
                <FailBatchOnErrorForLevel>No</FailBatchOnErrorForLevel>
                <FailBatchOnErrorForSequence>No</FailBatchOnErrorForSequence>
                <ParallelProcessing>
                    <Threshold></Threshold>
                    <TaskCount></TaskCount>
                </ParallelProcessing>
            </Entity>
        </EntitySetup>
    </SharedSetup>

    <TestGroup name='Set up Financials'>
        <TestCase Title='Import shared set up data package' ID='3933885' RepeatCount='1' TraceParser='off' TimeOut='20'>
            <DataFile RefID='SharedSetup' />
            <JobDefinition RefID='ImportJobDefinition_1' />
            <EntitySetup RefID='Generic' />
        </TestCase>

        <TestCase Title='Import financials for HQUS' ID='3933886' RepeatCount='1' TraceParser='off' TimeOut='20'>
            <DataFile RefID='FinancialsHQUS' />
            <JobDefinition RefID='ImportJobDefinition_1'>
                <LegalEntity>HQUS</LegalEntity>
            </JobDefinition>
            <EntitySetup RefID='Generic' />
        </TestCase>

        <TestCase Title='Import financials for PICH' ID='3933887' RepeatCount='1' TraceParser='off' TimeOut='20'>
            <DataFile RefID='FinancialsPICH' />
            <JobDefinition RefID='ImportJobDefinition_1'>
                <LegalEntity>PICH</LegalEntity>
            </JobDefinition>
            <EntitySetup RefID='Generic' />
        </TestCase>

        <TestCase Title='Import financials for PIFB' ID='3933888' RepeatCount='1' TraceParser='off' TimeOut='20'>
            <DataFile RefID='FinancialsPIFB' />
            <JobDefinition RefID='ImportJobDefinition_1'>
                <LegalEntity>PIFB</LegalEntity>
            </JobDefinition>
            <EntitySetup RefID='Generic' />
        </TestCase>
    </TestGroup>
</TestManifest>
```


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
