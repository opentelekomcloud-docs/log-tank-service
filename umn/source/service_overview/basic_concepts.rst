:original_name: lts_01_0003.html

.. _lts_01_0003:

Basic Concepts
==============

Log Group
---------

A log group is the basic unit for LTS to manage logs. It comprises log streams and categorizes them, but does not store any log data itself.

Log Stream
----------

Log stream is the basic unit for log read and write. Collected logs of different types are classified and stored in different log streams for easier log management. If there are a large number of logs, you can create multiple log streams and name them for quick log search.

ICAgent
-------

ICAgent is the log collection tool of LTS. If you want to use LTS to collect logs from a host, you need to install ICAgent on the host. Batch ICAgent installation is supported if you want to collect logs from multiple hosts. After ICAgent installation, you can check the ICAgent status on the LTS console in real time.
