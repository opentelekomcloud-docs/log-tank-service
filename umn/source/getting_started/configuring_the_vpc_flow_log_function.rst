:original_name: lts_01_0009.html

.. _lts_01_0009:

Configuring the VPC Flow Log Function
=====================================

Scenarios
---------

A Virtual Private Cloud (VPC) flow log captures information about the traffic going to and from your VPC. You can use flow logs to monitor network traffic, analyze network attacks, and determine whether security groups and firewall rules need to be modified.

To obtain traffic details of VPC Network Interface Cards (NICs), you can enable Log Tank Service (LTS) and view logs about the NICs on the LTS console.

This section describes how to create a VPC flow log to report logs to LTS.

Constraints
-----------

-  A VPC is available.
-  Currently, only C3, CC3, and P2 ECSs are supported.

Operation Process
-----------------

.. _lts_01_0009__en-us_topic_0224007674_fig14917812017:

.. figure:: /_static/images/en-us_image_0224007643.png
   :alt: **Figure 1** Flowchart

   **Figure 1** Flowchart

Operations in :ref:`Figure 1 <lts_01_0009__en-us_topic_0224007674_fig14917812017>` are performed on different consoles:

-  LTS console: Creating a log group and creating a log topic.
-  VPC console: Creating a VPC flow log and viewing the flow log.

Creating a Log Group
--------------------

#. Log in to the management console.

#. In the upper left corner of the management console, select the target region and project.

#. Click **Service List** and choose **Management & Deployment** > **Log Tank Service**.


   .. figure:: /_static/images/en-us_image_0224007663.png
      :alt: **Figure 2** Log management

      **Figure 2** Log management

#. On the **Log Management** page, click **Create Log Group**.


   .. figure:: /_static/images/en-us_image_0224007629.png
      :alt: **Figure 3** Creating a log group

      **Figure 3** Creating a log group

#. On the displayed page, enter a log group name.

   .. table:: **Table 1** Parameter description

      +------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter              | Description                                                                                                                                                                                                 | Example Value         |
      +========================+=============================================================================================================================================================================================================+=======================+
      | Log Group Name         | Specifies the log group name which must be globally unique. The configuration rules are as follows:                                                                                                         | lts-group-wule        |
      |                        |                                                                                                                                                                                                             |                       |
      |                        | -  Must be a string of 1 to 64 characters.                                                                                                                                                                  |                       |
      |                        | -  Only allows uppercase and lowercase letters, digits, underscores (_), hyphens (-), and periods (.). The name cannot start or end with a period.                                                          |                       |
      +------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Log Retention Duration | Specifies the time period, in the unit of days, of storing logs in the LTS database. The default retention period for logs is seven days. Any logs stored longer than the retention period will be deleted. | 7                     |
      +------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. Click **OK**.

Creating a Log Topic
--------------------

To create a log topic in the log group, perform the following operations:

#. Log in to the management console.
#. In the upper left corner of the management console, select the target region and project.
#. Click **Service List** and choose **Management & Deployment** > **Log Tank Service**.

4. In the log group list, click the name of the target log group.


   .. figure:: /_static/images/en-us_image_0224007683.png
      :alt: **Figure 4** Log topic list

      **Figure 4** Log topic list

5. On the displayed page, click **Create Log Topic**.


   .. figure:: /_static/images/en-us_image_0224007618.png
      :alt: **Figure 5** Creating a log topic

      **Figure 5** Creating a log topic

6. On the displayed page, enter a name.

   .. table:: **Table 2** Parameter description

      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                        | Example Value         |
      +=======================+====================================================================================================================================================+=======================+
      | Log Topic Name        | Specifies the log topic name. The name must be unique in a log group. The configuration rules are as follows:                                      | LogTopic1             |
      |                       |                                                                                                                                                    |                       |
      |                       | -  Must be a string of 1 to 64 characters.                                                                                                         |                       |
      |                       | -  Only allows uppercase and lowercase letters, digits, underscores (_), hyphens (-), and periods (.). The name cannot start or end with a period. |                       |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

