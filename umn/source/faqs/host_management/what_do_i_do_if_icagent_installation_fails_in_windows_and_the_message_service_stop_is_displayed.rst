:original_name: lts_faq_0120.html

.. _lts_faq_0120:

What Do I Do If ICAgent Installation Fails in Windows and the Message "SERVICE STOP" Is Displayed?
==================================================================================================

Background
----------

The ICAgent installation fails and the message **SERVICE STOP** is displayed.

The following issues may occur after the installation fails:

-  No ICAgent task exists in the task manager.
-  No ICAgent service exists in the system service list.
-  When **sc query icagent** is executed in the command line tool (CLI), a message is displayed, indicating that no ICAgent was found.

Possible Causes
---------------

The ICAgent registration is blocked by antivirus software, such as 360 Total Security.

Solution
--------

#. Check whether any antivirus software is running. If yes, go to the next step.
#. Stop the antivirus software and install ICAgent again.
