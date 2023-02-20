##### Chapter 9-9
##### Backup and Recovery

<b><font size="5" color="#000080">Introduction</font></b><br>
<br>
The Backup and Recovery functionality of the HCL C API for Domino and Notes allows the media recovery of databases under Domino.  This API functionality covers capturing a full point-in-time backup of a database, archiving transaction log file extents, and finally recovering a database by applying its logged transactions to its recoverable backup file.  API applications which utilize this functionality must execute locally.<br>
<br>
<br>
<b><font size="5" color="#000080">Overview</font></b><br>
<br>
Domino has the ability to log transactions against one or more Domino databases (Release 5 and later).  If transaction logging is enabled on the server, all Domino R5 (and later) format databases are logged by default unless logging is disabled for the database by the administrator, or the database is not in the Domino or Notes data path.  Earlier database versions will not support transaction logging.  All logged database transactions go into a single 'transaction log', consisting of one or more files or extents.  Transaction logging may be of either circular style, linear style or archive style.  Transaction logging must be enabled in order to implement the recovery of databases via the API's Backup and Recovery  functionality.<br>
<br>
Recovery of a logged Domino database starts with the last full backup of the database and then utilizes the database backup functions described below.  The backup of a Domino database, which may later be used for media recovery, can be implemented if the transaction log files are available and the state of the database, with regards to the transaction log, has remained consistent.  The state of the database will change if: transaction logging is disabled then re-enabled for the server, transaction logging is disabled then re-enabled for the database, the database is compacted with any option other than the space recovery option, fixup is forced on the database, the database is recovered with the DBRECOVER_ZAP_ID option, the database is moved to another system then moved back, or the database is opened from a path that is not in the Domino or Notes data path.  Under any of these circumstances, a new backup of the database must be taken if the possibility of media recovery from the transaction log is desired.  Please refer to the Domino documentation for a complete description of transaction logging.<br>
<br>
The transaction log is uniquely identified by a log series identifier (LogID).  For an archive style transaction log, each log file has a sequence number unique to that log series.  The LogID and log sequence number will be provided to the backup and recovery application when a transaction log is archived and then used when requesting a specific archived transaction log.  All logged databases are stamped with the LogID for the logger that it was recorded by.  When a logged database is backed up it is also stamped with the log sequence number of the first transaction log it will record to.  Examination of a restored backup will provide both the LogID and the log sequence number to request when rolling forward.  A recovered database can have all updates through the end of the transaction log applied to it, or only updates completed prior to a specified point in time.<br>
<br>
<br>
<b><font size="5" color="#000080">Full Database Backup</font></b><br>
<br>
The Backup and Recovery functionality of the HCL C API for Domino and Notes allows an application to capture a full point-in-time backup of a Domino database.  When a backup is initiated, a transaction consistent image of the database is forced to disk which can then be copied to a backup file.  For the duration of the backup process, before-images of any bytes modified in the database by Domino are captured, so the backup file may be augmented or modified to be consistent with the database at the point-in-time the backup was initiated.  These recorded before-images will need to be applied to the backup file prior to it being recovered. <br>
<br>
A database backup and recovery application initiates a database backup with a call to NSFBackupStart.  This will force any pending I/O to disk and return a context block for use in subsequent calls.  Once a backup is initiated, the database should be copied to a backup file using whatever method the database backup and recovery application chooses, provided it does not require exclusive access to the file.  While the backup is in progress, before-image changes are accumulated.  Initially, this will be for the entire database, but if a sequential file copy is done for the backup, the range may be narrowed by calling NSFSetHighWaterMark to move the lower range up once a portion of the database has been copied.  When the raw file copy has completed, NSFBackupStop is called to stop recording change information for the database.  NSFBackupGetChangeInfoSize may then be called to get the total size in bytes of the change information.  If the backup file is to ever be recovered, this change information will need to be applied to it.  NSFBackupGetNextChangeInfo should be called to get the change information.  It may take several calls to get all of the change information. The order that this data is returned is the order that it needs to be presented in, when it is applied to the backup file.  When all of the change information has been retrieved, NSFBackupEnd is called to end the backup of the database.<br>
<br>
NSFBackupStartApplyChangeInfo is called to initiate application of the change information to the backup file.  The change information is then passed in by one or more calls to NSFBackupApplyNextChangeInfo.  The data passed in for application must be in the same order as it was returned from NSFBackupGetNextChangeInfo.  Once all of the change information has been passed in, NSFBackupEndApplyChangeInfo is called to clean up any allocated resources.<br>
<br>
Important Note:  The resulting backup file will be a duplicate of the database that it was derived from, with the addition of certain recovery enabling criteria.  If this backup file is opened by Domino or Notes software prior to its recovery, the recovery criteria is removed and the file is no longer a recoverable backup.  Care should be taken to ensure the maintenance of recoverable database backup files.<br>
<br>
The following API database backup functions are provided:<br>

