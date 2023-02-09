---
# required metadata

title: Device management implementation guidance
description: This article is intended for people who implement functionality that is related to device management in a commerce environment. It gives implementation tips and guidance that you should consider as you plan your implementation.
author: jashanno
ms.date: 02/03/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: RetailTerminalTable, RetailDevice
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: jashanno
ms.search.validFrom: 2017-10-31
ms.dyn365.ops.version: Retail July 2017 update
---

# Device management implementation guidance

[!include [banner](includes/banner.md)]

This article is intended for people who implement functionality that is related to device management in a commerce environment. It gives implementation tips and guidance that you should consider as you plan your implementation.

## Overview

A *device* is an instrument on which a point of sale (POS) application can be installed, configured, and used to perform operations that are required in order to run or help run the business that owns that instrument. In other words, a device is a piece of technology that runs a POS application to help run a business. This business doesn't have to be exclusively a commerce operation. For example, a hospital has a gift shop, a warehouse manages inventory, and a law firm generates invoices. What is important is that the application that the device runs makes business operations simpler, more efficient, or just better managed and recorded. Regardless of the scenario that they are used in, devices are critical elements. As the number of devices that are used increases, it becomes more valuable to put processes in place to track and manage those devices. Together, these processes are known as *device management*.

The POS application that this article discusses is the Store Commerce app in Microsoft Dynamics 365 Commerce. The Store Commerce app lets users complete business operations quickly, efficiently, and simply. It also helps the organization manage the many devices that run the Store Commerce app across the business. Although this article discusses many aspects of Store Commerce app devices, the two critical aspects are the business-oriented *register* and the physical concept of a *device*.

The **Registers** page is the virtual tracking mechanism for the business-oriented details of an instance of the Store Commerce app. These details include the visual profile that is used, the automatic sign-out time, and the store that the register is a part of. All these details are stored in the virtual register. When the register is correctly set up and configured, it's linked to a virtual device.

The **Devices** page is the virtual tracking mechanism for the physical concept of a device. The business-oriented register is linked here to complete the configuration and prepare for installation. The virtual device stores details such as the validation status, when the POS application was activated, and the version that will be installed or the version that is currently installed.

As more registers are generated and then linked to the appropriate devices, both physical and virtual management become critically important. For example, a business has one physical device, a Microsoft Surface device that will run the Store Commerce app. The Surface must be configured for the business, because it might be on a domain or require additional software that is specific to that business. The Store Commerce app must also be installed and activated on the Surface device. Over time, the device might require servicing or replacement, or it might even be stolen. If the business doesn't have just one device, but dozens, hundreds, or even thousands, processes must be put in place to appropriately watch, manage, and verify the status of all the devices. These devices include both devices that are currently used and devices that aren't currently used.

Commerce already provides the basic requirements for device management. As you plan your implementation, you must make sure that you take all the appropriate considerations, to help minimize pain and maximize benefit.

## Implementation considerations

This section describes some things that you should consider as you plan to implement features that are related to device management in your retail store and distribution locations.

### Generate the physical topology

Planning is the most critical requirement for successful implementation of an enterprise resource planning (ERP) solution. One of the main deliverables of this planning should be a *physical topology*. The physical topology is a visualization of many details about a company, from the lowest POS device to the highest network connections at the headquarters. At a minimum, the following deliverables should be completed:

- **Store templates** – A store template consists of one or more diagrams that show the layout of a physical location, such as a brick-and-mortar store. In the long term, these diagrams help you easily implement future locations and quickly assess how you can fix or improve any issues that are found. The store template should include the following details:

    - **Location** – The physical layout of a location. Details should include the position of all devices that exist in the location.
    - **Network** – The internal layout of the network infrastructure and details about internet connectivity (for example, bandwidth up and down, thread count, and latency to the headquarters or other important internet locations).
    - **Device** – The details of all devices that exist in a location. These details include the device specifications or some type of associable tag that lets you quickly find the details about a device.
    - **Peripheral** – A list of all peripherals that are attached to a device, a count of peripherals, and physical location of all peripherals. Often, there should also be an associable tag that lets you quickly find details.

