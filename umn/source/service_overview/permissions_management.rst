:original_name: lts-03205.html

.. _lts-03205:

Permissions Management
======================

Description
-----------

If you need to assign different permissions to employees in your enterprise to access your LTS resources, is a good choice for fine-grained permissions management. IAM provides identity authentication, permissions management, and access control, helping you secure access to your LTS resources.

With IAM, you can use your account to create IAM users for your employees, and assign permissions to the users to control their access to LTS resources. For example, some software developers in your enterprise need to use LTS resources but should not delete them or perform other high-risk operations. In this case, you can create IAM users for the software developers and grant them only the permissions required.

If your account does not need individual IAM users for permissions management, you may skip over this section.

IAM can be used for free. You pay only for the resources in your account. For more information about IAM, see `IAM Service Overview <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0026.html>`__.

LTS Permissions
---------------

By default, new IAM users do not have permissions assigned. You need to add users to one or more groups, and attach permissions policies or roles to these groups. Users inherit permissions from the groups to which they are added and can perform specified operations on cloud services based on the permissions.

LTS is a project-level service deployed and accessed in specific physical regions. To assign LTS permissions to a user group, specify the scope as region-specific projects and select projects for the permissions to take effect. If **All projects** is selected, the permissions will take effect for the user group in all region-specific projects. When accessing LTS, the users need to switch to a region where they have been authorized to use LTS.

Policies: A type of fine-grained authorization mechanism that defines permissions required to perform operations on specific cloud resources under certain conditions. This mechanism allows for more flexible policy-based authorization, meeting requirements for secure access control. For example, you can grant Elastic Cloud Server (ECS) users only the permissions for managing a certain type of ECSs. Most policies define permissions based on APIs.

The system permissions supported by LTS are listed in :ref:`Table 1 <lts-03205__en-us_topic_0180792016_table7749356973>`.

.. _lts-03205__en-us_topic_0180792016_table7749356973:

.. table:: **Table 1** LTS system permissions

   +--------------------+---------------------------------------------------------------------------------------+-----------------------+------------------------------------------------------------------------------------+
   | Name               | Description                                                                           | Type                  | Dependency                                                                         |
   +====================+=======================================================================================+=======================+====================================================================================+
   | LTS FullAccess     | Full permissions for LTS. Users with these permissions can perform operations on LTS. | System-defined policy | CCE Administrator, OBS Administrator, and AOM FullAccess                           |
   +--------------------+---------------------------------------------------------------------------------------+-----------------------+------------------------------------------------------------------------------------+
   | LTS ReadOnlyAccess | Read-only permissions for LTS. Users with these permissions can only view LTS data.   | System-defined policy | CCE Administrator, OBS Administrator, and AOM FullAccess                           |
   +--------------------+---------------------------------------------------------------------------------------+-----------------------+------------------------------------------------------------------------------------+
   | LTS Administrator  | Administrator permissions for LTS.                                                    | System-defined role   | This role is dependent on the **Tenant Guest** and **Tenant Administrator** roles. |
   +--------------------+---------------------------------------------------------------------------------------+-----------------------+------------------------------------------------------------------------------------+

:ref:`Table 2 <lts-03205__en-us_topic_0180792016_table121207991710>` lists the common operations supported by each system-defined policy and role of LTS. Choose the appropriate policies and roles according to this table.

.. _lts-03205__en-us_topic_0180792016_table121207991710:

.. table:: **Table 2** Common operations supported by each LTS system policy or role

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

To use a custom fine-grained policy, log in to IAM as the administrator and select fine-grained permissions of LTS as required.

:ref:`Table 3 <lts-03205__en-us_topic_0180792016_table1643135052013>` describes fine-grained permission dependencies of LTS.

.. _lts-03205__en-us_topic_0180792016_table1643135052013:

.. table:: **Table 3** Fine-grained permission dependencies of LTS

   +-----------------------------------+------------------------------------+---------------------------------------+
   | Permission                        | Description                        | Dependency                            |
   +===================================+====================================+=======================================+
   | lts:agents:list                   | List agents                        | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:buckets:get                   | Get bucket                         | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:groups:put                    | Put log group                      | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:transfers:create              | Create transfer                    | obs:bucket:PutBucketAcl               |
   |                                   |                                    |                                       |
   |                                   |                                    | obs:bucket:GetBucketAcl               |
   |                                   |                                    |                                       |
   |                                   |                                    | obs:bucket:GetEncryptionConfiguration |
   |                                   |                                    |                                       |
   |                                   |                                    | obs:bucket:HeadBucket                 |
   |                                   |                                    |                                       |
   |                                   |                                    | dis:streams:list                      |
   |                                   |                                    |                                       |
   |                                   |                                    | dis:streamPolicies:list               |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:groups:get                    | Get log group                      | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:transfers:put                 | Put transfer                       | obs:bucket:PutBucketAcl               |
   |                                   |                                    |                                       |
   |                                   |                                    | obs:bucket:GetBucketAcl               |
   |                                   |                                    |                                       |
   |                                   |                                    | obs:bucket:GetEncryptionConfiguration |
   |                                   |                                    |                                       |
   |                                   |                                    | obs:bucket:HeadBucket                 |
   |                                   |                                    |                                       |
   |                                   |                                    | dis:streams:list                      |
   |                                   |                                    |                                       |
   |                                   |                                    | dis:streamPolicies:list               |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:resourceTags:delete           | Delete resource tag                | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:ecsOsLogPaths:list            | List ecs os logs paths             | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:structConfig:create           | Create struct config               | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:agentsConf:get                | Get agent conf                     | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:logIndex:list                 | Get log index                      | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:transfers:delete              | Delete transfer                    | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:regex:create                  | Create struct regex                | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:subscriptions:delete          | Delete subscription                | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:overviewLogsLast:list         | List overview last logs            | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:logIndex:get                  | Get log index                      | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:sqlalarmrules:create          | Create alarm options               | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:agentsConf:create             | Create agent conf                  | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:sqlalarmrules:get             | Get alarm options                  | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:datasources:batchdelete       | Batch delete datasource            | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:structConfig:put              | Update struct config               | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:groups:list                   | List log groups                    | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:sqlalarmrules:delete          | Delete alarm options               | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:transfers:action              | Enabled transfer                   | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:datasources:post              | Post datasource                    | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:topics:create                 | Create log topic                   | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:resourceTags:get              | Query resource tags                | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:logs:list                     | List logs                          | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:subscriptions:create          | Create subscription                | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:overviewLogsTopTopic:get      | List overview top logs             | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:datasources:put               | Put datasource                     | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:structConfig:delete           | Delete struct config               | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:logIndex:delete               | Deleting a specified log index     | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:topics:delete                 | Delete log topics                  | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:agentSupportedOsLogPaths:list | List agent supported os logs paths | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:topics:put                    | Put log topic                      | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:agentHeartbeat:post           | Post agent heartbeat               | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:logsByName:upload             | Upload logs by name                | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:buckets:list                  | List buckets                       | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:logIndex:post                 | Create log index                   | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:logContext:list               | List logs context                  | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:groups:delete                 | Delete log group                   | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:resourceTags:put              | Update resource tags               | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:structConfig:get              | Get struct config                  | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:overviewLogTotal:get          | Get overview logs total            | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:subscriptions:put             | Put subscription                   | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:subscriptions:list            | List subscription                  | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:datasources:delete            | Delete datasource                  | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:transfersStatus:get           | List transfer status               | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:logIndex:put                  | Put log index                      | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:sqlalarmrules:put             | Modify alarm options               | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:logs:upload                   | Upload logs                        | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:agentDetails:list             | List agent diagnostic log          | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:agentsConf:put                | Put agent conf                     | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:logstreams:list               | Check logstream resources          | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:subscriptions:get             | Get subscription                   | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:disStreams:list               | Query DIS pipe                     | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:groupTopics:put               | Create log group and log topic     | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:resourceInstance:list         | Query resource instance            | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:transfers:list                | List transfers                     | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:topics:get                    | Get log topic                      | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:agentsConf:delete             | Delete agent conf                  | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:agentEcs:list                 | List agent ecs                     | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:indiceLogs:list               | Search indiceLogs                  | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
   | lts:topics:list                   | List log topic                     | None                                  |
   +-----------------------------------+------------------------------------+---------------------------------------+
