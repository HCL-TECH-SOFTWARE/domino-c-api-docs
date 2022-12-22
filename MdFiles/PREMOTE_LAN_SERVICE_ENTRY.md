




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




**Initial Release 4.5**



**Data Type : Remote LAN adapter**



**PREMOTE\_LAN\_SERVICE\_ENTRY** **-** Calling
convention for a remote LAN service product adapter routine.


**----------------------------------------------------------------------------------------------------------**



**#include
<net.h>**



**Definition :**



typedef STATUS
(LNCALLBACKPTR PREMOTE\_LAN\_SERVICE\_ENTRY)(


   VARARG\_PTR Ap);


 


**Description :**



This typedef
defines the interface to a remote LAN service product adapter general entry
point routine.  This routine performs all the functions of the interface except
for initialization.  Under Windows, the routine must be exported in the
application's .DEF file.


 


This routine
is called by Notes with a standard set of the first five paramters.  After the
standard parameters, there may be additional ones specific to the particular
action being performed, as determined by the first paramter, the Type parameter.


 


Use VARG\_GET
to get the arguments.


 


Inputs:


These are
standard parameters, and must appear in the order shown below.


 


WORD
Type                       Type of action to perform.  See
REMOTE\_LAN\_SERVICE\_xxx for possible values.


 


DWORD
\*pNativeError        Place to store native error code  

  




DWORD
\*pConnectionHandle    


                                          Address
of native handle of the connection (to put to or get from, depending on the
type)  

  




char
\*pErrorBuffer               Place to store error messages for display and
logging by Notes.  Note that if type is REMOTE\_LAN\_SERVICE\_TERMINATE this
address will be NULL.  

  




WORD
ErrorBufferSize        Size of error buffer supplied


 


 


**Additional
arguments -**the interpretation of additonal arguments depends onthe
remote access action type:


 


for
REMOTE\_LAN\_SERVICE\_CONNECT:


            char
\*pEntryName         Name of native dial information entry. 


            char
\*pLoginName        Name to use to login to the remote network.       


            char
\*pPassword           Password to use to login to the remote network. 


            char
\*pPhoneNo            Phone number to dial.   


            char
\*pDialbackNo        Phone number for the remote access server to call back to
to complete the connection.       


 


for
REMOTE\_LAN\_SERVICE\_DISCONNECT:


            char
\*pEntryName         Name of native dial information entry. 


 


for
REMOTE\_LAN\_SERVICE\_CHECK\_CONNECTED**:**


            char
\*pEntryName         Name of native dial information entry. 


 


for
REMOTE\_LAN\_SERVICE\_GET\_EXISTING\_LINKS


            None.


 


for
REMOTE\_LAN\_SERVICE\_TERMINATE 


            None.


 


for
REMOTE\_LAN\_SERVICE\_GET\_DIAL\_ENTRY\_INFO 


            char
\*pPhoneNo            For return of the  phone number in the dial entry.


            char
\*pAreaCode           For return of the  area code in the dial entry.


            char
\*pCountryCode      For return of the country code in the dial entry.


            WORD                         Size
of each of the previous three buffers.


 


for
REMOTE\_LAN\_SERVICE\_CREATE\_DIAL\_ENTRY\_DIALOG 


            None.


 


for
REMOTE\_LAN\_SERVICE\_GET\_DIAL\_ENTRY\_LIST


            char
\*pReturnBuffer      For return of tab-separated list of dial entry names,
terminated by zero.


            WORD
BufSize             Size of storage allocated in the return buffer


            WORD
\*BufCount         Number of characters returned, including the Null terminator.


 


Note
that all strings passed to the adapter and returned from the adapter are stored
in multibyte character (LMBCS) format. To convert these to and from a format
acceptable to the operating system, the program must use the OSTranslate
function.


  

Outputs:


pConnectionHandle             Address
for returning the native handle of the connection after a successful connect
(used for call of type REMOTE\_LAN\_SERVICE\_CONNECT)


 


pErrorBuffer                        Return
error string in buffer at this address


 


(routine)                             Notes
error code. The following error codes have special meaning for Notes dial-up
connections:


NOERROR


ERR\_DEVICE\_IN\_USE


ERR\_CANCEL  
(i.e. the user has aborted)


ERR\_REMOTE\_BUSY;


ERR\_NO\_ANSWER;


ERR\_NO\_CARRIER;


ERR\_NO\_DIALTONE;


 


For all
other error condition, use:


ERR\_REMOTE\_LAN\_ERROR.


 


 **See Also :**


**[PREMOTE\_LAN\_STATUS\_CALLBACK](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/AF43F4D888713FA785256361003C0CB5)**



----------------------------------------------------------------------------------------------------------


 





