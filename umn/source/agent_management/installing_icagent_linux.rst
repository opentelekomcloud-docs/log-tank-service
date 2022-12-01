:original_name: lts_02_0013.html

.. _lts_02_0013:

Installing ICAgent (Linux)
==========================

ICAgent is a log collection tool for LTS. If you use LTS to collect logs from a host running Linux OS, you need to install ICAgent on the host.

Prerequisites
-------------

Ensure that the time and time zone of your local browser are consistent with those of the host to install ICAgent. If they are inconsistent, errors may occur during log reporting.

Installation Methods
--------------------

There are two methods to install ICAgent.

.. table:: **Table 1** Installation methods

   +------------------------+---------------------------------------------------------------------------------------------------------------------------+
   | Method                 | Scenario                                                                                                                  |
   +========================+===========================================================================================================================+
   | Initial installation   | You can use this method to install ICAgent on a host that has no ICAgent installed.                                       |
   +------------------------+---------------------------------------------------------------------------------------------------------------------------+
   | Inherited installation | When ICAgent has already been installed on one host but needs to be installed on multiple hosts, you can use this method. |
   +------------------------+---------------------------------------------------------------------------------------------------------------------------+

Initial Installation
--------------------

#. Log in to the LTS console and choose **Agent Management** in the navigation pane on the left.

#. Click **Install ICAgent**.

   |image1|

#. Select an installation mode:

   -  **Obtain AK/SK**. For details, see :ref:`How Do I Obtain an AK/SK Pair? <lts_03_0015>`

      .. note::

         If the AK/SK pair expires or is deleted, the ICAgent status may become abnormal. In this case, create an AK/SK pair and generate a new installation command. Log in to the host and run the command to reinstall ICAgent.

   -  **Create an agency**. For details, see :ref:`How Do I Install ICAgent by Creating an Agency? <lts_03_0002>`

#. Click **Copy Command** to copy the ICAgent installation command.

#. Log in as user **root** to the host which is deployed in the region same as that you are logged in to (for example, by using a remote login tool such as PuTTY) and run the copied command. If you have chosen **Obtain AK/SK** as the installation mode, enter the AK/SK pair as prompted.

   .. note::

      -  When the message **ICAgent install success** is displayed, ICAgent has been installed in the **/opt/oss/servicemgr/** directory of the host. You can then view the ICAgent status on the **Agent Management** page of the LTS console.
      -  If the installation fails, uninstall ICAgent and reinstall it. If reinstallation fails, contact technical support.

Inherited Installation
----------------------

Let's assume that you need to install ICAgent on multiple hosts, and one of the hosts already has ICAgent installed. The ICAgent installation package, **ICProbeAgent.tar.gz**, is in the **/opt/ICAgent/** directory. You can follow the directions below to install ICAgent on other hosts one by one.

#. Run the following command on the host where ICAgent has been installed, where *x.x.x.x* is the IP address of the host you want to install ICAgent on.

   **bash /opt/oss/servicemgr/ICAgent/bin/remoteInstall/remote_install.sh -ip** *x.x.x.x*

#. Enter the password for user **root** of the host when prompted.

   .. note::

      -  If the Expect tool is installed on the host that has ICAgent installed, the ICAgent installation should be able to complete without prompting you for a password.
      -  Ensure that user **root** can run SSH or SCP commands on the host where ICAgent has been installed to remotely communicate with the host to install ICAgent.
      -  When the message **ICAgent install success** is displayed, ICAgent has been installed in the **/opt/oss/servicemgr/** directory of the host. You can then view the ICAgent status on the **Agent Management** page of the LTS console.
      -  If the installation fails, uninstall ICAgent and reinstall it. If reinstallation fails, contact technical support.

Batch Inherited Installation
----------------------------

Let's assume that you need to install ICAgent on multiple hosts, and one of the hosts already has ICAgent installed. The ICAgent installation package, **ICProbeAgent.tar.gz**, is in the **/opt/ICAgent/** directory. You can follow the directions below to install ICAgent on other hosts in batches.

.. important::

   -  The hosts must all belong to the same Virtual Private Cloud (VPC) and be on the same subnet.

**Prerequisites**

The IP addresses and passwords of all hosts to install ICAgent have been collected, sorted in the **iplist.cfg** file, and uploaded to the **/opt/ICAgent/** directory on the host that has ICAgent installed. Each IP address and password in the **iplist.cfg** file must be separated by a space, as shown in the following:

**192.168.2.109** *Password of the host where ICAgent is to be installed*

**192.168.0.139** *Password of the host where ICAgent is to be installed*

.. note::

   -  The **iplist.cfg** file contains sensitive information. You are advised to clear it after using it.

   -  If all hosts share a password, list only IP addresses in the **iplist.cfg** file and enter the password manually during execution. If one of the hosts uses a different password, type the password behind its IP address.

**Procedure**

#. Run the following command on the host that has ICAgent installed:

   **bash /opt/oss/servicemgr/ICAgent/bin/remoteInstall/remote_install.sh -batchModeConfig /opt/ICAgent/iplist.cfg**

   Enter the password for user **root** of the hosts to install ICAgent. If the passwords of all hosts have been configured in the **iplist.cfg** file, press **Enter** to skip this step.

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

#. Choose **Agent Management** in the LTS navigation pane to view the ICAgent status. For details, see :ref:`ICAgent Status <lts_04_0013>`.

.. |image1| image:: /_static/images/en-us_image_0000001368172808.png
