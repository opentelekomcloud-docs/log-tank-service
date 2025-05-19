:original_name: lts_04_1112.html

.. _lts_04_1112:

Ingesting Logs to LTS Across IAM Accounts
=========================================

If you choose **Cross-Account Ingestion - Log Stream Mapping** as the log ingestion type, you can create an agency to map the log stream of the delegator account to that of the delegated account. The delegated account is the current account used to log in to LTS.

Prerequisites
-------------

An agency relationship has been created.

Constraints
-----------

Before data synchronization is complete, data in the target and source log streams may be different. Check back later in one hour.

Setting Cross-Account Ingestion
-------------------------------

If you choose cross-account ingestion as the log ingestion type, perform the following operations to configure the ingestion:

#. Log in to the management console and choose **Management & Deployment** > **Log Tank Service**.

#. Choose **Log Ingestion** > **Ingestion Center** in the navigation pane and click **Cross-Account Ingestion - Log Stream Mapping**.

   You can also choose **Log Ingestion** > **Ingestion Management** in the navigation pane and click **Ingest Log**. On the displayed page, click **Cross-Account Ingestion - Log Stream Mapping**.

#. Select an agency.

   Set parameters by referring to :ref:`Table 1 <lts_04_1112__en-us_topic_0000001294632105_table085665515403>` and click **Next: Log Stream Mapping**.

   .. _lts_04_1112__en-us_topic_0000001294632105_table085665515403:

   .. table:: **Table 1** Agency parameters

      +------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter              | Description                                                                                                                                                     |
      +========================+=================================================================================================================================================================+
      | Agency Name            | Enter the name of the agency created by the delegator. A delegator account can create an agency to delegate resource management permissions to another account. |
      +------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Delegator Account Name | Enter the delegator account name to verify the delegation.                                                                                                      |
      +------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Map log streams.

   On the **Log Stream Mapping** page, there are two ways to configure ingestion rules: automatic and manual configuration.

   -  **Automatic configuration**

      a. Click **Auto Configure**.

      b. On the displayed page, set the required parameters and click **OK**.

         .. table:: **Table 2** Parameters of automatic ingestion rule configuration

            +------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
            | Parameter                                                                                | Description                                                                                                                                                                                                                                     |
            +==========================================================================================+=================================================================================================================================================================================================================================================+
            | Rule Name Prefix                                                                         | Enter the rule name prefix. In automatic configuration, this prefix is used to generate multiple ingestion rules.                                                                                                                               |
            |                                                                                          |                                                                                                                                                                                                                                                 |
            |                                                                                          | Can contain only letters, digits, underscores (_), hyphens (-), and periods (.). The prefix cannot start with a period or underscore, or end with a period. If you do not specify a prefix, the default rule name prefix **rule** will be used. |
            +------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
            | Select the log groups or log streams that you want to ingest from the delegator account. | Up to 20 log groups or log streams can be selected.                                                                                                                                                                                             |
            +------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

         By default, the names of the target log groups and target log streams of the delegated account are the same as those of the source log groups and source log streams of the delegator account. You can also manually change the names of the target log groups and target log streams.

      c. Click **Preview**.

         #. There are two types of preview results:

            -  **A new target log stream will be created**: A target log group or log stream will be created in the delegated account.
            -  **An existing target log stream will be ingested**: The target log group or log stream already exists in the delegated account.

         #. Preview error messages are as follows:

            -  Source log stream *xxx* has been configured as the target log stream.
            -  Target log stream *xxx* has been configured as the source log stream.
            -  Target log stream *xxx* already exists in another log group.
            -  Target log stream *xxx* exists in different target log groups.
            -  Duplicate rule names.
            -  The source log stream *xxx* is already mapped.
            -  The number of log groups has reached the upper limit. Select an existing log group.

            If any of the preceding error messages is displayed, delete the corresponding ingestion rule of the log stream.

      d. After the preview is complete, click **Submit**.

   -  **Manual configuration**

      a. On the **Log Stream Mapping** page, click **Add Rule**. Set the rule by referring to :ref:`Table 3 <lts_04_1112__en-us_topic_0000001294632105_table9281534105611>`.

         .. _lts_04_1112__en-us_topic_0000001294632105_table9281534105611:

         .. table:: **Table 3** Parameters

            +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
            | Parameter             |                       | Description                                                                                                                                               |
            +=======================+=======================+===========================================================================================================================================================+
            | Rule Name             |                       | The default value is **rule\_**\ *xxx*. You can also specify a name as needed.                                                                            |
            |                       |                       |                                                                                                                                                           |
            |                       |                       | Can contain only letters, digits, underscores (_), hyphens (-), and periods (.). The name cannot start with a period or underscore, or end with a period. |
            +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
            | Delegator Account     | Source Log Group      | Log group of the delegator account. Select an existing log group.                                                                                         |
            +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
            |                       | Source Log Stream     | Log stream of the delegator account. Select an existing log stream.                                                                                       |
            +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
            | Delegated Account     | Target Log Group      | Log group of the delegator account. You can select an existing log group or enter a name to create one.                                                   |
            +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
            |                       | Target Log Stream     | Log stream of the delegated account. You can select an existing log stream or enter a name to create one.                                                 |
            +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+

      b. Click **Preview**.

         #. There are two types of preview results:

            -  **A new target log stream will be created**: A target log group or log stream will be created in the delegated account.
            -  **An existing target log stream will be ingested**: The target log group or log stream already exists in the delegated account.

         #. Preview error messages are as follows:

            -  Source log stream *xxx* has been configured as the target log stream.
            -  Target log stream *xxx* has been configured as the source log stream.
            -  Target log stream *xxx* already exists in another log group.
            -  Target log stream *xxx* exists in different target log groups.
            -  Duplicate rule names.
            -  The source log stream *xxx* is already mapped.
            -  The number of log groups has reached the upper limit. Select an existing log group.

            If any of the preceding error messages is displayed, delete the corresponding ingestion rule of the log stream.

      c. After the preview is complete, click **Submit** and wait until the log ingestion task is created.

#. Complete the ingestion configuration.

   After the configuration is complete, data will be synchronized within one hour. Please check back later.

   -  If multiple log streams are ingested, you can click **Back to Ingestion Configurations** to view the log ingestion list.
   -  If a single log stream is ingested, click **Back to Ingestion Configurations** to view the log ingestion list. Click **View Log Stream** to view details about the ingested log stream.
