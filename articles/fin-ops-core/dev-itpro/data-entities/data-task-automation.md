---
# required metadata

title: Data task automation
description: This article explains how you can use data task automation to repeat many types of data tasks and validate the outcome of each task.
author: peakerbl
ms.date: 05/06/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
ms.reviewer: twheeloc
ms.search.region: Global
# ms.search.industry: 
ms.author: peakerbl
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: Platform update 16

---

# Data task automation

[!include[banner](../includes/banner.md)]


[!INCLUDE [PEAP](../../../includes/peap-3.md)]

Data task automation lets you easily repeat many types of data tasks and validate the outcome of each task. Data task automation is very useful for projects that are in the implementation phase. For example, you can automate the creation and configuration of data projects. You can also configure and trigger the execution of import/export operations, such as the setup of demo data and golden configuration data, and other tasks that are related to data migration. You can also create automated testing of data entities by using task outcome validation.

> [!IMPORTANT]
> Data task automation isn't currently supported for on-premises environments.
> The user who executes data task automation must be in the same tenant as the application environment and LCS project.

We recommend the following approach for data task automation.

1. Identify the data-related tasks that will benefit from automation.

    We recommend that implementation teams review their configuration management plan and data migration plan to identify potential data tasks for automation, and also to identify data entity test cases.

2. Define tasks.

    Tasks are defined in an XML manifest. You can keep your manifest under source control as part of configuration management in your application lifecycle management (ALM) strategy.

3. Put the data packages that are related to data task automation in the Shared asset library of Microsoft Dynamics Lifecycle Services (LCS). You can also use a specific LCS project as you require.

    Data task automation manager can consume packages from any sandbox and/or production environment that is related to the LCS project.

    > [!IMPORTANT]
    > - The user account that runs Data task automation manager must have access to LCS and to the LCS project that is referenced in the manifest for data packages.
    > - Although data task automation can be run in any environment in the cloud, we strongly recommend that you not run any import/export tasks that use integration application programming interfaces (APIs) in a production environment. Data task automation that involves integration APIs should be used only for automated testing.

4. Run the data tasks, and then review the outcomes.

    Data task automation manager provides the success or failure outcome for each task. It also provides insights into the reason why a task failed.

    > [!IMPORTANT]
    > Although data task automation can be run in any environments in the cloud, we recommend that you not run any import/export tasks that use integration APIs in a production environment. Data task automation that involves integration APIs should be used only for automated testing.

