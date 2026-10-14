*This project has been created as part of the 42 curriculum by aaheddar.*

# NetPractice

## Description

NetPractice is a networking exercise where you configure small-scale networks by fixing broken IP configurations. Each level presents a network diagram with hosts, routers, switches, and routing tables. Your job is to fill in the missing or incorrect values (IP addresses, subnet masks, gateways, routes) so that all devices can communicate as required by the level's goals.

The project covers 10 levels of increasing complexity, starting from simple two-host setups and building up to multi-router topologies with Internet connectivity.

## Instructions

1. Download the project files from the project page and extract them into a folder.
2. Run the training interface:
   ```
   ./run.sh
   ```
   If that doesn't work, you can start it manually:
   ```
   python3 -m http.server 49242
   ```
   Then open `http://localhost:49242` in your browser.
3. Enter your **intranet login** in the field before starting. The configurations are generated based on your login, so this step is important.
4. Work through each level by modifying the editable (unshaded) fields until the network functions correctly. Use the **Check again** button to test your solution.
5. Once a level is solved, export your configuration using the **Get my config** button before moving on.

### Submission

Place all 10 exported configuration files (one per level) at the root of your Git repository and push.

During the defense, you will need to solve three random levels within a time limit. No external tools are allowed besides a basic calculator like `bc`.

## Concepts Studied

Working through this project required understanding several core networking topics:

- **TCP/IP Addressing**: how IPv4 addresses are structured, what each octet represents, and how devices use them to identify each other on a network.
- **Subnet Masks**: how masks define the boundary between the network portion and the host portion of an address, and how changing the mask changes which addresses belong to the same network.
- **CIDR Notation**: the shorthand `/24`, `/27`, `/30` and so on, and how to convert between CIDR and dotted-decimal masks.
- **Subnetting**: splitting a larger network into smaller ones, calculating network ranges, broadcast addresses, and usable host ranges for any given prefix length.
- **Default Gateways**: why hosts need a gateway to reach anything outside their local network, and what happens when the gateway is misconfigured or unreachable.
- **Routers**: how routers forward packets between different networks using their routing tables, how they pick the best route using longest prefix match, and the difference between directly connected routes and static routes.
- **Switches**: how switches operate at Layer 2 using MAC addresses, forwarding frames to the right port or flooding when the destination is unknown. They are transparent when everything is configured correctly, but misconfigurations on the routing side can make their behavior visible.
- **Routing Tables**: how entries are matched against destination IPs, what happens when multiple routes match (longest prefix wins), and what the default route (`0.0.0.0/0`) does.
- **OSI Model**: the seven layers of network communication, with particular focus on Layer 2 (Data Link, where switches and MAC addresses live) and Layer 3 (Network, where IP addresses and routers operate).
- **ISP and Internet Routing**: how a local router hands off traffic to an ISP's router through a default route, and how the ISP's infrastructure carries the packet further toward its destination.
- **ARP (Address Resolution Protocol)**: how devices resolve IP addresses to MAC addresses on a local network before they can send Ethernet frames.
- **ICMP**: the protocol used for error messages like "Destination Unreachable" and "Time Exceeded", which routers send back when they cannot forward a packet.
- **TTL (Time To Live)**: how routers decrement this field to prevent packets from looping forever in the network.

## Resources

### References

- [RFC 791 - Internet Protocol](https://datatracker.ietf.org/doc/html/rfc791)
- [Subnet Calculator](https://www.calculator.net/ip-subnet-calculator.html)
- [Cisco Networking Basics](https://www.cisco.com/c/en/us/solutions/small-business/resource-center/networking/networking-basics.html)
- [Computer Networking: A Top-Down Approach (Kurose & Ross)](https://gaia.cs.umass.edu/kurose_ross/index.php)
- [Practical Networking - Subnetting](https://www.practicalnetworking.net/stand-alone/subnetting-mastery/)

### AI Usage

AI was used throughout this project as a learning companion. Specifically:

- **Exploring concepts**: understanding how routers make forwarding decisions, what happens step by step when a packet travels through a network, and how subnet masks affect whether a host tries to reach a destination locally or through its gateway.
- **Revising ideas**: when a configuration failed, AI helped trace through the packet path to identify where and why it broke.
- **Weird scenarios**: testing edge cases like what happens when a subnet mask is too wide and a host thinks a remote device is local, or when a default route points to a gateway that no interface can reach.
- **Theory**: learning about ARP resolution, TTL behavior, ICMP error messages, the OSI model, and how real routers handle conflicts between connected routes and static routes.
- **README creation**: this README was drafted with the help of AI and then reviewed.

All AI-generated explanations were verified against the simulator's behavior and cross-checked with online resources.