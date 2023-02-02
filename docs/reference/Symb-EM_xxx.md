##### Symbolic Value : Extension Manager
##### EM_xxx - EMRegister() - Extension manager notfication IDs
---
##### #include <extmgr.h>
**Description :**
The extension manager ID of the specific NSF call that is to send notification 
to the callback routine specified in EMRegister().

#define EM_NSFDBCLOSESESSION                1
#define EM_NSFDBCLOSE                       2
#define EM_NSFDBCREATE                      3
#define EM_NSFDBDELETE                      4
#define EM_NSFNOTEOPEN                      5
#define EM_NSFNOTECLOSE                     6
#define EM_NSFNOTECREATE                    7
#define EM_NSFNOTEDELETE                    8
#define EM_NSFNOTEOPENBYUNID               10
#define EM_FTGETLASTINDEXTIME              11
#define EM_FTINDEX                         12
#define EM_FTSEARCH                        13
#define EM_NIFFINDBYKEY                    14
#define EM_NIFFINDBYNAME                   15
#define EM_NIFOPENNOTE                     17
#define EM_NIFREADENTRIES                  18
#define EM_NIFUPDATECOLLECTION             20
#define EM_NSFDBALLOCOBJECT                22
#define EM_NSFDBCOMPACT                    23
#define EM_NSFDBDELETENOTES                24
#define EM_NSFDBFREEOBJECT                 25
#define EM_NSFDBGETMODIFIEDNOTETABLE       26
#define EM_NSFDBGETNOTEINFO                29
#define EM_NSFDBGETNOTEINFOBYUNID          30
#define EM_NSFDBGETOBJECTSIZE              31
#define EM_NSFDBGETSPECIALNOTEID           32
#define EM_NSFDBINFOGET                    33
#define EM_NSFDBINFOSET                    34
#define EM_NSFDBLOCATEBYREPLICAID          35
#define EM_NSFDBMODIFIEDTIME               36
#define EM_NSFDBREADOBJECT                 37
#define EM_NSFDBREALLOCOBJECT              39
#define EM_NSFDBREPLICAINFOGET             40
#define EM_NSFDBREPLICAINFOSET             41
#define EM_NSFDBSPACEUSAGE                 42
#define EM_NSFDBSTAMPNOTES                 43
#define EM_NSFDBWRITEOBJECT                45
#define EM_NSFNOTEUPDATE                   47
#define EM_NIFOPENCOLLECTION               50
#define EM_NIFCLOSECOLLECTION              51
#define EM_NSFDBGETBUILDVERSION            52
#define EM_NSFDBRENAME        54
#define EM_NSFDBITEMDEFTABLE               56
#define EM_NSFDBREOPEN                     59
#define EM_NSFDBOPENEXTENDED               63
#define EM_NSFNOTEOPENEXTENDED             64
#define EM_TERMINATENSF                    69
#define EM_NSFNOTEDECRYPT                  70
#define EM_GETPASSWORD                     73
#define EM_SETPASSWORD                     74
#define EM_NSFCONFLICTHANDLER              75
#define EM_MAILSENDNOTE                    83
#define EM_CLEARPASSWORD                   90
#define EM_NSFNOTEUPDATEXTENDED           102
#define EM_SCHFREETIMESEARCH              105
#define EM_SCHRETRIEVE                    106
#define EM_SCHSRVRETRIEVE                 107
#define EM_NSFDBCOMPACTEXTENDED     121
#define EM_ADMINPPROCESSREQUEST           124
#define EM_NIFGETCOLLECTIONDATA           126
#define EM_NSFDBCOPYNOTE                  127
#define EM_NSFNOTECOPY                    128
#define EM_NSFNOTEATTACHFILE              129
#define EM_NSFNOTEDETACHFILE              130
#define EM_NSFNOTEEXTRACTFILE             131
#define EM_NSFNOTEATTACHOLE2OBJECT        132
#define EM_NSFNOTEDELETEOLE2OBJECT        133
#define EM_NSFNOTEEXTRACTOLE2OBJECT       134
#define EM_NSGETSERVERLIST                135
#define EM_NSFDBCOPY                      136
#define EM_NSFDBCREATEANDCOPY             137
#define EM_NSFDBCOPYACL                   138
#define EM_NSFDBCOPYTEMPLATEACL           139
#define EM_NSFDBCREATEACLFROMTEMPLATE     140
#define EM_NSFDBREADACL                   141
#define EM_NSFDBSTOREACL                  142
#define EM_NSFDBFILTER                    143
#define EM_FTDELETEINDEX                  144
#define EM_NSFNOTEGETINFO                 145
#define EM_NSFNOTESETINFO                 146
#define EM_NSFNOTECOMPUTEWITHFORM         147
#define EM_NIFFINDDESIGNNOTE              148
#define EM_NIFFINDPRIVATEDESIGNNOTE       149
#define EM_NIFGETLASTMODIFIEDTIME         150
#define EM_FTSEARCHEXT                    160
#define EM_NAMELOOKUP                     161
#define EM_NSFNOTEUPDATEMAILBOX           164
#define EM_NIFFINDDESIGNNOTEEXT           167
#define EM_AGENTOPEN                      170
#define EM_AGENTRUN                       171
#define EM_AGENTCLOSE                     172
#define EM_AGENTISENABLED                 173
#define EM_AGENTCREATERUNCONTEXT          175
#define EM_AGENTDESTROYRUNCONTEXT         176
#define EM_AGENTSETDOCUMENTCONTEXT        177
#define EM_AGENTSETTIMEEXECUTIONLIMIT     178
#define EM_AGENTQUERYSTDOUTBUFFER         179
#define EM_AGENTREDIRECTSTDOUT            180
#define EM_SECAUTHENTICATION              184
#define EM_NAMELOOKUP2                    185
#define EM_NSFDBHASPROFILENOTECHANGED     198
#define EM_NSFMARKREAD                    208
#define EM_NSFADDTOFOLDER                 209
#define EM_NSFDBSPACEUSAGESCALED          210
#define EM_NSFDBGETMAJMINVERSION          222
#define EM_ROUTERJOURNALMESSAGE           223
#define EM_SMTPCONNECT                    224  
#define EM_SMTPCOMMAND                    225
#define EM_SMTPMESSAGEACCEPT              226
#define EM_SMTPDISCONNECT                 227
#define EM_NSFARCHIVECOPYNOTES            228
#define EM_NSFARCHIVEDELETENOTES       229
#define EM_NSFNOTEEXTRACTWITHCALLBACK     235
#define EM_NSFDBSTAMPNOTESMULTIITEM       239
#define EM_MEDIARECOVERY_NOTE       244
    #define EM_NSFGETCHANGEDDBS     246
    #define EM_NSFDBMODIFIEDTIMEBYNAME   247
    #define EM_NSFGETDBCHANGES     250
    #define EM_NSFNOTECIPHERDECRYPT    251
    #define EM_NSFNOTECIPHEREXTRACTFILE   252
    #define EM_NSFNOTECIPHEREXTRACTWITHCALLBACK 253
    #define EM_NSFNOTECIPHEREXTRACTOLE2OBJECT 254
    #define EM_NSFNOTECIPHERDELETEOLE2OBJECT 255
    #define EM_NSFDBNOTELOCK     256
    #define EM_NSFDBNOTEUNLOCK     257

