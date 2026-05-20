---
# required metadata

title: Configure future life events
description: This article describes how to schedule future life events in Dynamics 365 Human Resources.
author: twheeloc
ms.date: 05/14/2026
ms.topic: how-to
# optional metadata

ms.search.form: BenefitFutureLifeEvents, BenefitWorkspace, HcmBenefitSummaryPart
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Configure future life events

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]
[!include [banner](../includes/preview-banner.md)]

You can schedule future life events in Dynamics 365 Human Resources.

1. In the **Benefits management** workspace, under **Setup**, select **Future life events**.

1. Select **New**.

1. Specify values for the following fields:

   | Field | Description |
   | --- | --- |
   | Life event date | The system processes all events during the enrollment period that occur up until this date. |
   | Life event logged | Date and time when the life event is logged. |
   | Log type | Shows whether the action is one of the following:</br></br>- **Update** – a change to an existing record that's tracking life events</br></br>- **Insert** – the creation of a new life event record |
   | Life event type ID | The life event type unique identifier. |
   | Life event type | A catalyst to updating an employee’s benefits enrollment. For more information, see the Life event triggers section. |
   | Status | Whether the life event is processed or not. |
   | Line | The line number of the future life event. |

1. Select **Save**. 

You can delete future life events. If you delete a processed future life event, you also delete the future record. 

[!INCLUDE[footer-include](../includes/footer-banner.md)]