<ul>
<ul type="disc">
<li>NSFBackupStart - Minimize activity in the database and return a backup context block to the caller.  After this is called, the caller is expected to begin doing raw file system I/O to create the backup the file.  NSF will record the before-images of any byte ranges to which writes are done, for the duration of the backup, and provide access to the before-images so the database backup and recovery application can record those, in addition to the raw I/O copy of the database.
<li>NSFBackupStop - Called to indicate to NSF that the raw backup of the database has completed, and that it should stop recording change information for the database.  There may be a set of to-be-processed changes at this point.
<li>NSFBackupEnd - Terminate backup of the database.  At this point, assuming the backup was successful, all recorded updates on the database should have been processed.  The backup context is deleted at this point.
<li>NSFBackupSetHighWaterMark - This function indicates to NSF that the database has been recorded, at least up to a given byte offset N, so that changes done to the database below the high water mark need not be recorded.  Though optional, this function has very low overhead and it is recommended that it be used frequently to avoid unnecessary system overhead in recording changes for bytes already recorded by the database backup and recovery application.
<li>NSFBackupGetChangeInfoSize - Returns the total size in bytes of the change information for the backup file.
<li>NSFBackupGetNextChangeInfo - Returns the next portion of the change information for the backup file. The order of the returned data must be maintained when it is passed in for application to the backup file.
<li>NSFBackupStartApplyChangeInfo - Initiates application of change information to a backup file taken during a backup operation. 
<li>NSFBackupApplyNextChangeInfo - Takes and applies the next portion of the change information.
<li>NSFBackupEndApplyChangeInfo - End the application of change information to a backup file.
<li>NSFDbGetLogInfo - Check if a database is being logged.</ul>
</ul>
<br>
Please refer to the <i>HCL C API Reference</i> for a more detailed description of these functions.<br>
<br>
<br>
<b><font size="5" color="#000080">Archiving Logs</font></b><br>
<br>
The Backup and Recovery functionality also allows an application to detect when a Domino logger, configured for archive style transaction logging, has file extents to be archived, and to notify the logger when a transaction log file extent has been successfully archived.  The Domino logger, the archived transaction logs, and the database backup files are all related by a unique log series identifier (LogID).  Within a log series, an individual transaction log is identified by a unique log sequence number.  The LogID and log sequence number are provided when a transaction log file is archived.  These will be used in all future calls to identify a specific log series, and within it, a specific transaction log.  <br>
<br>
<br>
The database backup and recovery application queries whether an archive style transaction log is ready to be archived with a call to either NSFGetFirstLogToArchive or NSFGetNextLogToArchive.  NSFGetFirstLogToArchive will always return information for the first transaction log, if there is one, in the list of logs waiting to be archived.  NSFGetNextLogToArchive will return information for the next log in the list, or for the first log in the list, if this is the first call made.  It isn't necessary to wait for one transaction log to be archived before initiating the archiving  of another.  The query will return a path to the transaction log as well as the LogID and log sequence number for that log.  The archived transaction logs should be copied to an archive store using whatever method the database backup and recovery application chooses.  Once a transaction log is successfully archived, NSFDoneArchivingLog is called to let the logger know that it may be recycled.  It is important that the database backup and recovery application archive transaction logs often enough so a backlog does not prevent the logger from being able to continue.<br>
<br>
It is possible for a transaction log that was archived to be returned as waiting to be archived, if a prior invocation of the logger did not recycle it before terminating.  The transaction log will not have changed and does not need to be re-archived, but NSFDoneArchivingLog should be called for it.<br>
<br>
The following API transaction log archive functions are provided:<br>

