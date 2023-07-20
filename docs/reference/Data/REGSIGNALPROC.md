##### Data Type : Signal Handler
##### REGSIGNALPROC - Callback function used to display status messages  for the user registration functions.
---
```
#include <reg.h>
```

**Definition :**
```
typedef void (LNCALLBACKPTR REGSIGNALPROC)(
   char far * Message) /* Status string that may be displayed by
                          the function */
```

**Description :**

This data structure defines the syntax of the user-defined callback function called by the user registration functions.  Specify a function that conforms to this syntax as the signalstatus parameter to REGNewWorkstation and other registration functions.  The user registration functions will call your function to display status messages.


**Sample Usage :**
```
/* This code snippet illustrates how to use the callback 
   function in a Window's program  */

    :
    :

FARPROC lpProc;
HCERTIFIER hCertCtx;
STATUS error;
 
/* Prepare to call REGNewWorkstation() to create and register 
   a new user. First get the Organization Unit Certifier 
   context for ABCorp, Sales Unit. Then, pass this certifier 
   context as input to REGNewWorkstation(). It will certify 
   the new user with this certifier. 
*/

if (error = GetCertCtx(ORGUNIT_CERT_ID, &hCertCtx, "abcorp"))
{
   return (ERR(error));
}


lpProc = MakeProcInstance(REGCallback, hInst);   

error = REGNewWorkstation (
   hCertCtx,              /* certifier context */
   KFM_IDFILE_TYPE_DERIVED, /* derived from certifier context */
   ServName,              /* Registration server */
   "Inside Sales",        /* Org Unit - provides uniqueness
                             to the name */
   "Doe",                 /* Last name */
   "Jayne",               /* First name */
   NULL,                  /* no middle initial */
   NULL,                  /* no password initially */
   USER_ID,               /* ID file name */
   "323 West",            /* location - optional */
   NULL,                  /* comment - optional */
   MAILSYSTEM_NOTES,      /* mail system  */
   ServName,              /* mail server name */
   MAILFILENAME,          /* pathname of mail file */
   NULL,                  /* forward address - optional */
   fREGCreateIDFileNow |  /* flags */
   fREGUSARequested    |
   fREGCreateMailFileNow |
   fREGCreateAddrBookEntry,
   0,                        /* minimum password length */
   (REGSIGNALPROC) lpProc,   /* pointer to callback function */
   FullDBPath);              /* returned pathname of file where
                                error occurred */

/* Free the certifier context */
SECKFMFreeCertifierCtx (hCertCtx);

FreeProcInstance(lpProc);

    :
    :
```

**See Also :**
[REGNewWorkstation](/domino-c-api-docs/reference/Func/REGNewWorkstation)
[REGNewServer](/domino-c-api-docs/reference/Func/REGNewServer)
[REGNewCertifier](/domino-c-api-docs/reference/Func/REGNewCertifier)
---
