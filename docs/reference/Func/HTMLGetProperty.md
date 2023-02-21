##### Function : HTML
##### HTMLGetProperty - get rotuine for properties.
---
```
#include <htmlapi.h>
STATUS LNPUBLIC HTMLGetProperty(

	HTMLHANDLE  hHTML,
	HTMLAPI_PROP_TYPE  PropertyType,
	void *pProperty);
```
**Description :**

/*
 * PROPERTIES
 * ==========
 * 
 * Information about the converter object is handled with an enumeration
 * and a pair of get/set methods.  The data type passed through the API
 * is void*.  Depending on the enumeration value, the thing pointed to
 * by the void* is cast to the actual type of that property.
 *
 * Note: r = read (only), w = write (only), rw = read/write.
 */

typedef enum
{
	HTMLAPI_PROP_TEXTLENGTH = 0 
	  /* (r DWORD) Number of bytes in output HTML text buffer.
	   This property is valid after calls to HTMLConvertXXX() 
	  */

	,HTMLAPI_PROP_NUMREFS = 1 
	  /* (r DWORD) Number of references in output list of HTML references.
	   This property is valid after callst to HTMLConvertXXX()
	  */

	,HTMLAPI_PROP_USERAGENT_LEN = 3 
	  /* (r DWORD)  Length of the USERAGENT property -- 0 if the USERAGENT
	   property isn't set.
	  */

	,HTMLAPI_PROP_USERAGENT = 4 
	  /* (rw char *)  NULL-terminated string indicating the "browser" being 
used.
	   Some HTML is generated differently depending on browser.
	   (On set, if the string is too big -- gerater than 
MAX_DOMINO_USERAGENT_LENGHT --
	    then ERR_HTMLAPI_INVALID_ARG is returned.
	    On get, buffer must hold at least PROP_USERAGENT_LEN+1 bytes.) 

	   This property must be set before calls to HTMLConvertXXX()
	  */

	,HTMLAPI_PROP_BINARYDATA = 6
	  /* (r BOOL) Indicates (when TRUE) that the results of GetText are 
binary data.
	   "HTMLConvertImage" and "HTMLConvertElement" usualy return binary 
text data.
	    */


	,HTMLAPI_PROP_MIMEMAXLINELENSEEN = 102
	     /* (r DWORD) Indicates the maximum number of LMBCS characters that 
have been
	   encountered between newlines in the generated HTML.

	   This proerty is only valid AFTER a calls to GetText() for a given 
converstion.

	   If the result of the HTMLCovertXXX() command is "binary" data, then 
this property
	   is not calculated, and the value returned is meaningless.

	   Details:
	   When GetText() is called it calculates "line lengths" by counting
	   the number of LMBCS characters between CRLFs.  The maximum line 
length encountered
	   is maitained in this property.

	   Note that if GetText is called multiple times with different 
starting offsets
	   and with a return buffer smaller than the total text length, the 
line length calculations
	   may not be accurate.
	  
	   Example:  assume return buffer contains:
	    1 2 3 4 5 6 CR LF 7 8 9

	    The text length == 11

	    Call GetText with StartingOffset == 0 and *pTextLength == 11, then 
this property
	    will have value of 6

	    Call GetText with StartingOffset == 0 and *pTextLength == 4, then 
this property
	    will have value of 4

	    Next call GetText with StartingOffset == 4 and *pTextLength == 7, 
then this
	    property will have value of 4.

	  */

} HTMLAPI_PROP_TYPE;


**Parameters :**
Input :
hHTML  -  A handle to the converter object

PropertyType  -  The value of the enumeration indicating which property to get/set.

Output :
(routine)  -  Return status from this call.
	NOERROR - Successful.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.


pProperty  -  A pointer to the value.


**Sample Usage :**
```
// get the length of converted text.
 HTMLHANDLE h; // initialized somehow
 DWORD tlength;
 STATUS r;
 r = HTMLGetProperty(h, HTMLAPI_PROP_TEXTLENGTH, &tlength);

```
**See Also :**
[HTMLAPI_PROP_TYPE](/domino-c-api-docs/reference/Data/HTMLAPI_PROP_TYPE)
[HTMLSetHTMLOptions](/domino-c-api-docs/reference/Func/HTMLSetHTMLOptions)
[HTMLSetProperty](/domino-c-api-docs/reference/Func/HTMLSetProperty)
---
