:original_name: lts_05_0001.html

.. _lts_05_0001:

Querying Real-Time LTS Traces
=============================

Overview
--------

CTS can record operations (traces) related to LTS for query, audit, and backtracking.

After you enable CTS, the system starts to record LTS operations. CTS stores operation records from the last seven days.

Enabling CTS
------------

To enable CTS, see "Enabling CTS" in the *Cloud Trace Service User Guide*.

After CTS is enabled, if you want to view LTS traces, see "Querying Real-Time Traces" in the *Cloud Trace Service User Guide*.

LTS Operations That Can Be Recorded by CTS
------------------------------------------

.. table:: **Table 1** LTS operations that can be recorded by CTS

   +------------------------------------------------------+------------------------------+-------------------------------+
   | Operation                                            | Resource Type                | Trace Name                    |
   +======================================================+==============================+===============================+
   | Creating a log group                                 | group                        | createLogGroup                |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Modifying a log group                                | group                        | updateLogGroup                |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Deleting a log group                                 | group                        | deleteLogGroup                |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Creating a log stream                                | topic                        | createLogStream               |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Modifying a log stream                               | topic                        | updateLogStream               |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Deleting a log stream                                | topic                        | deleteLogStream               |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Deleting a log from favorites                        | filter                       | deleteFavorite                |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Creating an OBS log transfer task                    | als                          | addLogPailToOBS               |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Modifying an OBS log transfer task                   | als                          | updateLogPailToOBS            |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Deleting an OBS log transfer task                    | als                          | deleteLogPailToOBS            |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Creating a log transfer task                         | transfer                     | createLogTransfer             |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Modifying a log transfer task                        | transfer                     | updateLogTransfer             |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Deleting a log transfer task                         | transfer                     | deleteLogTransfer             |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Creating quick search criteria                       | searchCriteria               | createLogSearchCriteria       |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Modifying quick search criteria                      | searchCriteria               | updateLogSearchCriteria       |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Deleting quick search criteria                       | searchCriteria               | deleteLogSearchCriteria       |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Adding a collection path                             | LogAgent                     | createLogAgent                |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Modifying a collection path                          | LogAgent                     | updateLogAgent                |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Deleting a collection path                           | LogAgent                     | deleteLogAgent                |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Creating a cross-account log ingestion configuration | ltsLogAccessConfig           | CreateLtsLogAccessConfig      |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Creating a log ingestion configuration               | ltsLogAccessConfig           | createAccessConfig            |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Modifying a log ingestion configuration              | ltsLogAccessConfig           | updateAccessConfig            |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Deleting a log ingestion configuration               | ltsLogAccessConfig           | deleteAccessConfig            |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Creating a notification template                     | NotificationTemplate         | createNotificationTemplate    |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Modifying a notification template                    | NotificationTemplate         | updateNotificationTemplate    |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Deleting a notification template                     | NotificationTemplate         | deleteNotificationTemplate    |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Creating a structuring template                      | structLogConfig              | createLogStreamStructConfig   |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Modifying a structuring template                     | structLogConfig              | updateLogStreamStructConfig   |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Deleting a structuring template                      | structLogConfig              | deleteLogStreamStructConfig   |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Adding or updating index settings                    | filedIndex                   | createOrUpdateFiledIndex      |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Creating a quick analysis task                       | wordFreqConfig               | updateWordFreqConfig          |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Creating a structuring rule                          | structurization              | addStructurization            |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Deleting a structuring rule                          | structurization              | deleteStructurization         |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Enabling log collection beyond free quota            | LogCollectionSwitchOperation | LogCollectionSwitchOperation  |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Disabling log collection beyond free quota           | LogCollectionSwitchOperation | LogCollectionSwitchOperation  |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Querying alarm rules in batches                      | alarm                        | batchQueryAlarmList           |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Modifying the status of an alarm rule                | KeywordsAlarm                | updateKeywordsAlarmRuleStatus |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Creating a keyword alarm rule                        | KeywordsAlarm                | createKeywordsAlarmRule       |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Deleting a keyword alarm rule                        | KeywordsAlarm                | deleteKeywordsAlarmRule       |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Modifying a keyword alarm rule                       | KeywordsAlarm                | updateKeywordsAlarmRule       |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Adding a log path collection rule                    | logPathCollectionType        | createLogPathCollection       |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Modifying a log path collection rule                 | logPathCollectionType        | updateLogPathCollection       |
   +------------------------------------------------------+------------------------------+-------------------------------+
   | Deleting a log path collection rule                  | logPathCollectionType        | deleteLogPathCollection       |
   +------------------------------------------------------+------------------------------+-------------------------------+
