:original_name: lts_04_0062.html

.. _lts_04_0062:

Configuring Log Alarm Rules
===========================

LTS allows you to set alarm rules for log data in log streams to monitor service status in real time. Currently, a maximum of 200 alarm rules can be created for each account.

You can create multiple alarm rules in a batch. For details, see :ref:`Configuring Multiple Alarm Rules <lts_04_0062__en-us_topic_0000001149151742_section259755232212>`.

Prerequisites
-------------

-  A log group and stream have been created. For details, see :ref:`Managing Log Groups <lts_04_0003>` and :ref:`Managing Log Streams <lts_04_0004>`.
-  To use field indexing for searching, analyzing, and collecting statistics on logs ingested to LTS, ensure that index settings are properly configured. Correct index settings help you efficiently query and analyze log data and configure log alarm rules based on specific fields, such as the log severity, error code, and response time.

Configuring a Keyword Alarm Rule
--------------------------------

LTS allows you to collect statistics on log keywords in log streams and set alarm rules to monitor them. By checking the number of keyword occurrences in a specified period, you can have a real-time view of the service running.

#. Log in to the management console and choose **Management & Deployment** > **Log Tank Service**.

#. Choose **Log Alarms** in the navigation pane.

#. Click the **Alarm Rules** tab.

#. Click **Create**. The **Create Alarm Rule** right panel is displayed.

