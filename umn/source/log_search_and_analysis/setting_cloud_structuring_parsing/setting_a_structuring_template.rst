:original_name: lts_0824.html

.. _lts_0824:

Setting a Structuring Template
==============================

LTS supports two types of structuring templates: system and custom templates.

System Templates
----------------

You can choose from multiple system templates, but cannot modify the field types in them or delete the fields. For details, see :ref:`Table 1 <lts_0824__en-us_topic_0000001532747921_table1181293435214>`.

#. On the **Cloud Structuring Parsing** tab page, select **Structuring Template**.
#. Click **System template** and select a template. A sample log event is displayed for each template.

3. View the log parsing results in the **Template Details** table.

   -  If you select a system template for structuring, it uses the custom log time.
   -  Fields of the string type do not support range query using the >, =, or < operators or the "in" syntax. Use asterisks (*) or question marks (?) for fuzzy query. You need to reconfigure the structuring and change the value of this field to a number.
   -  Supporting system templates for a cloud service does not mean logs of that service have been ingested to LTS. To view services with log ingestion configured, navigate to the **Ingestion Center** page under **Log Ingestion** on the LTS console.

   .. _lts_0824__en-us_topic_0000001532747921_table1181293435214:

   .. table:: **Table 1** System template fields

      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | Template Name                      | Template Description           | Field Type Can Be Changed | Field Can Be Deleted | Request Parameter       |
      +====================================+================================+===========================+======================+=========================+
      | ELB                                | Defined by ELB.                | No                        | No                   | ELB                     |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | VPC                                | Defined by VPC.                | No                        | No                   | VPC                     |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | CTS                                | Keys in JSON log events.       | No                        | No                   | CTS                     |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | APIG                               | Defined by APIG.               | No                        | No                   | APIG                    |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | DCS audit logs                     | Defined by DCS.                | No                        | No                   | DCS_AUDIT               |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | TOMCAT                             | Defined by Tomcat.             | No                        | No                   | TOMCAT                  |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | NGINX                              | Defined by Nginx.              | No                        | No                   | NGINX                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | GAUSSV5 audit logs                 | Defined by GAUSSV5.            | No                        | No                   | GAUSSDB_OPENGAUSS_AUDIT |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | DDS audit logs                     | Defined by DDS.                | No                        | No                   | DDS_AUDIT               |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | DDS error logs                     | Defined by DDS.                | No                        | No                   | MONGODB_ERROR           |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | DDS slow query logs                | Defined by DDS.                | No                        | No                   | MONGODB_SLOW            |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | CFW access control logs            | Defined by CFW.                | No                        | No                   | CFW_ACCESS              |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | CFW attack logs                    | Defined by CFW.                | No                        | No                   | CFW_ATTACK              |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | CFW traffic logs                   | Defined by CFW.                | No                        | No                   | CFW_FLOW                |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | MySQL error logs                   | Defined by MySQL.              | No                        | No                   | MYSQL_ERROR             |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | MySQL slow query logs              | Defined by MySQL.              | No                        | No                   | MYSQL_SLOW              |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | POSTGRESQL slow query logs         | Defined by PostgreSQL.         | No                        | No                   | POSTGRESQL_SLOW         |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | POSTGRESQL error logs              | Defined by PostgreSQL.         | No                        | No                   | POSTGRESQL_ERROR        |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | SQLServer error logs               | Defined by SQL Server.         | No                        | No                   | SQLSERVER_ERROR         |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | GeminiDB Redis slow query logs     | Defined by GeminiDB Redis.     | No                        | No                   | GAUSSDB_REDIS_SLOW      |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | CDN                                | Defined by CDN.                | No                        | No                   | CDN                     |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | SMN                                | Defined by SMN.                | No                        | No                   | SMN                     |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | ER Enterprise Router               | Defined by Enterprise Router.  | No                        | No                   | ER                      |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | MySQL audit logs                   | Defined by MySQL.              | No                        | No                   | MYSQL_AUDIT             |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | GeminiDB Cassandra slow query logs | Defined by GeminiDB Cassandra. | No                        | No                   | GAUSSDB_CASSANDRA_SLOW  |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | GeminiDB Mongo slow query logs     | Defined by GeminiDB Mongo.     | No                        | No                   | GAUSSDB_MONGO_SLOW      |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | GeminiDB Mongo error logs          | Defined by GeminiDB Mongo.     | No                        | No                   | GAUSSDB_MONGO_ERROR     |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | WAF access logs                    | Defined by WAF.                | No                        | No                   | WAF_ACCESS              |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | WAF attack logs                    | Defined by WAF.                | No                        | No                   | WAF_ATTACK              |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | DMS rebalancing logs               | Defined by DMS.                | No                        | No                   | DMS_REBALANCED          |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | CCE audit logs                     | Defined by CCE.                | No                        | No                   | CCE_AUDIT               |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | CCE event logs                     | Defined by CCE.                | No                        | No                   | CCE_EVENT               |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | CCE NGINX-INGRESS logs             | Defined by CCE.                | No                        | No                   | NGINX_INGRESS           |
      |                                    |                                |                           |                      |                         |
      |                                    |                                |                           | ``-``                |                         |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | GeminiDB Redis audit logs          | Defined by GeminiDB Redis.     | No                        | No                   | GAUSSDB_REDIS_AUDIT     |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | Influx slow query logs             | Defined by Influx.             | No                        | No                   | GAUSSDB_INFLUX_SLOW     |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | Microgateway                       | Defined by Microgateway.       | No                        | No                   | MICROGATEWAY            |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | GeminiDB Mongo audit logs          | Defined by GeminiDB Mongo.     | No                        | No                   | GEMINIDB_MONGODB_AUDIT  |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | CloudTable Doris audit logs        | Defined by CloudTable Doris.   | No                        | No                   | CLOUD_TABLE_DORIS       |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+
      | CoreDNS logs                       | Defined by CoreDNS.            | No                        | No                   | COREDNS_LOG             |
      +------------------------------------+--------------------------------+---------------------------+----------------------+-------------------------+

4. Click **Save**.

Custom Templates
----------------

Click **Custom template** and select a template. Custom templates can be obtained in the following ways:

-  When you extract fields using the regular expression, JSON, delimiter, or Nginx method, click **Save as Template** in the lower left corner. In the displayed dialog box, enter a template name and click **OK**. The template will be displayed in the custom template list.
-  Create a custom template under the **Structuring Template** option.

   #. Click **Custom template** and **Create Template**.
   #. On the displayed page, select **Regular Expressions**, **JSON**, **Delimiter**, or **Nginx**.
   #. After configuration, enter a template name and click **Save**. The template will be displayed in the custom template list.
