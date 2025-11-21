:original_name: lts_07_0072.html

.. _lts_07_0072:

Configuring ICAgent Structuring Parsing
=======================================

LTS offers the ICAgent structuring parsing function to structure logs. The ICAgent parsing rules can be defined only when a log ingestion configuration is initially created. Based on your log content, you can choose from the following rules: **Single-Line - Full-Text Log**, **Multi-Line - Full-Text Log**, **JSON**, **Delimiter**, **Single-Line - Completely Regular**, **Multi-Line - Completely Regular**, and **Combined Parsing**. Once collected, structured logs are sent to your specified log stream for search and analysis.

ICAgent supports only RE2 regular expressions. For details, see `Syntax <https://github.com/google/re2/wiki/syntax>`__.

Configuring Structuring Parsing
-------------------------------

LTS supports the following log structuring parsing rules:

.. table:: **Table 1** Parsing rules

   +--------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Type                                                                                                                                 | Description                                                                                                                                                                                                                                                                                                                                                                                  |
   +======================================================================================================================================+==============================================================================================================================================================================================================================================================================================================================================================================================+
   | :ref:`Single-Line - Full-Text Log <lts_07_0072__en-us_topic_0000001745955461_en-us_topic_0000001679121953_section7183176192810>`     | Uses a newline character **\\n** as the end of a log line and saves each log event in the default key value **content**.                                                                                                                                                                                                                                                                     |
   +--------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Multi-Line - Full-Text Log <lts_07_0072__en-us_topic_0000001745955461_en-us_topic_0000001679121953_section1236505816295>`      | Applicable to scenarios where a raw log spans multiple lines (for example, Java program logs). To distinguish each log logically, use the first line regular expression. If a line of log matches the preset regular expression, the line is considered as the start of a log. The next line is considered as the end of the log.                                                            |
   +--------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`JSON <lts_07_0072__en-us_topic_0000001745955461_en-us_topic_0000001679121953_section2012514377558>`                            | Applicable to scenarios where each line in the log text is a raw log event and each log event can be extracted into multiple key-value pairs based on the JSON parsing rule.                                                                                                                                                                                                                 |
   +--------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Delimiter <lts_07_0072__en-us_topic_0000001745955461_en-us_topic_0000001679121953_section1278024311814>`                       | Applicable to scenarios where each line in the log text is a raw log event and each log event can be extracted into multiple key-value pairs based on a specified delimiter.                                                                                                                                                                                                                 |
   +--------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Single-Line - Completely Regular <lts_07_0072__en-us_topic_0000001745955461_en-us_topic_0000001679121953_section935510161114>` | Applicable to scenarios where each line in the log text is a raw log event and each log event can be extracted into multiple key-value pairs using a specified regular expression.                                                                                                                                                                                                           |
   +--------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Multi-Line - Completely Regular <lts_07_0072__en-us_topic_0000001745955461_en-us_topic_0000001679121953_section124171306139>`  | Applicable to scenarios where a complete log spans multiple lines (for example, Java program logs) and the log can be parsed into multiple key-value pairs using a specified regular expression.                                                                                                                                                                                             |
   +--------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Combined Parsing <lts_07_0072__en-us_topic_0000001745955461_en-us_topic_0000001679121953_section9280134951318>`                | For logs with complex structures and requiring multiple parsing modes (for example, completely regular + JSON), you can use this rule. It defines the pipeline logic for log parsing by entering plug-in syntax (in JSON format) under **Plug-in Settings**. You can add one or more plug-in configurations. ICAgent executes the configurations one by one based on the specified sequence. |
   +--------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _lts_07_0072__en-us_topic_0000001745955461_en-us_topic_0000001679121953_section7183176192810:

Single-Line - Full-Text Log
---------------------------

This rule uses a newline character **\\n** as the end of a log line and saves each log event in the default key value **content**. Log structuring is not performed on log data, and log fields are not extracted. The time of a log attribute is determined by the log collection time.

**Procedure:**

#. Select **Single-Line - Full-Text Log**.
#. **Log Filtering** is disabled by default. To filter records that meet specific conditions from massive log data, enable log filtering and add whitelist or blacklist rules. A maximum of 20 whitelist or blacklist rules can be added.

   -  Set whitelist rules. This filtering rule acts as a matching criterion, collecting and reporting only logs that match the specified regular expression.

      a. Click **Add** under **Whitelist Rule** and enter a key value and filtering rule (regular expression). When adding multiple whitelist filtering rules, you can select the **And** or **Or** relationship. This means a log will be collected when it satisfies all or any of the rules. In single-line and multi-line full-text modes, **content** is used as the key name *{key}* of the full text by default.

         For example, to collect only log lines containing **hello** from the logs, set the filtering rule to **.*hello.\***.

      b. Click **Verify** in the **Operation** column. In the displayed dialog box, enter a field value, and click **Verify** to verify the rule.

      c. After the verification is successful, click **OK** or **Close** to exit the dialog box.

   -  Set blacklist rules. This filtering rule acts as a discarding criterion, discarding logs that match the specified regular expression.

      a. Click **Add** under **Blacklist Rule** and enter a key value and filtering rule (regular expression). When adding multiple blacklist filtering rules, you can select the **And** or **Or** relationship. This means a log will be excluded when it satisfies all or any of the rules. In single-line and multi-line full-text modes, **content** is used as the key name *{key}* of the full text by default.

         For example, if you do not want to collect log lines containing **hello** from the logs, set the filtering rule to **.*hello.\***.

      b. Click **Verify** in the **Operation** column. In the displayed dialog box, enter a field value, and click **Verify** to verify the rule.

      c. After the verification is successful, click **OK** or **Close** to exit the dialog box.

.. _lts_07_0072__en-us_topic_0000001745955461_en-us_topic_0000001679121953_section1236505816295:

Multi-Line - Full-Text Log
--------------------------

A complete multi-line - full-text log is a single log that spans multiple lines, such as a Java program log. In this case, using the newline character **\\n** as the end identifier of a log is improper. To distinguish each log logically, use the first line regular expression. If a line of log matches the preset regular expression, the line is considered as the start of a log. The next line is considered as the end of the log.

When the multi-line full-text log parsing rule is used to collect logs, the default key value content is set to store multi-line logs. The log data is not processed by log structuring, and log fields are not extracted. The time of the log attribute is determined by the log collection time.

**Procedure:**

#. Select **Multi-Line - Full-Text Log**.
#. Select a log example from existing logs or paste it from the clipboard.

   -  Click **Select from Existing Logs**, filter logs by time range, select a log event, and click **OK**.
   -  Click **Paste from Clipboard** to paste the copied log content to the **Log Example** box.

#. A regular expression can be automatically generated or manually entered under **Regular Expression of the First Line**. The regular expression of the first line must match the entire first line, not just the beginning of the first line.
#. **Log Filtering** is disabled by default. To filter records that meet specific conditions from massive log data, enable log filtering and add whitelist or blacklist rules. A maximum of 20 whitelist or blacklist rules can be added.

   -  Set whitelist rules. This filtering rule acts as a matching criterion, collecting and reporting only logs that match the specified regular expression.

      a. Click **Add** under **Whitelist Rule** and enter a key value and filtering rule (regular expression). When adding multiple whitelist filtering rules, you can select the **And** or **Or** relationship. This means a log will be collected when it satisfies all or any of the rules. In single-line and multi-line full-text modes, **content** is used as the key name *{key}* of the full text by default.

         For example, to collect only log lines containing **hello** from the logs, set the filtering rule to **.*hello.\***.

      b. Click **Verify** in the **Operation** column. In the displayed dialog box, enter a field value, and click **Verify** to verify the rule.

      c. After the verification is successful, click **OK** or **Close** to exit the dialog box.

   -  Set blacklist rules. This filtering rule acts as a discarding criterion, discarding logs that match the specified regular expression.

      a. Click **Add** under **Blacklist Rule** and enter a key value and filtering rule (regular expression). When adding multiple blacklist filtering rules, you can select the **And** or **Or** relationship. This means a log will be excluded when it satisfies all or any of the rules. In single-line and multi-line full-text modes, **content** is used as the key name *{key}* of the full text by default.

         For example, if you do not want to collect log lines containing **hello** from the logs, set the filtering rule to **.*hello.\***.

      b. Click **Verify** in the **Operation** column. In the displayed dialog box, enter a field value, and click **Verify** to verify the rule.

      c. After the verification is successful, click **OK** or **Close** to exit the dialog box.

.. _lts_07_0072__en-us_topic_0000001745955461_en-us_topic_0000001679121953_section2012514377558:

JSON
----

The JSON parsing rule is applicable to scenarios where each line in the log text is a raw log event and each log event can be extracted into multiple key-value pairs based on the JSON parsing rule. If the extraction of key-value pairs is not desired, follow the instructions in :ref:`Multi-Line - Full-Text Log <lts_07_0072__en-us_topic_0000001745955461_en-us_topic_0000001679121953_section1236505816295>`.

**Procedure:**

#. Choose **JSON**.

#. **Log Filtering** is disabled by default. To filter records that meet specific conditions from massive log data, enable log filtering and add whitelist or blacklist rules. A maximum of 20 whitelist or blacklist rules can be added.

   -  Set whitelist rules. This filtering rule acts as a matching criterion, collecting and reporting only logs that match the specified regular expression.

      a. Click **Add** under **Whitelist Rule** and enter a key value and filtering rule (regular expression). A key value is a log field name.

         When adding multiple whitelist filtering rules, you can select the **And** or **Or** relationship. This means a log will be collected when it satisfies all or any of the rules.

         For example, to collect only log lines containing **hello**, enter **hello** as the key value, and set the filtering rule to **.*hello.\***.

      b. Click **Verify** in the **Operation** column. In the displayed dialog box, enter a field value, and click **Verify** to verify the rule.

      c. After the verification is successful, click **OK** or **Close** to exit the dialog box.

   -  Set blacklist rules. This filtering rule acts as a discarding criterion, discarding logs that match the specified regular expression.

      a. Click **Add** under **Blacklist Rule** and enter a key value and filtering rule (regular expression). A key value is a log field name.

         When adding multiple blacklist filtering rules, you can select the **And** or **Or** relationship. This means a log will be excluded when it satisfies all or any of the rules.

         For example, if you do not want to collect log lines containing **hello**, enter **hello** as the key value, and set the filtering rule to **.*hello.\***.

      b. Click **Verify** in the **Operation** column. In the displayed dialog box, enter a field value, and click **Verify** to verify the rule.

      c. After the verification is successful, click **OK** or **Close** to exit the dialog box.

#. **Raw Log Upload**:

   After this function is enabled, raw logs are uploaded to LTS as the value of the **content** field.

#. **Upload Parsing Failure Log**:

   After this function is enabled, raw logs are uploaded to LTS as the value of the **\_content_parse_fail\_** field.

#. :ref:`Custom Time <lts_07_0072__en-us_topic_0000001745955461_en-us_topic_0000001679121953_section85057307305>`:

   Enabling this lets you specify a field as the log time. Otherwise, the time set during ingestion configuration is used.

#. **JSON Parsing Layers**: Configure the JSON parsing layers. The value must be an integer ranging from 1 (default) to 4.

   This function expands the fields of a JSON log. For example, for raw log **{"key1":{"key2":"value"}}**, if you choose to parse it into 1 layer, the log will become **{"key1":{"key2":"value"}}**; if you choose to parse it into 2 layers, the log will become **{"key1.key2":"value"}**.

#. **JSON String Parsing**: disabled by default. After this function is enabled, escaped JSON strings can be parsed into JSON objects. For example, **{"key1":"{\\"key2\\":\\"value\\"}"}** can be parsed into **key1.key2:value**.

.. _lts_07_0072__en-us_topic_0000001745955461_en-us_topic_0000001679121953_section1278024311814:

Delimiter
---------

The parsing rule is applicable to scenarios where each line in the log text is a raw log event and each log event can be extracted into multiple key-value pairs based on a specified delimiter. If the extraction of key-value pairs is not desired, follow the instructions in :ref:`Single-Line - Full-Text Log <lts_07_0072__en-us_topic_0000001745955461_en-us_topic_0000001679121953_section7183176192810>`.

**Procedure:**

#. Select a delimiter.

#. Select or customize a delimiter.

#. Select a log example from existing logs or paste it from the clipboard, click **Verify**, and view the results under **Extraction Results**.

   -  Click **Select from Existing Logs**, select a log event, and click **OK**. You can select different time ranges to filter logs.
   -  Click **Paste from Clipboard** to paste the copied log content to the **Log Example** box.

#. **Log Filtering** is disabled by default. To filter records that meet specific conditions from massive log data, enable log filtering and add whitelist or blacklist rules. A maximum of 20 whitelist or blacklist rules can be added.

   -  Set whitelist rules. This filtering rule acts as a matching criterion, collecting and reporting only logs that match the specified regular expression.

      a. Click **Add** under **Whitelist Rule** and enter a key value and filtering rule (regular expression). A key value is a log field name.

         When adding multiple whitelist filtering rules, you can select the **And** or **Or** relationship. This means a log will be collected when it satisfies all or any of the rules.

         For example, to collect only log lines containing **hello**, enter **hello** as the key value, and set the filtering rule to **.*hello.\***.

      b. Click **Verify** in the **Operation** column. In the displayed dialog box, enter a field value, and click **Verify** to verify the rule.

      c. After the verification is successful, click **OK** or **Close** to exit the dialog box.

   -  Set blacklist rules. This filtering rule acts as a discarding criterion, discarding logs that match the specified regular expression.

      a. Click **Add** under **Blacklist Rule** and enter a key value and filtering rule (regular expression). A key value is a log field name.

         When adding multiple blacklist filtering rules, you can select the **And** or **Or** relationship. This means a log will be excluded when it satisfies all or any of the rules.

         For example, if you do not want to collect log lines containing **hello**, enter **hello** as the key value, and set the filtering rule to **.*hello.\***.

      b. Click **Verify** in the **Operation** column. In the displayed dialog box, enter a field value, and click **Verify** to verify the rule.

      c. After the verification is successful, click **OK** or **Close** to exit the dialog box.

#. **Raw Log Upload**:

   After this function is enabled, raw logs are uploaded to LTS as the value of the **content** field.

#. **Upload Parsing Failure Log**:

   After this function is enabled, raw logs are uploaded to LTS as the value of the **\_content_parse_fail\_** field.

#. :ref:`Custom Time <lts_07_0072__en-us_topic_0000001745955461_en-us_topic_0000001679121953_section85057307305>`:

   Enabling this lets you specify a field as the log time. Otherwise, the time set during ingestion configuration is used.

.. _lts_07_0072__en-us_topic_0000001745955461_en-us_topic_0000001679121953_section935510161114:

Single-Line - Completely Regular
--------------------------------

This parsing rule is applicable to scenarios where each line in the log text is a raw log event and each log event can be extracted into multiple key-value pairs using a specified regular expression. If the extraction of key-value pairs is not desired, follow the instructions in :ref:`Single-Line - Full-Text Log <lts_07_0072__en-us_topic_0000001745955461_en-us_topic_0000001679121953_section7183176192810>`.

**Procedure:**

#. Select **Single-Line - Completely Regular**.

#. Select a log example from existing logs or paste it from the clipboard.

   -  Click **Select from Existing Logs**, select a log event, and click **OK**. You can select different time ranges to filter logs.
   -  Click **Paste from Clipboard** to paste the copied log content to the **Log Example** box.

#. Enter a regular expression for extracting the log under **Extraction Regular Expression**, click **Verify**, and view the results under **Extraction Results**.

   Alternatively, click **automatic generation of regular expressions**. In the displayed dialog box, extract fields based on the log example, enter the key, and click **OK** to automatically generate a regular expression. Then, click **OK**.

#. **Log Filtering** is disabled by default. To filter records that meet specific conditions from massive log data, enable log filtering and add whitelist or blacklist rules. A maximum of 20 whitelist or blacklist rules can be added.

   -  Set whitelist rules. This filtering rule acts as a matching criterion, collecting and reporting only logs that match the specified regular expression.

      a. Click **Add** under **Whitelist Rule** and enter a key value and filtering rule (regular expression). A key value is a log field name.

         When adding multiple whitelist filtering rules, you can select the **And** or **Or** relationship. This means a log will be collected when it satisfies all or any of the rules.

         For example, to collect only log lines containing **hello**, enter **hello** as the key value, and set the filtering rule to **.*hello.\***.

      b. Click **Verify** in the **Operation** column. In the displayed dialog box, enter a field value, and click **Verify** to verify the rule.

      c. After the verification is successful, click **OK** or **Close** to exit the dialog box.

   -  Set blacklist rules. This filtering rule acts as a discarding criterion, discarding logs that match the specified regular expression.

      a. Click **Add** under **Blacklist Rule** and enter a key value and filtering rule (regular expression). A key value is a log field name.

         When adding multiple blacklist filtering rules, you can select the **And** or **Or** relationship. This means a log will be excluded when it satisfies all or any of the rules.

         For example, if you do not want to collect log lines containing **hello**, enter **hello** as the key value, and set the filtering rule to **.*hello.\***.

      b. Click **Verify** in the **Operation** column. In the displayed dialog box, enter a field value, and click **Verify** to verify the rule.

      c. After the verification is successful, click **OK** or **Close** to exit the dialog box.

#. **Raw Log Upload**:

   After this function is enabled, raw logs are uploaded to LTS as the value of the **content** field.

#. **Upload Parsing Failure Log**:

   After this function is enabled, raw logs are uploaded to LTS as the value of the **\_content_parse_fail\_** field.

#. :ref:`Custom Time <lts_07_0072__en-us_topic_0000001745955461_en-us_topic_0000001679121953_section85057307305>`:

   Enabling this lets you specify a field as the log time. Otherwise, the time set during ingestion configuration is used.

.. _lts_07_0072__en-us_topic_0000001745955461_en-us_topic_0000001679121953_section124171306139:

Multi-Line - Completely Regular
-------------------------------

This parsing rule is applicable to scenarios where a complete log spans multiple lines (for example, Java program logs) and the log can be parsed into multiple key-value pairs using a specified regular expression. If the extraction of key-value pairs is not desired, follow the instructions in :ref:`Multi-Line - Full-Text Log <lts_07_0072__en-us_topic_0000001745955461_en-us_topic_0000001679121953_section1236505816295>`. When configuring **Multi-Line - Completely Regular**, you need to enter a log example, use the first-line regular expression to match the complete content of the first line, and customize the extraction regular expression.

**Procedure:**

#. Select **Multi-Line - Completely Regular**.

#. Select a log example from existing logs or paste it from the clipboard.

   -  Click **Select from Existing Logs**, select a log event, and click **OK**. You can select different time ranges to filter logs.
   -  Click **Paste from Clipboard** to paste the copied log content to the **Log Example** box.

#. A regular expression can be automatically generated or manually entered under **Regular Expression of the First Line**. The regular expression of the first line must match the entire first line, not just the beginning of the first line.

   The regular expression of the first line is used to identify the beginning of a multi-line log. Example:

   .. code-block::

      2024-10-11 10:59:07.000 a.log:1 level:warn
        no.1 log
      2024-10-11 10:59:17.000 a.log:2 level:warn
        no.2 log

   Complete lines:

   .. code-block::

      2024-10-11 10:59:07.000 a.log:1 level:warn
      no.1 log

   First line:

   .. code-block::

      2024-10-11 10:59:07.000 a.log:1 level:warn

   Example of the regular expression of the first line: **^\\d{4}-\\d{2}-\\d{2}\\d{3}:\\d{2}:\\d{2}\\.\\d{3}$**. The date in each first line is unique. Therefore, the regular expression in the first line can be generated based on the date.

#. Enter a regular expression for extracting the log under **Extraction Regular Expression**, click **Verify**, and view the results under **Extraction Results**.

   Alternatively, click **automatic generation of regular expressions**. In the displayed dialog box, extract fields based on the log example, enter the key, and click **OK** to automatically generate a regular expression. Then, click **OK**.

   The extraction result is the execution result of the extraction regular expression instead of the first line regular expression. To check the execution result of the first line regular expression, go to the target log stream.

   If you enter an incorrect regular expression for **Regular Expression of the First Line**, you cannot view the reported log stream data.

#. **Log Filtering** is disabled by default. To filter records that meet specific conditions from massive log data, enable log filtering and add whitelist or blacklist rules. A maximum of 20 whitelist or blacklist rules can be added.

   -  Set whitelist rules. This filtering rule acts as a matching criterion, collecting and reporting only logs that match the specified regular expression.

      a. Click **Add** under **Whitelist Rule** and enter a key value and filtering rule (regular expression). A key value is a log field name.

         When adding multiple whitelist filtering rules, you can select the **And** or **Or** relationship. This means a log will be collected when it satisfies all or any of the rules.

         For example, to collect only log lines containing **hello**, enter **hello** as the key value, and set the filtering rule to **.*hello.\***.

      b. Click **Verify** in the **Operation** column. In the displayed dialog box, enter a field value, and click **Verify** to verify the rule.

      c. After the verification is successful, click **OK** or **Close** to exit the dialog box.

   -  Set blacklist rules. This filtering rule acts as a discarding criterion, discarding logs that match the specified regular expression.

      a. Click **Add** under **Blacklist Rule** and enter a key value and filtering rule (regular expression). A key value is a log field name.

         When adding multiple blacklist filtering rules, you can select the **And** or **Or** relationship. This means a log will be excluded when it satisfies all or any of the rules.

         For example, if you do not want to collect log lines containing **hello**, enter **hello** as the key value, and set the filtering rule to **.*hello.\***.

      b. Click **Verify** in the **Operation** column. In the displayed dialog box, enter a field value, and click **Verify** to verify the rule.

      c. After the verification is successful, click **OK** or **Close** to exit the dialog box.

#. **Raw Log Upload**:

   After this function is enabled, raw logs are uploaded to LTS as the value of the **content** field.

#. **Upload Parsing Failure Log**:

   After this function is enabled, raw logs are uploaded to LTS as the value of the **\_content_parse_fail\_** field.

#. :ref:`Custom Time <lts_07_0072__en-us_topic_0000001745955461_en-us_topic_0000001679121953_section85057307305>`:

   Enabling this lets you specify a field as the log time. Otherwise, the time set during ingestion configuration is used.

.. _lts_07_0072__en-us_topic_0000001745955461_en-us_topic_0000001679121953_section9280134951318:

Combined Parsing
----------------

For logs with complex structures and requiring multiple parsing modes (for example, Nginx, completely regular, and JSON), you can use this rule. It defines the pipeline logic for log parsing by entering plug-in syntax (in JSON format) under **Plug-in Settings**. You can add one or more plug-in configurations. ICAgent executes the configurations one by one based on the specified sequence.

**Procedure:**

#. Select **Combined Parsing**.

#. Select a log example from existing logs or paste it from the clipboard and enter the configuration content under **Plug-in Settings**.

#. Customize the settings based on the log content by referring to the following plug-in syntax.

   -  processor_regex

      .. table:: **Table 2** Regular expression extraction

         +----------------------------+--------------+---------------------------------------------------------------------+
         | Parameter                  | Type         | Description                                                         |
         +============================+==============+=====================================================================+
         | source_key                 | String       | Original field name.                                                |
         +----------------------------+--------------+---------------------------------------------------------------------+
         | multi_line_regex           | String       | Regular expression of the first line.                               |
         +----------------------------+--------------+---------------------------------------------------------------------+
         | regex                      | String       | **()** in a regular expression indicates the field to be extracted. |
         +----------------------------+--------------+---------------------------------------------------------------------+
         | keys                       | string array | Field name for the extracted content.                               |
         +----------------------------+--------------+---------------------------------------------------------------------+
         | keep_source                | Boolean      | Whether to retain the original field.                               |
         +----------------------------+--------------+---------------------------------------------------------------------+
         | keep_source_if_parse_error | Boolean      | Whether to retain the original field when a parsing error occurs.   |
         +----------------------------+--------------+---------------------------------------------------------------------+

   -  processor_split_string

      .. table:: **Table 3** Parsing using delimiters

         +----------------------------+--------------------------+----------------------------------------------------------------------------------------------------------------------+
         | Parameter                  | Type                     | Description                                                                                                          |
         +============================+==========================+======================================================================================================================+
         | source_key                 | String                   | Original field name.                                                                                                 |
         +----------------------------+--------------------------+----------------------------------------------------------------------------------------------------------------------+
         | split_sep                  | String                   | Delimiters. Enter delimiters based on the value of **split_type**.                                                   |
         +----------------------------+--------------------------+----------------------------------------------------------------------------------------------------------------------+
         | keys                       | string array             | Field name for the extracted content.                                                                                |
         +----------------------------+--------------------------+----------------------------------------------------------------------------------------------------------------------+
         | keep_source                | Boolean                  | Whether to retain the original field in the parsed log.                                                              |
         +----------------------------+--------------------------+----------------------------------------------------------------------------------------------------------------------+
         | split_type                 | char/special_char/string | Delimiter type. The options are **char** (single character), **special_char** (invisible character), and **string**. |
         +----------------------------+--------------------------+----------------------------------------------------------------------------------------------------------------------+
         | keep_source_if_parse_error | Boolean                  | Whether to retain the original field when a parsing error occurs.                                                    |
         +----------------------------+--------------------------+----------------------------------------------------------------------------------------------------------------------+

   -  processor_split_key_value

      .. table:: **Table 4** Key-value pair segmentation

         +------------------+--------------------------+----------------------------------------------------------------------------------------------------------------------+
         | Parameter        | Type                     | Description                                                                                                          |
         +==================+==========================+======================================================================================================================+
         | source_key       | String                   | Original field name.                                                                                                 |
         +------------------+--------------------------+----------------------------------------------------------------------------------------------------------------------+
         | split_sep        | String                   | Delimiter between key-value pairs. The default value is the tab character (\\t).                                     |
         +------------------+--------------------------+----------------------------------------------------------------------------------------------------------------------+
         | split_type       | char/special_char/string | Delimiter type. The options are **char** (single character), **special_char** (invisible character), and **string**. |
         +------------------+--------------------------+----------------------------------------------------------------------------------------------------------------------+
         | expand_connector | String                   | Delimiter between the key and value in a key-value pair. The default value is a colon (:).                           |
         +------------------+--------------------------+----------------------------------------------------------------------------------------------------------------------+
         | keep_source      | Boolean                  | Whether to retain the original field in the parsed log.                                                              |
         +------------------+--------------------------+----------------------------------------------------------------------------------------------------------------------+

   -  processor_add_fields

      .. table:: **Table 5** Adding a field

         +-----------+-------------+------------------------------------------------------------------------------------------------------------------------+
         | Parameter | Type        | Description                                                                                                            |
         +===========+=============+========================================================================================================================+
         | fields    | json/object | Name and value of the field to be added. The field is in key-value pair format. Multiple key-value pairs can be added. |
         +-----------+-------------+------------------------------------------------------------------------------------------------------------------------+

   -  processor_drop

      .. table:: **Table 6** Discarded fields

         ========= ============ =========================
         Parameter Type         Description
         ========= ============ =========================
         drop_keys string array List of discarded fields.
         ========= ============ =========================

   -  processor_rename

      .. table:: **Table 7** Renaming a field

         =========== ============ ==============
         Parameter   Type         Description
         =========== ============ ==============
         source_keys string array Original name.
         dest_keys   string array New name.
         =========== ============ ==============

   -  processor_json

      .. table:: **Table 8** JSON expansion and extraction

         +----------------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                  | Type    | Description                                                                                                                                      |
         +============================+=========+==================================================================================================================================================+
         | source_key                 | String  | Original field name.                                                                                                                             |
         +----------------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------+
         | keep_source                | Boolean | Whether to retain the original field in the parsed log.                                                                                          |
         +----------------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------+
         | expand_depth               | int     | JSON expansion depth. The default value **0** indicates that the depth is not limited. Other numbers, such as **1**, indicate the current level. |
         +----------------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------+
         | expand_connector           | String  | Connector for expanding JSON. The default value is a period (.).                                                                                 |
         +----------------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------+
         | prefix                     | String  | Prefix added to a field name when JSON is expanded.                                                                                              |
         +----------------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------+
         | keep_source_if_parse_error | Boolean | Whether to retain the original field when a parsing error occurs.                                                                                |
         +----------------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------+
         | parse_escaped_json         | Boolean | Parses escaped JSON strings into JSON objects.                                                                                                   |
         +----------------------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------+

   -  processor_filter_regex

      .. table:: **Table 9** Filters

         +-----------+-------------+------------------------------------------------------------------------------------------------+
         | Parameter | Type        | Description                                                                                    |
         +===========+=============+================================================================================================+
         | include   | json/object | The key indicates the log field, and the value indicates the regular expression to be matched. |
         +-----------+-------------+------------------------------------------------------------------------------------------------+
         | exclude   | json/object | The key indicates the log field, and the value indicates the regular expression to be matched. |
         +-----------+-------------+------------------------------------------------------------------------------------------------+

   -  processor_gotime

      .. table:: **Table 10** Extraction time

         +-----------------+---------+------------------------------------------------------------------------------------------------------------+
         | Parameter       | Type    | Description                                                                                                |
         +=================+=========+============================================================================================================+
         | source_key      | String  | Original field name.                                                                                       |
         +-----------------+---------+------------------------------------------------------------------------------------------------------------+
         | source_format   | String  | Original time format.                                                                                      |
         +-----------------+---------+------------------------------------------------------------------------------------------------------------+
         | source_location | int     | Original time zone. If the value is empty, it indicates the time zone of the host or container is located. |
         +-----------------+---------+------------------------------------------------------------------------------------------------------------+
         | set_time        | Boolean | Whether to set the parsed time as the log time.                                                            |
         +-----------------+---------+------------------------------------------------------------------------------------------------------------+
         | keep_source     | Boolean | Whether to retain the original field in the parsed log.                                                    |
         +-----------------+---------+------------------------------------------------------------------------------------------------------------+

#. Extract fields from the following log example (for your reference only):

   .. code-block::

      2025-03-19:16:49:03 [INFO] [thread1] {"ref":"https://www.test.com/","curl":"https://www.test.com/so/search?spm=1000.1111.2222.3333&q=linux%20opt%testabcd&t=&u=","sign":"1234567890","pid":"so","0508":{"sign":"112233445566 English bb Error, INFO, error bb&&bb","float":15.25,"long":15},"float":15.25,"long":15}

   a. Use regular expressions to extract fields such as **nowtime**, **level**, **thread**, and **jsonmsg**.
   b. Use JSON parsing to extract the **jsonmsg** field.
   c. Use delimiters to extract the **key1**, **key2**, and **key3** fields from the **0508.sign** field obtained from a JSON file.
   d. Use regular expressions to extract fields such as **a1**, **a2**, and **a3** from **key1**.

   Plug-in configuration:

   .. code-block::

      [{
              "detail": {
                  "dest_format": "",
                  "keys": ["nowtime", "level", "thread", "jsonmsg"],
                  "keep_source": true,
                  "regex": "(\\d{4}-\\d{2}-\\d{2}:\\d{2}:\\d{2}:\\d{2})\\s+\\[(\\w+)\\]\\s+\\[(\\w+)\\]\\s+(.*)",
                  "source_key": "content"
              },
              "type": "processor_regex"
          }, {
              "detail": {
                  "expand_connector": ".",
                  "expand_depth": 4,
                  "keep_source": true,
                  "source_key": "jsonmsg",
                  "source_location": 8
              },
              "type": "processor_json"
          }, {
              "detail": {
                  "keep_source": true,
                  "keep_source_if_parse_error": true,
                  "keys": [
                      "key1",
                      "key2",
                      "key3"
                  ],
                  "source_key": "0508.sign",
                  "split_sep": ",",
                  "split_type": "char"
              },
              "type": "processor_split_string"
          }, {
              "detail": {
                  "keep_source": true,
                  "keep_source_if_parse_error": true,
                  "keys": [
                      "a1",
                      "a2",
                      "a3"
                  ],
                  "regex": "^(\\w+)(?:[^ ]* ){1}(\\w+)(?:[^ ]* ){2}([^\\$]+)",
                  "source_key": "key1"
              },
              "type": "processor_regex"
          }
      ]

.. _lts_07_0072__en-us_topic_0000001745955461_en-us_topic_0000001679121953_section85057307305:

Custom Time
-----------

You can enable **Custom Log Time** to display the custom log time on the **Log Search** tab page. For details about how to set parameters, see :ref:`Table 11 <lts_07_0072__en-us_topic_0000001745955461_en-us_topic_0000001679121953_table788424883516>`. If **Custom Log Time** is disabled, the log collection time is displayed as the log time on the **Log Search** tab page.

:ref:`Table 13 <lts_07_0072__en-us_topic_0000001745955461_table158771222314>` lists common time standards, examples, and expressions.

.. _lts_07_0072__en-us_topic_0000001745955461_en-us_topic_0000001679121953_table788424883516:

.. table:: **Table 11** Parameter configuration

   +----------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Parameter                  | Description                                                                                                                                                                                                                                                            | Example Value         |
   +============================+========================================================================================================================================================================================================================================================================+=======================+
   | Key Name of the Time Field | Name of an extracted field. You can select an extracted field from the drop-down list. The field is of the **string** or **long** type.                                                                                                                                | test                  |
   +----------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Field Value                | For an extracted field, after you select a key, its value is automatically filled in.                                                                                                                                                                                  | 2023-07-19 12:12:00   |
   +----------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Time Format                | By default, log timestamps in LTS are accurate to seconds. You do not need to configure information such as milliseconds and microseconds. For details, see :ref:`Table 12 <lts_07_0072__en-us_topic_0000001745955461_en-us_topic_0000001532867577_table19279450336>`. | yyyy-MM-dd HH:mm:ss   |
   |                            |                                                                                                                                                                                                                                                                        |                       |
   |                            | -  If the time format is incorrect or the specified field does not exist, the log time is the time set during ingestion configuration.                                                                                                                                 |                       |
   |                            | -  The time field needs to be verified again when operations such as field name modification, field deletion, and field type modification are performed on structuring parsing.                                                                                        |                       |
   +----------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
   | Operation                  | Click the verification icon (|image1|). If message "The time format is successfully matched with the time field value." is displayed, the verification is successful.                                                                                                  | ``-``                 |
   +----------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

.. _lts_07_0072__en-us_topic_0000001745955461_en-us_topic_0000001532867577_table19279450336:

.. table:: **Table 12** Common time formats

   +-----------+--------------------------------------------------------+----------------------+
   | Format    | Description                                            | Example Value        |
   +===========+========================================================+======================+
   | EEE       | Abbreviation for a day of the week.                    | Fri                  |
   +-----------+--------------------------------------------------------+----------------------+
   | EEEE      | Full name for a day of the week.                       | Friday               |
   +-----------+--------------------------------------------------------+----------------------+
   | MMM       | Abbreviation for a month.                              | Jan                  |
   +-----------+--------------------------------------------------------+----------------------+
   | MMMM      | Full name for a month.                                 | January              |
   +-----------+--------------------------------------------------------+----------------------+
   | dd        | Day of the month, ranging from 01 to 31 (decimal).     | 07, 31               |
   +-----------+--------------------------------------------------------+----------------------+
   | HH        | Hour, in 24-hour format.                               | 22                   |
   +-----------+--------------------------------------------------------+----------------------+
   | h         | Hour, in 12-hour format.                               | 11                   |
   +-----------+--------------------------------------------------------+----------------------+
   | MM        | Month, ranging from 01 to 12 (decimal).                | 08                   |
   +-----------+--------------------------------------------------------+----------------------+
   | mm        | Minute, ranging from 00 to 59 (decimal).               | 59                   |
   +-----------+--------------------------------------------------------+----------------------+
   | a         | a.m. or p.m.                                           | **am** or **pm**     |
   +-----------+--------------------------------------------------------+----------------------+
   | h:mm:ss a | Time, in 12-hour format.                               | 11:59:59 am          |
   +-----------+--------------------------------------------------------+----------------------+
   | HH:mm     | Hour and minute.                                       | 23:59                |
   +-----------+--------------------------------------------------------+----------------------+
   | ss        | Number of the second, ranging from 00 to 59 (decimal). | 59                   |
   +-----------+--------------------------------------------------------+----------------------+
   | yy        | Year without century, ranging from 00 to 99 (decimal). | **04** or **98**     |
   +-----------+--------------------------------------------------------+----------------------+
   | yyyy      | Year (decimal).                                        | **2004** or **1998** |
   +-----------+--------------------------------------------------------+----------------------+
   | d         | Day of the month, ranging from 1 to 31 (decimal).      | **7** or **31**      |
   +-----------+--------------------------------------------------------+----------------------+
   | %s        | Unix timestamp.                                        | 147618725            |
   +-----------+--------------------------------------------------------+----------------------+

.. _lts_07_0072__en-us_topic_0000001745955461_table158771222314:

.. table:: **Table 13** Examples

   ============================== =========================== =============
   Example                        Time Expression             Time Standard
   ============================== =========================== =============
   2022-07-14T19:57:36+08:00      yyyy-MM-dd'T'HH:mm:ssXXX    Custom
   1548752136                     %s                          Custom
   27/Jan/2022:15:56:44           dd/MMM/yyyy:HH:mm:ss        Custom
   2022-07-24T10:06:41.000        yyyy-MM-dd'T'HH:mm:ss.SSS   Custom
   Monday, 02-Jan-06 15:04:05 MST EEEE, dd-MMM-yy HH:mm:ss Z  RFC850
   Mon, 02 Jan 2006 15:04:05 MST  EEE, dd MMM yyyy HH:mm:ss Z RFC1123
   02 Jan 06 15:04 MST            dd MMM yy HH:mm Z           RFC822
   02 Jan 06 15:04 -0700          dd MMM yy HH:mm Z           RFC822Z
   2023-01-02T15:04:05Z07:00      yyyy-MM-dd'T'HH:mm:ss Z     RFC3339
   2022-12-11 15:05:07            yyyy-MM-dd HH:mm:ss         Custom
   2025-02-24T05:24:07.085Z       yyyy-MM-dd'T'HH:mm:ss.SSSZ  Custom
   ============================== =========================== =============

.. |image1| image:: /_static/images/en-us_image_0000002363932205.png
