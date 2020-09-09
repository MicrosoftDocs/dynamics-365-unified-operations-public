# Implement the Process Automation Framework

For an overview of process automation, see [Process automation](../fin-ops-core/dev-itpro/sysadmin/process-automation).

You should use the public APIs to implement process automation.

- Do not selecting from, inserting into, or directly reference the process automation tables.
- Do not extend the Process Automation Framework or integrate your code with the classes.
- Do not subscribe to table events such as insert/update/delete. We skip most of those events.
- If functionality is missing that you need please submit feature requests.

We anticipate that we will be adding features in the future and integrating too deeply with this framework could cause your integration to break.

Some of the examples shown are test examples and are not representative of shipping quality code. As always, it is expected that any processes built via the Process Framework will follow all the best practices and quality standards.

## Definitions

| Term | Definition                                                                             |
|------------------|--------------------------------------------------------------------------------- |
| Poller             | The poller is a system critical batch process which runs every minute that invokes various subsystems of the process automation framework. It consults with the schedule to see what processes are ready to run and then it invokes the execution side of the framework to ensure processes get executed. |
| Scheduled Process  | A process that is scheduled by users in the UI. Occurrences for these processes can be seen on a calendar view. |
| Background Process | A background process that runs frequently that doesn’t require user input and performs some background processing. Subledger transfer to GL is an example of a polled process. The term “Polled” is synonymous with the term “Background”.  |
| Type               | Throughout this documentation when we use the term type we are referring to ProcessScheduleType which is discussed in Type Registration section below.                                                                      |
| Series             | Every process that has a registered type must have a series. Series for scheduled processes are created in the UI by end users. Series for background processes are created via series registration. See the Series Registration section for details. |
| Date/Times         | All process automation framework dates are stored in UTC and displayed in the user preferred timezone. |

## Tasks

| Section                  | Required For Scheduled Process | Required For Background Process |
|------------------------------|---------------|-----------------------|
| Type Registration            | Yes           | Yes                   |
| Series Registration          | Not supported | Yes                   |
| Process Parameters           | No            | Not supported         |
| User Configurable Queries    | No            | Not supported         |
| Process Execution            | Yes           | Yes                   |
| Results and Message Logging  | Yes           | Yes                   |
| User Interface Customization | No            | See Below             |

Except for the sub sections series list page and Results and Messages, most of the User Interface Customization section is not supported for background processes.