<ul>
<ul type="disc">
<li>NSFGetTransLogStyle - Check to determine if 'CIRCULAR', 'LINEAR' or 'ARCHIVE' style transaction logging is being performed.
<li>NSFBeginArchivingLogs - Initiate the archiving of transaction logs.
<li>NSFEndArchivingLogs - Terminate the archiving of transaction logs.
<li>NSFGetFirstLogToArchive - Check from the start of the list to determine if a transaction log is waiting to be archived.  Return the path, LogID and log sequence number, to uniquely identify the transaction log.
<li>NSFGetNextLogToArchive - Check to determine if a transaction log is waiting to be archived.  Return the path, LogID and log sequence number, to uniquely identify the transaction log.
<li>NSFDoneArchivingLog - Marks the specified transaction log as archived.
<li>NSFIsNewBackupNeeded - Determine the state of the database or database backup file with respect to the current log state.  </ul>
</ul>
<br>
Please refer to the<i> HCL C API Reference</i> for a more detailed description of these functions.<br>
<br>
<br>
<b><font size="5" color="#000080">Incremental Archiving of Logs</font></b><br>
<br>
It is possible to archive a log extent that has not reached it's maximum size and therefore not been marked by Domino's Recovery Manager as &quot;ready to be archived&quot;.  This is accomplished using the same logic employed when archiving a &quot;full&quot;extent, and addressing an additional issue.<br>
Since Domino's Recovery Manager will still need to access the log extent being incrementally archived, it is essential that &quot;shared access&quot; to the file is maintained throughout the archive process and, since the extent has not reached its full capacity and will need to be archived again in the future, NSFDoneArchivingLog should not be called to mark the partial extent &quot;as archived&quot;. <br>
<br>
<br>
<b><font size="5" color="#000080">Media Recovery</font></b><br>
<br>
The Backup and Recovery functionality also allows an application to recover a database from its backup file, and for logged databases to have the logged transactions applied to its backup file.  For clarity, we will use the term &quot;recover&quot; to describe the act of applying the logged transactions to the database backup file, and the term &quot;restore&quot; to encompass the process to replace the existing database with the recovered backup file.   To replace an existing database with its backup file, activity against the database needs to be stopped and the database deleted.  Once that is done, a copy of the database's backup file should be placed in the Domino data directory where it can be recovered and restored to active use.  Backups of logged databases can then be rolled forward.  Backups of unlogged databases can just be brought online. <br>
<br>
For each database that is to be replaced, NSFTakeDatabaseOffline needs to be called.  This will make sure the database is not being accessed, close the database, and can delete the database.  If the database is being accessed it cannot be taken offline.  In this case, a wait period can be specified to retry taking it offline.  If it cannot be taken offline in that period then ERR_DBINUSE will be returned as the status, indicating that another process is accessing the database.  The administrator may intervene with the blocking processes or wait. <br>
<br>
A backup file may be recovered as a &quot;new&quot; database file.  In this case, during the recovery the database instance id (DBIID) is refreshed and the existing database does not need to be taken offline.  Because the recovered file will be a &quot;new&quot; database, logged updates to the existing database, after media recovery starts, will not be applied to this new database.  The DBIID of the new database must be refreshed as Domino does not allow active databases to have duplicate DBIIDs.<br>
<br>
NSFRecoverDatabases (or NSFRecoverDatabasesWithCallback)  is called with the list of logged databases to be rolled forward, and a callback routine for accessing archived transaction logs.  The databases will be examined and the first required transaction log determined. The callback routine will be passed the LogID and log sequence number to identify the desired archived transaction logs and a full path to where the log should be put.  A restored or recovered database is brought on-line with a call to NSFBringDatabaseOnline.<br>
<br>
The following API database recovery functions are provided:<br>

