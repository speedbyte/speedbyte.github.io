---
layout: post
title: "bosch"
date: 1970-01-01
---

===== RADAR =====


New combined Department of Defense (DOD) and Federal Aviation
Administration (FAA) S Band fan-beam track-while-scan Digital Airport Surveillance
Radar (DASR) ASR-11. This primary system uses a 17-kW peak-power solid-state
‘‘bottle’’ transmitter. Mounted on top of ASR-11 primary radar antenna is L-band open-
array rectangular antenna of colocated Monopulse Secondary Surveillance Radar
(MSSR). Up to 200 of these systems to be emplaced around the United States. (Photo
courtesy of Raytheon Company.)

which beam - fan beam

scan angle - 20 deg azimuth, 8 deg elevation

Which band - S band, X band, L band

radar type - phased array radar

Antenna type - open array rectangular antenna, dual beam cosecant squared antenna

What can the radar do? track-while-scan ( TWS ) , radar scans the target and the tracking algorithm tracks the targets by estimating the next position and thereby associating the ids

Combination of various radars mounted one on another. 

Power - 17KW peak power solid-state bottle transmitter, 25KW pea power solid state bottled transmitter

In order to make associations ( assigning the ids from frame to frame ), it is required to estimate the position based on its position and speed. 
If we have the position and the velocity of objects from the first scan, then we can predict the distance target 1 cuold move during the scan.to-scan period and as a result have an estimate
of the targets future position.
Since even the position and velocity of the targets are not known accurately even during the first scan, the error during the prediction has a window of a standard deviaiton. Nevertheless, a simple
system dynamic model can be created with the predicted position  = initial position + scanperiod * velocity ( assuming constant velocity and assuming that the target is on the radial range of the radar i.e direclty perpendicular in the beam )

The system can be extended to real, multi dimensional world where we have changing target velocities.

Filters like kalman filter are used to obtain running estimates of position and velocity and which in turn helps toassociate the ids.

Precision guidance of aircraft onto the runway during final approach.

Kalman tracking algorithm to accuratel< predict the impact of missiles as well as determining their launch sites.

limited scan electronicall steered ( phase-phase ) phased array radar

short range lmited scan electronically scanned ( phase - frequency )

Laser radar has much more accuracy than a microwave radar

SAR - Synthetic Aperture Radar
GMTI - Ground Moving Target Indicator Radar
Phased Array Radar



===== uncategorized =====

nzfsresize -i -f -v /dev/sda2
ntfsresize --force --force --no-action /dev/sda2

The Address Resolution Protocol is a request-response protocol whose messages are encapsulated by a link layer protocol. It is communicated within the boundaries of a single network, never routed across internetworking nodes. This property places ARP into the link layer of the Internet protocol suite.[2]

convert -list format
convert -list configure


cisco ras.uni-tuebingen.de

ip route is the newer version. route is an ancient tool and is taken over by ip route handled by the package iproute20

journalctl \_COMM=xxx --since=today

0.0.0.0 destination gateway means that the hop is 0 i.e the devices are locally connected.

0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 cscotun0
0.0.0.0         192.168.178.1   0.0.0.0         UG    256    0        0 wlp0s20f3
0.0.0.0         192.168.178.1   0.0.0.0         UG    20600  0        0 wlp0s20f3
134.2.184.0     0.0.0.0         255.255.254.0   U     0      0        0 cscotun0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 cscotun0
192.168.0.0     192.168.178.1   255.255.0.0     UG    0      0        0 wlp0s20f3
192.168.178.0   0.0.0.0         255.255.255.0   U     600    0        0 wlp0s20f3
192.168.178.1   0.0.0.0         255.255.255.255 UH    0      0        0 wlp0s20f3
193.197.62.142  192.168.178.1   255.255.255.255 UGH   0      0        0 wlp0s20f3


netstat -rn 

