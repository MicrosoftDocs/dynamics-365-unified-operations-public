---
# required metadata

title: X++ string run-time functions
description: This wiki describes the string run-time functions.
author: RobinARH
manager: AnnBe
ms.date: 2016-02-04 22 - 14 - 12
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: RobinARH
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 31401
ms.assetid: f8d76054-c863-40de-b32a-73dfaa77aeff
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# X++ string run-time functions

This wiki describes the string run-time functions.

match
-----

Searches for a string or expression in another string.

    int match(str pattern, str text)

### Parameters

| Parameter | Description                             |
|-----------|-----------------------------------------|
| pattern   | The string or expression to search for. |
| text      | The string to search.                   |

### Return value

**1** if the pattern is located in the string; otherwise, **0** (zero).

### Remarks

The search is case-insensitive. The following special characters can be used to create the pattern for the *pattern* parameter.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Character</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>\</td>
<td>A backslash (\) nullifies, or escapes, the special treatment of special characters, so that a special character can be matched like a normal letter. A pair of backslashes is translated into one non-special backslash. Examples:
<ul>
<li><strong>match(&quot;ab$cd&quot;,&quot;ab$cd&quot;);</strong> returns <strong>0</strong>.</li>
<li><strong>match(&quot;ab$cd&quot;,&quot;ab$cd&quot;);</strong> returns <strong>0</strong>. The backslash isn't escaped.</li>
<li><strong>match(&quot;ab\$cd&quot;,&quot;ab$cd&quot;);</strong> returns <strong>1</strong>. The backslash and dollar sign are escaped.</li>
</ul></td>
</tr>
<tr class="even">
<td>&lt; or ^</td>
<td>A left angle bracket (&lt;) or a circumflex (^) at the start of an expression is used to match the start of a line. Examples:
<ul>
<li><strong>match(&quot;&lt;abc&quot;,&quot;abcdef&quot;);</strong> returns <strong>1</strong>.</li>
<li><strong>match(&quot;&lt;abc&quot;,&quot;defabc&quot;);</strong> returns <strong>0</strong>.</li>
<li><strong>match(&quot;^abc&quot;,&quot;abcdef&quot;);</strong> returns <strong>1</strong>.</li>
<li><strong>match(&quot;^abc&quot;,&quot;defabc&quot;);</strong> returns <strong>0</strong>.</li>
</ul></td>
</tr>
<tr class="odd">
<td>&gt; or $</td>
<td>A right angle bracket (&gt;) or a dollar sign (?) at the end of the expression is used to match the end of a line. Examples:
<ul>
<li><strong>match(&quot;abc&gt;&quot;,&quot;abcdef&quot;);</strong> returns <strong>0</strong>.</li>
<li><strong>match(&quot;abc&gt;&quot;,&quot;defabc&quot;);</strong> returns <strong>1</strong>.</li>
</ul></td>
</tr>
<tr class="even">
<td>? or .</td>
<td>A question mark (?) or a period (.) matchs any one character in the same position. Examples:
<ul>
<li><strong>match(&quot;abc.def&quot;,&quot;abc#def&quot;);</strong> returns <strong>1</strong>.</li>
<li><strong>match(&quot;colou?r&quot;,&quot;colouXr&quot;);</strong> returns <strong>1</strong>.</li>
</ul></td>
</tr>
<tr class="odd">
<td>:x</td>
<td>A colon specifies a group of characters to match, as indicated by the character that immediately follows.</td>
</tr>
<tr class="even">
<td>:a</td>
<td>Sets the match to letters. Examples:
<ul>
<li><strong>match(&quot;ab:acd&quot;,&quot;ab#cd&quot;);</strong> returns <strong>0</strong>.</li>
<li><strong>match(&quot;ab:acd&quot;,&quot;abxyzcd&quot;);</strong> returns <strong>0</strong>.</li>
<li><strong>match(&quot;ab:acd&quot;,&quot;abxcd&quot;);</strong> returns <strong>1</strong>.</li>
</ul></td>
</tr>
<tr class="odd">
<td>:d</td>
<td>Sets the match to numeric characters. Examples:
<ul>
<li><strong>match(&quot;ab:dcd&quot;,&quot;ab3cd&quot;);</strong> returns <strong>1</strong>.</li>
<li><strong>match(&quot;ab:dcd&quot;,&quot;ab123cd&quot;);</strong> returns <strong>0</strong>.</li>
<li><strong>match(&quot;ab:dcd&quot;,&quot;abcd&quot;);</strong> returns <strong>0</strong>.</li>
</ul></td>
</tr>
<tr class="even">
<td>:n</td>
<td>Sets the match to alphanumeric characters. Examples:
<ul>
<li><strong>match(&quot;ab:ncd&quot;,&quot;ab%cd&quot;);</strong> returns <strong>0</strong>.</li>
<li><strong>match(&quot;ab:ncd&quot;,&quot;ab9cd&quot;);</strong> returns <strong>1</strong>.</li>
<li><strong>match(&quot;ab:ncd&quot;,&quot;abXcd&quot;);</strong> returns <strong>1</strong>.</li>
</ul></td>
</tr>
<tr class="odd">
<td>:SPACE</td>
<td>SPACE is the space character ( ). Sets the match to blanks, tabulations, and control characters such as Enter (new line). Examples:
<ul>
<li><strong>match(&quot;ab: cd&quot;,&quot;ab cd&quot;);</strong> returns <strong>1</strong>.</li>
<li><strong>match(&quot;ab: cd&quot;,&quot;ab\ncd&quot;);</strong> returns <strong>1</strong>.</li>
<li><strong>match(&quot;ab: cd&quot;,&quot;ab\tcd&quot;);</strong> returns <strong>1</strong>.</li>
<li><strong>match(&quot;ab: cd&quot;,&quot;ab cd&quot;);</strong> returns <strong>0</strong>. Only the first space is matched.</li>
</ul></td>
</tr>
<tr class="even">
<td>*</td>
<td>An expression that is followed by an asterisk (*) requires a match for zero, one, or more occurrences of the preceding expression. Examples:
<ul>
<li><strong>match(&quot;abc*d&quot;,&quot;abd&quot;);</strong> returns <strong>1</strong>.</li>
<li><strong>match(&quot;abc*d&quot;,&quot;abcd&quot;);</strong> returns <strong>1</strong>.</li>
<li><strong>match(&quot;abc*d&quot;,&quot;abcccd&quot;);</strong> returns <strong>1</strong>.</li>
<li><strong>match(&quot;abc*d&quot;,&quot;abxd&quot;);</strong> returns <strong>0</strong>.</li>
</ul></td>
</tr>
<tr class="odd">
<td>+</td>
<td>An expression that is followed by a plus sign (+) requires a match for one or more occurrences of the preceding expression. Examples:
<ul>
<li><strong>match(&quot;abc+d&quot;,&quot;abd&quot;);</strong> returns <strong>0</strong>.</li>
<li><strong>match(&quot;abc+d&quot;,&quot;abcd&quot;);</strong> returns <strong>1</strong></li>
<li><strong>match(&quot;abc+d&quot;,&quot;abcccd&quot;);</strong> returns <strong>1</strong>.</li>
<li><strong>match(&quot;abc+d&quot;,&quot;abxd&quot;);</strong> returns <strong>0</strong>.</li>
</ul></td>
</tr>
<tr class="even">
<td>-</td>
<td>An expression that is followed by a minus sign (-) requires a match for zero or one occurrence of the preceding expression. In other words, the preceding expression is optional. Examples:
<ul>
<li><strong>match(&quot;colou-r&quot;,&quot;color&quot;);</strong> returns <strong>1</strong>.</li>
<li><strong>match(&quot;colou-r&quot;,&quot;colour&quot;);</strong> returns <strong>1</strong>.</li>
</ul></td>
</tr>
<tr class="odd">
<td>[]</td>
<td>Matches a single character with any character that is enclosed in the brackets. A range of characters can be specified by two characters that are separated by a minus sign (-). For example, <strong>[a-z]</strong> matches all letters between a and z, <strong>[0-9]</strong> matches a digit, and <strong>[0-9a-f]</strong> matches a hexadecimal digit. Examples:
<ul>
<li><strong>match(&quot;[abc]&quot;,&quot;apple&quot;);</strong> returns <strong>1</strong>, because it matches the a in &quot;apple.&quot;</li>
<li><strong>match(&quot;[abc]&quot;,&quot;kiwi&quot;);</strong> returns <strong>0</strong>, because &quot;kiwi&quot; doesn't contain an a, b, or c.</li>
<li><strong>match(&quot;gr[ae]y&quot;,&quot;grey&quot;);</strong> returns 1. This expression also matches &quot;gray.&quot;</li>
<li><strong>match(&quot;gr[ae]y&quot;,&quot;graey&quot;);</strong> returns <strong>0</strong>, because only one character between &quot;gr&quot; and &quot;y&quot; is matched.</li>
</ul></td>
</tr>
<tr class="even">
<td>[^]</td>
<td>If the first character in the text that is enclosed in brackets is a circumflex (^), the expression matches all characters except the characters that are enclosed in the brackets. Examples:
<ul>
<li><strong>match(&quot;[^bc]at&quot;,&quot;bat&quot;);</strong> returns <strong>0</strong>.</li>
<li><strong>match(&quot;[^bc]at&quot;,&quot;hat&quot;);</strong> returns <strong>1</strong>.</li>
<li><strong>match(&quot;[^abc]&quot;,&quot;bat&quot;);</strong> returns <strong>1</strong>. Anything except a, b, or c is matched. Therefore, the t is matched.</li>
</ul></td>
</tr>
</tbody>
</table>

## strAlpha
Copies only the alphanumeric characters from a string.

    str strAlpha(str _text)

### Parameters

| Parameter | Description              |
|-----------|--------------------------|
| \_text    | The string to copy from. |

### Return value

A new string that contains all the alphanumeric characters from the specified string.

### Remarks

For example, **strAlpha("2+2=5 is this correct?")** returns the string **225isthiscorrect**.

### Example

    static void strAlphaExample(Args _arg)
    {
            str s;
            ;
            s = strAlpha("?a*bc123.");
            print s;
            pause;
    }

## strCmp
Compares two text strings.

    int strCmp(str text1, str text2)

### Parameters

| Parameter | Description        |
|-----------|--------------------|
| text1     | The first string.  |
| text2     | The second string. |

### Return value

**0** if the two strings are identical, **1** if the first string sorts earlier, or **-1** if the second string sorts earlier.

### Remarks

The comparison performed by this method is case-sensitive.

    print strCmp("abc", "abc"); //Returns the value 0.
    print strCmp("abc", "ABC"); //Returns the value 1.
    print strCmp("aaa", "bbb"); //Returns the value -1.
    print strCmp("ccc", "bbb"); //Returns the value 1.

## strColSeq
Converts all uppercase characters to lowercase characters, and converts all characters that have accents to the corresponding unaccented lowercase characters.

    str strColSeq(str text)

### Parameters

| Parameter | Description                                     |
|-----------|-------------------------------------------------|
| text      | The string to copy and convert characters from. |

### Return value

The converted text string.

### Remarks

The **strColSeq** function exists for backward-compatibility purposes. This function supports only the mapping for the following Western European characters:

-   AàáâãäÀÁÂÃÄBCçÇDEèéêëÈÉÊËFGHIìíîïÌÍÎÏJKLMNñÑOòóôõöÒÓÔÕÖPQRSTUùúûüÙÚÛÜVWXYýÝZæøåÆØÅ
-   aaaaaaaaaaabcccdeeeeeeeeefghiiiiiiiiijklmnnnooooooooooopqrstuuuuuuuuuvwxyyyz~¦Ç~¦Ç

For Unicode-compliant functionality, use the Win32 LCMapString application programming interface (API) via the **DLL** and **DLLFunc** classes.

### Example

The following example prints **abcdeabcde**.

    static void strColSeqExample(Args _arg)
    {
            ;
            print strColSeq("");
            pause;
    }

## strDel
Creates a copy of a string, from which the specified substring is removed.

    str strDel(str _text, int _position, int _number)

### Parameters

| Parameter  | Description                                                                                                                                                                                                                      |
|------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| \_text     | The string to copy from.                                                                                                                                                                                                         |
| \_position | The position at which to begin ignoring characters during the copy operation.                                                                                                                                                    |
| \_number   | The number of characters to ignore. A minus sign in front of the *\_number* parameter indicates that *\_number*–1 characters before the character at *\_position* should be removed together with the character at *\_position*. |

### Return value

The remaining characters that are copied from the string.

### Remarks

The **strDel** function is complementary to the **substr** function.

    strDel("ABCDEFGH",2,3); //Returns the string "AEFGH".
    strDel("ABCDEFGH",4,3); //Returns the string "ABCGH".

## strFind
Searches a string for the first occurrence of one of the specified characters.

    int strFind(str _text, str _characters, int _position, int _number)

### Parameters

| Parameter    | Description                                                                                                |
|--------------|------------------------------------------------------------------------------------------------------------|
| \_text       | The string to search.                                                                                      |
| \_characters | The characters to search for.                                                                              |
| \_position   | The position in the string where the search begins.                                                        |
| \_number     | A signed number that indicates the direction of the search and how many positions to search in the string. |

### Return value

The value of the position of the first occurrence of one of the specified characters.

### Remarks

To search from the beginning of the string to the end, use **1** as the value of the *\_position* parameter. If the value of the *\_number* parameter is negative, the system searches the number of characters backward from the specified position. The search isn't case-sensitive. Here is an example.

    strFind("ABCDEFGHIJ","KHD",1,10); //Returns the value 4 (the position where "D" was found).
    strFind("ABCDEFGHIJ","KHD",10,-10); //Returns the value 8 (the position where "H" was found).

The **strFind** function is complementary to the **strNFind** function.

## strFmt
Formats the specified string and substitutes any occurrences of n with the nth argument.

    str strFmt(str _string, ...)

### Parameters

| Parameter | Description            |
|-----------|------------------------|
| \_string  | The strings to format. |

### Return value

The formatted string.

### Remarks

If an argument isn't provided for a parameter, the parameter will be returned as "%n" in the string. The string conversion of values of the **real** type is limited to two decimal places. Values are rounded, not truncated. The **System.String::Format** method from the Microsoft .NET Framework can be used to gain additional functionality, as shown in the example.

### Example

    static void strFmtExampleJob(Args _arg)
    {
            System.Double sysDouble;
            real r = 8.3456789;
            int  i = 42;
            utcDateTime utc = str2DateTime("2008-01-16 13:44:55" ,321); // 321 == YMD.
            str  s;
            ;
            s = strFmt("real = %1, int = %2, utcDateTime = %3, [%4]", r, i, utc);
            info("X1:  " + s);
            //
            sysDouble = r;
            s = System.String::Format("{0:##.####}", sysDouble);
            info("N1:  " + s);
            //
            s = System.String::Format("{0,6:C}", sysDouble); // $
            info("N2:  " + s);
            /**********  Actual Infolog output
            Message (02:16:05 pm)
            X1:  real = 8.35, int = 42, utcDateTime = 1/16/2008 01:44:55 pm, [%4]
            N1:  8.3457
            N2:   $8.35
            **********/
    }

## strIns
Builds a string by inserting one string into another.

    str strIns(str _text1, str _text2, int _position)

### Parameters

| Parameter  | Description                                                                                          |
|------------|------------------------------------------------------------------------------------------------------|
| \_text1    | The string to insert the other string into.                                                          |
| \_text2    | The string to insert into the other string.                                                          |
| \_position | The position where the first character of the *\_text2* parameter should occur in the output string. |

### Return value

The combined text string.

### Remarks

The **strIns** function is complementary to the **strDel** function. If the value of the *\_position* parameter is more than the length of the original string, the string to insert is appended to the end of the original string.

    strIns("ABFGH","CDE",3); //Returns the string "ABCDEFGH".
    strIns("ABCD","EFGH",10); //Returns the string "ABCDEFGH".

## strKeep
Builds a string by using only the characters from the first input string that the second input string specifies should be kept.

    str strKeep(str _text1, str _text2)

### Parameters

| Parameter | Description                                                                         |
|-----------|-------------------------------------------------------------------------------------|
| \_text1   | The string that contains the characters that can be used to build an output string. |
| \_text2   | The string that specifies which characters to keep for the output string.           |

### Return value

A string of the characters that are kept.

### Remarks

    strKeep("ABBCDDEFGHB","BCD"); //Returns the string "BBCDDB".
    strKeep("abcZcba","bc") //Returns the string "bccb".

The **strKeep** function is complementary to the **strRem** function.

## strLen
Calculates the length of the specified string.

    int strLen(str text)

### Parameters

| Parameter | Description                            |
|-----------|----------------------------------------|
| text      | The string to calculate the length of. |

### Return value

The length of the specified string.

### Remarks

    strLen("ABC"); //Returns the value 3.
    strLen("ABCDEFGHIJ"); //Returns the value 10.

## strLine
Retrieves a single line from a string that spans multiple lines.

    str strLine(str string, int count)

### Parameters

| Parameter | Description                              |
|-----------|------------------------------------------|
| string    | A string that might span multiple lines. |
| count     | The offset of the line to return.        |

### Return value

A copied line of the string that is specified by the *string* parameter.

### Remarks

The first line of the string has an offset of 0. You can assign multiple lines to one string by embedding the *n* or *rn* characters in the string. Additionally, you can use the at sign (@) immediately before the opening quotation mark and use the Enter key to spread parts of the string value over multiple lines in the X++ code editor.

### Example

    static void strLineExample(Args _arg)
    {
            str mytxt = "first-linensecond-linenlast-line";
            ;
            // Prints "second-line".
            print strLine(mytxt,1);
            // Prints "last-line".
            print strLine(mytxt,2);
            pause;
    }

## strLTrim
Removes leading blanks from a text string.

    str strLTrim(str text)

### Parameters

| Parameter | Description                                   |
|-----------|-----------------------------------------------|
| text      | The string to delete the leading blanks from. |

### Return value

The string equivalent for the text that leading blanks have been removed from.

### Remarks

The **strLTrim** function is complementary to the **strRTrim** function.

### Example

    // Returns the text string "ABC-DEFG".
    strLTrim("   ABC-DEFG");

## strLwr
Converts all letters in the specified string to lowercase.

    str strLwr(str _text)

### Parameters

| Parameter | Description                         |
|-----------|-------------------------------------|
| \_text    | The string to convert to lowercase. |

### Return value

A copy of the specified string that contains only lowercase letter.

### Remarks

The **strLwr** function is complementary to the **strUpr** function. The **strLwr** function uses the **LCMapString** function in the Win32 API.

### Example

    static void strLwrExample(Args _args)
    {
            // Returns the text string "abcdd55efghij".
            print strLwr("Abcdd55EFGHIJ");
            pause;
    }

## strNFind
Searches part of a text string for the first occurrence of a character that isn't included in the specified list of characters.

    int strNFind(str _text, str _characters, int _position, int _number)

### Parameters

| Parameter    | Description                                                                                                                                                                                                     |
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| \_text       | The text string to search.                                                                                                                                                                                      |
| \_characters | The list of characters to exclude from the search.                                                                                                                                                              |
| \_position   | The position in the string at which to begin the search.                                                                                                                                                        |
| \_number     | A signed number that indicates the direction of the search and how many positions to search. If a minus sign precedes *\_number*, the system searches *\_number* characters in reverse order from *\_position*. |

### Return value

The position of the first occurrence of a character that isn't specified by the *\_characters* parameter.

### Remarks

The search isn't case-sensitive. To search from the beginning of the string to the end, use a value of **1** for the *\_position* parameter. If a minus sign precedes the value of the *\_number* parameter, the characters will be searched in reverse order, starting from the position that is specified by the *\_position* parameter.

    strNFind("ABCDEFGHIJ","ABCDHIJ",1,10); //Returns the value 5 (the position of "E");
    strNFind("CDEFGHIJ","CDEFGIJ",10,-10); //Returns the value 6 (the position of "H").
    strNFind("abcdef","abCdef",3,2) //Returns the value 0.
    strNFind("abcdef", "abcef",3,2) //Returns the value 4.

The **strNFind** function is complementary to the **strFind** function.

## strPoke
Overwrites part of a string with another string.

    str strPoke(str _text1, str _text2, int _position)

### Parameters

| Parameter  | Description                                                                     |
|------------|---------------------------------------------------------------------------------|
| \_text1    | The original string.                                                            |
| \_text2    | The string to replace part of the original string with.                         |
| \_position | The position of the original string at which to begin replacing the characters. |

### Return value

The new string.

### Remarks

The new string can be longer than the original string. However, if the value of the *\_position* parameter is more than the length of the string, the original string is returned without replacements.

    strPoke("12345678","AAA",3); //Returns the string "12AAA678".
    strPoke("abcde","4567",4); //Returns the string "abc4567".
    strPoke("abcde", "4567", "10"); //Returns the string "abcde".

## strPrompt
Appends a string with the specified number of period characters, followed by a colon and space character.

    str strPrompt(str _string, _int len)

### Parameters

| Parameter | Description                             |
|-----------|-----------------------------------------|
| \_string  | The original string.                    |
| \_len     | The desired final length of the string. |

### Return value

A string that looks like a prompt for user input.

### Remarks

In atypical cases, where the value of the *\_len* parameter is only slightly more than the length of the original string, the highest precedence is given to adding the trailing space. Next, precedence is given to the colon. The lowest precedence is given to the periods. Negative values for the *\_len* parameter return the input string appended with a trailing space.

    strPrompt("ab",-1); //Returns "ab ".
    strPrompt("ab",3); //Returns "ab ".
    strPrompt("ab",4); //Returns "ab: ".
    strPrompt("ab",5); //Returns "ab.: ".
    strPrompt("ab",6); //Returns "ab..: ".

### Example

    static void JobStrPromptDemo(Args _args)
    {
            // Printed string is "[abc..: ]"
            print "[", strPrompt("abc", 7), "]";
            pause;
    }

## strRem
Removes the characters that are specified in one string from another string.

    str strRem(str text1, str text2)

### Parameters

| Parameter | Description                                       |
|-----------|---------------------------------------------------|
| text1     | The string to remove characters from.             |
| text2     | The characters to exclude from the output string. |

### Return value

The remaining content of the original string.

### Remarks

This function is case-sensitive.

    strRem("abcd_abcd","Bc"); //Returns the string "abd_abd".
    strRem("ABCDEFGABCDEFG","ACEG"); //Returns the string "BDFBDF".

This function is complementary to the **strKeep** function.

## strRep
Repeats a string of characters.

    str strRep(str _text, str _number)

### Parameters

| Parameter | Description                               |
|-----------|-------------------------------------------|
| \_text    | The string to repeat.                     |
| \_number  | The number of times to repeat the string. |

### Return value

A new string that contains the contents of the original string that are repeated the specified number of times.

### Example

The following example prints the text string **ABABABABABAB**.

    static void strRepExample(Args _arg)
    {
            str strL;
            ;
            strL = strRep("AB",6);
            print strL;
            pause;
    }

## strRTrim
Removes the trailing space characters from the end of a string.

    str strRTrim(str _text)

### Parameters

| Parameter | Description                                               |
|-----------|-----------------------------------------------------------|
| \_text    | The string to remove the trailing space characters from . |

### Return value

A copy of the specified string that doesn't include trailing space characters.

### Remarks

    strRTrim("ABC-DEFG- "); //Returns the string "ABC-DEFG-".
    strRTrim(" CD "); //Returns " CD".

The **strRTrim** function is complementary to the **strLTrim** function.

## strScan
Searches a text string for an occurrence of another string.

    int strScan(str _text1, str _text2, int _position, int _number)

### Parameters

| Parameter  | Description                                                                                                                                                                                                                   |
|------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| \_text1    | The string to search in.                                                                                                                                                                                                      |
| \_text2    | The string to find.                                                                                                                                                                                                           |
| \_position | The first position in the *\_text1* parameter at which to perform a comparison.                                                                                                                                               |
| \_number   | The number of positions in the *\_text1* parameter to retry the comparison for. If a minus sign precedes the *\_number* parameter, the system searches the number of characters in reverse order from the specified position. |

### Return value

The position at which the specified string was found in the string; otherwise, **0** (zero).

### Remarks

The comparisons aren't case-sensitive. Values for the *\_position* parameter that are less than **1** are treated as **1**. The direction of the scan is controlled by the sign that is specified in the *\_number* parameter. A positive sign indicates that each successive comparison will start one position closer to the end of the string. A negative sign indicates that each comparison will start one position closer to the start of the string.

    strScan("ABCDEFGHIJ","DEF",1,10); //Returns the value 4.
    strScan ("ABCDEFGHIJ","CDE",10,-10); //Returns the value 3.

## strUpr
Converts all the letters in a string to uppercase.

    str strUpr(str _text)

### Parameters

| Parameter | Description                                 |
|-----------|---------------------------------------------|
| \_text    | The string to convert to uppercase letters. |

### Return value

A copy of the specified string that contains only lowercase letters.

### Remarks

The **strUpr** function is complementary to the **strLwr** function. The **strUpr** function uses the **LCMapString()** function in the Win32 API.

### Example

The following example will print **ABCDD55EFGHIJ**.

    static void strUprExample(Args _args)
    {
            print strUpr("Abcdd55EFGhiJ");
            pause;
    }

## subStr
Retrieves part of a string.

    str subStr(str _text, int _position, int _number)

### Parameters

| Parameter  | Description                                                                                                                                                                                                             |
|------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| \_text     | The original string.                                                                                                                                                                                                    |
| \_position | The position in the original string where the part to retrieve begins.                                                                                                                                                  |
| \_number   | A signed integer that indicates the direction and number of positions to retrieve from the original string. If a minus sign precedes *\_number*, the system selects the substring backward from the specified position. |

### Return value

A substring of the original string.

### Remarks

If a minus sign precedes the value of the *\_number* parameter, the substring will be selected backward from the specified position.

    subStr("ABCDEFGHIJ",3,5); //Returns the string "CDEFG".
    subStr("ABCDEFGHIJ",7,-4); //Returns the string "DEFG".
    subStr("abcdef"),2,99) //Returns the string "cdef".
    subStr("abcdef",2,3) //Returns the string "bcd".
    subStr("abcdef",2,-3); //Returns the string "ab".