7. Click **OK**.

Creating a VPC Flow Log
-----------------------

#. Log in to the management console.

#. In the upper left corner of the management console, select the target region and project.

#. Choose **Service List** > **Network** > **Virtual Private Cloud**.

#. In the navigation pane on the left, choose **VPC Flow Logs**.

#. In the upper right corner, click **Create VPC Flow Log**. On the displayed page, configure parameters as prompted.


   .. figure:: /_static/images/en-us_image_0224007690.png
      :alt: **Figure 6** Creating a VPC flow log

      **Figure 6** Creating a VPC flow log

   .. table:: **Table 3** Parameter description

      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                                                                 | Example Value         |
      +=======================+=============================================================================================================================================================================================+=======================+
      | Name                  | Specifies the VPC flow log name.                                                                                                                                                            | flowlog-495d          |
      |                       |                                                                                                                                                                                             |                       |
      |                       | The VPC flow log name can contain a maximum of 64 characters, which may consist of letters, digits, underscores (_), hyphens (-), and periods (.). The name cannot contain spaces.          |                       |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Resource Type         | Specifies the type of resources whose traffic is to be logged. Currently, **Resource Type** can only be **NIC**.                                                                            | NIC                   |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Select NIC            | Specifies the specific NIC whose traffic is to be logged. You can select only one NIC.                                                                                                      | ``-``                 |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Filter                | -  **All**: specifies that both accepted and rejected traffic of the specified resource will be logged.                                                                                     | All                   |
      |                       | -  **Accepted traffic**: specifies that only accepted traffic of the specified resource will be logged. Accepted traffic refers to the traffic permitted by the security group or firewall. |                       |
      |                       | -  **Rejected traffic**: specifies that only rejected traffic of the specified resource will be logged. Rejected traffic refers to the traffic not permitted by the firewall.               |                       |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Log Group             | Specifies the log group created in LTS.                                                                                                                                                     | lts-group-wule        |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Log Topic             | Specifies the log topic created in LTS.                                                                                                                                                     | LogTopic1             |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Description           | Provides supplementary information about the VPC flow log. This parameter is optional.                                                                                                      | ``-``                 |
      |                       |                                                                                                                                                                                             |                       |
      |                       | The VPC flow log description can contain a maximum of 255 characters and cannot contain angle brackets (< or >).                                                                            |                       |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. Click **OK**.

Viewing a VPC Flow Log
----------------------

The capture window is approximately 10 minutes, which indicates that a flow log record will be generated every 10 minutes. After creating a VPC flow log, you need to wait about 10 minutes before you can view the flow log record.

#. Log in to the management console.

#. In the upper left corner of the management console, select the target region and project.

#. Choose **Service List** > **Network** > **Virtual Private Cloud**.

#. In the navigation pane on the left, choose **VPC Flow Logs**.

