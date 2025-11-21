:original_name: lts_02_0828.html

.. _lts_02_0828:

Installing ICAgent (Extra-Region Hosts)
=======================================

ICAgent is a log collection tool for LTS. To use LTS to collect logs from extra-region hosts, you need to install ICAgent on the hosts. This section describes how to install ICAgent on an extra-region host.

Prerequisites
-------------

Before installing ICAgent, ensure that the time and time zone of your local browser are consistent with those of the host. If they are inconsistent, errors may occur during log reporting.

Installation Scenarios
----------------------

There are two methods to install ICAgent. Select one that best suits your needs.

.. table:: **Table 1** Installation scenarios

   +---------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------+
   | Scenario                                                | Description                                                                                                               |
   +=========================================================+===========================================================================================================================+
   | Initial installation                                    | You can use this method to install ICAgent on a host that has no ICAgent installed.                                       |
   +---------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------+
   | Inherited installation (supported only for Linux hosts) | When ICAgent has already been installed on one host but needs to be installed on multiple hosts, you can use this method. |
   +---------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------+

Initial Installation (Linux)
----------------------------

Before installing ICAgent on a host not in this region, apply for an ECS as a jump server on the ECS console. For details, see :ref:`Creating Multiple Jump Servers for Load Balancing Using ELB <lts_02_0828__en-us_topic_0000001200587559_section193401224185619>`.

.. note::

   You are advised to use **CentOS 6.5 64bit** or later images. The minimum flavor for the ECS is 1 vCPU and 1 GB of memory, while the recommended flavor is 2 vCPUs and 4 GB of memory.

#. Log in to the management console and choose **Management & Deployment** > **Log Tank Service**.

#. Choose **Host Management** > **Hosts** in the navigation pane.

#. Click **Install ICAgent** in the upper right corner.

#. Set **Host** to **Extra-region hosts**.

#. Set **OS** to **Linux**.

#. Set **Network Connectivity**. For extra-region hosts to report logs to LTS in the current region, you are advised to select **Private line** for higher stability and reliability.

   .. note::

      **Private line**: Extra-region hosts connect to LTS in the current region through a jump server or VPC Endpoint (VPCEP), offering greater security and stability. In this scenario, extra-region hosts cannot communicate with LTS in the current region by default, and ICAgent installed on these hosts cannot directly access the network segment used by LTS in the current region to report logs. Therefore, you need to configure a network connection solution to use a jump server or VPCEP to connect to the LTS backend and forward data to LTS.

      -  Jump server: functions as a data forwarder and forwards the data collected by ICAgent from extra-region hosts to LTS. This solution is suitable for tests or scenarios with low log traffic. VPCEP is recommended for scenarios with high log traffic.
      -  VPCEP: provides private channels to connect your VPC to LTS in the current region. This solution reduces the risks of data transmission on public networks and improves the transmission security and efficiency.

#. If you set **LTS Backend Connection** to **VPCEP**, enter the VPCEP domain name and go to :ref:`9 <lts_02_0828__en-us_topic_0000001200587559_en-us_topic_0174154559_en-us_topic_0173929603_li572917483129>`.

   With the assistance of network engineers, configure DNS domain name resolution rules on other clouds to resolve VPCEP domain names to specified IP addresses.

   Then, copy the ping command displayed on this page and run it on the target host whose logs are to be collected. A successful ping test indicates that the network configuration is correct.