Note that for the following Extension Manager  notifications, there is no 
corresponding directly-callable C API function.  However you can still register 
an Extension Manager callback routine for these events:

	EM_GETPASSWORD  see GetPasswordEMCallback
	EM_SETPASSWORD  see SetPasswordEMCallback
	EM_CLEARPASSWORD  see ClearPasswordEMCallback
	EM_NSFCONFLICTHANDLER  see ConflictHandlerEMCallback
	EM_ADMINPPROCESSREQUEST  see ProcessRequestEMCallback
	EM_TERMINATENSF  see TerminateNSFEMCallback
	EM_NOTEUPDATEMAILBOX  see NSFNoteUpdateMailboxEMCallback
	EM_NSFNOTEOPENEXTENDED  see NSFNoteOpenExtendedEMCallback
	EM_MAILSENDNOTE  see MailSendNoteEMCallback
	EM_NSFMARKREAD  see NSFMarkReadEMCallback
	EM_NSFADDTOFOLDER  see NSFAddToFolderEMCallback
	EM_SECAUTHENTICATION  see AuthenticationEMCallback
	EM_NSFARCHIVECOPYNOTES  see NSFArchiveCopyNotesEMCallback
	EM_NSFARCHIVEDELETENOTES  see NSFArchiveDeleteNotesEMCallback

Also, the signature for the callback function for the following Extension 
Manager notifications differs from the public C API function:

	EM_AGENTISENABLED see AgentIsEnabledEMCallback

