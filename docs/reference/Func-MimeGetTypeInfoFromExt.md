##### Function : MIME
##### MimeGetTypeInfoFromExt - given a file extension, returns a MIME type, subtype, and description.

---
##### #include <mimedir.h>
void LNPUBLIC **MimeGetTypeInfoFromExt(**

	char *pszExt,
	char *pszTypeBuf,
	WORD  wTypeBufLen,
	char *pszSubtypeBuf,
	WORD  wSubtypeBufLen,
	char *pszDescrBuf,
	WORD  wDescrBufLen);
**Description :**
The function MIMEGetTypeInfoFromExt maps an input file extension to a MIME 
type, subtype, and description.  If MIMEGetTypeInfoFromExt is called on the 
Domino server, it opens the Domino Directory and uses the Servers\File 
Identifications view entries to map the input file extension to the 
corresponding MIME type and subtype.

If this procedure fails and the Domino server is running Windows, 
MIMEGetTypeInfoFromExt opens the Windows Registry and searches for the 
'HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\InetInfo\Parameters\MimeMa
p' key.  If MIMEGetTypeInfoFromExt finds this key, it uses its value to map the 
input extension to the corresponding MIME type and subtype.

If MIMEGetTypeInfoFromExt cannot use the Windows registry, it uses an internal 
table to perform the mapping.

If MIMEGetTypeInfoFromExt is called on a Notes client machine running Windows, 
MIMEGetTypeInfoFromExt opens the Windows Registry and searches for the 
'HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\InetInfo\Parameters\MimeMa
p' key.  If MIMEGetTypeInfoFromExt finds this key, it uses its value to map the 
input extension to the corresponding MIME type and subtype.

If MIMEGetTypeInfoFromExt is called on a Notes client machine running a Mac OS, 
MIMEGetTypeInfoFromExt uses the Internet Config to map the input extension to 
the corresponding MIME type and subtype.

If this procedure fails, MIMEGetTypeInfoFromExt opens the Personal Name and 
Address Book and searches for a File Identifications view.  If it finds a File 
Identifications view, MIMEGetTypeInfoFromExt uses it to perform the mapping.

If MIMEGetTypeInfoFromExt cannot find or cannot use the Personal Name and 
Address Book, it uses an internal table to perform the mapping.

**Parameters :**
Input :
pszExt  -  file extension (without the dot).

wTypeBufLen  -  Length of this buffer.

wSubtypeBufLen  -  Length of this buffer.

wDescrBufLen  -  Length of this buffer

Output :
(routine)  -  void


pszTypeBuf  -  Pointer to buffer in which MIME type string will be copied.

pszSubtypeBuf  -  Pointer to buffer in which MIME subtype string will be copied.

pszDescrBuf  -  Pointer to buffer in which description string will be copied.

**Sample Usage :**
```
#define BUFSIZ 32

char aszType[BUFSIZ];
char aszSubtype[BUFSIZ];
char aszDesc[BUFSIZ];

MimeGetTypeInfoFromExt("DOC",
	       aszType,
	       BUFSIZE,
	       aszSubtype,
	       BUFSIZE,
	       aszDesc,
	       BUFSIZE);

```
**See Also :**
[MimeGetExtFromTypeInfo](D:/md_files/MimeGetExtFromTypeInfo.md)
---
