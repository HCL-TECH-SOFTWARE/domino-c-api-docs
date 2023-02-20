##### Data Type : Character Manipulation
##### NLS_STATUS - Return code type for National Language Services (NLS) C API functions.
---
```
#include <nls.h>
```
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
[NLS_find](/reference/Func/NLS_find)
[NLS_find_substr](/reference/Func/NLS_find_substr)
[NLS_get](/reference/Func/NLS_get)
[NLS_isalnum](/reference/Func/NLS_isalnum)
[NLS_isalpha](/reference/Func/NLS_isalpha)
[NLS_isarith](/reference/Func/NLS_isarith)
[NLS_iscntrl](/reference/Func/NLS_iscntrl)
[NLS_isdigit](/reference/Func/NLS_isdigit)
[NLS_isleadbyte](/reference/Func/NLS_isleadbyte)
[NLS_islower](/reference/Func/NLS_islower)
[NLS_ispunct](/reference/Func/NLS_ispunct)
[NLS_isspace](/reference/Func/NLS_isspace)
[NLS_isupper](/reference/Func/NLS_isupper)
[NLS_load_charset](/reference/Func/NLS_load_charset)
[NLS_put](/reference/Func/NLS_put)
[NLS_put_term](/reference/Func/NLS_put_term)
[NLS_string_bytes](/reference/Func/NLS_string_bytes)
[NLS_string_chars](/reference/Func/NLS_string_chars)
[NLS_translate](/reference/Func/NLS_translate)
[NLS_unload_charset](/reference/Func/NLS_unload_charset)
---