- **Naming methodology** – For any implementation, it's important that you maintain naming conventions across all devices. Generate the rules that govern the naming conventions, and follow those rules.

    > [!NOTE]
    > When you generate the naming methodology, we recommend that the name of a register be the same as, or very similar to, the name of the device. The name of the device, in turn, should be the same as, or very similar to, the friendly name of the physical computer that the register works on.

- **Procedures plan** – The more a business grows, the more important it becomes that procedures remain in place to help maintain enough order so that the business can run efficiently. You should consider your plan a living document that you must be maintained and appended often. This plan should explain how to perform almost every action that will be repeated in the stores that make up a company.
- **Servicing plan** – As business continues, servicing becomes more critical. You must decide when you will replace devices, when you will update devices and peripherals (both the applications and the operating systems), and how you will perform these tasks. The answers will vary from business to business, but these tasks should be planned for.
- **Disaster plan** – If something can go wrong, it should be planned for. As planning proceeds, make a note of risks and potential mitigations. Generate a plan that explains how to fix a problematic situation.

After planning is completed and all potential details are known, you will eventually have a list of stores and, for each store, a list of associated registers and devices. The next question that you must answer is how you will deploy all the various devices that are listed.

### Distributed deployment

As the number of devices increases into the hundreds or even thousands, manual configuration, installation, and activation of the POS application quickly becomes impractical. There are several concepts that you can use to alleviate this issue and to manage or help manage devices on a large scale:

- **Devices page** – When you use MPOS, the page that shows the details of a device includes information about the POS client that should be used on the device. Under the **Register package** subheading, there are four fields. The first three fields (**Package name**, **Package description**, and **Version number**) provide information about the version of the MPOS package that should be installed on the device either now or later. The fourth field shows the version of MPOS that is currently installed. Therefore, you can easily find this information for any device.
- **Channel deployment workspace** – This workspace lets you quickly view a large, filterable set of stores, registers, devices, and more. This workspace also provides options for mass deployment. (For more information, see [Customer orders in Modern POS (MPOS)](dev-itpro/retail-mass-deployment.md)). This workspace gives you quick access to important pages, can help decrease validation times when you do status checks are a deployment, and helps you efficiently manage device statuses.
- **Mass deployment** – Dynamics 365 customers who use MPOS and other client-side components can silently perform various actions to help with installation, configuration, and servicing. By running basic commands at a command prompt, you might be able to deploy and service (that is, update) commerce components. This basic method of skipping the installer's manual user interface can reduce the time that is required for installation and servicing. The log files remain the same and can be viewed for installation details.
- **Scripting** – Based on the mass deployment functionality, scripts can be generated and set up to run automatically to install or update commerce components such as the Store Commerce app. These basic scripts can be entered as a scheduled task on a device. The task then runs at a predetermined time and return the logs and results to a predetermined location, where they can be viewed as time permits.
- **Systems management solution** – A systems management solution can help increase the amount of known data about the devices that are used. It can also decrease the time that is required in order to get that data. Examples of systems management solutions include Microsoft System Center and Microsoft InTune. By using a systems management solution together with mass deployment and scripting, you can configure and install components much more quickly. In addition, you can more efficiently validate status after deployment or servicing. Microsoft has published a document specifically about device management via System Center Configuration Manager, [Choose a device management solution for System Center Configuration Manager](/sccm/core/plan-design/choose-a-device-management-solution).

<!--For more information that will help you better understand distributed deployment, see [Configure, install, and activate the Store Commerce app (MPOS)](retail-modern-pos-device-activation.md) and [Customer orders in the Store Commerce app](dev-itpro/retail-mass-deployment.md).-->

### Servicing devices

Although deployment is an important article that has many nuances, the ongoing nature of business requires that you consider servicing early, and that you plan for it. In that way, you can maximize efficiency and speed of completion every time that servicing is required. Servicing becomes even more important when you understand that, not only do applications have to be serviced, but the operating system and peripherals might also require updates. As we mentioned earlier, this process can be even more difficult when it's time to replace devices. In general, you should consider all the following factors:

- **Devices** – The process of servicing a device involves more than just determining whether servicing has been completed. Instead, many aspects of the device must be reviewed and updated, either individually or as part of a group of devices at the same time:

    - The information on the **Devices** page, or in the **Channel deployment** workspace, in Dynamics 365 headquarters can help you validate the current status and version of MPOS or other self-service components, such as hardware station or Commerce Scale Unit.
    - It's very useful if you know the version of Microsoft Windows. In scenarios where a systems management solution isn't used, you can use the **winver** command in a Command Prompt window to quickly learn the specific version of Windows that is currently installed. By comparing the version number against the [Windows version list](https://technet.microsoft.com/windows/release-info.aspx), you can easily learn what updates a computer is missing at a service pack level.
    - Internal and peripheral drivers must be checked for version updates too. You should include and monitor this information in the device and peripheral lists that you created as part of the store templates during the planning phase, as explained earlier in this article.
    - Always track when a computer goes out of service (warranty or service plan). In this way, you can quickly determine when a computer should be replaced instead of being sent out for servicing (warranty or service plan).

- **Peripherals** – The peripherals that are attached to a device or to the network must be monitored. As part of this process, you must also monitor the network devices themselves. (Routers, switches, firewalls, and all other network devices also have firmware that requires occasional updates to maintain security and compatibility, and to comply with servicing terms.) If appropriate planning has occurred, the process of watching for service dates and correctly updating peripherals should become a simplified task within the larger servicing flow for device management.
- **Replacements** – Eventually, devices and peripherals either fail or reach a point where servicing just isn't enough. In general, we highly recommended that you have a replacement system that is ready before this situation arises. Based on the procedures and servicing plans that you created during the planning phase, this process can be very fast and efficient. For a device that runs the Store Commerce app, you can generically prepare the replacement device and install the Store Commerce app on it long before you either send the unit on-site or store it on-site, depending on the approach that works best for the business. At the time of replacement, the Store Commerce app can "reactivate" a device that is already active. Therefore, you can handle special cases where a system stops responding and must be replaced, because it can't be repaired. However, you must make sure that the replacement is correctly up to date, and that it has recently been serviced.
- **Systems management solution** – A systems management solution can dramatically improve how servicing works and when servicing is done. These solutions include telemetry tools that monitor all the systems that are being used. Because of these telemetry tools and the device information data that is constantly stored and available, servicing should become proactive instead of reactive. In this best-case scenario, appropriate plans exist for procedures and servicing, and the alerts and the known data about a system can let you know about impending servicing or an impending replacement before an issue occurs and becomes a critical task.

### Worst-case scenarios

Unfortunately, things sometimes go wrong. It's important that you consider worst-case scenarios and put mitigation plans in place (per the disaster plan that you created during the planning phase) to help resolve issues that arise. In Commerce, the **Devices** page can at least help with device management.


- **Lost/stolen device** – When a device is lost or stolen, it becomes a critical issue, because private data can end up in the hands of a malicious person. The first step is to deactivate any lost or stolen device on the **Devices** page in Headquarters, to immediately prevent sign-on to that device. If you created a disaster plan, follow the rest of the guidelines to complete all tasks that are required in order to tag the device as gone, file all important documents (which might include documents for insurance and the police), and work to replace the device and continue business. If appropriate procedures have been created, a replacement device should already be ready.
- **Infrastructure issues** – Network equipment might go bad, the store layout might have to be altered, or, as a part of a store update, the devices might be changed from desktops to tablets. When issues arise that can affect the management of devices, it can be difficult to react appropriately and fix the issues. In the best-case scenario, you've already discussed these issues and listed then in the procedures, servicing, and disaster plans. At a minimum, before something is done that affects the layout of a business location, you should update the store layout documents to reflect the new layout, so that fewer surprises are met. As we mentioned earlier, for issues that affect MPOS specifically, the ability to reactivate should help mitigate downtime and should help with change management. If you're concerned about outages of network equipment, or if outages occur, the Store Commerce app client can support offline databases. This functionality can help mitigate the impact that outages have on business.
- **Disaster** – When a disaster occurs, everything is affected. If the disaster is environmental, the employees should always be the highest priority. However, eventually, you must handle the management of the internal systems, and those systems must be repaired. Unfortunately, no simple advice or specific considerations can be listed. Instead, you should plan early in a more general way. What sorts of disasters could affect the business? Utilities such as water and power can have devastating effects on equipment. How can you mitigate the effects on employees, locations, and equipment in various disasters? Keep in mind concepts such as the data that is stored in the location, and when and how it's backed up and secured.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
