:original_name: lts_02_1033.html

.. _lts_02_1033:

Managing Host Groups
====================

Host groups allow you to configure host log ingestion efficiently. You can sort multiple hosts to a host group and associate the host group with log ingestion configurations. The ingestion configurations will be applied to all the hosts in the host group, saving you the trouble of configuring the hosts individually.

-  When there is a new host, simply add it to a host group and the host will automatically inherit the log ingestion configurations associated with the host group.
-  You can also use host groups to modify the log collection paths for multiple hosts at one go.

.. _lts_02_1033__en-us_topic_0000001118763740_section665755611241:

Creating a Host Group (IP Address)
----------------------------------

#. Log in to the LTS console, and choose **Host Management** in the navigation pane on the left. On the displayed page, click **Create Host Group** in the upper right corner.

#. In the displayed slide-out panel, enter a host group name and select a host OS (Linux).


   .. figure:: /_static/images/en-us_image_0000001424794336.png
      :alt: **Figure 1** Creating an IP address host group

      **Figure 1** Creating an IP address host group

#. In the host list, select one or more hosts to add to the group and click **OK**.

   -  You can filter hosts by host name or host IP address. You can also click |image1| and enter multiple host IP addresses in the displayed search box to search for matches.
   -  If your desired hosts are not in the list, click **Install ICAgent**. On the displayed page, install ICAgent on the hosts as prompted. For details, see :ref:`Installing ICAgent <lts_02_0013>`.

.. _lts_02_1033__en-us_topic_0000001118763740_section6798040548:

Creating a Host Group (Custom Identifier)
-----------------------------------------

#. Log in to the LTS console, and choose **Host Management** in the navigation pane on the left. On the displayed page, click **Create Host Group** in the upper right corner.

#. On the displayed **Create Host Group** page, enter a host group name in the **Host Group** field and set **Host Group OS** to **Custom Identifier**.


   .. figure:: /_static/images/en-us_image_0000001460010097.png
      :alt: **Figure 2** Creating a custom identifier host group

      **Figure 2** Creating a custom identifier host group

   .. note::

      -  A host group with a custom ID supports only Linux hosts.
      -  You can click **Learn about the rules for filling in the collection path** to learn how to configure paths.

#. Click **Add** to add a custom identifier.

   .. note::

      Up to 10 custom identifiers can be added.

#. Click **OK**.

#. .. _lts_02_1033__en-us_topic_0000001118763740_li1975952413820:

   Run the following commands to create the **custom_tag** file:

   a. Run the **cd /opt/cloud** command. In the **cloud** directory, run the **mkdir lts** command to create the **lts** directory.
   b. Run the **chmod 750 lts** command to modify the permission on the **lts** directory.
   c. Run the **touch custom_tag** command in the **lts** directory to create the **custom_tag** file.
   d. Run the **chmod 640 custom_tag;vi custom_tag** command to modify the **custom_tag** permission and open the file.
   e. Press **i** to enter the insert mode, enter a custom identifier, press **Esc**, enter **:wq!**, save the modification and exit.

   .. note::

      After :ref:`5 <lts_02_1033__en-us_topic_0000001118763740_li1975952413820>`, you can use either of the following methods to add hosts to a custom host group:

      Method 1 (recommended):

      **Linux**

      In the **custom_tag** file of the **/opt/cloud/lts** directory on the host, view the host identifier and add it to the custom host group identifiers to add the host to the host group. For example, in the **custom_tag** file of the **/opt/cloud/lts** directory on the host, the identifier of the host is **test1**, and the custom identifier of the host group is **test1**. That is, the host is added to the host group.

      Method 2:

      **Linux**

      -  To add a host to a host group, add the custom host group identifier to the **custom_tag** file in the **/opt/cloud/lts** directory on the host. For example, if the custom identifier of the host group is **test**, enter **test** in the **custom_tag** file to add the host to the host group.
      -  If multiple custom identifiers are added, enter any custom identifier in the **custom_tag** file of the **/opt/cloud/lts** directory on the host to add the host to the host group.

Modifying a Host Group
----------------------

You can change the name of a host group, add hosts to or remove hosts from a host group, or associate a host group with log ingestion configurations.

