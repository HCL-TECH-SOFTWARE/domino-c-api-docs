##### Data Type : Views
##### COLLECTIONPOSITION - Index to a position within a view.
---
##### #include <nif.h>
**Description :**
This structure is used to specify the hierarchical, index position of an item 
(or category) within a View(collection).

Level = (number of levels in tumbler - 1)

Tumbler is an array of ordinal ranks within the view; with the first (0) entry 
referring to the top level.

For example, consider the following non-Domino Outline Scheme :

I.  First Main Category
        A.  First sub-category under I
        B.  Second sub-category under I
II.  Second Main Category
        A.  First sub-category under II
            1.  First item under  II.A
            2.  Second item under II.A
        B.  Second sub-category under II
        C.  Third sub-category under II
III.  Third Main Category

With this example, [2; II.A.2] refers to the "Second item under II.A."
Similarly, [0; III] refers to the "Third Main Category."

Finally, it should be noted that [2; I.B.1], [1; I.C], and [3; II.A.1] are all 
NOT valid positions.

[2; I.B.1] because the "Second sub-category under I" has no items.
[1; I.C] because there is no "Third sub-category under I", and
[3; II.A.1] because the value of Level (3) shows four levels
should be represented in the Tumbler and there are only three.

**See Also :**
[NIFFindByKey](D:/md_files/NIFFindByKey.md)
[NIFFindByName](D:/md_files/NIFFindByName.md)
[NIFReadEntries](D:/md_files/NIFReadEntries.md)
---
