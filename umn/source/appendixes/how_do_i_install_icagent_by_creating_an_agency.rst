:original_name: lts_03_0002.html

.. _lts_03_0002:

How Do I Install ICAgent by Creating an Agency?
===============================================

When installing ICAgent, you can create an IAM agency, and ICAgent will automatically obtain an AK/SK pair and generate the ICAgent installation command.

Procedure
---------

#. Log in to the console and choose **Service List** > **Management & Deployment** > **Identity and Access Management**.
#. Choose **Agencies** in the navigation pane on the left.
#. Click **Create Agency** in the upper right corner and set parameters as follows:

   .. table:: **Table 1** Agency parameters

      +-----------------------------------+------------------------------------------------------------------------+
      | Parameter                         | Description                                                            |
      +===================================+========================================================================+
      | Agency Name                       | Set the agency name. For example, **lts_ecm_trust**.                   |
      +-----------------------------------+------------------------------------------------------------------------+
      | Agency Type                       | Select **Cloud service**.                                              |
      +-----------------------------------+------------------------------------------------------------------------+
      | Cloud Service                     | Select **Elastic Cloud Server (ECS) and Bare Metal Server (BMS)**.     |
      +-----------------------------------+------------------------------------------------------------------------+
      | Validity Period                   | Select **Unlimited**.                                                  |
      +-----------------------------------+------------------------------------------------------------------------+
      | Description                       | (Optional) Provide details about the agency.                           |
      +-----------------------------------+------------------------------------------------------------------------+
      | Permissions                       | a. In the **Permissions** area, click **Assign Permissions**.          |
      |                                   | b. Search for **LTS Admin** and **APM Administrator** and select them. |
      |                                   | c. Click **OK** on the **Assign Permissions** page.                    |
      +-----------------------------------+------------------------------------------------------------------------+

#. Click **OK** on the **Create Agency** page.

Making an Agency Effective
--------------------------

#. Choose **Service List** > **Computing** > **Elastic Cloud Server**.
#. Click the ECS where ICAgent is installed. The ECS details page is displayed.
#. Select the created agency and confirm the configuration to make the agency effective.
#. (Optional) If you want to set an agency when you are purchasing an ECS, do as follows: Click **Buy ECS** on the ECS console. In the **Configure Advanced Settings** step, set **Advanced Options** to **Configure now** and select an agency from the **Agency** drop-down list. Set the other parameters and click **Next**.
