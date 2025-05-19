:original_name: lts_03_0002.html

.. _lts_03_0002:

How Do I Install ICAgent by Creating an Agency?
===============================================

When installing ICAgent, you can create an IAM agency, and ICAgent will automatically obtain an AK/SK pair and generate the ICAgent installation command.

Creating an Agency
------------------

#. Log in to the management console and choose **Identity and Access Management** in the service list.
#. Choose **Agencies** in the navigation pane.
#. Click **Create Agency** in the upper right corner and set parameters as follows:

   .. table:: **Table 1** Agency parameters

      =============== ====================================================
      Parameter       Description
      =============== ====================================================
      Agency Name     Set the agency name. For example, **lts_ecm_trust**.
      Agency Type     Select **Cloud service**.
      Cloud Service   Select **ECS**.
      Validity Period Select **Unlimited**.
      Description     (Optional) Provide details about the agency.
      =============== ====================================================

#. Click **Next**.
#. Search for **LTS Administrator** and **APM Administrator** in the permission search box and select them.
#. Click **Next**, set the authorization scope to **Region-specific projects**, and select projects.
#. Click **OK**. The authorization takes effect 15 to 30 minutes later.

Making an Agency Effective
--------------------------

#. Choose **Service List** > **Computing** > **Elastic Cloud Server**.
#. Click the ECS where ICAgent is installed. The ECS details page is displayed.
#. Select the created agency and confirm the configuration to make the agency effective.
