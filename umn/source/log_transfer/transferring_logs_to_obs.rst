:original_name: lts_04_0041.html

.. _lts_04_0041:

Transferring Logs to OBS
========================

You can transfer logs to OBS and download log files from the OBS console.

.. note::

   To transfer logs, you must have the **OBS Administrator** permissions apart from the LTS permissions.

Prerequisites
-------------

-  Logs have been ingested to LTS.
-  You have created an OBS bucket.

Creating a Log Transfer Task
----------------------------

#. Log in to the LTS console and choose **Log Transfer** in the navigation pane on the left.

#. Click **Configure Log Transfer** in the upper right corner.

#. On the displayed page, configure the log transfer parameters.

   .. note::

      After a transfer task is created, you can modify parameters except the log group name, transfer destination and log stream name.

   .. table:: **Table 1** Transfer parameters

      +--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------+
      | Parameter                | Description                                                                                                                                                                                                                                                                                                                                | Example Value                    |
      +==========================+============================================================================================================================================================================================================================================================================================================================================+==================================+
      | Enable Transfer          | Enabled by default.                                                                                                                                                                                                                                                                                                                        | Enabled                          |
      +--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------+
      | Transfer Log to OBS      | Enable log transfer to OBS.                                                                                                                                                                                                                                                                                                                | OBS                              |
      +--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------+
      | Transfer Destination     | Select a cloud service for log transfer.                                                                                                                                                                                                                                                                                                   | OBS                              |
      +--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------+
      | Log Group Name           | Select a log group.                                                                                                                                                                                                                                                                                                                        | N/A                              |
      +--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------+
      | Log Stream Name          | Select a log stream.                                                                                                                                                                                                                                                                                                                       | N/A                              |
      +--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------+
      | OBS Bucket               | -  Select an OBS bucket.                                                                                                                                                                                                                                                                                                                   | N/A                              |
      |                          |                                                                                                                                                                                                                                                                                                                                            |                                  |
      |                          |    -  If no OBS buckets are available, click **View OBS Bucket** to access the OBS console and create an OBS bucket.                                                                                                                                                                                                                       |                                  |
      |                          |    -  If encryption has been enabled for the selected OBS bucket, select a key name and select **I agree to grant permissions on Key Management Service (KMS) to LTS so LTS can create and use keys to encrypt and decrypt transferred logs**.                                                                                             |                                  |
      |                          |                                                                                                                                                                                                                                                                                                                                            |                                  |
      |                          | -  Only **Standard** OBS buckets are supported in LTS.                                                                                                                                                                                                                                                                                     |                                  |
      +--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------+
      | Key Name                 | Select a key name for an OBS bucket for which encryption has been enabled. If no keys are available, click **Create Key and Authorize** to go to the Data Encryption Workshop (DEW) console and create a key.                                                                                                                              | N/A                              |
      +--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------+
      | Custom Log Transfer Path | -  Enabled: Logs will be transferred to a custom path to separate transferred log files of different log streams.                                                                                                                                                                                                                          | LTS-test/%Y/%m/%done/%H/%m       |
      |                          |                                                                                                                                                                                                                                                                                                                                            |                                  |
      |                          |    The format is **/LogTanks/**\ *Region name/Custom path*. The default custom path is **lts/%Y/%m/%d**, where **%Y** indicates the year, **%m** indicates the month, and **%d** indicates the day. A custom path must meet the following requirements:                                                                                    |                                  |
      |                          |                                                                                                                                                                                                                                                                                                                                            |                                  |
      |                          |    -  Must start with **/LogTanks/**\ *Region name*.                                                                                                                                                                                                                                                                                       |                                  |
      |                          |    -  Can contain only letters, digits, and the following special characters: ``&$@;:,=+?-._/`` %. The character % can only be followed only by Y (year), m (month), d (day), H (hour), and M (minute). Any number of characters can be added before and after %Y, %m, %d, %H, and %M, and the sequence of these variables can be changed. |                                  |
      |                          |    -  Can contain 1-128 characters.                                                                                                                                                                                                                                                                                                        |                                  |
      |                          |                                                                                                                                                                                                                                                                                                                                            |                                  |
      |                          |    Example:                                                                                                                                                                                                                                                                                                                                |                                  |
      |                          |                                                                                                                                                                                                                                                                                                                                            |                                  |
      |                          |    a. If you enter **LTS-test/%Y/%m/%done/%H/%m**, the path is **LogTanks**/*Region name*/**LTS-test**/*Y*/*m*/*d*\ **one**/*H*/*m*/*Log file name*.                                                                                                                                                                                       |                                  |
      |                          |    b. If you enter **LTS-test/%d/%H/%m/%Y**, the path is **LogTanks**/*Region name*/**LTS-test**/*d*/*H*/*m*/*Y*/*Log file name*.                                                                                                                                                                                                          |                                  |
      |                          |                                                                                                                                                                                                                                                                                                                                            |                                  |
      |                          | -  Disabled: Logs will be transferred to the default path. The default path is **LogTanks/**\ *Region name/2019/01/01/Log group/Log stream/Log file name*.                                                                                                                                                                                 |                                  |
      +--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------+
      | Log Prefix               | The file name prefix of the log files transferred to an OBS bucket                                                                                                                                                                                                                                                                         | LTS-log                          |
      |                          |                                                                                                                                                                                                                                                                                                                                            |                                  |
      |                          | The prefix must meet the following requirements:                                                                                                                                                                                                                                                                                           |                                  |
      |                          |                                                                                                                                                                                                                                                                                                                                            |                                  |
      |                          | -  Can contain 0 to 64 characters.                                                                                                                                                                                                                                                                                                         |                                  |
      |                          | -  Can contain only letters, digits, hyphens (-), underscores (_), and periods (.).                                                                                                                                                                                                                                                        |                                  |
      |                          |                                                                                                                                                                                                                                                                                                                                            |                                  |
      |                          | Example: If you enter **LTS-log**, the log file name will be **LTS-log\_**\ *Log file name*.                                                                                                                                                                                                                                               |                                  |
      +--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------+
      | Format                   | The storage format of logs. The value can be **Raw Log Format** or **JSON**.                                                                                                                                                                                                                                                               | Json                             |
      |                          |                                                                                                                                                                                                                                                                                                                                            |                                  |
      |                          | -  Examples of the raw log format:                                                                                                                                                                                                                                                                                                         |                                  |
      |                          |                                                                                                                                                                                                                                                                                                                                            |                                  |
      |                          |    (Logs displayed on the LTS console are in the raw format.)                                                                                                                                                                                                                                                                              |                                  |
      |                          |                                                                                                                                                                                                                                                                                                                                            |                                  |
      |                          |    .. code-block::                                                                                                                                                                                                                                                                                                                         |                                  |
      |                          |                                                                                                                                                                                                                                                                                                                                            |                                  |
      |                          |       Sep 30 07:30:01 ecs-bd70 CRON[3459]: (root) CMD (/opt/oss/servicemgr/ICAgent/bin/manual/mstart.sh > /dev/null 2>&1)                                                                                                                                                                                                                  |                                  |
      |                          |                                                                                                                                                                                                                                                                                                                                            |                                  |
      |                          | -  The following is an example of the JSON format:                                                                                                                                                                                                                                                                                         |                                  |
      |                          |                                                                                                                                                                                                                                                                                                                                            |                                  |
      |                          |    .. code-block::                                                                                                                                                                                                                                                                                                                         |                                  |
      |                          |                                                                                                                                                                                                                                                                                                                                            |                                  |
      |                          |       {"host_name":"ecs-bd70","ip":"192.168.0.54","line_no":249,"message":"Sep 30 14:40:01 ecs-bd70 CRON[4363]: (root) CMD (/opt/oss/servicemgr/ICAgent/bin/manual/mstart.sh > /dev/null 2>&1)\n","path":"/var/log/syslog","time":1569825602303}                                                                                           |                                  |
      +--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------+
      | Log Transfer Interval    | The interval for automatically transferring logs to OBS buckets. The value can be 2, 5, or 30 minutes, or 1, 3, 6, or 12 hours.                                                                                                                                                                                                            | 3 hours                          |
      +--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------+
      | Time Zone                | When logs are transferred to OBS buckets, the time in the transfer directory and file name will use the specified UTC time zone.                                                                                                                                                                                                           | (UTC) Coordinated Universal Time |
      +--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------+

#. Click **OK**. When the log transfer status changes to **Normal**, the transfer task has been created.

#. Click the OBS bucket name in the **Transfer Destination** column to access the OBS console and view the transferred log files.

   Transferred logs can be downloaded from OBS to your local computer for viewing.


   .. figure:: /_static/images/en-us_image_0000001460346829.png
      :alt: **Figure 1** Transferring logs to OBS

      **Figure 1** Transferring logs to OBS

   .. note::

      Logs stored in OBS are in raw or JSON format.

Modifying a Log Transfer Task
-----------------------------

#. Log in to the LTS console and choose **Log Transfer** in the navigation pane on the left.
#. Locate the row that contains the target transfer task and click **Modify** in the **Operation** column.
#. Click **OK**.

Deleting a Log Transfer Task
----------------------------

If logs do not need to be transferred, you can delete the transfer task.

.. note::

   -  After a transfer task is deleted, log transfer will be stopped. Exercise caution when performing the deletion.
   -  After a transfer task is deleted, the logs that have been transferred remain in OBS.
   -  When you create a transfer task, OBS will grant read and write permissions to LTS for the selected bucket. If one OBS bucket is used by multiple transfer tasks, perform the following operations to delete the transfer task:

      -  If only one transfer task is created using this OBS bucket, delete the bucket access permission granted to specific users on the **Access Control** > **Bucket ACLs** tab page on the OBS console when you delete the transfer task.
      -  If multiple transfer tasks are created using this OBS bucket, do not delete the bucket access permission. Otherwise, data transfer will fail.

#. Log in to the LTS console and choose **Log Transfer** in the navigation pane on the left.
#. Locate the row of the target transfer task and choose **Delete** in the **Operation** column.
#. Click **OK**.

Viewing Transfer Status
-----------------------

The status of a transfer task can be **Normal**, **Abnormal**, or **Disabled**.

-  **Normal**: The log transfer task works properly.
-  **Abnormal**: An error occurred in the log transfer task. The possible causes are as follows:

   -  The OBS bucket has been deleted. Specify another OBS bucket.
   -  Access control on the OBS bucket is configured incorrectly. Access the OBS console to correct the settings.
   -  The key for the encrypted OBS bucket has been deleted or the authorization has been canceled. Ensure that the key is valid.

-  **Disabled**: The log transfer task is stopped.
