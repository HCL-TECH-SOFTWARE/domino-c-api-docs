##### Function : MIME
##### MimeGetExtFromTypeInfo - given a MIME type and subtype, returns a file extension and description.
---
##### #include <mimedir.h>
void LNPUBLIC **MimeGetExtFromTypeInfo(**

	char	*pszType,
	char	*pszSubtype,
	char	*pszExtBuf,
	WORD	  wExtBufLen,
	char	*pszDescrBuf,
	WORD	  wDescrBufLen);
**Description :**
The function MIMEGetTypeInfoFromExt maps an input MIME type and subtype to a 
file extension and description.  If MimeGetExtFromTypeInfo is called on the 
Domino server, it opens the Domino Directory and uses the Servers\File 
Identifications view entries to map the input MIME type and subtype to the 
corresponding file extension.

If this procedure fails and the Domino server is running Windows, 
MimeGetExtFromTypeInfo opens the Windows Registry and searches for the 
'HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\InetInfo\Parameters\MimeMa
p' key.  If MimeGetExtFromTypeInfo finds this key, it uses its value to map the 
input MIME type and subtype to the corresponding extension.

If MimeGetExtFromTypeInfo cannot use the Windows registry, it uses an internal 
table to perform the mapping.

If MimeGetExtFromTypeInfo is called on a Notes client machine running Windows, 
MimeGetExtFromTypeInfo opens the Windows Registry and searches for the 
'HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\InetInfo\Parameters\MimeMa
p' key.  If MimeGetExtFromTypeInfo finds this key, it uses its value to map the 
input MIME type and subtype to the corresponding extension.

If MimeGetExtFromTypeInfo is called on a Notes client machine running a Mac OS, 
MimeGetExtFromTypeInfo uses the Internet Config to map the input MIME type and 
subtype to the corresponding extension.

If this procedure fails, MimeGetExtFromTypeInfo opens the Personal Name and 
Address Book and searches for a File Identifications view.  If it finds a File 
Identifications view, MimeGetExtFromTypeInfo uses it to perform the mapping.

If MimeGetExtFromTypeInfo cannot find or cannot use the Personal Name and 
Address Book, it uses an internal table to perform the mapping.

**Parameters :**
Input :
pszType  -  Pointer to buffer in which MIME type string will be copied.

pszSubtype  -  Pointer to buffer in which MIME subtype string will be copied.

wExtBufLen  -  Length of the extension buffer.

wDescrBufLen  -  Length of the description buffer.

Output :
(routine)  -  void


pszExtBuf  -  pointer to buffer in which file extension (without the dot) will be copied.

pszDescrBuf  -  Pointer to buffer in which description string will be copied.

**Sample Usage :**
```
#define BUFSIZ 32

char aszExt[BUFSIZ];
char aszDesc[BUFSIZ];

MimeGetExtFromTypeInfo("application",
	       "msword",
	       aszExt,
	       BUFSIZE,
	       aszDesc,
	       BUFSIZE);

```
**See Also :**
[MimeGetTypeInfoFromExt](D:/md_files/MimeGetTypeInfoFromExt.md)
---
