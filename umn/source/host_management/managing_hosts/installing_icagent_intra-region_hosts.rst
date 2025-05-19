:original_name: lts_02_0013.html

.. _lts_02_0013:

Installing ICAgent (Intra-Region Hosts)
=======================================

To use LTS to collect logs (such as host metrics, container metrics, node logs, container logs, and standard output logs) from intra-region hosts, you need to install ICAgent on the hosts. ICAgent is a log collection tool for LTS. It runs on hosts where logs need to be collected.

Prerequisites
-------------

Before installing ICAgent, ensure that the time and time zone of your local browser are consistent with those of the host. If they are inconsistent, errors may occur during log reporting.

Installation Methods
--------------------

There are two methods to install ICAgent.

.. table:: **Table 1** Installation methods

   +---------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Method                                                  | Scenario                                                                                                                                         |
   +=========================================================+==================================================================================================================================================+
   | Initial installation                                    | You can use this method to install ICAgent on a host that has no ICAgent installed.                                                              |
   |                                                         |                                                                                                                                                  |
   |                                                         | Run the **ps -aux \| grep icagent** command on the host to check whether there is an ICAgent process. If no, the ICAgent has not been installed. |
   +---------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Inherited installation (supported only for Linux hosts) | When ICAgent has already been installed on one host but needs to be installed on multiple hosts, you can use this method.                        |
   +---------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+

Initial Installation (Linux)
----------------------------

#. Log in to the management console and choose **Management & Deployment** > **Log Tank Service**.

#. Choose **Host Management** > **Hosts** in the navigation pane.

#. Click **Install ICAgent** in the upper right corner.

   Before installing ICAgent, ensure that the time and time zone of your local browser are consistent with those of the host.

#. Set **Host** to **Intra-region hosts**.

#. Set **OS** to **Linux**.

#. If you set **Installation Mode** to **Obtain AK/SK**, perform this step. Obtain an access key (AK/SK) in advance. You need to enter it when installing ICAgent. AK is used together with SK to sign requests cryptographically, ensuring that the requests are secret, complete, and correct. Ensure that the public account and AK/SK will not be deleted or disabled. If the AK/SK is deleted, ICAgent cannot report data to LTS.

   For details, see :ref:`How Do I Obtain an AK/SK Pair? <lts_03_0015>`

#. If you set **Installation Mode** to **Create an agency**, this step is required. In this installation mode, you do not need to obtain and enter an AK/SK. ICAgent automatically obtains an AK/SK during agency creation.

   For details, see :ref:`How Do I Install ICAgent by Creating an Agency? <lts_03_0002>`

#. On the **Install ICAgent** page, click **Copy Command** to copy the ICAgent installation command.

