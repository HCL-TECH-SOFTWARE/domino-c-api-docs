##### Symbolic Value : Extension Manager
##### EM_xxx - EMRegister() - Extension manager notfication IDs
---
```
#include <extmgr.h>
```

**Symbolic Values :**

	EM_xxx	  -  see Description


**Description :**

The extension manager ID of the specific NSF call that is to send notification to the callback routine specified in EMRegister().
<ul><br>
<br>
<tt><font size="2">#define EM_NSFDBCLOSESESSION &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;1<br>
#define EM_NSFDBCLOSE &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 2<br>
#define EM_NSFDBCREATE &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;3<br>
#define EM_NSFDBDELETE &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;4<br>
#define EM_NSFNOTEOPEN &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;5<br>
#define EM_NSFNOTECLOSE &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 6<br>
#define EM_NSFNOTECREATE &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;7<br>
#define EM_NSFNOTEDELETE &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;8<br>
#define EM_NSFNOTEOPENBYUNID &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 10<br>
#define EM_FTGETLASTINDEXTIME &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;11<br>
#define EM_FTINDEX &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 12<br>
#define EM_FTSEARCH &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;13<br>
#define EM_NIFFINDBYKEY &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;14<br>
#define EM_NIFFINDBYNAME &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 15</font></tt><br>
<tt><font size="2">#define EM_NIFOPENNOTE &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 17</font></tt><tt><font size="2"><br>
#define EM_NIFREADENTRIES &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;18<br>
#define EM_NIFUPDATECOLLECTION &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 20<br>
#define EM_NSFDBALLOCOBJECT &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;22<br>
#define EM_NSFDBCOMPACT &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;23<br>
#define EM_NSFDBDELETENOTES &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;24<br>
#define EM_NSFDBFREEOBJECT &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 25<br>
#define EM_NSFDBGETMODIFIEDNOTETABLE &nbsp; &nbsp; &nbsp; 26<br>
#define EM_NSFDBGETNOTEINFO &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;29<br>
#define EM_NSFDBGETNOTEINFOBYUNID &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;30<br>
#define EM_NSFDBGETOBJECTSIZE &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;31<br>
#define EM_NSFDBGETSPECIALNOTEID &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 32<br>
#define EM_NSFDBINFOGET &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;33<br>
#define EM_NSFDBINFOSET &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;34<br>
#define EM_NSFDBLOCATEBYREPLICAID &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;35<br>
#define EM_NSFDBMODIFIEDTIME &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 36<br>
#define EM_NSFDBREADOBJECT &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 37<br>
#define EM_NSFDBREALLOCOBJECT &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;39<br>
#define EM_NSFDBREPLICAINFOGET &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 40<br>
#define EM_NSFDBREPLICAINFOSET &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 41<br>
#define EM_NSFDBSPACEUSAGE &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 42<br>
#define EM_NSFDBSTAMPNOTES &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 43<br>
#define EM_NSFDBWRITEOBJECT &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;45<br>
#define EM_NSFNOTEUPDATE &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 47<br>
#define EM_NIFOPENCOLLECTION &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 50<br>
#define EM_NIFCLOSECOLLECTION &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;51<br>
#define EM_NSFDBGETBUILDVERSION &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;52</font></tt><br>
<tt><font size="2">#define EM_NSFDBRENAME			 &nbsp; &nbsp; 54</font></tt><tt><font size="2"><br>
#define EM_NSFDBITEMDEFTABLE &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 56<br>
#define EM_NSFDBREOPEN &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 59<br>
#define EM_NSFDBOPENEXTENDED &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 63</font></tt><br>
<tt><font size="2">#define EM_NSFNOTEOPENEXTENDED &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 64<br>
#define EM_TERMINATENSF &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;69</font></tt><br>
<tt><font size="2">#define EM_NSFNOTEDECRYPT &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;70<br>
#define EM_GETPASSWORD &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 73<br>
#define EM_SETPASSWORD &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 74</font></tt><br>
<tt><font size="2">#define EM_NSFCONFLICTHANDLER &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;75</font></tt><br>
<tt><font size="2">#define EM_MAILSENDNOTE &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;83</font></tt><br>
<tt><font size="2">#define EM_CLEARPASSWORD &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 90</font></tt><br>
<tt><font size="2">#define EM_NSFNOTEUPDATEXTENDED &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 102</font></tt><br>
<tt><font size="2">#define EM_SCHFREETIMESEARCH &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;105<br>
#define EM_SCHRETRIEVE &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;106<br>
#define EM_SCHSRVRETRIEVE &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 107</font></tt><br>
<tt><font size="2">#define EM_NSFDBCOMPACTEXTENDED	 &nbsp; &nbsp;121</font></tt><br>
<tt><font size="2">#define EM_ADMINPPROCESSREQUEST &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 124</font></tt><br>
<tt><font size="2">#define EM_NIFGETCOLLECTIONDATA &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </font></tt><tt><font size="2">126</font></tt><br>
<tt><font size="2">#define EM_NSFDBCOPYNOTE &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><tt><font size="2">127</font></tt><br>
<tt><font size="2">#define EM_NSFNOTECOPY &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;128</font></tt><br>
<tt><font size="2">#define EM_NSFNOTEATTACHFILE &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><tt><font size="2">129</font></tt><br>
<tt><font size="2">#define EM_NSFNOTEDETACHFILE &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><tt><font size="2">130</font></tt><br>
<tt><font size="2">#define EM_NSFNOTEEXTRACTFILE &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </font></tt><tt><font size="2">131</font></tt><br>
<tt><font size="2">#define EM_NSFNOTEATTACHOLE2OBJECT &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><tt><font size="2">132</font></tt><br>
<tt><font size="2">#define EM_NSFNOTEDELETEOLE2OBJECT &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><tt><font size="2">133</font></tt><br>
<tt><font size="2">#define EM_NSFNOTEEXTRACTOLE2OBJECT &nbsp; &nbsp; &nbsp; </font></tt><tt><font size="2">134</font></tt><br>
<tt><font size="2">#define EM_NSGETSERVERLIST &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><tt><font size="2">135</font></tt><br>
<tt><font size="2">#define EM_NSFDBCOPY &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><tt><font size="2">136</font></tt><br>
<tt><font size="2">#define EM_NSFDBCREATEANDCOPY &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </font></tt><tt><font size="2">137</font></tt><br>
<tt><font size="2">#define EM_NSFDBCOPYACL &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </font></tt><tt><font size="2">138</font></tt><br>
<tt><font size="2">#define EM_NSFDBCOPYTEMPLATEACL &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </font></tt><tt><font size="2">139</font></tt><br>
<tt><font size="2">#define EM_NSFDBCREATEACLFROMTEMPLATE &nbsp; &nbsp; </font></tt><tt><font size="2">140</font></tt><br>
<tt><font size="2">#define EM_NSFDBREADACL &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </font></tt><tt><font size="2">141</font></tt><br>
<tt><font size="2">#define EM_NSFDBSTOREACL &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><tt><font size="2">142</font></tt><br>
<tt><font size="2">#define EM_NSFDBFILTER &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><tt><font size="2">143</font></tt><br>
<tt><font size="2">#define EM_FTDELETEINDEX &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><tt><font size="2">144</font></tt><br>
<tt><font size="2">#define EM_NSFNOTEGETINFO &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </font></tt><tt><font size="2">145</font></tt><br>
<tt><font size="2">#define EM_NSFNOTESETINFO &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </font></tt><tt><font size="2">146</font></tt><br>
<tt><font size="2">#define EM_NSFNOTECOMPUTEWITHFORM &nbsp; &nbsp; &nbsp; &nbsp; </font></tt><tt><font size="2">147</font></tt><br>
<tt><font size="2">#define EM_NIFFINDDESIGNNOTE &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><tt><font size="2">148</font></tt><br>
<tt><font size="2">#define EM_NIFFINDPRIVATEDESIGNNOTE &nbsp; &nbsp; &nbsp; </font></tt><tt><font size="2">149</font></tt><br>
<tt><font size="2">#define EM_NIFGETLASTMODIFIEDTIME &nbsp; &nbsp; &nbsp; &nbsp; </font></tt><tt><font size="2">150</font></tt><br>
<tt><font size="2">#define EM_FTSEARCHEXT &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><tt><font size="2">160</font></tt><br>
<tt><font size="2">#define EM_NAMELOOKUP &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 161</font></tt><br>
<tt><font size="2">#define EM_NSFNOTEUPDATEMAILBOX &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 164</font></tt><br>
<tt><font size="2">#define EM_NIFFINDDESIGNNOTEEXT &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 167</font></tt><br>
<tt><font size="2">#define EM_AGENTOPEN &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;170</font></tt><br>
<tt><font size="2">#define EM_AGENTRUN &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 171</font></tt><br>
<tt><font size="2">#define EM_AGENTCLOSE &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 172</font></tt><br>
<tt><font size="2">#define EM_AGENTISENABLED &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 173</font></tt><br>
<tt><font size="2">#define EM_AGENTCREATERUNCONTEXT &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;175</font></tt><br>
<tt><font size="2">#define EM_AGENTDESTROYRUNCONTEXT &nbsp; &nbsp; &nbsp; &nbsp; 176</font></tt><br>
<tt><font size="2">#define EM_AGENTSETDOCUMENTCONTEXT &nbsp; &nbsp; &nbsp; &nbsp;177</font></tt><br>
<tt><font size="2">#define EM_AGENTSETTIMEEXECUTIONLIMIT &nbsp; &nbsp; 178</font></tt><br>
<tt><font size="2">#define EM_AGENTQUERYSTDOUTBUFFER &nbsp; &nbsp; &nbsp; &nbsp; 179</font></tt><br>
<tt><font size="2">#define EM_AGENTREDIRECTSTDOUT &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;180</font></tt><br>
<tt><font size="2">#define EM_SECAUTHENTICATION &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;184</font></tt><br>
<tt><font size="2">#define EM_NAMELOOKUP2 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;185</font></tt><br>
<tt><font size="2">#define EM_NSFDBHASPROFILENOTECHANGED &nbsp; &nbsp; 198</font></tt><br>
<tt><font size="2">#define EM_NSFMARKREAD &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;208</font></tt><br>
<tt><font size="2">#define EM_NSFADDTOFOLDER &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 209</font></tt><br>
<tt><font size="2">#define EM_NSFDBSPACEUSAGESCALED &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;210</font></tt><br>
<tt><font size="2">#define EM_NSFDBGETMAJMINVERSION &nbsp; &nbsp; </font></tt><tt><font size="2">&nbsp; &nbsp; &nbsp;222</font></tt><br>
<tt><font size="2">#define EM_ROUTERJOURNALMESSAGE &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 223</font></tt><br>
<tt><font size="2">#define EM_SMTPCONNECT &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;224		</font></tt><br>
<tt><font size="2">#define EM_SMTPCOMMAND &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;225</font></tt><br>
<tt><font size="2">#define EM_SMTPMESSAGEACCEPT &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;226</font></tt><br>
<tt><font size="2">#define EM_SMTPDISCONNECT &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 227</font></tt><br>
<tt><font size="2">#define EM_NSFARCHIVECOPYNOTES &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;228</font></tt><br>
<tt><font size="2">#define EM_NSFARCHIVEDELETENOTES	 &nbsp; &nbsp; &nbsp;229</font></tt><br>
<tt><font size="2">#define EM_NSFNOTEEXTRACTWITHCALLBACK &nbsp; &nbsp; 235</font></tt><br>
<tt><font size="2">#define EM_NSFDBSTAMPNOTESMULTIITEM &nbsp; &nbsp; &nbsp; 239</font></tt><br>
<tt><font size="2">#define EM_MEDIARECOVERY_NOTE	 &nbsp; &nbsp; &nbsp;244</font></tt></ul>
<tt><font size="2">&nbsp; &nbsp; #define EM_NSFGETCHANGEDDBS					246</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; #define EM_NSFDBMODIFIEDTIMEBYNAME			247</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; #define EM_NSFGETDBCHANGES					250</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; #define EM_NSFNOTECIPHERDECRYPT				251</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; #define EM_NSFNOTECIPHEREXTRACTFILE			252</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; #define EM_NSFNOTECIPHEREXTRACTWITHCALLBACK	253</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; #define EM_NSFNOTECIPHEREXTRACTOLE2OBJECT	254</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; #define EM_NSFNOTECIPHERDELETEOLE2OBJECT	255</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; #define EM_NSFDBNOTELOCK					256</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; #define EM_NSFDBNOTEUNLOCK					257</font></tt>
<ul><br>
Note that for the following Extension Manager  notifications, there is no corresponding directly-callable C API function.  However you can still register an Extension Manager callback routine for these events:<br>
<br>
	EM_GETPASSWORD		see GetPasswordEMCallback<br>
	EM_SETPASSWORD		see SetPasswordEMCallback<br>
	EM_CLEARPASSWORD		see ClearPasswordEMCallback<br>
	EM_NSFCONFLICTHANDLER		see ConflictHandlerEMCallback<br>
	EM_ADMINPPROCESSREQUEST		see ProcessRequestEMCallback<br>
	EM_TERMINATENSF		see TerminateNSFEMCallback<br>
	EM_NOTEUPDATEMAILBOX		see NSFNoteUpdateMailboxEMCallback<br>
	EM_NSFNOTEOPENEXTENDED		see NSFNoteOpenExtendedEMCallback<br>
	EM_MAILSENDNOTE		see MailSendNoteEMCallback<br>
	EM_NSFMARKREAD		see NSFMarkReadEMCallback<br>
	EM_NSFADDTOFOLDER		see NSFAddToFolderEMCallback<br>
	EM_SECAUTHENTICATION		see AuthenticationEMCallback<br>
	EM_NSFARCHIVECOPYNOTES		see NSFArchiveCopyNotesEMCallback<br>
	EM_NSFARCHIVEDELETENOTES		see NSFArchiveDeleteNotesEMCallback<br>
