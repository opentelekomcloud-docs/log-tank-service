:original_name: lts_04_1031.html

.. _lts_04_1031:

Ingesting ECS Text Logs to LTS
==============================

ECSs are core computing resources that host many service applications. These applications generate text log data, including application and system logs. Such logs are essential for monitoring system health, optimizing performance, and troubleshooting. To better manage and analyze ECS text logs, you can ingest them to LTS. This centralizes log storage, enabling efficient log query, analysis, and alarm reporting.

Follow these steps to complete the ingestion configuration:

:ref:`Step 1: Select a Log Stream <lts_04_1031__en-us_topic_0000001118501736_section249910285303>`: Store various log types in separate log streams for better categorization and management.

:ref:`Step 2: (Optional) Select a Host Group <lts_04_1031__en-us_topic_0000001118501736_section1014910157328>`: Define the range of hosts for log ingestion. Host groups are virtual groups of hosts. They help you organize and categorize hosts, making it easier to configure log ingestion for multiple hosts simultaneously. You can add one or more hosts whose logs are to be collected to a single host group, and associate it with the same ingestion configuration.

:ref:`Step 3: Configure the Collection <lts_04_1031__en-us_topic_0000001118501736_section196913102330>`: Configure the log collection details, including collection paths and policies.

:ref:`Step 4: Configure Indexing <lts_04_1031__en-us_topic_0000001118501736_section18351555203314>`: An index is a storage structure used to query log data. Configuring indexing makes log searches and analysis faster and easier.

:ref:`Step 5: Complete the Ingestion Configuration <lts_04_1031__en-us_topic_0000001118501736_section9751116142720>`: After a log ingestion configuration is created, manage it in the ingestion list.

:ref:`Setting Multiple Ingestion Configurations in a Batch <lts_04_1031__en-us_topic_0000001118501736_section124378505151>`: Select this mode to collect logs from multiple scenarios.

Constraints
-----------

-  If a collection path of a host has been configured in AOM, do not configure it again in LTS.
-  After LTS delivers the collection configuration, ICAgent collects files according to the following rules:

   -  New files (collected for the first time): If the last modification time of a file is more than 6 hours earlier than the current time, the file is not collected.
   -  Old files (not collected for the first time): If the last modification time of a file is more than 3 minutes earlier than the current time, the file is not collected.

Prerequisites
-------------

-  A log group and a log stream have been created. For details, see :ref:`Managing Log Groups <lts_04_0003>` and :ref:`Managing Log Streams <lts_04_0004>`.
-  An ECS (host) to collect logs from has been created. If you already have an available ECS, skip this step.
-  ICAgent has been installed on the host. For details, see :ref:`Installing ICAgent (Intra-Region Hosts) <lts_02_0013>` or :ref:`Installing ICAgent (Extra-Region Hosts) <lts_02_0828>` according to the location of your host.
-  The host with ICAgent installed has been added to a host group. For details, see :ref:`Managing Host Groups <lts_02_1033>`.
-  To ensure that the host can properly report log data and use metrics, its security group must allow inbound ports 8149, 8102, 8923, 30200, 30201, and 80.

.. _lts_04_1031__en-us_topic_0000001118501736_section249910285303:

Step 1: Select a Log Stream
---------------------------

#. Log in to the management console and choose **Management & Deployment** > **Log Tank Service**.

#. Choose **Log Ingestion** > **Ingestion Center** in the navigation pane and click **ECS (Elastic Cloud Server)**.

   You can also choose **Log Ingestion** > **Ingestion Management** in the navigation pane and click **Create**. On the displayed page, click **ECS (Elastic Cloud Server)**.

#. Select a log group.

   -  **To use an existing log group:** Select a log group from the **Log Group** drop-down list.
   -  **To use a new log group:** If there is no desired log group, click **Create Log Group** to create one. For details, see :ref:`Managing Log Groups <lts_04_0003>`.

