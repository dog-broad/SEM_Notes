# Explain three way handshaking connection mechanisms in TCP(connection establishment,Data Transfer, connection Relase)

The three-way handshake is a method used by TCP to establish a connection between a client and a server. It involves three steps:

### 1. Connection Establishment

1. **Step 1: Client sends SYN (Synchronize) to Server**
   - The client initiates the connection by sending a SYN packet to the server.
   - The SYN packet contains a random initial sequence number (ISN) chosen by the client to start the communication.

2. **Step 2: Server Responds with SYN-ACK (Synchronize-Acknowledge) to Client**
   - Upon receiving the SYN packet, the server responds with a SYN-ACK packet back to the client.
   - The SYN-ACK packet contains its own random initial sequence number (ISN) as well as an acknowledgment number equal to the client's ISN incremented by 1.
   - The server also reserves buffer space and resources to handle the upcoming connection.

3. **Step 3: Client Sends ACK (Acknowledge) to Server**
   - Finally, the client acknowledges the server's response by sending an ACK packet.
   - The ACK packet contains the acknowledgment number equal to the server's ISN incremented by 1.
   - At this point, the connection is considered established, and both the client and server can begin exchanging data.

At this point, the connection is considered established, and both client and server are ready to exchange data.

### 2. Data Transfer

After the connection establishment, the client and server can exchange data using TCP. Here's how data transfer works:

1. **Sending Data (Client to Server)**
   - The client sends data in segments, each segment containing a sequence number.
   - The server receives the segments and sends an acknowledgment (ACK) back to the client, acknowledging the receipt of data.
   - If the client doesn't receive an ACK for a segment within a timeout period, it retransmits the data to ensure reliability.

2. **Receiving Data (Server to Client)**
   - The server sends data in segments to the client, each segment with its own sequence number.
   - The client acknowledges the received segments by sending ACK packets back to the server.
   - If the server doesn't receive an ACK for a segment within a timeout period, it retransmits the data to ensure reliability.

### 3. Connection Release

When either the client or the server wants to close the connection, a connection release process is initiated:

**Step 1: Initiating Connection Release**
1. The client or server that wants to close the connection sends a FIN (Finish) packet to the other side.
2. The FIN packet indicates the party's intention to terminate the connection.

**Step 2: Acknowledgment of FIN**
1. The receiving party acknowledges the FIN packet by sending an ACK packet back.

**Step 3: Finalizing Connection Release**
1. The receiving party may also send its own FIN packet to indicate its intention to close the connection.
2. The other party acknowledges the FIN packet with an ACK.

Once both sides have exchanged FIN and ACK packets, the connection is considered closed gracefully.

The three-way handshake and connection release mechanisms in TCP ensure reliable and orderly communication between client and server, while the data transfer process guarantees that data is successfully delivered and received.



# Discuss in detail about TCP Connection Management Modeling

![](img/2023-08-04-04-30-48.png)

![](img/2023-08-04-04-31-05.png)

In each of the 11 states shown in above table, some specific events are legal.

Corresponding to every legal event some action may be taken, but if some other event happens, then error is reported.

Each Connection is always in the CLOSED State Initially.

It comes out of this state when it does either the passive open (LISTEN) or an active open (CONNECT).

A connection is established, if the other side does the opposite and the state becomes ESTABLISHED.

When the both the sides initiate a connection release the connection is terminated and the state returns to CLOSED state.


# DHCP - Dynamic Host Configuration Protocol

**Notes on DHCP**

- DHCP stands for Dynamic Host Configuration Protocol.
- It is a network protocol used to automatically assign IP addresses and other network configuration parameters to devices on a network.
- DHCP is widely used in local area networks (LANs) to simplify the process of IP address management.
- It operates on the client-server model, where a DHCP server manages a pool of IP addresses and leases them to DHCP clients.
- The DHCP process involves four main steps: Discover, Offer, Request, and Acknowledge (DORA).

**Understanding DHCP**

DHCP is essential for the proper functioning of modern networks. Without DHCP, network administrators would need to manually assign IP addresses to each device, which can be time-consuming and prone to errors. DHCP automates this process, making it easier to manage IP address allocation and configuration.

