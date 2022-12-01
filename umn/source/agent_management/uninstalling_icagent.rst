:original_name: lts_02_0015.html

.. _lts_02_0015:

Uninstalling ICAgent
====================

If ICAgent is uninstalled from a host, log collection will be affected. Exercise caution when performing this operation.

.. note::

   Uninstalling ICAgent does not delete the installation files. You need to delete them manually if necessary.

There are a number of ways to uninstall ICAgent:

-  :ref:`Uninstalling ICAgent on the Console <lts_02_0015__en-us_topic_0178700396_s56b926e2e7b74b9ba2a87166afb4989b>`: This can be used to uninstall ICAgent that has been successfully installed.
-  :ref:`Uninstalling ICAgent on a Host <lts_02_0015__en-us_topic_0178700396_s3b88a85d5fc54597bdb601e26408a808>`: This can be used to remove ICAgent that fails to be installed for reinstallation.
-  :ref:`Remotely Uninstalling ICAgent <lts_02_0015__en-us_topic_0178700396_section6144172213109>`: This can be used to remotely uninstall ICAgent that has been successfully installed.
-  :ref:`Batch Uninstalling ICAgent <lts_02_0015__en-us_topic_0178700396_section1091572622115>`: This can be used to uninstall ICAgent that has been successfully installed from a batch of hosts.

.. _lts_02_0015__en-us_topic_0178700396_s56b926e2e7b74b9ba2a87166afb4989b:

Uninstalling ICAgent on the Console
-----------------------------------

#. Log in to the LTS console and choose **Agent Management** in the navigation pane on the left.

#. Select one or more hosts where ICAgent is to be uninstalled and click **Uninstall ICAgent**.

#. In the **Uninstall ICAgent** dialog box, click **Yes**.

   The uninstallation begins. This process takes about a minute.

   When the ICAgent status changes from **Uninstalling** to **Uninstalled**, the ICAgent uninstallation has completed.

   .. note::

      To reinstall ICAgent, wait for 5 minutes after the uninstallation completes, or the reinstalled ICAgent may be unintentionally uninstalled again.

.. _lts_02_0015__en-us_topic_0178700396_s3b88a85d5fc54597bdb601e26408a808:

Uninstalling ICAgent on a Host
------------------------------

#. Log in to a host where ICAgent is to be uninstalled as user **root**.

#. Run the following command:

   **bash /opt/oss/servicemgr/ICAgent/bin/manual/uninstall.sh;**

   If the message **ICAgent uninstall success** is displayed, the uninstallation has completed.

.. _lts_02_0015__en-us_topic_0178700396_section6144172213109:

Remotely Uninstalling ICAgent
-----------------------------

You can uninstall ICAgent on one host remotely from another host.

#. On a host that has ICAgent installed, run the following command. *x.x.x.x* indicates the IP address of the host you wish to uninstall ICAgent from.

   **bash /opt/oss/servicemgr/ICAgent/bin/remoteUninstall/remote_uninstall.sh -ip** *x.x.x.x*

#. Enter the password for user **root** for the remote host.

   .. note::

      -  If the Expect tool has been installed on the host you are running the command from, ICAgent will be uninstalled from the remote host after the command is executed. If the Expect tool has not been installed, you will need to enter the password of user **root** for the remote host as prompted.
      -  Ensure that user **root** can run SSH or SCP commands on the host where ICAgent has been installed to communicate with the remote host.
      -  If the message **ICAgent uninstall success** is displayed, the uninstallation has completed.

.. _lts_02_0015__en-us_topic_0178700396_section1091572622115:

Batch Uninstalling ICAgent
--------------------------

If ICAgent has been installed on a host and the ICAgent installation package **ICProbeAgent.tar.gz** is in the **/opt/ICAgent/** directory of the host, you can use this method to uninstall ICAgent from multiple hosts at once.

.. important::

   The hosts must all belong to the same Virtual Private Cloud (VPC) and be on the same subnet.

**Prerequisites**

The IP addresses and passwords of all hosts to uninstall ICAgent have been collected, sorted in the **iplist.cfg** file, and uploaded to the **/opt/ICAgent/** directory on the host that has ICAgent installed. Each IP address and password in the **iplist.cfg** file must be separated by a space, as shown in the following example:

*192.168.0.109 Password* (Replace the IP address and password with the actual ones)

*192.168.0.39 Password* (Replace the IP address and password with the actual ones)

.. note::

   -  The **iplist.cfg** file contains sensitive information. You are advised to clear it after using it.

   -  If all hosts share a password, list only IP addresses in the **iplist.cfg** file and enter the password manually during execution. If one of the hosts uses a different password, type the password behind its IP address.

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

#. Choose **Agent Management** in the LTS navigation pane to view the ICAgent status of the host.
