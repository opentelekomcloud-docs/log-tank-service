:original_name: lts_04_0041.html

.. _lts_04_0041:

Log Transfer
============

You can transfer logs to OBS to keep logs for a long time.

.. note::

   Local log files are cleared periodically, but the logs transferred to OBS will not be affected.

   To transfer logs, you must have the **OBS Administrator** permissions apart from the LTS permissions.

Prerequisites
-------------

-  Logs have been ingested to LTS.
-  You have purchased an OBS bucket.

Creating a Log Transfer Task
----------------------------

#. Log in to the LTS console and choose **Log Transfer** in the navigation pane on the left.

#. Click **Create Log Transfer** in the upper right corner.

#. On the displayed page, configure the log transfer parameters.

   .. note::

      After a transfer task is created, you can modify parameters except the log group name, and log stream name.

   .. table:: **Table 1** Transfer parameters

      +--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter                | Description                                                                                                                                                                                                                                      | Example Value         |
      +==========================+==================================================================================================================================================================================================================================================+=======================+
      | Log Group Name           | Select a log group.                                                                                                                                                                                                                              | N/A                   |
      +--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Log Stream Name          | Select a log stream.                                                                                                                                                                                                                             | N/A                   |
      +--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | OBS Bucket               | -  Select an OBS bucket.                                                                                                                                                                                                                         | N/A                   |
      |                          |                                                                                                                                                                                                                                                  |                       |
      |                          |    -  If no OBS buckets are available, click **View OBS Bucket** to access the OBS console and create an OBS bucket.                                                                                                                             |                       |
      |                          |                                                                                                                                                                                                                                                  |                       |
      |                          | -  Only **Standard** OBS buckets are supported in LTS.                                                                                                                                                                                           |                       |
      +--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Custom Log Transfer Path | -  Enabled: Logs will be transferred to a custom path to separate transferred log files of different log streams.                                                                                                                                | LTS-test              |
      |                          |                                                                                                                                                                                                                                                  |                       |
      |                          |    The format is **/LogTanks/**\ *Region name/Custom path*. A custom path must meet the following requirements:                                                                                                                                  |                       |
      |                          |                                                                                                                                                                                                                                                  |                       |
      |                          |    -  Must start with **/LogTanks/**\ *Region name*.                                                                                                                                                                                             |                       |
      |                          |    -  Can contain 1-64 characters.                                                                                                                                                                                                               |                       |
      |                          |                                                                                                                                                                                                                                                  |                       |
      |                          | -  Disabled: Logs will be transferred to the default path. The default path is **LogTanks/**\ *Region name/2019/01/01/Log group/Log stream/Log file name*.                                                                                       |                       |
      +--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Log File Prefix          | The file name prefix of the log files transferred to an OBS bucket                                                                                                                                                                               | LTS-log               |
      |                          |                                                                                                                                                                                                                                                  |                       |
      |                          | The prefix must meet the following requirements:                                                                                                                                                                                                 |                       |
      |                          |                                                                                                                                                                                                                                                  |                       |
      |                          | -  Can contain 0 to 64 characters.                                                                                                                                                                                                               |                       |
      |                          | -  Can contain only letters, digits, hyphens (-), underscores (_), and periods (.).                                                                                                                                                              |                       |
      |                          |                                                                                                                                                                                                                                                  |                       |
      |                          | Example: If you enter **LTS-log**, the log file name will be **LTS-log\_**\ *Log file name*.                                                                                                                                                     |                       |
      +--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Format                   | The storage format of logs. The value can be **Raw Log Format** or **JSON**.                                                                                                                                                                     | Json                  |
      |                          |                                                                                                                                                                                                                                                  |                       |
      |                          | -  Examples of the raw log format:                                                                                                                                                                                                               |                       |
      |                          |                                                                                                                                                                                                                                                  |                       |
      |                          |    (Logs displayed on the LTS console are in the raw format.)                                                                                                                                                                                    |                       |
      |                          |                                                                                                                                                                                                                                                  |                       |
      |                          |    .. code-block::                                                                                                                                                                                                                               |                       |
      |                          |                                                                                                                                                                                                                                                  |                       |
      |                          |       Sep 30 07:30:01 ecs-bd70 CRON[3459]: (root) CMD (/opt/oss/servicemgr/ICAgent/bin/manual/mstart.sh > /dev/null 2>&1)                                                                                                                        |                       |
      |                          |                                                                                                                                                                                                                                                  |                       |
      |                          | -  The following is an example of the JSON format:                                                                                                                                                                                               |                       |
      |                          |                                                                                                                                                                                                                                                  |                       |
      |                          |    .. code-block::                                                                                                                                                                                                                               |                       |
      |                          |                                                                                                                                                                                                                                                  |                       |
      |                          |       {"host_name":"ecs-bd70","ip":"192.168.0.54","line_no":249,"message":"Sep 30 14:40:01 ecs-bd70 CRON[4363]: (root) CMD (/opt/oss/servicemgr/ICAgent/bin/manual/mstart.sh > /dev/null 2>&1)\n","path":"/var/log/syslog","time":1569825602303} |                       |
      +--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Transfer Log to OBS      | Enable log transfer to OBS.                                                                                                                                                                                                                      | Enabled               |
      +--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Transfer Period          | The interval for automatically transferring logs to OBS buckets. The value can be 2, 5, or 30 minutes, or 1, 3, 6, or 12 hours.                                                                                                                  | 3 hours               |
      +--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. Click **OK**. When the log transfer status changes to **Normal**, the transfer task has been created.

#. Click the OBS bucket name in the **OBS Bucket** column to access the OBS console and view the transferred log files.

   Transferred logs can be downloaded from OBS to your local computer for viewing.

Viewing Transfer Status
-----------------------

The status of a transfer task can be **Normal**, **Abnormal**, or **Disabled**.

-  **Normal**: The log transfer task works properly.
-  **Abnormal**: An error occurred in the log transfer task. The possible causes are as follows:

   -  The OBS bucket has been deleted. Specify another OBS bucket.
   -  Access control on the OBS bucket is configured incorrectly. Access the OBS console to correct the settings.
   -  The key for the encrypted OBS bucket has been deleted or the authorization has been canceled. Ensure that the key is valid.

-  **Disabled**: The log transfer task is stopped.

Deleting a Log Transfer Task
----------------------------

If logs do not need to be transferred, you can delete the transfer task.

.. note::

   -  After a transfer task is deleted, log transfer will be stopped. Exercise caution when performing the deletion.
   -  After a transfer task is deleted, the logs that have been transferred remain in OBS.

#. Log in to the LTS console and choose **Log Transfer** in the navigation pane on the left.
#. Locate the row of the target transfer task and choose **More** > **Delete** in the **Operation** column.
#. Click **OK**.