#. Select a log stream.

   -  **To use an existing log stream:** Select a log stream from the **Log Stream** drop-down list.
   -  **To use a new log stream:** If there is no desired log stream, click **Create Log Stream** to create one. For details, see :ref:`Managing Log Streams <lts_04_0004>`.

#. Click **Next: (Optional) Select Host Group**.

.. _lts_04_1031__en-us_topic_0000001118501736_section1014910157328:

Step 2: (Optional) Select a Host Group
--------------------------------------

A host group is a virtual group of hosts, allowing you to configure host log collection efficiently. Ensure that :ref:`ICAgent has been installed <lts_02_0013>` on hosts where logs are to be collected and :ref:`the hosts have been added to a host group <lts_02_1033__en-us_topic_0000001118763740_li682633315215>`.

#. Select one or more host groups.

   -  **To select existing host groups:** In the host group list, select one or more host groups to collect their logs.

      .. caution::

         You can skip this step by not selecting any host group and clicking **Next: Configurations**, and then **Skip** in the subsequent dialog box. However, if you skip this step, the collection configuration will not take effect. It is advised to select host groups during the initial ingestion configuration.

      If you initially skip host group selection, you can associate host groups later using either method:

      -  Choose **Host Management** > **Host Groups** in the navigation pane and associate host groups with the desired ingestion configuration.
      -  After the ingestion configuration is created, choose **Log Ingestion** > **Ingestion Management** in the navigation pane. Click **Modify** in the **Operation** column of the desired ingestion configuration and associate it with host groups.

   -  If there are no desired host groups, click **Create** above the host group list. On the **Create Host Group** page, add hosts based on their ICAgent installation status.

      -  **If ICAgent is already installed:** Select the hosts with ICAgent installed under **Add Host**. For details, see :ref:`Managing Host Groups <lts_02_1033>`.
      -  **If ICAgent is not yet installed:** Click **Install ICAgent** under **Add Host**. Select **Intra-region hosts** or **Extra-region hosts** based on the host location and proceed with the ICAgent installation. For details, see :ref:`Installing ICAgent (Intra-Region Hosts) <lts_02_0013>`. After ICAgent is installed on the desired host, return to the ECS log ingestion page, click **Create** above the host group list again. The desired host will now be displayed under **Add Host** on the **Create Host Group** page.

#. Click **Next: Configurations**.

.. _lts_04_1031__en-us_topic_0000001118501736_section196913102330:

Step 3: Configure the Collection
--------------------------------

Collection configuration items include the log collection scope, collection mode, and format processing. Configure them as follows.

.. warning::

   Protect your privacy and sensitive data. You are advised not to transmit privacy or sensitive data through fields involved in access logs. Encrypt the data if necessary.

**Procedure**

#. **Collection Configuration Name**: Enter 1 to 64 characters. Only letters, digits, hyphens (-), underscores (_), and periods (.) are allowed. Do not start with a period or underscore, or end with a period.

   -  If you want to reuse existing collection configurations, click **Import Configuration** next to the text box. On the **Import Configuration** page, select a configuration and click **OK**.
   -  **Import Old-Edition Configuration**: Import the host ingestion configuration of the old version to the log ingestion of the new version.

      -  If LTS is newly installed and **Import Old-Edition Configuration** is not displayed, you can directly create a configuration without importing the old one.
      -  If LTS is upgraded, **Import Old-Edition Configuration** is displayed. Import the old configuration or create one as required.

