##### Data Type : Character Manipulation
##### NLS_STATUS - Return code type for National Language Services (NLS) C API functions.
---
##### #include <nls.h>
**Description :**
There are several C API functions that return values of type NLS_STATUS. A 
return value of NLS_SUCCESS indicates that the function completed successfully. 
The value of NLS_SUCCESS is 0.

Example:
if (error = NLSFunction(...))
     return (error);

The C API defines various non-zero NLS_STATUS values, or error codes, that are 
returned by C API functions in response to various error conditions. Specific 
NLS_STATUS error codes are defined in the C API header file nls.h.
**See Also :**
[NLS_find](D:/md_files/NLS_find.md)
[NLS_find_substr](D:/md_files/NLS_find_substr.md)
[NLS_get](D:/md_files/NLS_get.md)
[NLS_isalnum](D:/md_files/NLS_isalnum.md)
[NLS_isalpha](D:/md_files/NLS_isalpha.md)
[NLS_isarith](D:/md_files/NLS_isarith.md)
[NLS_iscntrl](D:/md_files/NLS_iscntrl.md)
[NLS_isdigit](D:/md_files/NLS_isdigit.md)
[NLS_isleadbyte](D:/md_files/NLS_isleadbyte.md)
[NLS_islower](D:/md_files/NLS_islower.md)
[NLS_ispunct](D:/md_files/NLS_ispunct.md)
[NLS_isspace](D:/md_files/NLS_isspace.md)
[NLS_isupper](D:/md_files/NLS_isupper.md)
[NLS_load_charset](D:/md_files/NLS_load_charset.md)
[NLS_put](D:/md_files/NLS_put.md)
[NLS_put_term](D:/md_files/NLS_put_term.md)
[NLS_string_bytes](D:/md_files/NLS_string_bytes.md)
[NLS_string_chars](D:/md_files/NLS_string_chars.md)
[NLS_translate](D:/md_files/NLS_translate.md)
[NLS_unload_charset](D:/md_files/NLS_unload_charset.md)
---
