:original_name: lts_05_0100.html

.. _lts_05_0100:

Overview
========

Log search and analysis are indispensable to O&M. After configuring log ingestion, you can search and analyze the collected log data on LTS. Its efficient and professional log collection, search, and analysis help you monitor and manage your systems and applications.

Log Structuring
---------------

Before searching and analyzing reported logs, you need to configure structuring and indexing for them. Structured data has a unified length and format, which can significantly improve search and analysis efficiency and accuracy.

Log data can be structured or unstructured.

-  Structured data refers to the data described using digits or unified data models. It has a fixed length and format, which facilitate storage and analysis.
-  Unstructured data has no pre-defined data models and cannot be fit into two-dimensional tables of databases. It is difficult to directly analyze unstructured data.

Log structuring extracts logs with fixed formats or high similarity from log streams and filters out irrelevant logs. .

Log structuring parsing is a process of converting log data from unstructured or semi-structured to structured for better storage, query, and analysis, improving log data readability, searchability, and query efficiency.

Log Search
----------

After structuring the logs, use LTS :ref:`search syntax <lts_05_0111>` to set search criteria with higher efficiency. For details, see :ref:`Accessing the Log Search Page <lts_05_0005>`.
