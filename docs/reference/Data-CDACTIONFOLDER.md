##### Data Type : Agents
##### CDACTIONFOLDER - Folder action CD record.
---
##### #include <queryods.h>
**Description :**
A CDACTIONFOLDER record is stored in fields of type TYPE_ACTION, usually the 
action field of an Agent.  The action depends on the signature.  
SIG_ACTION_MOVETOFOLDER indicates that the data selected by the agent is to be 
placed in the folder and deleted from the original location.  
SIG_ACTION_COPYTOFOLDER indicates that a copy of the data selected by the agent 
is to be placed in the folder.  SIG_ACTION_REMOVEFROMFOLDER indicates that the 
data selected by the agent is to be removed from the folder.  The fields in 
this structure are:

Header   Defines this composite data item as a CDACTIONFOLDER item.
dwFlags  Option flags (see ACTIONFOLDER_FLAG_xxx)
wFolderNameLen Length of the folder name
wSpare   Reserved;  must be 0.

This structure is followed by a packed string containing the folder name.
**See Also :**
[ACTIONFOLDER_FLAG_xxx](D:/md_files/ACTIONFOLDER_FLAG_xxx.md)
---
