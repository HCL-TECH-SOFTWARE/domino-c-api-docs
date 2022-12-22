




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



**LDAP\_xxx(1)** **-** Possible
error codes that can be returned.


**----------------------------------------------------------------------------------------------------------**



**#include <ldap.h>**


 **Symbolic Values :**      LDAP\_SUCCESS      -  Success.  

  

      LDAP\_OPERATIONS\_ERROR          -  Operations error.  

  

      LDAP\_PROTOCOL\_ERROR             -  Protocol error.  

  

      LDAP\_TIMELIMIT\_EXCEEDED         -  Time limit exceeded.  

  

      LDAP\_SIZELIMIT\_EXCEEDED         -  Size Limit exceeded.  

  

      LDAP\_COMPARE\_FALSE     -  Compare was false.  

  

      LDAP\_COMPARE\_TRUE      -  Compare was true.  

  

      LDAP\_STRONG\_AUTH\_NOT\_SUPPORTED             -  Strong authentication is
not supported.  

  

      LDAP\_STRONG\_AUTH\_REQUIRED             -  Strong authentication is
required.  

  

      LDAP\_PARTIAL\_RESULTS   -  The error code was never officially supported
in LDAPv2, nor is it supported in LDAPv3. However, we'll keep it around since
practically all clients which bind v2 expect UMich-style referrals.  

  

      LDAP\_REFERRAL    -  Referral. Error new in LDAPv3.  

  

      LDAP\_ADMINLIMIT\_EXCEEDED      -  Admin limit exceeded. Error new in
LDAPv3.  

  

      LDAP\_UNAVAILABLE\_CRITICAL\_EXTENSION         -  Unavailable critical
extension. Error new in LDAPv3.  

  

      LDAP\_CONFIDENTIALITY\_REQUIRED        -  Confidentiality required. Error
new in LDAPv3.  

  

      LDAP\_SASL\_BIND\_IN\_PROGRESS              -  SASL bin in progress. Error
new in LDAPv3.  

  

      LDAP\_NO\_SUCH\_ATTRIBUTE         -  No such attribute. Error indicates an
attribute problem.  

  

      LDAP\_UNDEFINED\_TYPE    -  Undefined type. Error indicates an attribute
problem.  

  

      LDAP\_INAPPROPRIATE\_MATCHING           -  Inappropriate matching. Error
indicates an attribute problem.  

  

      LDAP\_CONSTRAINT\_VIOLATION    -  Constraint violation. Error indicates an
attribute problem.  

  

      LDAP\_TYPE\_OR\_VALUE\_EXISTS    -  Type or value already exists. Error
indicates an attribute problem.  

  

      LDAP\_INVALID\_SYNTAX     -  Invalid syntax. Error indicates an attribute
problem.  

  

      LDAP\_NO\_SUCH\_OBJECT   -  No such object. Error indicates a naming
problem.  

  

      LDAP\_ALIAS\_PROBLEM      -  Alias problem. Error indicates a naming
problem.  

  

      LDAP\_INVALID\_DN\_SYNTAX           -  Invalid distinguished name syntax.
Error indicates a naming problem.  

  

      LDAP\_IS\_LEAF        -  Is leaf. Error indicates a naming problem, not
used in LDAPv3.  

  

      LDAP\_ALIAS\_DEREF\_PROBLEM     -  Alias deref problem. Error indicates a
naming problem.  

  

      LDAP\_INAPPROPRIATE\_AUTH       -  Inappropriate Authentication. Error
indicates a security problem.  

  

      LDAP\_INVALID\_CREDENTIALS       -  Invalid credentials. Error indicates a
security problem.  

  

      LDAP\_INSUFFICIENT\_ACCESS       -  Insufficient access. Error indicates a
security problem.  

  

      LDAP\_BUSY             -  Busy. Error indicates a service problem.  

  

      LDAP\_UNAVAILABLE           -  Unavailable. Error indicates a service
problem.  

  

      LDAP\_UNWILLING\_TO\_PERFORM              -  Unwilling to perform. Error
indicates a service problem.  

  

      LDAP\_LOOP\_DETECT         -  Loop detect. Error indicates a service
problem.  

  

      LDAP\_NAMING\_VIOLATION            -  Naming violation. Error indicates an
update problem.  

  

      LDAP\_OBJECT\_CLASS\_VIOLATION            -  Object class violation. Error
indicates an update problem.  

  

      LDAP\_NOT\_ALLOWED\_ON\_NONLEAF        -  Not allowed on non-leaf. Error
indicates an update problem.  

  

      LDAP\_NOT\_ALLOWED\_ON\_RDN     -  Not allowed on a relative distinguished
name. Error indicates an update problem.  

  

      LDAP\_ALREADY\_EXISTS    -  Already exists. Error indicates an update
problem.  

  

      LDAP\_NO\_OBJECT\_CLASS\_MODS             -  No object class modifications.
Error indicates an update problem.  

  

      LDAP\_RESULTS\_TOO\_LARGE        -  Results too large. Error indicates an
update problem, reserved for CLDAP.  

  

      LDAP\_AFFECTS\_MULTIPLE\_DSAS             -  Affects multiple DSAS. Error
indicates an update problem (LDAPv3).  

  




**Description :**



Many of the
LDAP API routines return result codes, some of which indicate local API errors
and some of which are LDAP resultCodes that are returned by servers.  All of
the result codes are non-negative integers.


 




----------------------------------------------------------------------------------------------------------


 