#. .. _lts_04_1031__en-us_topic_0000001118501736_li17754123317308:

   **Collection Paths**: Specify the paths from which LTS will collect logs. The rules for setting collection paths are as follows:

   -  **Logs can be collected recursively. A double asterisk (**) can represent up to 5 directory levels in a path.**

      For example, **/var/logs/**/a.log** will match the following logs:

      .. code-block::

         /var/logs/a.log
         /var/logs/1/a.log
         /var/logs/1/2/a.log
         /var/logs/1/2/3/a.log
         /var/logs/1/2/3/4/a.log
         /var/logs/1/2/3/4/5/a.log

      -  **/1/2/3/4/5/** indicates the 5 directory levels recursively nested within the **/var/logs** directory. All the **a.log** files found in all these levels of directories will be collected.
      -  Only one double asterisk (**) can be contained in a collection path. For example, **/var/logs/**/a.log** is acceptable but **/opt/test/**/log/*\*** is not.
      -  A collection path cannot begin with a double asterisk (**), such as **/**/test**, to avoid collecting system files.

   -  You can use an asterisk (*) as a wildcard for fuzzy match. The wildcard (*) can represent one or more characters of a directory or file name.

      If a log collection path is similar to **C:\\windows\\system32** but logs cannot be collected, enable Web Application Firewall (WAF) and configure the path again.

      -  Example 1: **/var/logs/*/a.log** will match all **a.log** files found in all directories under the **/var/logs/** directory:

         .. code-block::

            /var/logs/1/a.log
            /var/logs/2/a.log

      -  Example 2: **/var/logs/service-*/a.log** will match files as follows:

         .. code-block::

            /var/logs/service-1/a.log
            /var/logs/service-2/a.log

      -  Example 3: **/var/logs/service/a*.log** will match files as follows:

         .. code-block::

            /var/logs/service/a1.log
            /var/logs/service/a2.log

   -  If the collection path is set to a file name, the corresponding file is collected. Only text files can be collected.

   -  **Add Custom Wrapping Rule**: ICAgent determines whether a file is wrapped based on the file name rule. If your wrapping rule does not comply with the built-in rules, you can add a custom wrap rule to prevent log loss during repeated collection and wrapping.

      The built-in rules are *{basename}{connector}{wrapping identifier}.{suffix}* and *{basename}.{suffix}{connector}{wrapping identifier}*. Connectors can be hyphens (-), periods (.), or underscores (_), wrapping identifiers can contain only non-letter characters, and the suffix can contain only letters.

      A custom wrapping rule consists of *{basename}* and the feature regular expression of the wrapped file. Example: If your log file name is **test.out.log** and the names after wrapping are **test.2024-01-01.0.out.log** and **test.2024-01-01.1.out.log**, configure the collection path to **/opt/*.log**, and add a custom wrapping rule: *{basename}*\ **\\.\\d{4}-\\d{2}-\\d{2}\\.\\d{1}.out.log**.

   -  You can verify collection paths to ensure that logs can be properly collected. Click **use path verification**, enter the collection paths and absolute paths of the log files, and click **OK**. You can add up to 30 collection paths. If the paths are correct, a success message will be displayed.

   -  You can verify wrapping rules to ensure that logs can be properly collected. Click **wrapping rule verification**, enter the name of the collected file, file name after wrapping, and wrapping rule, and click **OK**. If the wrapping rule is correct, a success message will be displayed.

#. **Allows multiple file collection** (not available to Windows)

   After you enable this function, one host log file can be collected to multiple log streams.

   After you disable this function, each collection path must be unique. That is, the same log file in the same host cannot be collected to different log streams.

#. **Set Collection Filters**: Blacklisted directories or files will not be collected.

   Blacklist filters can be exact matches or wildcard pattern matches. For details, see :ref:`Collection Paths <lts_04_1031__en-us_topic_0000001118501736_li17754123317308>`.

   -  If you blacklist a file or directory that has been set as a collection path in the previous step, the blacklist settings will be used and the file or files in the directory will be filtered out.
   -  If a log has been added to the blacklist, it cannot be collected even if you create a log ingestion task. You can collect it again only after you delete the collection path from the blacklist.
   -  If you specify a directory, all files in the directory are filtered out, but log files in the folders in the directory cannot be filtered out.
   -  Collection filters cannot be set for Windows hosts.

#. **Collect Windows Event Logs**: To collect logs from Windows hosts, enable this option. Up to 500 Windows event logs can be collected per minute. Configure the parameters by referring to :ref:`Table 1 <lts_04_1031__en-us_topic_0000001118501736_table5492185916810>`.

   .. _lts_04_1031__en-us_topic_0000001118501736_table5492185916810:

   .. table:: **Table 1** Parameters for collecting windows event logs

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                            |
      +===================================+========================================================================================================================================================================================================================================================================+
      | Log Type                          | You can select from the following log types:                                                                                                                                                                                                                           |
      |                                   |                                                                                                                                                                                                                                                                        |
      |                                   | -  **System**: records events generated by Windows OS components, including drivers, system services, and hardware faults.                                                                                                                                             |
      |                                   | -  **Application**: records events generated by user applications or third-party software.                                                                                                                                                                             |
      |                                   | -  **Security**: records events related to system security, such as login attempts, permission changes, and audit policy triggers.                                                                                                                                     |
      |                                   | -  **Startup**: records events that occur during Windows OS startup.                                                                                                                                                                                                   |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | First Collection Time Offset      | If you set this parameter to **7**, logs generated within the seven days before the collection start time are collected. This offset takes effect only for the first collection to ensure that the logs are not repeatedly collected. The maximum value is seven days. |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Event Level                       | You can filter and collect Windows events based on their severity (**information**, **warning**, **error**, **critical**, and **verbose**). This function is available only to Windows Vista or later.                                                                 |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. **Structuring Parsing**:

   LTS offers various log parsing rules, including **Single-Line - Full-Text Log**, **Multi-Line - Full-Text Log**, **JSON**, **Delimiter**, **Single-Line - Completely Regular**, **Multi-Line - Completely Regular**, and **Combined Parsing**. Select a parsing rule that matches your log content. Once collected, structured logs are sent to your specified log stream, enabling field searching.

   -  If you enable **Structuring Parsing**, configure it by referring to :ref:`Configuring ICAgent Structuring Parsing <lts_07_0072>`.
   -  If you disable **Structuring Parsing**, log data will not be structured. Raw logs will be sent to the specified log stream, allowing only keyword-based searches.

#. **Other**: After setting the collection paths, you can also set log splitting, binary file collection, and custom metadata.

   .. table:: **Table 2** Other configurations

      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                                                                                                                                                                                                                                         | Example Value         |
      +=======================+=====================================================================================================================================================================================================================================================================================================================================================================+=======================+
      | Max Directory Depth   | Specify the number of directory levels that can be traversed when using double asterisks (``**``) for fuzzy matching of log collection paths. LTS supports a maximum of 20 directory levels.                                                                                                                                                                        | 5                     |
      |                       |                                                                                                                                                                                                                                                                                                                                                                     |                       |
      |                       | For example, to collect logs from **/var/logs/department/app/a.log**, set the collection path to **/var/logs/**/a.log** and **Max Directory Depth** to **5**.                                                                                                                                                                                                       |                       |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Split Logs            | To prevent individual logs from being too large or being truncated and discarded, you can split logs based on file size.                                                                                                                                                                                                                                            | Enable                |
      |                       |                                                                                                                                                                                                                                                                                                                                                                     |                       |
      |                       | -  If **Split Logs** is enabled, logs exceeding the specified size will be split into multiple logs for collection. Specify the size in the range from 500 KB to 1,024 KB. For example, if you set the size to 500 KB, a 600 KB log will be split into a 500 KB log and a 100 KB log. This restriction is applicable to single-line logs only, not multi-line logs. |                       |
      |                       | -  If **Split Logs** is disabled, any log exceeding 500 KB will have its excess content truncated and discarded.                                                                                                                                                                                                                                                    |                       |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Collect Binary Files  | Specify whether to collect log data stored in binary format. You can run the following command to check the file type. Log files containing **charset=binary** are binary files.                                                                                                                                                                                    | Enable                |
      |                       |                                                                                                                                                                                                                                                                                                                                                                     |                       |
      |                       | .. code-block::                                                                                                                                                                                                                                                                                                                                                     |                       |
      |                       |                                                                                                                                                                                                                                                                                                                                                                     |                       |
      |                       |    file -i File name                                                                                                                                                                                                                                                                                                                                                |                       |
      |                       |                                                                                                                                                                                                                                                                                                                                                                     |                       |
      |                       | -  If this option is enabled, binary log files that match the ingestion rule will be collected, but only UTF-8 strings are supported. Other strings will be garbled on the LTS console.                                                                                                                                                                             |                       |
      |                       | -  If this option is disabled, binary log files will not be collected.                                                                                                                                                                                                                                                                                              |                       |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Log File Code         | Select the storage format of characters in log files. You can select UTF-8. Set the encoding format properly to ensure that log content can be correctly read and parsed, preventing garbled characters or data damage.                                                                                                                                             | UTF-8                 |
      |                       |                                                                                                                                                                                                                                                                                                                                                                     |                       |
      |                       | UTF-8 encoding is a variable-length encoding mode and represents Unicode character sets.                                                                                                                                                                                                                                                                            |                       |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Collection Policy     | Set whether ICAgent reads a file from the end or the beginning when collecting new log files.                                                                                                                                                                                                                                                                       | Incremental           |
      |                       |                                                                                                                                                                                                                                                                                                                                                                     |                       |
      |                       | -  **Incremental**: When collecting a new file, ICAgent reads the file from the end of the file.                                                                                                                                                                                                                                                                    |                       |
      |                       | -  **All**: When collecting a new file, ICAgent reads the file from the beginning of the file.                                                                                                                                                                                                                                                                      |                       |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Custom Metadata       | -  If this option is disabled, the ICAgent system's default fields are used to report logs to LTS. You do not need to and cannot configure the fields.                                                                                                                                                                                                              | Enable                |
      |                       |                                                                                                                                                                                                                                                                                                                                                                     |                       |
      |                       | -  If this option is enabled, ICAgent will report logs based on your selected built-in fields and fields created with custom key-value pairs.                                                                                                                                                                                                                       |                       |
      |                       |                                                                                                                                                                                                                                                                                                                                                                     |                       |
      |                       |    **Built-in Fields**: Select built-in fields as required.                                                                                                                                                                                                                                                                                                         |                       |
      |                       |                                                                                                                                                                                                                                                                                                                                                                     |                       |
      |                       |    **Custom Key-Value Pairs**: Click **Add** and set a key and value.                                                                                                                                                                                                                                                                                               |                       |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. Configure the log format and time by referring to :ref:`Table 3 <lts_04_1031__en-us_topic_0000001118501736_table18406251941>`.

   .. _lts_04_1031__en-us_topic_0000001118501736_table18406251941:

   .. table:: **Table 3** Log collection settings

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                         |
      +===================================+=====================================================================================================================================================================================================================================================================================================================================================+
      | Log Format                        | -  **Single-line**: Each log line is displayed as a single log event.                                                                                                                                                                                                                                                                               |
      |                                   | -  **Multi-line**: Multiple lines of exception logs can be displayed as a single log event and each line of regular logs is displayed as a log event. This is helpful when you check logs to locate problems.                                                                                                                                       |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Log Time                          | **System time**: log collection time by default. It is displayed at the beginning of each log event.                                                                                                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                                                                                                                                                     |
      |                                   | -  Log collection time is the time when logs are collected and sent by ICAgent to LTS.                                                                                                                                                                                                                                                              |
      |                                   | -  Log printing time is the time when logs are printed. ICAgent collects and sends logs to LTS every second.                                                                                                                                                                                                                                        |
      |                                   | -  Restriction on log collection time: Logs are collected within 24 hours before and after the system time.                                                                                                                                                                                                                                         |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                                   | **Time wildcard**: You can set a time wildcard so that ICAgent will look for the log printing time as the beginning of a log event.                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                                                                                     |
      |                                   | -  If the time format in a log event is **2019-01-01 23:59:59.011**, the time wildcard should be set to **YYYY-MM-DD hh:mm:ss.SSS**.                                                                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                                                                                                                                                     |
      |                                   | -  If the time format in a log event is **19-1-1 23:59:59.011**, the time wildcard should be set to **YY-M-D hh:mm:ss.SSS**.                                                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                                                                                                                     |
      |                                   |    If a log event does not contain year information, ICAgent regards it as printed in the current year.                                                                                                                                                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                                                                                                                     |
      |                                   | Example:                                                                                                                                                                                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                                                                                                                                                                     |
      |                                   | .. code-block::                                                                                                                                                                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                                                                                                                     |
      |                                   |    YY   - year (19)                                                                                                                                                                                                                                                                                                                                 |
      |                                   |    YYYY - year (2019)                                                                                                                                                                                                                                                                                                                               |
      |                                   |    M    - month (1)                                                                                                                                                                                                                                                                                                                                 |
      |                                   |    MM   - month (01)                                                                                                                                                                                                                                                                                                                                |
      |                                   |    D    - day (1)                                                                                                                                                                                                                                                                                                                                   |
      |                                   |    DD   - day (01)                                                                                                                                                                                                                                                                                                                                  |
      |                                   |    hh   - hours (23)                                                                                                                                                                                                                                                                                                                                |
      |                                   |    mm   - minutes (59)                                                                                                                                                                                                                                                                                                                              |
      |                                   |    ss   - seconds (59)                                                                                                                                                                                                                                                                                                                              |
      |                                   |    SSS - millisecond (999)                                                                                                                                                                                                                                                                                                                          |
      |                                   |    hpm     - hours (03PM)                                                                                                                                                                                                                                                                                                                           |
      |                                   |    h:mmpm    - hours:minutes (03:04PM)                                                                                                                                                                                                                                                                                                              |
      |                                   |    h:mm:sspm  - hours:minutes:seconds (03:04:05PM)                                                                                                                                                                                                                                                                                                  |
      |                                   |    hh:mm:ss ZZZZ (16:05:06 +0100)                                                                                                                                                                                                                                                                                                                   |
      |                                   |    hh:mm:ss ZZZ  (16:05:06 CET)                                                                                                                                                                                                                                                                                                                     |
      |                                   |    hh:mm:ss ZZ   (16:05:06 +01:00)                                                                                                                                                                                                                                                                                                                  |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Log Segmentation                  | This parameter needs to be specified if the **Log Format** is set to **Multi-line**. **By generation time** indicates that a time wildcard is used to detect log boundaries, whereas **By regular expression** indicates that a regular expression is used.                                                                                         |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | By regular expression             | You can set a regular expression to look for a specific pattern to indicate the beginning of a log event. This parameter needs to be specified when you select **Multi-line** for **Log Format** and **By regular expression** for **Log Segmentation**.                                                                                            |
      |                                   |                                                                                                                                                                                                                                                                                                                                                     |
      |                                   | The time wildcard and regular expression will look for the specified pattern right from the beginning of each log line. If no match is found, the system time, which may be different from the time in the log event, is used. In general cases, you are advised to select **Single-line** for **Log Format** and **System time** for **Log Time**. |
      |                                   |                                                                                                                                                                                                                                                                                                                                                     |
      |                                   | ICAgent supports only RE2 regular expressions. For details, see `Syntax <https://github.com/google/re2/wiki/syntax>`__.                                                                                                                                                                                                                             |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Next: Index Settings**.

