**Employment employee entity**

**Important**

The functionality noted in this article is available from 10.0.39
version of the Dynamics 365 Human Resources.

**Applies to these Dynamics 365 apps**:  
Human Resources

This article describes the **PayIntV1HcmEmploymentEmployeeEntity**
entity for Dynamics 365 Human Resources.

**Description**

This entity provides information about the employee employment.

**Properties**

<table>
<colgroup>
<col style="width: 31%" />
<col style="width: 12%" />
<col style="width: 55%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>Property</strong></p>
<p>Physical name</p>
<p><em>Type</em></p></th>
<th><strong>Use</strong></th>
<th><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ProbationPeriod</p>
<p>mserp_ProbationPeriod</p>
<p><em>Date time offset</em></p></td>
<td>Read Only</td>
<td>This is the probation period detail.</td>
</tr>
<tr class="even">
<td><p>ValidFrom</p>
<p>mserp_ValidFrom</p>
<p><em>Date time offset</em></p></td>
<td>Read Only</td>
<td>Valid from details</td>
</tr>
<tr class="odd">
<td><p>ValidTo</p>
<p>mserp_ValidTo</p>
<p><em>Date time offset</em></p></td>
<td>Read Only</td>
<td>Valid to details</td>
</tr>
<tr class="even">
<td><p>EmploymentStartDate</p>
<p>mserp_EmploymentStartDate <em>Date time offset</em></p></td>
<td>Read Only</td>
<td><p>Employment start date detail</p>
<p> </p></td>
</tr>
<tr class="odd">
<td><p>EmploymentEndDate</p>
<p>mserp_EmploymentEndDate <em>Date time offset</em></p></td>
<td>Read Only</td>
<td><p>Employment end date details</p>
<p> </p></td>
</tr>
<tr class="even">
<td><p>LegalEntityId</p>
<p>mserp_LegalEntityId</p>
<p><em>String</em></p></td>
<td>Read Only</td>
<td>Details of the legal entity assigned. </td>
</tr>
<tr class="odd">
<td><p>PersonnelNumber</p>
<p>mserp_PersonnelNumber</p>
<p><em>String</em></p></td>
<td>Read Only</td>
<td><p>Personnel Number of the worker</p>
<p> </p></td>
</tr>
</tbody>
</table>

**Example query for Employment employee Detail entity**

**Request**

Entity name: *mserp_payintv1hcmemploymentemployeeentities*

*HTTPCopy*

*GET \[Organizaton
URI\]/api/data/v9.1/mserp_payintv1hcmemploymentemployeeentities*

**Response**

*JSONCopy*

*{  
      "mserp_probationperiod": "2017-11-19T08:00:00Z",  
      "mserp_validfrom": "2012-09-28T17:11:47Z",  
      "mserp_validto": "2154-12-31T23:59:59Z",  
      "mserp_employmentstartdate": "2011-11-19T08:00:00Z",  
      "mserp_employmentenddate": "2154-12-31T23:59:59Z",  
      "mserp_legalentityid": "USRT",  
      "mserp_personnelnumber": "000171",  
    }*
