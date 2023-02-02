##### Data Type : Views
##### COLLATION - Defines sorting information for the columns in a view note.
---
##### #include <nifcoll.h>
**Description :**
This structure is used to specify the manner in which data in a view is 
sorted.  The COLLATION structure, along with its associated COLLATE_DESCRIPTOR 
structures and character strings, comprise the $Collation item in a view note.

BufferSize = total size in bytes of the $Collation item.
Items          = number of columns in the view that are sorted or categorized.
Flags         =  Optional.  May be set to a COLLATION_FLAG_xxx value.  
Otherwise, set to 0.
Signature = COLLATION_SIGNATURE.

These values are immediately followed by an array of COLLATE_DESCRIPTOR 
structures, one for each sorted column.  The collation descriptor array is 
followed by a sequence of packed character strings relevant to those 
descriptors.  See the definition of COLLATE_DESCRIPTOR for more details.

**See Also :**
[COLLATE_DESCRIPTOR](D:/md_files/COLLATE_DESCRIPTOR.md)
[COLLATION_FLAG_xxx](D:/md_files/COLLATION_FLAG_xxx.md)
---
