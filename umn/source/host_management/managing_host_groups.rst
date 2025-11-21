:original_name: lts_02_1033.html

.. _lts_02_1033:

Managing Host Groups
====================

A host group is a virtual group of hosts, allowing you to configure host log collection efficiently. You can add multiple hosts to a host group and associate the host group with log ingestion configurations. The ingestion configurations will then be applied to all the hosts in the host group.

-  When there is a new host, simply add it to a host group and the host will automatically inherit the log ingestion configurations associated with the host group.
-  You can also use host groups to modify the log collection paths for multiple hosts at one go.

You can create host groups of the IP address or custom identifier type.

-  :ref:`Creating a Host Group (IP Address) <lts_02_1033__en-us_topic_0000001118763740_section665755611241>`: Select hosts of the IP address type and add them to the host group.

-  :ref:`Creating a Host Group (Custom Identifier) <lts_02_1033__en-us_topic_0000001118763740_section6798040548>`: You need to create identifiers for each host group and host. Hosts with an identifier will automatically be included in the corresponding host group sharing that identifier.

   Host groups with custom identifiers are suitable for the following scenarios:

   -  In custom network environments like VPCs, potential IP address conflicts among hosts may impede ICAgent management in LTS. Using custom identifiers can resolve this issue.
   -  Multiple servers using the same custom identifier enable auto scaling of host groups. Simply assign a custom identifier for a new host; LTS will then automatically identify the host and add it to corresponding host group with the same identifier.

.. _lts_02_1033__en-us_topic_0000001118763740_section665755611241:

Creating a Host Group (IP Address)
----------------------------------

#. Log in to the management console and choose **Management & Deployment** > **Log Tank Service**.
#. Choose **Host Management** > **Host Groups** in the navigation pane.
#. Click **Create Host Group**.
#. In the displayed slide-out panel, enter a host group name, select **IP** for **Host Group Type**, and select a host OS (**Linux** or **Windows**). Enter remarks. Up to 1,024 characters are allowed.
#. In the host list, select one or more hosts to add to the group and click **OK**.

   -  You can filter hosts by host name, enterprise project, IPv4 address, or IPv6 address. You can also click **Search by Host IP Address** and enter multiple host IP addresses in the displayed search box to search for matches.
   -  If your desired hosts are not in the list, click **Install ICAgent**. On the displayed page, install ICAgent on the hosts as prompted. For details, see :ref:`Installing ICAgent (Intra-Region Hosts) <lts_02_0013>`.

.. _lts_02_1033__en-us_topic_0000001118763740_section6798040548:

Creating a Host Group (Custom Identifier)
-----------------------------------------

To create a host group of the custom identifier type, you need to plan the hosts to be identified in advance and ensure that ICAgent has been installed on the hosts.

#. Click **Create Host Group**.

#. In the displayed slide-out panel, enter a host group name, select **Custom identifier** for **Host Group Type**, and select a host OS (**Linux** or **Windows**). Enter remarks. Up to 1,024 characters are allowed.


   .. figure:: /_static/images/en-us_image_0000002143733644.png
      :alt: **Figure 1** Creating a custom identifier host group

      **Figure 1** Creating a custom identifier host group

#. Enter a custom identifier. You can also click **Add** to enter more.

   Up to 10 custom identifiers can be added.

#. Click **OK**. After the host group is created, go to :ref:`5 <lts_02_1033__en-us_topic_0000001118763740_li145128092916>` to add hosts to it.

