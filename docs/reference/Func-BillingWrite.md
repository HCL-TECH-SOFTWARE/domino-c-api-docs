##### Function : Billing
##### BillingWrite - Writes a Billing message record
---
##### #include <billing.h>
STATUS LNPUBLIC **BillingWrite(**

	DWORD  Class,
	WORD  StructType,
	WORD  Len,
	void far *pMessage,
	char far *MQName);
**Description :**
Use this call to write a billing message record to a message queue.  By default 
the record is written to MQ$Billing.  The data in the MQ$Billing queue can then 
be read by the billing server task.  

Only a billing server task can execute BillingWrite().  Typically, the 
BillingWrite() function is called by an extension manager handler or from 
within a Lotus Domino Server add-in program.
**Parameters :**
Input :
Class  -  Billing Class values (see BILL_CLASS_xxx).

StructType  -  Billing Structure type written to the billing queue (see BILL_xxx (structure types)).  Note: Custom structure types that are user-defined are also valid.

Len  -  Size of the billing message to be sent to the message queue.

pMessage  -  Address of the billing message data structure to be sent to the message queue.

MQName  -  Name of the message queue.  NULL defaults to MQ$Billing.

Output :
(routine)  -  
If the message is written successfully to the Billing queue; NOERROR.
If pMessage is not present; ERR_BAD_PARAM.
If MQ error; then returns that error (see MQPut function for error details).


**Sample Usage :**
```
/* This is a sample Extension Manager Handler for using
   BillingWrite() to bill note creations*/

/* The following are additions/modifications that were made to a
   copy of the supplied C API include file billing.h in order
	to support the user extensions added here.*/

#define BILL_NOTECREATEREC  32001  /* new billing type */

typedef struct
      {
 char      Username[MAXUSERNAME+1];/* Username */
 NOTEID    dbNoteID;               /* Created note id */ 
    TIMEDATE  ReplicaID;              /* Database replica id */
   } NOTECREATEREC;


/* The following is a modified billing message structure taken
	from the C API include file billing.h  Typically, this code
	would replace the respective code that appears in billing.h  */

typedef union
{
   SESSIONREC    sess;
   REPLREC       repl;
   DOCUMENT      doc;
   MAILREC       mail;
   DBREC         db;
   AGENTREC      agent;
   HTTPREQREC    HttpRequest;
   NOTECREATEREC notecreate;
} BILLREC;


/* The following is a sample extension handler that sends billing
   records to the billing message queue after every sucessful 
   NFSNoteUpdate() API call for a created note. The EM registration
   calls are omitted */

STATUS LNCALLBACK BillHandler ( EMRECORD FAR * theData )
{ 
   
   STATUS     error = NOERROR;
   BILLMSG    BillMsg;
   VARARG_PTR argPtr;

   NOTEHANDLE hNote;                        /* NSFNoteUpdateExtended argument */
   HANDLE     hDb;                          /* Associated DB handle */
   char       Username[MAXUSERNAME+1];      /* Note create user */  
   NOTEID     NoteId;                       /* NOTEID of note */
   DBID       DbId;                         /* DBID of note */
   char       Servername[MAXUSERNAME+1];    /* Server name */  
   DWORD      BillClass; 

/* Check to see if Database billing class is enabled. If not, return without
   sending billing record */

   if (error = BillingGetClass( &BillClass ))

/* Only bill if the API was successful. If not, return without sending 
   billing record. */
     
      goto Done;

   if ((BOOL)(BillClass & BILL_CLASS_DATABASE))
   {

      if ( theData->Status != NOERROR )
         goto Done;
      
/* otherwise handle Note Create billing by interpreting NSFNoteUpdateExtended 
calls */
      
      argPtr = theData->Ap;

/* Before the API:  check to see if the Note ID is equal to zero.   If it is 
   then this means a new note is being created and we should track the output. 
*/
   
      if ( theData->NotificationType == EM_BEFORE )
      {
         hNote = VARARG_GET (argPtr, HANDLE);   /* save note handle */
         (void) VARARG_GET (argPtr, DWORD);      /* skip update flags */
            
   /* get NOTEID of input note handle */
         NSFNoteGetInfo(hNote, _NOTE_ID, &NoteId);

   /* if NOTEID = 0, then set for billing */
         if (NoteId == 0)
            gCreatedNote = TRUE;    
         else
            gCreatedNote = FALSE;    
            
         return ( ERR_EM_CONTINUE ); /* continue;, billing occurs after call */
      }

/* If after the call and a new note was created, fill in the UserName, Note ID, 
   and Replica ID of the created note in the billing record. */

/* NOTE: Since a global is used to determine if a new note was created, this 
         logic assumes that the EM_AFTER handling occurs before a different 
         NSFNoteUpdateExtended EM_BEFORE thread is handled by Domino.  For 
heavily
         loaded systems, it may be necessary to serialize these requests. */

      if (gCreatedNote == TRUE)
      {
         memset( &(BillMsg.rec.notecreate), (char)0, sizeof( 
BillMsg.rec.notecreate ) );
         hNote = VARARG_GET (argPtr, HANDLE);   /* save note handle */
         (void) VARARG_GET (argPtr, DWORD);      /* skip update flags */

   /* get NOTEID of note handle */
         NSFNoteGetInfo(hNote, _NOTE_ID, &NoteId);

   /* get the DBHANDLE for note handle */
         NSFNoteGetInfo(hNote, _NOTE_DB, &hDb);

   /* get DBID associated with the DBHANDLE */
         NSFDbIDGet(hDb, &DbId);

   /* get USERNAME associated with the DBHANDLE */
         (void) NSFDbUserNameGet(hDb, Username, MAXUSERNAME);

   /* if user is the server, then do not bill */
         (void) SECKFMGetUserName(Servername);
         if (!strcmp(Username, Servername))
            goto Done;       

   /* else, set billing message fields with appropriate info*/
         strcpy(BillMsg.rec.notecreate.Username, Username);
         BillMsg.rec.notecreate.dbNoteID = NoteId;  
         BillMsg.rec.notecreate.ReplicaID = DbId;  

   /* and write the billing record */
         error = BillingWrite( (DWORD)BILL_CLASS_DATABASE, 
                               (WORD)BILL_NOTECREATEREC, 
                               sizeof( BillMsg ),
                               &BillMsg,
                               BILL_QUEUE_NAME );
      }
   }

/* Whether or not the Billing the record was written, return the original
   NSFNoteUpdateExtended (EM_AFTER) status back to Domino */    

Done:
   if (theData && theData->NotificationType == EM_BEFORE)
      return( ERR_EM_CONTINUE );
   else
      return( theData->Status );

}
```
**See Also :**
[BillingGetClass](D:/md_files/BillingGetClass.md)
[BILLMSG](D:/md_files/BILLMSG.md)
[BILLREC](D:/md_files/BILLREC.md)
[BILL_CLASS_xxx](D:/md_files/BILL_CLASS_xxx.md)
[BILL_xxx (structure types)](D:/md_files/BILL_xxx (structure types).md)
[EMHANDLER](D:/md_files/EMHANDLER.md)
---