<ul>
<ul type="disc">
<li>NSFTakeDatabaseOffline - Stop access to a database and delete the database so it can be recovered.
<li>NSFRecoverDatabases - Perform media recovery on the specified databases.
<li>NSFRecoverDatabasesWithCallback - Perform media recovery on the specified databases and allow the use of a callback function.
<li>NSFBringDatabaseOnline - Bring a database online.<br>
</ul>
</ul>
Please refer to the <i>HCL C API Reference</i> database for a more detailed description of these functions.<br>
<br>
<br>
<b><font size="5" color="#000080">DB2 Specific Backup Functions</font></b><br>
<br>
Since release 7.0, Domino has the capability to access and store information in DB2 format.<br>
<br>
The following API database DB2 backup functions are provided:
<ul>
<ul>
<li type="disc">NSFDB2FastMove - Efficiently copies or moves an NSFDB2 database to a new schema / tablespace, and appropriately &quot;reconnects&quot; the Domino data contained in both the original DB2 schema  and the target schema, depending on whether the operation was a copy or a move.
<li type="disc">NDB2GetDbInfoValidity - Returns the schema  and table space that Domino believes the specified NSFDB2 database exists in.
<li type="disc">NSFDB2GetInfo -  Retrieves the DB2-related information about a Domino database.
<li type="disc">NSFDB2GetServerInfo - Retrieves the DB2-related information about a Domino server.
<li type="disc">NSFDbIsDB2 - Determines whether a Domino database is a DB2 database or an NSF database.
<li type="disc">NSFDB2ListNSFDB2Databases - Provides a list of all NSFDB2 databases.
<li type="disc">NSFDB2ReconnectNotesDatabase - Reconnects a DB2 schema/tablespace to Domino after a DB2 restore/rollforward operation.
<li type="disc">NSFDB2RegenerateLinks - Verifies that all link files exist on the Domino server's data directory after a DB2 database restore.</ul>
</ul>
<br>
Please refer to the <i>HCL C API Reference</i> database for a more detailed description of these functions.<br>
<b><font color="#0000FF"><br>
</font></b><br>
<b><font size="5" color="#000080">Disaster Recovery with Archive Style Logging</font></b><br>
<br>
In the event of the catastrophic loss of the active logger files, it will be possible to recover database backups to the last committed transaction in the archived transaction logs if the administrator has taken care to preserve the following, prior to any data loss: <br>

<ul type="disc">
<li>An up-to-date NOTES.INI file from the affected Domino server which has transactional logging enabled.
<li>A set of recoverable database backup files.
<li>The archived log extents.</ul>
<br>
With the components listed above available, the disaster recovery procedures consist of the following:<br>
<br>
<b>Disaster recovery using TRANSLOG_Recreate_Logctrl=1(ARCHIVE style logging only)</b><br>

