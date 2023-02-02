##### Symbolic Value : Alarms
##### MQPREFIX_FOR_CLIENT - Prefix for the client name.
---
##### #include <alarm.h>
**Description :**
Clients to the alarms daemon should append the client name to the 
MQPREFIX_FOR_CLIENT string in order to come up with a MQ Name to create before 
registering with the alarms daemon for alarms.  Alarms daemon will use the name 
<MQPREFIX_FOR_CLIENT><ClientName> as a string for opening the MQ for the client 
and send alarms to it.
**See Also :**
[MQCreate](D:/md_files/MQCreate.md)
[Alarm_RegisterInterest](D:/md_files/Alarm_RegisterInterest.md)
---
