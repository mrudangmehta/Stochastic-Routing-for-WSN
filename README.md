# Stochastic-Routing-for-WSN
This code is implemented in Python. It implements Novel concept of Stochastic Routing for Wireless Sensor Network.
############################################################
############################################################
#####    Mrudang T. Mehta, Himanshu S. Mazumdar   ##########
############################################################
############################################################

*_Published Paper Link_*
 https://tijer.org/tijer/papers/TIJER2311104.pdf
 
# WSN_Router
A Novel Energy Efficient Routing Algorithm for Wireless Sensor Network

Wireless sensor networks (WSNs) have become integral to various applications, necessitating energy-efficient strategies to extend their lifespan. This algorithm addresses the challenge of limited energy availability in wireless sensor nodes, which is particularly critical in applications where direct human intervention is impractical. A novel routing strategy involving both mobile and static sinks is proposed that optimizes retransmissions and puts low battery powered nodes in sleep.

The proposed routing algorithm for the wireless sensor network (WSN), our aim is to optimize the number of retransmissions in order to save the battery power of the nodes. Each node runs this algorithm in distributed edge computing mode and follows the following rules when receives a packet:

Algorithm:

1. If the received packet's destination address is the same as the receiver node's address, the node sends an acknowledge packet back to the source node with the same packet number and a hop count of 0. In the acknowledge packet, the source and destination addresses are interchanged, and the packet type is set to 1.

2. If the received packet's destination address is different, the node generates a time delay that is inversely proportional to the distance of the destination node from the stored localization table as explained in https://github.com/hsmazumdar/WSN_Localizer/tree/main . During this delay, the node enters a "ready to transmit" mode while waiting for the delay to expire.

3. While waiting for the delay time to expire, the receiver node checks for any further received packets. If it receives a packet with the same packet number but an increased hop count, it abandons the "ready to transmit" mode.

4. If no packet is received with the same packet number during the waiting period and its battery life parameter is more then 40%, the receiver node retransmits the packet with an increased hop count and updates the relay node number. It updates battery life parameter after each transmission.

By implementing these rules, the algorithm aims to minimize the number of retransmissions required to deliver packets in the network, thus conserving the battery power of the nodes.

# Equations.
1.	I have assumed a certain number of WSN nodes, say N, are placed randomly in a plain so that each node has at least a few, say M, neighbouring nodes within its transmitting range. Average number of neighbouring nodes M can be calculated as per following equation

![Screenshot (265)](https://github.com/user-attachments/assets/77de09ff-a5bc-4ce8-9f88-d9842f567761)

Parameters:
* N is total number of nodes in WSN area,
* R is range of transmission, 
* L and W are length and width of WSN area.

2.	I assumed that each node participates in a localization procedure using algorithm used in [18, 19] at regular intervals to generate a list of all nodes N with their node-no and location information x and y using received signal strengths. Considering the received signal strength is inversely proportional to the square of the distance from the transmitting node. Given are the reference nodes (x1, y1), (x2, y2), and (x3, y3), and the distances d1, d2, and d3 from the unknown node (x, y) to these reference nodes. Table 4.1 shows the corresponding localization equations.
   
![Screenshot (266)](https://github.com/user-attachments/assets/c0067910-4dc8-4251-b41e-b15155446d3e)



3.	I have assumed that WSN has required connectivity using Poisson distributed node density and transmission range. The connectivity can be estimated using probability mass function P(X=k). Minimum number of neighbouring nodes required within transmission range of a relaying node for reliable connectivity is estimated using equation


![Screenshot (267)](https://github.com/user-attachments/assets/e6528d16-7b6e-4b5a-9829-04d7bead7fe3)


Parameters:
* X is the random variable representing the number of nodes in range at any instance, 
* k is minimum number nodes desired for connectivity, 
* λ is the average number of nodes in transmission range.

4.	I have assumed that any arbitrary node n1 sends a data packet to another arbitrary node n2. 
The node n2 returns an acknowledged packet back to n1. 
The packet headers are shown below. 

Data Packet

![Screenshot (268)](https://github.com/user-attachments/assets/e9e3a79a-4823-442d-bc09-6dbc484b9fa0)



Acknoledgement Packet

![Screenshot (269)](https://github.com/user-attachments/assets/c35f4cf3-75d5-4f33-923e-4bf4998afd7a)



# Quick Start Steps:

1. Download the zip file and unzip in a folder ‘WSN_Router’.
2. Select ‘WsnRoutPwr.py’ file and load in VS Code
3. Install necessary library components in VC Code
4. Run WsnRoutPwr.py to popup 'WSN Auto Routing' application of figure-1
5. Open 'File' menu tab and press 'Draw Nodes (Cnt+d)' tab or press 'Control + d' to populate randomly distributed nodes as shown in figure-1. The default number of nodes are 100 and can be changed using ‘Max Nodes’ tab
6. Select a source and destination node pair from 'File' menu as shown in figure-2 or by simply pressing (Cnt+l)
7. Select and press 'File->Send Pkt (Cnt+s) from 'File' menu as shown in figure-3 or by simply pressing (Cnt+s). This will demonstrate data packet sending from source node to destination node and returning acknowledge packet back to source node using proposed power saving algorithm
8. Select and press 'File->Auto Pkt On (Cnt+a) from 'File' menu as shown in figure-4 to continuously send data packets from random source to random destination. During this process all transmitting nodes will discharge their batteries and show blue at 40% life. Blue nodes will inhibit themselves in relaying packets, however they will send or receive packets for self-use till 10% life.   


![Main](https://github.com/user-attachments/assets/e113ab6d-9b54-441a-a60a-cbd0085289f2)


Figure-1 Simulation of a Wireless Sensor Network (WSN) with interactive GUI to demonstrate a new Novel Energy Efficient Routing Algorithm. Initially populate selected number of nodes, with random placement on canvas using 'File' menu of by simply pressing (Cnt+d)

![SrcDstLine](https://github.com/user-attachments/assets/eb0b43a3-77ad-4436-91e9-0bd6dca4c8d1)

Figure-2 Select a source and destination node pair from 'File' menu or by simply pressing (Cnt+l) 

***************************************  

![SrcDstSend](https://github.com/user-attachments/assets/bec23c79-8ee9-45c3-99bc-7607999cbc7a)

Figure-3 Select and press 'File->Send Pkt (Cnt+s) from 'File' menu or by simply pressing (Cnt+s).

***************************************  

![SrcDstAuto](https://github.com/user-attachments/assets/2d8bf849-7762-4a93-898f-0fe08428efa4)

Figure-4 Select and press 'File->Auto Pkt On (Cnt+a) from 'File' menu to continuously send data packets from random source to random destination. The blue nodes represents low battery and unable to relay paskets.
***************************************  