EM_GETPASSWORD, EM_SETPASSWORD and EM_CLEARPASSWORD can only be registered with 
the EM_REG_BEFORE flag.  An extension manager hook for these operations cannot 
be called after Domino or Notes processes these operations.

The callback routine for the EM_NSFDBCOMPACT notification may receive NULL for 
the retStats parameter.  The Notes client will specify NULL for this parameter 
when database compaction is initiated from the user interface.

EM_SCHFREETIMESEARCH, EM_SCHRETRIEVE and EM_SCHSRVRETRIEVE  refer to the 
following functions, SchFreeTimeSearch, SchRetrieve and SchSrvRetrieve.

EM_NSFNOTEUPDATEMAILBOX occurs when an update is performed on any and all 
mailbox databases (e.g. a mail.box file).  This is true even if multiple 
mailboxes are enabled in the server configuration document.  The extension 
manager handler for this notification will have the sender's access to the 
mailbox database, not the server's access.

If EM_NSFNOTEUPDATE/NSFNOTEUPDATEXTENDED and EM_NSFNOTEUPDATEMAILBOX 
notifications are registered, the mailbox specific hook will be called 
"outside" the regular note update hook.  That is, the "before" for the mailbox 
specific hook will be called prior to calling the "before" for the regular 
hook, and the "after" for the mailbox specific hook will be called after 
calling the "after" for the regular note update hook.  The arguments are 
identical to those used for EM_NSFNOTEUPDATE.

EM_NSFNOTEDELETE occurs when NSFNoteDelete or NSFNoteDeleteExtended is called.  
The argument list passed to the extension manager callback routine is the same 
as the argument list for NSFNoteDelete.  Note that the extension manager 
callback routine can not know whether any extended Flag options have been 
passed to NSFNoteDeleteExtended.

EM_TERMINATENSF occurs when NSF service terminates for the process, right 
before the extension manager DLLs are unloaded.  

When an Extension Manager is installed on a Lotus Domino server, calls to the C 
API to operate on a database from a client workstation will not necessarily 
trigger a corresponding notification.  There is not a one-to-one correspondence 
between functions called on a client workstation and the requests sent to the 
server.  For example, NSFDbDeleteNotes can only be trapped when the function 
call is made on the system hosting the database.  If the system is a Domino 
server, requests to delete notes made remotely by client workstations will not 
result in EM_NSFDBDELETENOTES notifications on the server.

An Extension Manager that accesses note item data over a network in which the 
note was not opened by the Extension Manager itself may receive all note item 
data, including the data type WORD in canonical format.  This type of program 
must check the OpenFlags parameter in the callback function for EM_NSFNOTEOPEN 
or EM_NSFNOTEOPENBYUNID to see whether the OPEN_CANONICAL flag is set in the 
OpenFlags parameter.  If this flag is set, use ODSReadMemory to convert any 
note item data to host format.

The EM_NIFOPENNOTE opens a note by index position and optionally navigates.
**See Also :**
[AgentIsEnabledEMCallback](D:/md_files/AgentIsEnabledEMCallback.md)
[AuthenticationEMCallback](D:/md_files/AuthenticationEMCallback.md)
[ClearPasswordEMCallback](D:/md_files/ClearPasswordEMCallback.md)
[ConflictHandlerEMCallback](D:/md_files/ConflictHandlerEMCallback.md)
[EID](D:/md_files/EID.md)
[EMHANDLER](D:/md_files/EMHANDLER.md)
[EMRECORD](D:/md_files/EMRECORD.md)
[EMRegister](D:/md_files/EMRegister.md)
[GetPasswordEMCallback](D:/md_files/GetPasswordEMCallback.md)
[MailSendNoteEMCallback](D:/md_files/MailSendNoteEMCallback.md)
[NSFAddToFolderEMCallback](D:/md_files/NSFAddToFolderEMCallback.md)
[NSFDbHasProfileNoteChanged](D:/md_files/NSFDbHasProfileNoteChanged.md)
[NSFMarkReadEMCallback](D:/md_files/NSFMarkReadEMCallback.md)
[NSFNoteOpenExtendedEMCallback](D:/md_files/NSFNoteOpenExtendedEMCallback.md)
[NSFNoteUpdateMailboxEMCallback](D:/md_files/NSFNoteUpdateMailboxEMCallback.md)
[ProcessRequestEMCallback](D:/md_files/ProcessRequestEMCallback.md)
[SetPasswordEMCallback](D:/md_files/SetPasswordEMCallback.md)
[TerminateNSFEMCallback](D:/md_files/TerminateNSFEMCallback.md)
---
