##### Data Type : Extension Manager
##### EMHANDLER - Callback function for Extension Manager
---
##### #include <extmgr.h>
**Description :**
This function is the callback that will be called by Domino or  Notes when the 
NSF function with a registered extension is called.  Domino or Notes will 
execute the function before or after the core call, based on the flag that was 
set in the EMRegister done in the initialization of the application.

        An important note:  depending on how the extension has been registered 
(EM_REG_BEFORE, EM_REG_AFTER), when processing the extension, check the 
Notification Type in the EMRECORD structure.  If the Notification Type is 
EM_BEFORE (before the function has been called), input parameters, such as note 
handles, will be active and valid.  However if the Notification Type is 
EM_AFTER (after the function has been called), those same parameters will no 
longer be valid due to Domino or Notes internal processing that may have freed 
and deallocated them.

The parameters passed to the core function are passed to the callback in the 
EMRECORD structure in the Ap field.  This argument pointer is manipulated with 
macro VARARG_GET().  The parameter(s) are in the same order as the original NSF 
function.  All the parameters must be popped off of the Ap in the order they 
appear in the parameter list.

The status code generated inside of the callback function has a direct efffect 
on the execution of Domino or Notes core.  If the callback returns the special 
status code ERR_EM_CONTINUE, Domino or Notes will continue execution (as if 
this hook had never been called).  If the callback returns any other status 
code to Domino or Notes (including NOERROR), no other DLLs or Addins that are 
registered for the same NSF function will get called by the Extension Manager. 
Also if the callback registered with EM_REG_BEFORE returns a status code , the 
Domino or Notes core function will not be executed.
**Sample Usage :**
```
STATUS LNPUBLIC _export EMHandlerProc( EMRECORD FAR * theData )
{ 
 VARARG_PTR  argPtr;
 DBHANDLE    dbHandle;
 STATUS      error; 
 DBID      dbID;
 USHORT      retMode;


 argPtr = theData->Ap;

 /* do nothing if there is an error. */
 if ( theData->Status ) 
 {
  goto EXIT;
 } 


 switch (theData->EId)
 {
  
  case EM_NSFDBCLOSE:
  /*
      if database is opened then clear the flag when the close 
                 function is called on the database.
  */
   if ( gGotMyDatabase == FALSE ) break;
    
  dbHandle = VARARG_GET( argPtr, DBHANDLE ); 

            if (theData->NotificationType == EM_BEFORE)
            {
    if ( dbHandle ) 
    {
      NSFDbIDGet( dbHandle, &dbID );
      if ( EQUAL_DBID(gtheID,dbID) ) 
      {
                      gGotMyDatabase = FALSE;
      }
    }
            }
      break;
  

   case EM_NSFDBOPENEXTENDED:
  /* 
        don't handle any of the hooks until my database is opened,
       and be sure to ignore the hooks when my database is closed.
   */ 
   
   if ( gGotMyDatabase == TRUE ) break;
    
   
  VARARG_GET( argPtr, char FAR * ); 
  VARARG_GET( argPtr, WORD );
  VARARG_GET( argPtr, HANDLE ); 
  VARARG_GET( argPtr, TIMEDATE FAR * ); 
  dbHandle = *( DBHANDLE FAR * )VARARG_GET( argPtr, DBHANDLE FAR *);
  
            if (theData->NotificationType == EM_BEFORE)
            { 
    if ( dbHandle )
    {
   /* check to see if i got a db handle! */
   error = NSFDbModeGet( dbHandle, &retMode );
   if ( !error && (retMode & DB_LOADED) )
   { 
    NSFDbIDGet( dbHandle, &dbID );
    if ( EQUAL_DBID(gtheID,dbID) )
    {
     gGotMyDatabase = TRUE;
    }
   }
    }
            }  
  break;
    
    } /* END SWITCH */
   
 /* 
    if being notified before then always continue onward ignoring 
          the error if not it is possible to return a status code to 
          change the program flow.
 */
EXIT:

 if ( theData && theData->NotificationType == EM_BEFORE )
  return( ERR_EM_CONTINUE );
 else
  return( theData->Status );
}
```
**See Also :**
[EMDeregister](D:/md_files/EMDeregister.md)
[EMRECORD](D:/md_files/EMRECORD.md)
[EMRegister](D:/md_files/EMRegister.md)
[VARARG_GET](D:/md_files/VARARG_GET.md)
---
