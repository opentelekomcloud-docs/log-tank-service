:original_name: lts_08301.html

.. _lts_08301:

Creating Log Groups and Log Streams
===================================

Prerequisites
-------------

You have obtained an account and its password for logging in to the console.

Creating a Log Group
--------------------

#. Log in to the management console and choose **Management & Deployment** > **Log Tank Service**.

#. On the **Log Management** page, click **Create Log Group**.

#. In the dialog box displayed, set log group parameters by referring to :ref:`Table 1 <lts_08301__en-us_topic_0182095137_en-us_topic_0000001125775239_table9217134717322>`.

   .. _lts_08301__en-us_topic_0182095137_en-us_topic_0000001125775239_table9217134717322:

   .. table:: **Table 1** Log group parameters

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                      |
      +===================================+==================================================================================================================================================================================================================================+
      | Log Group Name                    | -  Enter 1 to 64 characters, including only letters, digits, hyphens (-), underscores (_), and periods (.). Do not start with a period or underscore or end with a period.                                                       |
      |                                   | -  Collected logs are sent to log streams of the corresponding log groups. If there are too many logs to collect, separate logs into different log groups based on log types, and name log groups in an easily identifiable way. |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Enterprise Project Name           | Select an enterprise project. You can click **View Enterprise Projects** to view all enterprise projects.                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                  |
      |                                   | Enterprise projects allow you to manage cloud resources and users by project.                                                                                                                                                    |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Log Retention Duration            | Specify the log retention duration for the log group, that is, how many days the logs will be stored in LTS after being reported to LTS.                                                                                         |
      |                                   |                                                                                                                                                                                                                                  |
      |                                   | By default, logs are retained for 30 days (customizable for 1 to 365 days).                                                                                                                                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Tag                               | You can tag log groups as required. Click **Add Tags**, enter a tag key and value, and enable **Apply to Log Stream**.                                                                                                           |
      |                                   |                                                                                                                                                                                                                                  |
      |                                   | -  To add more tags, repeat this step. A maximum of 20 tags can be added.                                                                                                                                                        |
      |                                   | -  A tag key can contain up to 128 characters, and a tag value can contain up to 255 characters.                                                                                                                                 |
      |                                   | -  A tag key must be unique.                                                                                                                                                                                                     |
      |                                   | -  If a tag is used by a transfer task, you need to modify the task configuration after deleting the tag.                                                                                                                        |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Remark                            | Enter remarks. The value contains up to 1,024 characters.                                                                                                                                                                        |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**. The created log group will be displayed in the log group list.

Creating a Log Stream
---------------------

#. Click |image1| on the left of a log group name and click **Create Log Stream**.

#. In the dialog box displayed, set log stream parameters by referring to :ref:`Table 2 <lts_08301__en-us_topic_0182095137_en-us_topic_0000001125876999_table1113345715819>`.

   .. _lts_08301__en-us_topic_0182095137_en-us_topic_0000001125876999_table1113345715819:

   .. table:: **Table 2** Log stream parameters

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                        |
      +===================================+====================================================================================================================================================================================================+
      | Log Group Name                    | The name of the target log group is displayed by default.                                                                                                                                          |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Log Stream Name                   | A log stream name can contain 1 to 64 characters, including only letters, digits, hyphens (-), underscores (_), and periods (.). It cannot start with a period or underscore or end with a period. |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Enterprise Project Name           | Select the required enterprise project. The default value is **default**. You can click **View Enterprise Projects** to view all enterprise projects.                                              |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Log Retention Duration            | Specify the log retention duration for the log stream, that is, how many days the logs will be stored in LTS after being reported to LTS.                                                          |
      |                                   |                                                                                                                                                                                                    |
      |                                   | By default, logs are retained for 30 days (customizable for 1 to 365 days).                                                                                                                        |
      |                                   |                                                                                                                                                                                                    |
      |                                   | -  If you enable **Log Retention Duration** for the log stream, logs are retained for the duration set for the log stream.                                                                         |
      |                                   | -  If you disable **Log Retention Duration** for the log stream, logs are retained for the duration set for the log group.                                                                         |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Tag                               | You can tag log streams as required. Click **Add Tags** and enter a tag key and tag value.                                                                                                         |
      |                                   |                                                                                                                                                                                                    |
      |                                   | .. note::                                                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                    |
      |                                   |    -  To add more tags, repeat this step. A maximum of 20 tags can be added.                                                                                                                       |
      |                                   |    -  A tag key can contain up to 128 characters, and a tag value can contain up to 255 characters.                                                                                                |
      |                                   |    -  A tag key must be unique.                                                                                                                                                                    |
      |                                   |    -  If a tag is used by a transfer task, you need to modify the task configuration after deleting the tag.                                                                                       |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Remark                            | Enter remarks. The value contains up to 1,024 characters.                                                                                                                                          |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**. The created log stream will be displayed under the target log group.

.. |image1| image:: /_static/images/en-us_image_0000001637679773.png
