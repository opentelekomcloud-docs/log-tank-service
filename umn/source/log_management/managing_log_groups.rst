:original_name: lts_04_0003.html

.. _lts_04_0003:

Managing Log Groups
===================

A log group is the basic unit for LTS to manage logs. It classifies and consists of log streams, but does not store any log data. Up to 100 log groups can be created for an account.

A log group usually corresponds to a project or business in a company. You are advised to sort log streams of various applications or services within a project or business to the same log group. In this way, project staff only need to monitor log streams in the log group corresponding to their project, without being distracted by log streams of other projects.

LTS allows you to add tags to log groups to help O&M personnel manage services.

Prerequisites
-------------

You have obtained an account and its password for logging in to the LTS console.

Creating a Log Group
--------------------

#. Log in to the management console and choose **Management & Deployment** > **Log Tank Service**. The **Log Management** page is displayed by default.

#. Click **Create Log Group**.

#. On the displayed page, set log group parameters by referring to :ref:`Table 1 <lts_04_0003__en-us_topic_0000001125775239_table9217134717322>`.

   .. _lts_04_0003__en-us_topic_0000001125775239_table9217134717322:

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

   -  In the log group list, you can view information such as the log group name, tags, and log streams.
   -  Click the log group name to access the log stream details page.
   -  When multiple log groups are created concurrently, there may be a limit exceeding error.

Modifying a Log Group
---------------------

You can modify log group settings, such as the group name, log retention duration, or tags as follows:

#. In the log group list on the **Log Management** page, locate the target log group and click **Modify** in the **Operation** column.

#. On the page displayed, modify the group name, log retention duration, and tags on the displayed page.

#. Click **OK**.

#. After the modification is successful, move the cursor over the log group name. The new and original log group names are displayed.


   .. figure:: /_static/images/en-us_image_0000001748544704.png
      :alt: **Figure 1** Log group name

      **Figure 1** Log group name

Deleting a Log Group
--------------------

You can delete a log group that is no longer needed. Deleting a log group will also delete the log streams and log data in the log group. Deleted log groups cannot be recovered. Exercise caution when performing the deletion.

.. note::

   If you want to delete a log group that is associated with a log transfer task, delete the task first.

#. In the log group list on the **Log Management** page, locate the target log group and click **Delete** in the **Operation** column.

#. Enter **DELETE** and click **OK**.


   .. figure:: /_static/images/en-us_image_0000001972605366.png
      :alt: **Figure 2** Deleting a log group

      **Figure 2** Deleting a log group

Searching Log Groups/Streams
----------------------------

In the log group list, you can set the following filter criteria:

-  Log group/stream
-  Original log group/stream name
-  Log group name/ID
-  Log stream name/ID
-  Log group tag
-  Remarks


.. figure:: /_static/images/en-us_image_0000001748704148.png
   :alt: **Figure 3** Searching log groups/streams

   **Figure 3** Searching log groups/streams

Other Operations
----------------

-  To check the details of a log group, including the log group name, ID, and creation time, go to the log group list and click **Details** in the **Operation** column of the desired log group.
-  To download all displayed information about a log group to the local PC, click |image1| next to the search box.

.. |image1| image:: /_static/images/en-us_image_0000001605059081.png
