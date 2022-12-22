




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
@font-face
 {font-family:Helv;
 panose-1:2 11 6 4 2 2 2 3 2 4;}
@font-face
 {font-family:"Cambria Math";
 panose-1:2 4 5 3 5 4 6 3 2 4;}
 /\* Style Definitions \*/
 p.MsoNormal, li.MsoNormal, div.MsoNormal
 {margin-top:0cm;
 margin-right:0cm;
 margin-bottom:8.0pt;
 margin-left:0cm;
 line-height:107%;
 font-size:11.0pt;
 font-family:"Calibri",sans-serif;}
.MsoChpDefault
 {font-size:11.0pt;}
.MsoPapDefault
 {margin-bottom:8.0pt;
 line-height:107%;}
 /\* Page Definitions \*/
 @page WordSection1
 {size:612.0pt 792.0pt;
 margin:72.0pt 72.0pt 72.0pt 72.0pt;}
div.WordSection1
 {page:WordSection1;}
-->




**Initial Release 4.0**



**Symbolic Value : Extension Manager**



**EM\_xxx** **-** EMRegister()
- Extension manager notfication IDs


**----------------------------------------------------------------------------------------------------------**



**#include <extmgr.h>**


 **Symbolic Values :**      EM\_xxx        -  see Description  

  




**Description :**



The
extension manager ID of the specific NSF call that is to send notification to
the callback routine specified in EMRegister().


 


#define
EM\_NSFDBCLOSESESSION                1  

#define EM\_NSFDBCLOSE                       2  

#define EM\_NSFDBCREATE                      3  

#define EM\_NSFDBDELETE                      4  

#define EM\_NSFNOTEOPEN                      5  

#define EM\_NSFNOTECLOSE                     6  

#define EM\_NSFNOTECREATE                    7  

#define EM\_NSFNOTEDELETE                    8  

#define EM\_NSFNOTEOPENBYUNID               10  

#define EM\_FTGETLASTINDEXTIME              11  

#define EM\_FTINDEX                         12  

#define EM\_FTSEARCH                        13  

#define EM\_NIFFINDBYKEY                    14  

#define EM\_NIFFINDBYNAME                   15


#define
EM\_NIFOPENNOTE                     17  

#define EM\_NIFREADENTRIES                  18  

#define EM\_NIFUPDATECOLLECTION             20  

#define EM\_NSFDBALLOCOBJECT                22  

#define EM\_NSFDBCOMPACT                    23  

#define EM\_NSFDBDELETENOTES                24  

#define EM\_NSFDBFREEOBJECT                 25  

#define EM\_NSFDBGETMODIFIEDNOTETABLE       26  

#define EM\_NSFDBGETNOTEINFO                29  

#define EM\_NSFDBGETNOTEINFOBYUNID          30  

#define EM\_NSFDBGETOBJECTSIZE              31  

#define EM\_NSFDBGETSPECIALNOTEID           32  

#define EM\_NSFDBINFOGET                    33  

#define EM\_NSFDBINFOSET                    34  

#define EM\_NSFDBLOCATEBYREPLICAID          35  

#define EM\_NSFDBMODIFIEDTIME               36  

#define EM\_NSFDBREADOBJECT                 37  

#define EM\_NSFDBREALLOCOBJECT              39  

#define EM\_NSFDBREPLICAINFOGET             40  

#define EM\_NSFDBREPLICAINFOSET             41  

#define EM\_NSFDBSPACEUSAGE                 42  

#define EM\_NSFDBSTAMPNOTES                 43  

#define EM\_NSFDBWRITEOBJECT                45  

#define EM\_NSFNOTEUPDATE                   47  

#define EM\_NIFOPENCOLLECTION               50  

#define EM\_NIFCLOSECOLLECTION              51  

#define EM\_NSFDBGETBUILDVERSION            52


#define EM\_NSFDBRENAME                       
54  

#define EM\_NSFDBITEMDEFTABLE               56  

#define EM\_NSFDBREOPEN                     59  

#define EM\_NSFDBOPENEXTENDED               63


#define
EM\_NSFNOTEOPENEXTENDED             64  

#define EM\_TERMINATENSF                    69


#define
EM\_NSFNOTEDECRYPT                  70  

#define EM\_GETPASSWORD                     73  

#define EM\_SETPASSWORD                     74


#define
EM\_NSFCONFLICTHANDLER              75


#define
EM\_MAILSENDNOTE                    83


#define
EM\_CLEARPASSWORD                   90


#define
EM\_NSFNOTEUPDATEXTENDED           102


#define
EM\_SCHFREETIMESEARCH              105  

#define EM\_SCHRETRIEVE                    106  

#define EM\_SCHSRVRETRIEVE                 107


#define
EM\_NSFDBCOMPACTEXTENDED       121


#define EM\_ADMINPPROCESSREQUEST          
124


#define
EM\_NIFGETCOLLECTIONDATA           126


#define
EM\_NSFDBCOPYNOTE                  127


#define
EM\_NSFNOTECOPY                    128


#define
EM\_NSFNOTEATTACHFILE              129


