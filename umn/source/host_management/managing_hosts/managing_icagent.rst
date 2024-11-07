:original_name: lts_02_0014.html

.. _lts_02_0014:

Managing ICAgent
================

After ICAgent is installed, you can :ref:`upgrade <lts_02_0014__en-us_topic_0000001167072801_section3441614134517>` and :ref:`uninstall <lts_02_0014__en-us_topic_0000001167072801_section109081507198>` it, and :ref:`view its status <lts_02_0014__en-us_topic_0000001167072801_section18919294522>`.

.. _lts_02_0014__en-us_topic_0000001167072801_section3441614134517:

Upgrading ICAgent
-----------------

To deliver a better collection experience, LTS regularly upgrades ICAgent. When LTS prompts you that a new ICAgent version is available, you can follow the directions here to obtain the latest version.

.. note::

   Linux hosts support ICAgent upgrade on the **Host Management** page of the LTS console.

#. Log in to the management console and choose **Management & Deployment** > **Log Tank Service**.

#. Choose **Host Management** in the navigation pane and click the **Hosts** tab.

#. Select **Intra-Region Hosts** or **Extra-Region Hosts**. When the system prompts you that a new ICAgent version is available, select one or more check boxes of hosts where ICAgent is to be upgraded, and click **Upgrade ICAgent**.

#. Click the **CCE Cluster** tab. Search for and select the cluster whose ICAgent is to be upgraded, and click **Upgrade ICAgent**.

   .. note::

      -  You need to create a CCE cluster before you can collect container standards and send them to AOM.

      -  To disable the function of exporting container standards to AOM, you need to have ICAgent 5.12.133 or later.

      -  .. _lts_02_0014__en-us_topic_0000001167072801_li1088163816131:

         If you create a CCE cluster for the first time, ICAgent will be installed on hosts in the cluster by default, and logs will be reported to AOM. **Output to AOM** is enabled by default. To report logs to LTS, disable **Output to AOM** before upgrading ICAgent. You are advised to choose **Log Ingestion** > **Cloud Service** > **Cloud Container Engine (CCE)** to collect container data and output it to LTS instead of AOM.

      -  CCE cluster ID (ClusterID): Each cluster has a fixed ID.

      -  When ICAgent is upgraded, LTS creates log groups and host groups for your CCE cluster. The name of the log group and host group is **k8s-log-**\ *{ClusterID}*. You can create an ingestion configuration (**Cloud Services** > **Cloud Container Engine (CCE)**) to add logs of the current CCE cluster to the log group.

      -  If the ICAgent is not installed on hosts in a cluster or the ICAgent version is too early, click **Upgrade ICAgent** to install the ICAgent on all hosts in the cluster.

#. In the displayed dialog box, click **OK**.

   The upgrade begins. This process takes about a minute. When the ICAgent status changes from **Upgrading** to **Running**, the ICAgent upgrade has completed.

   .. note::

      If the ICAgent is abnormal after the upgrade or if the upgrade fails, log in to the host and run the installation command. ICAgent can be re-installed on top of itself.

.. _lts_02_0014__en-us_topic_0000001167072801_section109081507198:

Uninstalling ICAgent
--------------------

If ICAgent is uninstalled from a host, log collection will be affected. Exercise caution when performing this operation.

.. note::

   Only ICAgent installed on Linux hosts can be uninstalled from the **Host Management** page of the LTS console. To uninstall ICAgent from a Windows host, go to **\\ICProbeAgent\\bin\\manual\\win** in the directory where the ICAgent installation package was decompressed, and double-click the script named **uninstall.bat**. If message **ICAgent uninstall success** is displayed, the uninstallation is successful.

   Uninstalling ICAgent does not delete the installation files. You need to delete them manually if necessary.

You can uninstall ICAgent using either of the following methods:

-  Uninstalling ICAgent on the console: applies to the scenario where ICAgent has been successfully installed.

   #. Choose **Host Management** in the navigation pane and click the **Hosts** tab.

   #. Select one or more hosts where ICAgent is to be uninstalled and click **Uninstall ICAgent**.

   #. In the displayed dialog box, click **OK**.

      The uninstallation begins. This process takes about a minute.

      The hosts with ICAgent uninstalled will be removed from the host list.

      .. note::

         To reinstall ICAgent, wait for 5 minutes after it is uninstalled. Otherwise, the ICAgent may be automatically uninstalled again.

-  Logging in to the host to uninstall ICAgent: applies to the scenario where ICAgent fails to be installed.

   #. Log in to a host where ICAgent is to be uninstalled as user **root**.

   #. Run the following command:

      .. code-block::

         bash /opt/oss/servicemgr/ICAgent/bin/manual/uninstall.sh

      If the message **ICAgent uninstall success** is displayed, the uninstallation has completed.

