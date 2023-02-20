##### Symbolic Value : Item (Field) Information
##### TYPE_xxx [USERID] - Item Data Type - V1/V2 Author
---
```
#include <nsfdata.h>
```
**Description :**

Notes V1/V2 Author fields contain a text user name followed by an 8 byte 
license ID. Notes 2.1 and earlier created items of TYPE_USERID when saving data 
from a field designed as data type "Document Author".  Notes 3.0 and later no 
longer uses the "Document Author" data type, or the item type TYPE_USERID.

In an item of TYPE_USERID, all but the last 8 bytes of the structure contains 
the user name, which may be printed as text.  The last 8 bytes contain the 
license ID, as follows:

typedef struct {
   char      Author[sizeof(user_name)];
   LICENSEID License;
} V1V2_Author;

You may obtain the user name and license ID from SECKFMUserInfo.  The user name 
text may optionally contain the name of the user plus a list of server names in 
parentheses.

Notes 3.0 or later recognizes items of TYPE_USERID as a Notes V1/V2 Author, 
field but does not save items with this type.

**Sample Usage :**
```
   STATUS      error;
    char        szDocAuthor[MAX_USERNAME_LEN];
    LICENSEID   License;
    char        achUSERID[MAX_USERNAME_LEN + sizeof(LICENSEID)];

    /* Get Current UserID and store it */
    if (error = SECKFMUserInfo(KFM_ui_GetUserInfo,
                           szDocAuthor,&License))
    {
        printf ("Error: unable to get info about current user.\n");
        return (error);
    }
                
    memcpy(achUSERID, szDocAuthor, strlen(szDocAuthor));
    memcpy(&achUSERID[strlen(szDocAuthor)],&License,
                       sizeof(LICENSEID));

    if (error = NSFItemAppend(hNote,ITEM_SUMMARY,
                        "From", strlen("From"),
                        TYPE_USERID, achUSERID,
                        (DWORD) (strlen(szDocAuthor) +
                        sizeof(LICENSEID))))
    {
        printf ("Error: unable to set From item in note.\n");
        return (error);
    } 
```
**See Also :**
[ITEM_xxx [NAMES]](/reference/Symb/ITEM_xxx [NAMES])
[ITEM_xxx [READERS]](/reference/Symb/ITEM_xxx [READERS])
[ITEM_xxx [READWRITERS]](/reference/Symb/ITEM_xxx [READWRITERS])
[NAMES_LIST](/reference/Data/NAMES_LIST)
[TYPE_xxx](/reference/Symb/TYPE_xxx)
---
