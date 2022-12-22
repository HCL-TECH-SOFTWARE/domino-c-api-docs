




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



**Data Type : DSAPI**



**FilterAuthenticatedUser** **-** DSAPI Filter
authenticated user structure.


**----------------------------------------------------------------------------------------------------------**



**#include
<dsapi.h>**



**Definition :**




typedef
struct {


        FilterAuthenticatedUserFields         fieldFlags;


        char                                         \*pUserCannonicalName;


        char                                         \*pWebUserName;


        char                                         \*pUserPassword;


        char                                         \*pUserGroupList;


}FilterAuthenticatedUser;


 


**Description :**



The
FilterAuthenticatedUser structure is used by the ServerSupport callback
functionality of the FilterContext.  see FilterContext for more information


 


fieldFlags                           -
(Input)  Flags specifying which fields to retrieve.  see
FilterAuthenticatedUserFields


pUserCannonicalName        -
(Output)  Set to the cannonical name of an authenticated user if fieldFlags
contains the value kCannonicalUserName, NULL otherwise.


pWebUserName                 -
(Output)  Set to the web user name if fieldFlags contains the value
kWebUserName, NULL otherwise.


pUserPassword                  -
(Output)  Set to the web user password if fieldFlags contain the value
kUserPassword, NULL otherwise.


pUserGroupList                  -
(Output)  Set to the user's group name list if fieldFlags contains the value
kUserGroupList, NULL otherwise.


 **See Also :**


**[FilterAuthenticatedUserFields](FilterAuthenticatedUserFields.md)**


**[FilterContext](FilterContext.md)**



----------------------------------------------------------------------------------------------------------


 