-  Remotely uninstalling ICAgent: applies to the scenario where the ICAgent has been successfully installed and needs to be remotely uninstalled.

   You can uninstall ICAgent on one host remotely from another host.

   #. Run the following command on the host where ICAgent has been installed. *x.x.x.x* indicates the IP address of the host you want to uninstall ICAgent from.

      .. code-block::

         bash /opt/oss/servicemgr/ICAgent/bin/remoteUninstall/remote_uninstall.sh -ip x.x.x.x

   #. Enter the password for user **root** of the host when prompted.

      .. note::

         -  If the Expect tool is installed on the host that has ICAgent installed, the ICAgent uninstallation should be able to complete without prompting you for a password. Otherwise, enter the password as prompted.
         -  Ensure that user **root** can run SSH or SCP commands on the host where ICAgent has been installed to communicate with the remote host.
         -  If the message **ICAgent uninstall success** is displayed, the uninstallation has completed.

-  Batch uninstalling ICAgent: applies to the scenario where the ICAgent has been installed and needs to be uninstalled in batches.

   If ICAgent has been installed on a host and the ICAgent installation package **ICProbeAgent.tar.gz** is in the **/opt/ICAgent/** directory of the host, you can use this method to uninstall ICAgent from multiple hosts at once.

   .. note::

      The hosts must all belong to the same VPC and be on the same subnet.

   **Prerequisites**

   The IP addresses and passwords of all hosts to uninstall ICAgent have been collected, sorted in the **iplist.cfg** file, and uploaded to the **/opt/ICAgent/** directory on the host that has ICAgent installed. Each IP address and password in the **iplist.cfg** file must be separated by a space. Examples:

   **192.168.0.109** *Password* (Replace the IP address and password with the actual ones)

   **192.168.0.39** *Password* (Replace the IP address and password with the actual ones)

   .. note::

      -  The **iplist.cfg** file contains sensitive information. You are advised to clear it after using it.

      -  If all hosts share a password, list only IP addresses in the **iplist.cfg** file and enter the password manually during execution. If one of the hosts uses a different password, type the password behind its IP address.

   #. Run the following command on the host that has ICAgent installed:

      .. code-block::

         bash /opt/oss/servicemgr/ICAgent/bin/remoteUninstall/remote_uninstall.sh -batchModeConfig /opt/ICAgent/iplist.cfg

      Enter the default password for user **root** of the hosts to uninstall ICAgent. If the passwords of all hosts have been configured in the **iplist.cfg** file, press **Enter** to skip this step.

      .. code-block::

         batch uninstall begin
         Please input default passwd:
         send cmd to 192.168.0.109
         send cmd to 192.168.0.39
         2 tasks running, please wait...
         End of uninstall agent: 192.168.0.109
         End of uninstall agent: 192.168.0.39
         All hosts uninstall icagent finish.

      If message **All hosts uninstall icagent finish.** is displayed, the batch uninstallation has completed.

   #. Choose **Host Management** > **Hosts** in the navigation pane of the LTS console to view the ICAgent status.

.. _lts_02_0014__en-us_topic_0000001167072801_section18919294522:

Checking the ICAgent Status
---------------------------

On the **Host Management** page, click the **Hosts** tab. Check the ICAgent status of the target host. The following table lists the ICAgent statuses.

.. table:: **Table 1** ICAgent statuses

   +---------------------+-------------------------------------------------------------------------------------------------------------------+
   | Status              | Description                                                                                                       |
   +=====================+===================================================================================================================+
   | Running             | ICAgent is running properly.                                                                                      |
   +---------------------+-------------------------------------------------------------------------------------------------------------------+
   | Uninstalled         | ICAgent is not installed.                                                                                         |
   +---------------------+-------------------------------------------------------------------------------------------------------------------+
   | Installing          | ICAgent is being installed. This process takes about one minute.                                                  |
   +---------------------+-------------------------------------------------------------------------------------------------------------------+
   | Installation failed | ICAgent installation failed.                                                                                      |
   +---------------------+-------------------------------------------------------------------------------------------------------------------+
   | Upgrading           | ICAgent is being upgraded. This process takes about one minute.                                                   |
   +---------------------+-------------------------------------------------------------------------------------------------------------------+
   | Upgrade failed      | ICAgent upgrade failed.                                                                                           |
   +---------------------+-------------------------------------------------------------------------------------------------------------------+
   | Offline             | ICAgent is abnormal because the AK/SK pair is incorrect. Obtain the correct AK/SK pair and install ICAgent again. |
   +---------------------+-------------------------------------------------------------------------------------------------------------------+
   | Faulty              | ICAgent is faulty. Contact technical support.                                                                     |
   +---------------------+-------------------------------------------------------------------------------------------------------------------+
