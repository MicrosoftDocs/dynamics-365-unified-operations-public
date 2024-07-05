---
# required metadata

title: Configure life event types
description: Microsoft Dynamics 365 Human Resources uses life event types to define events to update employee benefits enrollment.
author: twheeloc
ms.date: 07/02/2024
ms.topic: article
# optional metadata

ms.search.form: BenefitWorkspace, HcmBenefitSummaryPart, BenefitLifeEventTypes
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anisagrawal
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Configure life event types

Dynamics 365 Human Resources uses **Life event types** to define events where it is valid to update employee benefits enrollment, such as getting married or having a child. Each life event type ID may only be associated with one life event type. For example, if you create a **Life event ID** called **Address change** that is associated with the life event type **Employee address change**, you can’t create another ID labeled **Employee address change** and associate it with the life event type **Employee address change**. If a life event type isn't associated with a plan type, the life event type won't trigger a life event. For more information, see [Create plan types](hr-benefits-setup-plan-types.md).

## Create a life event type

1. In the **Benefits management** workspace, under **Setup**, select **Life event types**.
2. Select **New**.
3. Specify values for the following fields:

   | Field | Description |
   | --- | --- |
   | **Life event type ID** | The life event type unique identifier. |
   | **Description** | A description of the life event type. |
   | **Life event type** | A catalyst to updating an employee’s benefits enrollment. For a list of life events, see [Life events](hr-benefits-setup-payment-frequencies.md?life-events) below. |

4. Select **Save**.

## View attached plans

You can see a list of plans that are attached to the selected **Life event type**. Life events are attached to a plan type, and plan types are associated with a plan.

1. In the **Benefits management** workspace, under **Setup**, select **Life event types**.
2. Select **Actions**.
3. Select **Attached plans**.

## Life events

You can choose from the following life events when you create a life event type:

