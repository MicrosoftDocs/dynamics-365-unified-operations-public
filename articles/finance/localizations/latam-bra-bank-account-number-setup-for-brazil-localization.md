# Bank account number setup for Brazil Localization

When creating a bank account, the bank account number must be entered following a specific mask that encompasses the necessary attributes to identify a bank account number according to the regulations from the Brazilian Central Bank.

Follow these steps to create a bank account number:

1.  Go to **Cash and Bank Management &gt; Bank accounts &gt; Bank accounts.**

2.  Select an existing Bank account or create a new one selecting **New.**

3.  On the **Bank account number**, enter the bank account number as following mask:

123 1234-1 012345678901-12

Where:

123: the bank code as defined by the Brazilian Central Bank

1234: the bank branch

1: the check digit for the bank branch

012345678901: the bank account number

12: the check digit for the bank account number

4.  Select **Save.**

Note: the spaces between the block of digits must be provided according to the mask. When the entered bank account number does not comply to the mask, a validation throws the message: "Invalid bank account format. Expected format is "&lt;Bank code&gt; &lt;branch number&gt; &lt;account number&gt;"

Note: the localization design does not extract those bank account number elements automatically from the IBAN code, they must be manually extracted and entered in the **Bank account number**.
