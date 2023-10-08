# Network-Security
<h1><center>

 Network Security : Swich Security configuration

</center></h1>

<h3>
![image](https://github.com/ahmad-shakla/Network-Security/assets/66517841/fb9cb0e9-e5b9-40d3-9390-65e8d8fac2fe)



In most cases while you operate on a Cisco Switch chances that you have a low security configurations are high and in this lab i'm going to explain how to secure your switch.


1.Shutdown

after you finish creating your VLANs some attackers might use some of the open ports on your switch to do malicious activates  your network and to block them you'll need to shutdown all your unused ports here are the configurations you need :
</h3>
<h4>
<b>
switch>en

switch#conf t

switch(config)#int range (all the ranges of your unused ports)

switch(config-if-range)#shutdown

 </b>
 </h4>
<h3>
2.BlackHoles

if you still feel like you need to add more security you can add all of your unused ports into a vlan and name it BlackHole and it usually comes with the number 999 here is how to do so:

 </h3>
<b><h4>
switch>en

switch#conf t

switch(config)#vlan 999

switch(config-if)#name BlackHole

switch(config-if)#exit

switch(config)#int range (all the ranges of your unused ports)

switch(config-if-range)#sw mode access

switch(config-if-range)#sw access vlan 999

switch(config-if-range)#shutdown
</h4></b>
 
<h3>
and now we have solved any problems that comes form outside our Vlan but what if an attacker decided to take the cable off one of our devices and put it inside his laptop. fortunately, there is a way to protect from this types of attacks to and its called violation.We basically will go inside each used ports and add some violations to the switch and violations in a Cisco switch are ordered into tree types: 1-shutdown 2-restrict 3-protect

here's how to do a violation to a port on your switch

 </h3>

 <h4><b>

switch>en

switch#conf t

switch(config)#int range (all the ranges of your used ports)

switch(config-if-range)#sw port-security vio shut

</b></h4>

<h3>
and finally we have the Mac-address security

 </h3>

<h4><b>
switch>en

switch#conf t

switch(config)#int (any device on your interface)

switch(config-if)#sw port-security mac-add sticky
</b></h4>
 
<h3>
the switch will learn the right mac address to connect to and to do so you need to ping the device you have added the configurations to

 

Also make sure to allow only a specific amount of numbers of mac addresses 
</h3>
<h4><b>
switch>en

switch#conf t

switch(config)#int (any device on your interface)

switch(config-if)#sw port-sec max (number of your own)
</b></h4>

end.
