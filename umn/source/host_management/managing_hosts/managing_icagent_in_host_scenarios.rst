:original_name: lts_02_0014.html

.. _lts_02_0014:

Managing ICAgent in Host Scenarios
==================================

ICAgent is a log collection tool for LTS. It runs on hosts where logs need to be collected. This section describes how to install ICAgent on a host, upgrade ICAgent, uninstall ICAgent, and check the ICAgent status.

Host scenarios cover traditional computing environments, such as physical servers and ECSs. Hosts are classified into intra-region and extra-region hosts based on their locations.

Installing ICAgent
------------------

During installation, select **Intra-region hosts** or **Extra-region hosts** based on the host location. For details, see :ref:`Installing ICAgent (Intra-Region Hosts) <lts_02_0013>` and :ref:`Installing ICAgent (Extra-Region Hosts) <lts_02_0828>`.

Upgrading ICAgent
-----------------

LTS automatically checks ICAgent versions. When LTS detects that your host is running an outdated ICAgent version, it displays a message indicating that your ICAgent version is too early.

-  You can click **Authorize Auto Upgrade** to authorize LTS to automatically upgrade ICAgent during off-peak hours.
-  You can also click **Manually Upgrade** to go to the **Host Management** page to perform the upgrade yourself.
-  If you do not need to upgrade ICAgent, select **Do not show again**.
-  Upgrading ICAgent does not affect your services. You are advised to upgrade ICAgent during off-peak hours.
-  During the upgrade, the monitoring metrics reported by ICAgent are interrupted for about 2 to 3 minutes.
-  Upgrading ICAgent does not affect log collection. After the upgrade, ICAgent will continue collecting logs from the position before the upgrade.

Linux hosts support ICAgent upgrade on the LTS console, while Windows hosts do not.

#. Log in to the management console and choose **Management & Deployment** > **Log Tank Service**.

#. Choose **Host Management** > **Hosts** in the navigation pane.

#. Click the **Intra-Region Hosts** or **Extra-Region Hosts** tab. When the system prompts you that a new ICAgent version is available, select one or more hosts where ICAgent is to be upgraded, and click **Upgrade ICAgent**.

#. In the displayed dialog box, click **OK**.

   The ICAgent upgrade takes about 1 minute. When the ICAgent status changes from **Updating** to **Running**, the ICAgent upgrade has completed.

   If ICAgent is abnormal after the upgrade or if the upgrade fails, log in to the host and run the installation command to reinstall ICAgent. Uninstalling the original ICAgent is not required. For details, see :ref:`Installing ICAgent (Intra-Region Hosts) <lts_02_0013>` and :ref:`Installing ICAgent (Extra-Region Hosts) <lts_02_0828>`.

.. _lts_02_0014__en-us_topic_0000001167072801_section109081507198:

Uninstalling ICAgent
--------------------

.. warning::

   If ICAgent is uninstalled from a host, log collection will be affected. Exercise caution when performing this operation.

Uninstalling ICAgent does not delete the installation files. You need to delete them manually if necessary.

Only ICAgent installed on Linux hosts can be uninstalled from the **Host Management** page of the LTS console. To uninstall ICAgent from a Windows host, go to **\\ICProbeAgent\\bin\\manual\\win** in the directory where the ICAgent installation package was decompressed, and double-click the script named **uninstall.bat**. If message "ICAgent uninstall success" is displayed, the uninstallation is successful.

Uninstall ICAgent from a Linux environment using any of the following methods:

-  **Uninstalling ICAgent on the console:** applicable to uninstall ICAgent that has been successfully installed.

   #. Choose **Host Management** > **Hosts** in the navigation pane.

   #. Select one or more hosts where ICAgent is to be uninstalled and click **Uninstall ICAgent**.

   #. In the displayed dialog box, click **OK**.

      The uninstallation begins. This process takes about a minute.

      After the uninstallation is complete, the ICAgent status of the host will be displayed as **Uninstalled** in the host list.

      To reinstall ICAgent, wait for 5 minutes after it is uninstalled. Otherwise, the ICAgent may be automatically uninstalled again.

