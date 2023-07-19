##### Data Type : Character Manipulation
##### NLS_STATUS - Return code type for National Language Services (NLS) C API functions.
---
```
#include <nls.h>
```

**Definition :**

typedef WORD NLS_STATUS;

**Description :**

There are several C API functions that return values of type NLS_STATUS. A return value of NLS_SUCCESS indicates that the function completed successfully. The value of NLS_SUCCESS is 0.<br>

<ul>Example:<br>
if (error = NLSFunction(...))<br>
     return (error);</ul>

<ul>The C API defines various non-zero NLS_STATUS values, or error codes, that are returned by C API functions in response to various error conditions. Specific NLS_STATUS error codes are defined in the C API header file nls.h.</ul>



**See Also :**
[NLS_find](/domino-c-api-docs/reference/Func/NLS_find)
[NLS_find_substr](/domino-c-api-docs/reference/Func/NLS_find_substr)
[NLS_get](/domino-c-api-docs/reference/Func/NLS_get)
[NLS_isalnum](/domino-c-api-docs/reference/Func/NLS_isalnum)
[NLS_isalpha](/domino-c-api-docs/reference/Func/NLS_isalpha)
[NLS_isarith](/domino-c-api-docs/reference/Func/NLS_isarith)
[NLS_iscntrl](/domino-c-api-docs/reference/Func/NLS_iscntrl)
[NLS_isdigit](/domino-c-api-docs/reference/Func/NLS_isdigit)
[NLS_isleadbyte](/domino-c-api-docs/reference/Func/NLS_isleadbyte)
[NLS_islower](/domino-c-api-docs/reference/Func/NLS_islower)
[NLS_ispunct](/domino-c-api-docs/reference/Func/NLS_ispunct)
[NLS_isspace](/domino-c-api-docs/reference/Func/NLS_isspace)
[NLS_isupper](/domino-c-api-docs/reference/Func/NLS_isupper)
[NLS_load_charset](/domino-c-api-docs/reference/Func/NLS_load_charset)
[NLS_put](/domino-c-api-docs/reference/Func/NLS_put)
[NLS_put_term](/domino-c-api-docs/reference/Func/NLS_put_term)
[NLS_string_bytes](/domino-c-api-docs/reference/Func/NLS_string_bytes)
[NLS_string_chars](/domino-c-api-docs/reference/Func/NLS_string_chars)
[NLS_translate](/domino-c-api-docs/reference/Func/NLS_translate)
[NLS_unload_charset](/domino-c-api-docs/reference/Func/NLS_unload_charset)
---
