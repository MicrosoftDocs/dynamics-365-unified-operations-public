---
# required metadata

title: Advanced filtering and query syntax
description: This article describes the filtering and query options for the Advanced filter/sort dialog and the matches operator in the Filter pane or grid column header filters.  
author: jasongre
ms.date: 03/09/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SysQueryForm
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 3811
ms.assetid: b4969b30-2fe1-4a3c-bbea-725dc37c8b60
ms.search.region: Global
# ms.search.industry: 
ms.author: jasongre
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Advanced filtering and query syntax

[!include [banner](../includes/banner.md)]


[!INCLUDE [PEAP](../../../includes/peap-3.md)]

This article describes the filtering and query options that are available when you use the Advanced filter/sort dialog or the **matches** operator in the Filter pane or grid column header filters.

## Advanced query syntax

<table>
<thead>
<tr>
<th>Syntax</th>
<th>Character description</th>
<th>Description</th>
<th>Example</th>
</tr>
</thead>
<tbody>
<tr>
<td><em>value</em></td>
<td>Equal to the value that is entered</td>
<td>Type the value to find.</td>
<td><strong>Smith</strong> finds &quot;Smith&quot;.</td>
</tr>
<tr>
<td>!<em>value</em> (exclamation point)</td>
<td>Not equal to the value that is entered</td>
<td>Type an exclamation point and then the value to exclude.</td>
<td><strong>!Smith</strong> finds all values except &quot;Smith&quot;.</td>
</tr>
<tr>
<td><em>from-value</em>..<em>to-value</em> (double period)</td>
<td>Between the two values that are separated by double periods</td>
<td>Type the from-value, then two periods, and then the to-value.</td>
<td><strong>1..10</strong> finds all values from 1 through 10. However, in a string field, <strong>A..C</strong> finds all values that start with &quot;A&quot; and &quot;B&quot;, and values that are exactly equal to &quot;C&quot;. For example, this query won't find &quot;Ca&quot;. To find all values from &quot;A<em>&quot; through &quot;C</em>&quot;, type <strong>A..D</strong>.</td>
</tr>
<tr>
<td>..<em>value</em> (double period)</td>
<td>Less than or equal to the value that is entered</td>
<td>Type two periods and then the value.</td>
<td><strong>..1000</strong> finds any number that is less than or equal to 1000, such as &quot;100&quot;, &quot;999.95&quot;, and &quot;1,000&quot;.</td>
</tr>
<tr>
<td><em>value</em>.. (double period)</td>
<td>Greater than or equal to the value that is entered</td>
<td>Type the value and then two periods.</td>
<td><strong>1000..</strong> finds any number that is greater than or equal to 1000, such as &quot;1,000&quot;, &quot;1,000.01&quot;, and &quot;1,000,000&quot;.</td>
</tr>
<tr>
<td>&gt;<em>value</em> (greater than sign)</td>
<td>Greater than the value that is entered</td>
<td>Type a greater than sign (<strong>&gt;</strong>) and then the value.</td>
<td><strong>&gt;1000</strong> finds any number that is greater than 1000, such as &quot;1000.01&quot;, &quot;20,000&quot;, and &quot;1,000,000&quot;.</td>
</tr>
<tr>
<td>&lt;<em>value</em> (less than sign)</td>
<td>Less than the value that is entered</td>
<td>Type a less than sign (<strong>&lt;</strong>) and then the value.</td>
<td><strong>&lt;1000</strong> finds any number that is less than 1000, such as &quot;999.99&quot;, &quot;1&quot;, and &quot;-200&quot;.</td>
</tr>
<tr>
<td><em>value</em>* (asterisk)</td>
<td>Starting from the value that is entered</td>
<td>Type the starting value and then an asterisk (<strong>*</strong>).</td>
<td><strong>S*</strong> finds any string that starts with &quot;S&quot;, such as &quot;Stockholm&quot;, &quot;Sydney&quot;, and &quot;San Francisco&quot;.</td>
</tr>
<tr>
<td>*<em>value</em> (asterisk)</td>
<td>Ending with the value that is entered</td>
<td>Type an asterisk and then the ending value.</td>
<td><strong>*east</strong> finds any string that ends with &quot;east&quot;, such as &quot;Northeast&quot; and &quot;Southeast&quot;.</td>
</tr>
<tr>
<td>*<em>value</em>* (asterisk)</td>
<td>Containing the value that is entered</td>
<td>Type an asterisk, then a value, and then another asterisk.</td>
<td><strong>*th*</strong> finds any string that contains &quot;th&quot;, such as &quot;Northeast&quot; and &quot;Southeast&quot;.</td>
</tr>
<tr>
<td>? (question mark)</td>
<td>Having one or more unknown characters</td>
<td>Type a question mark at the position of the unknown character in the value.</td>
<td><strong>Sm?th</strong> finds &quot;Smith&quot; and &quot;Smyth&quot;.</td>
</tr>
<tr>
<td><em>value</em>,<em>value</em> (comma)</td>
<td>Matching the values that are separated by commas</td>
<td>Type all your criteria, and separate them by using commas.</td>
<td><strong>A, D, F, G</strong> finds exactly &quot;A&quot;, &quot;D&quot;, &quot;F&quot;, and &quot;G&quot;. <strong>10, 20, 30, 100</strong> finds exactly &quot;10, 20, 30, 100&quot;.</td>
</tr>
<tr>
<td>"" (two double quotes)</td>
<td>Matching a blank value</td>
<td>Type two consecutive double quotes to filter for blank values in that field.</td>
<td>Two consecutive double quotes (<strong>""</strong>) finds rows with no value for the current column.</td>
</tr>
<tr>
<td>(<span class="code">Finance and operations query</span>) (finance and operations query between parentheses)</td>
<td>Matching a defined query</td>
<td>Type a query as an SQL statement between parentheses using the finance and operations query language.</td>
  <td><strong><span class="code">((AccountNum LIKE "US*") && (DirPartyTable.Name LIKE "Cont*"))</span></strong><br><br> 
       as an example of syntax for a filter condition on a field from the root datasource as well as a field from a different datasource (for the All customers page)</td>