#. Configure alarm rule parameters.

   .. table:: **Table 1** Keyword alarm rule parameters

      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Category              | Parameter             | Description                                                                                                                                                                                                                                                                                                                                          |
      +=======================+=======================+======================================================================================================================================================================================================================================================================================================================================================+
      | Basic Info            | Rule Name             | Define a name for your alarm rule based on service requirements. After the rule is created, move the cursor to the rule name in the rule list to view both the rule name and the original rule name. You can modify the rule name, but cannot modify the original rule name (defined during rule creation).                                          |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                      |
      |                       |                       | **Naming rules:**                                                                                                                                                                                                                                                                                                                                    |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                      |
      |                       |                       | Use only letters, digits, hyphens (-), and underscores (_). Do not start or end with a hyphen or underscore.                                                                                                                                                                                                                                         |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Basic Info            | Description           | Description of the rule. Enter up to 128 characters.                                                                                                                                                                                                                                                                                                 |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Statistical Analysis  | Statistics            | **By keyword**: applicable to scenarios where keywords are used to search for and configure log alarms.                                                                                                                                                                                                                                              |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                      |
      |                       |                       | After an alarm rule is created, the statistics type cannot be changed. Plan the statistics type based on service requirements.                                                                                                                                                                                                                       |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                       | Query Condition       | **Log Group Name**: Select a log group.                                                                                                                                                                                                                                                                                                              |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                       |                       | **Log Stream Name**: Select a log stream.                                                                                                                                                                                                                                                                                                            |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                      |
      |                       |                       | If a log group contains more than one log stream, you can select multiple log streams when creating a keyword alarm rule.                                                                                                                                                                                                                            |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                       |                       | **Query Time Range**: Specify the query period of the statement. It is one period earlier than the current time. For example, if **Query Time Range** is set to one hour and the current time is 9:00, the query statement period is 8:00-9:00.                                                                                                      |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                      |
      |                       |                       | -  The value ranges from 1 to 60 in the unit of minutes.                                                                                                                                                                                                                                                                                             |
      |                       |                       | -  The value ranges from 1 to 24 in the unit of hours.                                                                                                                                                                                                                                                                                               |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                       |                       | **Keywords**: Enter log keywords that can be queried on the **Log Search** tab page. LTS monitors logs in the log stream based on these keywords.                                                                                                                                                                                                    |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                      |
      |                       |                       | Exact and fuzzy matches are supported. Enter up to 1,024 characters. For details about how to set keyword search, see :ref:`Using Search Syntax <lts_05_0111>`.                                                                                                                                                                                      |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                      |
      |                       |                       | In the index settings, **Case-Sensitive** is disabled by default. This means that keywords are case insensitive. If you enable this option, alarm keywords you enter will be case-sensitive for matching. For details, see :ref:`Configuring Log Indexing <lts_05_0008>`.                                                                            |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                       | Check Rule            | Configure a condition that will trigger the alarm.                                                                                                                                                                                                                                                                                                   |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                      |
      |                       |                       | -  **Matching Log Events**: When the number of log events that contain the configured keywords reaches the specified value, an alarm is triggered. Four comparison operators are supported: greater than (**>**), greater than or equal to (**>=**), less than (**<**), and less than or equal to (**<=**).                                          |
      |                       |                       | -  The alarm severity can be **Critical** (default), **Major**, **Minor**, or **Info**.                                                                                                                                                                                                                                                              |
      |                       |                       | -  The number of queries refers to the number of occurrences of the **Query Frequency** set in **Advanced Settings**. The number of times the condition is met refers to the number of times that the keyword appears. The number of queries must be greater than or equal to the number of times the condition must be met. Number of queries: 1-10 |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Advanced Settings     | Query Frequency       | Options:                                                                                                                                                                                                                                                                                                                                             |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                      |
      |                       |                       | -  **Hourly**: The query is performed at the top of each hour.                                                                                                                                                                                                                                                                                       |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                      |
      |                       |                       | -  **Daily**: The query is performed at a specific time every day.                                                                                                                                                                                                                                                                                   |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                      |
      |                       |                       | -  **Weekly**: The query is performed at a specific time on a specific day every week.                                                                                                                                                                                                                                                               |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                      |
      |                       |                       | -  **Custom interval**: You can specify the interval from 1 minute to 60 minutes or from 1 hour to 24 hours. For example, if the current time is 9:00 and the **Custom interval** is set to 5 minutes, the first query is at 9:00, the second query is at 9:05, the third query is at 9:10, and so on.                                               |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                      |
      |                       |                       |    When the query time range is larger than 1 hour, the custom interval must be at least 5 minutes.                                                                                                                                                                                                                                                  |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                      |
      |                       |                       | -  **CRON**: The query task is executed according to :ref:`Cron Expression <lts_04_0062__en-us_topic_0000001149151742_section818593212158>`. Cron expressions use the 24-hour format and are precise down to the minute.                                                                                                                             |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Advanced Settings     | Alarm Restored When   | Configure a policy for sending an alarm restoration notification.                                                                                                                                                                                                                                                                                    |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                      |
      |                       |                       | If alarm restoration notification is enabled and the trigger condition has not been met for the specified number of last queries, an alarm restoration notification is sent.                                                                                                                                                                         |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                      |
      |                       |                       | Number of last queries: 1-10                                                                                                                                                                                                                                                                                                                         |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Advanced Settings     | Notify When           | -  **Alarm triggered**: Specify whether to send a notification when an alarm is triggered. If this option is enabled, a notification will be sent when the trigger condition is met. If disabled, no notifications will be sent, even if the trigger condition is met.                                                                               |
      |                       |                       | -  **Alarm restored**: Specify whether to send a notification when an alarm is restored. If this option is enabled, a notification will be sent when the restoration policy is met. If disabled, no notifications will be sent, even if the restoration policy is met.                                                                               |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Advanced Settings     | Frequency             | You can select **Immediate**, **Every 5 minutes**, **Every 10 minutes**, **Every 15 minutes**, **Every 30 minutes**, **Every hour**, **Every 3 hours**, or **Every 6 hours** to send alarms.                                                                                                                                                         |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                      |
      |                       |                       | **Immediate** indicates that a notification is sent once an alarm is generated. **Every 10 minutes** indicates that the minimum interval between two notifications is 10 minutes, preventing alarm storms.                                                                                                                                           |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Advanced Settings     | Alarm Action Rules    | Select a desired rule from the drop-down list.                                                                                                                                                                                                                                                                                                       |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                      |
      |                       |                       | If no rule is available, click **Create Alarm Action Rule** on the right.                                                                                                                                                                                                                                                                            |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Advanced Settings     | Language              | Select the alarm language.                                                                                                                                                                                                                                                                                                                           |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Advanced Settings     | Tag                   | Tag alarm rules as required. Click **Add Tags** and enter a tag key and value.                                                                                                                                                                                                                                                                       |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                      |
      |                       |                       | To add more tags, repeat this step. A maximum of 20 tags can be added.                                                                                                                                                                                                                                                                               |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                      |
      |                       |                       | **Tag key restrictions:**                                                                                                                                                                                                                                                                                                                            |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                      |
      |                       |                       | -  A tag key can contain letters, digits, spaces, and special characters ``(_.:=+-@),`` but cannot start or end with a space or start with **\_sys\_**.                                                                                                                                                                                              |
      |                       |                       | -  A tag key can contain up to 128 characters.                                                                                                                                                                                                                                                                                                       |
      |                       |                       | -  Each tag key must be unique.                                                                                                                                                                                                                                                                                                                      |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                      |
      |                       |                       | **Tag value restrictions:**                                                                                                                                                                                                                                                                                                                          |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                      |
      |                       |                       | -  A tag value can contain letters, digits, spaces, and the following special characters: \_.:=+-@                                                                                                                                                                                                                                                   |
      |                       |                       | -  A tag value can contain up to 255 characters.                                                                                                                                                                                                                                                                                                     |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                      |
      |                       |                       | **Deleting a tag:**                                                                                                                                                                                                                                                                                                                                  |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                      |
      |                       |                       | .. warning::                                                                                                                                                                                                                                                                                                                                         |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                      |
      |                       |                       |    Deleted tags cannot be recovered.                                                                                                                                                                                                                                                                                                                 |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                      |
      |                       |                       | To delete a tag, click **Delete** in the **Operation** column of the tag.                                                                                                                                                                                                                                                                            |
      +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

   After an alarm rule is created, its status is **Enabled** by default. After the alarm rule is disabled, the alarm status is **Disabled**. After the alarm rule is disabled temporarily, the alarm status is **Temporarily closed to May 30, 2023 16:21:24.000 GMT+08:00**. (The time is for reference only.)

   When the alarm rule is enabled, an alarm will be triggered if the alarm rule is met. When it is disabled, an alarm will not be triggered even if the alarm rule is met.