-  **Logging in to the host to uninstall ICAgent:** applicable to uninstall ICAgent that failed to be installed.

   #. Log in to a host where ICAgent is to be uninstalled as user **root**.

   #. Run the following command:

      .. code-block::

         bash /opt/oss/servicemgr/ICAgent/bin/manual/uninstall.sh

      If the message "ICAgent uninstall success" is displayed, the uninstallation has completed.

-  **Remotely uninstalling ICAgent:** applicable to remotely uninstall ICAgent that has been successfully installed.

   You can uninstall ICAgent on one host remotely from another host. In remote uninstallation, the hosts must all belong to the same VPC and be on the same subnet.

   #. Run the following command on the host where ICAgent has been installed. *x.x.x.x* indicates the IP address of the host you want to uninstall ICAgent from.

      .. code-block::

         bash /opt/oss/servicemgr/ICAgent/bin/remoteUninstall/remote_uninstall.sh -ip x.x.x.x

   #. Enter the password for user **root** of the host when prompted.

      -  If the Expect tool is installed on the host that has ICAgent installed, the ICAgent uninstallation should be able to complete without prompting you for a password. Otherwise, enter the password as prompted.
      -  Ensure that user **root** can run SSH or SCP commands on the host where ICAgent has been installed to communicate with the remote host.
      -  If the message "Uninstall ICAgent success" is displayed, the uninstallation has completed.

-  **Batch uninstalling ICAgent:** applicable to uninstall ICAgent that has been successfully installed from a batch of hosts.

   If ICAgent has been installed on a host and the ICAgent installation package **ICProbeAgent.tar.gz** is in the **/opt/ICAgent/** directory of the host, you can use this method to uninstall ICAgent from multiple hosts at once.

   .. caution::

      The hosts must all belong to the same VPC and be on the same subnet.

   **Prerequisites**

   The IP addresses and passwords of all hosts to uninstall ICAgent have been collected, sorted in the **iplist.cfg** file, and uploaded to the **/opt/ICAgent/** directory on the host that has ICAgent installed. Each IP address and password in the **iplist.cfg** file must be separated by a space. Examples:

   .. code-block::

      192.168.0.109 Password (Replace the IP address and password with the actual ones)
      192.168.0.39 Password (Replace the IP address and password with the actual ones)

   -  The **iplist.cfg** file contains sensitive information. You are advised to clear it after using it.

   -  If all hosts share a password, list only IP addresses in the **iplist.cfg** file and enter the password manually during execution. If one of the hosts uses a different password, type the password behind its IP address.

   **Procedure**

   #. Run the following command on the host that has ICAgent installed:

      .. code-block::

         bash /opt/oss/servicemgr/ICAgent/bin/remoteUninstall/remote_uninstall.sh -batchModeConfig /opt/ICAgent/iplist.cfg

      Enter the default password for user **root** of the hosts to uninstall ICAgent. If the passwords of all hosts have been configured in the **iplist.cfg** file, press **Enter** to skip this step.

      Wait until the message "Uninstall ICAgent success" is displayed, which indicates that ICAgent is successfully uninstalled from all the servers listed in the configuration file.

      However, ICAgent on the server where the uninstallation operation is performed will not be uninstalled. You need to uninstall it from the server separately.

   #. Choose **Host Management** > **Hosts** in the navigation pane of the LTS console to check the ICAgent status.

.. _lts_02_0014__en-us_topic_0000001167072801_section18919294522:

Checking the ICAgent Status
---------------------------

In the navigation pane, choose **Host Management** > **Hosts**. Click the **Intra-Region Hosts** or **Extra-Region Hosts** tab based on your host's location, locate your host, and check its ICAgent status. For status details, see :ref:`Table 1 <lts_02_0014__en-us_topic_0000001167072801_table918112917487>`.

.. _lts_02_0014__en-us_topic_0000001167072801_table918112917487:

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