#define
EM\_NSFNOTEDETACHFILE              130


#define
EM\_NSFNOTEEXTRACTFILE             131


#define
EM\_NSFNOTEATTACHOLE2OBJECT        132


#define
EM\_NSFNOTEDELETEOLE2OBJECT        133


#define
EM\_NSFNOTEEXTRACTOLE2OBJECT       134


#define
EM\_NSGETSERVERLIST                135


#define EM\_NSFDBCOPY                     
136


#define
EM\_NSFDBCREATEANDCOPY             137


#define
EM\_NSFDBCOPYACL                   138


#define
EM\_NSFDBCOPYTEMPLATEACL           139


#define
EM\_NSFDBCREATEACLFROMTEMPLATE     140


#define
EM\_NSFDBREADACL                   141


#define
EM\_NSFDBSTOREACL                  142


#define
EM\_NSFDBFILTER                    143


#define
EM\_FTDELETEINDEX                  144


#define
EM\_NSFNOTEGETINFO                 145


#define
EM\_NSFNOTESETINFO                 146


#define
EM\_NSFNOTECOMPUTEWITHFORM         147


#define
EM\_NIFFINDDESIGNNOTE              148


#define
EM\_NIFFINDPRIVATEDESIGNNOTE       149


#define
EM\_NIFGETLASTMODIFIEDTIME         150


#define
EM\_FTSEARCHEXT                    160


#define
EM\_NAMELOOKUP                     161


#define
EM\_NSFNOTEUPDATEMAILBOX           164


#define
EM\_NIFFINDDESIGNNOTEEXT           167


#define
EM\_AGENTOPEN                      170


#define
EM\_AGENTRUN                       171


#define
EM\_AGENTCLOSE                     172


#define
EM\_AGENTISENABLED                 173


#define
EM\_AGENTCREATERUNCONTEXT          175


#define
EM\_AGENTDESTROYRUNCONTEXT         176


#define
EM\_AGENTSETDOCUMENTCONTEXT        177


#define
EM\_AGENTSETTIMEEXECUTIONLIMIT     178


#define
EM\_AGENTQUERYSTDOUTBUFFER         179


#define
EM\_AGENTREDIRECTSTDOUT            180


#define
EM\_SECAUTHENTICATION              184


#define
EM\_NAMELOOKUP2                    185


#define
EM\_NSFDBHASPROFILENOTECHANGED     198


#define
EM\_NSFMARKREAD                    208


#define
EM\_NSFADDTOFOLDER                 209


#define
EM\_NSFDBSPACEUSAGESCALED          210


#define
EM\_NSFDBGETMAJMINVERSION          222


#define
EM\_ROUTERJOURNALMESSAGE           223


#define
EM\_SMTPCONNECT                    224           


#define EM\_SMTPCOMMAND                   
225


#define
EM\_SMTPMESSAGEACCEPT              226


#define
EM\_SMTPDISCONNECT                 227


#define
EM\_NSFARCHIVECOPYNOTES            228


#define
EM\_NSFARCHIVEDELETENOTES        229


#define
EM\_NSFNOTEEXTRACTWITHCALLBACK     235


#define
EM\_NSFDBSTAMPNOTESMULTIITEM       239


#define
EM\_MEDIARECOVERY\_NOTE           244


    #define
EM\_NSFGETCHANGEDDBS                                     246


    #define
EM\_NSFDBMODIFIEDTIMEBYNAME                      247


    #define
EM\_NSFGETDBCHANGES                                      250


    #define
EM\_NSFNOTECIPHERDECRYPT                         251


    #define
EM\_NSFNOTECIPHEREXTRACTFILE                     252


    #define
EM\_NSFNOTECIPHEREXTRACTWITHCALLBACK      253


    #define
EM\_NSFNOTECIPHEREXTRACTOLE2OBJECT        254


    #define
EM\_NSFNOTECIPHERDELETEOLE2OBJECT 255


    #define
EM\_NSFDBNOTELOCK                                256


    #define
EM\_NSFDBNOTEUNLOCK                                      257


 


Note that
for the following Extension Manager  notifications, there is no corresponding
directly-callable C API function.  However you can still register an Extension
Manager callback routine for these events:


 


      EM\_GETPASSWORD                                       see
GetPasswordEMCallback


      EM\_SETPASSWORD                                       see
SetPasswordEMCallback


      EM\_CLEARPASSWORD                                   see
ClearPasswordEMCallback


      EM\_NSFCONFLICTHANDLER                          see
ConflictHandlerEMCallback


      EM\_ADMINPPROCESSREQUEST                    see
ProcessRequestEMCallback


      EM\_TERMINATENSF                                       see
TerminateNSFEMCallback


      EM\_NOTEUPDATEMAILBOX                           see
NSFNoteUpdateMailboxEMCallback


      EM\_NSFNOTEOPENEXTENDED                      see
NSFNoteOpenExtendedEMCallback


      EM\_MAILSENDNOTE                                       see
MailSendNoteEMCallback


      EM\_NSFMARKREAD                                        see