<br>
Also, the signature for the callback function for the following Extension Manager notifications differs from the public C API function:<br>
<br>
	EM_AGENTISENABLED	see AgentIsEnabledEMCallback<br>
<br>
EM_GETPASSWORD, EM_SETPASSWORD and EM_CLEARPASSWORD can only be registered with the EM_REG_BEFORE flag.  An extension manager hook for these operations cannot be called after Domino or Notes processes these operations.<br>
<br>
The callback routine for the EM_NSFDBCOMPACT notification may receive NULL for the retStats parameter.  The Notes client will specify NULL for this parameter when database compaction is initiated from the user interface.<br>
<br>
EM_SCHFREETIMESEARCH, EM_SCHRETRIEVE and EM_SCHSRVRETRIEVE  refer to the following functions, SchFreeTimeSearch, SchRetrieve and SchSrvRetrieve.<br>
<br>
EM_NSFNOTEUPDATEMAILBOX occurs when an update is performed on any and all mailbox databases (e.g. a mail.box file).  This is true even if multiple mailboxes are enabled in the server configuration document.  The extension manager handler for this notification will have the sender's access to the mailbox database, not the server's access.<br>
<br>
If EM_NSFNOTEUPDATE/NSFNOTEUPDATEXTENDED and EM_NSFNOTEUPDATEMAILBOX notifications are registered, the mailbox specific hook will be called &quot;outside&quot; the regular note update hook.  That is, the &quot;before&quot; for the mailbox specific hook will be called prior to calling the &quot;before&quot; for the regular hook, and the &quot;after&quot; for the mailbox specific hook will be called after calling the &quot;after&quot; for the regular note update hook.  The arguments are identical to those used for EM_NSFNOTEUPDATE.<br>
<br>
EM_NSFNOTEDELETE occurs when NSFNoteDelete or NSFNoteDeleteExtended is called.  The argument list passed to the extension manager callback routine is the same as the argument list for NSFNoteDelete.  Note that the extension manager callback routine can not know whether any extended Flag options have been passed to NSFNoteDeleteExtended.<br>
<br>
EM_TERMINATENSF occurs when NSF service terminates for the process, right before the extension manager DLLs are unloaded.  <br>
<br>
When an Extension Manager is installed on a Lotus Domino server, calls to the C API to operate on a database from a client workstation will not necessarily trigger a corresponding notification.  There is not a one-to-one correspondence between functions called on a client workstation and the requests sent to the server.  For example, NSFDbDeleteNotes can only be trapped when the function call is made on the system hosting the database.  If the system is a Domino server, requests to delete notes made remotely by client workstations will <b>not</b> result in EM_NSFDBDELETENOTES notifications on the server.<br>
<br>
An Extension Manager that accesses note item data over a network in which the note was not opened by the Extension Manager itself may receive all note item data, including the data type WORD in canonical format.  This type of program must check the OpenFlags parameter in the callback function for EM_NSFNOTEOPEN or EM_NSFNOTEOPENBYUNID to see whether the OPEN_CANONICAL flag is set in the OpenFlags parameter.  If this flag is set, use ODSReadMemory to convert any note item data to host format.<br>
<br>
The EM_NIFOPENNOTE opens a note by index position and optionally navigates.</ul>