.. _lts_04_0062__en-us_topic_0000001149151742_section259755232212:

Configuring Multiple Alarm Rules
--------------------------------

You can create multiple alarm rules in a batch.

#. On the **Alarm Rules** tab page, import alarm rules in a batch.

   a. Click **Import/Export** > **Import**. The **Import Alarm Rule** dialog box is displayed.
   b. Click **Download Alarm Template.xlsx** to download the template to the local PC and fill in the template.
   c. Click **Select File** and select the file that has been filled in.
   d. Check the imported rule information and click **Import**.
   e. After the import is successful, view the alarm rule details in the rule list.

#. Click **Batch Create/Edit**. The **Create or Edit Alarm Rules** page is displayed.
#. Under **Rule List**, enter the number of alarm rules and click **Add**.

   -  A maximum of 200 alarm rules can be added, including the one already exists under **Rule List** by default. Therefore, you can add up to 199 more.
   -  Enter a rule name under **Configuration Items** on the right. You can also double-click the name of the alarm rule on the left to replace it with a custom name after setting the configuration items. A rule name can contain 1 to 128 characters, including only letters, digits, hyphens (-), and underscores (_). It cannot start or end with a hyphen or underscore.
   -  To copy an alarm rule, move the cursor to it and click |image1|.
   -  To delete an alarm rule, move the cursor to it and click |image2|. In the displayed dialog box, click **OK**.
   -  If you enter an original rule name already in use, after you click **Submit**, the modification will apply to the existing rule, instead of creating a new one. After a rule is created, its statistics type cannot be modified. The modification will fail if you try to modify the statistics type.
   -  To import alarm rules in a batch, click **Import** under **Rule List**. On the **Import Alarm Rule** page that is displayed, download the alarm rule template. Fill in the template on your PC. Back to the **Import Alarm Rule** page, click **Select File**, select the template, and click **Import**.

