:original_name: lts_01_0003.html

.. _lts_01_0003:

Basic Concepts
==============

Log Groups
----------

A log group is a collection of log streams. It is similar to a folder and is used to classify and manage log streams. You can create log streams in a log group.

Log Streams
-----------

A log stream is the basic unit for log reads and writes.

You can sort logs of different types, such as operation logs and access logs, into different log streams. ICAgent will package and send the collected logs to LTS on a log stream basis. It makes it easier to find specific logs when you need them.

The use of log streams greatly reduces the number of log reads and writes and improves efficiency.

ICAgent
-------

ICAgent is the log collection tool of LTS. If you want to use LTS to collect logs from a host, you need to install ICAgent on the host. Batch ICAgent installation is supported if you want to collect logs from multiple hosts. After ICAgent installation, you can check the ICAgent status on the LTS console in real time.