| Life event | Location | Trigger |
| --- | --- | --- |
| **Marital status change** | **Worker > Profile > Personal information > Marital status**| Change in marital status |
| **Employment status change** |**Worker > Employment > Employment history page** | For a worker with an existing employment detail, creating a new employment detail with a different employment status will trigger a life event.  Updating an existing employment detail with a different employment status will also trigger a life event.  |
| **Employee address change** |**Worker > Profile > Addresses**</li><li>**Worker > Personal information > Personal contacts > Address**</li></ul> | Change in address. Address must be **Primary** to trigger a life event. |
| **Dependent change** |<br><ul><li>**Worker > Profile > Personal information > Personal contacts**/li><li>**Employee self service**</li></ul> | Add a personal contact specifying them as a dependent and defining **Valid from**. Update a personal contact’s dependent **Valid to** information. The personal contact relationship must be child, spouse, domestic partner, or ex-spouse.  |
| **Birth or Adoption (dependent)** |<br><ul><li>**Worker > Profile > Personal information > Personal contacts**</li><li>**Employee self service > Edit personal details > Personal contacts**</li></ul>| **Birth date** or **Adoption date** are added or updated. The **Birth date** of the child is required. |
| **Loss of coverage (Spouse / domestic partner)** | Worker > Profile > Personal information > Personal contacts >  Dependent details > Loss of coverage | **Loss of coverage** selected for a personal contact, along with **Effective date** |
| Domestic partner employment change | **Worker > Profile > Personal information > Personal contacts > Dependent details > Employed** | Creating a personal contact and setting **Employed** to **Yes**. Updating a personal contact and changing **Employed**.  |
| **Leave of absence (Spouse/domestic partner)** | **Worker > Profile > Personal information > Personal contacts > Dependent details > Leave of absence** | Personal contact created and **Leave of absence effective date** is defined. Personal contact **Leave of absence** is updated. Personal contact **Leave of absence effective date** is updated.  |
| **Change in coverage (Position)** |<br><ul><li>**Worker > Position Assignment > Worker position assignments**</li><li>**Positions > Positions**</li></ul>| Change to the position in the worker position assignment records. Change of the worker assignment in the position. |
| **Change in coverage (salary)** |<br><ul><li>**Worker > Compensation > Fixed plan**</li><li>**Worker > Personal information > Benefits annual salary**</li></ul>| If **Benefits management > Human resources shared parameters > Benefits > Benefits annual salary** isn't enabled, updating **Worker > Compensation > Fixed plan** will create a life event. If **Benefits management > Human resources shared parameters > Benefits > Benefits annual salary** is enabled, updating **Worker > Personal Information > Benefits annual salary** will create a life event. |
| **Medicare (Employee / dependent)** | **Worker > Profile > Personal information > Personal contacts > Dependent details > Medicare effective date** | Adding or updating **Medicare effective** date for a personal contact creates this life event. |
| **Court ordered support** | **Worker > Profile > Personal information > Personal contacts > Dependent > Court ordered support** (QMSCO/QDRO) and effective dates | When creating a personal contact, a life event will be created if **Court ordered support** is **Yes**. Updating **Court ordered support** or **Court ordered expiration date** will also trigger a life event. |
| **Deceased** | **Worker > Profile > Personal information > Deceased date** | A **Deceased date** is entered or updated. |
| **Evidence of insurance** | **Worker > Worker > Versions > Employment history > Date manager > Benefit details** | **Evidence of insurability** is set to **Yes**. **Evidence of insurability verification date** is defined. |
| **Beneficiary** | **Worker > Profile > Personal information > Personal contacts** | A personal contact is added and the **Beneficiary** and **Effective date** fields are populated. The personal contact must be of type **Child**, **Spouse**, **DomesticPartner**, **Sibling**, **FamilyContact**, **OtherContact**, or **Parent**. |
| **Employee Medicare** | **Worker > Worker > Versions > Employment history > Date manager > Benefit details** | **Medicare eligible** is set to **Yes**. **Medicare eligibility date** is changed. |
| **Birthday** | **Benefits management > Life event change processing** | These life events are created from **Life event change processing**. The process analyzes the chosen period and legal entity and finds associated workers. It calculates their last birthday and creates a birthday life event if one hasn't already been created. |
| **Worker eligibility change (not US-specific)** |<br><ul><li>**Worker > Employment**</li><li>**Worker > Worker > Versions > Employment history**</li></ul>| Creates a life event when:<br><ul><li>Creating a new employment, and there's a previous employment, and the worker type changes.</li><li>Creating a new employment detail, and there's a previous employment detail, and the employment type or employment category changes.</li><li>Updating an employment record and a different worker type is defined.</li><li>Updating an employment detail record and a different employment type or category is specified.</li></ul> |
| **New eligibility override (not US-specific)** | **Human resources advanced > Benefits > Plans > Benefits > Eligibility rule override** | Using Life event processing<br>Creating a new benefit plan eligibility override for a worker triggers this life event.<br>BenefitEligibilityRuleOverride.ValidFrom. |
| **Eligibility rule override change (not US-specific)** | **Human resources advanced > Benefits > Plans > Benefits > Eligibility rule override** | Updating **Valid from** or **Valid to** on a benefit plan eligibility override triggers this life event. |
| **Eligibility rule override expiration (not US-specific)** | Benefits management > Life event change processing  | These life events are created from **Life event change processing**. The process analyzes the chosen period and legal entity and finds associated benefit plan eligibility overrides. It creates life events if the overrides have expired. |
| **New benefit plan (not US-specific)** | **Human resources advanced > Benefits > Plans > New** | Eligibility options are added to a current plan. A new plan with eligibility options attached is added.</br></br>HR personnel should run Life event eligibility processing in this instance. |
| **Eligibility rule change (not US-specific)** | **Benefits management > Eligibility rules** | Using Life event eligibility processing. Logged when **BenefitEligibilityRule** records have the following values changed: **UseEmplCategory**, **UseEmplStatus**, or **UseEmplType**. Only updates life event transactions that already exist for a changed rule or eligibility criteria. |


[!INCLUDE[footer-include](../includes/footer-banner.md)]