.. _lts_04_1031__en-us_topic_0000001118501736_section18351555203314:

Step 4: Configure Indexing
--------------------------

An index is a storage structure used to query log data. Configuring indexing makes log searches and analysis faster and easier. Different index settings generate different query and analysis results. Configure index settings to fit your service requirements.

-  If you do not want to query or analyze logs using specific fields, you can skip configuring indexing when configuring log ingestion. This will not affect log collection. You can also configure indexing after creating the log ingestion configuration. However, index settings will only apply to newly ingested logs. If you choose to skip this step, retain the default settings on the **Index Settings** page and click **Skip and Submit**. The message "Logs ingested" will appear.

-  To query or analyze logs using specific fields, configure indexing on the **Index Settings** page when creating an ingestion configuration.

   On this page, click **Auto Configure** to have LTS generate index fields based on the first log event in the last 15 minutes or common system reserved fields (such as **hostIP**, **hostName**, and **pathFile**), and manually add structured fields. After completing the settings, click **Submit**. The message "Logs ingested" will appear. **You can also adjust the index settings after the ingestion configuration is created. However, the changes will only affect newly ingested logs.**

.. _lts_04_1031__en-us_topic_0000001118501736_section9751116142720:

Step 5: Complete the Ingestion Configuration
--------------------------------------------