#. Log in as user **root** to the host which is deployed in the region same as that you are logged in to (by using a remote login tool such as PuTTY) and run the copied command. If you have chosen **Obtain AK/SK** as the installation mode, enter the AK/SK as prompted.

   -  When message "ICAgent install success" is displayed, ICAgent has been installed in the **/opt/oss/servicemgr/** directory of the host.
   -  If the installation fails, uninstall ICAgent and then install it again.

#. Choose **Host Management** > **Hosts** in the navigation pane of the LTS console and check whether the ICAgent status is **Running**.

Initial Installation (Windows)
------------------------------

#. On the **Hosts** page of the LTS console, click **Install ICAgent** in the upper right corner.

#. Set **Host** to **Intra-region hosts**.

#. Set **OS** to **Windows**.

#. You can download it to the local PC by clicking the name of the package or visiting the download URL.

#. Save the ICAgent installation package to a directory on the target host, for example, **C:\\ICAgent**, and decompress the package.

#. Obtain an AK/SK. For details, see :ref:`How Do I Obtain an AK/SK Pair? <lts_03_0015>`

#. On the **Install ICAgent** page, click **Copy Command** to copy the ICAgent installation command to the local PC and replace the AK/SK in the command with the obtained one.

#. Open the Command Prompt, go to the directory where the ICAgent installation package is decompressed, and run the copied command.

   If the message "Service icagent installed successfully" is displayed, the installation is successful.

   -  If you have installed a third-party antivirus software, add ICAgent as a trusted program. Otherwise, ICAgent installation may fail.

   -  To uninstall ICAgent, go to the **\\ICProbeAgent\\bin\\manual\\win** directory where the ICAgent installation package was decompressed, and double-click the script named **uninstall.bat**. When the message "icagent removed successfully" is displayed, the uninstallation is successful.

      Uninstalling ICAgent does not delete the files in the corresponding directories. You need to delete them manually if necessary.

   -  To check the ICAgent status, go to the directory where the ICAgent installation package was decompressed, open the Command Prompt, and run the **sc query icagent** command. If **RUNNING** is returned, ICAgent is running. If the message "The specified service does not exist as an installed service" is displayed, ICAgent has been uninstalled.

   -  If you reinstall ICAgent after uninstallation and find that the ICAgent status remains pending, end the **icagent.exe** process in **Task Manager** and try installation again.

#. Choose **Host Management** > **Hosts** in the navigation pane of the LTS console and check whether the ICAgent status is **Running**.

Inherited Installation (Linux)
------------------------------

Assume that you need to install ICAgent on multiple hosts, and one of the hosts already has ICAgent installed. The ICAgent installation package, **ICProbeAgent.tar.gz**, is in the **/opt/ICAgent/** directory. To install ICAgent on other hosts one by one:

#. Run the following command on the host where ICAgent has been installed, where *x.x.x.x* is the IP address of the host you want to install ICAgent on.

   .. code-block::

      bash /opt/oss/servicemgr/ICAgent/bin/remoteInstall/remote_install.sh -ip x.x.x.x

#. Enter the password for user **root** of the host when prompted.

   -  If the Expect tool is installed on the host that has ICAgent installed, the ICAgent installation should be able to complete without prompting you for a password. Otherwise, enter the password as prompted.
   -  Ensure that user **root** can run SSH or SCP commands on the host where ICAgent has been installed to remotely communicate with the remote host to install ICAgent.
   -  When message "ICAgent install success" is displayed, ICAgent has been installed in the **/opt/oss/servicemgr/** directory of the host. You can then choose **Host Management** > **Hosts** in the navigation pane of the LTS console to check the ICAgent status.
   -  If "ICAgent install success" is not displayed, the installation fails. Uninstall ICAgent and install it again.

Batch Inherited Installation (Linux)
------------------------------------

Assume that you need to install ICAgent on multiple hosts, and one of the hosts already has ICAgent installed. The ICAgent installation package, **ICProbeAgent.tar.gz**, is in the **/opt/ICAgent/** directory. In this case, you can follow the directions below to install ICAgent on other hosts in batches.

-  The hosts must all belong to the same VPC and be on the same subnet.
-  **Python 3.\*** is required for batch installation. If you are prompted that Python cannot be found during ICAgent installation, install Python of a proper version on the host and try again.

**Prerequisites**

The IP addresses and **root**'s passwords of all hosts to install ICAgent have been collected, sorted in the **iplist.cfg** file, and uploaded to the **/opt/ICAgent/** directory on the host that has ICAgent installed. An IP address and the password of a host's user **root** in the **iplist.cfg** file must be separated by a space. Examples:

**192.168.0.109** *Password* (Replace the IP address and password with the actual ones)

**192.168.0.39** *Password* (Replace the IP address and password with the actual ones)

-  The **iplist.cfg** file contains sensitive information. You are advised to clear it after using it.

-  If all hosts share a password, list only IP addresses in the **iplist.cfg** file and enter the password manually during execution. If one of the hosts uses a different password, type the password behind its IP address.

**Procedure**

#. Run the following command on the host that has ICAgent installed:

   .. code-block::

      bash /opt/oss/servicemgr/ICAgent/bin/remoteInstall/remote_install.sh -batchModeConfig /opt/ICAgent/iplist.cfg

   Enter the default password for user **root** of the hosts to install ICAgent. If the passwords of all hosts have been configured in the **iplist.cfg** file, press **Enter** to skip this step.

   .. code-block::

      batch install begin
      Please input default passwd:
      send cmd to 192.168.0.109
      send cmd to 192.168.0.39
      2 tasks running, please wait...
      2 tasks running, please wait...
      2 tasks running, please wait...
      End of install agent: 192.168.0.39
      End of install agent: 192.168.0.109
      All hosts install icagent finish.

   Wait for a while. When message "All hosts install icagent finish." is displayed, ICAgent has been installed on all the hosts listed in the configuration file.

#. Choose **Host Management** > **Hosts** in the navigation pane of the LTS console to check the :ref:`ICAgent status <lts_02_0014__en-us_topic_0000001167072801_section18919294522>`.