NSFMarkReadEMCallback


      EM\_NSFADDTOFOLDER                                 see
NSFAddToFolderEMCallback


      EM\_SECAUTHENTICATION                             see
AuthenticationEMCallback


      EM\_NSFARCHIVECOPYNOTES                       see
NSFArchiveCopyNotesEMCallback


      EM\_NSFARCHIVEDELETENOTES                   see
NSFArchiveDeleteNotesEMCallback


 


Also, the
signature for the callback function for the following Extension Manager
notifications differs from the public C API function:


 


      EM\_AGENTISENABLED                       see
AgentIsEnabledEMCallback


 


EM\_GETPASSWORD,
EM\_SETPASSWORD and EM\_CLEARPASSWORD can only be registered with the
EM\_REG\_BEFORE flag.  An extension manager hook for these operations cannot be
called after Domino or Notes processes these operations.


 


The callback
routine for the EM\_NSFDBCOMPACT notification may receive NULL for the retStats
parameter.  The Notes client will specify NULL for this parameter when database
compaction is initiated from the user interface.


 


EM\_SCHFREETIMESEARCH,
EM\_SCHRETRIEVE and EM\_SCHSRVRETRIEVE  refer to the following functions,
SchFreeTimeSearch, SchRetrieve and SchSrvRetrieve.


 


EM\_NSFNOTEUPDATEMAILBOX
occurs when an update is performed on any and all mailbox databases (e.g. a
mail.box file).  This is true even if multiple mailboxes are enabled in the
server configuration document.  The extension manager handler for this
notification will have the sender's access to the mailbox database, not the
server's access.


 


If
EM\_NSFNOTEUPDATE/NSFNOTEUPDATEXTENDED and EM\_NSFNOTEUPDATEMAILBOX notifications
are registered, the mailbox specific hook will be called "outside"
the regular note update hook.  That is, the "before" for the mailbox
specific hook will be called prior to calling the "before" for the
regular hook, and the "after" for the mailbox specific hook will be
called after calling the "after" for the regular note update hook. 
The arguments are identical to those used for EM\_NSFNOTEUPDATE.


 


EM\_NSFNOTEDELETE
occurs when NSFNoteDelete or NSFNoteDeleteExtended is called.  The argument
list passed to the extension manager callback routine is the same as the
argument list for NSFNoteDelete.  Note that the extension manager callback
routine can not know whether any extended Flag options have been passed to
NSFNoteDeleteExtended.


 


EM\_TERMINATENSF
occurs when NSF service terminates for the process, right before the extension
manager DLLs are unloaded.  


 


When an
Extension Manager is installed on a Lotus Domino server, calls to the C API to
operate on a database from a client workstation will not necessarily trigger a
corresponding notification.  There is not a one-to-one correspondence between
functions called on a client workstation and the requests sent to the server. 
For example, NSFDbDeleteNotes can only be trapped when the function call is
made on the system hosting the database.  If the system is a Domino server,
requests to delete notes made remotely by client workstations will **not**
result in EM\_NSFDBDELETENOTES notifications on the server.


 


An Extension
Manager that accesses note item data over a network in which the note was not
opened by the Extension Manager itself may receive all note item data,
including the data type WORD in canonical format.  This type of program must
check the OpenFlags parameter in the callback function for EM\_NSFNOTEOPEN or
EM\_NSFNOTEOPENBYUNID to see whether the OPEN\_CANONICAL flag is set in the
OpenFlags parameter.  If this flag is set, use ODSReadMemory to convert any
note item data to host format.


 


The
EM\_NIFOPENNOTE opens a note by index position and optionally navigates.


 **See Also :**


**[AgentIsEnabledEMCallback](AgentIsEnabledEMCallback.md)**


**[AuthenticationEMCallback](AuthenticationEMCallback.md)**


**[ClearPasswordEMCallback](ClearPasswordEMCallback.md)**


**[ConflictHandlerEMCallback](ConflictHandlerEMCallback.md)**


**[EID](EID.md)**


**[EMHANDLER](EMHANDLER.md)**


**[EMRECORD](EMRECORD.md)**


**[EMRegister](EMRegister.md)**


**[GetPasswordEMCallback](GetPasswordEMCallback.md)**


**[MailSendNoteEMCallback](MailSendNoteEMCallback.md)**


**[NSFAddToFolderEMCallback](NSFAddToFolderEMCallback.md)**


**[NSFDbHasProfileNoteChanged](NSFDbHasProfileNoteChanged.md)**


**[NSFMarkReadEMCallback](NSFMarkReadEMCallback.md)**


**[NSFNoteOpenExtendedEMCallback](NSFNoteOpenExtendedEMCallback.md)**


**[NSFNoteUpdateMailboxEMCallback](NSFNoteUpdateMailboxEMCallback.md)**


**[ProcessRequestEMCallback](ProcessRequestEMCallback.md)**


**[SetPasswordEMCallback](SetPasswordEMCallback.md)**


**[TerminateNSFEMCallback](TerminateNSFEMCallback.md)**



----------------------------------------------------------------------------------------------------------


 





