---
tags:
  - system_design
draft: false
title: Distributed System
---
A distributed system is a group of independent machine connected together through a network, working together like a unique system. Those machines share tasks to achieve a common goal, in the client side the distributed system looks like a unique system.
The majors challenge of a distributed system include synchronization fault tolerance and failure management.
> [!abstract] 
> "Distributed system is a pandora's box, we should open it only if we have to."
> **- Martin Kleppmann**
## Why make a system distributed ?

**Sometimes it's a mandatory**
Sending a message from your mobile phone to your friend's phone is a distributed system as it involves 3 machines, your phone, your friend's phone and the server whose role is to carry out the communication between the two of you.

**When your need better reliability**
If you have a unique server if this server fails, the whole system is unavailable, if you have a distributed system, even if one node fails the system keeps functioning.

**Blazingly faaast**
With a distributed system you can get data from a nearby node rather than one halfway round the world.

**To solve bigger problems**
The huge size of the world wide web index cannot be stored by a unique computer, even if we could it would be a bad idea, distributed system make sens for 2 main features:

<u>Data distribution</u>: The web index data can be distributed and stored through multiple different machines.

<u>Parallel processing</u>: Once a request is received, it will be shared to the other stakeholders of the network their task will consist to find a consistent response through their index data, in parallel.

<u>Result aggregation</u>: The result of all the stakeholders are then gathered, sorted and merged to produce a finale collection which is sent to the user.

## Why NOT make a system distributed ?
Many trouble could occurs with a distributed system, I classified them in 6 types:

- Communication problems:
	- Latency: Data transmission between nodes can be slow.
	- Packet loss: Data send from a node to another can be lost during the transmission.
	- Bottleneck: Concentration of communication that could saturate a node's link or itself.
- Coordination and synchronization problems:
	- Locks and interlocking: Nodes can wait indefinitely for ressources owned by other nodes.
	- Clock problem: Hard to maintain a common notion of time between nodes.
	- Consensus: Hard to agree to a common value or decision.
- Reliability and availability problems:
	- Node failures: One or many nodes may fail.
	- Network failures: The network itself may experience interruptions or malfunctions 
	- Redundancy: How to store data on multiple nodes to guarantee availability.
- Security problems:
	- DOS attack: Attempts to prevent a system from responding to legitimate requests. 
	- Eavesdropping: Unauthorized eavesdropping between nodes.
	- Tampering: Malicious alteration of data or messages
	- Impersonation: Malicious node pretending to be a legitimate one.
- Consistency and replication problems:
	- Data consistency: Make sure all the copies of data are consistent between nodes.
	- Replication strategy: How and where to replicate data to ensure data fast access and fault tolerance.
- Load balancing problems:
	- Unequal distribution of work: Some nodes could be overload while others could be under-utilized.
	- Dynamic allocation strategy: How to distribute tasks through nodes according to their workload.

Links:
- [[rpc]]