##### Data Type : HTML
##### HTMLAPI_URLArg - Structure used to hold a URL argument value.
---
```
#include <htmlapi.h>
```

**Definition :**
```
typedef struct
{
	CmdArgID   Id;  /* CmdArgID identifier */
	CmdArgValueType  Type;  /* type of target or arg value (e.g., 
CAVT_String, CAVT_Int, etc.) */
	union
	{
	 int  n;   /* When Type == CAVT_Int,  value as int */
	 NOTEID  nid;   /* When Type == CAVT_NoteId, value as NOTEID */
	 UNID  unid;   /* When Type == CAVT_UNID,  value as UNID */
	 char  *s;   /* When Type == CAVT_String, value as nul-terminated 
string */
	 struct     /* When Type == CAVT_StringList,value is list of NULL 
terminated strings. */
	 {
	  DWORD count; /* number of strings in the list - 0 indicates empty 
list ('first' is undefined) */
	  char *first; /* pointer to first string in list - undefined if 
count==0 */
	 } slist;
	} Value;

} HTMLAPI_URLArg;
```

**Description :**

<br>
The HTMLAPI_URLArg is a part of HTMLAPIReference, please see below picture. When get the HTMLAPIReference from a translated HTML text, you can make analysis by judging the type of this HTMLAPI_URLArg, and then take your actions according to difference type. <br>
<br>
<img src="/apiref.nsf/0/5daf84e33d4e40d1482571960041b509/LongDesc/0.40F6?OpenElement&FieldElemFormat=gif" width="506" height="470">


**Sample Usage :**
```
see sample html/convattach
```

**See Also :**
[HTMLAPIReference](/domino-c-api-docs/reference/Data/HTMLAPIReference)
[HTMLAPI_URLComponent](/domino-c-api-docs/reference/Data/HTMLAPI_URLComponent)
---
