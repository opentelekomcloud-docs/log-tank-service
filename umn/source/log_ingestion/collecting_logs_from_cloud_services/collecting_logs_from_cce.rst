:original_name: lts_04_0511.html

.. _lts_04_0511:

Collecting Logs from CCE
========================

LTS can collect logs from Cloud Container Engine (CCE).

Prerequisites
-------------

-  ICAgent has been :ref:`installed <lts_02_0013>` and :ref:`added <lts_02_1033__en-us_topic_0000001118763740_section6798040548>` to the host group.
-  You have :ref:`disabled <lts_02_0014__en-us_topic_0000001167072801_li1088163816131>` **Output to AOM**.

Restrictions
------------

-  CCE cluster nodes whose container engine is Docker are supported.

-  CCE cluster nodes whose container engine is Containerd are supported. You must be using ICAgent 5.12.130 or later.

-  To collect container log directories mounted to host directories to LTS, you must configure the node file path.

-  Restrictions on the Docker storage driver: Currently, container file log collection supports only the overlay2 storage driver. devicemapper cannot be used as the storage driver. Run the following command to check the storage driver type:

   .. code-block::

      docker info | grep "Storage Driver"

-  If you select **Fixed log stream** for log ingestion, ensure that you have created a CCE cluster.

Procedure
---------

Perform the following operations to configure CCE log ingestion:

#. Log in to the LTS console.

#. In the navigation pane on the left, choose **Log Ingestion** and click **CCE (Cloud Container Engine)**.

#. **Select Log Stream**

   Choose between **Custom log stream** and **Fixed log stream** to suite your requirements.

   **Custom log stream**

   a. Select a log group from the **Log Group** drop-down list. If there are no desired log groups, click **Create Log Group** to create one.

   b. Select a log stream from the **Log Stream** drop-down list. If there are no desired log streams, click **Create Log Stream** to create one.

   c. Click **Next: Install Log Collection Component**.

      |image1|

   **Fixed log stream**

   Logs will be collected to a fixed log stream. By default, a CCE cluster has four types of log streams. Three of them are supported currently, including standard output/error (**stdout-**\ *{ClusterID}*), node file (**hostfile-**\ *{ClusterID}*), and container file (**containerfile-**\ *{ClusterID}*). Log streams are automatically named with a cluster ID. For example, if the cluster ID is **Cluster01**, the standard output/error log stream is **stdout-Cluster01**.

   Four log streams can be created in a CCE cluster, including standard output/error (**stdout-**\ *{ClusterID}*), node file (**hostfile-**\ *{ClusterID}*), container file (**containerfile-**\ *{ClusterID}*), and Kubernetes event (**event-**\ *{ClusterID}*) (coming soon). If one of them has been created in a log group, the log stream will no longer be created in the same log group or other log groups.

   a. Select a cluster from the **CCE Cluster** drop-down list.

   b. Select a log group from the **Log Group** drop-down list. If there are no desired log groups, click **Create Log Group** to create one.

   c. Click **Next: Install Log Collection Component**.

      |image2|

#. **Install Log Collection Component**

   To install the CCE log collection component, perform the following steps:

   1. Log in to the LTS console.

   2. In the navigation pane on the left, choose **Host Management**.

   3. On the displayed page, choose **Hosts** > **CCE clusters** and select a CCE cluster.

   4. Click **Upgrade ICAgent**.

   5. In the displayed dialog box, click **OK**.

   .. note::

      -  To ingest logs from CCE, the log collection component must be installed on hosts in the CCE cluster.

      -  If the ICAgent component has been installed in your CCE cluster, click **ICAgent Already Installed**.

         |image3|