<ol type="1">
<li><b>Restore the Domino server</b> - Depending on the extent of the data loss it may be necessary, and advisable, to install a new Domino server.  Be sure that the new installation is configured in the same manner as the damaged one (i.e. same directory structure/location and logdir path).  Install the NOTES.INI file that was preserved prior to the data loss.  <i>DO NOT LAUNCH THE NEW SERVER</i>.
<li><b>Prepare the data directory</b> - Retrieve database backup files of all required databases into the data directory (including NAB, unless a regular up-to-date copy is available from another server). 
<li><b>Prepare the log directory</b> - Make sure that the &quot;logdir&quot;, as it is defined in the NOTES.INI file, exists and that no old files are present therein.  If a transactional log control file remains from a previous installation it must be removed for the disaster recovery procedure to complete successfully.  Retrieve the archived log extents, that were created using the Archive functions previously described in this chapter, the into &quot;logdir&quot; (you will only be able to recover the backup files up to the last committed transaction in the most recent archived transaction log extent). 
<li><b>Facilitate creation of new control file</b> - Set the parameter TRANSLOG_Recreate_Logctrl=1 in the NOTES.INI file.
<li><b>Perform Media Recovery</b> - Using the Media Recovery functions previously described in this chapter, restore all database backup files that you desire to have rolled up to the latest state from the archived log extents.<b><font color="#0000FF">  </font></b>Upon the first Media Recovery call, the log control file will be rebuilt and the NOTES.INI setting for TRANSLOG_Recreate_Logctrl will be set to 0 automatically.
<li><b>Launch the Domino server</b> - With the disaster recovery complete, it is now safe to start the Domino server and execute server tasks and functions.
<li><b>Create new database backup files</b> - With the successful completion of the disaster recovery process and launching of the new Domino server, new database backup files should be created and secured to avoid any future loss of data.</ol>
<br>
<br>
<b><font size="5" color="#000080">Disaster Recover with Circular or Linear Style Logging</font></b><br>
<br>
In the event of the catastrophic loss of the active logger files, it will only be possible to recover the databases active at the time of the failure, by replacing them with their latest backup files, and use the regular version of the inactive databases (if the data disk is still available).  The procedure consists of setting the TRANSLOG_Path to point to a valid (empty) directory and restarting the server.  Upon restart, the server will display a list of databases that were corrupted at the time of failure, but cannot be recovered due to the missing transaction log.  You must then replace these corrupted databases with their latest corresponding database backup files and restart the server again.  Unpredictable results for logged databases can occur if you choose to run fixup with the -j switch on the corrupt databases.  Please refer to the Domino documentation for a complete description of transaction logging.<br>
<br>
<br>
<b><font size="5" color="#000080">Media Recover - Other Considerations</font></b><br>
<br>
<b>Media recovery only using TRANSLOG_MEDIAONLY=1</b><br>
<br>
The recovery of database backups may be time consuming and may adversely impact the performance of a Domino server.  The recovery of nonessential databases may be done on alternative machines or partitions and thus not affect the production server performance.  This is provided for by using the Media Recovery functions previously described in this chapter and setting the NOTES.INI parameter TRANSLOG_MEDIAONLY=1.<br>

<ol type="1">
<li><b>Prepare Domino server</b> -  If not already available, install the Domino server on an alternate machine or partition.  <i>DO NOT LAUNCH THE SERVER</i>.
<li><b>Prepare the data directory</b> - Retrieve database backup files of all required databases into the data directory. 
<li><b>Prepare the log directory</b> - Make sure that the &quot;logdir&quot;, as it is defined in the NOTES.INI file, exists and that no old files are present therein.  If a transactional log control file remains from a previous installation it must be removed for the disaster recovery procedure to complete successfully.  Retrieve the archived log extents, that were created using the Archive functions previously described in this chapter, into &quot;logdir&quot; (you will only be able to recover the backup files up to the last committed transaction in the most recent archived transaction log extent). 
<li><b>Prepare NOTES.INI file</b><b><font color="#0000FF"> </font></b>- Include proper TRANSLOG_Path and the parameter TRANSLOG_MEDIAONLY=1. 
<li><b>Perform Media Recovery</b> - Using the Media Recovery functions previously described in this chapter, restore all desired database backup files.  Upon the first Media Recovery call, the log control file will be rebuilt automatically.
<li><b>Replace databases</b> - Move the recovered database(s) back to the production server.</ol>

---
