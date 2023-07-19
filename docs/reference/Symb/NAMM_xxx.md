##### Symbolic Value : Menu Add-In
##### NAMM_xxx - Notes menu add-in function messages.
---
```
#include <addinmen.h>
```

**Symbolic Values :**

	NAMM_INIT	  -  Signals the menu add-in to add menu items to the Notes Actions menu.

	NAMM_INITMENU	  -  Signals the menu add-in to enable, disable, gray, check, etc. any of its menu items, if desired.

	NAMM_COMMAND	  -  Signals the menu add-in to process the selected menu item.

	NAMM_TERM	  -  Signals the menu add-in to free up any storage that it had allocated, before Notes frees the menu add-in.


**Description :**

The Notes workstation sends these messages to the main menu add-in function in response to certain events.  The menu add-in function responds to these messages in different ways depending on the message. <br>
<br>
Notes sends the NAMM_INIT message at initialization time. The menu add-in function should respond to NAMM_INIT by adding menu items to the Notes Actions menu. <br>
<br>
Notes sends NAMM_INITMENU to the menu add-in function when the Notes user selects the Actions menu. The menu add-in function should respond to NAMM_INITMENU by enabling or disabling the menu items.<br>
<br>
Notes sends NAMM_COMMAND to the menu add-in function when the Notes user selects one of the custom add-in menu items from the Actions menu.  The menu add-in function should respond to NAMM_COMMAND by taking the appropriate action.<br>
<br>
Notes sends NAMM_TERM to the menu add-in function when the Notes workstation is terminating. The menu add-in function should respond to NAMM_COMMAND by freeing any resources they allocated during the workstation session.


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
[WM_ADDIN_xxx](/domino-c-api-docs/reference/Symb/WM_ADDIN_xxx)
[NAM_INIT_INFO](/domino-c-api-docs/reference/Data/NAM_INIT_INFO)
[NAM_INITMENU_INFO](/domino-c-api-docs/reference/Data/NAM_INITMENU_INFO)
[NAM_COMMAND_INFO](/domino-c-api-docs/reference/Data/NAM_COMMAND_INFO)
[NAM_CONTEXT_DATA](/domino-c-api-docs/reference/Data/NAM_CONTEXT_DATA)
---
