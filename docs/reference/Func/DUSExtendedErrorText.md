##### Function : Domino Upgrade Services
##### DUSExtendedErrorText - Retrieves the text to be displayed in the event of an error calling the DUS extension DLL.
---
```
#include <dus.h>
void LNCALLBACK DUSExtendedErrorText(

	DHANDLE  hContext,
	char *ErrorBuffer,
	WORD  BufferLen,
	WORD *pErrorLevel);
```
**Description :**

This call retrieves the text to be displayed in the event that a call to the 
DUS application fails and the DUS application wishes to return its own error 
string. 

**Parameters :**
Input :
hContext  -  handle to this DUS' specific context information.

BufferLen  -  Length of ErrorBuffer.

Output :
(routine)  -  None.


ErrorBuffer  -  LMBCS string passed to the DUS framework for display.

pErrorLevel  -  pointer to one of three error level flags supplied by the DUS.  This value determines how the error message box will be displayed.  Please refer to DUS_ERROR_LEVEL_xxx.


**Sample Usage :**
```
#define PKG_DUS     PKG_ADDIN
#define STR_DUS_ERR_NOFILE   (PKG_DUS+7)
typedef struct
{
 HMODULE   hDUSModule;
 WORD    ExtendedError;
 WORD    ExtendedErrorLevel;
 DUSPROGRESSBARPROC ProgressBarProc;
 DUSLOGEVENTPROC  LogEventProc;
}DUS_CONTEXT, *PDUS_CONTEXT;

	....
	error = ERR_DUS_EXTENDED_ERROR;
 pDUSCtx->ExtendedError = STR_DUS_ERR_NOFILE;
 pDUSCtx->ExtendedErrorLevel = DUS_ERROR_LEVEL_ERROR; /* Going to gracefully 
shutdown */
	....
	return(error);
```
**See Also :**
[DUS_ERROR_LEVEL_xxx](/domino-c-api-docs/reference/Symb/DUS_ERROR_LEVEL_xxx)
---
