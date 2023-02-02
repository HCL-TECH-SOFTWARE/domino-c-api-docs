##### Data Type : HTML
##### HTMLAPI_REF_TYPE - Reference Types within a generated HTML URL
---
##### #include <htmlapi.h>
**Description :**
Indicate the purpose / use of the rerference. For detailed HTML reference type 
and its usage, please turn to the HTML specification.

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
[HTMLAPIReference](D:/md_files/HTMLAPIReference.md)
[HTMLAPI_URLComponent](D:/md_files/HTMLAPI_URLComponent.md)
---
