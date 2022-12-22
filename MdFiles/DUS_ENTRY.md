




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




**Initial Release 5.0**



**Data Type : Domino Upgrade Services**



**DUS\_ENTRY** **-** Represents
one user or group being imported via a DUS process.


**----------------------------------------------------------------------------------------------------------**



**#include
<dus.h>**



**Definition :**



typedef struct


{


char    Name[DUSMAXFLATNAME+1];       /\*      required
-- user or group name \*/


DWORD   ID;                                          /\*      required
-- unique value identifying this user or group \*/


DWORD   EntryFlags;                           /\*      not
to be used by the DUS \*/


DHANDLE hParentGroupList;             /\*
     Optional and rarely used.  Alloced by the DUS or Notes and freed by Notes.


                                                                    Contains
a Notes LIST of group names to which the entry belongs.


                                                                    This
can be adjusted by Notes after DUSInitialize, depending


                                                                    on
administrator choices at the UI, but can be initially set


                                                                    by
the DUS.  This LIST handle must be created with the


                                                                    prefix
data type set to FALSE (see ListAllocate) and must


                                                                    be
passed UNLOCKED back to Notes. \*/


}
DUS\_ENTRY;


 


 


**Description :**



An array of
these structures is allocated by Domino and passed in to the DUS with
DUSRetrieveUsers and DUSRetrieveGroups. The DUS fills in the data and the
DUS\_ENTRY is passed back to Domino, where the data is displayed in the
"Foreign Directory Import" dialog box within the list of
"Available users/groups" under registration for a user.  You are
responsible for allocating memory for each DUS\_ENTRY with OSMemAlloc() and
freeing the memory with OSMemFree().


 **See Also :**


**[DUSRetrieveGroups](DUSRetrieveGroups.md)**


**[DUSRetrieveUsers](DUSRetrieveUsers.md)**



----------------------------------------------------------------------------------------------------------


 





