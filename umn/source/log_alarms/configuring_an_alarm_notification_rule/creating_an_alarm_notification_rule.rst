:original_name: lts_02_0926.html

.. _lts_02_0926:

Creating an Alarm Notification Rule
===================================

LTS allows you to create custom alarm notification rules. An alarm notification rule associates an SMN topic with a message template. When an alarm is triggered, SMN automatically sends an alarm notification via channels like SMS or email, using the specified message template.

Prerequisites
-------------

-  A topic has been created.
-  A topic policy has been configured.
-  A subscriber has been added to the topic. A subscriber is the recipient of the notification, for example, an email or SMS message receiver.

Precaution
----------

You can create up to 1,000 alarm notification rules. If this limit has been reached, delete unnecessary rules.


Creating an Alarm Notification Rule
-----------------------------------

#. Log in to the management console and choose **Management & Deployment** > **Log Tank Service**.
#. Choose **Log Alarms** in the navigation pane.
#. Click the **Alarm Action Rules** tab.
#. Click **Create**. Set parameters such as the notification rule name and notification rule configuration.

   .. table:: **Table 1** Parameters for configuring an alarm action rule

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                     |
      +===================================+=================================================================================================================================================+
      | Action Rule                       | Enter 1 to 64 characters. Only digits, letters, underscores (_), and hyphens (-) are allowed. Do not start or end with an underscore or hyphen. |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
      | Enterprise Project                | Select an enterprise project.                                                                                                                   |
      |                                   |                                                                                                                                                 |
      |                                   | This parameter is displayed only when the enterprise project function is enabled for the current account.                                       |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Enter a description for the rule. Up to 1,024 characters are allowed.                                                                           |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
      | Topic                             | SMN topic. Select your desired topic from the drop-down list.                                                                                   |
      |                                   |                                                                                                                                                 |
      |                                   | If there is no topic you want to select, create one on the SMN console.                                                                         |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
      | Message Template                  | Notification message template. Select your desired template from the drop-down list.                                                            |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+

5. Click **OK**.
