:original_name: lts_04_0003.html

.. _lts_04_0003:

Managing Log Groups
===================

A log group is the basic unit for LTS to manage logs. It classifies and consists of log streams, but does not store any log data itself. Up to 100 log groups can be created for each account.

A log group usually corresponds to a project or business in a company. You are advised to sort log streams of various applications or services within a project or business to the same log group. In this way, project staff only need to monitor log streams in the log group corresponding to their project, without being distracted by log streams of other projects.

LTS allows you to add tags to log groups to help O&M personnel manage services.

Prerequisites
-------------

You have obtained an account and its password for logging in to the LTS console.

Creating a Log Group
--------------------

#. Log in to the management console and choose **Management & Deployment** > **Log Tank Service**.

#. On the **Log Management** page, click **Create Log Group**.

#. On the displayed page, set log group parameters by referring to :ref:`Table 1 <lts_04_0003__en-us_topic_0000001125775239_table9217134717322>`.

   .. _lts_04_0003__en-us_topic_0000001125775239_table9217134717322:

   .. table:: **Table 1** Log group parameters

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                 |
      +===================================+=============================================================================================================================================================================================================================================================+
      | Log Group Name                    | A log group is the basic unit for LTS to manage logs. It is used to classify log streams. If there are too many logs to collect, separate logs into different log groups based on log types, and name log groups in an easily identifiable way.             |
      |                                   |                                                                                                                                                                                                                                                             |
      |                                   | LTS automatically generates a default log group name. You are advised to customize one based on your service. You can also change it after the log group is created. The naming rules are as follows:                                                       |
      |                                   |                                                                                                                                                                                                                                                             |
      |                                   | -  Enter 1 to 64 characters, including only letters, digits, hyphens (-), underscores (_), and periods (.). Do not start with a period or underscore or end with a period.                                                                                  |
      |                                   | -  Each log group name must be unique.                                                                                                                                                                                                                      |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Enterprise Project Name           | Enterprise projects allow you to manage cloud resources and users by project.                                                                                                                                                                               |
      |                                   |                                                                                                                                                                                                                                                             |
      |                                   | By default, the **default** enterprise project is used. You are advised to select an enterprise project that fits your service needs. To see all available options, click **View Enterprise Projects**.                                                     |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Log Retention (Days)              | Specify the log retention period for the log group, that is, how many days the logs will be stored in LTS after being reported to LTS.                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                                             |
      |                                   | By default, logs are retained for 30 days. You can set the retention period to one to 365 days.                                                                                                                                                             |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Tag                               | Tag the log group as required. Click **Add Tags** and enter a tag key and value. If you enable **Apply to Log Stream**, the tag will be applied to all log streams in the log group. To add more tags, repeat this step. A maximum of 20 tags can be added. |
      |                                   |                                                                                                                                                                                                                                                             |
      |                                   | **Tag key restrictions:**                                                                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                                                                             |
      |                                   | -  A tag key can contain letters, digits, spaces, and special characters ``(_.:=+-@),`` but cannot start or end with a space or start with **\_sys\_**.                                                                                                     |
      |                                   | -  A tag key can contain up to 128 characters.                                                                                                                                                                                                              |
      |                                   | -  Each tag key must be unique.                                                                                                                                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                             |
      |                                   | **Tag value restrictions:**                                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                             |
      |                                   | -  A tag value can contain letters, digits, spaces, and the following special characters: \_.:=+-@                                                                                                                                                          |
      |                                   | -  A tag value can contain up to 255 characters.                                                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                                                                             |
      |                                   | **Deleting a tag:**                                                                                                                                                                                                                                         |
      |                                   |                                                                                                                                                                                                                                                             |
      |                                   | Click **Delete** in the **Operation** column of the tag.                                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                                             |
      |                                   | .. warning::                                                                                                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                                                             |
      |                                   |    Deleted tags cannot be recovered.                                                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                             |
      |                                   |    If a tag is used by a transfer task, you need to modify the task configuration after deleting the tag.                                                                                                                                                   |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Remark                            | Enter remarks. The value contains up to 1,024 characters.                                                                                                                                                                                                   |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**. The created log group will be displayed in the log group list.

   -  In the log group list, view information such as the log group name, tags, and log streams.
   -  Click the log group name to access the log details page.

Modifying a Log Group
---------------------

After a log group is created, you can modify its settings, such as the group name, log retention duration, or tags as follows:

#. In the log group list on the **Log Management** page, locate the target log group and click **Modify** in the **Operation** column.

#. On the page displayed, modify the group name, log retention period, and tags.

#. Click **OK**.

#. After the modification is successful, move the cursor over the log group name to view the new and original names along with the log group ID.


   .. figure:: /_static/images/en-us_image_0000001748544704.png
      :alt: **Figure 1** Log group name

      **Figure 1** Log group name

Deleting a Log Group
--------------------

You can delete a log group that is no longer needed. Deleting a log group will also delete the log streams and log data in the log group.

If you want to delete a log group that is associated with a log transfer task, delete the task first.

.. warning::

   Deleting a log group may lead to exceptions in related log tasks. In addition, deleted log groups cannot be restored.

#. In the log group list on the **Log Management** page, locate the target log group and click **Delete** in the **Operation** column.

#. Enter **DELETE** in the text box or click **Auto Enter**, and click **OK**.


   .. figure:: /_static/images/en-us_image_0000002178924481.png
      :alt: **Figure 2** Deleting a log group

      **Figure 2** Deleting a log group

Searching Log Groups/Streams
----------------------------

You can search for log groups using the following filter criteria:

-  **Log Group/Log Stream**: log group or stream name.
-  **Original Log Group Name/Original Log Stream Name**: original name of a log group or log stream before the name is changed, that is, the name defined during creation.
-  **Log Group Name/ID**: log group name or ID (hover your cursor over the log group name to view the ID)
-  **Log Stream Name/ID**: log stream name or ID (hover your cursor over the log stream name to view the ID)
-  **Log Group Tag**: tags set for a log group
-  **Remark**: remarks customized during log group creation.


.. figure:: /_static/images/en-us_image_0000001748704148.png
   :alt: **Figure 3** Searching log groups/streams

   **Figure 3** Searching log groups/streams

Other Operations
----------------

-  **Viewing log group details:** In the log group list, click **Details** in the **Operation** column of the desired log group to view its name, ID, and creation time.
-  To download all displayed information about a log group to the local PC, click |image1| next to the search box.

.. |image1| image:: /_static/images/en-us_image_0000002444585646.png