.. table:: **Table 1** Operations on host groups

   +--------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Operation                                                          | Procedure                                                                                                                                                                                              |
   +====================================================================+========================================================================================================================================================================================================+
   | Changing a host group name                                         | #. Log in to the LTS console. In the navigation pane on the left, choose **Host Management**.                                                                                                          |
   |                                                                    | #. On the **Host Groups** tab, click |image2| in the **Operation** column of the row containing the target host group.                                                                                 |
   |                                                                    | #. On the displayed dialog box, change the host group name and customized identifier.                                                                                                                  |
   |                                                                    | #. Click **OK**.                                                                                                                                                                                       |
   +--------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Adding hosts to a host group                                       | **Method 1:**                                                                                                                                                                                          |
   |                                                                    |                                                                                                                                                                                                        |
   |                                                                    | #. On the **Host Management** page, click the **Host Groups** tab, and click |image3| in the row containing the target host group.                                                                     |
   |                                                                    |                                                                                                                                                                                                        |
   |                                                                    | #. .. _lts_02_1033__en-us_topic_0000001118763740_li682633315215:                                                                                                                                       |
   |                                                                    |                                                                                                                                                                                                        |
   |                                                                    |    Click **Add Host**.                                                                                                                                                                                 |
   |                                                                    |                                                                                                                                                                                                        |
   |                                                                    | #. In the displayed slide-out panel, all hosts that are not in the host group and run the selected OS type are displayed. Select the hosts to be added to the host group.                              |
   |                                                                    |                                                                                                                                                                                                        |
   |                                                                    |    -  You can filter hosts by host name or host IP address. You can also click |image4| and enter multiple host IP addresses in the displayed search box to search for matches.                        |
   |                                                                    |    -  If your desired hosts are not in the list, click **Install ICAgent**. On the displayed page, install ICAgent on the hosts as prompted. For details, see :ref:`Installing ICAgent <lts_02_0013>`. |
   |                                                                    |                                                                                                                                                                                                        |
   |                                                                    | #. Click **OK**.                                                                                                                                                                                       |
   |                                                                    |                                                                                                                                                                                                        |
   |                                                                    | **Method 2:**                                                                                                                                                                                          |
   |                                                                    |                                                                                                                                                                                                        |
   |                                                                    | #. On the **Host Management** page, click the **Hosts** tab.                                                                                                                                           |
   |                                                                    | #. In the host list, select the target hosts and click **Add to Host Group**.                                                                                                                          |
   |                                                                    | #. In the displayed slide-out panel, select the target host group.                                                                                                                                     |
   |                                                                    | #. Click **OK**.                                                                                                                                                                                       |
   +--------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Removing a host from a host group                                  | #. On the **Host Management** page, click the **Host Groups** tab, and click |image5| in the row containing the target host group.                                                                     |
   |                                                                    | #. In the host list, click **Remove** in the **Operation** column of the row containing the host to be removed.                                                                                        |
   |                                                                    | #. In the displayed dialog box, click **OK**.                                                                                                                                                          |
   |                                                                    |                                                                                                                                                                                                        |
   |                                                                    | .. note::                                                                                                                                                                                              |
   |                                                                    |                                                                                                                                                                                                        |
   |                                                                    |    This operation is not supported for hosts in the custom identifier host group.                                                                                                                      |
   +--------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Uninstalling ICAgent from a host                                   | #. On the **Host Management** page, click the **Host Groups** tab, and click |image6| in the row containing the target host group.                                                                     |
   |                                                                    | #. In the host list, click **Uninstall ICAgent** in the **Operation** column of the row containing the target host.                                                                                    |
   |                                                                    | #. In the displayed dialog box, click **OK** to uninstall ICAgent from the host and remove the host from the host group.                                                                               |
   |                                                                    |                                                                                                                                                                                                        |
   |                                                                    |    .. note::                                                                                                                                                                                           |
   |                                                                    |                                                                                                                                                                                                        |
   |                                                                    |       -  This operation is not supported for hosts in the custom identifier host group.                                                                                                                |
   |                                                                    |       -  If the host has also been added to other host groups, it will be removed from those groups as well.                                                                                           |
   +--------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Removing hosts from a host group                                   | #. On the **Host Management** page, click the **Host Groups** tab, and click |image7| in the row containing the target host group.                                                                     |
   |                                                                    | #. In the host list, select the target hosts and click the **Remove** button above the list.                                                                                                           |
   |                                                                    | #. Click **OK**.                                                                                                                                                                                       |
   +--------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Associating a host group with an ingestion configuration           | #. On the **Host Management** page, click the **Host Groups** tab, and click |image8| in the row containing the target host group.                                                                     |
   |                                                                    | #. Click the **Associated Ingestion Configuration** tab.                                                                                                                                               |
   |                                                                    | #. Click **Associate**.                                                                                                                                                                                |
   |                                                                    | #. In the displayed slide-out panel, select the target ingestion configuration.                                                                                                                        |
   |                                                                    | #. Click **OK**. The associated ingestion configuration is displayed in the list.                                                                                                                      |
   +--------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Disassociating a host group from an ingestion configuration        | #. On the **Associated Ingestion Configuration** tab, click **Disassociate** in the **Operation** column of the row containing the target ingestion configuration.                                     |
   |                                                                    | #. Click **OK**.                                                                                                                                                                                       |
   +--------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Disassociating a host group from multiple ingestion configurations | #. On the **Associated Ingestion Configuration** tab, select the target ingestion configurations and click the **Disassociate** button above the list.                                                 |
   |                                                                    | #. Click **OK**.                                                                                                                                                                                       |
   +--------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Deleting Host Groups
--------------------

**Deleting a single host group**

#. Log in to the LTS console. In the navigation pane on the left, choose **Host Management**.

#. On the **Host Groups** tab, click |image9| in the **Operation** column of the row containing the target host group.


   .. figure:: /_static/images/en-us_image_0000001459933005.png
      :alt: **Figure 3** Deleting a host group

      **Figure 3** Deleting a host group

#. In the displayed dialog box, click **OK**.

**Deleting host groups in batches**

#. On the **Host Groups** tab, select multiple host groups to be deleted and click **Delete** above the list.
#. In the displayed dialog box, click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001165708405.png
.. |image2| image:: /_static/images/en-us_image_0000001119722454.png
.. |image3| image:: /_static/images/en-us_image_0000001119882370.png
.. |image4| image:: /_static/images/en-us_image_0000001166602143.png
.. |image5| image:: /_static/images/en-us_image_0000001166682183.png
.. |image6| image:: /_static/images/en-us_image_0000001119882370.png
.. |image7| image:: /_static/images/en-us_image_0000001119882370.png
.. |image8| image:: /_static/images/en-us_image_0000001119882370.png
.. |image9| image:: /_static/images/en-us_image_0000001165793419.png
