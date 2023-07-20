##### Data Type : Views
##### COLLECTIONPOSITION - Index to a position within a view.
---
```
#include <nif.h>
```

**Definition :**
```
typedef struct {
   WORD  Level;   /* # levels -1 in tumbler (top level = 0)*/
   BYTE MinLevel; /* MINIMUM level that this position */
                  /* is allowed to be nagivated to. */
                  /* This is useful to navigate a */
                  /* subtree using all navigator codes. */
                  /* This field is IGNORED unless */
                  /* the NAVIGATE_MINLEVEL flag is */
                  /* enabled (for backward compatibility) */
   BYTE MaxLevel; /* MAXIMUM level that this position */
                  /* is allowed to be nagivated to. */
                  /* This is useful to navigate a */
                  /* subtree using all navigator codes. */
                  /* This field is IGNORED unless */
                  /* the NAVIGATE_MAXLEVEL flag is */
                  /* enabled (for backward compatibility) */
   DWORD Tumbler[MAXTUMBLERLEVELS]; /* Current tumbler (1.2.3, etc) */
                  /* (an array of ordinal ranks) */
                  /* (0th entry = top level) */
                  /* Actual number of array entries is Level+1 */
} COLLECTIONPOSITION;
```

**Description :**

This structure is used to specify the hierarchical, index position of an item (or category) within a View(collection).<br>
<br>
Level = (number of levels in tumbler - 1)<br>
<br>
Tumbler is an array of ordinal ranks within the view; with the first (0) entry referring to the top level.<br>
<br>
For example, consider the following non-Domino Outline Scheme :<br>
<br>
I.  First Main Category<br>
        A.  First sub-category under I<br>
        B.  Second sub-category under I<br>
II.  Second Main Category<br>
        A.  First sub-category under II<br>
            1.  First item under  II.A<br>
            2.  Second item under II.A<br>
        B.  Second sub-category under II<br>
        C.  Third sub-category under II<br>
III.  Third Main Category<br>
<br>
With this example, [2; II.A.2] refers to the &quot;Second item under II.A.&quot;<br>
Similarly, [0; III] refers to the &quot;Third Main Category.&quot;<br>
<br>
Finally, it should be noted that [2; I.B.1], [1; I.C], and [3; II.A.1] are all NOT valid positions.<br>
<br>
[2; I.B.1] because the &quot;Second sub-category under I&quot; has no items.<br>
[1; I.C] because there is no &quot;Third sub-category under I&quot;, and<br>
[3; II.A.1] because the value of Level (3) shows four levels<br>
should be represented in the Tumbler and there are only three.<br>



**See Also :**
[NIFFindByKey](/domino-c-api-docs/reference/Func/NIFFindByKey)
[NIFFindByName](/domino-c-api-docs/reference/Func/NIFFindByName)
[NIFReadEntries](/domino-c-api-docs/reference/Func/NIFReadEntries)
---
