:original_name: lts_06_0011.html

.. _lts_06_0011:

Creating a Message Template on the LTS Console
==============================================

A message template defines the format of alarm notification messages sent to subscribers. LTS provides built-in message templates. Subscribers can select templates based on protocols. If the template of a specified protocol does not exist, the built-in template of that protocol is used to send messages to subscribers. When using a message template to send alarm notification messages, the system automatically replaces the template variables with the content in the alarm rule.

Creating a Message Template
---------------------------

#. Log in to the management console and choose **Management & Deployment** > **Log Tank Service**.

#. Choose **Log Alarms** in the navigation pane and click the **Alarm Action Rules** tab.

   By default, LTS provides the following built-in message templates. If no message content is configured in your selected template, LTS uses a built-in template instead.

   -  **keywords_template** (English): keyword alarm template

#. Click **Create** on the **Message Templates** tab page. On the displayed page, set the required parameters.

   -  The email content supports HTML tags and message preview.
   -  You can create up to 100 message templates for AOM and LTS. If there are already 100 templates, delete unnecessary templates before creating a new one.

   .. _lts_06_0011__en-us_topic_0000001159394194_table13241557318:

   .. table:: **Table 1** Message template parameters

      +---------------------+-------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+
      | Parameter           | Description                                     | Verification Rule                                                                                                                                                                                                                      | Example           |
      +=====================+=================================================+========================================================================================================================================================================================================================================+===================+
      | Template Name       | Message template name.                          | Include digits, letters, underscores (_), and hyphens (-). Do not start or end with an underscore or hyphen. (Max. 100 characters)                                                                                                     | LTS-test          |
      +---------------------+-------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+
      | Description         | Description of the template.                    | Include digits, letters, and underscores (_). Do not start or end with an underscore. (Max. 1,024 characters)                                                                                                                          | ``-``             |
      +---------------------+-------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+
      | Message Header      | Default message header to be added in messages. | -  English                                                                                                                                                                                                                             | -  "Dear user,"   |
      +---------------------+-------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+
      | Notification method | Notification method.                            | -  Email                                                                                                                                                                                                                               | ``-``             |
      |                     |                                                 | -  SMS                                                                                                                                                                                                                                 |                   |
      |                     |                                                 | -  HTTP/HTTPS                                                                                                                                                                                                                          |                   |
      +---------------------+-------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+
      | Topic               | Message topic.                                  | Customize the topic name or use variables. (Max. 512 characters)                                                                                                                                                                       | test              |
      |                     |                                                 |                                                                                                                                                                                                                                        |                   |
      |                     |                                                 | Only email templates need a topic name.                                                                                                                                                                                                |                   |
      +---------------------+-------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+
      | Body                | Message content.                                | **Add Variable**                                                                                                                                                                                                                       | ${event_name}     |
      |                     |                                                 |                                                                                                                                                                                                                                        |                   |
      |                     |                                                 | -  Original rule name: *${event_name}*                                                                                                                                                                                                 | ${event_severity} |
      |                     |                                                 | -  Alarm severity: *${event_severity}*                                                                                                                                                                                                 |                   |
      |                     |                                                 | -  Occurrence time: *${starts_at}*                                                                                                                                                                                                     | ${starts_at}      |
      |                     |                                                 | -  Occurrence region: *${region_name}*                                                                                                                                                                                                 |                   |
      |                     |                                                 | -  Account: *${domain_name}*                                                                                                                                                                                                           | ${region_name}    |
      |                     |                                                 | -  Alarm source: *$event.metadata.resource_provider*                                                                                                                                                                                   |                   |
      |                     |                                                 | -  Resource type: *$event.metadata.resource_type*                                                                                                                                                                                      |                   |
      |                     |                                                 | -  Resource ID: *${resources}*                                                                                                                                                                                                         |                   |
      |                     |                                                 | -  Alarm status: *$event.annotations.alarm_status*                                                                                                                                                                                     |                   |
      |                     |                                                 | -  Expression: *$event.annotations.condition_expression*                                                                                                                                                                               |                   |
      |                     |                                                 | -  Current value: *$event.annotations.current_value*                                                                                                                                                                                   |                   |
      |                     |                                                 | -  Statistical period: *$event.annotations.frequency*                                                                                                                                                                                  |                   |
      |                     |                                                 | -  Rule name: *$event.annotations.alarm_rule_alias*                                                                                                                                                                                    |                   |
      |                     |                                                 | -  Frequency: *$event.annotations.notification_frequency*                                                                                                                                                                              |                   |
      |                     |                                                 | -  Original log group name: *$event.annotations.results[0].log_group_name*                                                                                                                                                             |                   |
      |                     |                                                 | -  Original log stream name: *$event.annotations.results[0].log_stream_name*                                                                                                                                                           |                   |
      |                     |                                                 | -  Variables supported by keyword alarms:                                                                                                                                                                                              |                   |
      |                     |                                                 |                                                                                                                                                                                                                                        |                   |
      |                     |                                                 |    a. Query time: *$event.annotations.results[0].time*                                                                                                                                                                                 |                   |
      |                     |                                                 |                                                                                                                                                                                                                                        |                   |
      |                     |                                                 |    b. Query logs: (The maximum log size is 2 KB. If a log exceeds 2 KB, the extra part will be truncated and discarded.)                                                                                                               |                   |
      |                     |                                                 |                                                                                                                                                                                                                                        |                   |
      |                     |                                                 |       *$event.annotations.results[0].raw_results*                                                                                                                                                                                      |                   |
      |                     |                                                 |                                                                                                                                                                                                                                        |                   |
      |                     |                                                 |    c. Query URL:                                                                                                                                                                                                                       |                   |
      |                     |                                                 |                                                                                                                                                                                                                                        |                   |
      |                     |                                                 |       *$event.annotations.results[0].url*                                                                                                                                                                                              |                   |
      |                     |                                                 |                                                                                                                                                                                                                                        |                   |
      |                     |                                                 |    d. Log group/stream name: *$event.annotations.results[0].resource_id*                                                                                                                                                               |                   |
      |                     |                                                 |                                                                                                                                                                                                                                        |                   |
      |                     |                                                 |       Only the original name of the log group or log stream created for the first time can be added. The modified log group or log stream name cannot be added.                                                                        |                   |
      |                     |                                                 |                                                                                                                                                                                                                                        |                   |
      |                     |                                                 |    e. Enterprise project ID of the log stream: *$event.annotations.results[0].eps_id*                                                                                                                                                  |                   |
      |                     |                                                 |                                                                                                                                                                                                                                        |                   |
      |                     |                                                 |    f. Query custom field: *$event.annotations.results[0].fields.xxx*                                                                                                                                                                   |                   |
      |                     |                                                 |                                                                                                                                                                                                                                        |                   |
      |                     |                                                 |       *xxx* indicates the structured fields and system fields (such as **hostIP** and **hostName**) of the raw logs. The maximum size of a log field is 1 KB. If a field exceeds 1 KB, the extra part will be truncated and discarded. |                   |
      |                     |                                                 |                                                                                                                                                                                                                                        |                   |
      |                     |                                                 | **Copy from Existing**                                                                                                                                                                                                                 |                   |
      |                     |                                                 |                                                                                                                                                                                                                                        |                   |
      |                     |                                                 | -  keywords_template                                                                                                                                                                                                                   |                   |
      |                     |                                                 | -  Custom templates (created with variables)                                                                                                                                                                                           |                   |
      +---------------------+-------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------+

#. When the configuration is complete, click **OK**.

Modifying a Message Template
----------------------------

#. In the message template list, click **Modify** in the row that contains the target template, and modify the template according to :ref:`Table 1 <lts_06_0011__en-us_topic_0000001159394194_table13241557318>`. The template name cannot be modified. Built-in message templates cannot be modified.
#. Click **OK**.

Copying a Message Template
--------------------------

#. In the message template list, click **Copy** in the row that contains the target template. Set a new template name.
#. Click **OK**.

Deleting a Message Template
---------------------------

#. In the message template list, click **Delete** in the **Operation** column of the target template. Built-in message templates cannot be deleted.
#. Click **OK**.

Deleting Message Templates in a Batch
-------------------------------------

#. In the message template list, select the templates to be deleted and click **Delete**.
#. Click **OK**.

Exporting Message Templates
---------------------------

#. In the message template list, select the templates to be exported and click **Export**.
#. Click **Export all data to an XLSX file** or **Export selected data to an XLSX file**. After the data is exported, you can view it on the local PC.
