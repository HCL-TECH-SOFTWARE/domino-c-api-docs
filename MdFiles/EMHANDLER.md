




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
@font-face
 {font-family:Helv;
 panose-1:2 11 6 4 2 2 2 3 2 4;}
@font-face
 {font-family:"Cambria Math";
 panose-1:2 4 5 3 5 4 6 3 2 4;}
 /\* Style Definitions \*/
 p.MsoNormal, li.MsoNormal, div.MsoNormal
 {margin-top:0cm;
 margin-right:0cm;
 margin-bottom:8.0pt;
 margin-left:0cm;
 line-height:107%;
 font-size:11.0pt;
 font-family:"Calibri",sans-serif;}
.MsoChpDefault
 {font-size:11.0pt;}
.MsoPapDefault
 {margin-bottom:8.0pt;
 line-height:107%;}
 /\* Page Definitions \*/
 @page WordSection1
 {size:612.0pt 792.0pt;
 margin:72.0pt 72.0pt 72.0pt 72.0pt;}
div.WordSection1
 {page:WordSection1;}
-->




**Initial Release 4.0**



**Data Type : Extension Manager**



**EMHANDLER** **-** Callback
function for Extension Manager


**----------------------------------------------------------------------------------------------------------**



**#include
<extmgr.h>**



**Definition :**



typedef STATUS
(LNCALLBACKPTR EMHANDLER)(


   EMRECORD far \*);


 


**Description :**



This
function is the callback that will be called by Domino or  Notes when the NSF
function with a registered extension is called.  Domino or Notes will execute
the function before or after the core call, based on the flag that was set in
the EMRegister done in the initialization of the application.


 


       **An
important note:**  depending on how the extension has been registered
(EM\_REG\_BEFORE, EM\_REG\_AFTER), when processing the extension, check the
Notification Type in the EMRECORD structure.  If the Notification Type is
EM\_BEFORE (before the function has been called), input parameters, such as note
handles, will be active and valid.  However if the Notification Type is
EM\_AFTER (after the function has been called), those same parameters will no
longer be valid due to Domino or Notes internal processing that may have freed
and deallocated them.  

  

The parameters passed to the core function are passed to the callback in the
EMRECORD structure in the Ap field.  This argument pointer is manipulated with
macro VARARG\_GET().  The parameter(s) are in the same order as the original NSF
function.  All the parameters must be popped off of the Ap in the order they
appear in the parameter list.  

  

The status code generated inside of the callback function has a direct efffect
on the execution of Domino or Notes core.  If the callback returns the special
status code ERR\_EM\_CONTINUE, Domino or Notes will continue execution (as if
this hook had never been called).  If the callback returns any other status
code to Domino or Notes (including NOERROR), no other DLLs or Addins that are
registered for the same NSF function will get called by the Extension Manager.
Also if the callback registered with EM\_REG\_BEFORE returns a status code , the
Domino or Notes core function will not be executed.


 **Sample Usage :**


STATUS LNPUBLIC \_export
EMHandlerProc( EMRECORD FAR \* theData )  

{   

    VARARG\_PTR  argPtr;  

    DBHANDLE    dbHandle;  

    STATUS      error;   

    DBID         dbID;  

    USHORT       retMode;  

  

  

    argPtr = theData->Ap;  

  

    /\* do nothing if there is an error. \*/  

    if ( theData->Status )   

    {  

           goto EXIT;  

    }   

  

  

    switch (theData->EId)  

    {  

             

           case EM\_NSFDBCLOSE:  

           /\*  

               if database is opened then clear the flag when the close   

                 function is called on the database.  

           \*/  

           if ( gGotMyDatabase == FALSE ) break;  

                     

           dbHandle = VARARG\_GET( argPtr, DBHANDLE ); 


 


            if
(theData->NotificationType == EM\_BEFORE)


            {  

             if ( dbHandle )   

             {  

               NSFDbIDGet( dbHandle, &dbID );  

               if ( EQUAL\_DBID(gtheID,dbID) )   

               {  

                      gGotMyDatabase = FALSE;  

               }  

             }


            }


               break;  

             

  

           case EM\_NSFDBOPENEXTENDED:  

           /\*   

               don't handle any of the hooks until my database is opened,  

               and be sure to ignore the hooks when my database is closed.  

            \*/   

                     

           if ( gGotMyDatabase == TRUE ) break;  

                     

                     

           VARARG\_GET( argPtr, char FAR \* );   

           VARARG\_GET( argPtr, WORD );  

           VARARG\_GET( argPtr, HANDLE );   

           VARARG\_GET( argPtr, TIMEDATE FAR \* );   

           dbHandle = \*( DBHANDLE FAR \* )VARARG\_GET( argPtr, DBHANDLE FAR \*);  

           


            if
(theData->NotificationType == EM\_BEFORE)


            {    

             if ( dbHandle )  

             {  

                   /\* check to see if i got a db handle! \*/  

                   error = NSFDbModeGet( dbHandle, &retMode );  

                   if ( !error && (retMode & DB\_LOADED) )  

                   {   

                          NSFDbIDGet( dbHandle, &dbID );  

                          if ( EQUAL\_DBID(gtheID,dbID) )  

                          {  

                                  gGotMyDatabase = TRUE;  

                          }  

                   }  

             }


            }    

           break;  

                     

    } /\* END SWITCH \*/  

              

    /\*   

       if being notified before then always continue onward ignoring   

          the error if not it is possible to return a status code to   

          change the program flow.  

    \*/  

EXIT:  

  

    if ( theData && theData->NotificationType == EM\_BEFORE )  

           return( ERR\_EM\_CONTINUE );  

    else  

           return( theData->Status );  

}


 **See Also :**


**[EMDeregister](EMDeregister.md)**


**[EMRECORD](EMRECORD.md)**


**[EMRegister](EMRegister.md)**


**[VARARG\_GET](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/C9DF5C6F757C150F852562420065DF69)**



----------------------------------------------------------------------------------------------------------


 





