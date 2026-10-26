---
# required metadata

title: Add custom fields to preboarding (preview)
description: This article explains how to add your own fields to the preboarding steps on the careers site and write their values to Microsoft Dynamics 365 Human Resources.
author: ramagadu
ms.date: 10/23/2026
ms.topic: how-to
ms.reviewer: twheeloc
# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: ramagadu
ms.search.validFrom: 2026-10-23
ms.dyn365.ops.version: Human Resources

---

# Add custom fields to preboarding (preview)

[!INCLUDE [banner](../includes/banner.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

You can add your own fields to the preboarding steps on the careers site, such as a preferred name or a T-shirt size. The candidate fills them in along with the standard fields. When the candidate submits the form, the values go to the fields you add in Human Resources.

A custom field has four parts:

1. A field in Human Resources, exposed on the data entity for that section.
1. A column in the matching preboarding table in Dataverse, which holds the candidate's value.
1. A **Pre-joining custom field** row in Dataverse, which connects the column to the field in Human Resources and controls how it's shown.
1. Access for the careers site to the new column.

## Sections and where values go

Each custom field belongs to a section. The section decides which Dataverse table holds the value, and which Human Resources entity receives it.

| Section | Dataverse table | Human Resources data entity |
| --- | --- | --- |
| Personal details | `msdyn_prejoiningpersonaldetail` | `HcmCandidateToHireEntity` |
| Address | `msdyn_prejoiningaddress` | `DirPartyLocationPostalAddressV2Entity` |
| Phone | `msdyn_prejoiningphone` | `DirPartyContactV3Entity` |
| Email | `msdyn_prejoiningemail` | `DirPartyContactV3Entity` |
| Dependents | `msdyn_prejoiningdependent` | `HcmPreJoiningDependentEntity` |
| Emergency contact | `msdyn_prejoiningemergencycontact` | `HcmPreJoiningEmergencyContactEntity` |
| Identification | `msdyn_prejoiningidentification` | `HcmPersonIdentificationNumberEntity` |
| Skills | `msdyn_prejoiningskill` | `HcmPersonSkillEntity` |
| Certificates | `msdyn_prejoiningcertificate` | `HcmPersonCertificateEntity` |
| Screenings | `msdyn_prejoiningscreening` | `HcmPersonScreeningEntity` |
| Education | `msdyn_prejoiningeducation` | `HcmPersonEducationEntity` |
| Professional experience | `msdyn_prejoiningprofessionalexperience` | `HcmPersonProfessionalExperienceEntity` |

The **Documentation** step doesn't support custom fields. To ask for more documents, set up document requirements instead. For more information, see [Configure preboarding](hr-preboarding-configuration.md).

## Supported field types

| Data type | Dataverse column type | Human Resources field type |
| --- | --- | --- |
| Text | Single line of text, Multiple lines of text | String, Memo |
| Whole number | Whole number | Integer, Int64 |
| Decimal | Decimal, Float | Real |
| Date | Date only | Date |
| Yes/No | Yes/No | NoYes enumeration |
| Choice | Choice | Enumeration |

Lookups, multi-select choices, files, images, and currency fields aren't supported.

## Add a custom field

To add a custom field, follow these steps:
1. Add the field in Human Resources.
1. Add the column in Dataverse.
1. Set the careers site to read and write the column.
1. Add the custom field row.
1. Map choice values.
1. Add labels in other languages (optional).
1. Test the field.

### Add the field in Human Resources

1. Add the field to the table in Human Resources, and to the data entity for the section, by using an extension. For more information, see [Add fields to the database by using extensions](../fin-ops-core/dev-itpro/extensibility/add-field-extension.md).
1. Build and deploy the extension.
1. In Dataverse, refresh the virtual table for the entity so that the new field appears as a column. For more information, see [Refresh virtual entity metadata](../fin-ops-core/dev-itpro/power-platform/enable-virtual-entities.md#refresh-virtual-entity-metadata).

> [!IMPORTANT]
> Refresh the virtual table after you add the field. If you skip the refresh, the new field isn't available in Dataverse, and the value isn't written.

In Dataverse, the new field's column name is `mserp_` followed by the field name in lowercase. For example, the field **TShirtSize** becomes `mserp_tshirtsize`. To confirm the name, open the virtual table in Power Apps, and check its columns.

### Add the column in Dataverse

1. In [Power Apps](https://make.powerapps.com/), open the preboarding table for the section, such as `msdyn_prejoiningpersonaldetail`.
1. Add a column of the matching type. For a Date data type, use **Date only**.
1. Publish your customizations.
1. Copy the column's logical name, such as `new_tshirtsize`. You need it in the next steps.

### Let the careers site read and write the column

The careers site reads and writes only the columns that are listed in the site setting for each table.

1. In [Power Pages](https://make.powerpages.microsoft.com/), select your careers site, select the ellipsis (**...**), and then select **Power Pages Management**.
1. Select **Site settings**, and open the `Webapi/<table>/fields` setting for the table. For example, `Webapi/msdyn_prejoiningpersonaldetail/fields`.
1. Add the column's logical name to the comma-separated list, exactly as it appears in Dataverse, and save.

The change can take a few minutes to apply.

### Add the custom field row

1. In [Power Apps](https://make.powerapps.com/), open the **Pre-joining custom field** table, and select **Edit** to add a row.
1. Enter the following values.

| Column | Value |
| --- | --- |
| **Name** | A name for the field, such as **T-shirt size**. |
| **Section** | The section where the field appears. |
| **Source column** | The logical name of the Dataverse column, such as `new_tshirtsize`. |
| **Target field** | The `mserp_` column name of the field in Human Resources, such as `mserp_tshirtsize`. |
| **Data type** | The data type of the field. |
| **Control type** | Optional. The field is shown as: **Text**, **Textarea**, **Number**, **Date**, **Dropdown**, or **Checkbox**. If it's blank, a control that matches the data type is used. |
| **Legal entity code** | Optional. The legal entity where the field is used. Leave it blank to use the field in all legal entities. |
| **Render in portal** | **Yes** to show the field on the careers site. |
| **Sync enabled** | **Yes** to write the value to Human Resources. |
| **Is required** | **Yes** if the candidate must fill in the field. |
| **Validation regex** | Optional. A regular expression that the value must match. |
| **Display order** | The order of the field among the custom fields in the section. |
| **Failure mode** | **Warn** (default) or **Block**. For more information, see [What happens if a value can't be written](#what-happens-if-a-value-cant-be-written). |

### Map choice values

For a **Choice** field, add one **Pre-joining field value map** row for each option:

| Column | Value |
| --- | --- |
| **Custom field** | The custom field row. |
| **Source value** | The Dataverse option value, as a number. For example, `100000000`. |
| **Target value** | The value to write to Human Resources. For an enumeration field, enter the option value that the Human Resources virtual table uses, which is 200000000 plus the enumeration value. For example, enter `200000001` for the enumeration value 1. |
| **Option label** | The text that the candidate sees. |
| **Display order** | The order of the option in the list. |

Text, number, date, and Yes/No fields don't need value maps.

### Add labels in other languages (optional)

To show the field's label in other languages, add a **Pre-joining custom field label** row for each language, with the **Language code** (for example, `1036` for French), the **Label**, and optional **Help text**. Candidates whose language has no label see the English label.

### Test the field

1. Initiate preboarding for a test candidate.
1. On the careers site, check that the field appears in its section, fill it in, and submit.
1. In Human Resources, check that the value is on the candidate.
1. Request rework on the section, change the value on the careers site, and submit again. Check that the new value is on the candidate.

> [!NOTE]
> If a candidate clears a custom field value during rework, the earlier value stays on the candidate in Human Resources. Only values that are filled in are written. If a value must be removed, HR clears it on the candidate directly.

#### What happens if a value can't be written

- With **Warn**, the field is skipped, and the rest of the submission is saved. The HR notification that the candidate submitted lists the fields that weren't saved, under **Custom fields not saved**. Check those values on the candidate in Human Resources.
- With **Block**, the submission fails, and the candidate is asked to submit again.

Use **Block** only for fields that must reach Human Resources before HR can continue.

#### Related information

- [Configure preboarding](hr-preboarding-configuration.md)
- [Complete preboarding as a candidate](hr-preboarding-for-candidates.md)
