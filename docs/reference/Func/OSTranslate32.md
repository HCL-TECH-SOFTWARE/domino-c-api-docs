##### Function : OS Strings
##### OSTranslate32 - Translate a string between the specified character set and Lotus Multi-Byte Character Set (LMBCS) just like OSTranslate.
---
```
#include <osmisc.h>
DWORD OSTranslate32(

	WORD  Charset,
	char *In,
	DWORD  InLength,
	DWORD  OutSize,
	char *OriginalOut);
```
**Description :**

Translate a string between the specified character set and Lotus Multi-Byte 
Character Set (LMBCS) optimized for Group 1. The character set is specified in 
the TranslateMode parameter.  It allows for longer strings (DWORD instead of 
WORD).

LMBCS optimized for Group 1 is the format used for all input and output to the 
API. It is also the format in which all Domino and Notes strings are stored 
internally. 

LMBCS is composed of a set of character "groups" with the leading byte of each 
character indicating the group that the character is in. A string may be 
optimized for a particular group, in which case characters in that group are 
stripped of their initial byte. 

Since Domino and Notes use LMBCS optimized for Group 1, every character in 
Domino and Notes is assumed to be in Group 1 unless it begins with a byte 
indicating otherwise. Japanese characters, for instance, are not in Group 1 so 
within Domino and Notes they begin with a byte indicating their group. 

For UNICODE, only the UTF-8 and UTF-16 encodings are supported. Any UNICODE 
character string supplied to OSTranslate will need to be in UTF-16 format: 
16-bit characters packed together on 16-bit boundaries. This function does the 
same processing as OSTranslate except it allows for longer strings (DWORD vs 
WORD lengths).

**Parameters :**
Input :
Charset  -  ID of the character set to use for translation.
 A flag to control which direction the input string is translated, either LMBCS to the specified character set or the specified character set to LMBCS. 
The flags are described in the symbol set OS_TRANSLATE_xxx.

In  -  The string to be translated.

InLength  -  The size of the input string in bytes, or MAXDWORD.(if MAXDWORD, length is computed by Clstrlen(in)).

OutSize  -  The size of the output buffer in bytes.

Output :
(routine)  -  The number of bytes used to store the return data in the output buffer.


OriginalOut  -  Buffer to receive output.


**Sample Usage :**
```
	char szTmpBuf[MAXSPRINTF+1];
	char *pBuf = szTmpBuf;
  DWORD dwBufLen = sizeof(szTmpBuf); 

	szOriginalOut[0] = '\0';

  /* Dynamically allocate if necessary. */ 

	if (dwOutSize > sizeof(szTmpBuf))
	 {
	  if (OSLocalAllocNZ(dwOutSize, &pBuf)) 
	  return 0; 

	 dwBufLen = dwOutSize; 
	}

	/* We escape first and assume/require the input string to be in LMBCS. 
*/
	 switch (wEscapeMode)
	 {
   case OS_ESCAPE_TO_XML:
	   dwInLength = EscapeForML(szIn, dwInLength, pBuf, dwBufLen);
	 break;
  
	 default:
	   NPpanic("Unknown escape mode in OSTranslateAndEscape\n"); 
	 break;
  }
	
  /* Now do the translation.*/ 
	dwBufLen = OSTranslate32(wCharset, pBuf, dwInLength, szOriginalOut, 
dwOutSize);

  if (pBuf != szTmpBuf) 
	 OSLocalFree (pBuf); 
	 return(dwBufLen);
```
**See Also :**
---
