:original_name: en-us_topic_0000001795709689.html

.. _en-us_topic_0000001795709689:

What Do I Do If I Could Not Search for Logs on LTS?
===================================================

When you search for logs on the LTS console, if a message is displayed indicating that the query result is inaccurate, too many log results are matched, or field *XXX* without indexing configured cannot be queried, perform the following operations:

Message Displayed During Query: Inaccurate Query Results
--------------------------------------------------------

-  Possible causes: There are too many logs in the query time range, and not all logs are displayed.
-  Solution: Click the query button multiple times until you obtain all logs, or shorten the query time range and query again.

Too Many Logs Results from Log Query
------------------------------------

-  Possible cause: Only searches with phrase **#"value"** can ensure the sequence of keywords. For example, if the query statement is **abc def**, logs that contain either **abc** or **def** and logs that contain the phrase **abc def** will be matched.
-  Solution: Use phrase **#"abc def"** to accurately match logs containing phrase **abc def**.

Expected Logs Not Obtained with Specific Search Statements and No Error Message Displayed
-----------------------------------------------------------------------------------------

-  Possible causes: Search delimiters are not supported, or **\*** and **?** in a search statement are regarded as common characters and are not used as wildcards.
-  Solution: Use the correct query statement.

Message Displayed During Query: Field *XXX* Is Not Configured with Indexing and Cannot Be Queried
-------------------------------------------------------------------------------------------------

-  Possible cause: No field indexing is configured.
-  Solution: Create an index for field *XXX* on the **Index Settings** tab page and run the query statement again.

Message Displayed During Query: Full-Text Index Not Enabled and content Field and Full-Text Query Unsupported
-------------------------------------------------------------------------------------------------------------

-  Possible cause: Full-text indexing is disabled.
-  Solution: Enable **Index Whole Text** on the **Index Settings** tab page and run the query statement again.

Message Displayed During Query: Do Not Start with an Asterisk (*) or a Question Mark (?)
----------------------------------------------------------------------------------------

-  Possible cause: An asterisk (*) or question mark (?) is placed before the query statement.
-  Solution: Modify the query statement or use a correct delimiter.

Message Displayed During Query: long and float Fields Do Not Support Fuzzy Query Using Asterisks (*) or Question Marks (?)
--------------------------------------------------------------------------------------------------------------------------

-  Possible cause: An asterisk (*) or question mark (?) is used to query fields of the long and float types.
-  Solution: Modify the query statement and use operators (>=<) or IN syntax for range query.

Message Displayed During Query: string Fields Do Not Support Range Query Using the Operator (>=<) or IN Syntax
--------------------------------------------------------------------------------------------------------------

-  Possible cause: Operators (>=<) or the IN syntax is used to query fields of the string type.
-  Solutions:

   #. Modify the query statement and use the asterisk (*) or question mark (?) to perform fuzzy query.
   #. Change the value of this field to a number.

Message Displayed During Query: The Search Syntax Is Incorrect and the Query Statement Needs to Be Modified
-----------------------------------------------------------------------------------------------------------

-  Possible cause: The syntax of the operator is incorrect.

   Solution: Each operator has its syntax rule. Modify the search statement based on the rule. For example, operator **=** requires that the value on the right must be digits.

-  Possible cause: The search statement contains syntax keywords.

   Solution: If the log to search contains syntax keywords, the search statement must be enclosed in double quotation marks to convert the keywords into common characters. For example, if **and** is a syntax keyword, change the query statement **field:and** to **field:"and"**.
