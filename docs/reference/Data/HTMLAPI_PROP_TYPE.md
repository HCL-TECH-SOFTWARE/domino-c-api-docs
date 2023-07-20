##### Data Type : HTML
##### HTMLAPI_PROP_TYPE - Information about the converter object is handled with an enumeration and a pair of get/set methods.
---
```
#include <htmlapi.h>
```

**Definition :**
```
typedef enum
{
	HTMLAPI_PROP_TEXTLENGTH = 0 
	,HTMLAPI_PROP_NUMREFS = 1 
	,HTMLAPI_PROP_USERAGENT_LEN = 3 
	,HTMLAPI_PROP_USERAGENT = 4 
	,HTMLAPI_PROP_BINARYDATA = 6
	,HTMLAPI_PROP_MIMEMAXLINELENSEEN = 102 

} HTMLAPI_PROP_TYPE;

```

**Description :**

Information about the converter object is handled with an enumeration and a pair of get/set methods.  The data type passed through the API is void*.  Depending on the enumeration value, the thing pointed to by the void* is cast to the actual type of that property. The symbols(r &amp; w) in the parentheses below represent whether this property can be read(r) or write(w)<br>
<br>
<br>
	HTMLAPI_PROP_TEXTLENGTH = 0	<br>
			/* (r DWORD)	Number of bytes in output HTML text buffer.<br>
				This property is valid after calls to HTMLConvertXXX() <br>
			*/<br>
<br>
	,HTMLAPI_PROP_NUMREFS = 1	<br>
			/* (r DWORD)	Number of references in output list of HTML references.<br>
				This property is valid after callst to HTMLConvertXXX()<br>
			*/<br>
<br>
	,HTMLAPI_PROP_USERAGENT_LEN = 3 <br>
			/* (r DWORD)  Length of the USERAGENT property -- 0 if the USERAGENT<br>
				property isn't set.<br>
			*/<br>
<br>
	,HTMLAPI_PROP_USERAGENT = 4 <br>
			/* (rw char *)  NULL-terminated string indicating the &quot;browser&quot; being used.<br>
				Some HTML is generated differently depending on browser.<br>
				(On set, if the string is too big -- gerater than MAX_DOMINO_USERAGENT_LENGHT --<br>
				 then ERR_HTMLAPI_INVALID_ARG is returned.<br>
				 On get, buffer must hold at least PROP_USERAGENT_LEN+1 bytes.) <br>
<br>
				This property must be set before calls to HTMLConvertXXX()<br>
			*/<br>
<br>
	,HTMLAPI_PROP_BINARYDATA = 6<br>
			/* (r BOOL) Indicates (when TRUE) that the results of GetText are binary data.<br>
				&quot;HTMLConvertImage&quot; and &quot;HTMLConvertElement&quot; usualy return binary text data.<br>
		   */<br>
<br>
<br>
	,HTMLAPI_PROP_MIMEMAXLINELENSEEN = 102<br>
		    /* (r DWORD) Indicates the maximum number of LMBCS characters that have been<br>
				encountered between newlines in the generated HTML.<br>
<br>
				This proerty is only valid AFTER a calls to GetText() for a given converstion.<br>
<br>
				If the result of the HTMLCovertXXX() command is &quot;binary&quot; data, then this property<br>
				is not calculated, and the value returned is meaningless.<br>
<br>
				Details:<br>
				When GetText() is called it calculates &quot;line lengths&quot; by counting<br>
				the number of LMBCS characters between CRLFs.  The maximum line length encountered<br>
				is maitained in this property.<br>
<br>
				Note that if GetText is called multiple	times with different starting offsets<br>
				and with a return buffer smaller than the total text length, the line length calculations<br>
				may not be accurate.<br>
			<br>
				Example:  assume return buffer contains:<br>
					1 2 3 4 5 6 CR LF 7 8 9<br>
<br>
					The text length == 11<br>
<br>
					Call GetText with StartingOffset == 0 and *pTextLength == 11, then this property<br>
					will have value of 6<br>
<br>
					Call GetText with StartingOffset == 0 and *pTextLength == 4, then this property<br>
					will have value of 4<br>
<br>
					Next call GetText with StartingOffset == 4 and *pTextLength == 7, then this<br>
					property will have value of 4.<br>
<br>
			*/


**Sample Usage :**
```
 rslt = HTMLGetProperty(hHTML, HTMLAPI_PROP_BINARYDATA, &bBinary);
 if(rslt = HTMLGetProperty(hHTML, HTMLAPI_PROP_TEXTLENGTH, &wTextLength))
{
	PrintLogInfo("HTML Get Image Binary Length fail");
	//PrintAPIError(rslt);
	return rslt;
}
```

**See Also :**
[HTMLGetProperty](/domino-c-api-docs/reference/Func/HTMLGetProperty)
[HTMLGetText](/domino-c-api-docs/reference/Func/HTMLGetText)
[HTMLSetProperty](/domino-c-api-docs/reference/Func/HTMLSetProperty)
---
