##### Chapter 14-1
##### Anatomy of a Note ID

This chapter describes note IDs in detail and explains how different Domino or Notes tasks (replicator and so on) use the components of a note ID and how API programs can use them.<br>
<br>
The parts of a note ID are:
<ul>
<ul></ul>

<li type="disc">UNID (Universal Note ID) - Identifies all the copies of a note, regardless of location or time. In other words, every replica of a note has the same UNID, and the UNID does not change when a note is modified.
<li type="disc">OID (Originator ID) - Identifies a particular revision of a note, regardless of location. In other words, every replica of a note has the same OID, but the OID changes when the note is modified.
<li type="disc">GNID (Global Note ID) - Identifies a particular note in a particular database. The GNID does not change as the note is modified. The GNIDs of replica copies of a note will probably be different, since the various copies will occupy different positions in their databases.
<li type="disc">NID (Note ID) - Identifies a particular note in a given database. The NID does not contain information about the database being referred to, and it does not change when the note is modified.
<li type="disc">IID (Instance ID) - Identifies a particular revision of a note in a given database. The IID does not contain information about the database being referred to. The IID changes when the note is modified.
<li type="disc">GIID (Global Instance ID) - Identifies a particular revision of a note in a particular database. The GIID contains information about the database being referred to. The GIID changes when the note is modified.</ul>
<br>
You can examine the ID information for a particular document from the Notes user interface. Select the document in a view or open it, then select File - Document Properties. Notes displays the &quot;Document Properties&quot; infobox. On the information page, Notes displays the header data associated with this document, including the dates and times the document was created and modified and the note ID information.  <br>
<br>
The note ID information is displayed by Notes as three lines consisting of key characters and hex digits. For a typical data note, it looks like this:
<ul><br>
<font face="System Proportional">ID: OF0000039D:3836C29F-ON85255DC9:0056FB94</font><br>
<font face="System Proportional">    SD00255DF4:0057B8FA-SN00000003</font><br>
<font face="System Proportional">    DB85255CD9:00567287-NT0000C092</font></ul>
<br>
These three lines contain the Originator ID (OID), the Universal Note ID (UNID), the Global Note ID (GID), and the Note ID (NID) of the open or selected document.<br>
<br>
<br>
<b><font size="5" color="#000080">The Universal Note ID (UNID) and the Originator ID (OID)</font></b><br>
<br>
The first two lines of the ID constitute the complete Originator ID for the note.  In turn, the Originator ID consists of the Universal Note ID (the whole first line) plus the sequence number and the sequence time (the second line)<font color="#FF0000">:</font><br>
<br>

<ul><u><font face="System Proportional">Originator ID (OID) =</font></u><br>
<font face="System Proportional">ID: OF</font><u><font face="System Proportional">0000039D:3836C29F</font></u><font face="System Proportional">-ON</font><u><font face="System Proportional">85255DC9:0056FB94</font></u><br>
<font face="System Proportional">    SD</font><u><font face="System Proportional">00255DF4:0057B8FA</font></u><font face="System Proportional">-SN</font><u><font face="System Proportional">00000003</font></u><br>
<font face="System Proportional">    DB85255CD9:00567287-NT0000C092</font></ul>
<br>

<ul><u><font face="System Proportional">Universal Note ID (UNID) =</font></u><br>
<font face="System Proportional">ID: OF</font><u><font face="System Proportional">0000039D:3836C29F</font></u><font face="System Proportional">-ON</font><u><font face="System Proportional">85255DC9:0056FB94</font></u><br>
<font face="System Proportional">    SD00255DF4:0057B8FA-SN00000003</font><br>
<font face="System Proportional">    DB85255CD9:00567287-NT0000C092</font></ul>
<br>

