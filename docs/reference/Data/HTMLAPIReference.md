##### Data Type : HTML
##### HTMLAPIReference - the complete reference of converted HTML result
---
```
#include <htmlapi.h>
```
**Description :**

HTMLAPIReference is the complete reference of converted HTML result. To 
understand this data structure more clearly, we will set an example here.
Suppose there exist a section with a database named picture.nsf. The section's 
format is like below:


Below is a section :
	1. section part 1
	2. section part 2
After the HTML tranlation,  the HTML code transformed from the section is like 
below :

<a name ="_Section1"></a>
<a 
href="/picture.nsf/0/64a510cea327672d48257146001bfdac?OpenDocument&ExpandSection
=-1#_Section1" target="_self">
<img height="16" width="16" src='/icons/collapse.gif' border="0" alt="Hide 
details for Below is a section:">
</a>
Below is a section:
<ul>
1. section part 1<br>
2. section part 2<br>
</ul>

To explain the HTMLAPIReference data structure more clearly, we will explain it 
with below bitmap:

1    The reference Type is HTMLAPI_REF_HREF (RefType)
2   The URL command is OpenDocument (CommandId)
3    Reference Text (pRefText)
4   The number of HTMLAPI_URLTargetComponent within this HTMLAPIReference is 2
5,6,7   The first HTMLAPI_URLTargetComponent's detailed information
8,9  The second HTMLAPI_URLTargetComponent's detailed information
10  The URL command's Argument is ExpandSection
11  The value of the URL command's Argument is -1


**See Also :**
[HTMLAPI_REF_TYPE](/reference/Data/HTMLAPI_REF_TYPE)
[HTMLAPI_URLComponent](/reference/Data/HTMLAPI_URLComponent)
---