#. .. _lts_02_1033__en-us_topic_0000001118763740_li145128092916:

   Perform the following operations to create the **custom_tag** file to save host tags:

   a. Log in to the host and run the following command to check for the **/opt/cloud** directory:

      .. code-block::

         cd /opt/cloud

      -  If the **/opt/cloud** directory does not exist, run the following command to create it:

         .. code-block::

            mkdir /opt/cloud/

      -  If the **/opt/cloud** directory already exists, navigate to it and run the following command to create the **lts** directory in it.

         .. code-block::

            mkdir lts

   b. Run the following command to change the permission on the **lts** directory:

      .. code-block::

         chmod 750 lts

   c. Run the following command in the **lts** directory to create the **custom_tag** file.

      .. code-block::

         cd lts
         touch custom_tag

   d. Run the following command to modify the **custom_tag** permission and open the file.

      .. code-block::

         chmod 640 custom_tag;vi custom_tag

   e. Press **i** to enter the insert mode, enter a custom identifier, press **Esc**, enter **:wq!**, save the modification and exit.

      .. code-block::

         :wq!

   f. Use either of the following methods to add a host to the custom identifier host group:

      .. table:: **Table 1** Methods

         +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Type                  | Method 1 (Recommended)                                                                                                                                                                                                                                                                                                                                                   | Method 2                                                                                                                                                                                                                                                                     |
         +=======================+==========================================================================================================================================================================================================================================================================================================================================================================+==============================================================================================================================================================================================================================================================================+
         | Linux host            | View the host's identifier in the **custom_tag** file of the **/opt/cloud/lts** directory on the host. Then, add the identifier to the host group to include the host within it. For example, if the **custom_tag** file in the **/opt/cloud/lts** directory shows the host's identifier as **test1**, simply add **test1** to the group's custom identifiers.           | -  Add the host group's custom identifier to the **custom_tag** file in the **/opt/cloud/lts** directory on the host to include the host within the host group. For example, if the group's custom identifier is **test**, enter **test** into the **custom_tag** file.      |
         |                       |                                                                                                                                                                                                                                                                                                                                                                          | -  If the group has multiple custom identifiers, simply enter any one of them into the **custom_tag** file of the **/opt/cloud/lts** directory on the host.                                                                                                                  |
         +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Windows host          | View the host's identifier in the **custom_tag** file of the **C:\\opt\\cloud\\lts** directory on the host. Then, add the identifier to the host group to include the host within it. For example, if the **custom_tag** file in the **C:\\opt\\cloud\\lts** directory shows the host's identifier as **test1**, simply add **test1** to the group's custom identifiers. | -  Add the host group's custom identifier to the **custom_tag** file in the **C:\\opt\\cloud\\lts** directory on the host to include the host within the host group. For example, if the group's custom identifier is **test**, enter **test** into the **custom_tag** file. |
         |                       |                                                                                                                                                                                                                                                                                                                                                                          | -  If the group has multiple custom identifiers, simply enter any one of them into the **custom_tag** file of the **C:\\opt\\cloud\\lts** directory on the host.                                                                                                             |
         +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Modifying a Host Group
----------------------

You can change the name of a host group, add hosts to or remove hosts from a host group, or associate a host group with log ingestion configurations. For details, see :ref:`Table 2 <lts_02_1033__en-us_topic_0000001118763740_table32281421165117>`.

.. _lts_02_1033__en-us_topic_0000001118763740_table32281421165117:

