:original_name: lts_0822.html

.. _lts_0822:

Overview
========

Log data can be structured or unstructured. Structured data is quantitative data or can be defined by unified data models. It has a fixed length and format. Unstructured data has no pre-defined data models and cannot be fit into two-dimensional tables of databases.

During log structuring, logs with fixed or similar formats are extracted from a log stream based on your defined structuring method and irrelevant logs are filtered out.

Log structuring parsing is a process of converting log data from unstructured or semi-structured to structured for better storage, query, and analysis, improving log data readability, searchability, and query efficiency.

Precautions
-----------

-  Log structuring is performed on a per-log-stream basis.
-  Log structuring is recommended when most logs in a log stream share a similar pattern.
-  After the structuring configuration is modified, the modification takes effect only for newly written log data.
