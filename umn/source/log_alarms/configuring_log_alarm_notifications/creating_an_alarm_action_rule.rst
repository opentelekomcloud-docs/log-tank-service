:original_name: lts_02_0926.html

.. _lts_02_0926:

Creating an Alarm Action Rule
=============================

LTS allows you to customize alarm action rules. You can create an alarm action rule to associate an SMN topic with a message template. You can also customize notification content when creating a message template.

Prerequisites
-------------

-  A topic has been created.
-  A topic policy has been configured.
-  A subscriber has been added to the topic. A subscriber is the recipient of the notification, for example, an email or SMS message receiver.

Precaution
----------

You can create a maximum of 1,000 alarm action rules. If this number has been reached, delete unnecessary rules.


Creating an Alarm Action Rule
-----------------------------

#. Log in to the management console and choose **Management & Deployment** > **Log Tank Service**.
#. Choose **Alarms** in the navigation pane.
#. Click the **Alarm Action Rules** tab.
#. Click **Create**. Set parameters such as the action rule name and action rule configuration.

   .. table:: **Table 1** Parameters for configuring an alarm action rule

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                         |
      +===================================+=====================================================================================================================================================+
      | Action Rule                       | Enter 1 to 64 characters. Only digits, letters, underscores (_), and hyphens (-) are allowed. Do not start or end with an underscore or hyphen.     |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Enterprise Project                | Select an enterprise project.                                                                                                                       |
      |                                   |                                                                                                                                                     |
      |                                   | This parameter is displayed only when the enterprise project function is enabled for the current account.                                           |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Enter a description for the rule. Up to 1,024 characters are allowed.                                                                               |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Topic                             | SMN topic. Select your desired topic from the drop-down list.                                                                                       |
      |                                   |                                                                                                                                                     |
      |                                   | If there is no topic you want to select, create one on the SMN console.                                                                             |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Message Template                  | Notification message template. Select your desired template from the drop-down list.                                                                |
      |                                   |                                                                                                                                                     |
      |                                   | If there is no message template you want to select, create one by referring to :ref:`Creating a Message Template on the LTS Console <lts_06_0011>`. |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

5. Click **OK**.

More Operations
---------------

After an alarm action rule is created, you can perform operations described in :ref:`Table 2 <lts_02_0926__en-us_topic_0000001791568665_en-us_topic_0000001744503349_en-us_topic_0000001164001658_en-us_topic_0169698264_table14918185010104>`.

.. _lts_02_0926__en-us_topic_0000001791568665_en-us_topic_0000001744503349_en-us_topic_0000001164001658_en-us_topic_0169698264_table14918185010104:

.. table:: **Table 2** Related operations

   +------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Operation                          | Description                                                                                                                                               |
   +====================================+===========================================================================================================================================================+
   | Modifying an alarm action rule     | Click **Modify** in the **Operation** column.                                                                                                             |
   +------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Exporting an alarm action rule     | Select one or more alarm action rules and click **Export**. If no alarm action rule is selected, clicking **Export** will export all alarm action rules.  |
   +------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Deleting an alarm action rule      | -  To delete a single rule, click **Delete** in the **Operation** column in the row that contains the rule, and then click **Yes** on the displayed page. |
   |                                    | -  To delete one or more rules, select them, click **Delete** above the rule list, and then click **Yes** on the displayed page.                          |
   |                                    |                                                                                                                                                           |
   |                                    |    .. note::                                                                                                                                              |
   |                                    |                                                                                                                                                           |
   |                                    |       Before deleting an alarm action rule, you need to delete the alarm rule bound to the action rule.                                                   |
   +------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Searching for an alarm action rule | Enter a rule name in the search box in the upper right corner and click |image1|.                                                                         |
   +------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000001791568973.png
