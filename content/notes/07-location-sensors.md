---
title: "07-location-sensors"
tags: 
- lecture
- info305
sr-due: 2023-08-03
sr-interval: 3
sr-ease: 250
---


## Terminology

- Precision vs. Accuracy 
- How practical are systems that are: 
	- Precise but not accurate? 
	- Accurate but not precise?
![Accuracy vs. Precision](https://i.imgur.com/r0dRA8K.png)

- Degrees of Freedom (DoF): 
- How many translational and rotational movements are possible? 
- How many degrees of freedom in 3D space? 
	- 2 DoF? 
	- 3 DoF? 
	- 6 DoF? 
	- 9 DoF? 
	- Unlimited DoF? 
- How many degrees of freedom in 2D space?
![Degrees of Freedom](https://i.imgur.com/uWDwFsO.png)

- (Tri)angulation: 
	- Based on angles between signals 
		- Referred to as angles of arrival 
		- Angle to reference point determined by means of special antennas 
	- Positions of reference points have to be known 
	- 3D-positioning requires three reference points (triangulation)
![Angulation](https://i.imgur.com/8k8aD5h.png)
> [!INFO] if you have two reference points and the angle towards them, you can get the location

- (Tri)lateration 
	- Based on distances between device and reference points 
	- Calculated e.g. by time of arrival (ToA) or signal strength 
	- Positions of reference points have to be known 
	- 3D-positioning requires three reference points (trilateration)
![Lateration](https://i.imgur.com/KQTJDSH.png)
> [!INFO] siimilra to triangulation but you need three points and its calculated using distancees not angles. the distances can be calculated by time of arrival of a signal

## Cell-based
- Positioning based on GSM cell ID 
- Mobile Positioning System (MPS) by Ericsson to improve accuracy 
	- Few changes of infrastructure 
	- No changes of user devices 
1. Cell Global Identity (CGI) for identification of the cell 
	- Uses GSM cell ID 
	- If sector-antennas used position can be narrowed to segment of the circle 
	- Angulation
![](https://i.imgur.com/uzTcwTC.png)
> [!INFO] compute your position based on which cell tower you are connected to. each tower has a unique ID. 
> used by emergency providers, they know where you last logged in

2. GSM based on FDMA (Frequency-division multiple access) and TDMA (Time-division multiple access) 
	- Exact timing required for the synchronization of uplink and downlink 
	- Timing Advance (TA) 
	- Device calculates distance based on signal propagation time 
	- Can be used for positioning in combination with CGI
![|200](https://i.imgur.com/zGMWd9E.png)
![](https://i.imgur.com/U2VHcye.png)
> [!INFO] "towers" use FDMA or TDMA  [[21-data-link-layer#multiple access links and protocols]] Timing advance used for multiple access can be used to calculate time

3. Uplink-Time Difference of Arrival (UL-TOA) 
	- Four base stations needed 
	- Measurement of signal propagation time at base stations 
	- Calculation of position based on lateration 
	- Accuracy 50 – 150m 
	- Network-based location technology, 
		- Can locate any type of mobile phone. 
		- Only available to the owner of the sensor network
![Uplink-Time Difference of Arrival](https://i.imgur.com/CI07t5Z.png)
> [!INFO]biggest drawback is that it is network based - cant be used offline. and you phone doesn't have this data - only the network provider e.g., vodaphone. the police and request vodaphone to send them data for your phone

cell based location summary
- Integrated approach based on existing infrastructure 
- Low costs (for user) 
- Low power draw 
- High availability 
- Works indoor and outdoor (no direct line of sight needed) 
- Information not always available to the user (often only network provider) 
	- Used for “Enhanced 911” 	
- But relatively low accuracy
![](https://i.imgur.com/oLITCmM.png)


- Other cell-based location approaches: WiFi/WLan-cells 
	- Integrated infrastructure approach 
	- WiFi/WLAN (cell-id, lateration, fingerprinting)
![](https://i.imgur.com/VSMfEqW.png)

> [!INFO] fingerprinting.
> want to extend wifi to find location
> create fingerprint for many location in a room - contains all the signals recieved in each spot.
> fingerprints are automatically created.
> fingerprints are aligned between people to find where they are
> used by google.

- Based on already existing WLAN infrastructure, primarily installed for communication purposes 
- Cell ID requires database with mapping WiFi cell ID to GPS or …. (e.g. created by Apple, Google) 
- Lateration 
	- Requires accurate information about access point positions 
	- Measurement of signal strength of various access points 
		- At least three access points have to be available 
		- Measurements are influenced by obstacles like walls 
- Improved approach: Fingerprinting


- Fingerprinting: 
	- 1st Phase: Radio Map Creation (Offline): 
		- Measurements of fingerprints at reference points -> stored in fingerprint DB 
	- Definition of reference points according to accuracy needs and building structure 
- 2nd Phase: Radio Map Usage (Online): 
	- Fingerprint of current position is taken 
	- Search for closest matching reference point on radio map Position taken from that reference point or interpolated
> [!INFO] uses trilateration

- Fingerprint 
	- Location: lat,lon,floor 
	- VisibleAccessPoints{ 
		- Fingerprint DB 
		- AP1: 
			- SSID: eduroam 
			- MAC: 08:17:35:33:5f:80 
			- signal strength: -64 
		- AP2 
			- SSID: VPN/WEB 
			- MAC: 08:17:35:33:5f:81 
			- signal strength: -61 
		- APn o...
![](https://i.imgur.com/vJSirwu.png)
> [!INFO] e.g., when you load google maps, you send this fingerprint. indoors you send access points, if outside you send gps and access points. by combining data they know the rough location of access points. google maps used their database of access points to know where requests are coming from
> if acces point is moved the database can be invalid for a short time
> ∴ position is not always from GPS
> access points dont need to be connected to be transmitted in the fingerprint
> also only work online because you need database query

Fingerprinting services using Wifi 
- ~99% of queries use Google location database (Google Maps Geolocation API) 
	- https://developers.google.com/maps/documentation/geolocation 
	- Access is logged 
	- Used to improve DB 
	- Privacy issues (e.g. private routers) 
- Alternatives (less coverage & accuracy) 
	- OpenCellID 
	- Mozilla Location DB 
- Not available when offline, cell DB too large 
- WLAN cells can move/change - frequent update required
![](https://i.imgur.com/FowUq39.png)

- Cell structure: circular (theory), hexagonal (planning), irregular (reality) 
- Neighbouring cells use different frequencies to minimise interference 
	- Some overlap inevitable 	
- Typical cell sizes: 
	- WiFi: 10m - 100m 
	- 3G (UMTS): 100m - 5km 
	- 2G (GSM): 100m - 35km
![7-cell cluster (commonly used)](https://i.imgur.com/4s8Bv7g.png)
![cell characteristics](https://i.imgur.com/maI9ctM.png)
> [!INFO] shape of cell affected by environment
> 5G has higher density

## Proximity Sensors & Near Field Communication
- Different technologies for sensing proximity or exchanging data (often dual purpose) 
	- Stand-alone infrastructure approaches 
	- Not widely accepted due to special hardware requirements infrastructure costs (for tracking) 
- Conceptually often similar to cell-based approaches but require extra infrastructure
![](https://i.imgur.com/AdxaFMb.png)
> [!INFO] smaller distances
> require their own infrastructure

- WIPS (Infrared) 
	- Beacons installed in the rooms sending unique ID 
	- User’s badges receive signals of local beacons 
	- Received beacon ID is sent to location server via WLAN 
	- Server maps received beacon ID to semantic location which is sent back to the user 
- Active Badge (Infrared) 
	- Users carry badge sending specific user ID 
	- IR-receivers in the rooms receive those signals 
	- Position of user is tracked by central server 
	- Energy-efficient badges (sending short signals of 0,1s each 15s)
![](https://i.imgur.com/y2wweyT.png)
> [!INFO] active badge and WIPS are the opposite of each other
> WIPS - user recieves
> AB - user transmits
> used to track people is large building sometimes: IBM, the pentagon

- Bluetooth Low Energy LE (Bluetooth specification 4.0) 
- Not to confuse with “classic” Bluetooth (e.g. used in headsets or for I/O devices) 
	- Optimized for battery powered sensors 
	- Months or years of battery liftetime 
	- Lower data rate (1MBIT/sec) 
	- Backwards compatible (same frequency and modulation)
![](https://i.imgur.com/BKftnA4.png)
> [!INFO] not classic bluetooth. doesn't send large amounts of data constantly

- Two classes for peripherals: 
	- Beacons (pure static broadcasts: 
		- iBeacon simply broadcasts UUID 
		- Additional data possible on request 
	- Sensors (broad/unicast with sensor data) 
		- Different profiles temperature, gravity, hear rate, pressure, … 
		- Notification possible to avoid polling 
	- Bidirectional communication 
		- Not primarily focus, mostly for setting parameters
> [!INFO] beacons send out theur UUID periodically, does not use much battery, low bandwith
> sensors send out some data with the UUID

- Location and Proximity Sensing using Bluetooth LE 
	- One beacon (e.g. per room) 
		- Pure proximity sensing, looking for strongest signal 
		- E.g. Region monitoring to detect Beacon presence 
	- Many beacons (e.g. per room) 
		- Range calculation using Received Signal Strength Indicator (RSSI) and calibrated transmitter power (txPower = RSSI at 1m) 
		- Trilateration using several beacons but not very accurate 
- Range different for beacons but typically between 20-50m (rarely 100m)
![](https://i.imgur.com/Xqh7cp0.png)
> [!INFO] can locate things using similar techniques to cell towers


- Different protocols on top of Bluetooth LE 
	- iBeacon (Apple) 
		- Broadcasts a UUID 
		- ID is used with database integrated in the app 
		- Further information on request (e.g. range information)
	- Eddystone (Google) 
		- Beacons broacasts information about the beacon (telemetry frame e.g. battery or sensor information) 
		- Beacons broadcasts and redirects to an URL (physical web)

![|200](https://i.imgur.com/jVfJF41.png)

