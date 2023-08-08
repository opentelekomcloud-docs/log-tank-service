:original_name: lts_02_0015.html

.. _lts_02_0015:

Uninstalling ICAgent
====================

If ICAgent is uninstalled from a host, log collection will be affected. Exercise caution when performing this operation.

.. note::

   Only ICAgent installed on Linux hosts can be uninstalled from the **Host Management** page of the LTS console. To uninstall ICAgent from a Windows host, go to **\\ICProbeAgent\\bin\\manual\\win** in the directory where the ICAgent installation package was decompressed, and double-click the script named **uninstall.bat**. If the message **ICAgent uninstall success** is displayed, the uninstallation was successful.

   Uninstalling ICAgent does not delete the installation files. You need to delete them manually if necessary.

There are a number of ways to uninstall ICAgent:

-  :ref:`Uninstalling ICAgent on the Console <lts_02_0015__en-us_topic_0000001167192835_s56b926e2e7b74b9ba2a87166afb4989b>`: This can be used to uninstall ICAgent that has been successfully installed.
-  :ref:`Uninstalling ICAgent on a Host <lts_02_0015__en-us_topic_0000001167192835_s3b88a85d5fc54597bdb601e26408a808>`: This can be used to remove ICAgent that fails to be installed for reinstallation.
-  :ref:`Remotely Uninstalling ICAgent <lts_02_0015__en-us_topic_0000001167192835_section6144172213109>`: This can be used to remotely uninstall ICAgent that has been successfully installed.
-  :ref:`Batch Uninstalling ICAgent <lts_02_0015__en-us_topic_0000001167192835_section1091572622115>`: This can be used to uninstall ICAgent that has been successfully installed from a batch of hosts.

.. _lts_02_0015__en-us_topic_0000001167192835_s56b926e2e7b74b9ba2a87166afb4989b:

Uninstalling ICAgent on the Console
-----------------------------------

#. Log in to the LTS console and choose **Host Management** in the navigation pane on the left.

#. Click the **Hosts** tab.

#. Select one or more hosts where ICAgent is to be uninstalled and click **Uninstall ICAgent**.

#. In the displayed dialog box, click **OK**.

   The uninstallation begins. This process takes about a minute.

   The ICAgent uninstalled will be removed from the host list.

   .. note::

      To reinstall ICAgent, wait for 5 minutes after the uninstallation completes, or the reinstalled ICAgent may be unintentionally uninstalled again.

.. _lts_02_0015__en-us_topic_0000001167192835_s3b88a85d5fc54597bdb601e26408a808:

Uninstalling ICAgent on a Host
------------------------------

#. Log in to a host where ICAgent is to be uninstalled as user **root**.

#. Run the following command:

   **bash /opt/oss/servicemgr/ICAgent/bin/manual/uninstall.sh;**

   If the message **ICAgent uninstall success** is displayed, the uninstallation has completed.

.. _lts_02_0015__en-us_topic_0000001167192835_section6144172213109:

Remotely Uninstalling ICAgent
-----------------------------

You can uninstall ICAgent on one host remotely from another host.

#. Run the following command on the host where ICAgent has been installed, *x.x.x.x* is the IP address of the host you want to uninstall ICAgent from.

   **bash /opt/oss/servicemgr/ICAgent/bin/remoteUninstall/remote_uninstall.sh -ip** *x.x.x.x*

#. Enter the password for user **root** of the host when prompted.

   .. note::

      -  If the Expect tool is installed on the host that has ICAgent installed, the ICAgent uninstallation should be able to complete without prompting you for a password. Otherwise, enter the password as prompted.
      -  Ensure that user **root** can run SSH or SCP commands on the host where ICAgent has been installed to communicate with the remote host to uninstall ICAgent.
      -  If the message **ICAgent uninstall success** is displayed, the uninstallation has completed.

.. _lts_02_0015__en-us_topic_0000001167192835_section1091572622115:

Batch Uninstalling ICAgent
--------------------------

If ICAgent has been installed on a host and the ICAgent installation package **ICProbeAgent.tar.gz** is in the **/opt/ICAgent/** directory of the host, you can use this method to uninstall ICAgent from multiple hosts at once.

.. important::

   The hosts must all belong to the same Virtual Private Cloud (VPC) and be on the same subnet.

**Prerequisites**

The IP addresses and passwords of all hosts to uninstall ICAgent have been collected, sorted in the **iplist.cfg** file, and uploaded to the **/opt/ICAgent/** directory on the host that has ICAgent installed. Each IP address and password in the **iplist.cfg** file must be separated by a space, as shown in the following example:

**192.168.0.109** *Password* (Replace the IP address and password with the actual ones)

**192.168.0.39** *Password* (Replace the IP address and password with the actual ones)

.. note::

   -  Because the **iplist.cfg** file contains sensitive information, you are advised to clear it after using it.

   -  If all hosts share a password, list only IP addresses in the **iplist.cfg** file and enter the password during execution. If one of the hosts uses a different password, type the password behind its IP address.

**Procedure**

#. Run the following command on the host that has ICAgent installed:

   **bash /opt/oss/servicemgr/ICAgent/bin/remoteUninstall/remote_uninstall.sh -batchModeConfig /opt/ICAgent/iplist.cfg**

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

   If the message **All hosts uninstall icagent finish.** is displayed, the batch uninstallation has completed.

#. Choose **Host Management** > **Hosts** on the LTS console to view the ICAgent status.
