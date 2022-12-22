




<!--
 /\* Font Definitions \*/
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



**Symbolic Value : Database**



**DBCREATE\_xxx** **-** NSFDbCreateExtended
- Options


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**


 **Symbolic Values :**      DBCREATE\_LOCALSECURITY        -  Create a locally encrypted
database.  

  

      DBCREATE\_OBJSTORE\_NEVER     -  NSFNoteUpdate will not use an object store
for notes in the database.  

  

      DBCREATE\_MAX\_SPECIFIED         -  The maximum database length is
specified in bytes in NSFDbCreateExtended.  

  

      DBCREATE\_NORESPONSE\_INFO   -  Don't support note hierarchy - ODS21 and up
only  

  

      DBCREATE\_NOUNREAD     -  Don't maintain unread lists for this DB  

  

      DBCREATE\_NO\_FREE\_OVERWRITE          -  Skip overwriting freed disk buffer
space  

  

      DBCREATE\_FORM\_BUCKET\_OPT   -  Maintain form/bucket bitmap  

  

      DBCREATE\_DISABLE\_TXN\_LOGGING        -  Disable transaction logging for this
database if specified  

  

      DBCREATE\_MAINTAIN\_LAST\_ACCESSED              -  Enable maintaining last
accessed time  

  

      DBCREATE\_IS\_MAILBOX    -  TRUE if database is a mail[n].box database  

  

      DBCREATE\_LARGE\_UNKTABLE     -  TRUE if database should allow
"large" (>64K bytes) UNK table  

  




**Description :**



Database
creation options.


 **See Also :**


**[NSFDbCreateExtended](NSFDbCreateExtended.md)**



----------------------------------------------------------------------------------------------------------


 





