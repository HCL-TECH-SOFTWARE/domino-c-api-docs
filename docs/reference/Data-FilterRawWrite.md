##### Data Type : DSAPI
##### FilterRawWrite - Write content
---
##### #include <dsapi.h>
**Description :**
content - Input/Output parameter. It is a pointer to a buffer that contains the 
data to send to the client. The filter can change the data in place (using the 
same buffer) or allocate a new buffer and fill it.

contentLen Input/Output parameter. It is the number of valid bytes in the 
supplied buffer on input, and/or the number of valid bytes in the buffer on 
output.

reserved - reserved for future use.
**See Also :**
[](D:/md_files/.md)
---