.. table:: **Table 2** Operations on host groups

   +--------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Operation                                                          | Procedure                                                                                                                                                                                                                            |
   +====================================================================+======================================================================================================================================================================================================================================+
   | Changing a host group name                                         | #. On the **Host Groups** list, click **Modify** in the **Operation** column of the target host group.                                                                                                                               |
   |                                                                    | #. On the displayed dialog box, modify the information such as the host group name and custom identifier.                                                                                                                            |
   |                                                                    | #. Click **OK**.                                                                                                                                                                                                                     |
   +--------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Adding hosts to a host group                                       | **Method 1:**                                                                                                                                                                                                                        |
   |                                                                    |                                                                                                                                                                                                                                      |
   |                                                                    | #. In the host group list, locate the host group whose host group type is **IP** and click |image1| next to the host group name.                                                                                                     |
   |                                                                    |                                                                                                                                                                                                                                      |
   |                                                                    | #. .. _lts_02_1033__en-us_topic_0000001118763740_li682633315215:                                                                                                                                                                     |
   |                                                                    |                                                                                                                                                                                                                                      |
   |                                                                    |    Click **Add Host**.                                                                                                                                                                                                               |
   |                                                                    |                                                                                                                                                                                                                                      |
   |                                                                    | #. In the displayed slide-out panel, all hosts that are not in the host group and run the selected OS type are displayed. Select the hosts to be added to the host group.                                                            |
   |                                                                    |                                                                                                                                                                                                                                      |
   |                                                                    |    -  You can filter hosts by host name, enterprise project, IPv4 address, or IPv6 address. You can also click **Search by Host IP Address** and enter multiple host IP addresses in the displayed search box to search for matches. |
   |                                                                    |    -  If your desired hosts are not in the list, click **Install ICAgent**. On the displayed page, install ICAgent on the hosts as prompted. For details, see :ref:`Installing ICAgent <lts_02_0013>`.                               |
   |                                                                    |                                                                                                                                                                                                                                      |
   |                                                                    | #. Click **OK**.                                                                                                                                                                                                                     |
   |                                                                    |                                                                                                                                                                                                                                      |
   |                                                                    | **Method 2:**                                                                                                                                                                                                                        |
   |                                                                    |                                                                                                                                                                                                                                      |
   |                                                                    | #. Choose **Host Management** > **Hosts** in the navigation pane.                                                                                                                                                                    |
   |                                                                    | #. In the host list, select the target hosts and click **Add to Host Group**.                                                                                                                                                        |
   |                                                                    | #. In the displayed slide-out panel, select the target host group.                                                                                                                                                                   |
   |                                                                    | #. Click **OK**.                                                                                                                                                                                                                     |
   +--------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Removing a host from a host group                                  | #. In the host group list, click |image2| in the row containing the target host group.                                                                                                                                               |
   |                                                                    | #. In the host list, click **Remove** in the **Operation** column of the row containing the host to be removed.                                                                                                                      |
   |                                                                    | #. In the displayed dialog box, click **OK**. This operation is not supported for hosts in the custom identifier host group.                                                                                                         |
   +--------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Uninstalling ICAgent from a host                                   | #. In the host group list, click |image3| in the row containing the target host group.                                                                                                                                               |
   |                                                                    | #. In the host list, click **Uninstall ICAgent** in the **Operation** column of the row containing the target host.                                                                                                                  |
   |                                                                    | #. In the displayed dialog box, click **OK** to uninstall ICAgent from the host and remove the host from the host group.                                                                                                             |
   |                                                                    |                                                                                                                                                                                                                                      |
   |                                                                    |    -  This operation is not supported for hosts in the custom identifier host group.                                                                                                                                                 |
   |                                                                    |    -  If the host has also been added to other host groups, it will be removed from those groups as well.                                                                                                                            |
   +--------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Removing hosts from a host group                                   | #. In the host group list, click |image4| in the row containing the target host group.                                                                                                                                               |
   |                                                                    | #. In the host list, select the target hosts and click the **Remove** button above the list.                                                                                                                                         |
   |                                                                    | #. Click **OK**.                                                                                                                                                                                                                     |
   +--------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Associating a host group with an ingestion configuration           | #. In the host group list, click |image5| in the row containing the target host group.                                                                                                                                               |
   |                                                                    | #. The **Hosts** tab page is displayed by default. Click the **Associated Ingestion Configurations** tab.                                                                                                                            |
   |                                                                    | #. Click **Associate**.                                                                                                                                                                                                              |
   |                                                                    | #. In the displayed slide-out panel, select the target ingestion configuration.                                                                                                                                                      |
   |                                                                    | #. Click **OK**. The associated ingestion configuration is displayed in the list.                                                                                                                                                    |
   +--------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Disassociating a host group from an ingestion configuration        | #. On the **Associated Ingestion Configurations** tab page, locate the target ingestion configuration, and then click **Disassociate** in the **Operation** column.                                                                  |
   |                                                                    | #. Click **OK**.                                                                                                                                                                                                                     |
   +--------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Disassociating a host group from multiple ingestion configurations | #. In the host group list, click |image6| in the row containing the target host group.                                                                                                                                               |
   |                                                                    | #. The **Hosts** tab page is displayed by default. Click the **Associated Ingestion Configurations** tab, select the target ingestion configurations, and then click **Disassociate** above the list.                                |
   |                                                                    | #. Click **OK**.                                                                                                                                                                                                                     |
   +--------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Copying a host group ID                                            | Hover your cursor over a host group name to copy the host group ID.                                                                                                                                                                  |
   +--------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Exporting host information                                         | #. On the **Hosts** page, switch to the **Intra-Region Hosts**, **CCE Cluster**, or **Extra-Region Hosts** tab and select the desired hosts.                                                                                         |
   |                                                                    | #. Click **Export** and choose **Export all data to an XLSX file** or **Export selected data to an XLSX file** to export the host information to your local PC.                                                                      |
   +--------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Deleting Host Groups
--------------------

You can delete a host group that is no longer needed.

.. warning::

   Deleting a host group may lead to log ingestion exceptions. In addition, deleted host groups cannot be restored.

#. Choose **Host Management** > **Host Groups** in the navigation pane.
#. Delete a host group:

   a. Click **Delete** in the **Operation** column of the target host group.
   b. In the displayed dialog box, click **OK**.

#. Delete host groups in batches:

   a. Select host groups to be deleted and click **Delete** above the list.
   b. In the displayed dialog box, click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001119882370.png
.. |image2| image:: /_static/images/en-us_image_0000001166682183.png
.. |image3| image:: /_static/images/en-us_image_0000001119722456.png
.. |image4| image:: /_static/images/en-us_image_0000001119882372.png
.. |image5| image:: /_static/images/en-us_image_0000001166602145.png
.. |image6| image:: /_static/images/en-us_image_0000002339501700.png
