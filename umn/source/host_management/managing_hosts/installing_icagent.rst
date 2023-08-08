:original_name: lts_02_0013.html

.. _lts_02_0013:

Installing ICAgent
==================

ICAgent is a log collection tool for LTS. To use LTS to collect logs from hosts, you need to install ICAgent on the hosts.

Prerequisites
-------------

Ensure that the time and time zone of your local browser are consistent with those of the host to install ICAgent. If they are inconsistent, errors may occur during log reporting.

Installation Methods
--------------------

There are two methods to install ICAgent.

.. table:: **Table 1** Installation methods

   +---------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------+
   | Method                                                  | Scenario                                                                                                                  |
   +=========================================================+===========================================================================================================================+
   | Initial installation                                    | You can use this method to install ICAgent on a host that has no ICAgent installed.                                       |
   +---------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------+
   | Inherited installation (supported only for Linux hosts) | When ICAgent has already been installed on one host but needs to be installed on multiple hosts, you can use this method. |
   +---------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------+

Initial Installation (Linux)
----------------------------

#. Log in to the LTS console and choose **Host Management** in the navigation pane on the left.

#. Click **Install ICAgent** in the upper right corner.


   .. figure:: /_static/images/en-us_image_0000001576328724.png
      :alt: **Figure 1** Installing ICAgent

      **Figure 1** Installing ICAgent

#. Set **OS** to **Linux**.

#. Select an installation mode:

   -  **Obtain AK/SK**. For details, see :ref:`How Do I Obtain an AK/SK Pair? <lts_03_0015>`

      Obtain and use the AK/SK of a public account.

      .. important::

         Ensure that the public account and AK/SK will not be deleted or disabled. If the AK/SK is deleted, the ICAgent cannot report data to LTS.

#. Click **Copy Command** to copy the ICAgent installation command.

#. Log in as user **root** to the host which is deployed in the region same as that you are logged in to (for example, by using a remote login tool such as PuTTY) and run the copied command. If you have chosen **Obtain AK/SK** as the installation mode, enter the AK/SK pair as prompted.

   .. note::

      -  When the message **ICAgent install success** is displayed, ICAgent has been installed in the **/opt/oss/servicemgr/** directory of the host. You can then view the ICAgent status on the **Host Management** > **Hosts** page of the LTS console.
      -  If the installation fails, uninstall ICAgent and reinstall it. If the reinstallation fails, contact technical support.

Initial Installation (Windows)
------------------------------

#. Log in to the LTS console and choose **Host Management** in the navigation pane on the left.

#. Click **Install ICAgent** in the upper right corner.

#. Set **OS** to **Windows**.

   |image1|

#. Download the ICAgent installation package to the host.

   You can download it by clicking the name of the package or copying the download URL to the address bar of your browser.

#. Save the ICAgent installation package to a directory, for example, **C:\\ICAgent**, and decompress the package.

#. Enter the AK/SK pair to generate the ICAgent installation command. For details about how to obtain an AK/SK pair, see :ref:`How Do I Obtain an AK/SK Pair? <lts_03_0015>`

   .. note::

      If the AK/SK pair expires or is deleted, the ICAgent status may become abnormal. In this case, create an AK/SK pair and generate a new installation command. Log in to the host and run the command to reinstall ICAgent.

#. Open the Command Prompt, go to the directory where the ICAgent installation package is decompressed, and run the copied command.

   If the message **Service icagent installed successfully** is displayed, the installation is successful.

   .. note::

      -  If you have installed a third-party antivirus software, add ICAgent as a trusted program. Otherwise, ICAgent installation may fail.

      -  To uninstall ICAgent, go to the **\\ICProbeAgent\\bin\\manual\\win** directory where the ICAgent installation package was decompressed, and double-click the script named **uninstall.bat**. When the message **icagent removed successfully** is displayed, the uninstallation is successful.

         Uninstalling ICAgent does not delete the files in the corresponding directories. You need to delete them manually if necessary.

      -  To check the ICAgent status, go to the directory where the ICAgent installation package was decompressed, open the Command Prompt, and run the **sc query icagent** command. If **RUNNING** is returned, ICAgent is running. If the message **The specified service does not exist as an installed service** is displayed, ICAgent has been uninstalled.

      -  If you reinstall ICAgent after uninstallation and find that the ICAgent status is still pending, end the ICAgent process in Task Manager and try again.

Inherited Installation (Linux)
------------------------------

Let's assume that you need to install ICAgent on multiple hosts, and one of the hosts already has ICAgent installed. The ICAgent installation package, **ICProbeAgent.tar.gz**, is in the **/opt/ICAgent/** directory. You can follow the directions below to install ICAgent on other hosts one by one.

#. Run the following command on the host where ICAgent has been installed, where *x.x.x.x* is the IP address of the host you want to install ICAgent on.

   **bash /opt/oss/servicemgr/ICAgent/bin/remoteInstall/remote_install.sh -ip** *x.x.x.x*

#. Enter the password for user **root** of the host when prompted.

   .. note::

      -  If the Expect tool is installed on the host that has ICAgent installed, the ICAgent installation should be able to complete without prompting you for a password. Otherwise, enter the password as prompted.
      -  Ensure that user **root** can run SSH or SCP commands on the host where ICAgent has been installed to remotely communicate with the remote host to install ICAgent.
      -  When the message **ICAgent install success** is displayed, ICAgent has been installed in the **/opt/oss/servicemgr/** directory of the host. You can then view the ICAgent status on the **Host Management** > **Hosts** page of the LTS console.
      -  If the installation fails, uninstall ICAgent and reinstall it. If reinstallation fails, contact technical support.

Batch Inherited Installation (Linux)
------------------------------------

Let's assume that you need to install ICAgent on multiple hosts, and one of the hosts already has ICAgent installed. The ICAgent installation package, **ICProbeAgent.tar.gz**, is in the **/opt/ICAgent/** directory. You can follow the directions below to install ICAgent on other hosts in batches.

.. important::

   -  The hosts must all belong to the same Virtual Private Cloud (VPC) and be on the same subnet.
   -  **Python 3.\*** is required for batch installation. If you are prompted that Python cannot be found during ICAgent installation, install Python of a proper version and try again.

**Prerequisites**

The IP addresses and passwords of all hosts to install ICAgent have been collected, sorted in the **iplist.cfg** file, and uploaded to the **/opt/ICAgent/** directory on the host that has ICAgent installed. Each IP address and password in the **iplist.cfg** file must be separated by a space, as shown in the following example:

**192.168.0.109** *Password* (Replace the IP address and password with the actual ones)

**192.168.0.39** *Password* (Replace the IP address and password with the actual ones)

.. note::

   -  Because the **iplist.cfg** file contains sensitive information, you are advised to clear it after using it.

   -  If all hosts share a password, list only IP addresses in the **iplist.cfg** file and enter the password manually during execution. If one of the hosts uses a different password, type the password behind its IP address.

**Procedure**

#. Run the following command on the host that has ICAgent installed:

   **bash /opt/oss/servicemgr/ICAgent/bin/remoteInstall/remote_install.sh -batchModeConfig /opt/ICAgent/iplist.cfg**

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

   If the message **All hosts install icagent finish.** is displayed, ICAgent has been installed on all the hosts listed in the configuration file.

#. You can then view the :ref:`ICAgent status <lts_04_0013>` on the **Host Management** > **Hosts** page of the LTS console.

.. |image1| image:: /_static/images/en-us_image_0000001626584937.png
