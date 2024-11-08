:original_name: lts_0829.html

.. _lts_0829:

Installing ICAgent
==================

ICAgent is the log collection tool of LTS. Install ICAgent on a host from which you want to collect logs.

If ICAgent has been installed on the host when you use other cloud services, skip the installation.

Prerequisites
-------------

Before installing ICAgent, ensure that the time and time zone of your local browser are consistent with those of the host.


Installing ICAgent
------------------

#. Log in to the management console and choose **Management & Deployment** > **Log Tank Service**.

#. In the navigation pane, choose **Host Management**.

#. Click **Install ICAgent** in the upper right corner.


   .. figure:: /_static/images/en-us_image_0000001795704605.png
      :alt: **Figure 1** Installing ICAgent

      **Figure 1** Installing ICAgent

#. Set **Host** to **Intra-Region Hosts**.

#. Set **OS** to **Linux**.

#. Set **Installation Mode** to **Obtain AK/SK**.

   .. note::

      Ensure that the public account and AK/SK will not be deleted or disabled. If the AK/SK is deleted, the ICAgent cannot report data to LTS.

   Obtain and use the AK/SK of a public account.

   The Access Key ID/Secret Access Key (AK/SK) can be obtained on the **My Credentials** page. The procedure is as follows:

   a. Hover the mouse pointer over the username in the upper right corner of the page and select **My Credentials**.
   b. On the **My Credentials** page, choose **Access Keys**.
   c. Click **Create Access Key** and enter a description.

      .. note::

         Up to 2 access keys can be created for each user. An access key can be downloaded only right after it is created. If the **Create Access Key** button is grayed out, delete an access key first before creating one.

   d. Click **OK**, download the AK/SK, and keep it secure.

#. Click **Copy Command** to copy the ICAgent installation command.

#. Log in as user **root** to the host (for example, by using a remote login tool such as PuTTY). Run the copied command and enter the obtained AK/SK to install ICAgent.

   When message **ICAgent install success** is displayed, ICAgent has been installed in the **/opt/oss/servicemgr/** directory of the host. You can then view the ICAgent status on the **Hosts** tab of the **Host Management** page on the LTS console.
