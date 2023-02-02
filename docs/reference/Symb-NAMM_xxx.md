##### Symbolic Value : Menu Add-In
##### NAMM_xxx - Notes menu add-in function messages.
---
##### #include <addinmen.h>
**Description :**
The Notes workstation sends these messages to the main menu add-in function in 
response to certain events.  The menu add-in function responds to these 
messages in different ways depending on the message. 

Notes sends the NAMM_INIT message at initialization time. The menu add-in 
function should respond to NAMM_INIT by adding menu items to the Notes Actions 
menu. 

Notes sends NAMM_INITMENU to the menu add-in function when the Notes user 
selects the Actions menu. The menu add-in function should respond to 
NAMM_INITMENU by enabling or disabling the menu items.

Notes sends NAMM_COMMAND to the menu add-in function when the Notes user 
selects one of the custom add-in menu items from the Actions menu.  The menu 
add-in function should respond to NAMM_COMMAND by taking the appropriate action.

Notes sends NAMM_TERM to the menu add-in function when the Notes workstation is 
terminating. The menu add-in function should respond to NAMM_COMMAND by freeing 
any resources they allocated during the workstation session.
**Sample Usage :**
```
NAMRESULT LNPUBLIC DTMenuProc (WORD wMsg, LONG lParam)
{
   static WORD startingID;   /* the Notes ID for the first 
                                addin menu item */

   switch (wMsg)
   {
      case NAMM_INIT:
      {
         NAM_INIT_INFO *pInitInfo;

         /* lParam is a pointer to the NAM_INIT_INFO structure */
         pInitInfo = (NAM_INIT_INFO *)lParam;
```
**See Also :**
[WM_ADDIN_xxx](D:/md_files/WM_ADDIN_xxx.md)
[NAM_INIT_INFO](D:/md_files/NAM_INIT_INFO.md)
[NAM_INITMENU_INFO](D:/md_files/NAM_INITMENU_INFO.md)
[NAM_COMMAND_INFO](D:/md_files/NAM_COMMAND_INFO.md)
[NAM_CONTEXT_DATA](D:/md_files/NAM_CONTEXT_DATA.md)
---
