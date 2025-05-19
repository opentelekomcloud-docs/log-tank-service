:original_name: lts_04_1031.html

.. _lts_04_1031:

Ingesting ECS Text Logs to LTS
==============================

Elastic Cloud Server (ECS) provides scalable, on-demand cloud servers to build secure, flexible, and efficient environment for your applications.

After you configure ECS log ingestion, ICAgent collects logs from ECSs (hosts) based on your specified rules, and sends the logs to LTS by log stream. You can view and analyze these logs on the LTS console for improving host running stability and information security.

Perform the following steps to complete the ingestion configuration:

#. :ref:`Step 1: Select a Log Stream <lts_04_1031__en-us_topic_0000001118501736_section249910285303>`
#. :ref:`Step 2: (Optional) Select a Host Group <lts_04_1031__en-us_topic_0000001118501736_section1014910157328>`
#. :ref:`Step 3: Configure the Collection <lts_04_1031__en-us_topic_0000001118501736_section196913102330>`
#. :ref:`Step: Configure Log Structuring <lts_04_1031__en-us_topic_0000001118501736_section1378734643812>`
#. :ref:`Step 4: Configure Indexing <lts_04_1031__en-us_topic_0000001118501736_section18351555203314>`
#. :ref:`Step 5: Complete the Ingestion Configuration <lts_04_1031__en-us_topic_0000001118501736_section9751116142720>`

To collect logs from multiple scenarios, :ref:`set multiple ingestion configurations in a batch <lts_04_1031__en-us_topic_0000001118501736_section124378505151>`.

Prerequisites
-------------

ICAgent has been :ref:`installed <lts_02_0013>` and :ref:`added <lts_02_1033__en-us_topic_0000001118763740_li682633315215>` to the host group.

.. _lts_04_1031__en-us_topic_0000001118501736_section249910285303:

Step 1: Select a Log Stream
---------------------------

#. Log in to the management console and choose **Management & Deployment** > **Log Tank Service**.

#. Choose **Log Ingestion** > **Ingestion Center** in the navigation pane and click **ECS (Elastic Cloud Server)**.

   You can also choose **Log Ingestion** > **Ingestion Management** in the navigation pane and click **Ingest Log**. On the displayed page, choose **ECS (Elastic Cloud Server)**.

#. Select a log group from the **Log Group** drop-down list. If there is no desired log group, click **Create Log Group**. For details, see :ref:`Managing Log Groups <lts_04_0003>`.

#. Select a log stream from the **Log Stream** drop-down list. If there is no desired log stream, click **Create Log Stream**. For details, see :ref:`Managing Log Streams <lts_04_0004>`.

#. Click **Next: (Optional) Select Host Group**.

.. _lts_04_1031__en-us_topic_0000001118501736_section1014910157328:

Step 2: (Optional) Select a Host Group
--------------------------------------

A host group is a virtual group of hosts, allowing you to configure host log collection efficiently. Ensure that you have :ref:`installed ICAgent <lts_02_0013>` on the host where logs need to be collected and :ref:`added it to a host group <lts_02_1033__en-us_topic_0000001118763740_li682633315215>`.

#. In the host group list, select one or more host groups to collect their logs.

   You can skip this step and configure host groups as follows after the ingestion configuration is complete. **However, you are advised to configure host groups during the first ingestion configuration to ensure that the configuration takes effect.**

   -  Choose **Host Management** > **Host Groups** in the navigation pane and associate host groups with ingestion configurations.
   -  Choose **Log Ingestion** > **Ingestion Management** in the navigation pane. In the ingestion configuration list, click **Modify** in the **Operation** column. On the page displayed, select required host groups.

#. If there are no desired host groups, click **Create** above the host group list.

   -  On the **Create Host Group** page displayed, select hosts with ICAgent installed under **Add Host**. For details, see :ref:`Managing Host Groups <lts_02_1033>`.
   -  If the desired host has no ICAgent installed, click **Install ICAgent** under **Add Host**. Select **Intra-region hosts** or **Extra-region hosts** based on the host location and install ICAgent by referring to :ref:`Installing ICAgent (Intra-Region Hosts) <lts_02_0013>`. After ICAgent is installed on the desired host, return to the ECS log ingestion page, click **Create** above the host group list again. The desired host will now be displayed under **Add Host** on the **Create Host Group** page.

