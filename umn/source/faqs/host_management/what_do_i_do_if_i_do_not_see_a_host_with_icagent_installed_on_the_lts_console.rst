:original_name: lts_faq_0072.html

.. _lts_faq_0072:

What Do I Do If I Do Not See a Host with ICAgent Installed on the LTS Console?
==============================================================================

If a host with ICAgent installed is not displayed on the **Hosts** tab page on the LTS console, perform the following steps:

-  If you are configuring ECS log ingestion and do not see the host with ICAgent installed on the **Hosts** tab page:

   #. On the **Install ICAgent** page, ensure that the installation command is correctly copied. Do not use the installation command across regions.

   #. Ensure that the obtained AK/SK pair is correct and has not been deleted.

   #. Run the **netstat -nap \| grep icagent** command to check whether the network connection status of the host is **ESTABLISHED**. If yes, the network connection is normal.

      |image1|

-  If you are configuring CCE log ingestion and do not see the host with ICAgent installed on the **Hosts** tab page:

   #. Ensure that ICAgent has been installed in the CCE cluster.
   #. If ICAgent is not installed, click **CCE Cluster** on the **Hosts** tab page and click **Upgrade ICAgent**.

.. |image1| image:: /_static/images/en-us_image_0000001976408865.png
