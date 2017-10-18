---
# required metadata

title: Device management implementation guidance
description: This topic is for those implementing device management-related functionality in a retail environment, and provides implementation tips and guidance to consider as you plan for your implementation.
author: jashanno
manager: AnnBe
ms.date: 10/16/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: 
ms.search.validFrom: 2017-10-31
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update
---

# Device management implementation guidance
This topic is for those implementing device management-related functionality in a retail environment, and provides implementation tips and guidance to consider as you plan for your implementation.

## Overview
A device is an instrument on which a point of sale application can be installed, configured, and utilized to perform necessary operations to run (or at least assist) the business that owns the instrument.  This is an eloquent way of stating that a device is a piece of technology that runs a point of sale application to help run a business.  This business does not need to be specifically a retail operation.  For example, a hospital has a gift shop, a warehouse manages inventory, and a law firm generates an invoice.  What is critical is that the application makes business operations simpler, more efficient, or just better managed and recorded.  No matter what the scenario in which it is used, devices are critical aspects.  Eventually, as the count of devices being used continuously increases, it becomes more and more valuable to put processes in place to track and manage these devices.  This is called “device management”.

In the Dynamics 365 for Finance and Operations or Dynamics 365 for Retail solution, the point of sale application to be discussed here will be Retail Modern Point of Sale (MPOS).  MPOS allows users to complete business operations quickly, efficiently, and simply while assisting the headquarters with the management of the many devices running MPOS across the business.  While there are many pieces surrounding this MPOS register that will be discussed, the two critical aspects of an MPOS device are the business oriented “register” and the physical oriented “device”.

The form titled **Registers** is the virtual tracking mechanism for the business oriented details of an instance of the Modern Point of Sale application.  The visual profile to use, the auto logoff time, or the store that the register is a part of are all details stored within the virtual register.  When the register is set up and configured properly, it is then linked to a virtually created device.

The form titled **Devices** is the virtual tracking mechanism for the physical concept of a device.  The business oriented register is linked here to complete the configuration and prepare for installation.  Details such as the validation status, when the point of sale application was activated, and the version to be installed or is currently installed are all stored within the virtual device.

As more and more registers are generated and then linked to the appropriate devices, the management (both physically and virtually) becomes critically important.  Look at a real device, such as a Microsoft Surface that will run MPOS.  The Surface needs to be configured for the business as it may be on a domain or require additional software specific to that business.  The Surface must have Modern POS installed and activated.  Over time, the device may need servicing, replacement, or could even be stolen.  When multiplied by dozens, hundreds, or even thousands of devices, processes must be put in place to properly watch, manage, and verify the status of all the devices both in use and not in use. 

In the Dynamics 365 for Finance and Operations or Dynamics 365 for Retail solution, the simplest necessities to begin managing devices are already provided.  Next, it is important to make certain that the implementation being planned takes all proper considerations to minimize pain and maximize benefit.

## Implementation considerations
Below are some things to consider as you plan your implementation of inventory management related features at your retail store and distribution locations.

If the discussion is still occurring whether Retail Modern POS or Retail Cloud POS would be better for a specific business, review the implementation considerations document Modern POS and Cloud POS **ADD LINK HERE**.

If the discussion is still occurring whether to utilize Retail Store Scale Unit, review the implementation considerations document Retail Store Scale Unit **ADD LINK HERE**.

### Generate the physical topology
Planning is the single most critical requirement to successfully implement an ERP solution.  One of the key deliverables of this planning should be a physical topology.  This physical topology visualizes many of the informational details of how a company looks from the lowest point of sale device to the highest headquarters network connections.  The minimal set of deliverables to complete should include the following:

-	**Store templates** – A store template is one or more diagrams that show how a physical location, such as a retail brick and mortar store, is laid out.  These diagrams serve long-term as a means of easily implementing future locations and quickly assessing how to fix or improve issues that are found.  The store template should include the following details:

    -	**Location** – The physical layout of a location, detailing where all devices that exist in the location are placed.
  
    -	**Network** – The network infrastructure layout internally and details of internet connectivity (bandwidth up and down, thread count, latency to headquarters or other important internet locations, etc.).
  
    *	**Device** – The details of all devices that exist in a location, including the specifications of the devices or some form of associable tag where details can quickly be found.
  
    *	**Peripheral** – List of all peripherals that attaches to a device, count of peripherals, and physical location of all peripherals, often with associable tag where details can quickly be found.
  