#.  **Select Host Group**

   a. In the host group list, select one or more host groups to collect logs. If there are no desired host groups, click **Create** in the upper left corner of the list. On the displayed **Create Host Group** page, create a host group. For details, see :ref:`Creating a Host Group (Custom Identifier) <lts_02_1033__en-us_topic_0000001118763740_section6798040548>`.

      .. note::

         -  The host group to which the cluster belongs is selected by default. You can select another created host group as required.
         -  You can skip this step and configure host groups after the ingestion configuration is complete. There are two options to do this:

            -  On the LTS console, choose **Host Management** > **Host Groups** and associate host groups with ingestion configurations.
            -  On the LTS console, choose **Log Ingestion** in the navigation pane on the left and click an ingestion configuration. On the displayed page, add one or more host groups for association.

   b. Click **Next: Configure Collection**.

#. **Configurations**

   Specify collection rules. For details, see :ref:`Configurations <lts_04_0511__en-us_topic_0000001327056857_section1191613128141>`.

#. **Finish.**

   Click **Submit**.

.. _lts_04_0511__en-us_topic_0000001327056857_section1191613128141:

Configurations
--------------

When CCE is used to ingest logs, the configuration details are as follows:

#. **Basic Information**: Enter a name containing 1 to 64 characters. Only letters, digits, hyphens (-), underscores (_), and periods (.) are allowed. The name cannot start with a period or underscore, or end with a period.
#. **Data Source**: Select a data source type and configure it.

   -  **Container standard output**: Collects stderr and stdout logs of a specified container in the cluster.

      .. note::

         -  The standard output of the matched container is collected to the specified log stream. Standard output to AOM stops.
         -  The container standard output must be unique to a host.

   -  **Container file**: Collects file logs of a specified container in the cluster.
   -  **Node file**: Collects files of a specified node in the cluster.

      .. note::

         The collection path must be unique to a host.

   .. table:: **Table 1** Configuration parameters

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                         |
      +===================================+=====================================================================================================================================================================================================================================================================+
      | Container standard output         | Collects container standard output to AOM, and collects stderr and stdout logs of a specified container in the cluster.                                                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                                     |
      |                                   | Collecting container standard output to AOM: ICAgent is installed on hosts in the cluster by default, and logs is collected to AOM. The function of collecting container standard output to AOM is enabled. Disable this function to collect stdout streams to LTS. |
      |                                   |                                                                                                                                                                                                                                                                     |
      |                                   | Either stdout or stderr must be enabled.                                                                                                                                                                                                                            |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Container file                    | -  :ref:`Collection Paths <lts_04_1031__en-us_topic_0000001118501736_li17754123317308>`: LTS collects logs from the specified paths.                                                                                                                                |
      |                                   |                                                                                                                                                                                                                                                                     |
      |                                   |    .. note::                                                                                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                                     |
      |                                   |       -  If a container mount path has been configured for the CCE cluster workload, the paths added for this field are invalid. The collection paths take effect only after the mount path is deleted.                                                             |
      |                                   |       -  The collection path must be unique to a host.                                                                                                                                                                                                              |
      |                                   |                                                                                                                                                                                                                                                                     |
      |                                   | -  **Set Collection Filters**: Blacklisted directories or files will not be collected. If you specify a directory, all files in the directory are filtered out.                                                                                                     |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Node file                         | -  :ref:`Collection Paths <lts_04_1031__en-us_topic_0000001118501736_li17754123317308>`: LTS collects logs from the paths you added for this field.                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                     |
      |                                   |    .. note::                                                                                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                                     |
      |                                   |       The collection path must be unique to a host.                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                     |
      |                                   | -  **Set Collection Filters**: Blacklisted directories or files will not be collected. If you specify a directory, all files in the directory are filtered out.                                                                                                     |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. **Kubernetes Matching Rules**: Set this parameter only when the data source type is set to **Container standard output** or **Container file path**.

   .. table:: **Table 2** Kubernetes matching rules

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                               |
      +===================================+===========================================================================================================================================================================================================================================================================================================================+
      | Namespace Name Regular Expression | Specifies the container whose logs are to be collected based on the namespace name. Regular expression matching is supported.                                                                                                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                                                                                           |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                                                           |
      |                                   |    LTS will collect logs of the namespaces with names matching this expression. To collect logs of all namespaces, leave this field empty.                                                                                                                                                                                |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Pod Name Regular Expression       | Specifies the container whose logs are to be collected based on the Pod name. Regular expression matching is supported.                                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                                                                                                                                           |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                                                           |
      |                                   |    LTS will collect logs of the Pods with names matching this expression. To collect logs of all Pods, leave this field empty.                                                                                                                                                                                            |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Container Name Regular Expression | Specifies the container whose logs are to be collected based on the container name (the Kubernetes container name is defined in **spec.containers**). Regular expression matching is supported.                                                                                                                           |
      |                                   |                                                                                                                                                                                                                                                                                                                           |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                                                           |
      |                                   |    LTS will collect logs of the containers with names matching this expression. To collect logs of all containers, leave this field empty.                                                                                                                                                                                |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Container Label Whitelist         | Specifies the containers whose logs are to be collected. If you want to set a container label whitelist, **Label Key** is mandatory and **Label Value** is optional.                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                                                                                                           |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                                                           |
      |                                   |    LTS will match all containers with a container label containing either a **Label Key** with an empty corresponding **Label Value**, or a **Label Key** with its corresponding **Label Value**.                                                                                                                         |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Container Label Blacklist         | Specifies the containers whose logs are not to be collected. If you want to set a container label blacklist, **Label Key** is mandatory and **Label Value** is optional.                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                                                           |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                                                           |
      |                                   |    LTS will exclude all containers with a container label containing either a **Label Key** with an empty corresponding **Label Value**, or a **Label Key** with its corresponding **Label Value**.                                                                                                                       |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Container Label                   | After the **Container Label** is set, LTS adds related fields to logs.                                                                                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                                                                                                           |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                                                           |
      |                                   |    LTS adds the specified fields to the log when each **Label Key** has a corresponding **Label Value**. For example, if you enter "app" as the key and "app_alias" as the value, when the container label contains "app=lts", "{app_alias: lts}" will be added to the log.                                               |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Environment Variable Whitelist    | Specifies the containers whose logs are to be collected. If you want to set an environment variable whitelist, **Label Key** is mandatory and **Label Value** is optional.                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                                                                                                                           |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                                                           |
      |                                   |    LTS will match all containers with environment variables containing either an **Environment Variable Key** with an empty corresponding **Environment Variable Value**, or an **Environment Variable Key** with its corresponding **Environment Variable Value**.                                                       |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Environment Variable Blacklist    | Specifies the containers whose logs are not to be collected. If you want to set an environment variable blacklist, **Label Key** is mandatory and **Label Value** is optional.                                                                                                                                            |
      |                                   |                                                                                                                                                                                                                                                                                                                           |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                                                           |
      |                                   |    LTS will exclude all containers with environment variables containing either an **Environment Variable Key** with an empty corresponding **Environment Variable Value**, or an **Environment Variable Key** with its corresponding **Environment Variable Value**.                                                     |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Environment Variable Label        | After the environment variable label is set, the log service adds related fields to the log.                                                                                                                                                                                                                              |
      |                                   |                                                                                                                                                                                                                                                                                                                           |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                                                           |
      |                                   |    LTS adds the specified fields to the log when each **Environment Variable Key** has a corresponding **Environment Variable Value**. For example, if you enter "app" as the key and "app_alias" as the value, when the Kubernetes environment variable contains "app=lts", "{app_alias: lts}" will be added to the log. |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. **Advanced Settings**: Configure the log format and log time.

   .. table:: **Table 3** Log collection settings

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                 |
      +===================================+=============================================================================================================================================================================================================================================================+
      | Log Format                        | -  **Single-line**: Each log line is displayed as a single log event.                                                                                                                                                                                       |
      |                                   | -  **Multi-line**: Multiple lines of exception log events can be displayed as a single log event. This is helpful when you check logs to locate problems.                                                                                                   |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Log Time                          | **System time**: log collection time by default. It is displayed at the beginning of each log event.                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                             |
      |                                   | .. note::                                                                                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                                                                             |
      |                                   |    -  Log collection time is the time when logs are collected and sent by ICAgent to LTS.                                                                                                                                                                   |
      |                                   |    -  Log printing time is the time when logs are printed. ICAgent collects and sends logs to LTS with an interval of 1 second.                                                                                                                             |
      |                                   |    -  Restriction on log collection time: Logs are collected within 24 hours before and after the system time.                                                                                                                                              |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                                   | **Time wildcard**: You can set a time wildcard so that ICAgent will look for the log printing time as the beginning of a log event.                                                                                                                         |
      |                                   |                                                                                                                                                                                                                                                             |
      |                                   | -  If the time format in a log event is **2019-01-01 23:59:59.011**, the time wildcard should be set to **YYYY-MM-DD hh:mm:ss.SSS**.                                                                                                                        |
      |                                   | -  If the time format in a log event is **19-1-1 23:59:59.011**, the time wildcard should be set to **YY-M-D hh:mm:ss.SSS**.                                                                                                                                |
      |                                   |                                                                                                                                                                                                                                                             |
      |                                   | .. note::                                                                                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                                                                             |
      |                                   |    If a log event does not contain year information, ICAgent regards it as printed in the current year.                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                             |
      |                                   | Example:                                                                                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                                             |
      |                                   | .. code-block::                                                                                                                                                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                             |
      |                                   |    YY   - year (19)                                                                                                                                                                                                                                         |
      |                                   |    YYYY - year (2019)                                                                                                                                                                                                                                       |
      |                                   |    M    - month (1)                                                                                                                                                                                                                                         |
      |                                   |    MM   - month (01)                                                                                                                                                                                                                                        |
      |                                   |    D    - day (1)                                                                                                                                                                                                                                           |
      |                                   |    DD   - day (01)                                                                                                                                                                                                                                          |
      |                                   |    hh   - hours (23)                                                                                                                                                                                                                                        |
      |                                   |    mm   - minutes (59)                                                                                                                                                                                                                                      |
      |                                   |    ss   - seconds (59)                                                                                                                                                                                                                                      |
      |                                   |    SSS - millisecond (999)                                                                                                                                                                                                                                  |
      |                                   |    hpm     - hours (03PM)                                                                                                                                                                                                                                   |
      |                                   |    h:mmpm    - hours:minutes (03:04PM)                                                                                                                                                                                                                      |
      |                                   |    h:mm:sspm  - hours:minutes:seconds (03:04:05PM)                                                                                                                                                                                                          |
      |                                   |    hh:mm:ss ZZZZ (16:05:06 +0100)                                                                                                                                                                                                                           |
      |                                   |    hh:mm:ss ZZZ  (16:05:06 CET)                                                                                                                                                                                                                             |
      |                                   |    hh:mm:ss ZZ   (16:05:06 +01:00)                                                                                                                                                                                                                          |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Log Segmentation                  | This parameter needs to be specified if the **Log Format** is set to **Multi-line**. **By generation time** indicates that a time wildcard is used to detect log boundaries, whereas **By regular expression** indicates that a regular expression is used. |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Regular Expression                | You can set a regular expression to look for a specific pattern to indicate the beginning of a log event. This parameter needs to be specified when you select **Multi-line** for **Log Format** and **By regular expression** for **Log Segmentation**.    |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. note::

      The time wildcard and regular expression will look for the specified pattern right from the beginning of each log line. If no match is found, the system time, which may be different from the time in the log event, is used. In general cases, you are advised to select **Single-line** for **Log Format** and **System time** for **Log Time**.

.. |image1| image:: /_static/images/en-us_image_0000001424310404.png
.. |image2| image:: /_static/images/en-us_image_0000001536874781.png
.. |image3| image:: /_static/images/en-us_image_0000001474668261.png
