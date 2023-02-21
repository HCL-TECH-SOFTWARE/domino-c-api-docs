##### Data Type : Domino Upgrade Services
##### DUSLOGEVENTPROC - Log Event callback passed to DUS with DUSStart().
---
```
#include <dus.h>
```
**Description :**

In DUSStart(), DUSLOGEVENTPROC is declared.  This allows the ability to send 
messages to the LOG.NSF file from a DUS application.

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

PDUS_CONTEXT pDUSCtx;  

pDUSCtx->LogEventProc = DUSLogEvent;

/* Send a message to the log.nsf file. */
pDUSCtx->LogEventProc( STR_DUS_GETTING_USERS, pDUSCtx->hDUSModule, NOERROR );
```
**See Also :**
[DUSStart](/domino-c-api-docs/reference/Func/DUSStart)
---
