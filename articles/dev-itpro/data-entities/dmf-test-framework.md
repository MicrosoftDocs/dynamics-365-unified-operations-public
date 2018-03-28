---
# required metadata

title: Data task automation
description: Data task automation in Dynamics 365 for Finance and Operations lets you easily repeat many types of data tasks, and validate the outcome of each task. 
author: Sunil-Garg
manager: AnnBe
ms.date: 03/28/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
ms.reviewer: margoc
ms.search.scope: Operations
ms.search.region: Global
# ms.search.industry: 
ms.author: sunilg
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: Platform update 14

---

# Data task automation

Data task automation in Microsoft Dynamics 365 for Finance and Operations lets you easily repeat many types of data tasks, and validate the outcome of each task. Data task automation is very useful for projects in the implementation phase. For example, you can automate data project creation and data project configuration. You can also configure and trigger the execution of import/export operations, such as setting up demo data, golden configuration data, and performing other data migration related tasks. You can also use data task automation to create automated testing of data entities, using task outcome validation. 

> [!IMPORTANT]
> Data task automation is currently not supported for on-premises environments.

We recommend the following approach to data task automation:

1.	Identify the data related tasks that will benefit from automation. 

    We recommend that implementation teams review their configuration management and data migration plans to identify potential data tasks for automation, and data entity test cases. 

2.	Define tasks.

    Tasks are defined in an XML manifest. You can keep your manifest under source control as part of configuration management in your application lifecycle management (ALM) strategy.

3.	Put the data packages related to the automation manager in the asset library of the appropriate LCS project. 

    The Data task automation manager can consume packages from any environment (sandbox and/or production) related to the LCS project.

    > [!IMPORTANT]
    > Although data task automation can be run on any environment in the cloud, we strongly recommend that you not run any import/export tasks that use integration API’s in a production environment. Data task automation with integration API’s should be used for automated testing only.

4.	Run the data tasks, and then review the outcomes. 

    Data task automation manager provides success or failure outcome for each task. It also provides insights into why a task failed. The level of information provided in the task automation manager is optimized to facilitate initial discovery. Detailed investigation must be done using the data project and execution details in the Data management workspace.
    
    > [!NOTE]
    > Although the task automation can be run on any environments in the cloud, it is not recommended to run any import/export tasks using integration API’s in a production environment. The intent for using integration API’s in task automation should only be for automated testing purposes.


## Task manifest
Once the task has been identified, it must be defined in an XML manifest. This section describes the manifest. Refer to the best practice section for guidance on how to name and design the manifest.

## Manifest root
The <TestManifest>  is the root of the manifest. All the elements are children of this element.

![Manifest](./media/Manifest.png)

## Shared set up
The shared set up section provides for defining the generic task parameters and task behavior for all tasks in the manifest. This enables maintainability of the manifest.

![Shared set up](./media/SharedData.png)

## Data files
The <DataFile> element allows to define the data packages and/or data files that must be used by the tasks in the manifest. The data files must be in the LCS asset library of an LCS project or it can be in the shared asset library.
Note: The user account running the task automation manager in Dynamics 365 for Operations and Finance must have access to LCS and the LCS project that is referenced in the manifest for data packages.

![Data files](./media/SharedData2.png)

## Data project definition
The data project definition is defined using the <JobDefinition> element. There can be more than one job definitions in a manifest.

![JobDef](./media/JobDef.png)

## Entity set up:
The entity set up provides for defining the characteristics of an entity that is being used by a task. There can be more than one such definition one for each entity being used by tasks in the manifest.

![Entity set up](./media/EntitySetup.png)

![Entity set up](./media/EntitySetup2.png)

## Test groups:
Groups can be used to organize related tasks together in a manifest. There can be more than one group in a manifest.

![Groups](./media/Groups.png)

## Best practice for manifest design
There are different ways in which a manifest can be defined. Below are a few pointers to consider when designing the manifest.

