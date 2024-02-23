
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
- ISDN BRI( 2B+D)
- T1 CAS(24 DSOs)
- ISDN PRI(23B+D) - primary
- SIP Trunk




> Written with [StackEdit](https://stackedit.io/).

<!--stackedit_data:
eyJoaXN0b3J5IjpbNzE5OTYyODgyLDE2ODkyMjg1OF19
-->