#. Locate the target VPC flow log and click **View Log Record** in the **Operation** column to view information about the flow log record in LTS.


   .. figure:: /_static/images/en-us_image_0224007651.png
      :alt: **Figure 7** Viewing a log record

      **Figure 7** Viewing a log record


   .. figure:: /_static/images/en-us_image_0224007665.png
      :alt: **Figure 8** Viewing details of a log record

      **Figure 8** Viewing details of a log record

   The flow log record is in the following format:

   .. code-block::

      <version> <project-id> <interface-id> <srcaddr> <dstaddr> <srcport> <dstport> <protocol> <packets> <bytes> <start> <end> <action> <log-status>

   Example 1: The following is an example of a flow log record in which traffic was allowed during the capture window:

   .. code-block::

      1 5f67944957444bd6bb4fe3b367de8f3d 1d515d18-1b36-47dc-a983-bd6512aed4bd 192.168.0.154 192.168.3.25 38929 53 17 1 96 1548752136 1548752736 ACCEPT OK

   Value **1** indicates the VPC flow log version. Traffic with a size of 96 bytes to NIC **1d515d18-1b36-47dc-a983-bd6512aed4bd** during the past 10 minutes (from 16:55:36 to 17:05:36 on January 29, 2019) was allowed. A data packet was transmitted over the UDP protocol from source IP address **192.168.0.154** and port **38929** to destination IP address **192.168.3.25** and port **53**.

   Example 2: The following is an example of a flow log record in which no data was recorded during the capture window:

   .. code-block::

      1 5f67944957444bd6bb4fe3b367de8f3d 1d515d18-1b36-47dc-a983-bd6512aed4bd - - - - - - - 1431280876 1431280934 - NODATA

   Example 3: The following is an example of a flow log record in which records were skipped during the capture window:

   .. code-block::

      1 5f67944957444bd6bb4fe3b367de8f3d 1d515d18-1b36-47dc-a983-bd6512aed4bd - - - - - - - 1431280876 1431280934 - SKIPDATA

   :ref:`Table 4 <lts_01_0009__en-us_topic_0224007674_t9a4cf19ba62a45f0ac75fd5bebea45c6>` describes the fields of a flow log record.

   .. _lts_01_0009__en-us_topic_0224007674_t9a4cf19ba62a45f0ac75fd5bebea45c6:

   .. table:: **Table 4** Log field description

      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | Field                 | Description                                                                                                                                                | Example Value                        |
      +=======================+============================================================================================================================================================+======================================+
      | version               | Specifies the VPC flow log version.                                                                                                                        | 1                                    |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | project-id            | Specifies the project ID.                                                                                                                                  | 5f67944957444bd6bb4fe3b367de8f3d     |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | interface-id          | Specifies the ID of the NIC for which the traffic is recorded.                                                                                             | 1d515d18-1b36-47dc-a983-bd6512aed4bd |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | srcaddr               | Specifies the source IP address.                                                                                                                           | x.x.x.x                              |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | dstaddr               | Specifies the destination IP address.                                                                                                                      | x.x.x.x                              |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | srcport               | Specifies the source port of the traffic.                                                                                                                  | 38929                                |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | dstport               | Specifies the destination port of the traffic.                                                                                                             | 53                                   |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | protocol              | Specifies the Internet Assigned Numbers Authority (IANA) protocol number of the traffic. For details, see Assigned Internet Protocol Numbers.              | 17                                   |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | packets               | Specifies the number of packets transferred during the capture window.                                                                                     | 1                                    |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | bytes                 | Specifies the number of bytes transferred during the capture window.                                                                                       | 96                                   |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | start                 | Specifies the time, in Unix seconds, of the start of the capture window.                                                                                   | 1548752136                           |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | end                   | Specifies the time, in Unix seconds, of the end of the capture window.                                                                                     | 1548752736                           |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | action                | Specifies the action associated with the traffic:                                                                                                          | ACCEPT                               |
      |                       |                                                                                                                                                            |                                      |
      |                       | -  **ACCEPT**: The recorded traffic was permitted by the security group or firewall.                                                                       |                                      |
      |                       | -  **REJECT**: The recorded traffic was not permitted by the firewall.                                                                                     |                                      |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+
      | log-status            | Specifies the logging status of the VPC flow log:                                                                                                          | OK                                   |
      |                       |                                                                                                                                                            |                                      |
      |                       | -  **OK**: Data is logging normally to the chosen destinations.                                                                                            |                                      |
      |                       | -  **NODATA**: There was no network traffic to or from the NIC during the capture window.                                                                  |                                      |
      |                       | -  **SKIPDATA**: Some flow log records were skipped during the capture window. This may be caused by an internal capacity constraint or an internal error. |                                      |
      +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------+

   You can enter a keyword on the log topic details page on the LTS console to search for flow log records.
