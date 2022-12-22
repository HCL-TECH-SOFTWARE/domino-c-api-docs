




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



**Symbolic Value : Backup**



**DB2BACKUP\_LINKS\_xxx** **-** NSFDB2
regenerate links flags.


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**


 **Symbolic Values :**      DB2BACKUP\_LINKS\_VERIFYEXISTING       -  Validate existing
NSFDB2 database link files in the Domino server's data directory and
subdirectories to make sure the link files point to valid NSFDB2 databases.  

  

      DB2BACKUP\_LINKS\_SCANSCHEMAS         -  Scan all schemas defined in the
DB2 database to determine what rows may be missing from the Domino server's
CATALOG table.  

  

      DB2BACKUP\_LINKS\_QUIET            -  Use this flag if you do not wish
NSFDB2RegenerateLinks to log its activity.  

  




**Description :**



These values
are for the flags parameter of NSFDB2RegenerateLinks.


 **See Also :**


**[NSFDB2RegenerateLinks](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/986F1A03FA32C49985256E600055985D)**



----------------------------------------------------------------------------------------------------------


 





