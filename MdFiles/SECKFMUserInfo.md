




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
@font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
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




 


**Function : User**



**SECKFMUserInfo** **- Get
current Username and/or License ID.**


**----------------------------------------------------------------------------------------------------------**



**#include <kfm.h>**



STATUS
LNPUBLIC **SECKFMUserInfo(**  

      WORD  Function,  

      char far \*lpName,  

      LICENSEID far \*lpLicense**);**



**Description :**



This
function allows access to both the Username and the LICENSEID structure
associated with the workstation's or server's ID where this function is
executed.


 


**Parameters :**



Input :  

Function  -  Only one action supported:   KFM\_ui\_GetUserInfo - Get the Username
and LICENSEID structure.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - action successful  

  

  

lpName  -  The address of a text buffer in which a null-terminated user name
string obtained from the local ID file is returned.   The buffer must have a
minumum length of  MAXUSERNAME + 1 (see names.h).  This argument may be NULL if
you do not wish this string to be returned.  

  

lpLicense  -  The address of a LICENSEID structure in which the LICENSEID
obtained from the local ID file is returned.  This argument may be NULL if you
do not wish this structure to be returned.  

  




 **Sample Usage :**


/\* Get the User Name
associated w/  current USER.ID \*/  

  

if (error\_status = SECKFMUserInfo(KFM\_ui\_GetUserInfo, user\_name,  

                                     user\_license\_ptr))  

   goto Exit;


 **See Also :**


**[SECKFMGetUserName](SECKFMGetUserName.md)**



----------------------------------------------------------------------------------------------------------


 





