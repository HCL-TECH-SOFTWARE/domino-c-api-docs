##### Data Type : HTML
##### HTMLAPIReference - the complete reference of converted HTML result
---
```
#include <htmlapi.h>
```

**Definition :**

typedef struct {

	HTMLAPI_REF_TYPE RefType; /* How ref is used in the HTML text 
(HTMLAPI_REF_xxx - see list above) */
	char   *pRefText; /* Reference's NULL-terminated text string */
	CmdId   CommandId; /* A web server command associated with the target 
URL */
	HTMLAPI_URLComponent *pTargets; /* Reference's target components */
	HTMLAPI_URLComponent *pArgs; /* Reference's arguments (eg, &Start=xxx, 
&Count=xxx, etc). */
	DWORD   NumTargets; /* Number of components in the target part of the 
reference (dbname, unid, etc.) */
	DWORD   NumArgs; /* Number of components in the args part of the 
reference (&Start, etc.) */
	char   *pFragment; /* NULL-terminated LMBCS text string -- the fragment 
part of URL
	         if there is no fragment, pointer points to "" (i.e. '\0') */

	/* The rest of struct is variable in length.  Use the pointers
	 * in the elements above here to access data from here on down.
	 */
	HTMLAPI_URLComponent URLParts[1]; /* C trick to align first member of 
an array of target and arg values */
	     /* Then come the reference's target strings, arg strings, and text 
string */
} HTMLAPIReference;

**Description :**

<tt>HTMLAPIReference is the complete </tt>reference of converted HTML result<tt>. To understand this data structure more clearly, we will set an example here.</tt><br>
<tt>Suppose there exist a section with a database named picture.nsf. The section's format is like below:</tt><br>
<img width="16" height="16" src="/icons/graycol.gif" border="0" alt="Inactive hide details for Below is a section :"><tt>Below is a section :</tt><br>
<br>
<tt>Below is a section :</tt><br>
<tt>	1. section part 1</tt><br>
<tt>	2. section part 2</tt><br>
<font face="Times New Roman">After the HTML tranlation,  the HTML code transformed from the section is like below :</font><br>
<br>
&lt;a name =&quot;_Section1&quot;&gt;&lt;/a&gt;<br>
&lt;a href=&quot;/picture.nsf/0/64a510cea327672d48257146001bfdac?OpenDocument&amp;ExpandSection=-1#_Section1&quot; target=&quot;_self&quot;&gt;<br>
&lt;img height=&quot;16&quot; width=&quot;16&quot; src='/icons/collapse.gif' border=&quot;0&quot; alt=&quot;Hide details for Below is a section:&quot;&gt;<br>
&lt;/a&gt;<br>
Below is a section:<br>
&lt;ul&gt;<br>
1. section part 1&lt;br&gt;<br>
2. section part 2&lt;br&gt;<br>
&lt;/ul&gt;<br>
<br>
To explain the HTMLAPIReference data structure more clearly, we will explain it with below bitmap:<br>
<br>
<img src="/apiref.nsf/0/134acd680a97ca7b48257196004256c5/LongDesc/58.47D2?OpenElement&FieldElemFormat=gif" width="907" height="236"><br>
<br>
<br>
1  	 The reference Type is HTMLAPI_REF_HREF (RefType)<br>
2 	 The URL command is OpenDocument (CommandId)<br>
3  	 Reference Text (pRefText)<br>
4 	 The number of HTMLAPI_URLTargetComponent within this HTMLAPIReference is 2<br>
5,6,7 	 The first HTMLAPI_URLTargetComponent's detailed information<br>
8,9	 The second HTMLAPI_URLTargetComponent's detailed information<br>
10	 The URL command's Argument is ExpandSection<br>
11	 The value of the URL command's Argument is -1


**See Also :**
[HTMLAPI_REF_TYPE](/domino-c-api-docs/reference/Data/HTMLAPI_REF_TYPE)
[HTMLAPI_URLComponent](/domino-c-api-docs/reference/Data/HTMLAPI_URLComponent)
---
