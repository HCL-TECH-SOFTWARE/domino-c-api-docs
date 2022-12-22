




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




**Initial Release 7.0**



**Symbolic Value : Database; DB2**



**DB2NSF\_INFO\_xxx** **-** Flags for
NSFDB2GetInfo.


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**


 **Symbolic Values :**      DB2NSF\_INFO\_IS\_DB2\_BACKED     -  If the database is DB2, the
buffer will contain a "1". If the database is NSF, the buffer will
contain a "0". Maximum returned buffer size for this flag is
"sizeof(DWORD)".  

  

      DB2NSF\_INFO\_SCHEMA\_NAME      -  The name, in LMBCS, of the database
schema.  

  

      DB2NSF\_INFO\_TABLESPACE\_NAME          -  The name, in LMBCS, of the DB2
tablespace.  

  

      DB2NSF\_INFO\_TSID            -  (LUW only) returns TSID of DB2 tablespace
containing NSFDB2 database  

  

      DB2NSF\_INFO\_USERSCHEMA\_NAME         -  returns the user schema associated
with Domino Access View table & view data.  

  

      DB2NSF\_INFO\_CLASS\_DESC          -  The nsfdb2 class designation that can
be used by third party software applications to group similar NSFDB2 databases.  

  




**Description :**



The type of
information for NSFDB2GetInfo to return.


 **See Also :**


**[NSFDB2GetInfo](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/406189AFDCB6E04385256E60004A00D1)**



----------------------------------------------------------------------------------------------------------


 





