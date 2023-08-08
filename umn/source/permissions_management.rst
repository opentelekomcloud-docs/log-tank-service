:original_name: lts_04_0015.html

.. _lts_04_0015:

Permissions Management
======================

This chapter describes how to use `Identity and Access Management (IAM) <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0026.html>`__ for fine-grained permissions control for your LTS. With IAM, you can:

-  Create IAM users for personnel based on your enterprise's organizational structure. Each IAM user has their own identity credentials for accessing LTS resources
-  Grant only the permissions required for users to perform a specific task.
-  Entrust an account or a cloud service to perform professional and efficient O&M on your LTS resources.

If your account meets your permissions requirements, skip this section.

This section describes the procedure for granting user permissions. :ref:`Figure 1 <lts_04_0015__en-us_topic_0191978428_fig1591121431319>` shows the process flow.

Prerequisites
-------------

Before granting permissions to user groups, learn about "Permissions Management" in the section *Service Overview*) for LTS and select the permissions as required. For system permissions of other cloud services, see `Permissions <https://docs.otc.t-systems.com/permissions/index.html>`__ supported by IAM.

Process Flow
------------

.. _lts_04_0015__en-us_topic_0191978428_fig1591121431319:

.. figure:: /_static/images/en-us_image_0231061605.png
   :alt: **Figure 1** Process of granting permissions to a user

   **Figure 1** Process of granting permissions to a user

#. .. _lts_04_0015__en-us_topic_0191978428_li1777449128:

   Log in to the IAM console. Create a user group on the IAM console and grant the **LTS FullAccess** permission to the user group. For details, see `Create a user group and grant it permissions <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0030.html>`__.

   .. note::

      If you select the **LTS FullAccess** permissions, the **Tenant Guest** policy that the permission depends on is automatically selected. You also need to grant the **Tenant Administrator** policy for the global service project to the user group.

#. Create a user on the IAM console and add the user to the user group created in :ref:`1 <lts_04_0015__en-us_topic_0191978428_li1777449128>`. For details, see `Create an IAM user and add it to the created user group <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0031.html>`__.

#. Log in to the console by using the created user and verify permissions in the authorized region. For details, see `Log in as the IAM user <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0032.html>`__ and verify permissions.