#. Click **Next: Configurations**.

.. _lts_04_1031__en-us_topic_0000001118501736_section196913102330:

Step 3: Configure the Collection
--------------------------------

After selecting host groups, configure the collection as follows:

-  Ensure that sensitive information is not collected.
-  If a collection path of a host has been configured in AOM, do not configure the path in LTS.
-  If log files were last modified more than 12 hours earlier than the time when the path is added, the files are not collected.

#. **Collection Configuration Name**: Enter 1 to 64 characters. Only letters, digits, hyphens (-), underscores (_), and periods (.) are allowed. Do not start with a period or underscore, or end with a period.

   If you want to reuse existing collection configurations, click **Import Configuration** next to the text box. On the **Import Configuration** page, select a configuration and click **OK**.

   **Import Old-Edition Configuration**: Import the host ingestion configuration of the old version to the log ingestion of the new version.

   -  If LTS is newly installed and **Import Old-Edition Configuration** is not displayed, you can directly create a configuration without importing the old one.
   -  If LTS is upgraded, **Import Old-Edition Configuration** is displayed. Import the old configuration or create one as required.

#. .. _lts_04_1031__en-us_topic_0000001118501736_li17754123317308:

   **Collection Paths**: Add one or more host paths. LTS will collect logs from these paths. The rules for setting collection paths are as follows:

   -  Logs can be collected recursively. A double asterisk (**) can represent up to 5 directory levels in a path.

      For example, **/var/logs/**/a.log** will match the following logs:

      .. code-block::

         /var/logs/a.log
         /var/logs/1/a.log
         /var/logs/1/2/a.log
         /var/logs/1/2/3/a.log
         /var/logs/1/2/3/4/a.log
         /var/logs/1/2/3/4/5/a.log

      -  **/1/2/3/4/5/** indicates the 5 levels of directories under the **/var/logs** directory. All the **a.log** files found in all these levels of directories will be collected.
      -  Only one double asterisk (**) can be contained in a collection path. For example, **/var/logs/**/a.log** is acceptable but **/opt/test/**/log/*\*** is not.
      -  A collection path cannot begin with a double asterisk (**), such as **/**/test**, to avoid collecting system files.

   -  You can use an asterisk (*) as a wildcard for fuzzy match. The wildcard (*) can represent one or more characters of a directory or file name.

      If a log collection path is similar to **C:\\windows\\system32** but logs cannot be collected, enable Web Application Firewall (WAF) and configure the path again.

      -  Example 1: **/var/logs/*/a.log** will match all **a.log** files found in all directories under the **/var/logs/** directory:

         /var/logs/1/a.log

         /var/logs/2/a.log

      -  Example 2: **/var/logs/service-*/a.log** will match files as follows:

         /var/logs/service-1/a.log

         /var/logs/service-2/a.log

      -  Example 3: **/var/logs/service/a*.log** will match files as follows:

         /var/logs/service/a1.log

         /var/logs/service/a2.log

   -  If the collection path is set to a file name, the corresponding file is collected. Only text files can be collected.

   -  **Add Custom Wrapping Rule**: ICAgent determines whether a file is wrapped based on the file name rule. If your wrapping rule does not comply with the built-in rules, you can add a custom wrap rule to prevent log loss during repeated collection and wrapping.

      The built-in rules are *{basename}{connector}{wrapping identifier}.{suffix}* and *{basename}.{suffix}{connector}{wrapping identifier}*. Connectors can be hyphens (-), periods (.), or underscores (_), wrapping identifiers can contain only non-letter characters, and the suffix can contain only letters.

      A custom wrapping rule consists of *{basename}* and the feature regular expression of the wrapped file. Example: If your log file name is **test.out.log** and the names after wrapping are **test.2024-01-01.0.out.log** and **test.2024-01-01.1.out.log**, configure the collection path to **/opt/*.log**, and add a custom wrapping rule: *{basename}*\ **\\.\\d{4}-\\d{2}-\\d{2}\\.\\d{1}.out.log**.

#. **Allows multiple file collection** (not available to Windows)

   After you enable this function, one host log file can be collected to multiple log streams.

   After you disable this function, each collection path must be unique. That is, the same log file in the same host cannot be collected to different log streams.

#. **Set Collection Filters**: Blacklisted directories or files will not be collected.

   Blacklist filters can be exact matches or wildcard pattern matches. For details, see :ref:`Collection Paths <lts_04_1031__en-us_topic_0000001118501736_li17754123317308>`.

   -  If you blacklist a file or directory that has been set as a collection path in the previous step, the blacklist settings will be used and the file or files in the directory will be filtered out.
   -  If a log has been added to the blacklist, it cannot be collected even if you create a log ingestion task. You can collect it again only after you delete the collection path from the blacklist.
   -  If you specify a directory, all files in the directory are filtered out, but log files in the folders in the directory cannot be filtered out.

#. **Collect Windows Event Logs**: To collect logs from Windows hosts, enable this option and set the following parameters.

   .. table:: **Table 1** Parameters for collecting windows event logs

      +------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                    | Description                                                                                                                                                                                                                                                            |
      +==============================+========================================================================================================================================================================================================================================================================+
      | Log Type                     | Log types include **System**, **Application**, **Security**, and **Startup**.                                                                                                                                                                                          |
      +------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | First Collection Time Offset | If you set this parameter to **7**, logs generated within the seven days before the collection start time are collected. This offset takes effect only for the first collection to ensure that the logs are not repeatedly collected. The maximum value is seven days. |
      +------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Event Level                  | You can filter and collect Windows events based on their severity (**information**, **warning**, **error**, **critical**, and **verbose**). This function is available only to Windows Vista or later.                                                                 |
      +------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Set other configurations.

   .. table:: **Table 2** Other configurations

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                        |
      +===================================+====================================================================================================================================================================================================================================================================================================================================================================+
      | Split Logs                        | -  If log splitting is enabled, logs exceeding the specified size will be split into multiple logs for collection. Specify the size in the range from 500 KB to 1,024 KB. For example, if you set the size to 500 KB, a 600 KB log will be split into a 500 KB log and a 100 KB log. This restriction is applicable to single-line logs only, not multi-line logs. |
      |                                   | -  If log splitting is disabled, when a log exceeds 500 KB, the extra part will be truncated and discarded.                                                                                                                                                                                                                                                        |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Collect Binary Files              | LTS can collect binary files.                                                                                                                                                                                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                    |
      |                                   | Run the **file -i** *File_name* command to view the file type. **charset=binary** indicates that a log file is a binary file.                                                                                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                    |
      |                                   | If this option is enabled, binary log files will be collected, but only UTF-8 strings are supported. Other strings will be garbled on the LTS console.                                                                                                                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                    |
      |                                   | If this option is disabled, binary log files will not be collected.                                                                                                                                                                                                                                                                                                |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Custom Metadata                   | -  If this option is disabled, ICAgent will report logs to LTS based on the default system fields. You do not need to and cannot configure the fields.                                                                                                                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                    |
      |                                   | -  If this option is enabled, ICAgent will report logs based on your selected built-in fields and fields created with custom key-value pairs.                                                                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                    |
      |                                   |    **Built-in Fields**: Select built-in fields as required.                                                                                                                                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                    |
      |                                   |    **Custom Key-Value Pairs**: Click **Add** and set a key and value.                                                                                                                                                                                                                                                                                              |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Configure the log format and time by referring to :ref:`Table 3 <lts_04_1031__en-us_topic_0000001118501736_table18406251941>`.

   .. _lts_04_1031__en-us_topic_0000001118501736_table18406251941:

   .. table:: **Table 3** Log collection settings

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                         |
      +===================================+=====================================================================================================================================================================================================================================================================================================================================================+
      | Log Format                        | -  **Single-line**: Each log line is displayed as a single log event.                                                                                                                                                                                                                                                                               |
      |                                   | -  **Multi-line**: Multiple lines of exception log events can be displayed as a single log event. This is helpful when you check logs to locate problems.                                                                                                                                                                                           |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Log Time                          | **System time**: log collection time by default. It is displayed at the beginning of each log event.                                                                                                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                                                                                                                                                     |
      |                                   | -  Log collection time is the time when logs are collected and sent by ICAgent to LTS.                                                                                                                                                                                                                                                              |
      |                                   | -  Log printing time is the time when logs are printed. ICAgent collects and sends logs to LTS with an interval of 1 second.                                                                                                                                                                                                                        |
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
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _lts_04_1031__en-us_topic_0000001118501736_section1378734643812:

Step: Configure Log Structuring
-------------------------------

#. Configure log structuring. For details, see :ref:`Setting Cloud Structuring Parsing <lts_0821>`.

   If structuring has been configured for the selected log stream, exercise caution when deleting it.

#. Click **Next: Index Settings**.

.. _lts_04_1031__en-us_topic_0000001118501736_section18351555203314:

Step 4: Configure Indexing
--------------------------

#. Configure indexing. For details, see :ref:`Setting Indexes <lts_05_0008>`.
#. Click **Submit**.

.. _lts_04_1031__en-us_topic_0000001118501736_section9751116142720:

Step 5: Complete the Ingestion Configuration
--------------------------------------------

The created ingestion configuration will be displayed.

-  Click its name to view its details.

-  Click **Modify** in the **Operation** column to modify the ingestion configuration.

-  Click **Configure Tag** in the **Operation** column to add a tag.

-  Click **More** > **Copy** in the **Operation** column to copy the ingestion configuration.

-  Click **More** > **Delete** in the **Operation** column to delete the ingestion configuration.

   Deleting an ingestion configuration may lead to log collection failures, potentially resulting in service exceptions related to user logs. In addition, the deleted ingestion configuration cannot be restored. Exercise caution when performing this operation.

.. _lts_04_1031__en-us_topic_0000001118501736_section124378505151:

Setting Multiple Ingestion Configurations in a Batch
----------------------------------------------------

You can set multiple ingestion configurations for multiple scenarios in a batch, avoiding repetitive setups.

#. On the **Ingestion Management** page, click **Batch Ingest** to go to the details page. For details, see :ref:`Table 4 <lts_04_1031__en-us_topic_0000001118501736_table960663620>`.

   .. _lts_04_1031__en-us_topic_0000001118501736_table960663620:

   .. table:: **Table 4** Adding configurations in batches

      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Type                  | Parameter             | Description                                                                                                                                                                                        |
      +=======================+=======================+====================================================================================================================================================================================================+
      | Basic Settings        | Ingestion Type        | Select **ECS (Elastic Cloud Server)**.                                                                                                                                                             |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                       | Configurations to Add | Enter the number of ingestion configurations in the text box and click **Add**.                                                                                                                    |
      |                       |                       |                                                                                                                                                                                                    |
      |                       |                       | A maximum of 100 ingestion configurations can be added, including the one already exists under **Ingestion Settings** by default. Therefore, you can add up to 99 more.                            |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Ingestion Settings    | Configuration List    | a. The ingestion configurations are displayed on the left. You can add up to 99 more configurations.                                                                                               |
      |                       |                       | b. The ingestion configuration items are displayed on the right. Set them by referring to :ref:`Step 3: Configure the Collection <lts_04_1031__en-us_topic_0000001118501736_section196913102330>`. |
      |                       |                       | c. After an ingestion configuration is complete, you can click **Apply to Other Configurations** to copy its settings to other configurations.                                                     |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Check Parameters**. After the check is successful, click **Submit**.

   The added ingestion configurations will be displayed on the **Ingestion Management** page after the batch creation is successful.

#. (Optional) Perform the following operations on ingestion configurations:

   -  Select multiple existing ingestion configurations and click **Edit**. On the displayed page, select an ingestion type to modify the corresponding ingestion configurations.
   -  Select multiple existing ingestion configurations and click **Enable** or **Disable**. Logs will not be collected for disabled ingestion configurations.
   -  Select multiple existing ingestion configurations and click **Delete**.
