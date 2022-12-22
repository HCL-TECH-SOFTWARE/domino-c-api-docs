




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




**Initial Release 6**



**Function : LDAP**



**ldap\_delete\_s** **- Initiate
a synchronous ldap delete operation.**


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**



int
LNPUBLIC **ldap\_delete\_s(**  

      LDAP \*ld,  

      const char \*dn**);**



**Description :**



This
function will initiate a synchronous ldap delete operation.


 


Note that
the entry to delete must be a leaf entry (i.e., it must have no children).
Deletion of entire subtrees in a single operation is not supported by LDAP.


 


Implemented
as a macro:


 


#define
ldap\_delete\_s(ld, dn)           ND\_ldap\_delete\_s((ld), (dn))


 


**Parameters :**



Input :  

ld  -  The LDAP session handle.  

  

dn  -  The distinguished name of the entry to delete.  If NULL, a zero length
DN is sent to the server.  

  




Output :  

(routine)  -  LDAP\_SUCCESS  - If the request was successfully sent, or another
LDAP result code if not.  

  

  




 **Sample Usage :**



    if ((
rc = ldap\_delete\_s( ld, ndn )) != LDAP\_SUCCESS )


    {


         /\*
If entry does not exist, fine.  Ignore this error. \*/


         if
( rc == LDAP\_NO\_SUCH\_OBJECT )


         {


             
printf( "\tEntry \"%s\" is not in the directory.  "


             
"\n\t  No need to delete.\n", ndn );


         }


        
else


         {


            
ldap\_perror( ld, "ldap\_delete\_s" );


            
NotesTerm();


            
return( 1 );


         }


    }


    else


    {


         
printf( "\tDeleted entry \"%s\".\n", ndn );


    }


 




----------------------------------------------------------------------------------------------------------


 