<ul><u><font face="System Proportional">Sequence Time =</font></u><br>
<font face="System Proportional">ID: OF0000039D:3836C29F-ON85255DC9:0056FB94</font><br>
<font face="System Proportional">    SD</font><u><font face="System Proportional">00255DF4:0057B8FA</font></u><font face="System Proportional">-SN00000003</font><br>
<font face="System Proportional">    DB85255CD9:00567287-NT0000C092</font></ul>
<br>

<ul><u><font face="System Proportional">Sequence Number =</font></u><br>
<font face="System Proportional">ID: OF0000039D:3836C29F-ON85255DC9:0056FB94</font><br>
<font face="System Proportional">    SD00255DF4:0057B8FA-SN</font><u><font face="System Proportional">00000003</font></u><br>
<font face="System Proportional">    DB85255CD9:00567287-NT0000C092</font></ul>
<br>
<br>
The first two parts of the Originator ID (and the Universal Note ID) consist of a File member and a Note member. The first line of the ID information in the  Document Properties infobox consists of the letters &quot;OF&quot; (&quot;Originator ID - File&quot;), followed by sixteen hex digits, followed by a hyphen, followed by the letters &quot;ON&quot; (&quot;Originator ID - Note&quot;), followed by sixteen more hex digits. The sixteen hex digits after the &quot;OF&quot; and before the hyphen constitute the File member of the OID. The sixteen hex digits after the hyphen and the &quot;ON&quot; constitute the Note member of the OID. <br>

<ul><u><font face="System Proportional">OID.File =</font></u><br>
<font face="System Proportional">ID: OF</font><u><font face="System Proportional">0000039D:3836C29F</font></u><font face="System Proportional">-ON85255DC9:0056FB94</font><br>
<font face="System Proportional">    SD00255DF4:0057B8FA-SN00000003</font><br>
<font face="System Proportional">    DB85255CD9:00567287-NT0000C092</font></ul>
<br>