#. Enable forwarding ports on the jump server. This step is mandatory when **LTS Backend Connection** is set to **Jump server**.

   a. Apply for an ECS in the current region as a jump server.

   b. Add security group rules for the jump server and enable the corresponding inbound ports to ensure data connectivity between the extra-region hosts and the jump server.

      #. On the ECS console, click the ECS name to access the details page, and click the **Security Groups** tab. The security group list is displayed.

      #. Click a security group name to access the details page.

      #. On the security group details page, click the **Inbound Rules** tab and then click **Add Rule**. On the page displayed, add a security group rule based on :ref:`Table 2 <lts_02_0828__en-us_topic_0000001200587559_table94613420541>`.

         .. _lts_02_0828__en-us_topic_0000001200587559_table94613420541:

         .. table:: **Table 2** Security group rule

            +-----------+----------+----------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+
            | Direction | Protocol | Port                                   | Description                                                                                                                         |
            +===========+==========+========================================+=====================================================================================================================================+
            | Inbound   | TCP      | 8149, 8102, 8923, 30200, 30201, and 80 | Ports used by ICAgent to send data to the jump server, ensuring data connectivity between VMs in other regions and the jump server. |
            +-----------+----------+----------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+

   c. Go back to the LTS console. On the **Install ICAgent** page, enter the obtained private IP address of the jump server to generate its SSH tunneling command. The private IP address of the jump server refers to the internal IP address of the VPC where the jump server is located.


      .. figure:: /_static/images/en-us_image_0000002017782149.png
         :alt: **Figure 1** Entering the private IP address of the jump server

         **Figure 1** Entering the private IP address of the jump server

   d. On the **Install ICAgent** page, click **Copy Command** to copy the SSH tunneling command.

   e. Log in to the jump server as user **root** and run the SSH tunneling command.

      Enter the password of user **root** as prompted.

   f. Run the following command to check whether the corresponding ports are being listened to. If the command output similar to :ref:`Figure 2 <lts_02_0828__en-us_topic_0000001200587559_en-us_topic_0174154559_en-us_topic_0173929603_fig2754142620246>` is returned, the TCP ports are open.

      .. code-block::

         netstat -lnp | grep ssh

      .. _lts_02_0828__en-us_topic_0000001200587559_en-us_topic_0174154559_en-us_topic_0173929603_fig2754142620246:

      .. figure:: /_static/images/en-us_image_0000001155057118.png
         :alt: **Figure 2** Verification results of TCP ports

         **Figure 2** Verification results of TCP ports

      .. note::

         If the jump server powers off and restarts, run the preceding command again.

   g. Obtain an AK/SK and specify **DC** and **Connection IP**.

      -  **DC**: Specify a name for the data center of the host so it is easier to find the host.
      -  **Connection IP**: For EIP connection, use the EIP of the jump server. For VPC peering connection, use the internal IP address of the VPC where the jump server locates.

#. .. _lts_02_0828__en-us_topic_0000001200587559_en-us_topic_0174154559_en-us_topic_0173929603_li572917483129:

   Copy the ICAgent installation command on the **Install ICAgent** page.

