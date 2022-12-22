




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Helv;
 panose-1:2 11 6 4 2 2 2 3 2 4;}
@font-face
 {font-family:"Cambria Math";
 panose-1:2 4 5 3 5 4 6 3 2 4;}
 /\* Style Definitions \*/
 p.MsoNormal, li.MsoNormal, div.MsoNormal
 {margin-top:0cm;
 margin-right:0cm;
 margin-bottom:8.0pt;
 margin-left:0cm;
 line-height:107%;
 font-size:11.0pt;
 font-family:"Calibri",sans-serif;}
.MsoChpDefault
 {font-size:11.0pt;}
.MsoPapDefault
 {margin-bottom:8.0pt;
 line-height:107%;}
 /\* Page Definitions \*/
 @page WordSection1
 {size:612.0pt 792.0pt;
 margin:72.0pt 72.0pt 72.0pt 72.0pt;}
div.WordSection1
 {page:WordSection1;}
-->




**Initial Release 6**



**Symbolic Value : LDAP**



**LDAP\_OPT\_xxx** **-** LDAP
options.


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**


 **Symbolic Values :**      LDAP\_OPT\_API\_INFO          -  Used to retrieve some basic
information about the LDAP API implementation at execution time. Set
optionValue type to LDAPAPIInfo \* for ldap\_get\_option. This option is READ-ONLY
and cannot be set using ldap\_set\_option. See LDAPAPIInfo.  

  

      LDAP\_OPT\_DEREF              -  Determines how aliases are handled during
search. See LDAP\_DEREF\_xxx. Set optionValue type to int \* for ldap\_get\_option.
Set optionValue type to int \* for ldap\_set\_option.  

  

      LDAP\_OPT\_SIZELIMIT         -  A limit on the number of entries to return
from a search. The default value for this option is LDAP\_NO\_LIMIT (see
LDAP\_NO\_LIMIT.) Set optionValue type to int \* for ldap\_get\_option. Set
optionValue type to int \* for ldap\_set\_option.  

  

      LDAP\_OPT\_TIMELIMIT        -  A limit on the number of seconds to spend on
a search. The default value for this option is LDAP\_NO\_LIMIT(see
LDAP\_NO\_LIMIT.) This value is passed to the server in the search request only;
it does not affect how long the API implementation itself will wait locally for
search results. Note that the timeout parameter passed to the ldap\_search\_ext\_s
or ldap\_result functions can be used to specify a limit on how long the API
implementation will wait for results. Set optionValue type to int \* for
ldap\_get\_option. Set optionValue type to int \* for ldap\_set\_option.  

  

      LDAP\_OPT\_PROTOCOL\_VERSION             -  This option indicates the
version of the LDAP protocol used when communicating with the primary LDAP
server. It SHOULD be one of the constants LDAP\_VERSION2 (2) or LDAP\_VERSION3
(3). If no version is set the default is LDAP\_VERSION2 (2). Set optionValue
type to int \* for ldap\_get\_option. Set optionValue type to int \* for
ldap\_set\_option.  

  

      LDAP\_OPT\_SERVER\_CONTROLS   -  A default list of LDAP server controls to
be sent with each request. Set optionValue type to LDAPControl \*\*\* for
ldap\_get\_option. Set optionValue type to LDAPControl \*\* for ldap\_set\_option.  

  

      LDAP\_OPT\_CLIENT\_CONTROLS    -  A default list of client controls that
affect the LDAP session. Set optionValue type to LDAPControl \*\*\* for
ldap\_get\_option. Set optionValue type to LDAPControl \*\* for ldap\_set\_option.  

  

      LDAP\_OPT\_API\_FEATURE\_INFO    -  Used to retrieve version information
about LDAP API extended features at execution time. Set optionValue type to
LDAPAPIFeatureInfo \* for ldap\_get\_option. This option is READ-ONLY and cannot
be set using ldap\_set\_option.  

  

      LDAP\_OPT\_HOST\_NAME    -  The host name (or list of hosts) for the primary
LDAP server (see ldap\_init for the definition of the hostname parameter for the
allowed syntax.) Set optionValue type to char \*\* for ldap\_get\_option. Set
optionValue type to char \* for ldap\_set\_option.  

  

      LDAP\_OPT\_RESULT\_CODE            -  The most recent local (API generated)
or server returned LDAP result code that occurred for this session. Set
optionValue type to int \* for ldap\_get\_option. Set optionValue type to int \*
for ldap\_set\_option.  

  

      LDAP\_OPT\_ERROR\_STRING          -  The message returned with the most
recent LDAP error that occurred for this session. Set optionValue type to char
\*\* for ldap\_get\_option. Set optionValue type to char \* for ldap\_set\_option.  

  

      LDAP\_OPT\_MATCHED\_DN              -  The matched DN value returned with
the most recent LDAP error that occurred for this session. Set optionValue type
to char \*\* for ldap\_get\_option. Set optionValue type to char \* for
ldap\_set\_option.  

  

      LDAP\_OPT\_DEBUG\_LEVEL             -  The debug level to be set. See
LDAP\_DEBUG\_API.  

  

      LDAP\_OPT\_PRIVATE\_EXTENSION\_BASE   -  Specify a new private or
experimental option. Putting this new option in the specified range (0x4000 to
0x7FFF inclusive) will guarantee not to disturb any existing or new standards
track options.  

  




**Description :**



LDAP options
that can be accessed or set using the functions ldap\_get\_option and
ldap\_set\_option.  Type may differ dependant on whether option is to be accessed
or set.


 **See Also :**


**[LDAP\_DEBUG\_API](LDAP_DEBUG_API.md)**


**[LDAP\_DEREF\_xxx](LDAP_DEREF_xxx.md)**


**[ldap\_get\_option](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/611E3525171346C185256F5C00488A5E)**


**[LDAP\_OPT\_xxx](LDAP_OPT_xxx.md)**


**[LDAP\_OPT\_xxx (on/off)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F10E0AB16DF5B1E985256ACC007084E6)**


**[LDAP\_OPT\_xxx (SSL)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/8127200C14817DC185256ACD004F8C5A)**


**[ldap\_set\_option](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/9E2625CD7E72282B85256F5C00488A88)**



----------------------------------------------------------------------------------------------------------


 