#. Under **Configuration Items**, set the alarm rules.
#. Click **Check Parameters**.
#. After the check is successful, click **Submit**.

   -  After setting an alarm rule, you can click **Apply to Other Rules** to copy its settings to other alarm rules.
   -  The created alarm rules will be displayed on the **Alarm Rules** tab page after the batch creation is successful.

Follow-up Operations on Alarm Rules
-----------------------------------

After creating an alarm rule, you can modify, enable, disable, copy, or delete it. Exercise caution when performing these operations.

-  You can perform the following operations on a single alarm rule.

   Modifying an alarm rule: Click **Modify** in the **Operation** column of the target alarm rule. On the displayed page, modify the rule name, query condition, and check rule, and click **OK**.

   Temporarily disabling an alarm rule: Click **More** > **Disable Temporarily** in the **Operation** column of the target alarm rule, and click **OK**.

   Copying an alarm rule: Click **More** > **Copy** in the **Operation** column of the target alarm rule.

   Deleting an alarm rule: Click **Delete** in the **Operation** column of the target alarm rule. In the displayed dialog box, click **OK**.

   .. note::

      Deleted alarm rules cannot be recovered. Exercise caution when performing this operation.

-  **Restoration Notification**: If this option is enabled, a notification will be sent when the restoration policy is met. If disabled, no notifications will be sent, even if the restoration policy is met.

-  **Rule Status**: An alarm rule takes effect only when the switch in this column is toggled on. If this switch is toggled off, the alarm rule is invalid.

-  **Configure Tag**: In the **Operation** column of the target alarm rule, choose **More** > **Configure Tag**. On the displayed page, add tags.

-  After selecting multiple alarm rules, you can perform the following operations on them: **Enable**, **Disable**, **Disable Temporarily**, **Re-Enable**, **Enable Restoration Notification**, **Disable Restoration Notification**, **Delete**, **Import**, **Export selected data to an XLSX file**, and **Export all data to an XLSX file**.

-  You can hover over a rule name to see both the current and original names. The original rule name cannot be changed.

.. _lts_04_0062__en-us_topic_0000001149151742_section818593212158:

Cron Expression
---------------

A cron expression consists of the following six fields: minute (0-59), hour (0-23), day (1-31), month (1-12), and day of the week (0-6: 0 indicates Sunday and 6 indicates Saturday). These fields are separated by spaces and are mandatory. In addition to the basic values, you can use special characters to output more complex time rules. Examples:

-  The query starts from 00:00 and is performed every 10 minutes at 00:00, 00:10, 00:20, 00:30, 00:40, 00:50, 01:00, and so on. **\*** indicates any value of the field, and **/** indicates the interval between specified time points.

   .. code-block::

      0/10 * * * *

   For example, if the current time is 16:37, the next query is at 16:50.

-  The query starts from 00:00 and is performed every 5 hours at 00:00, 05:00, 10:00, 15:00, 20:00, and so on. **\*** indicates any value of the field, and **/** indicates the interval between specified time points.

   .. code-block::

      0 0/5 * * *

   For example, if the current time is 16:37, the next query is at 20:00.

-  The query is performed at 14:00 every day.

   .. code-block::

      0 14 * * *

-  The query is performed at 00:00 on the 10th day of every month.

   .. code-block::

      0 0 10 * *

.. |image1| image:: /_static/images/en-us_image_0000002190046046.png
.. |image2| image:: /_static/images/en-us_image_0000002225246441.png
