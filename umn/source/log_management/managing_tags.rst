:original_name: lts_04_1217.html

.. _lts_04_1217:

Managing Tags
=============

You can tag log groups, log streams, host groups, and log ingestion configurations.

Tagging a Log Group
-------------------

Users can add, delete, modify, and query tags on the log group page.

#. Log in to the management console and choose **Management & Deployment** > **Log Tank Service**.

#. On the **Log Management** page, move the cursor to the **Tags** column of the target log group and click |image1|.

#. On the displayed page, click **Add Tags** and enter a tag key and value. If you enable **Apply to Log Stream**, the tag will be synchronized to all log streams in the log group.


   .. figure:: /_static/images/en-us_image_0000002143569266.png
      :alt: **Figure 1** Editing a tag

      **Figure 1** Editing a tag

   .. note::

      -  A tag key can contain letters, digits, spaces, and special characters ``(_.:=+-@),`` but cannot start or end with a space or start with **\_sys\_**.
      -  A tag value can contain letters, digits, spaces, and the following special characters: \_.:=+-@

      -  To add multiple tags, repeat this step.
      -  To delete a tag, click **Delete** in the **Operation** column of the tag.
      -  A tag key can contain up to 128 characters, and a tag value can contain up to 255 characters.
      -  Each tag key must be unique.
      -  If a tag is used by a transfer task, you need to modify the task configuration after deleting the tag.

#. Click **OK**. In the log group list, you can view the added tags in the **Tags** column.

Tagging a Log Stream
--------------------

You can add, delete, modify, and view tags in the log stream list. Changes made to one log stream's tags do not affect other log streams.

#. Click |image2| in front of the name of the target log group.

#. Move the cursor to the **Tags** column of the target log stream and click |image3|.

#. On the displayed page, click **Add Tags** and enter a tag key and value.


   .. figure:: /_static/images/en-us_image_0000002143569402.png
      :alt: **Figure 2** Editing a tag

      **Figure 2** Editing a tag

   .. note::

      -  A tag key can contain letters, digits, spaces, and special characters ``(_.:=+-@),`` but cannot start or end with a space or start with **\_sys\_**.
      -  A tag value can contain letters, digits, spaces, and the following special characters: \_.:=+-@

      -  To add multiple tags, repeat this step.
      -  To delete a tag, click **Delete** in the **Operation** column of the tag.
      -  A tag key can contain up to 128 characters, and a tag value can contain up to 255 characters.
      -  Each tag key must be unique.
      -  If a tag is used by a transfer task, you need to modify the task configuration after deleting the tag.

#. Click **OK**. In the log stream list, you can view the added tags in the **Tags** column.

Tagging a Host Group
--------------------

You can add, delete, modify, and view tags of host groups. When you manage the tags of a single host group, the changes will not be synchronized to other groups.

#. Choose **Host Management** > **Host Groups** in the navigation pane.
#. Locate the target host group and click **More** > **Configure Tag** in the **Operation** column.
#. On the displayed page, click **Add Tags** and enter a tag key and value.

   .. note::

      -  A tag key can contain letters, digits, spaces, and special characters ``(_.:=+-@),`` but cannot start or end with a space or start with **\_sys\_**.
      -  A tag value can contain letters, digits, spaces, and the following special characters: \_.:=+-@

      -  To add multiple tags, repeat this step.
      -  To delete a tag, click **Delete** in the **Operation** column of the tag.
      -  A tag key can contain up to 128 characters, and a tag value can contain up to 255 characters.
      -  Each tag key must be unique.

#. Click **OK**. On the **Host Groups** page, you can view the added tags in the **Tags** column.

Tagging a Log Ingestion Configuration
-------------------------------------

You can add, delete, modify, and view tags of log ingestion configurations. When you manage the tags of a single log ingestion configuration, the changes will not be synchronized to other configurations.

#. In the navigation pane, choose **Log Ingestion** > **Ingestion Management**.
#. Locate the target log ingestion configuration and click **More** > **Configure Tag** in the **Operation** column.
#. On the displayed page, click **Add Tags** and enter a tag key and value.

   .. note::

      -  A tag key can contain letters, digits, spaces, and special characters ``(_.:=+-@),`` but cannot start or end with a space or start with **\_sys\_**.
      -  A tag value can contain letters, digits, spaces, and the following special characters: \_.:=+-@

      -  To add multiple tags, repeat this step.
      -  To delete a tag, click **Delete** next to the tag on the tag management dialog box.
      -  A tag key can contain up to 128 characters, and a tag value can contain up to 255 characters.
      -  Each tag key must be unique.

#. Click **OK**. On the **Ingestion Management** page, you can view the added tags in the **Tags** column.

Tagging a Log Alarm Rule
------------------------

You can add, delete, modify, and view tags of log alarm rules. When you manage the tags of a single log alarm rule, the changes will not be synchronized to other alarm rules.

#. In the navigation pane, choose **Log Alarms**. On the displayed page, click the **Alarm Rules** tab.
#. Locate the target log alarm rule and click **More** > **Configure Tag** in the **Operation** column.
#. On the displayed page, click **Add Tags** and enter a tag key and value.

   .. note::

      -  A tag key can contain letters, digits, spaces, and special characters ``(_.:=+-@),`` but cannot start or end with a space or start with **\_sys\_**.
      -  A tag value can contain letters, digits, spaces, and the following special characters: \_.:=+-@

      -  To add multiple tags, repeat this step.
      -  To delete a tag, click **Delete** next to the tag on the tag management dialog box.
      -  A tag key can contain up to 128 characters, and a tag value can contain up to 255 characters.
      -  Each tag key must be unique.

#. Click **OK**. On the **Alarm Rules** tab page, you can view the added tags in the **Tags** column.

.. |image1| image:: /_static/images/en-us_image_0000001658469148.png
.. |image2| image:: /_static/images/en-us_image_0000001706749901.png
.. |image3| image:: /_static/images/en-us_image_0000001706710657.png
