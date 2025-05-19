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

      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | Template Name                      | Field Name                     | Field Type Can Be Changed | Field Can Be Deleted |
      +====================================+================================+===========================+======================+
      | ELB                                | Defined by ELB.                | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | VPC                                | Defined by VPC.                | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | CTS                                | Keys in JSON log events.       | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | APIG                               | Defined by APIG.               | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | DCS audit logs                     | Defined by DCS.                | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | TOMCAT                             | Defined by Tomcat.             | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | NGINX                              | Defined by Nginx.              | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | GAUSSV5 audit logs                 | Defined by GAUSSV5.            | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | DDS audit logs                     | Defined by DDS.                | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | DDS error logs                     | Defined by DDS.                | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | DDS slow query logs                | Defined by DDS.                | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | CFW access control logs            | Defined by CFW.                | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | CFW attack logs                    | Defined by CFW.                | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | CFW traffic logs                   | Defined by CFW.                | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | MySQL error logs                   | Defined by MySQL.              | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | MySQL slow query logs              | Defined by MySQL.              | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | POSTGRESQL slow query logs         | Defined by PostgreSQL.         | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | POSTGRESQL error logs              | Defined by PostgreSQL.         | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | SQLServer error logs               | Defined by SQL Server.         | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | GeminiDB Redis slow query logs     | Defined by GeminiDB Redis.     | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | CDN                                | Defined by CDN.                | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | SMN                                | Defined by SMN.                | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | GAUSSDB_MYSQL error logs           | Defined by GaussDB(for MySQL). | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | GaussDB_MySQL slow query logs      | Defined by GaussDB(for MySQL). | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | ER Enterprise Router               | Defined by Enterprise Router.  | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | MySQL audit logs                   | Defined by MySQL.              | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | GeminiDB Cassandra slow query logs | Defined by GeminiDB Cassandra. | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | GeminiDB Mongo slow query logs     | Defined by GeminiDB Mongo.     | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | GeminiDB Mongo error logs          | Defined by GeminiDB Mongo.     | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | WAF access logs                    | Defined by WAF.                | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | WAF attack logs                    | Defined by WAF.                | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | DMS rebalancing logs               | Defined by DMS.                | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | CCE audit logs                     | Defined by CCE.                | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | CCE event logs                     | Defined by CCE.                | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | CCE NGINX-INGRESS logs             | Defined by CCE.                | No                        | No                   |
      |                                    |                                |                           |                      |
      |                                    |                                |                           | ``-``                |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | GeminiDB Redis audit logs          | Defined by GeminiDB Redis.     | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | Influx slow query logs             | Defined by Influx.             | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | Microgateway                       | Defined by Microgateway.       | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+
      | GeminiDB Mongo audit logs          | Defined by GeminiDB Mongo.     | No                        | No                   |
      +------------------------------------+--------------------------------+---------------------------+----------------------+

4. Click **Save**.

Custom Templates
----------------

Click **Custom template** and select a template. Custom templates can be obtained in the following ways:

-  When you extract fields using methods of regular expression, JSON, delimiter, or Nginx, click **Save as Template** in the lower left corner. In the displayed dialog box, enter a template name and click **OK**. The template will be displayed in the custom template list.
-  Create a custom template under the **Structuring Template** option.

   #. Click **Custom template** and **Create Template**.
   #. On the displayed page, select **Regular Expressions**, **JSON**, **Delimiter**, or **Nginx**.
   #. After configuration, enter a template name and click **Save**. The template will be displayed in the custom template list.