**See Also :**
[AgentIsEnabledEMCallback](/domino-c-api-docs/reference/Func/AgentIsEnabledEMCallback)
[AuthenticationEMCallback](/domino-c-api-docs/reference/Func/AuthenticationEMCallback)
[ClearPasswordEMCallback](/domino-c-api-docs/reference/Func/ClearPasswordEMCallback)
[ConflictHandlerEMCallback](/domino-c-api-docs/reference/Func/ConflictHandlerEMCallback)
[EID](/domino-c-api-docs/reference/Data/EID)
[EMHANDLER](/domino-c-api-docs/reference/Data/EMHANDLER)
[EMRECORD](/domino-c-api-docs/reference/Data/EMRECORD)
[EMRegister](/domino-c-api-docs/reference/Func/EMRegister)
[GetPasswordEMCallback](/domino-c-api-docs/reference/Func/GetPasswordEMCallback)
[MailSendNoteEMCallback](/domino-c-api-docs/reference/Func/MailSendNoteEMCallback)
[NSFAddToFolderEMCallback](/domino-c-api-docs/reference/Func/NSFAddToFolderEMCallback)
[NSFDbHasProfileNoteChanged](/domino-c-api-docs/reference/Func/NSFDbHasProfileNoteChanged)
[NSFMarkReadEMCallback](/domino-c-api-docs/reference/Func/NSFMarkReadEMCallback)
[NSFNoteOpenExtendedEMCallback](/domino-c-api-docs/reference/Func/NSFNoteOpenExtendedEMCallback)
[NSFNoteUpdateMailboxEMCallback](/domino-c-api-docs/reference/Func/NSFNoteUpdateMailboxEMCallback)
[ProcessRequestEMCallback](/domino-c-api-docs/reference/Func/ProcessRequestEMCallback)
[SetPasswordEMCallback](/domino-c-api-docs/reference/Func/SetPasswordEMCallback)
[TerminateNSFEMCallback](/domino-c-api-docs/reference/Func/TerminateNSFEMCallback)
---