**What DHCP Does:**

1. **IP Address Allocation:** DHCP dynamically assigns IP addresses to devices on a network. When a device joins the network, it sends a DHCP Discover message to find an available IP address. The DHCP server responds with a DHCP Offer, providing the client with an IP address lease.

2. **Subnet Mask and Default Gateway:** DHCP not only provides IP addresses but also supplies subnet masks and default gateway information to clients. These parameters are crucial for proper routing of data packets within the network.

3. **DNS Server Configuration:** DHCP can also provide clients with the IP addresses of Domain Name System (DNS) servers. This ensures that devices can resolve domain names into IP addresses for internet connectivity and name resolution.

4. **Lease Management:** IP addresses assigned by DHCP are not permanent. Instead, they are leased for a specific duration. Before the lease expires, the client can request a lease renewal from the DHCP server. This allows the network to efficiently manage IP address allocation and adapt to changes in the network.

**How DHCP Works:**

The DHCP process involves the following steps:

1. **Discover:** When a device connects to a network and needs an IP address, it broadcasts a DHCP Discover message on the network. The Discover message asks for an available DHCP server.

2. **Offer:** When a DHCP server receives the Discover message, it checks its pool of available IP addresses. If an address is available, the DHCP server sends a DHCP Offer message to the requesting client, offering the available IP address for lease.

3. **Request:** Upon receiving the DHCP Offer, the client may receive multiple offers from different DHCP servers. It then selects one of the offers and sends a DHCP Request message to the chosen server, indicating its acceptance of the offered IP address.

4. **Acknowledge:** The DHCP server that receives the DHCP Request message acknowledges the client's acceptance by sending a DHCP Acknowledge (ACK) message. This message confirms the IP address lease and provides additional configuration information, such as subnet mask, default gateway, and DNS server addresses.

5. **Lease Renewal:** As the IP address lease approaches its expiration time, the client may request a lease renewal from the DHCP server. If the DHCP server approves the renewal, the client's IP address lease is extended.

6. **Release:** When a device disconnects from the network or no longer needs an IP address, it sends a DHCP Release message to the DHCP server, indicating that it is relinquishing the leased IP address.


# Working Principle of FTP

File Transfer Protocol (FTP) is an internet tool provided by TCP/IP that enables the transfer of files between computers. It was first developed by Abhay Bhushan in 1971. FTP allows users to access directories or folders on remote computers and transfer data, software, and text files between different kinds of computers. The end-user in the connection is known as localhost and the server which provides data is known as the remote host. 

### Goals of FTP

- Encourages direct use of remote computers.
- Shields users from system variations (operating system, directory structures, file structures, etc.).
- Promotes sharing of files and other types of data.

### FTP Clients

FTP works on a client-server model. The FTP client is a program that runs on the user's computer, enabling them to interact with remote computers and retrieve files. FTP clients use various commands to establish connections, transfer files, and manage the process. Some common commands include `get` (retrieve a file from the server), `mget` (retrieve multiple files), and `ls` (list files available in the current directory of the server).

### Types of FTP Connections

FTP connections can be of two types:

1. **Active FTP Connection:** In this type, the client establishes the command channel, and the server establishes the data channel. When the client requests data, the server initiates the transfer to the client. Active FTP is not the default connection and may encounter issues with firewalls.

2. **Passive FTP Connection:** Here, the client establishes both the data and command channels. When the client requests data, the server sends a random port number to the client, which then establishes the data channel. Passive FTP is the default connection and works better with firewalls.

### Anonymous FTP

Some FTP sites offer anonymous access, where users can access files without providing a username or password. Instead, the username is set to "anonymous," and the password is typically set to the guest's email address. However, anonymous users usually have limited access and cannot navigate through directories.

### How FTP Works

1. FTP connection is established between two systems using the network.
2. Two communication channels are established: the command channel and the data channel.
3. The command channel is used to transfer commands and responses between the client and server using the NVT ASCII character set. It uses port number 21.
4. The data channel is used for actual data transfer and uses port number 20.
5. The user logs in using credentials or anonymous login (email address).
6. Once connected, the client can access and transfer files from the server.
7. The client exits the connection after transferring desired files.
