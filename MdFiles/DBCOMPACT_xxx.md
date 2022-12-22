




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




**Initial Release 4.5**



**Symbolic Value : Mail**



**DBCOMPACT\_xxx** **-** Optional
values for the Options parameter of NSFDbCompact and NSFDbCompactExtended.


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**


 **Symbolic Values :**      DBCOMPACT\_NO\_INDEXES           -  Don't preserve view
indexes  

  

      DBCOMPACT\_NO\_LOCKOUT          -  Don't lock out database users  

  

      DBCOMPACT\_REVERT\_ODS          -  Revert current ODS to the previous ODS
version  

  

      DBCOMPACT\_MAX\_4GB     -  Create new file with 4GB file size limit  

  

      DBCOMPACT\_MAILBOX      -  Compact a mail.box file for mail router and
other MTAs  

  

      DBCOMPACT\_NO\_INPLACE            -  Don't do in-place compaction  

  

      DBCOMPACT\_DISABLE\_UNREAD   -  Disable unread marks in destination
database  

  

      DBCOMPACT\_ENABLE\_UNREAD    -  Reenable unread marks in destination
database (default)  

  

      DBCOMPACT\_DISABLE\_RESPONSE\_INFO             -  Disable response info in
resulting database  

  

      DBCOMPACT\_ENABLE\_RESPONSE\_INFO              -  Reenable response info in
resulting database (default)  

  

      DBCOMPACT\_ENABLE\_FORM\_BKT\_OPT   -  Enable form/bucket bitmap optimization  

  

      DBCOMPACT\_DISABLE\_FORM\_BKT\_OPT   -  Disable form/bucket bitmap optimization
(default)  

  

      DBCOMPACT\_IGNORE\_ERRORS    -  Ignore errors encountered during
compaction. That is, make best effort to get something at the end.  

  

      DBCOMPACT\_RECOVER\_SPACE\_ONLY     -  If set, do only bitmap correction if
in-place can be done.  

  

      DBCOMPACT\_ARCHIVE      -  Archive/delete, then compact the database.  

  

      DBCOMPACT\_ARCHIVE\_ONLY       -  Just archive/delete, no need to compact.  

  

      DBCOMPACT\_RECOVER\_ALL\_SPACE        -  If set, always do full space
recovery compaction.  

  




**Description :**



Optional
values for the Options parameter of NSFDbCompact and NSFDbCompactExtended. Use
DBCOMPACT\_MAILBOX for NSFDbCompact and the others for NSFDbCompactExtended.


 **See Also :**


**[NSFDbCompact](NSFDbCompact.md)**


**[NSFDbCompactExtended](NSFDbCompactExtended.md)**



----------------------------------------------------------------------------------------------------------


 





