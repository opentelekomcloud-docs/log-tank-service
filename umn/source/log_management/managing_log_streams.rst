:original_name: lts_04_0004.html

.. _lts_04_0004:

Managing Log Streams
====================

LTS manages logs by log stream. Collected logs of different types are classified and stored in different log streams for easier log management. If there are a large number of logs, you can create multiple log streams and name them for quick log search. For example, you can sort operation logs and access logs into different log streams, making it easier to find specific logs when you need them. You can add tags to log streams to help O&M personnel manage services.

Up to 100 log streams can be created in a log group. The upper limit cannot be increased. If you cannot create a log stream because the upper limit is reached, you are advised to delete log streams that are no longer needed and try again, or create log streams in a new log group.

Prerequisites
-------------

You have created a log group.

Creating a Log Stream
---------------------

#. Log in to the management console and choose **Management & Deployment** > **Log Tank Service**. The **Log Management** page is displayed by default.

#. Click |image1| on the left of the target log group.

#. Click **Create Log Stream**. On the displayed page, set log stream parameters by referring to :ref:`Table 1 <lts_04_0004__en-us_topic_0000001125876999_table1113345715819>`.

   .. _lts_04_0004__en-us_topic_0000001125876999_table1113345715819:

   .. table:: **Table 1** Log stream parameters

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


   .. figure:: /_static/images/en-us_image_0000002009165089.png
      :alt: **Figure 1** Creating a log stream

      **Figure 1** Creating a log stream

#. Click **OK**. In the log stream list, you can view information such as the log stream name and operations.

Modifying a Log Stream
----------------------

By default, a log stream inherits the log retention setting from the log group it belongs to.

#. In the log stream list, locate the target log stream and click |image2| in the **Operation** column.

#. On the page displayed, modify the stream name, log retention duration, and tags.

   .. note::

      -  If you disable **Log Retention Duration**, the log stream will inherit the log retention setting of the log group.
      -  If you enable **Log Retention Duration**, you can set the log retention duration specifically for the log stream.
      -  The logs that exceed the retention period will be automatically deleted. You can transfer logs to OBS buckets for long-term storage.

#. Click **OK**.

#. After the modification is successful, move the cursor over the log stream name. The new and original log stream names are displayed.


   .. figure:: /_static/images/en-us_image_0000001795707481.png
      :alt: **Figure 2** Log stream name

      **Figure 2** Log stream name

Deleting a Log Stream
---------------------

You can delete a log stream that is no longer needed. Deleting a log stream will also delete the log data in the log stream. Deleted log streams cannot be recovered. Exercise caution when performing the deletion.

.. note::

   -  Before deleting a log stream, check whether any log collection task is configured for it. If there is a log collection task, deleting the log stream may affect log reporting.
   -  If you want to delete a log stream that is associated with a log transfer task, delete the task first.

#. In the log stream list, locate the target log stream and click |image3| in the **Operation** column.

#. Enter **DELETE** and click **OK**.


   .. figure:: /_static/images/en-us_image_0000002009164357.png
      :alt: **Figure 3** Deleting a log stream

      **Figure 3** Deleting a log stream

Other Operations
----------------

-  Adding a log stream to favorites

   Click |image4| in the **Operation** column of a log stream. The stream is then displayed in the **My Favorites**/**My Favorites(Local Cache)** list.

-  Viewing details

   Click |image5| in the **Operation** column of a log stream to view its details, including its name, ID, and creation time.

.. |image1| image:: /_static/images/en-us_image_0000001217758588.png
.. |image2| image:: /_static/images/en-us_image_0000002065402777.png
.. |image3| image:: /_static/images/en-us_image_0000001543219709.png
.. |image4| image:: /_static/images/en-us_image_0000002029238830.png
.. |image5| image:: /_static/images/en-us_image_0000002065396965.png
