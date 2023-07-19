##### Data Type : Menu Add-In
##### NAM_INIT_INFO - Contains information about add-in menu items.
---
```
#include <addinmen.h>
```

**Definition :**

typedef struct
   {
   WORD wStartingID;     /* Input: DLL must add this to its 
                            menu item ID. */
   WORD wMenuItemNumber; /* Input: Ascending ordinal number for 
                                   each call. */

   WORD wMenuID;          /* Output: DLL's Menu ID. */
   char MenuItemName[MAX_ADDIN_MENU_NAME]; /* Output: Text of 
                                                      menu item in LMBCS. */
   } NAM_INIT_INFO;

**Description :**

This structure contains information passed from a menu add-in program to Notes about the menu item to be added, including the menu add-in's menu item ID and name.  The name must be in LMBCS.  A mnemonic may be assigned to the menu item by placing an ampersand (&amp;) next to the desired character in the MenuItemName field of this structure.  This will cause the character that follows the ampersand to be underlined when the Actions menu is displayed and will allow the user to select the menu item with this key.  <br>
<br>
The structure also contains information passed from Notes to the menu add-in, including the Notes assigned id of the first menu item, and how many times this procedure has been called (a value of zero indicates the first time this procedure has been called).<br>
<br>
The menu add-in receives this information when processing the NAMM_INIT message from Notes.


**See Also :**
[NAMM_xxx](/domino-c-api-docs/reference/Symb/NAMM_xxx)
---
