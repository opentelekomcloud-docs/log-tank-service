:original_name: lts_01_0005.html

.. _lts_01_0005:

Related Services
================

VPC
---

LTS provides a platform to store and analyze log data for Virtual Private Cloud (VPC). After VPC is associated with a log group and log stream in LTS, Network Interface Cards (NICs) logs are uploaded to LTS for preview, search, and storage.

OBS
---

Object Storage Service (OBS) is an object-based massive storage service. Logs can be transferred to OBS buckets for long-term storage.

IAM
---

Identity and Access Management (IAM) provides identity authentication and permissions management. LTS calls IAM APIs to obtain administrator permissions for log management.

CTS
---

If you enable **Trace Analysis** for a tracker in Cloud Trace Service (CTS), traces recorded by the tracker will be synchronized to LTS. You can then set custom filters to search for traces generated in the last 7 days in LTS.

WAF
---

You can record attack logs and access logs of Web Application Firewall (WAF) in LTS, and use the logs for real-time decision-making, device O&M, and service trend analysis.

ELB
---

You can ingest access logs of Elastic Load Balance (ELB) to a log stream of a log group in LTS. Then you can check the access logs to view details about HTTP and HTTPS requests sent to layer 7 load balancers and perform log analysis.
