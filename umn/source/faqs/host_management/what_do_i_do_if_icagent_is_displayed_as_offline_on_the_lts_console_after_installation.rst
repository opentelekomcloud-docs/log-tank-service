:original_name: en-us_topic_0000001727118868.html

.. _en-us_topic_0000001727118868:

What Do I Do If ICAgent Is Displayed as Offline on the LTS Console After Installation?
======================================================================================

In this case, perform the following steps:

#. Check whether the ICAgent network connection is normal.

   a. Log in to the host where ICAgent is installed.

   b. Run the **netstat -nap \| grep icagent** command to check whether the network connection status of the ICAgent process is **ESTABLISHED**. If yes, the network connection is normal.

      Check whether the connection status of ports 30200 and 30201 on the server is **ESTABLISHED**. If not, check whether these ports are allowed in the security group.

      |image1|

#. Check whether the ICAgent authentication is successful.

   a. Run the **cd /var/ICAgent** command to go to the ICAgent log directory.
   b. Run the **zgrep 'msworkflow' \* \| grep 'retCode\\['** command to query the ICAgent authentication log.

      -  If **200** is returned, the authentication is successful. If ICAgent is still offline, contact technical support.
      -  If the return code is not 200, check whether the AK/SK pair entered during ICAgent installation is correct. If not, go to the next step.

#. Obtain the correct AK/SK pair and install ICAgent again.

.. |image1| image:: /_static/images/en-us_image_0000001947827468.png
