##### Function : HTML
##### HTMLCreateConverter - Create new converter object.
---
##### #include <htmlapi.h>
STATUS LNPUBLIC **HTMLCreateConverter(**

	HTMLHANDLE *phHTML);
**Description :**
A converter object is used to access most of the HTML API's features.
 The handle is passed as an argument to the those API functions.

**Parameters :**

Output :
(routine)  -  Return status from this call.
	NOERROR - Successful.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.


phHTML  -  the handle to the newly created converter.

**Sample Usage :**
```
	STATUS nstat = NOERROR;
	HTMLHANDLE cvtr = NULLHANDLE;
	if(nstat = HTMLCreateConverter(&cvtr))
	{
	 printf("%s\n", "Error in Creating HTMLConverter");
	 return nstat;
	}
```
**See Also :**
[HTMLDestroyConverter](D:/md_files/HTMLDestroyConverter.md)
[HTMLHANDLE](D:/md_files/HTMLHANDLE.md)
---
