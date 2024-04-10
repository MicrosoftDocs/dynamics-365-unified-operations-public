**Compensation fixed plan table entity**

**Important**

The functionality noted in this article is available from 10.0.39
version of the Dynamics 365 Human Resources.

**Applies to these Dynamics 365 apps**:  
Human Resources

This article describes the mserp_PayIntV1HcmCompFixedPlanTableEntity
entity for Dynamics 365 Human Resources.

**Description**

This entity provides information about the compensation fixed plan of an
employee.

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
<td><p>ControlPoint</p>
<p>mserp_ControlPoint</p>
<p><em>String</em></p></td>
<td>Read Only</td>
<td>Reference point setups</td>
</tr>
<tr class="even">
<td><p>Currency</p>
<p>mserp_Currency</p>
<p><em>String</em></p></td>
<td>Read Only</td>
<td><p>Currency details</p>
<p> </p></td>
</tr>
<tr class="odd">
<td><p>Description</p>
<p>mserp_Description</p>
<p><em>String</em></p></td>
<td>Read Only</td>
<td>Description of the fixed compensation plans</td>
</tr>
<tr class="even">
<td><p>EnableRecommendation</p>
<p>mserp_RecommendationAllowed <em>Enum</em></p></td>
<td>Read Only</td>
<td><p>Recommendation allowed or not.</p>
<p> </p></td>
</tr>
<tr class="odd">
<td><p>GridId</p>
<p>mserp_CompensationStructure <em>String</em></p></td>
<td>Read Only</td>
<td> Compensation grid value</td>
</tr>
<tr class="even">
<td><p>HireRule</p>
<p>mserp_HireRule</p>
<p><em>Enum</em></p></td>
<td>Read Only</td>
<td><p>Hire rule set.</p>
<p> </p></td>
</tr>
<tr class="odd">
<td><p>MarketPriceIndicator</p>
<p>mserp_MarketPriceIndicator <em>Enum</em></p></td>
<td>Read Only</td>
<td><p>Market price indicator set.</p>
<p> </p></td>
</tr>
<tr class="even">
<td><p>PayFrequencyId</p>
<p>mserp_PayFrequency</p>
<p>String</p></td>
<td>Read Only</td>
<td>Pay rate conversion details</td>
</tr>
<tr class="odd">
<td><p>PlanId</p>
<p>mserp_Plan</p>
<p>String</p></td>
<td>Read Only</td>
<td>Name of the compensation plan</td>
</tr>
<tr class="even">
<td><p>Tolerance</p>
<p>mserp_OutOfRangeTolerance <em>Enum</em></p></td>
<td>Read Only</td>
<td>Out of range tolerance details.</td>
</tr>
<tr class="odd">
<td><p>Type</p>
<p>mserp_Type</p>
<p><em>Enum</em></p></td>
<td>Read Only</td>
<td>Type details.</td>
</tr>
<tr class="even">
<td><p>ValidTo</p>
<p>mserp_ ExpirationDate</p>
<p><em>Date time offset</em></p></td>
<td>Read Only</td>
<td>Compensation plan expiration date</td>
</tr>
<tr class="odd">
<td><p>ValidFrom</p>
<p>mserp_EffectiveDate</p>
<p><em>Date time offset</em></p></td>
<td>Read Only</td>
<td>Compensation plan effective date</td>
</tr>
<tr class="even">
<td><p>RefPointSetupId</p>
<p>mserp_RefPointSetupId</p>
<p>String</p></td>
<td>Read Only</td>
<td>Reference point setup id</td>
</tr>
</tbody>
</table>

**Example query for compensation fixed plan table entity**

**Request**

Entity name: mserp_payintv1hcmcompfixedplantableentities

*HTTPCopy*

*GET \[Organizaton
URI\]/api/data/v9.1/mserp_payintv1hcmcompfixedplantableentities*

**Response**

*JSONCopy*

*{  
      "mserp_controlpoint": "",  
      "mserp_currency": "USD",  
      "mserp_description": "Executive Broad Band",  
      "mserp_recommendationallowed": 200000000,  
      "mserp_compensationstructure": "ExBand",  
      "mserp_hirerule": 200000001,  
      "mserp_marketpriceindicator": 200000000,  
      "mserp_payfrequency": "Annual",  
      "mserp_plan": "ExBand",  
      "mserp_outofrangetolerance": 200000002,  
      "mserp_type": 200000002,  
      "mserp_effectivedate": "2005-01-01T00:00:00Z",  
      "mserp_expirationdate": "2154-12-31T00:00:00Z",  
      "mserp_refpointsetupid": "",  
  
    }*