The created ingestion configuration will be displayed.

-  Click its name to view its details.
-  Click **Modify** in the **Operation** column to modify the ingestion configuration.
-  Click **More** > **Configure Tag** in the **Operation** column to add a tag.
-  Click **More** > **Copy** in the **Operation** column to copy the ingestion configuration.
-  Click **Delete** in the **Operation** column to delete the ingestion configuration.

   .. warning::

      Deleting an ingestion configuration may lead to log collection failures, potentially resulting in service exceptions related to user logs. In addition, the deleted ingestion configuration cannot be restored. Exercise caution when performing this operation.

-  To stop log collection of an ingestion configuration, toggle off the switch in the **Ingestion Configuration** column to disable the configuration. To restart log collection, toggle on the switch in the **Ingestion Configuration** column.

   .. warning::

      Disabling an ingestion configuration may lead to log collection failures, potentially resulting in service exceptions related to user logs. Exercise caution when performing this operation.

.. _lts_04_1031__en-us_topic_0000001118501736_section124378505151:

Setting Multiple Ingestion Configurations in a Batch
----------------------------------------------------

You can set multiple ingestion configurations for multiple scenarios in a batch, avoiding repetitive setups.

#. On the **Ingestion Management** page, click **Batch Create** to go to the configuration details page.

   a. **Ingestion Type**: Select **ECS (Elastic Cloud Server)**.
   b. **Rule List**:

      -  Enter the number of ingestion configurations in the text box and click **Add**.
      -  Enter a rule name under **Configuration Items** on the right. You can also double-click the name of the ingestion configuration on the left to replace it with a custom name after setting the configuration items. A rule name can contain 1 to 64 characters, including only letters, digits, hyphens (-), underscores (_), and periods (.). It cannot start with a period or underscore or end with a period.
      -  To copy an ingestion configuration, move the cursor to it and click |image1|.
      -  To delete an ingestion configuration, move the cursor to it and click |image2|. In the displayed dialog box, click **Yes**.

   c. **Configuration Items**:

      -  The ingestion configurations are displayed on the left. You can add up to 99 more configurations.
      -  The ingestion configuration items are displayed on the right. Set them by referring to :ref:`Step 3: Configure the Collection <lts_04_1031__en-us_topic_0000001118501736_section196913102330>`.
      -  After an ingestion configuration is complete, you can click **Apply to Other Configurations** to copy its settings to other configurations.

#. Click **Check Parameters**. After the check is successful, click **Submit**.

   The added ingestion configurations will be displayed on the **Ingestion Management** page after the batch creation is successful.

#. (Optional) Perform the following operations on ingestion configurations:

   -  Select multiple existing ingestion configurations and click **Edit**. On the displayed page, select an ingestion type to modify the corresponding ingestion configurations.
   -  Select multiple disabled ingestion configurations, click **Enable/Disable Ingestion Configuration**, and select **Enable** to enable them in a batch.
   -  Select multiple enabled ingestion configurations, click **Enable/Disable Ingestion Configuration**, and select **Disable**. Logs will not be collected for disabled ingestion configurations. Exercise caution when disabling these configurations.
   -  Select multiple existing ingestion configurations and click **Delete**.

.. |image1| image:: /_static/images/en-us_image_0000002224771849.png
.. |image2| image:: /_static/images/en-us_image_0000002189491442.png
