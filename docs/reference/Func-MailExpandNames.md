##### Function : Mail Gateway
##### MailExpandNames - Expands all groups in a recipient text list.
---
##### #include <mailserv.h>
STATUS LNPUBLIC **MailExpandNames(**

	DHANDLE  hWorkList,
	WORD  WorkListSize,
	DHANDLE far *hOutputList,
	WORD far *OutputListSize,
	BOOL  UseExpanded,
	DHANDLE  hRecipsExpanded);
**Description :**
This function expands all groups in a recipient text list.
**Parameters :**
Input :
hWorkList  -  Handle of recipient text list to be expanded.  It is assumed that the recipient text list is prefixed with a WORD containing the Domino data type and resides in the local directory.

WorkListSize  -  Size of recipients list.

UseExpanded  -  TRUE if this function is to use and update the hRecipsExpanded list, otherwise FALSE.

hRecipsExpanded  -  Handle to a global text list of recipient group names that have already been expanded so that these groups will not be expanded again by this function.  Used only if UseExpanded is TRUE.  If UseExpanded is FALSE, use NULLHANDLE for this argument.

Output :
(routine)  -   Return status from the call -- indicates either success (NOERROR) or what the error is.


hWorkList  -  This list is deallocated, even on error conditions.

hOutputList  -  Pointer to returned handle to the new list.  The caller is responsible for releasing this memory using OSMemFree.

OutputListSize  -  Pointer to returned size of the new list.

hRecipsExpanded  -  The updated text list that reflects any new expansions.  Used only if UseExpanded is TRUE.

**See Also :**
[MailAddRecipientsItem](D:/md_files/MailAddRecipientsItem.md)
[MailDeleteMessageRecipient](D:/md_files/MailDeleteMessageRecipient.md)
[MailGetMessageRecipient](D:/md_files/MailGetMessageRecipient.md)
---
