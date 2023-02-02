##### Function : Extension Manager
##### MailSendNoteEMCallback - Extension Manager callback for EM_MAILSENDNOTE
---
##### #include <extmgr.h>
STATUS LNPUBLIC **MailSendNoteEMCallback(**

	HANDLE  hNote,
	void *internalViewDesc,
	WORD  Flags,
	BOOL *Modified,
	void *SendNoteCtx);
**Description :**
EM_MAILSENDNOTE is called when the Mailer sends an open note to recipients 
listed in the note's header items.
**Parameters :**
Input :
hNote  -  Handle to open note.

internalViewDesc  -  Used by alternate mail to find the form for the note.

Flags  -  Note:  MSN_xxx Flags are not currently exposed. 

Output :
(routine)  -  Return status from the call 
ERR_EM_CONTINUE


Modified  -  Set to True if note is modified, otherwise it is set to False. 

SendNoteCtx  -  Note:  The structure of this data is not currently exposed.

**See Also :**
[EM_xxx](D:/md_files/EM_xxx.md)
---
