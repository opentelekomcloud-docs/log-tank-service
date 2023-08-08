:original_name: lts_02_0014.html

.. _lts_02_0014:

Upgrading ICAgent
=================

To deliver a better collection experience, LTS regularly upgrades ICAgent. When LTS prompts you that a new ICAgent version is available, you can follow the directions here to obtain the latest version.

.. note::

   Linux hosts support ICAgent upgrade on the **Host Management** page of the LTS console.

Procedure
---------

#. Log in to the LTS console and choose **Host Management** in the navigation pane on the left.

#. On the **Host Management** page, click the **Hosts** tab.

#. Select **Hosts**. Select one or more hosts where ICAgent is to be upgraded, and click **Upgrade ICAgent**.

   Select **CCE Cluster**. In the drop-down list on the right, select the cluster whose ICAgent is to be upgraded, and click **Upgrade ICAgent**.


   .. figure:: /_static/images/en-us_image_0000001460235561.png
      :alt: **Figure 1** Upgrading ICAgent

      **Figure 1** Upgrading ICAgent

   .. note::

      -  .. _lts_02_0014__en-us_topic_0000001167072801_li1088163816131:

         If you create a CCE cluster for the first time, ICAgents will be installed on hosts in the cluster by default, and logs will be reported to AOM. **Output to AOM** is enabled by default. To report logs to LTS, disable **Output to AOM** before upgrading ICAgents. You are advised to choose **Log Ingestion** > **Cloud Service** > **Cloud Container Engine (CCE)** to collect container data and output it to LTS instead of AOM.

      -  CCE cluster ID (ClusterID): Each cluster has a fixed ID.

      -  When ICAgent is upgraded, LTS creates log groups and host groups for your CCE cluster. The name of the log group and host group is **k8s-log-**\ *{ClusterID}*. You can create an ingestion configuration (**Cloud Services** > **Cloud Container Engine (CCE)**) to add logs of the current CCE cluster to the log group.

      -  If the ICAgent is not installed on hosts in a cluster or the ICAgent version is too early, click **Upgrade ICAgent** to install the ICAgent on all hosts in the cluster.

#. In the displayed dialog box, click **OK**.

   The upgrade begins. This process takes about a minute. When the ICAgent status changes from **Upgrading** to **Running**, the ICAgent upgrade has completed.

   .. note::

      If the ICAgent is abnormal after the upgrade or if the upgrade fails, log in to the host and run the installation command. ICAgent can be re-installed on top of itself.