<ul><u><font face="System Proportional">OID.Note =</font></u><br>
<font face="System Proportional">ID: OF0000039D:3836C29F-ON</font><u><font face="System Proportional">85255DC9:0056FB94</font></u><br>
<font face="System Proportional">    SD00255DF4:0057B8FA-SN00000003</font><br>
<font face="System Proportional">    DB85255CD9:00567287-NT0000C092</font></ul>
<br>
<br>
The header file nsfdata.h contains the following definition of the ORIGINATORID data structure and the UNIVERSALNOTEID data structure:<br>
<br>
<br>
<tt><font size="2">typedef struct {<br>
 &nbsp; &nbsp; &nbsp;DBID File; &nbsp; &nbsp; &nbsp; &nbsp;/* Unique (random) number */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* (Even though this field is called &quot;File,&quot; */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* &nbsp;it doesn't have anything to do with the file!) */<br>
 &nbsp; &nbsp; &nbsp;TIMEDATE Note; &nbsp; &nbsp;/* Original Note Creation time/date */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* (THE ABOVE 2 FIELDS MUST BE FIRST - UNID */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* &nbsp;COPIED FROM HERE ASSUMED AT OFFSET 0) */<br>
 &nbsp; &nbsp; &nbsp;DWORD Sequence; &nbsp; /* LOW ORDER: sequence number, 1 for first version */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* HIGH ORDER WORD: flags, as above */<br>
 &nbsp; &nbsp; &nbsp;TIMEDATE SequenceTime;/* time/date when sequence number was bumped */<br>
} ORIGINATORID;</font></tt><br>
<br>
<tt><font size="2">#define OID ORIGINATORID</font></tt><br>
<br>
<tt>typedef struct {<br>
 &nbsp; &nbsp; &nbsp;DBID File; &nbsp; &nbsp; &nbsp; &nbsp;/* Unique (random) number */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* (Even though this field is called &quot;File,&quot; */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* &nbsp;it doesn't have anything to do with the file!) */<br>
 &nbsp; &nbsp; &nbsp;TIMEDATE Note; &nbsp; &nbsp;/* Original Note Creation time/date */<br>
} UNIVERSALNOTEID;</tt><br>
<br>
<tt><font size="2">#define UNID UNIVERSALNOTEID</font></tt><br>
<br>
<br>
The Originator ID (OID) for a note identifies all replica copies of the same note. The OID is composed of two parts: the Universal Note ID (UNID) and the sequence number and sequence time. The UNID universally identifies all instances of the same note. Taken together, the sequence number and the sequence time distinguish different revisions of the same note from one another.  <br>
<br>
The Universal note ID (UNID) identifies a note across all servers. However, the UNID lacks the information necessary to directly access the note in a given database. The UNID is used to reference a specific note from another note. The &quot;$REF&quot; (FIELD_LINK) field of a response note contains the UNID of its parent. Similarly, DocLinks(see the NOTELINK structure in nsfdata.h) contains the UNID of the linked-to note, the UNID of the linked-to note view, plus the ID of the database where the linked-to note can be found (ViewLinks contain the same information except the linked-to note structure is set to all zeros and DatabaseLinks zero out the linked-to note and view structures.)  The important characteristic of the UNID is that it continues to identify a note even after the note is updated.<br>
<br>
<br>
<b><font size="4" color="#000080">The UNID, the OID, and the Replicator</font></b><br>
<br>
The Universal Note ID (the first half of the Originator ID) uniquely identifies all versions and all copies of the same note. Two notes are replica copies of each other if they share the same UNID.  Therefore, different versions and all replica copies of the same note have the same UNID. A corollary of this rule is that one database must not contain two notes with the same UNID. If the replicator finds two notes with the same UNID in the same database, it generates an error message in the log and does not replicate the document.<br>
<br>
The full Originator ID, on the other hand, uniquely identifies one particular version of a note. In other words, all replica copies of the same version of a note have the same OID. However, a modified version of a replica copy of a particular note will have a different OID, because Domino and Notes increment the sequence number when a note is edited and also sets the sequence time to the timedate when the sequence number was incremented. Therefore, when one replica copy of a note remains unchanged but another copy is edited and modified, the UNIDs of the two notes remain the same but the sequence number and sequence times (and therefore the OIDs) are different.<br>
<br>
The Domino replicator uses the UNID to match the notes in one database with their respective replica copies in other databases. For example, if database A is replicating with database B, and database A contains a note with a particular UNID but database B does not, the replicator creates a copy of that note and add it to database B.  <br>
<br>
If database A contains a note with a particular UNID and database B contains a note with the same UNID, the replicator concludes that these two notes are replica copies of one another. In this case, the replicator goes on to examine the sequence number and sequence time of the two notes. If the sequence number and sequence time are the same for both notes, then the replicator concludes that the two notes are up to date with one another, and no action is required. On the other hand, if either the sequence number or the sequence time -- or both -- differ between two notes, the replicator must decide which one is more recent and update the older note with the most recent version.<br>
<br>
If one note has been updated but the other note has not, the sequence number of the first note will be greater than that of the second. The replicator handles this case by overwriting the second note with the first, bringing the two databases into synchronization.<br>
<br>
<b><font color="#000080">Replication Conflicts</font></b><br>
<br>
Replication conflicts arise from concurrent edits of the same note. If a user updates a note in database A and, before the change replicates to database B, another user updates the replica copy of that note in database B, the two notes have the same sequence number but different sequence times. In this case, the replicator generates a replication conflict because this represents a concurrent edit of the same note. <br>
<br>
The replicator handles replication conflicts by generating a replica conflict document. The document with the later sequence time becomes the conflict winner and the document with the earlier sequence time becomes the conflict loser. The conflict winner is copied to the database containing the loser, and the conflict loser is turned into a response document to the winner.<br>
<br>
The replicator generates the conflict loser (black diamond) document in the database initially holding the document with the earlier sequence time. The replicator copies the winning document from the winning database into the losing database. This winning document keeps its OID intact.  Then the replicator turns the losing document into a new document by generating a distinct OID and adding the special item &quot;$Conflict&quot; (VIEW_CONFLICT_ITEM) to the document. This $Conflict item causes a black diamond to appear in the left-hand margin of any view that displays the conflict loser. The replicator also turns the losing document into a response document by adding to it a $REF item that contains the UNID of the winning document.<br>
<br>
NOTE: The conflict loser (black diamond document) may not always appear on both servers immediately after replication completes. When the server holding the document that will be the winner initiates the replication, the conflict loser does not appear on the winning server immediately after replication, but does appear on the losing server. This happens because the replicator generates the conflict loser (black diamond document) only on the server initially holding the losing document. <br>
<br>
Specifically, when server B initiates replication with server A, B first pulls changes from A, and then A pulls changes from B. When B pulls from A, B sees the conflicting document on A, determines that B's version is the winner, and does not bring the conflicting document over from A to B. The justification for this is that B already has the winner, so B does not need to bring over the loser. Then A pulls from B, sees the conflicting document on B, and determines that B's version is the winner. Therefore A makes its own version into a replica conflict loser (black diamond) document and brings B's version over to A as the replica conflict winner. This satisfies the requirement that when replication is complete, both copies of the database present the same version of the document as the most up-to-date (winning) version of the document. However, the conflict loser (black diamond) does not yet appear on B. The next time B replicates with A the replica conflict loser (black diamond) document will come back to B and both copies of the database will be synchronized.<br>
<br>
<br>
<b><font size="4" color="#000080">The OID and the API</font></b><br>
<br>
API programs use NSFNoteGetInfo to obtain the various components of the Originator ID, specifying the _NOTE_OID info flag. For example:<br>
<br>
<tt><font size="2">&nbsp; &nbsp; ORIGINATORID &nbsp; &nbsp;NoteOID;<br>
</font></tt><br>
<tt><font size="2">&nbsp;	/*<br>
 &nbsp; &nbsp; * Get the OID from the note AFTER it has been updated<br>
 &nbsp; &nbsp; */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; NSFNoteGetInfo (hNote, _NOTE_OID, &amp;NoteOID);</font></tt><br>
<br>
<br>
NSFNoteUpdate causes Domino and Notes to change the sequence number and sequence time of the note being updated. Therefore, API programs must pay particular attention to the order in which they call NSFNoteUpdate and NSFNoteGetInfo when obtaining the OID information for a note.  <br>
<br>
Specifically, using NSFNoteCreate to create a new note yields a note handle, but until this note has been stored in the database (using NSFNoteUpdate), NSFNoteGetInfo does not return a valid OID.  However, since the UNID has been assigned at this stage, API programs can parse the returned value from the NSFNoteGetInfo to retrieve the UNID of this newly created note.<br>
<br>
<br>
<br>
<b><font size="4" color="#000080">UNID.File</font></b><br>
<br>
The File member of the OID (and UNID) contains a number derived in different ways depending on the release of Domino or Notes. Pre- 2.1 versions of Notes set the File member to the creation timedate of the NSF file in which the note is created. Notes 2.1 sets the File member to a user-unique identifier, derived partly from information in the ID of the user creating the note and partly from the database in which the note is created. Notes 3.0 and later releases of Domino and Notes sets the File member to a random number generated when the note is created.<br>
<br>
<br>
<b><font size="4" color="#000080">UNID.Note</font></b><br>
<br>
The Note member of the OID (and UNID) is the timedate when the note was created.  (For details on the TIMEDATE structure, please see the Appendix chapter &quot;Data Types&quot;.)<br>
<br>
<br>
<b><font size="5" color="#000080">Global Note ID (GNID) and NOTEID (NID)</font></b><br>
<br>
The Global Note ID (GNID) is composed of two parts: the Database ID and the Note ID (NID).  Since the GNID identifies both the database and the note in the database, it uniquely identifies a particular copy of a note across all databases. <br>
<br>
The GNID appears in the bottom line of the ID information displayed by the Design - Document Properties infobox. The first part of the GNID corresponds to the File member of the  GLOBALNOTEID structure. The second part corresponds to the NoteID member. <br>
<br>

<ul><u><font face="System Proportional">Global Note ID (GNID) =</font></u><br>
<font face="System Proportional">ID: OF0000039D:3836C29F-ON85255DC9:0056FB94</font><br>
<font face="System Proportional">    SD00255DF4:0057B8FA-SN00000003</font><br>
<font face="System Proportional">    DB</font><u><font face="System Proportional">85255CD9:00567287</font></u><font face="System Proportional">-NT</font><u><font face="System Proportional">0000C092</font></u></ul>
<br>

<ul><u><font face="System Proportional">Database ID (GNID.File) =</font></u><br>
<font face="System Proportional">ID: OF0000039D:3836C29F-ON85255DC9:0056FB94</font><br>
<font face="System Proportional">    SD00255DF4:0057B8FA-SN00000003</font><br>
<font face="System Proportional">    DB</font><u><font face="System Proportional">85255CD9:00567287</font></u><font face="System Proportional">-NT0000C092</font><br>
<br>
<u><font face="System Proportional">Note ID (GNID.NoteID) =</font></u><br>
<font face="System Proportional">ID: OF0000039D:3836C29F-ON85255DC9:0056FB94</font><br>
<font face="System Proportional">    SD00255DF4:0057B8FA-SN00000003</font><br>
<font face="System Proportional">    DB85255CD9:00567287-NT</font><u><font face="System Proportional">0000C092</font></u></ul>
<br>
<br>
The third line of ID information in the Design - Document Properties infobox consists of the letters &quot;DB&quot; (which stands for &quot;Data Base&quot;), followed by sixteen hex digits, followed by a hyphen, followed by the letters &quot;NT&quot; (&quot;NoTe&quot;), followed by eight more hex digits. The sixteen hex digits after the &quot;DB&quot; and before the hyphen constitute the File member of the GNID. The eight hex digits after the &quot;NT&quot; constitute the Note ID member of the GNID. <br>
<br>
<br>
<b><font size="4" color="#000080">Global Note ID (GNID)</font></b><br>
<br>
Unlike the OID, the GNID does not distinguish between different versions of the same note.  Since the NoteID field is relative to the file that contains the note, the GNIDs of replica notes will most likely be different.<br>
<br>
The Database ID (the File member of the GNID) contains the replica ID of the database. The API header file nsfdata.h defines the DBID data structure as a TIMEDATE:<br>
<br>
<tt><font size="2">#define DBID TIMEDATE</font></tt><br>
<br>
The fourth line in the info box for the note contains the DBID not the Replica ID.<br>
The info box for the db displays the DBID as Created, you need a tool like notespeek or dumpnsf to see it in hex.<br>
<br>
The DBID is only equal to ReplicaID when the db is first created, any replicas gets a different DBID.<br>
All replicas of a db have the same ReplicaID but they should have different DBIDs.<br>
<br>
When the first replica of a db is created, the DBID and ReplicaID are more or less the time the db was created and are equal.  <br>
(There are some issues about generating different DBIDs when many dbs are created in a short time, so in end cases this time can go into the future some.)<br>
<br>
But when a replica of this db is created, its DBID is the time it was created, while the ReplicaID is the same as that of the db from which it is being created.<br>
<br>
Elements in the info box for the note:<br>

<ul>OID
<ul>UNID<br>
File			OF line, currently a random mumber<br>
Note		       ON line, currently the time/date the note was created (@Created)<br>
SequenceTime		SD part of 3rd line, time/date the note was last updated in the universe of replication, @Modified<br>
Sequence (number)	SN part of 3rd line, roughly the number of times the note has been written, should start at 1 but some cases start at 0.<br>
</ul>
DBID			DB line, time/date this instance of the db was created<br>
<br>
NoteID			NT line
<ul><br>
</ul>
</ul>
See GLOBALINSTANCED and UNIVERSALNOTEID in inc\nsfdata.h<br>
<br>
<br>
<b><font size="4" color="#000080">Note ID (NID)</font></b><br>
<br>
The note ID (NID) identifies a note in a database. The NID is the file position of the Record Relocation Vector (RRV) for the note. An RRV is a DWORD offset in a file. Confusion often arises because the note ID is casually referred to as &quot;the Note's RRV in this file.&quot;  In fact, the note ID is the offset in the file to the RRV, which in turn points to the record for the note. An RRV is a  general structure, while a note ID is more specific. Internal to Domino and Notes, various other objects besides notes have an associated RRV.<br>
<br>
<tt><font size="2">typedef DWORD RRV;</font></tt><br>
<tt><font size="2">typedef DWORD NOTEID;</font></tt><br>
<br>
The note ID is guaranteed never to change in one database (.NSF) file, except when the note is deleted. When the note is deleted, the RRV_DELETED bit is set in the note ID. <br>
<br>
<tt><font size="2">#define RRV_DELETED 0x80000000L	/* indicates a deleted note */</font></tt><br>
<br>
Since a note ID is specific to the database file that contains it, replica copies of the same note in other databases will most likely have a different note ID.<br>
<br>
<br>
<b><font size="5" color="#000080">INSTANCEID (IID)</font></b><br>
<br>
The Instance ID identifies an instance of a note in a given database. Each time a note is modified, Domino or Notes stamps the instance ID with the time and date that the update occurred. The Instance ID consists of the note's modification TIMEDATE and the note ID.<br>
<br>
<tt><font size="2">typedef struct {<br>
	TIMEDATE Note;				/* Note's MODIFICATION date/time */<br>
	NOTEID NoteID;				/* Note's RRV */<br>
} INSTANCEID;</font></tt><br>
<br>
<tt><font size="2">#define IID INSTANCEID</font></tt><br>
<br>
The modification TIMEDATE (the Note member of the IID) is not the same thing as the Revision Time in the OID.  Database views use the note modification timedate in the IID to determine when to display the unread flags. You can access the modification timedate by specifying _NOTE_MODIFIED to NSFNoteGetInfo. The replicator uses the Revision Time in the OID to compare replica copies of notes in different databases. You access the Revision Time by  specifying _NOTE_OID to NSFNoteGetInfo.
<ul>
<ul></ul>
</ul>
The NoteID member of the IID is the same value found in the NoteID member of the GNID.<br>
<br>
NSFNoteUpdate sets the modification timedate every time the note is updated to the .NSF file.  The modification timedate governs the unread flags in views. <br>
<br>
There are several ways for an API program to obtain the IID for a note. Get the note ID from the GNID, a NIFReadEntries buffer, or the ID.NoteID member of a SEARCH_MATCH structure. Get the modification timedate from the ID.Note member of a SEARCH_MATCH structure or by calling NSFNoteGetInfo and specifying _NOTE_MODIFIED.<br>
<br>
<br>
<b><font size="5" color="#000080">GLOBALINSTANCEID (GIID)</font></b><br>
<br>
The Global Instance ID globally identifies an instance of a note across databases. It consists of the same members as the Instance ID but adds the database ID as the File member. The note with the latest modification date is the &quot;most recent&quot; instance.<br>
<br>
<tt><font size="2">typedef struct {<br>
	DBID File;					/* database Creation time/date */<br>
	TIMEDATE Note;				/* note Modification time/date */<br>
	NOTEID NoteID;				/* note ID in database */<br>
} GLOBALINSTANCEID;</font></tt><br>
<br>
<tt><font size="2">#define GIID GLOBALINSTANCEID</font></tt><br>
<br>
<br>
API programs can initialize a GIID structure for a note by calling NSFDbIDGet to obtain the File member and then calling NSFNoteGetInfo, specifying _NOTE_MODIFIED to get the members that correspond to the IID modification timedate.
---
