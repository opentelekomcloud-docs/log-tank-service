:original_name: lts_07_1119.html

.. _lts_07_1119:

Managing ICAgent in Container Scenarios
=======================================

ICAgent is a log collection tool for LTS. It runs on hosts where logs need to be collected. This section describes how to install ICAgent on a host, upgrade ICAgent, uninstall ICAgent, and check the ICAgent status.

Container scenarios cover services deployed on Kubernetes container platforms .

Installing ICAgent
------------------

-  .. _lts_07_1119__en-us_topic_0000002452562620_li34651214281:

   Installing ICAgent in a CCE cluster

   #. Choose **Host Management** > **Hosts** in the navigation pane.

   #. Click the **CCE Cluster** tab. Select **ICAgent Status** in the search box to filter clusters whose ICAgent is in **Uninstalled** state, select one of the clusters, and click **Upgrade ICAgent**.

      -  If there are no CCE clusters available, **Output to AOM** is unavailable.
      -  To disable the function of collecting container standard output to AOM 1.0, ICAgent 5.12.133 or later is required.
      -  When a CCE cluster is created, ICAgent is installed on its hosts by default and reports logs to LTS. The **Output to AOM** feature is disabled by default. If you enabled **Output to AOM** after cluster creation but want to switch back to reporting logs to LTS, ensure **Output to AOM** is disabled before upgrading ICAgent. For :ref:`Ingesting CCE Application Logs to LTS <lts_04_0511>`, you are advised to collect container standard output to LTS instead of AOM.
      -  CCE cluster ID: Each cluster has a fixed ID.
      -  When ICAgent is upgraded, LTS automatically creates a log group and host group for your CCE cluster, named **k8s-log-**\ *{Cluster ID}*. You can ingest logs of this CCE cluster to this log group when creating an ingestion configuration. For details, see :ref:`Ingesting CCE Application Logs to LTS <lts_04_0511>`.
      -  If the cluster's hosts do not have ICAgent installed or have an outdated version, clicking **Upgrade ICAgent** will install or upgrade ICAgent on all hosts in the cluster.

   #. In the displayed dialog box, click **OK**.

      The ICAgent upgrade takes about 1 minute. When the ICAgent status changes from **Updating** to **Running**, the upgrade is successful.

Upgrading ICAgent
-----------------

Upgrading ICAgent in a CCE cluster is the same as the installation process. For details, see :ref:`Installing ICAgent in a CCE cluster <lts_07_1119__en-us_topic_0000002452562620_li34651214281>`.

-  Upgrading ICAgent does not affect your services. You are advised to upgrade ICAgent during off-peak hours.
-  During the upgrade, the monitoring metrics reported by ICAgent are interrupted for about 2 to 3 minutes.
-  Upgrading ICAgent does not affect log collection. After the upgrade, ICAgent will continue collecting logs from the position before the upgrade.

Checking the ICAgent Status
---------------------------

To check the ICAgent status of a target host, choose **Host Management** > **Hosts** in the navigation pane, and click the **CCE Cluster** tab. For status details, see :ref:`Table 1 <lts_07_1119__en-us_topic_0000002452562620_table918112917487>`.

.. _lts_07_1119__en-us_topic_0000002452562620_table918112917487:

.. table:: **Table 1** ICAgent statuses

   +----------------------+---------------------------------------------------------------------------------------------------------+
   | Status               | Description                                                                                             |
   +======================+=========================================================================================================+
   | Running              | ICAgent is running properly.                                                                            |
   +----------------------+---------------------------------------------------------------------------------------------------------+
   | Uninstalled          | ICAgent is not installed.                                                                               |
   +----------------------+---------------------------------------------------------------------------------------------------------+
   | Installing           | ICAgent is being installed. This process takes about 1 minute.                                          |
   +----------------------+---------------------------------------------------------------------------------------------------------+
   | Installation failed  | ICAgent installation failed.                                                                            |
   +----------------------+---------------------------------------------------------------------------------------------------------+
   | Upgrading            | ICAgent is being upgraded. This process takes about 1 minute.                                           |
   +----------------------+---------------------------------------------------------------------------------------------------------+
   | Upgrade failed       | ICAgent upgrade failed.                                                                                 |
   +----------------------+---------------------------------------------------------------------------------------------------------+
   | Offline              | ICAgent is abnormal because the AK/SK is incorrect. Obtain the correct AK/SK and install ICAgent again. |
   +----------------------+---------------------------------------------------------------------------------------------------------+
   | Faulty               | ICAgent is faulty. Contact technical support.                                                           |
   +----------------------+---------------------------------------------------------------------------------------------------------+
   | Uninstalling         | ICAgent is being uninstalled. This process takes about 1 minute.                                        |
   +----------------------+---------------------------------------------------------------------------------------------------------+
   | Authentication error | Authentication fails because parameters were incorrectly configured during ICAgent installation.        |
   +----------------------+---------------------------------------------------------------------------------------------------------+