</tr>
<tr>
<td>T</td>
<td>Today's date</td>
<td>Type <strong>T</strong>.</td>
<td><strong>T</strong> matches today's date.</td>
</tr>
<tr>
<td>(methodName(parameters)) (<strong>SysQueryRangeUtil</strong> method between parentheses)</td>
<td>Matching the value or range of values that are specified by the parameters of the <strong>SysQueryRangeUtil</strong> method</td>
<td>Type a <strong>SysQueryRangeUtil</strong> method that has parameters that specify the value or range of values.</td>
<td>
<ol>
<li>Click <strong>Accounts receivable</strong> &gt; <strong>Invoices</strong> &gt; <strong>Open customer invoices</strong>.</li>
<li>Press Ctrl+Shift+F3 to open the <strong>Inquiry</strong> page.</li>
<li>On the <strong>Range</strong> tab, click <strong>Add</strong>.</li>
<li>In the <strong>Table</strong> field, select <strong>Open customer transactions</strong>.</li>
<li>In the <strong>Field</strong> field, select <strong>Due date</strong>.</li>
<li>In the <strong>Criteria</strong> field, enter <strong>(yearRange(-2,0))</strong>.</li>
<li>Click <strong>OK</strong>. The list page is updated and lists the invoices that match the criterion that you entered. For this example, invoices that were due in the previous two years are listed.</li>
</ol>
See the table in the next section for additional details about <strong>SysQueryRangeUtil</strong> date methods, and several examples.</td>
</tr>
</tbody>
</table>

## Advanced date queries that use SysQueryRangeUtil methods

<table>
<thead>
<tr>
<th>Method</th>
<th>Description</th>
<th>Example</th>
</tr>
</thead>
<tbody>
<tr>
<td>Day (_relativeDays=0)</td>
<td>Find a date relative to the session date. Positive values indicate future dates, and negative values indicate past dates.</td>
<td>
<ul>
<li><strong>Tomorrow</strong> – Enter <strong>(Day(1))</strong>.</li>
<li><strong>Today</strong> – Enter <strong>(Day(0))</strong>.</li>
<li><strong>Yesterday</strong> – Enter <strong>(Day(-1))</strong>.</li>
</ul>
</td>
</tr>
<tr>
<td>DayRange (_relativeDaysFrom=0, _relativeDaysTo=0)</td>
<td>Find a range of dates relative to the session date. Positive values indicate future dates, and negative values indicate past dates.</td>
<td>
<ul>
<li><strong>Last 30 days</strong> – Enter <strong>(DayRange(-30,0))</strong>.</li>
<li><strong>Previous 30 days and next 30 days</strong> – Enter <strong>(DayRange(-30,30))</strong>.</li>
</ul>
</td>
</tr>
<tr>
<td>GreaterThanDate (_relativeDays=0) GreaterThanUtcDate (_relativeDays=0)</td>
<td>Find all dates after the specified relative date.</td>
<td>
<ul>
<li><strong>More than 30 days from now</strong> – Enter <strong>(GreaterThanDate(30))</strong>.</li>
</ul>
</td>
</tr>
<tr>
<td>GreaterThanUtcNow ()</td>
<td>Find all date/time entries after the current time.</td>
<td>
<ul>
<li><strong>All future date/times</strong> – Enter <strong>(GreaterThanUtcNow())</strong>.</li>
</ul>
</td>
</tr>
<tr>
<td>LessThanDate (_relativeDays=0) LessThanUtcDate (_relativeDays=0)</td>
<td>Find all dates before the specified relative date.</td>
<td>
<ul>
<li><strong>Less than seven days from now</strong> – Enter <strong>(LessThanDate(7))</strong>.</li>
</ul>
</td>
</tr>
<tr>
<td>LessThanUtcNow ()</td>
<td>Find all date/time entries before the current time.</td>
<td>
<ul>
<li><strong>All past date/times</strong> – Enter <strong>(LessThanUtcNow())</strong>.</li>
</ul>
</td>
</tr>
<tr>
<td>MonthRange (_relativeFrom=0, _relativeTo=0)</td>
<td>Find a range of dates, based on months relative to the current month.</td>
<td>
<ul>
<li><strong>Previous two months</strong> – Enter <strong>(MonthRange(-2,0))</strong>.</li>
<li><strong>Next three months</strong> – Enter <strong>(MonthRange(0,3))</strong>.</li>
</ul>
</td>
</tr>
<tr>
<td>YearRange (_relativeFrom=0, _relativeTo=0)</td>
<td>Find a range of dates, based on years relative to the current year.</td>
<td>
<ul>
<li><strong>Next year</strong> – Enter <strong>(YearRange(0, 1))</strong>.</li>
<li><strong>Previous year</strong> – Enter <strong>(YearRange(-1,0))</strong>.</li>
</ul>
</td>
</tr>
</tbody>
</table>


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
