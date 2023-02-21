##### Function : String
##### Soundex - Convert a string into its Soundex equivalent.
---
```
#include <misc.h>
void LNPUBLIC Soundex(

	const char far *String,
	WORD  StringLength,
	char far *retSoundexString);
```
**Description :**

This function takes a string, typically a user's last name or a server name, 
the length of that string, and converts it into an equivalent Soundex string.

Soundex strings have the property that if two character strings sound the same 
but are spelled differently, they both convert to identical Soundex strings.  

Soundex only processes the first part of the input string. Soundex ("first 
last") will return the soundex equivalent of "first" and stop at the first 
white space. 

The soundex string consists of a leading character followed by a three digit 
ordinal number.  Different names that sound alike usually yield the same 
soundex string.  The Soundex algorithm is defined in Knuth Computer Algorithms 
vol 3 page 392.  The algorithm strips off the first character of the name and 
holds it.  Then it takes the remaining characters, strips out all the vowels, 
and converts the remaining (all consonant) characters to an ordinal 3-digit 
number.  The concatenation of the first character with the 3 digit number is a 
soundex string.  This algorithm does a reasonable job of yielding the same 
soundex string for different spellings of the same name.  For example, "Perlin" 
and "Perlmutter" both yield the same soundex string, "P645".

Notes takes all Person documents in the Address book or Domino Directory 
(Server's Address book) and computes the soundex strings of just the last 
names. Then it builds a view ($USERS) that categorizes all Person documents by 
FirstName, LastName, FullName, ShortName, and Soundex(LastName).  When the  
Mailer can't find an exact match for a name specified on the SendTo, CC, or 
BlindCC list, it computes the soundex string for that name and presents the 
user with a choice of all the other names that fall under that soundex string 
category.

**Parameters :**
Input :
String  -  A string containing the name you wish to use to generate the Soundex string.  The string does not have to be null-terminated.

StringLength  -  A WORD containing the string's length.

Output :
(routine)  -  None.


retSoundexString  -  The address of the text buffer in which the Soundex string (null terminated) is returned.


**See Also :**
[NIFFindByKey](/domino-c-api-docs/reference/Func/NIFFindByKey)
[NIFFindByName](/domino-c-api-docs/reference/Func/NIFFindByName)
---
