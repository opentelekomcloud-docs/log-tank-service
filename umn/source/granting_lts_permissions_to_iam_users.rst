:original_name: lts_04_0015.html

.. _lts_04_0015:

Granting LTS Permissions to IAM Users
=====================================

You can use `Identity and Access Management (IAM) <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0026.html>`__ for fine-grained permissions control for your LTS. With IAM, you can:

-  Create IAM users for personnel based on your enterprise's organizational structure. Each IAM user has their own identity credentials for accessing LTS resources.
-  Grant users only the permissions required to perform a given task based on their job responsibilities.
-  Entrust an account or a cloud service to perform efficient O&M on your LTS resources.

If your account does not require individual IAM users, you can skip this section.

This section describes the procedure for granting user permissions. :ref:`Figure 1 <lts_04_0015__en-us_topic_0191978428_fig13241132531318>` shows the process flow.

Prerequisites
-------------

Before granting permissions to user groups, learn about system-defined permissions in `Permissions Management <https://docs.otc.t-systems.com/log-tank-service/umn/service_overview/permissions_management.html#lts-03205>`__ for LTS.

Process Flow
------------

.. _lts_04_0015__en-us_topic_0191978428_fig13241132531318:

.. figure:: /_static/images/en-us_image_0000001999720813.png
   :alt: **Figure 1** Process of granting LTS permissions

   **Figure 1** Process of granting LTS permissions

#. .. _lts_04_0015__en-us_topic_0191978428_li1777449128:

   Log in to the IAM console. Create a user group on the IAM console and assign the **LTS FullAccess** permissions to the group. For details, see `Creating a User Group and Assigning Permissions <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0030.html>`__.

#. Create a user on the IAM console and add the user to the user group created in :ref:`1 <lts_04_0015__en-us_topic_0191978428_li1777449128>`. For details, see `Creating a User and Adding the User to a User Group <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0031.html>`__.

#. Log in to the LTS console as the created user, switch to the authorized region, and verify your permissions by performing operations on the console. For details, see `Logging In as an IAM User <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0032.html>`__.