#. Log in as user **root** to the host which is deployed in the region same as that you are logged in to (by using a remote login tool such as PuTTY) and run the copied command.

   .. note::

      -  When message "ICAgent install success" is displayed, ICAgent has been installed in the **/opt/oss/servicemgr/** directory of the host. You can then choose **Host Management** > **Hosts** in the navigation pane of the LTS console to check the ICAgent status.
      -  If the installation fails, uninstall ICAgent and then install it again. For details, see :ref:`Uninstalling ICAgent <lts_02_0014__en-us_topic_0000001167072801_section109081507198>`.
      -  The NIC information is obtained by ICAgent installed on the node using the **ifconfig** command. If **inet** information is not configured for the NIC, the IPv4 address is not reported, and **--** is displayed in the **Host IPv4 Address** column on the **Hosts** page. If **inet6** information is not configured, the IPv6 address is not reported, and **--** is displayed in the **Host IPv6 Address** column on the **Hosts** page.

Initial Installation (Windows)
------------------------------

Before installing ICAgent on a host not in this region, apply for a Linux ECS as a jump server on the ECS console. For details, see :ref:`Creating Multiple Jump Servers for Load Balancing Using ELB <lts_02_0828__en-us_topic_0000001200587559_section193401224185619>`.

.. note::

   You are advised to use **CentOS 6.5 64bit** or later images. The minimum flavor for the ECS is 1 vCPU and 1 GB of memory, while the recommended flavor is 2 vCPUs and 4 GB of memory.

#. Click **Install ICAgent** in the upper right corner.

#. Set **Host** to **Extra-region hosts**.

#. Set **OS** to **Windows**.

#. Set **Network Connectivity**. For extra-region hosts to report logs to LTS in the current region, you are advised to select **Private line** for higher stability and reliability.

   .. note::

      **Private line**: Extra-region hosts connect to LTS in the current region through a jump server or VPC Endpoint (VPCEP), offering greater security and stability. In this scenario, extra-region hosts cannot communicate with LTS in the current region by default, and ICAgent installed on these hosts cannot directly access the network segment used by LTS in the current region to report logs. Therefore, you need to configure a network connection solution to use a jump server or VPCEP to connect to the LTS backend and forward data to LTS.

      -  Jump server: functions as a data forwarder and forwards the data collected by ICAgent from extra-region hosts to LTS. This solution is suitable for tests or scenarios with low log traffic. VPCEP is recommended for scenarios with high log traffic.
      -  VPCEP: provides private channels to connect your VPC to LTS in the current region. This solution reduces the risks of data transmission on public networks and improves the transmission security and efficiency.

#. If you set **LTS Backend Connection** to **VPCEP**, enter the VPCEP domain name and go to :ref:`7 <lts_02_0828__en-us_topic_0000001200587559_li176451219830>`.

   With the assistance of network engineers, configure DNS domain name resolution rules on other clouds to resolve VPCEP domain names to specified IP addresses.

   Then, copy the ping command displayed on this page and run it on the target host whose logs are to be collected. A successful ping test indicates that the network configuration is correct.

#. Enable forwarding ports on the jump server. This step is mandatory when **LTS Backend Connection** is set to **Jump server**.

   a. Apply for a Linux ECS in the current region as a jump server.

   b. Modify the security group rule used by the jump server.

      #. On the ECS details page, click the **Security Groups** tab.

      #. Click a security group name to access the details page.

      #. On the security group details page, click the **Inbound Rules** tab and then click **Add Rule**. On the page displayed, add a security group rule based on :ref:`Table 3 <lts_02_0828__en-us_topic_0000001200587559_en-us_topic_0174154559_en-us_topic_0173929603_table1218216483590>`.

         .. _lts_02_0828__en-us_topic_0000001200587559_en-us_topic_0174154559_en-us_topic_0173929603_table1218216483590:

         .. table:: **Table 3** Security group rule

            +-----------+----------+----------------------------------------+---------------------------------------------------------------------+
            | Direction | Protocol | Port                                   | Description                                                         |
            +===========+==========+========================================+=====================================================================+
            | Inbound   | TCP      | 8149, 8102, 8923, 30200, 30201, and 80 | ICAgent will send data to the jump server through the listed ports. |
            +-----------+----------+----------------------------------------+---------------------------------------------------------------------+

   c. Go back to the LTS console. On the **Install ICAgent** page, enter the obtained private IP address of the jump server to generate its SSH tunneling command. The private IP address of the jump server refers to the internal IP address of the VPC where the jump server is located.

   d. On the **Install ICAgent** page, click **Copy Command** to copy the SSH tunneling command.

   e. Log in to the jump server as user **root** and run the SSH tunneling command.

      Enter the password of user **root** as prompted.

   f. Run the **netstat -lnp \| grep ssh** command to check whether the corresponding ports are being listened to. If the command output similar to :ref:`Figure 3 <lts_02_0828__en-us_topic_0000001200587559_fig27641128182815>` is returned, the TCP ports are open.

      .. _lts_02_0828__en-us_topic_0000001200587559_fig27641128182815:

      .. figure:: /_static/images/en-us_image_0000001200507455.png
         :alt: **Figure 3** Verification results of TCP ports

         **Figure 3** Verification results of TCP ports

      .. note::

         If the jump server powers off and restarts, run the preceding command again.

#. .. _lts_02_0828__en-us_topic_0000001200587559_li176451219830:

   Download the ICAgent installation package to the local PC as prompted.

#. Save the ICAgent installation package to a directory on the Windows host, for example, **C:\\ICAgent**, and decompress the package.

#. Obtain an AK/SK and save it to replace the AK/SK in the installation command.

#. Generate the installation command and copy it.

   a. Enter the connection IP in the text box and replace the AK/SK to generate the installation command.

      **Connection IP**: For EIP connection, use the EIP of the jump server. For VPC peering connection, use the internal IP address of the VPC where the jump server locates.

   b. Click **Copy Command** to copy the ICAgent installation command.

#. Open the Command Prompt, go to the directory where the ICAgent installation package is decompressed, and run the copied command.

   .. note::

      -  If the message "Service icagent installed successfully" is displayed, the installation is successful. You can then choose **Host Management** > **Hosts** in the navigation pane of the LTS console to check the ICAgent status.
      -  If the installation fails, uninstall ICAgent and then install it again. For details, see :ref:`Uninstalling ICAgent <lts_02_0014__en-us_topic_0000001167072801_section109081507198>`.
      -  The NIC information is obtained by ICAgent installed on the node using the **ifconfig** command. If **inet** information is not configured for the NIC, the IPv4 address is not reported, and **--** is displayed in the **Host IPv4 Address** column on the **Hosts** page. If **inet6** information is not configured, the IPv6 address is not reported, and **--** is displayed in the **Host IPv6 Address** column on the **Hosts** page.

.. _lts_02_0828__en-us_topic_0000001200587559_section193401224185619:

Creating Multiple Jump Servers for Load Balancing Using ELB
-----------------------------------------------------------

A single jump server may encounter a single point of failure (SPOF), potentially leading to O&M instability. To mitigate this, you can create multiple jump servers and use ELB to distribute traffic among them, enhancing access reliability.

#. .. _lts_02_0828__en-us_topic_0000001200587559_li4393122623411:

   Create a Linux ECS that as a jump server.

   Log in to the ECS console and create a Linux ECS. If you already have an ECS that meets the requirements, you can directly use it as the jump server.

   .. note::

      Configure the CPU and memory based on the service requirements. The recommended specifications are 2 vCPUs and 4 GB of memory, or above.

#. Add security group rules for the jump server and enable the corresponding inbound ports to ensure data connectivity between the extra-region hosts and the jump server.

   a. Log in to the ECS console, check the ECS list, and locate the ECS that you created as the jump server.

   b. Click its name to go to the ECS details page. Click the security group name to access the security group details page.

   c. Click the **Inbound Rules** tab and click **Add Rule**. Set the ports by referring to :ref:`Table 4 <lts_02_0828__en-us_topic_0000001200587559_table1090118814816>`. Set other parameters based on your network requirements.

      .. _lts_02_0828__en-us_topic_0000001200587559_table1090118814816:

      .. table:: **Table 4** Security group rule

         +--------+----------+-------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+
         | Action | Protocol | Port                          | Description                                                                                                                           |
         +========+==========+===============================+=======================================================================================================================================+
         | Allow  | TCP      | 8149,8102,8923,30200,30201,80 | Ports used by ICAgent to send data to the jump server, ensuring data connectivity between hosts in other regions and the jump server. |
         +--------+----------+-------------------------------+---------------------------------------------------------------------------------------------------------------------------------------+

#. Return to the ECS list, locate the ECS created in :ref:`1 <lts_02_0828__en-us_topic_0000001200587559_li4393122623411>`, and view its private IP address and EIP (available if an EIP has been enabled).

#. Log in to the LTS console. In the navigation pane, choose **Host Management** > **Hosts**. Click **Install ICAgent**. On the displayed page, enter the private IP address of the jump server to generate the SSH tunneling command. The private IP address of the jump server refers to the internal IP address of the VPC where the jump server is located.

#. On the **Install ICAgent** page, click **Copy Command** to copy the SSH tunneling command.

#. Log in to the jump server as user **root** and run the copied SSH tunneling command.

#. Repeat the preceding steps to create multiple jump servers. Add them to the same VPC by selecting the same VPC for **Network** during their creation.

8.  Log in to the ELB console and create a load balancer. When creating the load balancer, you should:

    a. Select the same VPC as that of the jump servers.
    b. Create an EIP for connecting to the jump servers.
    c. Apply for the bandwidth based on the service requirements.

9.  Add listeners for TCP ports 30200, 30201, 8149, 8923, and 8102.
10. Create a backend server group and add all the jump servers to it.
11. Return to the LTS console. On the **Install ICAgent** page, enter the EIP of the load balancer in **Connection IP**, copy the installation command, and run it on the extra-region host.

Inherited Installation (Linux)
------------------------------

Assume that you need to install ICAgent on multiple hosts, and one of the hosts already has ICAgent installed. The ICAgent installation package, **ICProbeAgent.tar.gz**, is in the **/opt/ICAgent/** directory. To install ICAgent on other hosts one by one:

#. Run the following command on the host where ICAgent has been installed, where *x.x.x.x* is the IP address of the host you want to install ICAgent on.

   .. code-block::

      bash /opt/oss/servicemgr/ICAgent/bin/remoteInstall/remote_install.sh -ip x.x.x.x

#. Enter the password for user **root** of the host when prompted.

   .. note::

      -  If the Expect tool is installed on the host that has ICAgent installed, the ICAgent installation should be able to complete without prompting you for a password. Otherwise, enter the password as prompted.
      -  Ensure that user **root** can run SSH or SCP commands on the host where ICAgent has been installed to remotely communicate with the remote host to install ICAgent.
      -  When message "ICAgent install success" is displayed, ICAgent has been installed in the **/opt/oss/servicemgr/** directory of the host. You can then choose **Host Management** > **Hosts** in the navigation pane of the LTS console to check the ICAgent status.
      -  If the installation fails, uninstall ICAgent and reinstall it. If the reinstallation fails, contact technical support.

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

-  If all servers share the same password, the **iplist.cfg** file only needs to include the IP addresses, not passwords. You need to enter the password during execution. If an IP address has a different password, enter the password after the IP address.

Perform the following operations:

#. Run the following command on the host that has ICAgent installed:

   .. code-block::

      bash /opt/oss/servicemgr/ICAgent/bin/remoteInstall/remote_install.sh -batchModeConfig /opt/ICAgent/iplist.cfg

   Enter the default password for user **root** of the hosts to install ICAgent. If the passwords of all hosts have been configured in the **iplist.cfg** file, press **Enter** to skip this step.

   Wait for a while. When message "Install ICAgent success" is displayed, ICAgent has been installed on all the hosts listed in the configuration file.

#. Choose **Host Management** > **Hosts** in the navigation pane of the LTS console to check the hosts' ICAgent statuses. For details, see :ref:`Checking the ICAgent Status <lts_02_0014__en-us_topic_0000001167072801_section18919294522>`.
