
# reference

https://www.youtube.com/watch?v=YWv608W7O1Y

## lab

- rack rental 

### analog
loop start signaling
- a phone :
	- on hook : circuit is open
	- off hook : circuit is close
- glare effect 
	- just before the 
Ground start signaling
### Digital
 -8000Hz * 8bit = 64000 bps (64k TDM)
- G.711 codec
- T1  : 24 timeslots
Time Division Multiplexing
## signaling
CAS - Channel Associated Signaling
- steals bits from the voice channel
- the 8th bit on every 6th sample
- 24 voice channel
- also called RBS(Robbed Bit Signaling)

CCS - Common Channel Signaling
ISDN PRI(CCS) 
- use D/Delta channel for signaling channel
- only 23 voice channel
### PSTN Term
- Analog Telephone : FXS (Foreign Exchange Station)
- Local Loop(last mile) : link between CPE (Customer Premise) and CO(Central Office)
- Central Office Switch : provide service the customer via local loop
- Private Switch : a telephone switch at a customer premise (PBX)
- Trunk : connection CO Switch/COSwitch or COSwitch/PBX
- SS7 : signaling between CO Switches 
- E.164 - a numbering plan
	- Country Code
	- National Destination Code
	- Subscriber Number
	- NANP - North American Numbering Plan
		- 1 : country code
		- 614 : area code
		- 555: CO Code
		- 1212: station code

### 4 PSTN interface

- Analog POTS lines (FXO)
	- Loop Start/ Ground Start
	- pair of copper wires (tip/ring)
- DID Trunk (Analog)
	- No Long common
	- a single audio conversation at one time
	- one pair of copper wires(tip/ring)
	- uses a wink signal to pass dialed digit information
	- more like FXS connection (to router) than FXO connection
	- 
- ISDN BRI( 2B+D) - basic rate interface
	- two audio channel
	- D 16k
- T1 CAS(24 DSOs)
	- 193Bits per frame :192Bits + 1 Framing Bit
	- use ESF(Extended Super Frame) , got 4 bit (ABCD) for signaling
	- supports Loop Start, Ground Start, E&M Signaling
	- support DNIS (), ANI(caller ID)
- ISDN PRI(CCS) - primary rate interface
	- 23B + D 64K
	- Europe (E1 , 31+D)
- SIP Trunking
	- end to end IP transport
	- different DTMF
	- different codec
	- 
### 5 Audio Codecs
- G.711 
	- 2 Forms : uLaw (us and Japan), aLaw
	- 64k uncompressed
	- 300Hz to 4000Hz
- G.729 - 
	- 8kb/s compressed
- G726 - 32kb/s
- ILBC - Internet Low Bitrate Codec 15.2kb/s

Measuring Voice Quality
Mean Opinion Score - 

### 6 DSP - Digital Signal Processing
analog to digital 
PVDM2-8/16/32/48/64

RTP  
- Real-time Transport Protocol
- RTP rides on top of UDP
- add timestamps and sequence number 
- manage playback speeds

RTCP : RTP Control Protocol
- a performance reporting protocol
- provides key metrics on the RTP stream
	- Packet Count / Delay
	- Packet Loss
	- Jitter (Variations in Delay)

### 7 Network for UC - switched network design
supplying power 
- Inline Power (Pre-Standard)
	- 3500xl switch (cisco 7940, 7960, 7905)
- PoE (Power over Ethernet) 802.3af
	- Cisco 7941 7961 8945
	- 
- Mid-Span Power(Injectors)
- Power Bricks
	```
	show power inline
	switchport mode dynamic desirable
	power inline delay shutdown 20 initial 300
	```
Voice VLAN
- data traffic is untagged
- voice traffic is tagged

CDP - Cisco Discovery Protocol
- to discover the voice vlan to be used
- LLDP - Link Layer Discovery Protocol

IP Phone Boot Process
- Cisco IP phone connect to switch
	- power negotiation 
- spanning tree unblock
	- Voice VLAN is learned via CDP
- Cisco IP phone send DHCP request
	- get DHCP Address with options
		- Options 150 : TFTP boot server (UMUC server)
- download config file from TFTP server
- Contact the call processing server specified in the config file

### 8 Switch Port Config for IP Telephony

```
show vlan
conf t
int fa0/10
switchport voice vlan 20
switchport access vlan 10
spanning-tree portfast

```
### 9 DHCP server config

VLAN 20
Name HQ_PHONES
subnet 10.10.200.0
DHCP pool: 10.10.200.100 -120
TFTP(CUCM/CUCME)  10.10.210.10

IP helper if DHCP on another subnet
```
conf t
ip dhcp excluded-address 10.10.200.1 10.10.200.99
ip dhcp excluded-address 10.10.200.121 10.10.200.254
ip dhcp pool HQ_PHONES
network 10.10.2000.0 255.255.255.0
dns-server 4.2.2.2
default-router 10.10.200.1
option 150 ip 10.10.210.10
#
show ip dhcp binding
debug ip dhcp server events

```
### 10 NTP client config
stratum 
```
show clock
conf t
ntp server 173.13.85.5
show ntp association
show ntp status

```
### 11 CUCM GUI

### 13 Manual Configuring of CUCM Endpoints

CM admin > Device Phone > add new
- type:
- protocol : SCCP, SIP
- MAC ADDR:
- Device Pool
- Phone Button Template
- Device Security profile
- 
- 



> Written with [StackEdit](https://stackedit.io/).

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEwNjM1NDEzMjQsMTcyMjE2NDM0NCwtMT
UwNTkwODMzMywzNjE2Mzk2NzddfQ==
-->