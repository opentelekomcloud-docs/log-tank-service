:original_name: lts-03205.html

.. _lts-03205:

Permissions
===========

Description
-----------

If you need to grant your enterprise personnel permission to access your LTS resources, use Identity and Access Management (IAM). IAM provides identity authentication, fine-grained permissions management, and access control. IAM helps you secure access to your LTS resources.

With IAM, you can create IAM users and grant them permission to access only specific resources. For example, if you want some software developers in your enterprise to be able to use LTS resources but do not want them to be able to delete resources or perform any other high-risk operations, you can create IAM users and grant permission to use LTS resources but not permission to delete them.

If your account does not require individual IAM users for permissions management, you can skip this section.

IAM is a free service. You only pay for the resources in your account. For more information about IAM, see `IAM Service Overview <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0026.html>`__.

LTS Permissions
---------------

New users do not have any permissions assigned by default. You need to first add them to one or more groups and then attach policies or roles to these groups. The users then inherit permissions from the groups and can perform specified operations on LTS based on the permissions they have been assigned.

LTS is a project-level service deployed for specific regions. When you set **Scope** to **Region-specific projects** and select the specified projects in the specified regions, the users only have permissions for LTS in the selected projects. If you select **All projects**, the users have permissions for LTS in all region-specific projects. When accessing LTS, the users need to switch to the authorized region.

You can grant permissions by using roles and policies.

-  Roles: A coarse-grained authorization strategy that defines permissions by job responsibility. Only a limited number of service-level roles are available for authorization. Cloud services often depend on each other. When you grant permissions using roles, you also need to attach any existing role dependencies. Roles are not ideal for fine-grained authorization and least privilege access.
-  Policies: A fine-grained authorization strategy that defines permissions required to perform operations on specific cloud resources under certain conditions. This type of authorization is more flexible and is ideal for least privilege access.

The system permissions supported by LTS are listed in :ref:`Table 1 <lts-03205__en-us_topic_0180792016_table7749356973>`.

.. _lts-03205__en-us_topic_0180792016_table7749356973:

.. table:: **Table 1** System-defined permissions for LTS

   +--------------------+---------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------+
   | Role/Policy Name   | Description                                                                           | Type                  | Dependencies                                             |
   +====================+=======================================================================================+=======================+==========================================================+
   | LTS FullAccess     | Full permissions for LTS. Users with these permissions can perform operations on LTS. | System-defined policy | CCE Administrator, OBS Administrator, and AOM FullAccess |
   +--------------------+---------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------+
   | LTS ReadOnlyAccess | Read-only permissions for LTS. Users with these permissions can only view LTS data.   | System-defined policy | CCE Administrator, OBS Administrator, and AOM FullAccess |
   +--------------------+---------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------+
   | LTS Administrator  | Administrator permissions for LTS.                                                    | System-defined role   | **Tenant Guest** and **Tenant Administrator**            |
   +--------------------+---------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------+

:ref:`Table 2 <lts-03205__en-us_topic_0180792016_table121207991710>` lists the common operations supported by system-defined permissions for LTS.

.. _lts-03205__en-us_topic_0180792016_table121207991710:

.. table:: **Table 2** Common operations supported by system-defined permissions

   +---------------------------------------+----------------+--------------------+-------------------+
   | Operation                             | LTS FullAccess | LTS ReadOnlyAccess | LTS Administrator |
   +=======================================+================+====================+===================+
   | Querying a log group                  | Y              | Y                  | Y                 |
   +---------------------------------------+----------------+--------------------+-------------------+
   | Creating a log group                  | Y              | x                  | Y                 |
   +---------------------------------------+----------------+--------------------+-------------------+
   | Modifying a log group                 | Y              | x                  | Y                 |
   +---------------------------------------+----------------+--------------------+-------------------+
   | Deleting a log group                  | Y              | x                  | Y                 |
   +---------------------------------------+----------------+--------------------+-------------------+
   | Querying a log stream                 | Y              | Y                  | Y                 |
   +---------------------------------------+----------------+--------------------+-------------------+
   | Creating a log stream                 | Y              | x                  | Y                 |
   +---------------------------------------+----------------+--------------------+-------------------+
   | Modifying a log stream                | Y              | x                  | Y                 |
   +---------------------------------------+----------------+--------------------+-------------------+
   | Deleting a log stream                 | Y              | x                  | Y                 |
   +---------------------------------------+----------------+--------------------+-------------------+
   | Configuring log collection from hosts | Y              | x                  | Y                 |
   +---------------------------------------+----------------+--------------------+-------------------+
   | Viewing a log transfer task           | Y              | Y                  | Y                 |
   +---------------------------------------+----------------+--------------------+-------------------+
   | Creating a log transfer task          | Y              | x                  | Y                 |
   +---------------------------------------+----------------+--------------------+-------------------+
   | Modifying a log transfer task         | Y              | x                  | Y                 |
   +---------------------------------------+----------------+--------------------+-------------------+
   | Deleting a log transfer task          | Y              | x                  | Y                 |
   +---------------------------------------+----------------+--------------------+-------------------+
   | Enabling a log transfer task          | Y              | x                  | Y                 |
   +---------------------------------------+----------------+--------------------+-------------------+
   | Disabling a log transfer task         | Y              | x                  | Y                 |
   +---------------------------------------+----------------+--------------------+-------------------+
   | Installing ICAgent                    | Y              | x                  | Y                 |
   +---------------------------------------+----------------+--------------------+-------------------+
   | Upgrading ICAgent                     | Y              | x                  | Y                 |
   +---------------------------------------+----------------+--------------------+-------------------+
   | Uninstalling ICAgent                  | Y              | x                  | Y                 |
   +---------------------------------------+----------------+--------------------+-------------------+
