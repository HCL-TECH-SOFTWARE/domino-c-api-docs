##### Data Type : HTML
##### HTMLAPI_REF_TYPE - Reference Types within a generated HTML URL
---
```
#include <htmlapi.h>
```

**Definition :**

typedef enum
{
	HTMLAPI_REF_UNKNOWN = 0   /* unknown purpose */
	,HTMLAPI_REF_HREF = 1   /* A tag HREF= value */
	,HTMLAPI_REF_IMG = 2    /* IMG tag SRC= value */
	,HTMLAPI_REF_FRAME = 3   /* (I)FRAME tag SRC= value */
	,HTMLAPI_REF_APPLET = 4   /* Java applet reference */
	,HTMLAPI_REF_EMBED = 5   /* plugin SRC= reference */
	,HTMLAPI_REF_OBJECT = 6   /* active object DATA= referendce */
	,HTMLAPI_REF_BASE = 7   /* BASE tag value */
	,HTMLAPI_REF_BACKGROUND = 8   /* BODY BACKGROUND */
	,HTMLAPI_REF_CID = 9    /* IMG SRC= value from MIME message */

} HTMLAPI_REF_TYPE;

**Description :**

Indicate the purpose / use of the rerference. For detailed HTML reference type and its usage, please turn to the HTML specification.


**Sample Usage :**
```
	 for ( t = 0; t < nTargets; t++) 
	 { 
	  //check if the refer type is 2 : that is image, then use 
HTMLSetrRferenceText to 
	  //change the text,
	  tgt = pRef->pTargets[t].Target;
	  
	  switch(pRef->RefType) {
	  case HTMLAPI_REF_OBJECT:
	   // do object processing
	   break;
	  case HTMLAPI_REF_IMG:
	   // do  image processing
	   break;
	  }
	 }
```

**See Also :**
[HTMLAPIReference](/domino-c-api-docs/reference/Data/HTMLAPIReference)
[HTMLAPI_URLComponent](/domino-c-api-docs/reference/Data/HTMLAPI_URLComponent)
---