*	**Naming methodology** – It is important as a function of implementing to maintain common naming conventions across all devices.  Generate the rules that govern the naming convention used and stick to it.

     > [!Note]
     > When generating this naming methodology, it is recommended that the registers are named the same (or very similar) to the device which should be named the same (or very similar) to the physical computer name (Friendly name) on which the register functions.
     
*	**Procedures plan** – The larger a business grows, the more critical it becomes to keep procedures in place that maintain enough order to efficiently run the business.  This, especially, is a living document that must be maintained and appended often.  This plan should showcase how to perform almost every action that will be repeated within the stores that make up a company.

*	**Servicing plan** – As business continues, servicing becomes more and more critical.  When to replace devices, when to update devices and peripherals (both the applications and the operating systems), and how to perform these needed operations.  This will change from business to business, but most certainly should be planned for.

*	**Disaster plan** – If something can go wrong, it should be planned for.  As planning goes along, note risks and potential mitigations.  Generate a plan that explains how to fix a problematic situation.

After planning is finished and all potential details are known, the eventual result in the implementation will be a list of stores that all have lists themselves of associated registers and devices.  With the numerous devices listed, the next question to answer is how to deploy all of them.

### Distributed deployment
As the device count soars into the hundreds or even thousands of devices, the manual configuration, installation, and activation of the POS application quickly becomes impractical to continue to complete manually.  There are several concepts that can be utilized to alleviate, assist, or even manage devices at a large scale:

*	**Devices form** – On the form showcasing the details of a device, using Retail Modern POS, there are two sets of fields that assist in knowing information regarding the POS client to be used on the device.  Under the **Register package** sub-heading are four fields.  The first three fields (**Package name**, **Package description**, and **Version number**) showcase the version of the Retail Modern POS package that should be installed (now or in the future) on the device.  The fourth field states the currently installed MPOS version, allowing for easy viewing for any device.

*	**Channel deployment workspace** – This workspace allows for quickly viewing a large, filterable set of stores, registers, devices, and more.  This workspace is also where the mass deployment options exist (See the mass deployment document shown at the start of this sub-heading for more information).  Frequently referencing this workspace can speed up access to important forms, decrease validation times for post-deployment status checks, and efficiently assist in managing device statuses.

*	Mass deployment – Dynamics 365 customers using Retail Modern POS (and other client-side components) can silently perform a variety of actions to assist in installation, configuration, and servicing.  Using basic command-line driven commands, retail components could be potentially deployed and serviced (updated to newer versions).  This basic method of skipping the manual user interface of the installer can speed up installation and servicing times.  The log files remain the same and can be viewed for installation details.  For more information on how to utilize this, review the document shown above in this sub-heading.

*	Scripting – Based on the mass deployment functionality, scripts could be generated and setup to be run automatically to install or update retail components such as Retail Modern POS.  These basic scripts could be entered as a scheduled task on a device, which will then run at a pre-determined time, and return the logs and results to a pre-determined location for viewing as time permits.