The following video is a 55-minute TechTalk that walks you through an early release of [Task automation framework](https://community.dynamics.com/365/b/techtalks/posts/task-automation-framework-for-data-management-march-3-2018).

## Task manifest
A task must be defined in an XML manifest. This section describes the manifest. For guidance about how to name and design the manifest, see the "Best practices for manifest design" section later in this article.

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
**\<DataFile\>** elements define the data packages and data files that the tasks in the manifest will use. The data files must be either in the LCS asset library of your LCS project or in the Shared asset library.

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
|                 | \<DataFile\> | \-                  | assetType    | The asset type in LCS asset library that stores the data file. This is the asset type name as shown in LCS asset library. |
|                 | \<DataFile\> | \-                  | lcsProjectId | The LCS project that has the data file in its asset library. If the project ID is specified as '' then, it indicates the Shared asset library. |

### Data project definition
The **\<JobDefinition\>** element defines the data project definition. There can be more than one job definition in a manifest.

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
| \<SharedSetup\>   | \<JobDefinition\>                | 1..n                | ID        | The job definition ID is used in the tasks to reference the definition to be used for the data project. |
| \<JobDefinition\> | \<Operation\>                    | 1..1                | \-        | The operation to be performed is specified by the following values: <br> - Import <br> - Export |
|                   | \<Truncate\>                     | 1..1                | \-        | This is a Boolean field with possible values of Yes or No. This is applicable only when operation is set to *Import*. |
|                   | \<Mode\>                         | 1..1                | \-        | The mode specifies the method using which the operation must be performed. The possible values are:<br>- Import async <br>- Export async <br>- Recurring batch: This uses the enqueue API. Dequeue API is not supported yet. Package API supports both export and import.|
|                   | \<ConfigurationOnly\>            | 0..1                | \-        | This is a Boolean field with possible values of Yes or No. This must be set to Yes if the task is only to configure the data project but not to perform the specified operation. |
|                   | \<BatchFrequencyInMinutes\>      | 1..1                | \-        | This specifies the frequency in which the batch must be scheduled. This is applicable only when mode is set to *recurring batch*. |
|                   | \<NumberOfTimesToRunBatch\>      | 1..1                | \-        | This is used to set a limit to how many times the scheduled batch should run. This is applicable only when mode is set to *recurring batch*. |
|                   | \<UploadFrequencyInSeconds\>     | 1..1                | \-        | This is used to control the rate at which a file is uploaded to the recurring batch job for import. This must be used only for automated testing of recurring integrations in non-production environments. This is applicable only when mode is set to *recurring batch* and operation is set to *Import*. |
|                   | \<TotalNumberOfTimesToUpload\>   | 1..1                |           | This controls the total number of times the file should be uploaded to the recurring batch. This must be used only for automated testing of recurring integrations in non-production environments. This is applicable only when mode is set to *recurring batch* and operation is set to *Import*. |
|                   | \<SupportedDataSoureType\>       | 1..1                |           | This must be used to specify if a file is being sent to the recurring batch or a package. This is only applicable when mode is set to 'recurring batch'. |
|                   | \<ProcessMessagesInOrder\>       | 1..1                |           | This is a Boolean field with possible values of Yes or No. This is applicable only when mode is set to *recurring batch* and operation is *Import*. |
|                   | \<PreventUploadWhenZeroRecords\> | 1..1                |           | This is a Boolean field with possible values of Yes or No. This is applicable only when mode is set to *recurring batch* and operation is *Export*. |
|                   | \<UseCompanyFromMessage\>        | 1..1                |           | This is a Boolean field which can be set to Yes or No. This is applicable only when mode is set to *recurring batch* and operation is *Import*. |
|                   | \<LegalEntity\>                  | 1..1                |           | This is used to specify the legal entity in which the import/export job must be executed. |
|                   | \<PackageAPIExecute\>            | 1..1                |           | Refer to package API documentation to understand this parameter. This is a Boolean field which takes 'true' or 'false'. |
|                   | \<PackageAPIOverwrite\>            | 1..1                |           | Refer to package API documentation to understand this parameter. This is a Boolean field which takes 'true' or 'false'. |
|                   | \<PackageAPIReexecute\>            | 1..1                |           | Refer to package API documentation to understand this parameter. This is a Boolean field which takes 'true' or 'false'. |
|                   | \<DefinitionGroupID\>            | 1..1                |           | Refer to package API documentation to understand this parameter. This is a string field. |
|                   | \<PackageName\>            | 1..1                |           | Refer to package API documentation to understand this parameter. This is a string field. |

### Entity setup
The **Entity setup** section defines the characteristics of an entity that a task in the manifest will use. There can be more than one definition, one for each entity that is used by the tasks in the manifest.

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
| \<SharedSetup\>        | \<EntitySetup\>                      | 1..n                | ID                | An identification that will be used by tasks to reference an entity definition to be used. |
| \<EntitySetup\>        | \<Entity\>                           | 1..1                | name              | The entity element is identified by the entity's name. However, to facilitate easy manifest definition, this element also supports \* as a wild card which will mean all entities being used in a task. This comes in very handy when using data packages with hundreds of entities in a task. |
| \<Entity\>             | \<SourceDataFormatName\>             | 1..1                | \-                | This is the file format to be used for the entity. |
|                        | \<ChangeTracking\>                   | 1..1                | \-                | This is a Boolean field with possible values of Yes or No. It enables or disables change tracking on the entire entity. |
|                        | \<PublishToBYOD\>                    | 1..1                | \-                | This is a Boolean field with possible values of Yes or No. |
|                        | \<DefaultRefreshType\>               | 1..1                | \-                | This sets the default refresh rate on the entity. The possible values are *Incremental push only* or *Full push*. |
|                        | \<ExcelWorkSheetName\>               | 1..1                | \-                | This is used to specify the worksheet to be used for the entity. |
|                        | \<SelectFields\>                     | 1..1                | \-                | This can be used to specify the fields to be included in the template for an export operation. |
|                        | \<SetBasedProcessing\>               | 1..1                | \-                | This is a Boolean field with possible values of Yes or No. It is used to enable or disable set based processing on an entity. |
|                        | \<FailBatchOnErrorForExecutionUnit\> | 1..1                | \-                | This is a Boolean field with possible values of Yes or No. It is used to enable or disable failure at execution unit level on an entity. |
|                        | \<FailBatchOnErrorForLevel\>         | 1..1                | \-                | This is a Boolean field with possible values of Yes or No. It is used to enable or disable failure at execution level on an entity. |
|                        | \<DisableEntity\>                    | 1..1                | \-                | This is a Boolean field with possible values of Yes or No. It is used to enable or disable an entity in a data project. |
|                        | \<SkipStaging\>                      | 1..1                | \-                | This is a Boolean field with possible values of Yes or No. It is used to skip staging table for an entity during exports. |
|                        | \<ParallelProcessing\>               | 1..1                | \-                | This is used to define the parallel processing set up for an entity. The task will delete these settings if already exits at the beginning of the task and it will delete the created settings at the end of its execution. |
| \<ParallelProcessing\> | \<Threshold\>                        | 1..1                | \-                | This specifies the threshold for the parallel processing rule. |
|                        | \<TaskCount\>                        | 1..1                | \-                | This is used to specify the number of parallel tasks to be used for parallel processing. |
| \<Entity\>             | \<MappingDetail\>                    | 0..n                | \-                | Allows to configure the *auto generate*, *auto default* and other settings on the mapping for an entity. |
|                        | \<MappingDetail\>                    | \-                  | StagingFieldName  | This attribute is used to identify the entity column for which the settings are to be specified. |
|                        | \<MappingDetail\>                    | \-                  | AutoGenerate      | This is a Boolean field with possible values of Yes or No for enabling/disabling auto generate option. |
|                        | \<MappingDetail\>                    | \-                  | AutoDefault       | This is a Boolean field with possible values of Yes or No for enabling/disabling auto default option. |
|                        | \<MappingDetail\>                    | \-                  | DefaultValue      | This is the default value to be used if auto defaulting is enabled. |
|                        | \<MappingDetail\>                    | \-                  | IgnoreBlankValues | This is a Boolean field with possible values of Yes or No for enabling/disabling this option. |
|                        | \<MappingDetail\>                    | \-                  | TextQualifier     | This is a Boolean field with possible values of Yes or No for enabling/disabling this option. |
|                        | \<MappingDetail\>                    | \-                  | UseEnumLabel      | This is a Boolean field with possible values of Yes or No for enabling/disabling this option. |

### Test groups
Test groups can be used to organize related tasks in a manifest. There can be more than one test group in a manifest.

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
|                  | \<TestGroup\>     | 1..1                | Name        | This is the name for the group to identify its functional reason. |
| \<TestGroup\>    | \<TestCase\>      | 1..n                | \-          | The task is defined in this element. The task can refer to the shared set up to inherit task parameters and task behavior. The task can also override parameters and behavior at its level thus making the management of the manifest simple. |
|                  | \<TestCase\>      | \-                  | Title       | This is the title for the task. |
|                  | \<TestCase\>      | \-                  | ID          | This is the ID for the task. This can be alphanumeric with a max character limit of 10. |
|                  | \<TestCase\>      | \-                  | RepeatCount | This is a placeholder for a future functionality. However, this must be specified with a value of *1*. |
|                  | \<TestCase\>      | \-                  | TraceParser | This is a placeholder for a future functionality. However, this must be specified with a value *off*. |
|                  | \<TestCase\>      | \-                  | Timeout     | This is the maximum duration a task will be monitored by the task automation manager. If the task is still active beyond the timeout specified, the manager will proceed to the next task in the manifest. |
| \<TestCase\>     | \<DataFile\>      | 1..n                | \-          | This element is used to define the file or data package to be used by the task. This can reference to an already declared file or a data package in the shared section of the manifest. A task can have more than one data file specified for recurring batch import scenarios only. For other scenarios, even if more than one files are specified, the first file is what will be used by the task. |
|                  | \<JobDefinition\> | 1..1                | \-          | This element is used to define the data project to be used by the task. This can reference to an already declared job definition in the shared section of the manifest. The task can override elements of job definition to a new value than what is defined in the shared set up. |
|                  | \<EntitySetup\>   | 1..1                | \-          | This element is used to define the entity set up for entities used by the task. This can reference to an already declared entity set up in the shared section of the manifest. The task can override elements of entity setup to a new value than what is defined in the shared set up. |

## Best practices for manifest design
You can define a manifest in many ways. Here are a few pointers that you should consider when you design a manifest.

### Granularity
We recommend that you determine the granularity of your manifest as a functional decision. Your team must decide whether it wants to manage many manifests or manage changes in a single manifest.

- Start with as many manifests as your team thinks you logically need. Later, when the team actually starts to run the manifests, it might find that it uses fewer manifests than it expected, and it might want to merge them. In this case, you can merge manifests.
- Consider separation of duties. For example, you might have one manifest for the setup of demo data and another manifest for the setup of the golden configuration for your environment. In this way, you can make sure that team members use only the manifests that they are supposed to use.
- Consider user access to LCS. For example, larger and globally distributed implementation teams might have multiple instances of the application or multiple LCS projects.

### Inheritance
The manifest schema supports inheritance of common elements that will apply to all tasks in the manifest. A task can override a common element to define a unique behavior. The purpose of the **Shared setup** section is to minimize repetition of configuration elements, so that elements are reused as much as possible. The goal is to keep the manifest concise and clean, to improve maintenance and readability.

### Source control
Manifests that must be used by all the members of an implementation team should be stored in source control in the Application Object Tree (AOT). This approach not only provides the benefits of source control, but also enables a process to distribute or make manifests available to all users in a consistent manner. This approach also enables configuration management for data projects that are related to data management, if manifests are used for configuration.

### Number of job definitions and entity definitions
For most of the use cases, one job definition in a manifest should be enough, because inheritance can be used to change the behavior at the task level. This principle also applies to entity definitions.

## Validations
Data task automation manager performs validations, based on the setup of a task. If a task fails, you can quickly determine the reason for the failure by viewing the validations after the task is completed. The level of information that Data task automation manager provides is optimized to facilitate initial discovery. For detailed investigation, you must look at the corresponding data project and its execution details.

The following data validations are currently supported:

- **Job status** – This validation checks whether the job was successful.
- **Batch status** – This validation checks whether the batch was successful.
- **Message status** – If the test is about integrations, the message status is validated.
- **Truncation** – If truncation is enabled, this validation checks whether truncation occurred.
- **Skip staging** – If **Skip staging** is enabled on a test, this validation checks whether staging was skipped.

## Example 1: Configuration management for data projects
The **\<ConfigurationOnly\>** element can be used to create configuration tasks for data projects. When ConfigurationOnly is set to Yes, the data projects are only created but not executed. This allows for managing data projects across environments in an automated manner.

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
The following manifest shows the setup of demo data for three legal entities when the demo data packages are stored in the Shared asset library. The difference in this example from the previous example is the actual execution of the data projects to set up the demo data. This is accomplished by not using the ConfigurationOnly option or setting it to No to use it for consistency of the manifest.

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
