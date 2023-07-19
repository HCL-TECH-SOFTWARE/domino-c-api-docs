##### Data Type : HTML
##### HTMLAPI_URLTargetComponent - Structure used to hold URL target component.
---
```
#include <htmlapi.h>
```

**Definition :**

typedef struct
{
	UAT AddressableType;  /* the kind of note object the component refers 
to */
	URT ReferenceType; /* the value type of the component -- determines
	       the branch of the following union to use */
	union
	{
	 char  *name;  /* text name of an object */
	 UNID  unid;  /* unique note id */
	 NOTEID  nid;  /* note id */
	 USV  special; /* a special value */
	 DBID  dbid;  /* database id */
	} Value;
} HTMLAPI_URLTargetComponent;


**Description :**

The HTMLAPI_URLTargetComponent is a part of HTMLAPIReference, please see below picture. When get the HTMLAPIReference from a translated HTML text, you can make analysis by judging the type of this HTMLAPI_URLTargetComponent, and then take your actions according to difference type. <br>
<br>
<img src="/apiref.nsf/0/2827d557fd70e40e48257196003ec7dc/LongDesc/0.4100?OpenElement&FieldElemFormat=gif" width="506" height="470">


**Sample Usage :**
```
see samples html/convattach, html/convsection
```

**See Also :**
[HTMLAPIReference](/domino-c-api-docs/reference/Data/HTMLAPIReference)
[HTMLAPI_URLComponent](/domino-c-api-docs/reference/Data/HTMLAPI_URLComponent)
---
