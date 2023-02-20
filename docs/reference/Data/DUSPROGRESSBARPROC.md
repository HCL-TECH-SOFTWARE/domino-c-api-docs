##### Data Type : Domino Upgrade Services
##### DUSPROGRESSBARPROC - Progress Bar callback passed to DUS with DUSStart.
---
```
#include <dus.h>
```
**Description :**

In DUSStart(), DUSPROGRESSBARPROC is declared.  This allows the ability to 
display a progress bar status within a DUS application.

**Sample Usage :**
```
typedef struct
{
 HMODULE   hDUSModule;
 WORD    ExtendedError;
 WORD    ExtendedErrorLevel;
 DUSPROGRESSBARPROC ProgressBarProc;
 DUSLOGEVENTPROC  LogEventProc;
}DUS_CONTEXT, *PDUS_CONTEXT;
char Message[MAXSPRINTF];

PDUS_CONTEXT pDUSCtx;

pDUSCtx->ProgressBarProc = DUSProgressBar;
OSLoadString(pDUSCtx->hDUSModule, STR_DUS_GETTING_USERS, Message, 
sizeof(Message));
for(i=0, index=0; i < *pNumUsersReturned; i++) 
{
 pDUSCtx->ProgressBarProc((DWORD)*pNumUsersReturned, i, Message);
 Sleep(100);   /* Allow for display of Progress Bar status */
 position = 0; 
 pExternalUsers[i].ID = i + *pNumUsersReturned;
 while(((FileBuffer[index] != CHAR_CR) && (FileBuffer[index] != CHAR_LF)) && 
(index < NumberOfBytesRead))
 {  
  /* Parse the data from the input file */
  pExternalUsers[i].Name[position] = FileBuffer[index];
  index++;
  position++;
 }
 index+=2; /* Hop over CRLF in the input File */
}
pDUSCtx->ProgressBarProc(*pNumUsersReturned, *pNumUsersReturned, Message); /* 
Reset Progress Bar */
```
**See Also :**
[DUSStart](/reference/Func/DUSStart)
---