-   **Granularity** – the granularity of the manifest must be a functional
    decision more than anything else. There is going be a fine balance between
    the number of manifests an implementation team must manage versus showing
    discipline and being judicious to manage all tasks in a single manifest. One
    rule of thumb teams can use is to find out if they are constantly having an
    urge to merge tasks from multiple manifests as they start using them. This
    would indicate that the manifests are too granular and are functionally not
    composed as needed. The other aspect to consider would we separation of
    duties on who should perform what tasks. For example, there could be a one
    manifest to set up the demo data and a different manifest to set up the
    golden configuration on environments. This way, team members can be guided
    to only use manifests which they are supposed to use. A third aspect would
    be the implementation team’s access to LCS as the tasks would expect the
    data packages to be in LCS. This could become a point to consider for larger
    and globally distributed implementation teams/end user base that either has
    multiple instances of Dynamics 365 for Finance and Operations or have
    multiple LCS projects.

-   **Inheritance** – the manifest schema supports inheritance of common
    elements that are going to be applicable to all tasks in the manifest. The
    task can override an element to create a unique behavior for itself. This
    helps to keep the manifest concise and clean which improves readability and
    maintenance. Emphasis must be given to minimize repeating of configuration
    elements and instead re-use as much as it is possible.

-   **Source control** – manifests that must be used by all the members of an
implementation team should be source controlled in the application object tree
(AOT). This not only provides for the benefits of source control but also
enables a process to distribute or make the manifest(s) available to all users
in a consistent manner. This also enables configuration management for data
management related data projects if manifests are being used to configure.

## Validations
The task automation manager performs validations based on the set up of a task. The validations can be viewed after the task has completed to know the reasons of a failure in case the task had failed.

![Validations](./media/Validations.png)

## Configuration management for data projects
The ‘ConfigurationOnly’ element can be used to create configuration tasks for data projects and recurring schedules. Below is a sample for such a task. The fist one is an example to configure a data project without any recurring schedule. The second one is an example where a recurring schedule must also be configured. The difference is the value provided to the <Operation> element.
The manifest for the configuration tasks can be source controlled to enable ALM on configuration management of data projects

![Config](./media/Config.png)

![Config](./media/Config2.png)

## Automating demo data set up for environments
Manifests can be created with tasks to import demo data packages directly from LCS. You can schedule all the tasks to be executed thereby not having to monitor individual package import for completion. The <LegalEntity> element comes in very handy in this scenario because, the data project import happens in the specified legal entity thereby eliminating for the user to switch companies to import a data package. Below is an example task for demo data import where the demo data packages are in the shared asset library.

![Demo data](./media/DemoData.png)

## Automating data migration tasks
A similar approach to demo data tasks can be also taken to perform data imports of data packages in a data migration process. Typically, once the environment for data migration has been deployed, the implementation team proceeds with configuring the environment with the base configuration (also called as the golden configuration data packages) data packages. After the base configuration is complete, the migrated data is imported via data management. These import tasks can be configured as tasks in a manifest and can be executed using the task automation manager to simplify and streamline this part of the data migration process.

## Data entity test automation
The task automation concepts can be also used to perform automated testing of data entities including integration scenarios. The ability to configure a data project and entities using the manifest provides the flexibility to test various combinations of scenarios for data entities.

The automation manager has inbuilt validations to aid with confirmation of why a task failed or passed. The data validations currently supported are the following.

-   Job status – checks if the status of the job is successful or not

-   Batch status – checks if the status of the batch was successful or not

-   Message status – if the test is about integrations then, the message status
    is also validated

-   Truncation – if truncation was enabled, then validation is done to check if
    truncation happened

-   Skip staging – if skip staging was enabled on a test then, validation is done to
check if staging was skipped

If a task has failed, looking at the validations is a quick way to know why the task failed. The corresponding data project and its execution details must be looed into for detailed investigation.
