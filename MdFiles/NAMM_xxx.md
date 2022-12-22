




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




 


**Symbolic Value : Menu Add-In**



**NAMM\_xxx** **-** Notes menu
add-in function messages.


**----------------------------------------------------------------------------------------------------------**



**#include <addinmen.h>**


 **Symbolic Values :**      NAMM\_INIT             -  Signals the menu add-in to add menu
items to the Notes Actions menu.  

  

      NAMM\_INITMENU    -  Signals the menu add-in to enable, disable, gray,
check, etc. any of its menu items, if desired.  

  

      NAMM\_COMMAND   -  Signals the menu add-in to process the selected menu
item.  

  

      NAMM\_TERM          -  Signals the menu add-in to free up any storage that
it had allocated, before Notes frees the menu add-in.  

  




**Description :**



The Notes
workstation sends these messages to the main menu add-in function in response
to certain events.  The menu add-in function responds to these messages in
different ways depending on the message.   

  

Notes sends the NAMM\_INIT message at initialization time. The menu add-in
function should respond to NAMM\_INIT by adding menu items to the Notes Actions
menu.   

  

Notes sends NAMM\_INITMENU to the menu add-in function when the Notes user
selects the Actions menu. The menu add-in function should respond to
NAMM\_INITMENU by enabling or disabling the menu items.  

  

Notes sends NAMM\_COMMAND to the menu add-in function when the Notes user
selects one of the custom add-in menu items from the Actions menu.  The menu
add-in function should respond to NAMM\_COMMAND by taking the appropriate
action.  

  

Notes sends NAMM\_TERM to the menu add-in function when the Notes workstation is
terminating. The menu add-in function should respond to NAMM\_COMMAND by freeing
any resources they allocated during the workstation session.


 **Sample Usage :**


NAMRESULT LNPUBLIC
DTMenuProc (WORD wMsg, LONG lParam)  

{  

   static WORD startingID;   /\* the Notes ID for the first   

                                addin menu item \*/  

  

   switch (wMsg)  

   {  

      case NAMM\_INIT:  

      {  

         NAM\_INIT\_INFO \*pInitInfo;  

  

         /\* lParam is a pointer to the NAM\_INIT\_INFO structure \*/  

         pInitInfo = (NAM\_INIT\_INFO \*)lParam;


 **See Also :**


**[WM\_ADDIN\_xxx](WM_ADDIN_xxx.md)**


**[NAM\_INIT\_INFO](NAM_INIT_INFO.md)**


**[NAM\_INITMENU\_INFO](NAM_INITMENU_INFO.md)**


**[NAM\_COMMAND\_INFO](NAM_COMMAND_INFO.md)**


**[NAM\_CONTEXT\_DATA](NAM_CONTEXT_DATA.md)**



----------------------------------------------------------------------------------------------------------


 





