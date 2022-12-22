




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




**Initial Release 5.0.3**



**Function : Extension Manager**



**AuthenticationEMCallback** **- Extension
Manager callback for EM\_SECAUTHENTICATION**


**----------------------------------------------------------------------------------------------------------**



**Note:** This function is only available as an Extension Manager callback
-- you cannot call this function directly.


 


**#include <extmgr.h>**



STATUS
LNPUBLIC **AuthenticationEMCallback(**  

      WORD  wEvent,  

      SESSIONID  SessionId,  

      char far \*pRemoteName,  

      DWORD  dwFlags,  

      WORD  wNetProtocol,  

      char far \*NetAddress,  

      void far \*vpNull**);**



**Description :**



EM\_SECAUTHENTICATION
allows an Extension Manager to include additional authentication processing. 
This notification is called on the server after the core Domino Authentication
succeeds but before the session is actually opened.


 


The type of 
Authentication Events are:  AUTHEM\_StartAuthentication, AUTHEM\_Identify,
AUTHEM\_Poll, AUTHEM\_Terminate  

  

The AUTHEM\_StartAuthentication Event indicates the callback should initiate
it's additional authentication protocol.  The AUTHEM\_Identify Event  indicates
the callback should return a null terminated string that identifies the 3rd
party in pRemoteName.  The AUTHEM\_Poll Event indicates that the value
ERR\_NETBFR\_YIELD has been returned from a previous AUTHEM\_StartAuthentication
Event and more extensive processing is required. The AUTHEM\_Terminate Event
indicates the current session is closing and may have failed.  The callback
should then initiate clean up processing.  

  

If the Extension Manager Notification Type is equal to EM\_BEFORE (pre-Domino Authentication),
the pRemoteName parameter will be null.  If the Extension Manager Notification
Type is equal to EM\_AFTER  (post-Domino Authentication), and the Events are
either AUTHEM\_StartAuthentication or AUTHEM\_Poll, the pRemoteName parameter
will contain the full canonical Domino name of the remote entity being
authenticated.    

If the Event is AUTHEM\_Identify,  the callback should return the name of the
3rd party authentication extension.


 


It is
important to consider that the callback will be invoked for every new session
and should be designed with process and thread memory issues in mind.    

.


 


**Parameters :**



Input :  

wEvent  -  This parameter indicates the type of event the callback is being
called to handle.  

  

  

SessionId  -  This parameter uniquely identifies the current client-server
session.  

  

pRemoteName  -  This parameter has several uses depending on the Event
received.  See above.  

  

dwFlags  -  This parameter indicates authentication role and state.  See
fAuthxxx flags.  

  

wNetProtocol  -  This parameter indicates the network protocol the current
session is using.  See PROTOCOL\_xxx.  

  

NetAddress  -  This parameter indicates the network address of the remote
entity and is only used when the protocol type is PROTOCOL\_TCP.  

  

vpNull  -  This parameter is for future use.  

  




Output :  

(routine)  -    

ERR\_EM\_CONTINUE - this return value indicates the callback has approved the
session.  

ERR\_SECURE\_FAILED\_AUTH - this return value will break the current session
causing authentication to stop.  

ERR\_NETBFR\_YIELD -  this return value will cause an AUTHEM\_Poll Event allowing
additional processing to continue.  

  

  

pRemoteName  -  This parameter has several uses depending on the Event
received.  See above.  

  

  




 **Sample Usage :**


STATUS LNPUBLIC
EMHandlerProc( EMRECORD FAR \* theData )  

{   

    VARARG\_PTR  argPtr;  

    STATUS      sError = ERR\_EM\_CONTINUE;  

      

    argPtr = theData->Ap;  

  

    /\* do nothing if there is an error. \*/  

    if ( theData->Status )   

    {  

           goto EXIT;  

    }   

  

  

    switch (theData->EId)  

    {  

             

           case EM\_SECAUTHENTICATION:  

           


            /\* declare
the arguments \*/


 


            WORD wEvent
= 0;


            SESSIONID
SessionId;


            char
\*pRemoteName = NULL;


            DWORD
dwFlags = 0;


            WORD
wNetProtocol = 0;


            char
\*pNetAddress;


                   


            /\* get the
arguments \*/


  

           wEvent = VARARG\_GET( argPtr, WORD );  

           SessionId = VARARG\_GET( argPtr, SESSIONID );   

           pRemoteName = VARARG\_GET( argPtr, char far \* ); 


            dwFlags =
VARARG\_GET( argPtr, DWORD ); 


           
wNetProtocol = VARARG\_GET( argPtr, WORD );


            pNetAddress
= VARARG\_GET( argPtr, char far \* );  


                   


            /\* for this
example, only process post Domino Authentication \*/


            if
(theData->NotificationType != EM\_AFTER)


              break; 
/\* break out of here \*/


          

         /\* switch on types of wEvent \*/


              switch
(wEvent)


            {


                       


                  /\*
additional authentication code goes here \*/


               case
AUTHEM\_StartAuthentication:


 


                  if (dwFlags
& fAuthRoleServer)


                  {


                     /\*
additional processing \*/


                  }  


        


                  if
(dwFlags & fAuthRolePassthruServer)


                  {


                     /\*
additional processing \*/


                  }


                  


                  if
(dwFlags & fAuthClientViaPassthruServer)


                  {


                     /\*
additional processing \*/


                  }


 


                  /\*
protocol processing... \*/


                 
switch (wNetProtocol)


                  {


                       case
PROTOCOL\_TCP:


              


                       
break;


                       
case ...


                  }


 


                  /\*
yield processing and cause AUTHEM\_Poll wEvent or return ERR\_EM\_CONTINUE \*/  


                 
sError = ERR\_NETBFR\_YIELD;


 


                 
break;


 


                  /\*
code to identify 3rd party goes here \*/


               case
AUTHEM\_Identify:


 


                 
strcpy(pRemoteName, "Extension Manager Security Authentication
Sample");


 


                 
sError = ERR\_EM\_CONTINUE;


                  


                 
break;


 


                  /\*
code to handle extensive and/or yielded processing \*/


               case
AUTHEM\_Poll:


 


                 
sError = ERR\_EM\_CONTINUE;


                  


                 
break;


 


                  /\*
code to handle termination of session or possible failed session \*/


               case
AUTHEM\_Terminate:


 


                 
sError = ERR\_EM\_CONTINUE;


                  


                 
break;


 


 


               }  


        


      } /\* END SWITCH
\*/  

              

      

    return( sError );  

}   


 **See Also :**


**[AUTHEM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/0BB02A45BD3FBDD5852568AB00535371)**


**[EM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CCB2911F1DF6C7AF8525681000480140)**


**[fAuth\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F632254A786B5BE7852568AB00535370)**



----------------------------------------------------------------------------------------------------------


 





