---
layout: post
title: "hs_esslingen_lectures_distributed_real_time_systems"
date: 1970-01-01
---



In real time systems, there is a trade off between timeliness and reliability. Some of the basic requirements for a communication system is low protocol latency with minimal jitter, the establishment of a global time base, fast error detection at the receiver and the need for temporal error containment. The BMTS is at the waist that transports a message from the sender to a set of receiver within a given latency and with a given reliability. The protocol above BMTS takes care of request-response formats and the protocols below BMTS implements the transport service.

From the temporal point of view, i.e when a message is ready to be sent there are 3 different communication services: event triggered communication ( like CAN, Ethernet ) , time triggered communication ( like FlexRay, TTEthernet )  and rate constrained communication ( such as ARINC 629 and ARINC 684 ).  In a TT communication system, the start of theele message transmission is triggered exactly when the global time reaches the start of the cycle and hence TT systems are deterministic.

In case the sender produces more messages in an event triggered communication system, than the BMTS can handle, either back pressure is excercised on the sender or the messages are lost.  In a rate constrained message, the messages should not exceed a maximum worst case transport latency. In the time triggered architecture, sender and receiver agree a priori on the exact instants when the messages are sent and received.

Short Message Transport Latency, Minimal Jitter and Clock Syncronization are the most important differences between a real time communication system and a non real time communication system. It is upto the communication system to establish such a global time and to synchronize the nodes, eg , by following the IEEE 1588 standard for clock synchronization. Temporal accuracy can be only checked if the duration between the instant of observation of an RT entity, observed by the sensor node and the instant of use, determined by the actuator node, can be measured.

Achieving reliability can be achieved, if replicated messages are sent on diverse channels ( eg frequency hopping in wireless system ), possibly at different times. The reliability can also be increased by retransmission of the lost messages ( time redundancy ), but this kind of method would increase the latency and hence makes the system non �~@~S real time communication.

There are two methods �~@~S PAR and end to end acknowledgement. In the end to end acknowledgement, the ack is send by a different node back to the sender. The success of the transmission of the message can be reported by a node other than to which the message was sent. Also, where sensors send data periodically, a retransmission can be avoided because the RT image is already updated with the new sensor value. Hence a old sensor value arent of much importance any more.

Temporal fault containment should be done by erecting temporal firewallls that contains the temporal faults of a component, so that the communication among the components that are not directly affected by the faulty  component is not compromised. The error is detected if the message has been corrupted can be checked by checking the CRC field of the redundant information. Faults such as cut wires should also be detected and safe measures should be taken to avoid any catastrophe. For example, if a wire is cut and no communication takes place then the system should be signalled to shut down to avoid any kind of mishap. Any kind of failure should also be reported to all the nodes that were part of the membership.

Physical Fault Isolation: The nodes in the fault tolerant units are placed in such a manner so that a lightning stroke, will not disable all the nodes.

Physical Performance Limitation: Due to the limit in speed of the light, the transmission of a signal from one end to the other end takes a finite amount of time. This delay is called the propagation delay and the number of bits that can stay on the bus during this time is called the bitlength. The bandwidth is the number of bits that can be transferred within one second. The data efficiency of any media access protocol depends on the message length. If the message length is too less, then it is a waste of the bandwidth.

Flowcontrol : Explicit, where there is an explicit acknowledge of every message by the receiver; Implicit, where the acknowledge lies in the response of the receiver; the besteffort flow control, where a buffer is provided in case the link for the further transport of messages to the final receiver is not available. Example is switched Ethernet. In case buffer overflows, backpresssure is exercised or messages are dropped; the Back-pressure flow control, where the sender is forced to delay sending further messages until the overload condition has disappeared; the rate-constrained flow control, where the receiver will accept all the messages as long as the sender rate remains below the agreed maximum.

ARINC Rate constrained flow control and rate-constrained communication system is used in the aircrafts. Recently TT Ethernet is undergoing standardization.

Manchester coding,  NRZ are some of the methods to transmit data.
~                                                                   