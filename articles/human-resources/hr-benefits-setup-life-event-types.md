---
# required metadata

title: Configure life event types
description: Microsoft Dynamics 365 Human Resources uses life event types to define events where it is valid to update employee benefits enrollment.
author: andreabichsel
manager: AnnBe
ms.date: 02/03/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-human-resources
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Configure life event types

Microsoft Dynamics 365 Human Resources uses life event types to define events where it is valid to update employee benefits enrollment. For example, getting married or having a child. Each life event type ID may only be associated with one life event type. For example, if you create a life event ID called Address change that is associated with the life event type Employee address change, you can’t create another ID labeled Employee address change and associate it with the life event type Employee address change. 

After you create life event types, you need to associate them with plan types. For more information, see [Create plan types](hr-benefits-setup-plan-types.md).

   > [!NOTE]
   > When you create a life event, you need to associate it with a plan type. For more information, see [Create plan types](hr-benefits-setup-life-event-types.md).

## Create a life event type

1. In the **Benefits management** workspace, under **Setup**, select **Life event types**.

2. Select **New**.

3. Specify values for the following fields:

   | Field | Description |
   | --- | --- |
   | Life event type ID | The life event type unique identifier. |
   | Description | A description of the life event type. |
   | Life event type | A catalyst to updating an employee’s benefits enrollment. For a list of life events, see [Life events](hr-benefits-setup-payment-frequencies.md?life-events) below. |

4. Select **Save**.

## View attached plans

You can see a list of plans that are attached to the selected life event type. Life events are attached to a plan type, and plan types are associated with a plan. 

1. In the **Benefits management** workspace, under **Setup**, select **Life event types**.

2. Select **Actions**.

3. Select **Attached plans**.

## Life events

You can choose from the following life events when you create a life event type:

| Life event | Location | Trigger |
| --- | --- | --- |
| Marital status change | Worker > Profile > Personal information > Marital status| Change in marital status |
| Employment status change | <ul><li>Worker > Employment</li><li>Employment history page</li></ul> | Change in employment status |
| Employee address change | <ul><li>Worker > Profile > Addresses </li><li>Worker > Personal information > Personal contacts > Address</li></ul> Added, edited, or deleted address |
| Dependent change | <ul><li>Worker > Profile > Personal information > Personal contacts > Add or delete a dependent</li><li>Employee self service</li></ul> | Added or deleted dependent. The personal contact relationship must be child, spouse, domestic partner, or ex-spouse. Updating the **Valid from** date triggers the life event. If you don’t update that date, no life event will trigger. |
| Birth or Adoption (dependent) | <ul><li>Worker > Profile > Personal information > Personal contacts > Dependent details</li><li>Employee self service</li></ul> | **Adoption date** field populated. The birthdate of the child is required. |
| Loss of coverage (Spouse / domestic partner) | Worker > Profile > Personal information > Personal contacts >  Dependent details > Loss of coverage | **Loss of coverage** selected for a personal contact, along with **Effective date** |
| Domestic partner employment change | Worker > Profile > Personal information > Personal contacts > Dependent details >Employed. | <ul><li>Dependent details record created and **Personal contact employed** box = Yes</li><li>**Personal contact employed** box changed (Yes or No)</li></ul> |
| Leave of absence (Spouse/domestic partner) | Worker > Profile > Personal information > Personal contacts > Dependent details > Leave of absence | <ul><li>Dependent details record created and **EhrLOAEffectiveDate** filled in</li><li>**personPrivateDetails.EhrIsLOA** is changed (Yes or No)</li><li>**personPrivateDetails.EhrLOAEffectiveDate** is changed</li></ul> |
| Change in coverage (Position) | <ul><li>Worker > Position Assignment > Worker position assignments</li><li>Positions > Positions</li></ul> | <ul><li>Change to the position in the worker position assignment records</li><li>Change of the worker assignment in the position</li></ul> |
| Change in coverage (salary) | Worker > Compensation > Fixed plan | Annual benefit salary automatically recalculates when you change the compensation |
| Medicare (Employee / dependent) | Worker > Profile > Personal information > Personal contacts > Dependent details > Medicare effective date | Not automatically triggered when a personal contact enters an effective date. |
| Court ordered support | Worker > Profile > Personal information > Personal contacts > Dependent > Court ordered support (QMSCO/QDRO and effective dates | Doesn't trigger any automatic updates. It doesn't impact eligibility; it records a life event. |
| Deceased | Worker > Profile > Personal information > Deceased date | A deceased date is entered |
| Evidence of insurance | <ul><li>Worker > Worker > Versions > Employment history > Date manager > Benefit details</li><li> Worker > Employment > Benefit Details > Verification Date</li></ul> | <ul><li>A worker enters a verification date</li><li>A worker sets the EvidenceOfInsurability field to **Yes**</li></ul> |
| Beneficiary | Worker > Profile > Personal information > Personal contacts | A personal contact is added and the **Beneficiary** box and **Effective date** are populated. The personal contact must be of type **Child**, **Spouse**, **DomesticPartner**, **Sibling**, **FamilyContact**, **OtherContact**, **Parent**, **BeneficiaryEstate**, **BeneficiaryOrg**, or **BeneficiaryTrust**. |
| Employee Medicare | Worker > Worker > Versions > Employment history > Date manager > Benefit details | <ul><li>**EhrMedicareEligibilityDate** is changed</li><li>**MedicareEligibile** is set to **Yes**</li></ul> |
| Birthday | Worker > Profile > Personal information > Personal contacts > Dependent details > Birth date | A birth date is added or updated (not after Life event change processing). Example: If the **Personal contact eligibility options** for a child is set to Age: 26 in Setup > Benefits > Personal contact eligibility options, and if HR personnel run Life event change processing any day after the dependent turns 26, a message appears alerting them that the dependent is no longer eligible for coverage. |
| Worker eligibility change (not US-specific) | <ul><li>Worker > Employment</li><li>Worker > Worker > Versions > Employment history</li></ul> | <ul><li>Employee type, Employment category, or the five user-definable eligibility fields change</li><li>**HcmEmploymentDetail.EhrEmploymentType** changes (only processed for *changed* employment detail records, not processed for *new* employment records, like rehire and termination)</li></ul> |
| New eligibility override (not US-specific) | Human resources advanced > Benefits > Plans > Benefits > Eligibility rule override | Using Life event processing | EhrBenefitEligibilityRuleOverride.ValidFrom |
| Eligibility rule override change (not US-specific) | Human resources advanced > Benefits > Plans > Benefits > Eligibility rule override | Using Life event processing (only catches changes to **ValidFrom** and **ValidTo** fields on the Eligibility rule override) |
| Eligibility rule override expiration (not US-specific) | Human resources advanced > Benefits > Plans > Benefits > Eligibility rule override | Using Life event change processing. For example, if you edit a plan’s eligibility rule override expiration date to be today at 5:00 pm, any time after 5:00 pm or the following days, and then run Life event change processing, a message appears saying that the eligibility rule override has expired. |
| New benefit plan (not US-specific) | Human resources advanced > Benefits > Plans > New | <ul><li>Eligibility options are added to a current plan</li><li>A new plan with eligibility options attached is added</li></ul></br></br>HR personnel should run Life event eligibility processing in this instance. |
| Eligibility rule change (not US-specific) | Human resources advanced > Benefits > Rules/options > Eligibility rules | Using Life event eligibility processing. Logged when **EhrBenefitEligibilityRule** records have the following values changed: **UseEmplCategory**, **UseEmplStatus**, or **UseEmplType**. Only updates life event transactions that already exist for a changed rule or eligibility criteria. |
