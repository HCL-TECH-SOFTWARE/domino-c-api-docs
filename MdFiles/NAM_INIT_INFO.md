




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




 


**Data Type : Menu Add-In**



**NAM\_INIT\_INFO** **-** Contains
information about add-in menu items.


**----------------------------------------------------------------------------------------------------------**



**#include
<addinmen.h>**



**Definition :**



typedef struct  

   {  

   WORD wStartingID;     /\* Input: DLL must add this to its   

                            menu item ID. \*/  

   WORD wMenuItemNumber; /\* Input: Ascending ordinal number for   

                                   each call. \*/  

  

   WORD wMenuID;          /\* Output: DLL's Menu ID. \*/  

   char MenuItemName[MAX\_ADDIN\_MENU\_NAME]; /\* Output: Text of   

                                                      menu item in LMBCS. \*/  

   } NAM\_INIT\_INFO;


 


**Description :**



This
structure contains information passed from a menu add-in program to Notes about
the menu item to be added, including the menu add-in's menu item ID and name. 
The name must be in LMBCS.  A mnemonic may be assigned to the menu item by
placing an ampersand (&) next to the desired character in the MenuItemName
field of this structure.  This will cause the character that follows the
ampersand to be underlined when the Actions menu is displayed and will allow
the user to select the menu item with this key.    

  

The structure also contains information passed from Notes to the menu add-in,
including the Notes assigned id of the first menu item, and how many times this
procedure has been called (a value of zero indicates the first time this
procedure has been called).  

  

The menu add-in receives this information when processing the NAMM\_INIT message
from Notes.


 **See Also :**


**[NAMM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/006E007C005700A585255DEA0077E6DB)**



----------------------------------------------------------------------------------------------------------


 





