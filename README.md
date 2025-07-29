# CN-exp-2




Network Topologies: Simple LAN Configurations
This README.md provides an overview, characteristics, and basic setup procedures for common network topologies: Bus, Star, and Mesh. These are fundamental concepts for understanding Local Area Networks (LANs).

1. Bus Topology
Info:
A Bus topology is one of the simplest and oldest network architectures. In this setup, all devices (nodes) are connected to a single, shared communication cable, often called the "backbone" or "bus." Data travels along this central cable, and each device listens for data addressed to it. Terminators are required at both ends of the bus to absorb signals and prevent reflections, which could cause interference.

Characteristics:

Simple and Inexpensive: Requires less cabling than other topologies.

Easy to Install: Straightforward to set up for small networks.

Single Point of Failure (Cable): If the main cable breaks, the entire network goes down.

Troubleshooting Difficulty: Identifying cable breaks or faulty connections can be challenging.

Performance Degradation: As more devices are added, network performance can decrease due to increased traffic collisions.

Limited Scalability: Not ideal for large networks.

Simple Procedure (Conceptual):
Cabling: Obtain a coaxial cable (e.g., RG-58 for 10Base2 Ethernet) of appropriate length.

Connectors: Attach BNC connectors (Twist-on or Crimp-on) to the ends of the cable segments.

T-Connectors: For each device, use a BNC T-connector. One end of the 'T' connects to the network interface card (NIC) of the computer, and the other two ends connect to the main bus cable segments.

Terminators: Place 50-ohm BNC terminators at both extreme ends of the bus cable. This is crucial for proper signal termination.

Device Configuration: Ensure all devices (computers) have compatible network cards and are configured with IP addresses within the same subnet.

Example Setup:

[Terminator] --- [PC 1] --- [PC 2] --- [PC 3] --- [Terminator]
                (T-connector) (T-connector) (T-connector)
2. Star Topology
Info:
The Star topology is the most common and widely used network architecture today. In a Star network, all devices are connected individually to a central connecting device, typically a switch or a hub. Each device has a dedicated cable segment connecting it to the central device.

Characteristics:

Centralized Control: All communication goes through the central device.

Easy to Install and Manage: Relatively simple to add or remove devices.

Fault Isolation: If one cable segment or device fails, only that segment/device is affected; the rest of the network remains operational.

Higher Cost: Requires more cabling and a central device (switch/hub), increasing the overall cost.

Single Point of Failure (Central Device): If the central switch/hub fails, the entire network goes down.

Good Performance: Dedicated connections reduce collisions (especially with a switch), leading to better performance.

Scalability: Relatively easy to expand by adding more ports to the central device or connecting more switches.

Simple Procedure:
Central Device: Place a network switch (recommended) or a hub in a central location.

Cabling: Obtain Ethernet cables (e.g., Cat5e, Cat6) of sufficient length.

Connect Devices:

Connect one end of an Ethernet cable to the Ethernet port on each computer/device (PC, printer, server, etc.).

Connect the other end of the same Ethernet cable to an available port on the central switch/hub.

Power On: Power on the switch/hub and all connected devices.

Device Configuration: Ensure all devices are configured with IP addresses within the same subnet. Most modern operating systems will automatically obtain an IP address via DHCP if a DHCP server is present on the network (e.g., provided by a router). If not, manual static IP configuration is needed.

Example Setup:

        [Switch/Hub]
        /    |    \
       /     |     \
    [PC 1] [PC 2] [PC 3]
3. Mesh Topology
Info:
A Mesh topology is a robust and highly redundant network architecture where every device is connected to every other device in the network. This creates multiple paths for data to travel, enhancing reliability and fault tolerance. Mesh topologies can be "full mesh" (every node connected to every other node) or "partial mesh" (some nodes connected to multiple, but not all, other nodes). Full mesh is more common in small, highly critical networks, or as a backbone for larger networks.

Characteristics:

High Redundancy and Reliability: Multiple paths ensure data can still reach its destination even if one link fails.

Fault Tolerance: Excellent for mission-critical applications where downtime is unacceptable.

High Cost: Requires a significant amount of cabling and a large number of network interfaces, making it very expensive to implement, especially for a large number of devices.

Complex Implementation: Difficult to set up and manage due to the many interconnections.

No Single Point of Failure: The network can continue to operate even if several links fail.

Less Common for LANs: Rarely used for typical desktop LANs due to its complexity and cost, but often found in specialized environments or as part of a hybrid topology.

Simple Procedure (Conceptual for Full Mesh with few devices):
Note: Implementing a full mesh for more than a handful of devices becomes impractical very quickly due to the number of connections required. The number of connections needed for 'n' nodes in a full mesh is calculated as $n \* (n - 1) / 2$.

Network Interfaces: Each device will need multiple network interface cards (NICs) – one for each connection to another device in the mesh.

Cabling: Obtain Ethernet cables for each direct connection.

Direct Connections:

Connect PC 1 directly to PC 2.

Connect PC 1 directly to PC 3.

Connect PC 2 directly to PC 3.

(And so on, for all possible pairs if implementing a full mesh).

IP Configuration: This is where it gets complex. Each direct connection forms a separate point-to-point network segment. Therefore, each NIC on a device needs a unique IP address for each connection it participates in, and routing protocols (like OSPF or EIGRP) would be necessary to ensure traffic can find its way across the multiple paths.

Routing Configuration: Manual static routes would be required for a very small setup, or dynamic routing protocols for anything larger, to manage the multiple paths.

Example Setup (3 devices - Full Mesh):

    [PC 1] --- [PC 2]
      |        / |
      |       /  |
      |      /   |
      |     /    |
      |    /     |
      |   /      |
      |  /       |
    [PC 3] ------
Conclusion
Understanding these fundamental network topologies is crucial for designing and troubleshooting effective LANs. While Bus topology is largely obsolete for new installations, Star topology is the industry standard for most modern LANs due to its balance of performance, manageability, and cost. Mesh topology, while highly reliable, is reserved for niche applications due to its significant cost and complexity.
