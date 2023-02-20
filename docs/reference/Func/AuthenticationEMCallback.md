##### Function : Extension Manager
##### AuthenticationEMCallback - Extension Manager callback for EM_SECAUTHENTICATION
---
```
#include <extmgr.h>
STATUS LNPUBLIC AuthenticationEMCallback(

	WORD  wEvent,
	SESSIONID  SessionId,
	char far *pRemoteName,
	DWORD  dwFlags,
	WORD  wNetProtocol,
	char far *NetAddress,
	void far *vpNull);
```
**Description :**

EM_SECAUTHENTICATION allows an Extension Manager to include additional 
authentication processing.  This notification is called on the server after the 
core Domino Authentication succeeds but before the session is actually opened.

The type of  Authentication Events are:  AUTHEM_StartAuthentication, 
AUTHEM_Identify, AUTHEM_Poll, AUTHEM_Terminate

The AUTHEM_StartAuthentication Event indicates the callback should initiate 
it's additional authentication protocol.  The AUTHEM_Identify Event  indicates 
the callback should return a null terminated string that identifies the 3rd 
party in pRemoteName.  The AUTHEM_Poll Event indicates that the value 
ERR_NETBFR_YIELD has been returned from a previous AUTHEM_StartAuthentication 
Event and more extensive processing is required. The AUTHEM_Terminate Event 
indicates the current session is closing and may have failed.  The callback 
should then initiate clean up processing.

If the Extension Manager Notification Type is equal to EM_BEFORE (pre-Domino 
Authentication), the pRemoteName parameter will be null.  If the Extension 
Manager Notification Type is equal to EM_AFTER  (post-Domino Authentication), 
and the Events are either AUTHEM_StartAuthentication or AUTHEM_Poll, the 
pRemoteName parameter will contain the full canonical Domino name of the remote 
entity being authenticated.  
If the Event is AUTHEM_Identify,  the callback should return the name of the 
3rd party authentication extension.

It is important to consider that the callback will be invoked for every new 
session and should be designed with process and thread memory issues in mind.  
.

**Parameters :**
Input :
wEvent  -  This parameter indicates the type of event the callback is being called to handle.


SessionId  -  This parameter uniquely identifies the current client-server session.

pRemoteName  -  This parameter has several uses depending on the Event received.  See above.

dwFlags  -  This parameter indicates authentication role and state.  See fAuthxxx flags.

wNetProtocol  -  This parameter indicates the network protocol the current session is using.  See PROTOCOL_xxx.

NetAddress  -  This parameter indicates the network address of the remote entity and is only used when the protocol type is PROTOCOL_TCP.

vpNull  -  This parameter is for future use.

Output :
(routine)  -  
ERR_EM_CONTINUE - this return value indicates the callback has approved the session.
ERR_SECURE_FAILED_AUTH - this return value will break the current session causing authentication to stop.
ERR_NETBFR_YIELD -  this return value will cause an AUTHEM_Poll Event allowing additional processing to continue.


pRemoteName  -  This parameter has several uses depending on the Event received.  See above.



**Sample Usage :**
```
STATUS LNPUBLIC EMHandlerProc( EMRECORD FAR * theData )
{ 
 VARARG_PTR  argPtr;
 STATUS      sError = ERR_EM_CONTINUE;
 
 argPtr = theData->Ap;

 /* do nothing if there is an error. */
 if ( theData->Status ) 
 {
  goto EXIT;
 } 


 switch (theData->EId)
	{
  
  case EM_SECAUTHENTICATION:
  
            /* declare the arguments */

            WORD wEvent = 0;
            SESSIONID SessionId;
            char *pRemoteName = NULL;
            DWORD dwFlags = 0;
            WORD wNetProtocol = 0;
            char *pNetAddress;
                   
            /* get the arguments */

   wEvent = VARARG_GET( argPtr, WORD );
   SessionId = VARARG_GET( argPtr, SESSIONID ); 
  pRemoteName = VARARG_GET( argPtr, char far * ); 
            dwFlags = VARARG_GET( argPtr, DWORD ); 
            wNetProtocol = VARARG_GET( argPtr, WORD );
            pNetAddress = VARARG_GET( argPtr, char far * );  
                   
            /* for this example, only process post Domino Authentication */
            if (theData->NotificationType != EM_AFTER)
              break;  /* break out of here */
	 
         /* switch on types of wEvent */
           switch (wEvent)
            {
	   
                  /* additional authentication code goes here */
              case AUTHEM_StartAuthentication:

                  if (dwFlags & fAuthRoleServer)
                  {
                     /* additional processing */
                  }  
	 
                  if (dwFlags & fAuthRolePassthruServer)
                  {
                     /* additional processing */
                  }
                  
                  if (dwFlags & fAuthClientViaPassthruServer)
                  {
                     /* additional processing */
                  }

                  /* protocol processing... */
                  switch (wNetProtocol)
                  {
                    case PROTOCOL_TCP:
              
                        break;
                        case ...
                  }

                  /* yield processing and cause AUTHEM_Poll wEvent or return 
ERR_EM_CONTINUE */  
                  sError = ERR_NETBFR_YIELD;

                  break;

                  /* code to identify 3rd party goes here */
              case AUTHEM_Identify:

                  strcpy(pRemoteName, "Extension Manager Security 
Authentication Sample");

                  sError = ERR_EM_CONTINUE;
                  
                  break;

                  /* code to handle extensive and/or yielded processing */
              case AUTHEM_Poll:

                  sError = ERR_EM_CONTINUE;
                  
                  break;

                  /* code to handle termination of session or possible failed 
session */
              case AUTHEM_Terminate:

                  sError = ERR_EM_CONTINUE;
                  
                  break;


               }  
	 
      } /* END SWITCH */
   
 
 return( sError );
} 
```
**See Also :**
[AUTHEM_xxx](/reference/Symb/AUTHEM_xxx)
[EM_xxx](/reference/Symb/EM_xxx)
[fAuth_xxx](/reference/Symb/fAuth_xxx)
---