*	Systems management solution – Whether the solution be Microsoft System Center, InTune, or something else, a systems management solution dramatically increases the known data of the devices being used while decreasing the time it takes to get that information.  When used in combination with Mass deployment and scripting, configuration and installation of retail components becomes much quicker with more efficient means of validating status post deployment or post servicing.  Microsoft has published a document specifically on device management with System Center Configuration Manager, which can be reviewed in the document [Choose a device management solution for System Center Configuration Manager](https://docs.microsoft.com/en-us/sccm/core/plan-design/choose-a-device-management-solution).

To better understand distributed deployment, it would also be helpful to read [Retail Modern POS configuration and installation](/retail-modern-pos-device-activation.md) and [Mass Deployment](/dev-itpro/retail-mass-deployment.md).

### Servicing devices
While deployment is an important topic with many potential nuances, the ongoing nature of business requires servicing to be considered early and planned for to maximize efficiency and speed of completion each time it is required. Servicing becomes twice as important when it is understood that not only must the applications be serviced, but the operating system and peripherals may also require updates.  As mentioned briefly previously, this can be made more difficult when it comes time to replace devices.  In general, the following should all be considered:

*	Devices – Servicing a device is not as simple as yes or no regarding completion.  Instead, many facets of the device must be reviewed and updated either individually or as part of a group of devices at the same time:

     *	Utilizing the information showcased in Dynamics 365 headquarters on the Devices page or the Channel deployment workspace can assist in validations what the current status and version of components such as MPOS (Or other Self-service components such as hardware station or Retail Store Scale Unit).
  
     *	Knowing the Windows version is exceptionally useful.  In scenarios where a systems management solution is not employed, the Command Prompt command “winver” can quickly bring up a window showcasing the specific version of windows currently installed.  Compared against the [Windows version list](https://technet.microsoft.com/en-us/windows/release-info.aspx?f=255&MSPPError=-2147217396), this can easily explain what updates a computer is still missing (at a service pack level).

      *	Internal and peripheral drivers must be checked for version updates as well.  This would be an important aspect to list and monitor in the device and peripheral lists created as part of the store templates during the planning phase (explained earlier in this document).
  
     *	Always track when the computer goes out of service (warranty or service plan).  This allows for quickly noting when a computer will be replaced as opposed to just sent out for servicing (warranty or service plan).
  
*	Peripherals – The peripherals attached to a device or the network must also be monitored.  This includes the network devices themselves (routers, switches, firewalls, and all the rest also have firmware that requires updates from time to time to maintain security, compatibility, and stay within servicing terms).  Assuming proper planning has occurred, then watching for service dates and properly updating should become a simplified task as part of the greater device management servicing flow.

*	Replacements – Eventually devices and peripherals will fail or get to a point that servicing is simply not enough.  This will be discussed somewhat in the next sub-heading, but generally in these times, it is highly recommended to have a system already ready for replacement well before this eventuality occurs.  Based on the procedures and servicing plans generated initially, this process can be extremely fast and efficient.  When specifically replacing a device running MPOS, the replacement device can be generically prepared and MPOS installed long prior to sending the unit on-site (Or store it on-site ahead of time, dependent on what is best for the business).  At the time of replacement, MPOS has the capabilities already to “Re-activate” a currently active device.  This allows for these special cases when a system crashes and cannot be repaired but will instead be replaced.  An important note, though, is to make certain that the replacement is properly up to date and has been serviced recently enough to maintain the same versions of everything previously mentioned in this sub-heading prior to using it in the business.

*	Systems management solution – Using a solution can dramatically improve how servicing functions and when to perform servicing.  Between the telemetry tools provided that monitor all the systems in use and the device information data that is constantly stored and available, servicing should no longer be reactive but instead become proactive.  This is the best-case scenario, where proper plans exist for procedures and servicing, and the alerts and data known about a system can generate knowledge of an impending servicing or replacement before it ever happens and becomes a critical task.

### Worst case scenarios
It would be wonderful to believe that nothing ever goes wrong, but sadly, all to often it does.  It is important that the worst-case scenarios are accounted for and mitigation plans are in place (per the disaster plan generated already) to solve the problems that arise.  In Dynamics 365 for Finance and Operations and Dynamics 365 for Retail, the Devices form can, at least, assist regarding device management.

*	Lost / Stolen device – When a device is lost or stolen, it becomes a critical issue as private data can potentially be in the hands of a malicious person.  First, be certain to “Deactivate” the device(s) in question on the Devices form in headquarters.  This will immediately disallow anyone attempting to login on that device to lose all access.  Assuming a disaster plan was created, follow the rest of the guidelines to perform all necessary tasks related to tagging the device as gone, filing all important documents (including possibly documents to insurance and police), and continue with the work to replace the device and continue business.  If proper procedures have been generated (as discussed previously), then there should already be a replacement device ready to be used.

*	Infrastructure issues – Possibly network equipment has gone bad, the store layout must be altered, or as a part of a store update the devices have dramatically been altered from desktops to tablets.  When things occur that can influence the management of devices, it can be difficult to properly react and fix the issues at hand.  In the best-case scenario, these ideas will have already been discussed and listed in the procedures, servicing, and disaster plans.  At a minimum, prior to something that influences the layout of a business location, the store layout documents should be updated to reflect the new layout so that fewer surprises can occur.  As mentioned previously, when it comes to specifically MPOS being affected, the ability to reactivate should assist in mitigation of downtime and change management.  If network equipment outage is a concern or does come up, the current abilities to have offline databases on the MPOS client can assist in mitigating the impact to business.

*	Disaster – When a disaster occurs, everything suffers.  If the disaster is environmental, the utmost importance is always the employees first.  This stated, eventually the management of the internal systems becomes a topic that must be handled and repaired.  There is no simple advice or considerations that can be listed explicitly.  Instead, plan early in a more generical way.  What sorts of disasters could affect the business?  Utilities such as water and power can have devastating effects on equipment.  How can the employees, locations, equipment be mitigated in these various potential disasters?  Keep in mind concepts such as the data being stored in the location (and when and how it is being backed up and secured).
