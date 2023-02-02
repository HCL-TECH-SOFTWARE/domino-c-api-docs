##### Function : Extension Manager
##### JournalMessageEMCallback - Extension Manager callback for EM_ROUTERJOURNALMESSAGE
---
##### #include <extmgr.h>
STATUS LNPUBLIC **JournalMessageEMCallback(**

	DBHANDLE  hMailBoxHandle,
	NOTEID  NoteID);
**Description :**
EM_ROUTERJOURNALMESSAGE occurs when the router has received a message that has 
been marked to be journalled. It can be called only when: 1) the server has 
mail journalling enabled and 2) there is a system mail rule that has "Journal 
this message" for some selected set of e-mail messages.

Journaling does not disrupt the normal routing of a message. It saves a copy of 
the selected messages to configured journal database for later 
review/retrieval.
**Parameters :**
Input :
hMailBoxHandle  -  Handle of the mail box.

NoteID  -  Note ID of the message.

Output :
(routine)  -  ERR_EM_CONTINUE -  Continue processing.  



**See Also :**
[EM_xxx](D:/md_files/EM_xxx.md)
---
