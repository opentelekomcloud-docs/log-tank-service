:original_name: lts_04_1217.html

.. _lts_04_1217:

Managing Tags
=============

You can tag log groups, log streams, host groups, and log ingestion configurations.

Tagging a Log Group
-------------------

Users can add, delete, modify, and query tags on the log group page.

#. Log in to the management console and choose **Management & Deployment** > **Log Tank Service**. The **Log Management** page is displayed by default.

#. Move the cursor to the **Tags** column of the target log group and click |image1|.

#. On the **Edit** page that is displayed, click **Add Tags** and enter a tag key and value. If you enable **Apply to Log Stream**, the tag will be synchronized to all log streams in the log group.


   .. figure:: /_static/images/en-us_image_0000001748707920.png
      :alt: **Figure 1** Editing a tag

      **Figure 1** Editing a tag

   .. note::

      -  A tag key can contain only UTF-8 letters, digits, spaces, and the following special characters ``_.:=+-@.`` Do not start with an underscore (_).
      -  A tag value can contain only UTF-8 letters, digits, spaces, and the following special characters ``_.:=+-@.``
      -  To add multiple tags, repeat this step.
      -  To delete a tag, click **Delete** in the **Operation** column of the tag.
      -  A tag key can contain up to 128 characters, and a tag value can contain up to 255 characters.
      -  A tag key must be unique.
      -  If a tag is used by a transfer task, you need to modify the task configuration after deleting the tag.

#. Click **OK**.

   On the **Log Management** page, you can view the added tags in the **Tags** column of the log group.

Tagging a Log Stream
--------------------

You can add, delete, modify, and view tags on the log stream list page. When you manage the tags of a single log stream, the changes will not be synchronized to other streams.

#. Click |image2| in front of the name of the target log group.

#. Move the cursor to the **Tags** column of the target log stream and click |image3|.

#. On the **Edit** page that is displayed, click **Add Tags** and enter a tag key and value.


   .. figure:: /_static/images/en-us_image_0000001748708036.png
      :alt: **Figure 2** Editing a tag

      **Figure 2** Editing a tag

   .. note::

      -  A tag key can contain only UTF-8 letters, digits, spaces, and the following special characters ``_.:=+-@.`` Do not start with an underscore (_).
      -  A tag value can contain only UTF-8 letters, digits, spaces, and the following special characters ``_.:=+-@.``
      -  To add multiple tags, repeat this step.
      -  To delete a tag, click **Delete** in the **Operation** column of the tag.
      -  A tag key can contain up to 128 characters, and a tag value can contain up to 255 characters.
      -  A tag key must be unique.
      -  If a tag is used by a transfer task, you need to modify the task configuration after deleting the tag.

#. Click **OK**.

   In the log stream list, you can view the system tags and added custom tags in the **Tags** column of the log stream.

Tagging a Host Group
--------------------

You can add, delete, modify, and view tags on the host group list page. When you manage the tags of a single host group, the changes will not be synchronized to other groups.

#. Choose **Host Management** in the navigation pane.

#. On the **Host Groups** tab, click |image4| in the **Operation** column of a host group.

#. On the **Edit** page that is displayed, click **Add Tags** and enter a tag key and value.

   .. note::

      -  A tag key can contain only UTF-8 letters, digits, spaces, and the following special characters ``_.:=+-@.`` Do not start with an underscore (_).
      -  A tag value can contain only UTF-8 letters, digits, spaces, and the following special characters ``_.:=+-@.``
      -  To add multiple tags, repeat this step.
      -  To delete a tag, click **Delete** in the **Operation** column of the tag.
      -  A tag key can contain up to 128 characters, and a tag value can contain up to 255 characters.
      -  A tag key must be unique.

#. Click **OK**.

   On the **Host Management** page, you can view the added tags in the **Tags** column of the host group.

Tagging a Log Ingestion Configuration
-------------------------------------

You can add, delete, modify, and view tags on the log ingestion page. When you manage the tags of a single log ingestion configuration, the changes will not be synchronized to other configurations.

#. Choose **Log Ingestion** in the navigation pane.

#. Click **Configure Tag** in the **Operation** column of a log ingestion rule on the **Ingestion Rule** tab page.

#. On the **Edit** page that is displayed, click **Add Tags** and enter a tag key and value.

   .. note::

      -  A tag key can contain only UTF-8 letters, digits, spaces, and the following special characters ``_.:=+-@.`` Do not start with an underscore (_).
      -  A tag value can contain only UTF-8 letters, digits, spaces, and the following special characters ``_.:=+-@.``
      -  To add multiple tags, repeat this step.
      -  To delete a tag, click **Delete** next to the tag on the tag management dialog box.
      -  A tag key can contain up to 128 characters, and a tag value can contain up to 255 characters.
      -  A tag key must be unique.

#. Click **OK**.

   On the **Log Ingestion** page, you can view the added tags in the **Tags** column of the log ingestion configuration.

.. |image1| image:: /_static/images/en-us_image_0000001658469148.png
.. |image2| image:: /_static/images/en-us_image_0000001706749901.png
.. |image3| image:: /_static/images/en-us_image_0000001706710657.png
.. |image4| image:: /_static/images/en-us_image_0000001658312108.png
